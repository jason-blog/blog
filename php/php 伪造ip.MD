<pre class="prettyprint lang-js linenums">$ch = curl_init();
$url = "http://www.ddd.com";
$header = array(
    //'CLIENT-IP:58.68.44.61',
   'X-FORWARDED-FOR:58.68.44.61,',
);
curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, false); //不验证证书
curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, false); //不验证证书
curl_setopt($ch, CURLOPT_URL, $url);
curl_setopt($ch, CURLOPT_HTTPHEADER, $header);
curl_setopt($ch, CURLOPT_RETURNTRANSFER,true);
$page_content = curl_exec($ch);
curl_close($ch);
echo $page_content;
</pre>