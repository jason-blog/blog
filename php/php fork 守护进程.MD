&lt;?php&nbsp;<br />
<br />
define('FILE', dirname(__FILE__).'/');<br />
class daemon{<br />
&nbsp; &nbsp; public $pidFileLocation= 'daemon.pid';<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; public $file;<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp;<br />
&nbsp; &nbsp; public function __construct(){<br />
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; set_time_limit(0);<br />
&nbsp; &nbsp; &nbsp; &nbsp; $this-&gt;pidFileLocation=FILE.$this-&gt;pidFileLocation;<br />
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; file_put_contents($this-&gt;pidFileLocation,'');<br />
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; $this-&gt;_logMessage("DAEMON START ...");<br />
&nbsp; &nbsp; &nbsp; &nbsp;// if(trim(file_get_contents(FILE.'./daemon.ctrl')) == '1')<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; //register_shutdown_function(array(&amp;$this, 'restart'));<br />
&nbsp; &nbsp; }<br />
<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; public function daemon(){<br />
&nbsp; &nbsp; &nbsp; &nbsp; $this-&gt;_logMessage('START FUNCTION START...');<br />
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; while (trim(file_get_contents(FILE.'daemon.ctrl')) == '1'){<br />
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; // &nbsp;ob_start();<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; $this-&gt;getData();<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; // &nbsp;$text = ob_get_clean();<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;// &nbsp; echo $text;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; file_put_contents('DAEMON_STATUS.S',date("Y-m-d H:i:s").'\n');<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; $this-&gt;_fork();<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; sleep(15);<br />
&nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; }<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; public function restart(){<br />
&nbsp; &nbsp; &nbsp; &nbsp; file_put_contents($this-&gt;pidFileLocation,'');<br />
&nbsp; &nbsp; &nbsp; &nbsp; $this-&gt;_logMessage('restart... beginPID: '.$this-&gt;pidFileLocation.' ');<br />
&nbsp; &nbsp; &nbsp; &nbsp; $this-&gt;daemon();<br />
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; }<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; /**<br />
&nbsp; &nbsp; &nbsp;* Forks process<br />
&nbsp; &nbsp; &nbsp;*<br />
&nbsp; &nbsp; &nbsp;* @return bool<br />
&nbsp; &nbsp; &nbsp;*/<br />
&nbsp; &nbsp; private function _fork() {<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; $pid = pcntl_fork();<br />
&nbsp; &nbsp; &nbsp; &nbsp; if ($pid == -1) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; register_shutdown_function(array(&amp;$this, 'restart'));<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; $this-&gt;_logMessage('pcntl_fork Could not start');<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; return false;<br />
&nbsp; &nbsp; &nbsp; &nbsp; } elseif ($pid) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; $this-&gt;_logMessage('pcntl_fork kill this pid');<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; exit();<br />
&nbsp; &nbsp; &nbsp; &nbsp; } else {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; $this-&gt;_logMessage('start pcntl_fork this pid');<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; $pid=posix_getpid();<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; if (!$fp = fopen($this-&gt;pidFileLocation, 'w')) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; $this-&gt;_logMessage('Could not write to PID file');<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; return false;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; } else {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; fputs($fp,$pid);<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; fclose($fp);<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; return true;<br />
&nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; }<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; public function _logMessage($data){<br />
&nbsp; &nbsp; &nbsp; &nbsp; $time=date("Y-m-d H:i:s");<br />
&nbsp; &nbsp; &nbsp; &nbsp; $text="\n\n&lt;TIME&gt;$time&lt;/TIME&gt;\n";<br />
&nbsp; &nbsp; &nbsp; &nbsp; file_put_contents(FILE.'deamon.log',$text.$data.'\n \n',8);<br />
&nbsp; &nbsp; }<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; public function getData(){<br />
&nbsp; &nbsp; &nbsp; &nbsp; echo "======================getdata============================= \n";<br />
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; /**<br />
&nbsp; &nbsp; &nbsp;* &nbsp;设置货币<br />
&nbsp; &nbsp; */<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; (empty($argv[1]))?$currencyCode="USD":$currencyCode=$argv[1];<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; $url = 'https://www.ss.com;<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; $files=dirname(__FILE__);<br />
&nbsp; &nbsp; $files=$files."/jackpotsdate.html";<br />
&nbsp; &nbsp; $json=$this-&gt;send_post($url);<br />
&nbsp; &nbsp; $data =json_decode( $json,true);<br />
&nbsp; &nbsp; if($data){<br />
&nbsp; &nbsp; &nbsp; &nbsp; $xmlData=array();<br />
&nbsp; &nbsp; &nbsp; &nbsp; $oData=array();<br />
&nbsp; &nbsp; &nbsp; &nbsp; foreach ($data as $key=&gt;$row){<br />
&nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; &nbsp; $data= $this-&gt;toXml(array_merge($xmlData,$oData)) ;<br />
&nbsp; &nbsp; &nbsp; &nbsp; echo '\n';<br />
&nbsp; &nbsp; &nbsp; &nbsp; echo file_put_contents($files,$data);<br />
&nbsp; &nbsp; &nbsp; &nbsp; print(' GET &nbsp;SUCCESS ! CURRENCY: '.$currencyCode);<br />
&nbsp; &nbsp; &nbsp; &nbsp; echo $time=date("Y-m-d H:i:s");<br />
&nbsp; &nbsp; &nbsp; &nbsp; echo '\n';<br />
&nbsp; &nbsp; }else{<br />
&nbsp; &nbsp; &nbsp; &nbsp; echo '\n';<br />
&nbsp; &nbsp; &nbsp; &nbsp; print("GET &nbsp;API ERROR! URL: ". $url );<br />
&nbsp; &nbsp; &nbsp; &nbsp; echo $time=date("Y-m-d H:i:s");<br />
&nbsp; &nbsp; &nbsp; &nbsp; echo '\n';<br />
&nbsp; &nbsp; &nbsp; &nbsp; syslog(LOG_ERR,"GET &nbsp;API ERROR! URL: ". $url );<br />
&nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; }<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; function send_post($url, $post_data='') {<br />
&nbsp; &nbsp; &nbsp; &nbsp; $postdata='';<br />
&nbsp; &nbsp; &nbsp; &nbsp; if($post_data)<br />
&nbsp; &nbsp; &nbsp; &nbsp; $postdata = http_build_query($post_data);<br />
&nbsp; &nbsp; &nbsp; &nbsp; $options = array(<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'http' =&gt; array(<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'method' =&gt; 'GET',//or GET<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'header' =&gt; 'Content-type:application/x-www-form-urlencoded',<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'content' =&gt; $postdata,<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'timeout' =&gt; 15 * 60 // 超时时间（单位:s）<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; )<br />
&nbsp; &nbsp; &nbsp; &nbsp; );<br />
&nbsp; &nbsp; &nbsp; &nbsp; $context = stream_context_create($options);<br />
&nbsp; &nbsp; &nbsp; &nbsp; $result = file_get_contents($url, false, $context);<br />
&nbsp; &nbsp; &nbsp; &nbsp; return $result;<br />
&nbsp; &nbsp; }<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; function curlJson($url,$data='',$H='',$type='GET'){<br />
&nbsp; &nbsp; &nbsp; &nbsp; // $data_string = json_encode($data);<br />
&nbsp; &nbsp; &nbsp; &nbsp; //echo $data_string;<br />
&nbsp; &nbsp; &nbsp; &nbsp; $ch = curl_init($url);<br />
&nbsp; &nbsp; &nbsp; &nbsp; curl_setopt($ch, CURLOPT_CUSTOMREQUEST, $type);<br />
&nbsp; &nbsp; &nbsp; &nbsp; //curl_setopt($ch, CURLOPT_NOSIGNAL,true);//支持毫秒级别超时设置<br />
&nbsp; &nbsp; &nbsp; &nbsp; //curl_setopt($ch, CURLOPT_TIMEOUT_MS,1); &nbsp;//超时毫秒，cURL 7.16.2中被加入。从PHP 5.2.3起<br />
&nbsp; &nbsp; &nbsp; &nbsp; //curl_setopt($ch, CURLOPT_TIMEOUT,1); //设置超时<br />
&nbsp; &nbsp; &nbsp; &nbsp; curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, false); //不验证证书<br />
&nbsp; &nbsp; &nbsp; &nbsp; curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, false); //不验证证书<br />
&nbsp; &nbsp; &nbsp; &nbsp; curl_setopt($ch, CURLOPT_HTTP_VERSION , CURL_HTTP_VERSION_1_1);<br />
&nbsp; &nbsp; &nbsp; &nbsp; curl_setopt($ch, CURLOPT_POSTFIELDS, $data);<br />
&nbsp; &nbsp; &nbsp; &nbsp; curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);<br />
&nbsp; &nbsp; &nbsp; &nbsp; // curl_setopt($ch, CURLOPT_HTTPHEADER, $H );<br />
&nbsp; &nbsp; &nbsp; &nbsp; $result = curl_exec($ch);<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; return $result;<br />
&nbsp; &nbsp; }<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; function curl_request($url,$post='',$cookie='', $returnCookie=0){<br />
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; return file_get_contents($url);<br />
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; $curl = curl_init();<br />
&nbsp; &nbsp; &nbsp; &nbsp; curl_setopt($curl, CURLOPT_URL, $url);<br />
&nbsp; &nbsp; &nbsp; &nbsp; curl_setopt($curl, CURLOPT_USERAGENT, 'Mozilla/5.0 (compatible; MSIE 10.0; Windows NT 6.1; Trident/6.0)');<br />
&nbsp; &nbsp; &nbsp; &nbsp; curl_setopt($curl, CURLOPT_FOLLOWLOCATION, 1);<br />
&nbsp; &nbsp; &nbsp; &nbsp; curl_setopt($curl, CURLOPT_AUTOREFERER, 1);<br />
&nbsp; &nbsp; &nbsp; &nbsp; curl_setopt($curl, CURLOPT_REFERER, "http://www.baidu.com");<br />
&nbsp; &nbsp; &nbsp; &nbsp; if($post) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; curl_setopt($curl, CURLOPT_POST, 1);<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; curl_setopt($curl, CURLOPT_POSTFIELDS, http_build_query($post));<br />
&nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; &nbsp; if($cookie) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; curl_setopt($curl, CURLOPT_COOKIE, $cookie);<br />
&nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; &nbsp; curl_setopt($curl, CURLOPT_SSL_VERIFYPEER, false); //不验证证书<br />
&nbsp; &nbsp; &nbsp; &nbsp; curl_setopt($curl, CURLOPT_SSL_VERIFYHOST, false); //不验证证书<br />
&nbsp; &nbsp; &nbsp; &nbsp; curl_setopt($curl, CURLOPT_FAILONERROR, false);<br />
&nbsp; &nbsp; &nbsp; &nbsp; curl_setopt($curl, CURLOPT_HEADER, $returnCookie);<br />
&nbsp; &nbsp; &nbsp; &nbsp; curl_setopt($curl, CURLOPT_TIMEOUT, 10);<br />
&nbsp; &nbsp; &nbsp; &nbsp; curl_setopt($curl, CURLOPT_RETURNTRANSFER, 1);<br />
&nbsp; &nbsp; &nbsp; &nbsp; $data = curl_exec($curl);<br />
&nbsp; &nbsp; &nbsp; &nbsp; if (curl_errno($curl)) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; return curl_error($curl);<br />
&nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; &nbsp; curl_close($curl);<br />
&nbsp; &nbsp; &nbsp; &nbsp; if($returnCookie){<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; list($header, $body) = explode("\r\n\r\n", $data, 2);<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; preg_match_all("/Set\-Cookie:([^;]*);/", $header, $matches);<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; $info['cookie'] &nbsp;= substr($matches[1][0], 1);<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; $info['content'] = $body;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; return $info;<br />
&nbsp; &nbsp; &nbsp; &nbsp; }else{<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; return $data;<br />
&nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; }<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; /**<br />
&nbsp; &nbsp; &nbsp;* 转xml<br />
&nbsp; &nbsp; &nbsp;* @param unknown $data<br />
&nbsp; &nbsp; &nbsp;* @param string $rootNodeName<br />
&nbsp; &nbsp; &nbsp;* @param number $stand<br />
&nbsp; &nbsp; &nbsp;* @return mixed<br />
&nbsp; &nbsp; &nbsp;*/<br />
&nbsp; &nbsp; function toXml($data,$rootNodeName = 'Counters'){<br />
&nbsp; &nbsp; &nbsp; &nbsp; $xml="&lt;?xml version='1.0' encoding='utf-8'?&gt; \n ";<br />
&nbsp; &nbsp; &nbsp; &nbsp; $xml.="&lt;Counters&gt; \n ";<br />
&nbsp; &nbsp; &nbsp; &nbsp; foreach($data as $key =&gt; $value){<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; $xml.= "&lt;Counter&gt; \n ";<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; foreach($data[$key] as $k=&gt;$r){<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; $xml.= "&lt;$k&gt;".$r."&lt;/$k&gt; \n ";<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; $xml.= "&lt;/Counter&gt; \n ";<br />
&nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; &nbsp; $xml.="&lt;/Counters&gt; \n";<br />
&nbsp; &nbsp; &nbsp; &nbsp; return $xml;<br />
&nbsp; &nbsp; }<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; function xml_parser($str){<br />
&nbsp; &nbsp; &nbsp; &nbsp; $xml_parser = xml_parser_create();<br />
&nbsp; &nbsp; &nbsp; &nbsp; if(!xml_parse($xml_parser,$str,true)){<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; xml_parser_free($xml_parser);<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; return false;<br />
&nbsp; &nbsp; &nbsp; &nbsp; }else {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; return (json_decode(json_encode(simplexml_load_string($str)),true));<br />
&nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; }<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp;&nbsp;<br />
}<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; $daemon=new daemon();<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; $daemon-&gt;daemon();<br />
?&gt;<br />