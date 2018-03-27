<p>
	=======================&nbsp;socket server&nbsp;========================
</p>
<p>
	<br />
</p>
<p>
	&lt;?php
</p>
header("Content-type: text/html; charset=utf-8");<br />
//phpinfo();<br />
//确保在连接客户端时不会超时<br />
set_time_limit(0);<br />
$ip = '127.0.0.1';<br />
$port = 1935;<br />
/*<br />
&nbsp;+-------------------------------<br />
&nbsp;* &nbsp; &nbsp;@socket通信整个过程<br />
&nbsp;+-------------------------------<br />
&nbsp;* &nbsp; &nbsp;@socket_create<br />
&nbsp;* &nbsp; &nbsp;@socket_bind<br />
&nbsp;* &nbsp; &nbsp;@socket_listen<br />
&nbsp;* &nbsp; &nbsp;@socket_accept<br />
&nbsp;* &nbsp; &nbsp;@socket_read<br />
&nbsp;* &nbsp; &nbsp;@socket_write<br />
&nbsp;* &nbsp; &nbsp;@socket_close<br />
&nbsp;+--------------------------------<br />
&nbsp;*/<br />
/*---------------- &nbsp; &nbsp;以下操作都是手册上的 &nbsp; &nbsp;-------------------*/<br />
if(($sock = socket_create(AF_INET,SOCK_STREAM,SOL_TCP)) &lt; 0) {<br />
&nbsp; &nbsp; echo "socket_create() 失败的原因是:".socket_strerror($sock)."\n";<br />
}<br />
if(($ret = socket_bind($sock,$ip,$port)) &lt; 0) {<br />
&nbsp; &nbsp; echo "socket_bind() 失败的原因是:".socket_strerror($ret)."\n";<br />
}<br />
if(($ret = socket_listen($sock,4)) &lt; 0) {<br />
&nbsp; &nbsp; echo "socket_listen() 失败的原因是:".socket_strerror($ret)."\n";<br />
}<br />
$count = 0;<br />
do {<br />
&nbsp; &nbsp; if (($msgsock = socket_accept($sock)) &lt; 0) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; echo "socket_accept() failed: reason: " . socket_strerror($msgsock) . "\n";<br />
&nbsp; &nbsp; &nbsp; &nbsp; break;<br />
&nbsp; &nbsp; } else {<br />
<br />
&nbsp; &nbsp; &nbsp; &nbsp; //发到客户端<br />
&nbsp; &nbsp; &nbsp; &nbsp; $msg ="测试成功！\n".time();<br />
&nbsp; &nbsp; &nbsp; &nbsp; socket_write($msgsock, $msg, strlen($msg));<br />
<br />
&nbsp; &nbsp; &nbsp; &nbsp; echo "测试成功了啊\n";<br />
&nbsp; &nbsp; &nbsp; &nbsp; $buf = socket_read($msgsock,8192);<br />
<br />
<br />
&nbsp; &nbsp; &nbsp; &nbsp; $talkback = "收到的信息:$buf\n";<br />
&nbsp; &nbsp; &nbsp; &nbsp; echo $talkback;<br />
<br />
&nbsp; &nbsp; &nbsp; &nbsp; if(++$count &gt;= 5){<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; break;<br />
&nbsp; &nbsp; &nbsp; &nbsp; };<br />
&nbsp; &nbsp; }<br />
&nbsp; &nbsp; //echo $buf;<br />
&nbsp; &nbsp; socket_close($msgsock);<br />
} while (true);<br />
<p>
	socket_close($sock);
</p>
<p>
	<span style="white-space:normal;">=======================&nbsp;</span><span style="white-space:normal;">socket server&nbsp;</span><span style="white-space:normal;">========================</span> 
</p>
<p>
	<span style="white-space:normal;">=======================&nbsp;</span><span style="white-space:normal;">socket client&nbsp;</span><span style="white-space:normal;">========================</span> 
</p>
<p>
	&lt;?php<br />
header("Content-type: text/html; charset=utf-8");<br />
<br />
error_reporting(E_ALL);<br />
set_time_limit(0);<br />
echo "&lt;h2&gt;TCP/IP Connection&lt;/h2&gt;\n";<br />
$port = 1935;<br />
$ip = "127.0.0.1";<br />
/*<br />
&nbsp;+-------------------------------<br />
&nbsp;* &nbsp; &nbsp;@socket连接整个过程<br />
&nbsp;+-------------------------------<br />
&nbsp;* &nbsp; &nbsp;@socket_create<br />
&nbsp;* &nbsp; &nbsp;@socket_connect<br />
&nbsp;* &nbsp; &nbsp;@socket_write<br />
&nbsp;* &nbsp; &nbsp;@socket_read<br />
&nbsp;* &nbsp; &nbsp;@socket_close<br />
&nbsp;+--------------------------------<br />
&nbsp;*/<br />
$socket = socket_create(AF_INET, SOCK_STREAM, SOL_TCP);<br />
if ($socket &lt; 0) {<br />
&nbsp; &nbsp; echo "socket_create() failed: reason: " . socket_strerror($socket) . "\n";<br />
}else {<br />
&nbsp; &nbsp; echo "OK.\n";<br />
}<br />
echo "试图连接 '$ip' 端口 '$port'...\n";<br />
$result = socket_connect($socket, $ip, $port);<br />
if ($result &lt; 0) {<br />
&nbsp; &nbsp; echo "socket_connect() failed.\nReason: ($result) " . socket_strerror($result) . "\n";<br />
}else {<br />
&nbsp; &nbsp; echo "连接OK\n";<br />
}<br />
$in = "Ho\r\n";<br />
$in .= "first blood\r\n";<br />
$out = '';<br />
if(!socket_write($socket, $in, strlen($in))) {<br />
&nbsp; &nbsp; echo "socket_write() failed: reason: " . socket_strerror($socket) . "\n";<br />
}else {<br />
&nbsp; &nbsp; echo "发送到服务器信息成功！\n";<br />
&nbsp; &nbsp; echo "发送的内容为:&lt;font color='red'&gt;$in&lt;/font&gt; &lt;br&gt;";<br />
}<br />
while($out = socket_read($socket, 8192)) {<br />
&nbsp; &nbsp; echo "接收服务器回传信息成功！\n";<br />
&nbsp; &nbsp; echo "接受的内容为:",$out;<br />
}<br />
echo "关闭SOCKET...\n";<br />
socket_close($socket);<br />
echo "关闭OK\n";
</p>
<p>
	<span style="white-space:normal;">=======================&nbsp;</span><span style="white-space:normal;">socket client&nbsp;</span><span style="white-space:normal;">========================</span><span style="white-space:normal;"></span> 
</p>
<p>
	<span style="white-space:normal;">======================= html 页面 ==========================</span>
</p>
<p>
	<span style="white-space:normal;">&lt;!DOCTYPE html&gt;<br />
&lt;html&gt;<br />
&lt;head&gt;<br />
&lt;meta http-equiv="Access-Control-Allow-Origin" content="true"&gt;<br />
&lt;script src="http://cdn.socket.io/socket.io-1.3.0.js"&gt;&lt;/script&gt;<br />
&lt;script&gt;<br />
<br />
&nbsp; &nbsp; var socket = io.connect("http://127.0.0.1:1935");<br />
&nbsp; &nbsp; socket.on('message', function(d){<br />
&nbsp; &nbsp; &nbsp; &nbsp;console.log(d);<br />
&nbsp; &nbsp; });<br />
&nbsp;&nbsp;<br />
&lt;/script&gt;<br />
<br />
&lt;head/&gt;<br />
&lt;/html&gt;<br />
<br />
</span>
</p>
<p>
	<span style="white-space:normal;"><span style="white-space:normal;">======================= html 页面 ==========================</span><br />
</span>
</p>
<p>
	<span style="white-space:normal;"><br />
</span>
</p>