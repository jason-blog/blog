&lt;?php<br />
header('Content-type:text/html;charset=utf-8');<br />
//读取图片文件，转换成base64编码格式<br />
$image_file = './verytalk.png';<br />
$image_info = getimagesize($image_file);<br />
$base64_image_content = "data:{$image_info['mime']};base64," . chunk_split(base64_encode(file_get_contents($image_file)));<br />
?&gt;<br />
<br />
<br />
<br />
<br />
<br />
&lt;html&gt;<br />
&lt;head&gt;<br />
&lt;meta http-equiv="Content-Type" content="text/html;charset=utf-8"&gt;<br />
<br />
&lt;link rel="apple-touch-icon" href="&lt;?php echo $base64_image_content;?&gt;" /&gt;<br />
&lt;/head&gt;<br />
<br />
<br />
<br />
&lt;/html&gt;<br />