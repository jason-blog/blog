&lt;?php<br />
header('Content-type:text/html;charset=utf-8');<br />
//读取图片文件，转换成base64编码格式<br />
$image_file = './verytalk.png';<br />
$image_info = getimagesize($image_file);<br />
$base64_image_content = "data:{$image_info['mime']};base64," . chunk_split(base64_encode(file_get_contents($image_file)));<br />
<br />
//保存base64字符串为图片<br />
//匹配出图片的格式<br />
if (preg_match('/^(data:\s*image\/(\w+);base64,)/', $base64_image_content, $result)){<br />
&nbsp; $type = $result[2];<br />
&nbsp; $new_file = "./test.{$type}";<br />
&nbsp; if (file_put_contents($new_file, base64_decode(str_replace($result[1], '', $base64_image_content)))){<br />
&nbsp; &nbsp; echo '新文件保存成功：', $new_file;<br />
&nbsp; }<br />
<br />
}<br />
?&gt;<br />