package projectT;<br />
<br />
import java.text.SimpleDateFormat;<br />
import java.util.ArrayList;<br />
import java.util.Calendar;<br />
import java.util.Date;<br />
import java.util.HashMap;<br />
import java.util.Iterator;<br />
import java.util.List;<br />
import java.util.Map;<br />
<br />
<br />
<br />
<br />
<br />
public class testDate {<br />
<br />
public static void main(String[] args) &nbsp;{<br />
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
//		info infos = null;<br />
//		infos=new info();<br />
//		infos.setPlayerId("1100");<br />
//		infos.setTotal_PNL("testss");<br />
//		infos.setTotal_Stake_Accurate("gggggg");<br />
// <br />
//		List&lt;info&gt; lists= new ArrayList&lt;info&gt;();<br />
//		lists.add(infos);<br />
//		for(info z:lists){<br />
//			System.out.println(z.getPlayerId());<br />
//		}<br />
// <br />
//		Iterator&lt;info&gt; iter = lists.iterator();<br />
//		 &nbsp;<br />
//		 while(iter.hasNext()) &nbsp;<br />
// &nbsp; &nbsp; &nbsp; &nbsp; { &nbsp;<br />
// &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;System.out.println(iter.next().getPlayerId()); &nbsp;<br />
// &nbsp; &nbsp; &nbsp; &nbsp; } &nbsp;<br />
// <br />
//		 &nbsp;<br />
//		 &nbsp;<br />
//		 &nbsp;Map map = new HashMap();<br />
//		 &nbsp;<br />
//		 &nbsp;map.put("aaa","aaa");<br />
//		 &nbsp;<br />
//	 &nbsp; &nbsp;	System.out.println(map.get("aaa"));<br />
// <br />
//List&lt;info&gt; infolist=null;<br />
<br />
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
//((info) infolist).setTotal_PNL("111");<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
//格式化时间<br />
SimpleDateFormat sdf = new SimpleDateFormat("yyyyMMdd HH:mm:ss");<br />
Calendar cl = Calendar.getInstance();<br />
<br />
System.out.println(Calendar.MINUTE);<br />
<br />
cl.setTime(new Date());<br />
//时区<br />
cl.set(Calendar.HOUR_OF_DAY, cl.get(Calendar.HOUR_OF_DAY) + (-12));<br />
<br />
//分钟<br />
cl.set(Calendar.MINUTE, (cl.get(Calendar.MINUTE) + 1));<br />
<br />
String endTime = sdf.format(cl.getTime());<br />
<br />
System.out.println(cl.getTime());<br />
//设置分钟减49<br />
cl.set(Calendar.MINUTE, cl.get(cl.MINUTE) - 49);<br />
String beginTime = sdf.format(cl.getTime());<br />
<br />
//时间戳<br />
long createTime = cl.getTime().getTime() / 1000;<br />
<br />
System.out.println("createTime:"+createTime);<br />
System.out.println("beginTime:"+beginTime);<br />
System.out.println("endTime:"+endTime);<br />
<br />
<br />
<br />
<br />
<br />
&nbsp; &nbsp; }<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
}<br />
<div style="white-space:nowrap;">
	<br />
</div>