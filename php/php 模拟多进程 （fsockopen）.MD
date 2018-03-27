&lt;?php<br />
<br />
header('Content-Type: text/html; charset=UTF-8');<br />
<br />
function doRequest($url, $param=array()){<br />
<br />
&nbsp; &nbsp; $urlinfo = parse_url($url);<br />
<br />
&nbsp; &nbsp; $host = $urlinfo['host'];<br />
&nbsp; &nbsp; $path = $urlinfo['path'];<br />
&nbsp; &nbsp; $query = isset($param)? http_build_query($param) : '';<br />
<br />
&nbsp; &nbsp; $port = 80;<br />
&nbsp; &nbsp; $errno = 0;<br />
&nbsp; &nbsp; $errstr = '';<br />
&nbsp; &nbsp; $timeout = 10;<br />
<br />
&nbsp; &nbsp; $fp = fsockopen($host, $port, $errno, $errstr, $timeout);<br />
<br />
&nbsp; &nbsp; $out = "POST ".$path." HTTP/1.1\r\n";<br />
&nbsp; &nbsp; $out .= "host:".$host."\r\n";<br />
&nbsp; &nbsp; $out .= "content-length:".strlen($query)."\r\n";<br />
&nbsp; &nbsp; $out .= "content-type:application/x-www-form-urlencoded\r\n";<br />
&nbsp; &nbsp; $out .= "connection:close\r\n\r\n";<br />
&nbsp; &nbsp; $out .= $query;<br />
<br />
&nbsp; &nbsp; fputs($fp, $out);<br />
&nbsp; &nbsp; fclose($fp);<br />
}<br />
doRequest("http://localhost/20160525/1.php",array('bbb'=&gt;'test'));<br />
<br />
//ignore_user_abort(true); // 忽略客户端断开 &nbsp;<br />
//set_time_limit(0); &nbsp; &nbsp; &nbsp; // 设置执行不超时 &nbsp;<br />
<br />
<br />
?&gt;<br />
<div style="white-space:nowrap;">
	<br />
</div>