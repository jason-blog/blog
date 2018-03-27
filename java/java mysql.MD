package ceshi;<br />
<br />
import java.sql.Connection;<br />
import java.sql.DriverManager;<br />
import java.sql.ResultSet;<br />
import java.sql.SQLException;<br />
import java.sql.Statement;<br />
import java.util.Collection;<br />
import java.util.HashSet;<br />
import java.util.Iterator;<br />
<br />
import com.mysql.jdbc.ResultSetMetaData;<br />
<br />
public class db {<br />
public Object conn(){<br />
&nbsp; &nbsp; &nbsp; &nbsp; // 驱动程序名<br />
&nbsp; &nbsp; &nbsp; &nbsp; String driver = "com.mysql.jdbc.Driver";<br />
&nbsp; &nbsp; &nbsp; &nbsp; // URL指向要访问的数据库名scutcs<br />
&nbsp; &nbsp; &nbsp; &nbsp; String url = "jdbc:mysql://10.1.0.226:3306/game";<br />
&nbsp; &nbsp; &nbsp; &nbsp; // MySQL配置时的用户名<br />
&nbsp; &nbsp; &nbsp; &nbsp; String user = "root";&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; // MySQL配置时的密码<br />
&nbsp; &nbsp; &nbsp; &nbsp; String password = "";<br />
&nbsp; &nbsp; &nbsp; &nbsp; try {&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;// 加载驱动程序<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;Class.forName(driver);<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;// 连续数据库<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;Connection conn = DriverManager.getConnection(url, user, password);<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;if(!conn.isClosed())&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; System.out.println("Succeeded connecting to the Database!");<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;return conn;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;// statement用来执行SQL语句<br />
// &nbsp; &nbsp; &nbsp; &nbsp; Statement statement = conn.createStatement();<br />
// &nbsp; &nbsp; &nbsp; &nbsp; return &nbsp;statement;<br />
// &nbsp; &nbsp; &nbsp; &nbsp; // 要执行的SQL语句<br />
// &nbsp; &nbsp; &nbsp; &nbsp; String sql = "select * from ceshi";<br />
// &nbsp; &nbsp; &nbsp; &nbsp; // 结果集<br />
// &nbsp; &nbsp; &nbsp; &nbsp; ResultSet rs = statement.executeQuery(sql);<br />
// &nbsp; &nbsp; &nbsp; &nbsp; System.out.println("-----------------");<br />
// &nbsp; &nbsp; &nbsp; &nbsp; System.out.println("执行结果如下所示:");<br />
// &nbsp; &nbsp; &nbsp; &nbsp; System.out.println("-----------------");<br />
// &nbsp; &nbsp; &nbsp; &nbsp; System.out.println(" id" + "\t" + " &nbsp; &nbsp;user_name" + "\t"+" amount" + "\t" + " roundid");<br />
// &nbsp; &nbsp; &nbsp; &nbsp; System.out.println("-----------------");<br />
// &nbsp; &nbsp; &nbsp; &nbsp; String name = null;<br />
// &nbsp; &nbsp; &nbsp; &nbsp; while(rs.next()) {<br />
// &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;// 选择sname这列数据<br />
// &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;name = rs.getString("user_name");<br />
// &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;// 首先使用ISO-8859-1字符集将name解码为字节序列并将结果存储新的字节数组中。<br />
// &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;// 然后使用GB2312字符集解码指定的字节数组<br />
// &nbsp; &nbsp; &nbsp; &nbsp; // name = new String(name.getBytes("ISO-8859-1"),"GB2312");<br />
// &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;// 输出结果<br />
// &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;System.out.println(rs.getString("id") + " &nbsp;" + name + "\t"+rs.getString("amount") &nbsp;+ "\t"+rs.getString("roundid"));<br />
// &nbsp; &nbsp; &nbsp; &nbsp; }<br />
// &nbsp; &nbsp; &nbsp; &nbsp; rs.close();<br />
// &nbsp; &nbsp; &nbsp; &nbsp; conn.close();<br />
&nbsp; &nbsp; &nbsp; &nbsp; } catch(ClassNotFoundException e) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;System.out.println("Sorry,can`t find the Driver!");&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;e.printStackTrace();<br />
&nbsp; &nbsp; &nbsp; &nbsp; } catch(SQLException e) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;e.printStackTrace();<br />
&nbsp; &nbsp; &nbsp; &nbsp; } catch(Exception e) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;e.printStackTrace();<br />
&nbsp; &nbsp; &nbsp; &nbsp; }<br />
return 1;&nbsp;<br />
}<br />
public String select(String sql){<br />
String Str="";<br />
try{<br />
&nbsp; &nbsp; &nbsp;Object conn=conn();<br />
<br />
&nbsp;// 要执行的SQL语句<br />
&nbsp; &nbsp; &nbsp;// String sql = "select * from ceshi";<br />
&nbsp; &nbsp; &nbsp; Statement statement = ((Connection) conn).createStatement();<br />
&nbsp; &nbsp; &nbsp; // 结果集<br />
&nbsp; &nbsp; &nbsp; ResultSet rs = statement.executeQuery(sql);<br />
// &nbsp; &nbsp; &nbsp;System.out.println("-----------------");<br />
// &nbsp; &nbsp; &nbsp;System.out.println("执行结果如下所示:");<br />
// &nbsp; &nbsp; &nbsp;System.out.println("-----------------");<br />
// &nbsp; &nbsp; &nbsp;System.out.println(" id" + "\t" + " &nbsp; &nbsp;user_name" + "\t"+" amount" + "\t" + " roundid");<br />
// &nbsp; &nbsp; &nbsp;System.out.println("-----------------");<br />
&nbsp; &nbsp; &nbsp;// ResultSetMetaData rsmd = (ResultSetMetaData) rs.getMetaData();<br />
&nbsp; &nbsp; &nbsp;// int colcount = rsmd.getColumnCount();<br />
&nbsp; &nbsp; &nbsp;<br />
&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; ResultSetMetaData rsmd = (ResultSetMetaData) rs.getMetaData();<br />
&nbsp; &nbsp; &nbsp; int colcount1 = rsmd.getColumnCount();//取得全部列数<br />
&nbsp; &nbsp; &nbsp; Collection list=new HashSet();<br />
&nbsp; &nbsp; &nbsp; for(int i=1;i&lt;=colcount1;i++){<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;String colname = rsmd.getColumnName(i);//取得全部列名<br />
&nbsp; &nbsp; &nbsp; &nbsp;// &nbsp;System.out.println(colname);<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;list.add(colname);<br />
&nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp;&nbsp;<br />
// &nbsp; &nbsp; &nbsp;ResultSet rrrr=statement.executeQuery("describe rfcorp_admin");<br />
// &nbsp; &nbsp; &nbsp;//String[] list = new String[]{};<br />
// &nbsp; &nbsp; &nbsp;Collection list=new HashSet();<br />
// &nbsp; &nbsp; &nbsp; while (rrrr.next()) {<br />
// &nbsp; &nbsp;	String ssss=rrrr.getString(1);&nbsp;<br />
// &nbsp; &nbsp;	 &nbsp; list.add(ssss);<br />
// &nbsp; &nbsp;	 &nbsp; System.out.println(ssss);<br />
// &nbsp; &nbsp; &nbsp;}<br />
&nbsp; &nbsp;&nbsp;<br />
// &nbsp; &nbsp; &nbsp;for(int i=0;i&lt;colcount;i++){<br />
// &nbsp; &nbsp;	 &nbsp; String colname = rsmd.getColumnName(i);//取得全部列名<br />
// &nbsp; &nbsp;	 &nbsp; System.out.println(colname);<br />
// &nbsp; &nbsp;	}<br />
&nbsp; &nbsp; &nbsp; &nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp;Iterator it =list.iterator();<br />
// &nbsp; &nbsp; &nbsp; while (it.hasNext()){<br />
//	 &nbsp; &nbsp; &nbsp; &nbsp;String s=(String) it.next();<br />
//	 &nbsp; &nbsp; &nbsp; &nbsp;System.out.println(s);<br />
//	 &nbsp; &nbsp; &nbsp; &nbsp;//data+= rs.getString(s)+"\t";<br />
//	 &nbsp; &nbsp; &nbsp; }<br />
// &nbsp; &nbsp; &nbsp; System.exit(1);<br />
&nbsp; &nbsp; &nbsp; String name = null;<br />
&nbsp; &nbsp; &nbsp; String data= "";<br />
&nbsp; &nbsp; &nbsp; while(rs.next()) {<br />
&nbsp; &nbsp; 	 &nbsp;<br />
&nbsp; &nbsp; 	 &nbsp; while (it.hasNext()){<br />
&nbsp; &nbsp; 	 &nbsp; &nbsp; &nbsp; &nbsp;String s=(String) it.next();<br />
&nbsp; &nbsp; 	 &nbsp; &nbsp; &nbsp; &nbsp;System.out.println(s);<br />
&nbsp; &nbsp; 	 &nbsp; &nbsp; &nbsp; &nbsp;data+= rs.getString(s)+"\t";<br />
&nbsp; &nbsp; 	 &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; 	 // &nbsp;data+="\n";<br />
&nbsp; &nbsp; &nbsp; &nbsp;// 选择sname这列数据<br />
&nbsp; &nbsp; &nbsp;// &nbsp;name = rs.getString("username");<br />
&nbsp; &nbsp; &nbsp; &nbsp;// 首先使用ISO-8859-1字符集将name解码为字节序列并将结果存储新的字节数组中。<br />
&nbsp; &nbsp; &nbsp; &nbsp;// 然后使用GB2312字符集解码指定的字节数组<br />
&nbsp; &nbsp; &nbsp; // name = new String(name.getBytes("ISO-8859-1"),"GB2312");<br />
&nbsp; &nbsp; &nbsp; &nbsp;// 输出结果<br />
&nbsp; &nbsp; &nbsp;// &nbsp;Str+=rs.getString("id") + " &nbsp;" + name + "\t"+rs.getString("amount") &nbsp;+ "\t"+rs.getString("roundid")+"\n";<br />
&nbsp; &nbsp; &nbsp; System.out.println(data);<br />
&nbsp; &nbsp; &nbsp; Str+=data;<br />
&nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; rs.close();<br />
&nbsp; &nbsp; &nbsp;// conn.close();<br />
}catch(SQLException e){<br />
System.out.println("cuowu !!");<br />
}<br />
return Str;<br />
}<br />
}<br />
<br />
<br />