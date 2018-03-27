<p style="font-family:tahoma,arial,宋体;font-size:14px;line-height:25.2px;margin-top:0px;margin-bottom:0px;padding-top:5px;padding-bottom:5px;">
	<strong>设置端口转发</strong>&nbsp;
</p>
<p style="margin-top:0px;margin-bottom:0px;padding-top:5px;padding-bottom:5px;">
	<br />
</p>
<div style="text-align:justify;font-family:tahoma,arial,宋体;font-size:14px;line-height:25.2px;">
	<span style="white-space:pre;"></span>1. 打开conf/httpd.conf文件；&nbsp;
</div>
<div style="text-align:justify;font-family:tahoma,arial,宋体;font-size:14px;font-weight:bold;line-height:25.2px;">
	<span style="white-space:pre;"></span>2. 找到Listen，将后面的端口改成自己需要的，如80，也可以另写一行来监听多个端口；&nbsp;
</div>
<div style="text-align:justify;">
	<span style="white-space:pre;"></span>3. 将
</div>
<div style="text-align:justify;">
	<span style="white-space:pre;"></span>#Include conf/extra/httpd-vhosts.conf
</div>
<div style="text-align:justify;">
	<strong><span style="white-space:pre;"></span>#LoadModule proxy_module modules/mod_proxy.so</strong><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;font-weight:bold;line-height:25.2px;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;font-weight:bold;line-height:25.2px;white-space:pre;"></span><strong>#LoadModule
 proxy_http_module modules/mod_proxy_http.so</strong><br />
</div>
<div style="text-align:justify;">
	<span style="white-space:pre;"></span>前面的#去掉
</div>
<strong></strong> 
<div style="text-align:justify;">
	<span style="white-space:pre;"></span>4. 打开conf/extra/httpd-vhost.conf文件，在下面加入以下代码&nbsp;
</div>
<div class="dp-highlighter" id="" style="font-family:Monaco, &quot;font-size:14px;font-weight:bold;line-height:25.2px;width:679px;overflow:auto;margin-left:9px;padding:1px;word-break:break-all;">
	<div class="bar">
		<div class="tools" style="text-align:justify;padding:3px;margin:0px;">
			&nbsp;
		</div>
	</div>
	<ol start="1" class="dp-j" style="font-size:1em;line-height:1.4em;margin:0px 0px 1px;padding:2px 0px;border:1px solid #D1D7DC;color:#2B91AF;">
		<li style="text-align:justify;font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left-width:1px;border-left-style:solid;border-left-color:#D1D7DC;line-height:18px;background-color:#FAFAFA;">
			&lt;VirtualHost&nbsp;*:80&gt;（*表示监听所有IP，后面的80表示监听从哪个端口发来的数据）&nbsp;&nbsp;
		</li>
		<li style="text-align:justify;font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left-width:1px;border-left-style:solid;border-left-color:#D1D7DC;line-height:18px;background-color:#FAFAFA;">
			ServerAdmin&nbsp;XXX@xxx.cn&nbsp;（这里是管理员的邮件地址）&nbsp;&nbsp;
		</li>
		<li style="text-align:justify;font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left-width:1px;border-left-style:solid;border-left-color:#D1D7DC;line-height:18px;background-color:#FAFAFA;">
			ServerName&nbsp;www.xx.cn&nbsp;（这里就是你的域名地址）&nbsp;&nbsp;
		</li>
		<li style="text-align:justify;font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left-width:1px;border-left-style:solid;border-left-color:#D1D7DC;line-height:18px;background-color:#FAFAFA;">
			&nbsp;&nbsp;&nbsp;&nbsp;ProxyPass&nbsp;/&nbsp;http://www.xx.cn:8100/&nbsp;（这里就是你要转发到的地址，就是Tomcat中的地址）&nbsp;&nbsp;
		</li>
		<li style="text-align:justify;font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left-width:1px;border-left-style:solid;border-left-color:#D1D7DC;line-height:18px;background-color:#FAFAFA;">
			&nbsp;&nbsp;&nbsp;&nbsp;ProxyPassReverse&nbsp;/&nbsp;http://www.xx.cn:8100/&nbsp;（指令用于处理重定向时的转发）&nbsp;&nbsp;
		</li>
		<li style="text-align:justify;font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left-width:1px;border-left-style:solid;border-left-color:#D1D7DC;line-height:18px;background-color:#FAFAFA;">
			&nbsp;&nbsp;&nbsp;&nbsp;ErrorLog&nbsp;"logs/www.xx.cn/error.log"&nbsp;（日志位置）&nbsp;&nbsp;
		</li>
		<li style="text-align:justify;font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left-width:1px;border-left-style:solid;border-left-color:#D1D7DC;line-height:18px;background-color:#FAFAFA;">
			&nbsp;&nbsp;&nbsp;&nbsp;CustomLog&nbsp;"logs/www.xx.cn/access.log"&nbsp;common&nbsp;&nbsp;（重复一下）&nbsp;&nbsp;
		</li>
		<li style="text-align:justify;font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left-width:1px;border-left-style:solid;border-left-color:#D1D7DC;line-height:18px;background-color:#FAFAFA;">
			&lt;/VirtualHost&gt;&nbsp;
		</li>
	</ol>
</div>