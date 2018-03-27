<span style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">【apache配置禁止访问】</span><br style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">1. 禁止访问某些文件/目录</span><br style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">增加Files选项来控制，比如要不允许访问 .inc 扩展名的文件，保护php类库：</span><br style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#362E2B;font-size:14px;white-space:normal;background-color:#FFFFFF;font-family:&quot;">&lt;Files ~ "\.inc$"&gt;<br />
&nbsp;&nbsp; Order allow,deny<br />
&nbsp;&nbsp; Deny from all<br />
&lt;/Files&gt;<br />
禁止访问某些指定的目录：（可以用 &lt;DirectoryMatch&gt;&nbsp;&nbsp; 来进行正则匹配）<br />
&lt;Directory ~ "^/var/www/(.+/)*[0-9]{3}"&gt;&nbsp;<br />
&nbsp;&nbsp; Order allow,deny<br />
&nbsp;&nbsp; Deny from all<br />
&lt;/Directory&gt;<br />
通过文件匹配来进行禁止，比如禁止所有针对图片的访问：<br />
&lt;FilesMatch \.(?i:gif|jpe?g|png)$&gt;<br />
&nbsp;&nbsp; Order allow,deny<br />
&nbsp;&nbsp; Deny from all<br />
&lt;/FilesMatch&gt;&nbsp;<br />
针对URL相对路径的禁止访问：<br />
&lt;Location /dir/&gt;<br />
&nbsp;&nbsp; Order allow,deny<br />
&nbsp;&nbsp; Deny from all<br />
&lt;/Location&gt;&nbsp;<br />
针对代理方式禁止对某些目标的访问（&lt;ProxyMatch&gt; 可以用来正则匹配），比如拒绝通过代理访问cnn.com：<br />
&lt;Proxy http://cnn.com/*&gt;<br />
&nbsp;&nbsp; Order allow,deny<br />
&nbsp;&nbsp; Deny from all<br />
&lt;/Proxy&gt;&nbsp;<br />
2. 禁止某些IP访问/只允许某些IP访问&nbsp;<br />
如果要控制禁止某些非法IP访问，在Directory选项控制：<br />
&lt;Directory "/var/www/web/"&gt;<br />
&nbsp;&nbsp; Order allow,deny<br />
&nbsp;&nbsp; Allow from all<br />
&nbsp;&nbsp; Deny from 10.0.0.1 #阻止一个IP<br />
&nbsp;&nbsp; Deny from 192.168.0.0/24 #阻止一个IP段<br />
&lt;/Directory&gt;<br />
只允许某些IP访问，适合比如就允许内部或者合作公司访问：<br />
&lt;Directory "/var/www/web/"&gt;<br />
&nbsp;&nbsp; Order deny,allow<br />
&nbsp;&nbsp; Deny from all<br />
&nbsp;&nbsp; All from example.com #允许某个域名<br />
&nbsp;&nbsp; All from 10.0.0.1 #允许一个iP<br />
&nbsp;&nbsp; All from 10.0.0.1 10.0.0.2 #允许多个iP<br />
&nbsp;&nbsp; Allow from 10.1.0.0/255.255.0.0 #允许一个IP段，掩码对<br />
&nbsp;&nbsp; All from 10.0.1 192.168 #允许一个IP段，后面不填写<br />
&nbsp;&nbsp; All from 192.168.0.0/24 #允许一个IP段，网络号<br />
&lt;/Directory&gt;<br />
</span><br style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">Apache：解决办法；</span><br style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">&lt;Directory "/home/domain/public_html"&gt;</span><br style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">Options -Indexes FollowSymLinks</span><br style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">AllowOverride All</span><br style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">&lt;Files ~ ".txt"&gt;</span><br style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">Order allow,deny</span><br style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">Deny from all</span><br style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">&lt;/Files&gt;</span><br style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">&lt;/Directory&gt;</span>