package projectT;<br />
<br />
import java.io.File;<br />
import java.io.IOException;<br />
import java.io.StringReader;<br />
import java.util.ArrayList;<br />
import java.util.Iterator;<br />
import java.util.LinkedList;<br />
import java.util.List;<br />
<br />
import javax.xml.bind.JAXBContext;<br />
import javax.xml.bind.JAXBException;<br />
import javax.xml.bind.Marshaller;<br />
import javax.xml.bind.Unmarshaller;<br />
import javax.xml.bind.annotation.XmlRootElement;<br />
import javax.xml.parsers.DocumentBuilder;<br />
import javax.xml.parsers.DocumentBuilderFactory;<br />
import javax.xml.parsers.ParserConfigurationException;<br />
<br />
import org.w3c.dom.Document;<br />
import org.w3c.dom.NodeList;<br />
import org.xml.sax.SAXException;<br />
<br />
;public class test {<br />
<br />
public static void main(String[] args) throws SAXException, IOException, ParserConfigurationException {<br />
// TODO Auto-generated method stub<br />
<br />
<br />
//		TestJaxb TestJaxb=new TestJaxb();<br />
//		TestJaxb.XMLStringToBean();<br />
<br />
<br />
// <br />
long lasting =System.currentTimeMillis();&nbsp;<br />
//		　　try{&nbsp;<br />
// <br />
// <br />
<br />
File f=new File("C:\\Users\\Json\\Desktop\\test1.xml");&nbsp;<br />
<br />
DocumentBuilderFactory factory=DocumentBuilderFactory.newInstance();<br />
DocumentBuilder builder =factory.newDocumentBuilder();&nbsp;<br />
Document doc = builder.parse(f);<br />
<br />
NodeList nl = doc.getElementsByTagName("name");&nbsp;<br />
<br />
<br />
<br />
String test=doc.getElementsByTagName("name").item(0).getFirstChild().getNodeValue();<br />
<br />
String test1=doc.getElementsByTagName("string").item(0).getFirstChild().getNodeValue();<br />
<br />
<br />
<br />
//		System.out.println(test);<br />
//		System.out.println(test1);<br />
// <br />
//	System.exit(0);<br />
<br />
&nbsp;info info =new info();<br />
<br />
&nbsp;String [][] arr =new String [nl.getLength()/3][3];;<br />
&nbsp;<br />
&nbsp; &nbsp; &nbsp;int z=0;<br />
for (int i=0;i&lt;nl.getLength();i=i+3){&nbsp;<br />
String PlayerId=doc.getElementsByTagName("name").item(i).getFirstChild().getNodeValue();<br />
String PlayerIdv=doc.getElementsByTagName("string").item(i).getFirstChild().getNodeValue();<br />
<br />
String Total_Stake_Accurate=doc.getElementsByTagName("name").item(i+1).getFirstChild().getNodeValue();<br />
String Total_Stake_Accuratev=doc.getElementsByTagName("string").item(i+1).getFirstChild().getNodeValue();<br />
<br />
String Total_PNL=doc.getElementsByTagName("name").item(i+2).getFirstChild().getNodeValue();<br />
String Total_PNLv=doc.getElementsByTagName("string").item(i+2).getFirstChild().getNodeValue();<br />
<br />
//			System.out.println(PlayerIdv);&nbsp;<br />
//			System.out.println(Total_Stake_Accuratev);&nbsp;<br />
//			System.out.println(Total_PNLv);&nbsp;<br />
// <br />
<br />
info.setPlayerId(PlayerIdv);<br />
info.setTotal_Stake_Accurate(Total_Stake_Accuratev);<br />
info.setTotal_PNL(Total_PNLv);<br />
<br />
<br />
arr[z][0]=PlayerIdv;<br />
arr[z][1]=Total_Stake_Accuratev;<br />
arr[z][2]=Total_PNLv;<br />
<br />
<br />
<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; z++;<br />
//		　 　}&nbsp;<br />
//		　　}catch(Exception e){&nbsp;<br />
//		　　　e.printStackTrace();&nbsp;<br />
//		}&nbsp;<br />
}<br />
<br />
//System.out.println(arr[0]);<br />
<br />
&nbsp;<br />
System.out.println(arr.length);<br />
<br />
for(int x = 0; x&lt; arr.length; x++){ &nbsp;//定位行 &nbsp;<br />
&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;for(int y = 0; y&lt;arr[x].length; y++){ &nbsp;//定位每行的元素个数 &nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;System.out.print(arr[x][y]); &nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;} &nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp;} &nbsp;<br />
<br />
<br />
<br />
<br />
//// <br />
//		System.out.println(getInfo.get(1).getPlayerId());<br />
//		System.out.println(getInfo.get(0).getTotal_Stake_Accurate());<br />
// <br />
// <br />
//		 &nbsp;Iterator&lt;info&gt; iter = getInfo.iterator();&nbsp;<br />
// <br />
&nbsp;<br />
&nbsp;<br />
//		 &nbsp;while(iter.hasNext()) &nbsp;<br />
//	 &nbsp; &nbsp; &nbsp; &nbsp;{ &nbsp;<br />
//	 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;iter.next(); &nbsp;<br />
//	 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br />
//	 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; System.out.println(iter.next().getPlayerId()); &nbsp;<br />
//	 &nbsp; &nbsp; &nbsp; &nbsp;} &nbsp;<br />
//		 &nbsp;<br />
// <br />
<br />
<br />
<br />
&nbsp; <br />
}<br />
public static void readXML() {<br />
&nbsp;SAXReader sr = new SAXReader();// 获取读取xml的对象。<br />
&nbsp;try {<br />
&nbsp; Document doc = sr.read("D:\\zend\\DDF-SVN\\trunk\\test1.xml");// 得到xml所在位置。然后开始读取。并将数据放入doc中<br />
&nbsp; Element el_root = doc.getRootElement();// 向外取数据，获取xml的根节点。<br />
&nbsp; System.out.println("根节点：" + el_root.getName());<br />
&nbsp; Iterator it = el_root.elementIterator();// 从根节点下依次遍历，获取根节点下所有子节点<br />
<br />
&nbsp; while (it.hasNext()) {// 遍历子节点<br />
&nbsp; &nbsp;Object o = it.next();<br />
&nbsp; &nbsp;Element el_row = (Element) o;<br />
&nbsp; &nbsp;String str = el_row.getText();<br />
&nbsp; &nbsp;Iterator it_row = el_row.elementIterator();<br />
&nbsp; &nbsp;while (it_row.hasNext()) {<br />
&nbsp; &nbsp; Element el_ename = (Element) it_row.next();<br />
&nbsp; &nbsp; System.out.println(el_ename.getName() + "="<br />
&nbsp; &nbsp; &nbsp; + el_ename.getData());<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp;}<br />
&nbsp; }<br />
&nbsp;} catch (DocumentException e) {<br />
&nbsp; e.printStackTrace();<br />
&nbsp;}<br />
}<br />
<br />
<br />
<br />
}<br />
<br />
<br />
<div style="white-space:nowrap;">
	<br />
</div>