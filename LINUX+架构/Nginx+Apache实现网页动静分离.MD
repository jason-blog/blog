<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	本文使用nginx处理静态文件和做负载反向代理，apache负责处理php动态页面，通过简单的配置实现动静分离。
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	由于apache处理静态页面的效率不高，而一般网站大多数的内容都是静态文件（如图片、html、css、js等），经过nginx前端的反向代理加速和过滤，后端apache处理请求的压力便可大大减少，只需负责处理动态内容就可以了。在性能与稳定性的权衡下，使用nginx+apache搭配便可让它们在各自擅长的领域大展拳脚。
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	<strong>推荐阅读：</strong>
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	Nginx+Tomcat实现动静分离架构实现&nbsp;<a href="http://www.linuxidc.com/Linux/2013-06/85780.htm" style="color:#B32BD5;">http://www.linuxidc.com/Linux/2013-06/85780.htm</a>
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	Nginx+Tomcat实现反向代理与动静分离&nbsp;<a href="http://www.linuxidc.com/Linux/2013-01/78309.htm" style="color:#B32BD5;">http://www.linuxidc.com/Linux/2013-01/78309.htm</a>
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	Nginx动静分离经典案例配置&nbsp;<a href="http://www.linuxidc.com/Linux/2012-12/76457.htm" style="color:#B32BD5;">http://www.linuxidc.com/Linux/2012-12/76457.htm</a>
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	Nginx+Tomcat动静分离搭建&nbsp;<a href="http://www.linuxidc.com/Linux/2012-10/72855.htm" style="color:#B32BD5;">http://www.linuxidc.com/Linux/2012-10/72855.htm</a>
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	<strong><span style="font-size:16px;">一、安装与配置Apache</span></strong>
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	<strong>1.&nbsp;</strong><strong>安装Apache2</strong>
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	<span style="background-color:#CCCCCC;"># sudo yum install httpd</span>&nbsp;
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	<strong>2. 修改配置文件</strong>
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	修改服务端口号，将80端口改成8080。<br />
<span style="line-height:1.5;background-color:#CCCCCC;font-size:10pt;"># sudo vim&nbsp;</span><span style="line-height:1.5;background-color:#CCCCCC;font-size:10pt;">/etc/httpd/conf/httpd.conf<br />
</span>
</p>
<table border="1" cellspacing="0" cellpadding="2" style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;background-color:#FAFAFC;width:753px;">
	<tbody>
		<tr>
			<td style="font-size:14px;word-wrap:break-word;font-family:tahoma, 宋体;line-height:1.6;">
				...<br />
				<p>
					#Listen 12.34.56.78:80<br />
<span style="line-height:1.5;">Listen 8080<br />
</span><span style="line-height:1.5;">...</span>
				</p>
			</td>
		</tr>
	</tbody>
</table>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	<strong>3.&nbsp;</strong><strong>启动服务并设置开机自启动</strong>
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	<span style="line-height:1.5;background-color:#CCCCCC;font-size:10pt;"># sudo&nbsp;</span><span style="line-height:1.5;background-color:#CCCCCC;font-size:10pt;">/etc/init.d/httpd start<br />
# sudo /sbin/chkconfig&nbsp;httpd&nbsp;on</span>
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	<strong><span style="font-size:16px;">二、安装与配置Nginx</span></strong>
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	<strong>1. 启用 EPEL repo源</strong>
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	<span style="line-height:1.5;font-size:10pt;">如果使用的<a href="http://www.linuxidc.com/topicnews.aspx?tid=14" target="_blank" title="CentOS" style="color:#B32BD5;">CentOS</a>&nbsp;5.x版本，安装以下repo源：</span><br />
<span style="background-color:#CCCCCC;"># sudo rpm -Uvh http://dl.<a href="http://www.linuxidc.com/topicnews.aspx?tid=5" target="_blank" title="Fedora" style="color:#B32BD5;">Fedora</a>project.org/pub/epel/5/i386/epel-release-5-4.noarch.rpm</span><br />
如果使用的CentOS 6.x版本，安装以下repo源：<br />
<span style="line-height:1.5;background-color:#CCCCCC;font-size:10pt;"># sudo rpm -Uvh http://dl.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm</span>
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	<span style="line-height:1.5;font-size:10pt;"><strong>2.&nbsp;</strong></span><span style="line-height:1.5;font-size:10pt;"><strong>安装nginx</strong></span>
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	<span style="background-color:#CCCCCC;"># sudo yum install nginx</span>
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	&nbsp;
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	<strong>3. 修改配置文件</strong>
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	<span style="line-height:1.5;font-size:10pt;">主配置文件/etc/nginx/nginx.conf无需做太大改动，只需将worker_processes设置成与机器CPU核数相等即可（如CPU数为1，则worker_processes 1;）。<br />
<span style="background-color:#CCCCCC;"># sudo vim /etc/nginx/conf.d/virtual.conf</span><br />
</span>
</p>
<table border="1" cellspacing="0" cellpadding="2" style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;background-color:#FAFAFC;width:753px;">
	<tbody>
		<tr>
			<td style="font-size:14px;word-wrap:break-word;font-family:tahoma, 宋体;line-height:1.6;">
				server {<br />
listen 80;<br />
server_name 192.168.85.83;<br />
root /var/www/html;<br />
index index.html index.htm index.php;<br />
location ~ \.(php)?$ {<br />
proxy_set_header Host $host;<br />
proxy_set_header X-Real-IP $remote_addr;<br />
proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;<br />
proxy_pass http://127.0.0.1:8080;<br />
}<br />
location ~ .*.(htm|html|gif|jpg|jpeg|png|bmp|swf|ioc|rar|zip|txt|flv|mid|doc|ppt|pdf|xls|mp3|wma)$ {<br />
expires 15d;<br />
}<br />
location ~ .*.(js|css)?$ {<br />
expires 1h;<br />
}<br />
}
			</td>
		</tr>
	</tbody>
</table>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	<br />
<strong>4. 启动服务并设置开机自启动</strong>
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	<span style="line-height:1.5;font-size:10pt;"><span style="background-color:#CCCCCC;"># sudo /etc/init.d/nginx start</span><br />
<span style="background-color:#CCCCCC;"># sudo /sbin/chkconfig nginx on</span></span>
</p>