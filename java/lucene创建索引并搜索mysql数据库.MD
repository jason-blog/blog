<p>
	<br />
</p>
<p style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-size:18px;">http://blog.csdn.net/winnerspring/article/details/34112269</span> 
</p>
<p style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-size:18px;"><br />
</span>
</p>
<p style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-size:18px;">1：写一段传统的JDBC程序，将每条的用户信息从<a href="http://lib.csdn.net/base/mysql" class="replace_word" title="MySQL知识库" target="_blank" style="color:#DF3434;text-decoration-line:none;font-weight:bold;">数据库</a>读取出来</span> 
</p>
<p style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-size:18px;">2：针对每条用户记录，建立一个lucene document&nbsp;</span> 
</p>
<span style="color:#333333;font-family:Arial;white-space:normal;background-color:#FFFFFF;font-size:18px;">Document doc = new Document();&nbsp;<br />
并根据你的需要，将用户信息的各个字段对应luncene document中的field 进行添加，如：&nbsp;<br />
doc.add(new TextField("id", id+"",Field.Store.YES));<br />
然后将该条doc加入到索引中， 如： iwriter.addDocument(doc);<br />
这样就建立了lucene的索引库<br />
3：编写对索引库的搜索程序（看lucene文档），通过对lucene的索引库的查找，你可以快速找到对应记录的值<br />
</span><span style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;"></span> 
<p style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<br />
</p>
<p style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<br />
</p>
<p style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-size:18px;">代码：</span> 
</p>
<p style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-size:18px;">jar包：IKAnalyzer2012_FF.jar</span> 
</p>
<p style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-size:18px;"><span style="white-space:pre;"></span>&nbsp; &nbsp;lucene-analyzers-common-4.9.0.jar</span> 
</p>
<p style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-size:18px;"><span style="white-space:pre;"></span>&nbsp; &nbsp;lucene-core-4.9.0.jar</span> 
</p>
<p style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-size:18px;"><span style="white-space:pre;"></span>&nbsp; &nbsp;lucene-queryparser-4.9.0.jar</span> 
</p>
<p style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-size:18px;">建议使用jdk1.7</span> 
</p>
<p style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-size:18px;"><br />
<br />
import&nbsp;<a href="http://lib.csdn.net/base/javase" class="replace_word" title="Java SE知识库" target="_blank" style="color:#DF3434;text-decoration-line:none;font-weight:bold;">Java</a>.io.File;<br />
import java.io.IOException;<br />
import java.sql.Connection;<br />
import java.sql.DriverManager;<br />
import java.sql.PreparedStatement;<br />
import java.sql.ResultSet;<br />
<br />
<br />
import org.apache.lucene.analysis.Analyzer;<br />
import org.apache.lucene.document.Document;<br />
import org.apache.lucene.document.Field;<br />
import org.apache.lucene.document.TextField;<br />
import org.apache.lucene.index.DirectoryReader;<br />
import org.apache.lucene.index.IndexWriter;<br />
import org.apache.lucene.index.IndexWriterConfig;<br />
import org.apache.lucene.index.IndexWriterConfig.OpenMode;<br />
import org.apache.lucene.queryparser.classic.ParseException;<br />
import org.apache.lucene.queryparser.classic.QueryParser;<br />
import org.apache.lucene.search.IndexSearcher;<br />
import org.apache.lucene.search.Query;<br />
import org.apache.lucene.search.ScoreDoc;<br />
import org.apache.lucene.store.Directory;<br />
import org.apache.lucene.store.FSDirectory;<br />
import org.apache.lucene.store.RAMDirectory;<br />
import org.apache.lucene.util.Version;<br />
import org.wltea.analyzer.lucene.IKAnalyzer;<br />
<br />
<br />
<br />
<br />
<br />
<br />
/**<br />
&nbsp;*<br />
&nbsp;* Lucene与数据库结合使用<br />
&nbsp;*<br />
&nbsp;* @author&nbsp;<br />
&nbsp;*/<br />
public class LuceneDemo01 {<br />
<br />
<br />
&nbsp; &nbsp; private static final String driverClassName="com.<a href="http://lib.csdn.net/base/mysql" class="replace_word" title="MySQL知识库" target="_blank" style="color:#DF3434;text-decoration-line:none;font-weight:bold;">MySQL</a>.jdbc.Driver";<br />
&nbsp; &nbsp; private static final String url="jdbc:mysql://127.0.0.1:3306/test?characterEncoding=utf-8";<br />
&nbsp; &nbsp; private static final String username="root";<br />
&nbsp; &nbsp; private static final String password="root";<br />
<br />
<br />
&nbsp; &nbsp; private static final Version version = Version.LUCENE_4_9;<br />
&nbsp; &nbsp; private Directory directory = new RAMDirectory();<br />
&nbsp; &nbsp; private DirectoryReader ireader = null;<br />
&nbsp; &nbsp; private IndexWriter iwriter = null;<br />
&nbsp; &nbsp; private IKAnalyzer analyzer;<br />
&nbsp; &nbsp; //存放索引文件的位置，即索引库<br />
&nbsp; &nbsp; private String searchDir = "d:\\Test\\Index";<br />
&nbsp; &nbsp; private static File indexFile = null; &nbsp;&nbsp;<br />
&nbsp; &nbsp; private Connection conn;<br />
&nbsp; &nbsp; /**<br />
&nbsp; &nbsp; &nbsp;* 读取索引文件<br />
&nbsp; &nbsp; &nbsp;* @return<br />
&nbsp; &nbsp; &nbsp;* @throws Exception<br />
&nbsp; &nbsp; &nbsp;*/<br />
&nbsp; &nbsp; public IndexSearcher getSearcher() throws Exception{<br />
&nbsp; &nbsp;&nbsp;<span style="white-space:pre;"></span>indexFile = new File(searchDir);<br />
&nbsp; &nbsp; &nbsp; &nbsp; ireader = DirectoryReader.open(FSDirectory.open(indexFile));<br />
&nbsp; &nbsp; &nbsp; &nbsp; return new IndexSearcher(ireader);<br />
&nbsp; &nbsp; }<br />
&nbsp; &nbsp; /**<br />
&nbsp; &nbsp; &nbsp;* 获取数据库连接<br />
&nbsp; &nbsp; &nbsp;* @return<br />
&nbsp; &nbsp; &nbsp;*/<br />
&nbsp; &nbsp; public Connection getConnection(){<br />
&nbsp; &nbsp; &nbsp; &nbsp; if(this.conn == null){<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; try {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Class.forName(driverClassName);<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; conn = DriverManager.getConnection(url, username, password);<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; } catch (Exception e) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; e.printStackTrace();<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; &nbsp; return conn;<br />
&nbsp; &nbsp; }<br />
&nbsp; &nbsp; /**<br />
&nbsp; &nbsp; &nbsp;* 中文分词工具<br />
&nbsp; &nbsp; &nbsp;* @return<br />
&nbsp; &nbsp; &nbsp;*/<br />
&nbsp; &nbsp; private IKAnalyzer getAnalyzer(){<br />
&nbsp; &nbsp; &nbsp; &nbsp; if(analyzer == null){<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; return new IKAnalyzer();<br />
&nbsp; &nbsp; &nbsp; &nbsp; }else{<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; return analyzer;<br />
&nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; }<br />
&nbsp; &nbsp; /**<br />
&nbsp; &nbsp; &nbsp;* 创建索引文件<br />
&nbsp; &nbsp; &nbsp;*/<br />
&nbsp; &nbsp; public void createIndex(){<br />
&nbsp; &nbsp; &nbsp; &nbsp; Connection conn = getConnection();<br />
&nbsp; &nbsp; &nbsp; &nbsp; ResultSet rs = null;<br />
&nbsp; &nbsp; &nbsp; &nbsp; PreparedStatement pstmt = null;<br />
&nbsp; &nbsp; &nbsp; &nbsp; if(conn == null){<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; System.out.println("get the connection error...");<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; return ;<br />
&nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; &nbsp; String sql = "select id,name from t_user";<br />
&nbsp; &nbsp; &nbsp; &nbsp; try {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; pstmt = conn.prepareStatement(sql);<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; rs = pstmt.executeQuery();<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /**<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;* 获取索引文件位置<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;*/<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; indexFile = new File(searchDir); &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; if(!indexFile.exists()) { &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; indexFile.mkdirs(); &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; } &nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /**<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;* 设置索引参数<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;*/<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; directory = FSDirectory.open(indexFile); &nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; IndexWriterConfig iwConfig = &nbsp;new IndexWriterConfig(version, getAnalyzer());<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; iwConfig.setOpenMode(OpenMode.CREATE_OR_APPEND);<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; iwriter = new IndexWriter(directory,iwConfig);<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /*lucene本身不支持更新&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;* &nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;* 通过删除索引然后再建立索引来更新&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;*/&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; iwriter.deleteAll();//删除上次的索引文件，重新生成索引<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; while(rs.next()){<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; int id = rs.getInt("id");<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; String name = rs.getString("name");<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Document doc = new Document();<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; doc.add(new TextField("id", id+"",Field.Store.YES));<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; doc.add(new TextField("name", name+"",Field.Store.YES));<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; iwriter.addDocument(doc);<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; &nbsp; } catch (Exception e) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; e.printStackTrace();<br />
&nbsp; &nbsp; &nbsp; &nbsp; }finally{<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; try {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; if(iwriter != null)<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; iwriter.close();<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; rs.close();<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; pstmt.close();<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; if(!conn.isClosed()){<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; conn.close();<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; } catch (Exception e) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; e.printStackTrace();<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; }<br />
&nbsp; &nbsp; /**<br />
&nbsp; &nbsp; &nbsp;* 查询方法<br />
&nbsp; &nbsp; &nbsp;* @param field 字段名称<br />
&nbsp; &nbsp; &nbsp;* @param keyword 字段值<br />
&nbsp; &nbsp; &nbsp;* @param num&nbsp;<br />
&nbsp; &nbsp; &nbsp;* @throws Exception<br />
&nbsp; &nbsp; &nbsp;*/<br />
&nbsp; &nbsp; public void searchByTerm(String field,String keyword,int num) throws Exception{<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;IndexSearcher isearcher = getSearcher();<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;Analyzer analyzer = &nbsp;getAnalyzer();<br />
&nbsp; &nbsp; &nbsp; &nbsp; //使用QueryParser查询分析器构造Query对象<br />
&nbsp; &nbsp; &nbsp; &nbsp; QueryParser qp = new QueryParser(version,field,analyzer);<br />
&nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; qp.setDefaultOperator(QueryParser.OR_OPERATOR);<br />
&nbsp; &nbsp; &nbsp; &nbsp; try {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Query query = qp.parse(keyword);<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ScoreDoc[] hits;<br />
<br />
<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; //注意searcher的几个方法<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; hits = isearcher.search(query, null, num).scoreDocs;<br />
<br />
<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; System.out.println("the ids is =");<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; for (int i = 0; i &lt; hits.length; i++) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Document doc = isearcher.doc(hits[i].doc);<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; System.out.print(doc.get("id")+" ");<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; System.out.println(doc.get("name")+" ");<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }<br />
<br />
<br />
&nbsp; &nbsp; &nbsp; &nbsp; } catch (IOException e) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; e.printStackTrace();<br />
&nbsp; &nbsp; &nbsp; &nbsp; } catch (ParseException e) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; e.printStackTrace();<br />
&nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; }<br />
&nbsp; &nbsp; /** &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp;* 搜索索引 &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp;*/ &nbsp; &nbsp;<br />
&nbsp; &nbsp; public static void main(String[] args) throws Exception {<br />
&nbsp; &nbsp; &nbsp; &nbsp; LuceneDemo01 ld = new LuceneDemo01();<br />
&nbsp; &nbsp; &nbsp; &nbsp; //ld.createIndex();<br />
&nbsp; &nbsp; &nbsp; &nbsp; ld.searchByTerm("name", "玉", 100);<br />
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; }<br />
}</span> 
</p>
<p>
	<br />
</p>