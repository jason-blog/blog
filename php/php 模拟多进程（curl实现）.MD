&lt;?php<br />
<br />
header('Content-Type: text/html; charset=UTF-8');<br />
<br />
<br />
<br />
&nbsp;function curlJson($url,$data='',$type='POST'){<br />
&nbsp; &nbsp; $data_string = json_encode($data);<br />
&nbsp; &nbsp; //echo $data_string;<br />
&nbsp; &nbsp; $ch = curl_init($url);<br />
&nbsp; &nbsp; curl_setopt($ch, CURLOPT_CUSTOMREQUEST, $type);<br />
&nbsp; &nbsp; //curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, false); //不验证证书<br />
&nbsp; &nbsp; //curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, false); //不验证证书<br />
&nbsp; &nbsp; curl_setopt($ch, CURLOPT_NOSIGNAL,true);//支持毫秒级别超时设置<br />
&nbsp; &nbsp; curl_setopt($ch, CURLOPT_TIMEOUT_MS,1); &nbsp;//超时毫秒，cURL 7.16.2中被加入。从PHP 5.2.3起<br />
&nbsp; &nbsp; //curl_setopt($ch, CURLOPT_TIMEOUT,1);<br />
&nbsp; &nbsp; curl_setopt($ch, CURLOPT_HTTP_VERSION , CURL_HTTP_VERSION_1_1);<br />
&nbsp; &nbsp; curl_setopt($ch, CURLOPT_POSTFIELDS, $data_string);<br />
&nbsp; &nbsp; curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);<br />
&nbsp; &nbsp; // curl_setopt($ch, CURLOPT_HTTPHEADER, $H );<br />
&nbsp; &nbsp; $result = curl_exec($ch);<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; return $result;<br />
}<br />
<br />
<br />
$stime = microtime(true);<br />
<br />
<br />
<br />
curlJson("http://localhost/20151208/1.php");<br />
<br />
<br />
$etime = microtime(true);<br />
echo &nbsp;$etime - $stime;<br />
echo '&lt;/br/&gt;';<br />
echo '11111';<br />
//ignore_user_abort(true); // 忽略客户端断开 &nbsp;<br />
//set_time_limit(0); &nbsp; &nbsp; &nbsp; // 设置执行不超时&nbsp;<br />