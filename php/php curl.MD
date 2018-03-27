<pre class="prettyprint lang-php linenums">&lt;?php



function curlJson($url,$data='',$H='',$type='POST'){
  // $data_string = json_encode($data);
   //echo $data_string;
   $ch = curl_init($url);
   curl_setopt($ch, CURLOPT_CUSTOMREQUEST, $type);
        //curl_setopt($ch, CURLOPT_NOSIGNAL,true);//支持毫秒级别超时设置
        //curl_setopt($ch, CURLOPT_TIMEOUT_MS,1);  //超时毫秒，cURL 7.16.2中被加入。从PHP 5.2.3起
//curl_setopt($ch, CURLOPT_TIMEOUT,1); //设置超时
   //curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, false); //不验证证书
   //curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, false); //不验证证书
   curl_setopt($ch, CURLOPT_HTTP_VERSION , CURL_HTTP_VERSION_1_1);
   curl_setopt($ch, CURLOPT_POSTFIELDS, $data);
   curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
  // curl_setopt($ch, CURLOPT_HTTPHEADER, $H );
   $result = curl_exec($ch);

   return $result;
}

echo curlJson("http://www.baishunkang.com/test.php");

file_put_contents('test.xml', microtime(true));
   /**
    * curl
    * @param unknown $url
    * @param unknown $data
    * @param unknown $H
    * @return mixed
    */
    function curlRequest($url,$data='',$type='POST'){
        if($type=='GET')
          ECHO $url=$url.'?'.http_build_query($data);
       $ch = curl_init($url);
      // curl_setopt($ch, CURLOPT_CUSTOMREQUEST, $type);
       curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, false); //不验证证书
       curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, false); //不验证证书
       curl_setopt($ch, CURLOPT_HTTP_VERSION , CURL_HTTP_VERSION_1_1);
       curl_setopt($ch, CURLOPT_POSTFIELDS, $data);
       curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
       //curl_setopt($ch, CURLOPT_HTTPHEADER, $H );
       $result = curl_exec($ch);
       
       print_r($result);
       
       return $result;
   }




/**
    * 建立请求，以表单HTML形式构造（默认）
    * @param $para_temp 请求参数数组
    * @param $method 提交方式。两个值可选：post、get
    * @param $button_name 确认按钮显示文字
    * @return 提交表单HTML文本
    */
   function buildRequestForm($url,$para_temp,$method='POST', $button_name='') {
   
       $sHtml = "&lt;form id='alipaysubmit' name='alipaysubmit' action='".$url."' method='".$method."'&gt;";
       while (list ($key, $val) = each ($para_temp)) {
           $sHtml.= "&lt;input type='hidden' name='".$key."' value='".$val."'/&gt;";
       }
        if($button_name)
        $sHtml = $sHtml."&lt;input type='submit' value='".$button_name."'&gt;&lt;/form&gt;";
        $sHtml = $sHtml."&lt;script&gt;document.forms['alipaysubmit'].submit();&lt;/script&gt;";
   
       return $sHtml;
   }
   
   
   
   //curl 代理 socket5
   function agent(){
$curl=curl_init();
curl_setopt($curl,CURLOPT_URL, "http://www.24k88.com");
//curl_setopt($curl,CURLOPT_HEADER,1);
curl_setopt($curl,CURLOPT_RETURNTRANSFER,1);
curl_setopt($curl,CURLOPT_POST,1);

///代理
curl_setopt($curl,CURLOPT_PROXYTYPE,CURLPROXY_SOCKS5);//使用了SOCKS5代理
curl_setopt($curl, CURLOPT_PROXY, "61.218.72.2:9999");
curl_setopt ($ch, CURLOPT_PROXYUSERPWD, "botulism:MwutduPBSGWwf");
///代理

//$data = array('user' =&gt; "geek", 'password' =&gt; 'fuck');
//curl_setopt($curl, CURLOPT_POSTFIELDS, $data);
//curl_setopt($curl, CURLOPT_HTTPPROXYTUNNEL, 1);如果是HTTP代理
//curl_setopt($curl, CURLOPT_COOKIEJAR, 'cookie.txt');cookie你懂的


///证书
curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, true);   // 只信任CA颁布的证书  
        curl_setopt($ch, CURLOPT_CAINFO, $cacert); // CA根证书（用来验证的网站证书是否是CA颁布）  
        curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, 2); // 检查证书中是否设置域


echo $request = curl_exec($curl);
//var_dump($request);
curl_close($curl);

   
   }



/*
*
curl_setopt($tuCurl, CURLOPT_URL, $url);
curl_setopt($tuCurl, CURLOPT_PORT , 443);
curl_setopt($tuCurl, CURLOPT_VERBOSE, 0);
curl_setopt($tuCurl, CURLOPT_HTTPHEADER, $header);
curl_setopt($tuCurl, CURLOPT_SSL_VERIFYPEER, 0);
curl_setopt($tuCurl, CURLOPT_SSL_VERIFYHOST, 0);
curl_setopt($tuCurl, CURLOPT_SSLCERT, $path . '.pem');
curl_setopt($tuCurl, CURLOPT_RETURNTRANSFER, 1);
curl_setopt($tuCurl, CURLOPT_SSLKEY, $path . '.key');

*/
?&gt;


</pre>
<br /><pre class="prettyprint lang-js linenums">&lt;?php



	 function curlJson($url,$data='',$H='',$type='POST'){
	   // $data_string = json_encode($data);
	    //echo $data_string;
		
		//$data=http_build_query($data); 有的服务器要求http query格式 so ...
	    $ch = curl_init($url);
	    curl_setopt($ch, CURLOPT_CUSTOMREQUEST, $type);
        //curl_setopt($ch, CURLOPT_NOSIGNAL,true);//支持毫秒级别超时设置
        //curl_setopt($ch, CURLOPT_TIMEOUT_MS,1);  //超时毫秒，cURL 7.16.2中被加入。从PHP 5.2.3起
		//curl_setopt($ch, CURLOPT_TIMEOUT,1); //设置超时
	    //curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, false); //不验证证书
	    //curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, false); //不验证证书
	    curl_setopt($ch, CURLOPT_HTTP_VERSION , CURL_HTTP_VERSION_1_1);
	    curl_setopt($ch, CURLOPT_POSTFIELDS, $data);
	    curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
	   // curl_setopt($ch, CURLOPT_HTTPHEADER, $H );
	    $result = curl_exec($ch);

	    return $result;
	}

	echo curlJson("http://www.baishunkang.com/test.php");
	
	file_put_contents('test.xml', microtime(true));
   /**
    * curl
    * @param unknown $url
    * @param unknown $data
    * @param unknown $H
    * @return mixed
    */
    function curlRequest($url,$data='',$type='POST'){
        if($type=='GET')
          ECHO $url=$url.'?'.http_build_query($data);
       $ch = curl_init($url);
      // curl_setopt($ch, CURLOPT_CUSTOMREQUEST, $type);
       curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, false); //不验证证书
       curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, false); //不验证证书
       curl_setopt($ch, CURLOPT_HTTP_VERSION , CURL_HTTP_VERSION_1_1);
       curl_setopt($ch, CURLOPT_POSTFIELDS, $data);
       curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
       //curl_setopt($ch, CURLOPT_HTTPHEADER, $H );
       $result = curl_exec($ch);
       
       print_r($result);
       
       return $result;
   }
	
	
	
	
	 /**
    * 建立请求，以表单HTML形式构造（默认）
    * @param $para_temp 请求参数数组
    * @param $method 提交方式。两个值可选：post、get
    * @param $button_name 确认按钮显示文字
    * @return 提交表单HTML文本
    */
   function buildRequestForm($url,$para_temp,$method='POST', $button_name='') {
   
       $sHtml = "&lt;form id='alipaysubmit' name='alipaysubmit' action='".$url."' method='".$method."'&gt;";
       while (list ($key, $val) = each ($para_temp)) {
           $sHtml.= "&lt;input type='hidden' name='".$key."' value='".$val."'/&gt;";
       }
        if($button_name)
        $sHtml = $sHtml."&lt;input type='submit' value='".$button_name."'&gt;&lt;/form&gt;";
        $sHtml = $sHtml."&lt;script&gt;document.forms['alipaysubmit'].submit();&lt;/script&gt;";
   
       return $sHtml;
   }
   
   
   
   //curl 代理 socket5
   function agent(){
		$curl=curl_init();
		curl_setopt($curl,CURLOPT_URL, "http://www.24k88.com");
		//curl_setopt($curl,CURLOPT_HEADER,1);
		curl_setopt($curl,CURLOPT_RETURNTRANSFER,1);
		curl_setopt($curl,CURLOPT_POST,1);
		
		///代理
		curl_setopt($curl,CURLOPT_PROXYTYPE,CURLPROXY_SOCKS5);//使用了SOCKS5代理
		curl_setopt($curl, CURLOPT_PROXY, "61.218.72.2:9999");
		curl_setopt ($ch, CURLOPT_PROXYUSERPWD, "botulism:MwutduPBSGWwf");
		///代理
		
		//$data = array('user' =&gt; "geek", 'password' =&gt; 'fuck');
		//curl_setopt($curl, CURLOPT_POSTFIELDS, $data);
		//curl_setopt($curl, CURLOPT_HTTPPROXYTUNNEL, 1);如果是HTTP代理
		//curl_setopt($curl, CURLOPT_COOKIEJAR, 'cookie.txt');cookie你懂的
		
		
		///证书
		curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, true);   // 只信任CA颁布的证书  
        curl_setopt($ch, CURLOPT_CAINFO, $cacert); // CA根证书（用来验证的网站证书是否是CA颁布）  
        curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, 2); // 检查证书中是否设置域
		
		
		echo $request = curl_exec($curl);
		//var_dump($request);
		curl_close($curl);

   
   }
	
	
	
	/*
	*
curl_setopt($tuCurl, CURLOPT_URL, $url);
curl_setopt($tuCurl, CURLOPT_PORT , 443);
curl_setopt($tuCurl, CURLOPT_VERBOSE, 0);
curl_setopt($tuCurl, CURLOPT_HTTPHEADER, $header);
curl_setopt($tuCurl, CURLOPT_SSL_VERIFYPEER, 0);
curl_setopt($tuCurl, CURLOPT_SSL_VERIFYHOST, 0);
curl_setopt($tuCurl, CURLOPT_SSLCERT, $path . '.pem');
curl_setopt($tuCurl, CURLOPT_RETURNTRANSFER, 1);
curl_setopt($tuCurl, CURLOPT_SSLKEY, $path . '.key');

	*/
?&gt;



</pre>