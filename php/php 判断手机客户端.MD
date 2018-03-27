<p style="text-indent:2em;">
	&lt;?php<br />
<br />
<br />
function isMobile()<br />
{<br />
&nbsp; &nbsp; // 如果有HTTP_X_WAP_PROFILE则一定是移动设备<br />
&nbsp; &nbsp; if (isset ($_SERVER['HTTP_X_WAP_PROFILE']))<br />
&nbsp; &nbsp; {<br />
&nbsp; &nbsp; &nbsp; &nbsp; return true;<br />
&nbsp; &nbsp; }<br />
&nbsp; &nbsp; // 如果via信息含有wap则一定是移动设备,部分服务商会屏蔽该信息<br />
&nbsp; &nbsp; if (isset ($_SERVER['HTTP_VIA']))<br />
&nbsp; &nbsp; {<br />
&nbsp; &nbsp; &nbsp; &nbsp; // 找不到为flase,否则为true<br />
&nbsp; &nbsp; &nbsp; &nbsp; return stristr($_SERVER['HTTP_VIA'], "wap") ? true : false;<br />
&nbsp; &nbsp; }<br />
&nbsp; &nbsp; // 脑残法，判断手机发送的客户端标志,兼容性有待提高<br />
&nbsp; &nbsp; if (isset ($_SERVER['HTTP_USER_AGENT']))<br />
&nbsp; &nbsp; {<br />
&nbsp; &nbsp; &nbsp; &nbsp; $clientkeywords = array ('nokia',<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'sony',<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'ericsson',<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'mot',<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'samsung',<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'htc',<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'sgh',<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'lg',<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'sharp',<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'sie-',<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'philips',<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'panasonic',<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'alcatel',<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'lenovo',<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'iphone',<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'ipod',<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'blackberry',<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'meizu',<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'android',<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'netfront',<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'symbian',<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'ucweb',<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'windowsce',<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'palm',<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'operamini',<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'operamobi',<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'openwave',<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'nexusone',<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'cldc',<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'midp',<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'wap',<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'mobile'<br />
&nbsp; &nbsp; &nbsp; &nbsp; );<br />
&nbsp; &nbsp; &nbsp; &nbsp; // 从HTTP_USER_AGENT中查找手机浏览器的关键字<br />
&nbsp; &nbsp; &nbsp; &nbsp; if (preg_match("/(" . implode('|', $clientkeywords) . ")/i", strtolower($_SERVER['HTTP_USER_AGENT'])))<br />
&nbsp; &nbsp; &nbsp; &nbsp; {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; return true;<br />
&nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; }<br />
&nbsp; &nbsp; // 协议法，因为有可能不准确，放到最后判断<br />
&nbsp; &nbsp; if (isset ($_SERVER['HTTP_ACCEPT']))<br />
&nbsp; &nbsp; {<br />
&nbsp; &nbsp; &nbsp; &nbsp; // 如果只支持wml并且不支持html那一定是移动设备<br />
&nbsp; &nbsp; &nbsp; &nbsp; // 如果支持wml和html但是wml在html之前则是移动设备<br />
&nbsp; &nbsp; &nbsp; &nbsp; if ((strpos($_SERVER['HTTP_ACCEPT'], 'vnd.wap.wml') !== false) &amp;&amp; (strpos($_SERVER['HTTP_ACCEPT'], 'text/html') === false || (strpos($_SERVER['HTTP_ACCEPT'], 'vnd.wap.wml') &lt; strpos($_SERVER['HTTP_ACCEPT'], 'text/html'))))<br />
&nbsp; &nbsp; &nbsp; &nbsp; {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; return true;<br />
&nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; }<br />
&nbsp; &nbsp; return false;<br />
}<br />
</p>