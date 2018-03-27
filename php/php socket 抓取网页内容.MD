&lt;?php<br />
<br />
<br />
function GETBySocket($URL, $port=80) {<br />
&nbsp; &nbsp; //get host from url<br />
&nbsp; &nbsp; preg_match('/\/\/.*\//sU',$URL,$host_array);<br />
&nbsp; &nbsp; if(!$host_array[0]) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; $URL.='/';<br />
&nbsp; &nbsp; &nbsp; &nbsp; preg_match('/\/\/.*\//sU',$URL,$host_array);<br />
&nbsp; &nbsp; }<br />
&nbsp; &nbsp; $host=substr($host_array[0],2,-1);<br />
&nbsp; &nbsp; //connect<br />
&nbsp; &nbsp; $fp = stream_socket_client("$host:$port", $errcode, $errstr, 1);// or die("get ". $host ." failed");<br />
&nbsp; &nbsp; //<br />
&nbsp; &nbsp; $header = "GET ". $URL. " HTTP/1.1\r\n";<br />
&nbsp; &nbsp; $header .= "Accept: */*\r\n";<br />
&nbsp; &nbsp; $header .= "Accept-Language: zh-cn\r\n";<br />
&nbsp; &nbsp; //$header .= "HTTP_CONNECTION: Keep-Alive\r\n";<br />
&nbsp; &nbsp; $header .= "HTTP_ACCEPT: text/xml,application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5\r\n";<br />
&nbsp; &nbsp; $header .= "HTTP_ACCEPT_CHARSET: gbk,*,utf-8\r\n";<br />
&nbsp; &nbsp; //$header .= "Accept-Encoding: gzip, deflate\r\n";<br />
&nbsp; &nbsp; $header .= "User-Agent: Mozilla/4.0(compatible; MSIE 6.0; Windows NT 5.1;)\r\n";<br />
&nbsp; &nbsp; $header .= "Host: ". $host ."\r\n";<br />
&nbsp; &nbsp; //$header .= "Connection: Keep-Alive\r\n";<br />
&nbsp; &nbsp; //$header .= "Cookie: cnzz02=2; rtime=1; ltime=1148456424859; cnzz_eid=56601755-\r\n\r\n";<br />
&nbsp; &nbsp; $header .= "Connection: close\r\n\r\n";<br />
&nbsp; &nbsp; stream_socket_sendto($fp, $header);<br />
&nbsp; &nbsp; ///////////////////$content=stream_socket_recvfrom($fp,1000,STREAM_PEEK);<br />
&nbsp; &nbsp; $content=stream_get_contents($fp);<br />
&nbsp; &nbsp; fclose($fp);<br />
&nbsp; &nbsp; $position_header=strpos($content, "\r\n\r\n");<br />
&nbsp; &nbsp; if (stripos(substr($content, 0 ,$position_header), 'Transfer-Encoding: chunked')) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; return substr($content, strpos($content, "\r\n", $position_header +4)+2);<br />
&nbsp; &nbsp; } else {<br />
&nbsp; &nbsp; &nbsp; &nbsp; return substr($content, $position_header +4);<br />
&nbsp; &nbsp; }<br />
<br />
}<br />
echo GETBySocket('http://www.qq.com/');<br />