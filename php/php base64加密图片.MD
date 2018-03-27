&lt;?php<br />
header('Content-Type: text/html; charset=UTF-8');<br />
$switch=1;<br />
<br />
if($switch==1){<br />
$file = "1.jpg";<br />
$type = getimagesize($file);<br />
$fp = fopen($file,"r") or die("Can't open file");<br />
echo $file_content = urlencode(base64_encode(fread($fp,filesize($file))));<br />
<br />
fclose($fp);<br />
<br />
}else{<br />
$code=@base64_decode(urldecode(trim($_REQUEST['code'])));<br />
&nbsp; // &nbsp; &nbsp;file_put_contents('1.jpg', $aa);<br />
if($code){<br />
&nbsp; &nbsp;downfile('1.jpg',$code);<br />
&nbsp;}<br />
}<br />
<br />
function downfile($filename,$code){<br />
&nbsp; &nbsp; header( "Content-type: &nbsp; application/octet-stream ");<br />
&nbsp; &nbsp; header( "Accept-Ranges: &nbsp; bytes ");<br />
&nbsp; &nbsp; header( "Content-Disposition: &nbsp; attachment; &nbsp; filename=$filename");<br />
&nbsp; &nbsp; header( "Expires: &nbsp; 0 ");<br />
&nbsp; &nbsp; header( "Cache-Control: &nbsp; must-revalidate, &nbsp; post-check=0, &nbsp; pre-check=0 ");<br />
&nbsp; &nbsp; header( "Pragma: &nbsp; public ");<br />
&nbsp; &nbsp; echo &nbsp;$code;<br />
}<br />
?&gt;&nbsp;<br />
&lt;?php if( $switch !=1 ){ ?&gt;<br />
&lt;form action='' method='post'&gt;<br />
&lt;textarea name='code'&gt;<br />
&lt;/textarea&gt;<br />
&nbsp;&lt;input type='submit' value='确定'/&gt;<br />
&nbsp;&lt;/form&gt;<br />
&lt;?php } ?&gt;<br />
<div style="white-space:nowrap;">
	<br />
</div>