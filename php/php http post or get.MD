&lt;?php<br />
/**<br />
&nbsp;* php 发送http post get 请求<br />
&nbsp;*/<br />
header("Content-type:text/html;charset=utf-8");<br />
function send_post($url, $post_data) {<br />
&nbsp; &nbsp; $postdata = http_build_query($post_data);<br />
&nbsp; &nbsp; $options = array(<br />
&nbsp; &nbsp; &nbsp; &nbsp; 'http' =&gt; array(<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'method' =&gt; 'GET',//or GET<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'header' =&gt; 'Content-type:application/x-www-form-urlencoded',<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'content' =&gt; $postdata,<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'timeout' =&gt; 15 * 60 // 超时时间（单位:s）<br />
&nbsp; &nbsp; &nbsp; &nbsp; )<br />
&nbsp; &nbsp; );<br />
&nbsp; &nbsp; $context = stream_context_create($options);<br />
&nbsp; &nbsp; $result = file_get_contents($url, false, $context);<br />
&nbsp; &nbsp; return $result;<br />
}<br />
//使用方法<br />
$post_data = array(<br />
&nbsp; &nbsp; 'username' =&gt; 'stclair2201',<br />
&nbsp; 'password' =&gt; 'handan'<br />
&nbsp; );<br />
&nbsp; $result=send_post('http://www.ddf.com', $post_data);<br />
&nbsp;&nbsp;<br />
&nbsp; print_r($result);<br />
&nbsp; //PHP接收方法<br />
&nbsp; /**<br />
&nbsp; &nbsp;* $input=file_get_contents("php://input");<br />
file_put_contents("java.xml",$input);<br />
print_r($input);<br />
&nbsp; &nbsp;*/<br />
&nbsp; &nbsp;<br />
&nbsp; &nbsp;<br />
?&gt;<br />
<br />
&lt;?php<br />
/**<br />
&nbsp;* php 发送http post get 请求<br />
&nbsp;*/<br />
header('Content-Type: text/html; charset=UTF-8');<br />
<br />
function send_post($url, $post_data) {<br />
&nbsp; &nbsp; $postdata = http_build_query($post_data);<br />
&nbsp; &nbsp; $options = array(<br />
&nbsp; &nbsp; &nbsp; &nbsp; 'http' =&gt; array(<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'method' =&gt; 'POST',//or GET<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'header' =&gt; array('Content-type:application/x-www-form-urlencoded',<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'Cookie:adminUserId=10; Hm_lvt_7b1919221e89d2aa5711e4deb935debd=1458710012; CNZZDATA1000310955=821610460-1444729678-%7C1462155006; CNZZDATA5517574=cnzz_eid%3D1611205201-1444729374-%26ntime%3D1462437670; PHPSESSID=3a62f5485732929620cf3; CNZZDATA1000493589=1225702284-1444701670-%7C1462936498'<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ),&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'content' =&gt; $postdata,<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'timeout' =&gt; 15 * 60 // 超时时间（单位:s）<br />
&nbsp; &nbsp; &nbsp; &nbsp; )<br />
&nbsp; &nbsp; );<br />
&nbsp; &nbsp; $context = stream_context_create($options);<br />
&nbsp; &nbsp; $result = file_get_contents($url, false, $context);<br />
&nbsp; &nbsp; return $result;<br />
}<br />
//使用方法<br />
$post_data = array(<br />
&nbsp; &nbsp; 'username' =&gt; 'stclair2201',<br />
&nbsp; &nbsp; 'password' =&gt; 'handan'<br />
);<br />
$result=send_post('http://www.ddf.com/user.php', $post_data);<br />
<br />
print_r($result);<br />
&nbsp; //PHP接收方法<br />
&nbsp; /**<br />
&nbsp; &nbsp;* $input=file_get_contents("php://input");<br />
file_put_contents("java.xml",$input);<br />
print_r($input);<br />
&nbsp; &nbsp;*/<br />
&nbsp; &nbsp;<br />
&nbsp; &nbsp;<br />
&nbsp; &nbsp;<br />
&nbsp; &nbsp;<br />
&nbsp; &nbsp;<br />
&nbsp; &nbsp;<br />
?&gt;<br />