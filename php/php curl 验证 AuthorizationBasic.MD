<p>
	http://www.cnblogs.com/hzijone/p/5802428.html
</p>
<p>
	&lt;?php
</p>
<br />
$url="https://api.mailgun.net/v3/address/validate";<br />
&nbsp; &nbsp; //?api_key=pubkey-87c027fab3ac7eb22b752aaac6054b5b";<br />
<br />
<br />
&nbsp; &nbsp; &nbsp; &nbsp;$ch = curl_init($url);<br />
&nbsp; &nbsp; &nbsp; &nbsp;<br />
&nbsp; &nbsp; &nbsp; $data=http_build_query(array('address'=&gt;"1123123@qq.com"));<br />
&nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; $Basic=base64_encode("api".":"."pubkey-dddddd");<br />
&nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; $H=array(<br />
&nbsp; &nbsp; &nbsp; &nbsp;"Authorization:Basic ".$Basic,<br />
&nbsp; &nbsp; &nbsp;// &nbsp;"Content-Type:application/json",<br />
&nbsp; &nbsp; &nbsp; &nbsp;"Cache-Control:no-cache"<br />
&nbsp; &nbsp;);<br />
&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; curl_setopt($ch, CURLOPT_CUSTOMREQUEST, "GET");<br />
&nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp;curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, false); //不验证证书<br />
&nbsp; &nbsp; &nbsp; &nbsp;curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, false); //不验证证书<br />
&nbsp; &nbsp; &nbsp; &nbsp;curl_setopt($ch, CURLOPT_HTTP_VERSION , CURL_HTTP_VERSION_1_1);<br />
&nbsp; &nbsp; &nbsp; &nbsp;curl_setopt($ch, CURLOPT_POSTFIELDS, $data);<br />
&nbsp; &nbsp; &nbsp; &nbsp;curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);<br />
&nbsp; &nbsp; &nbsp;// &nbsp;curl_setopt($ch, CURLOPT_USERPWD, "api:pubkey-87c027fab3ac7eb22b752aaac6054b5b");<br />
&nbsp; &nbsp; &nbsp; &nbsp;curl_setopt($ch, CURLOPT_HTTPHEADER, $H );<br />
&nbsp; &nbsp; &nbsp; &nbsp;$result = curl_exec($ch);<br />
&nbsp; &nbsp; &nbsp; &nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp;return $result;<br />