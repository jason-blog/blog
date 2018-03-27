<p>
	1.设置 nginx 访问文件名权限&nbsp;
</p>
<p>
	<br />
</p>
<p>
	#注意这里是只有没有后缀名和.php结尾的文件才交给apache处理
</p>
<p>
	#所以只能nginx设置后缀名权限
</p>
<p>
	#为了做动态静态分离
</p>
<p>
	#涉及到权限问题需要谨慎操作
</p>
<p>
	&nbsp; location ~ ^([^.]+|.*\.php)$ {<br />
&nbsp; &nbsp; &nbsp; &nbsp; proxy_set_header Host $host;<br />
&nbsp; &nbsp; &nbsp; &nbsp; proxy_set_header X-Real-IP $remote_addr;<br />
&nbsp; &nbsp; &nbsp; &nbsp; proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;<br />
&nbsp; &nbsp; &nbsp; &nbsp; proxy_pass http://127.0.0.1:88;<br />
&nbsp; &nbsp; &nbsp; &nbsp; }
</p>
<p>
	<br />
</p>
<p>
	<br />
</p>
<p>
	<span style="font-family:&quot;background-color:#FFFFFF;width:700.906px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;color:#5C5C5C;margin:0px 0px 1px 45px !important;font-size:13px;border:none;white-space:normal;">&nbsp;location ~ .*.(htm|html|gif|jpg|jpeg|png|bmp|swf|ioc|rar|zip|txt|flv|mid|doc|ppt|pdf|xls|mp3|wma)$ {</span><br style="font-family:&quot;background-color:#FFFFFF;width:700.906px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;color:#5C5C5C;margin:0px 0px 1px 45px !important;font-size:13px;border:none;white-space:normal;" />
<span style="font-family:&quot;background-color:#FFFFFF;width:700.906px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;color:#5C5C5C;margin:0px 0px 1px 45px !important;font-size:13px;border:none;white-space:normal;">&nbsp; &nbsp; &nbsp; &nbsp; expires 15d;</span><br style="font-family:&quot;background-color:#FFFFFF;width:700.906px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;color:#5C5C5C;margin:0px 0px 1px 45px !important;font-size:13px;border:none;white-space:normal;" />
<span style="font-family:&quot;background-color:#FFFFFF;width:700.906px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;color:#5C5C5C;margin:0px 0px 1px 45px !important;font-size:13px;border:none;white-space:normal;">&nbsp; &nbsp; &nbsp; &nbsp; }</span><br style="font-family:&quot;background-color:#FFFFFF;width:700.906px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;color:#5C5C5C;margin:0px 0px 1px 45px !important;font-size:13px;border:none;white-space:normal;" />
<span style="font-family:&quot;background-color:#FFFFFF;width:700.906px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;color:#5C5C5C;margin:0px 0px 1px 45px !important;font-size:13px;border:none;white-space:normal;">&nbsp;location ~ .*.(js|css)$ {</span><br style="font-family:&quot;background-color:#FFFFFF;width:700.906px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;color:#5C5C5C;margin:0px 0px 1px 45px !important;font-size:13px;border:none;white-space:normal;" />
<span style="font-family:&quot;background-color:#FFFFFF;width:700.906px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;color:#5C5C5C;margin:0px 0px 1px 45px !important;font-size:13px;border:none;white-space:normal;">&nbsp; &nbsp; &nbsp; &nbsp; expires 1h;</span><br style="font-family:&quot;background-color:#FFFFFF;width:700.906px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;color:#5C5C5C;margin:0px 0px 1px 45px !important;font-size:13px;border:none;white-space:normal;" />
<span style="font-family:&quot;background-color:#FFFFFF;width:700.906px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;color:#5C5C5C;margin:0px 0px 1px 45px !important;font-size:13px;border:none;white-space:normal;">&nbsp; &nbsp; &nbsp; &nbsp; #deny all;</span><br style="font-family:&quot;background-color:#FFFFFF;width:700.906px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;color:#5C5C5C;margin:0px 0px 1px 45px !important;font-size:13px;border:none;white-space:normal;" />
<span style="font-family:&quot;background-color:#FFFFFF;width:700.906px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;color:#5C5C5C;margin:0px 0px 1px 45px !important;font-size:13px;border:none;white-space:normal;">&nbsp; &nbsp; &nbsp; &nbsp; }</span><br style="font-family:&quot;background-color:#FFFFFF;width:700.906px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;color:#5C5C5C;margin:0px 0px 1px 45px !important;font-size:13px;border:none;white-space:normal;" />
</p>
<p>
	#注意确保上面的配置不包含所有 例如 * ? 等
</p>
<p>
	<br />
</p>
<ol start="1" style="white-space:normal;padding:0px;list-style:none;font-family:Consolas, &quot;background-color:#FFFFFF;width:700.906px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;color:#5C5C5C;margin:0px 0px 1px 45px !important;font-size:13px;border:none;">
	<li class="alt" style="list-style-type:decimal-leading-zero;list-style-image:initial;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;list-style-position:outside !important;margin:0px !important;padding:0px 3px 0px 10px !important;">
		<span style="margin:0px;padding:0px;border:none;">location&nbsp;~*&nbsp;\.(ini|docx|txt|doc)$&nbsp;{&nbsp;&nbsp;</span>
	</li>
	<li class="" style="list-style-type:decimal-leading-zero;list-style-image:initial;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;list-style-position:outside !important;margin:0px !important;padding:0px 3px 0px 10px !important;">
		<span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;deny&nbsp;all;&nbsp;&nbsp;</span>
	</li>
	<li class="alt" style="list-style-type:decimal-leading-zero;list-style-image:initial;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;list-style-position:outside !important;margin:0px !important;padding:0px 3px 0px 10px !important;">
		<span style="margin:0px;padding:0px;border:none;">} &nbsp;</span>
	</li>
</ol>
<p>
	<span style="font-family:'Consolas, background-color:#FFFFFF;width:700.906px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;color:#5C5C5C;margin:0px 0px 1px 45px !important;font-size:13px;border:none;"><br />
</span>
</p>
<p>
	<span style="font-family:'Consolas, background-color:#FFFFFF;width:700.906px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;color:#5C5C5C;margin:0px 0px 1px 45px !important;font-size:13px;border:none;"><br />
</span>
</p>
<p>
	<br />
</p>
<p>
	2.设置apache中文件权限
</p>
<p>
	<br />
</p>
<p>
	####确认nginx已经将需要限制的文件后缀名抛给了apache处理&nbsp;
</p>
<p>
	<br />
</p>
<p>
	<span style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">增加Files选项来控制，比如要不允许访问 .inc 扩展名的文件，保护php类库：</span>
</p>
<p>
	<span style="color:#362E2B;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">&lt;Files ~ "\.inc$"&gt;</span><br style="color:#362E2B;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#362E2B;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">&nbsp;&nbsp; Order allow,deny</span><br style="color:#362E2B;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#362E2B;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">&nbsp;&nbsp; Deny from all</span><br style="color:#362E2B;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#362E2B;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">&lt;/Files&gt;</span>
</p>
<p>
	<br />
</p>
<p>
	<span style="color:#362E2B;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<div id="article_content" class="article_content" style="margin:20px 0px 0px;font-stretch:normal;font-size:14px;line-height:26px;font-family:Arial;color:#362E2B;white-space:normal;background-color:#FFFFFF;">
		<span style="font-family:&quot;">禁止访问某些指定的目录：（可以用 &lt;DirectoryMatch&gt;&nbsp;&nbsp; 来进行正则匹配）<br />
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
</span><br />
Apache：解决办法；<br />
&lt;Directory "/home/domain/public_html"&gt;<br />
Options -Indexes FollowSymLinks<br />
AllowOverride All<br />
&lt;Files ~ ".txt"&gt;<br />
Order allow,deny<br />
Deny from all<br />
&lt;/Files&gt;<br />
&lt;/Directory&gt;<br />
	</div>
	<div class="bdsharebuttonbox tracking-ad bdshare-button-style0-16" data-mod="popu_172" data-bd-bind="1492409711701" style="zoom:1;color:#362E2B;font-family:Arial, Console, Verdana, &quot;white-space:normal;background-color:#FFFFFF;float:right;">
		<a href="http://blog.csdn.net/cdefg198/article/details/6732767#" class="bds_more" data-cmd="more" target="_blank" style="color:#333333;text-decoration-line:none;float:left;padding-left:17px;line-height:16px;height:16px;background-repeat:no-repeat;cursor:pointer;margin:6px 6px 6px 0px;background-image:url(&quot;http://bdimg.share.baidu.com/static/api/img/share/icons_0_16.png?v=d754dcc0.png&quot;background-position:0px 0px !important;"></a><a href="http://blog.csdn.net/cdefg198/article/details/6732767#" class="bds_qzone" data-cmd="qzone" title="分享到QQ空间" target="_blank" style="color:#6A3906;text-decoration-line:none;float:left;padding-left:17px;line-height:16px;height:16px;background-image:url(&quot;background-repeat:no-repeat;cursor:pointer;margin:6px 6px 6px 0px;background-position:0px -52px !important;"></a><a href="http://blog.csdn.net/cdefg198/article/details/6732767#" class="bds_tsina" data-cmd="tsina" title="分享到新浪微博" target="_blank" style="color:#6A3906;text-decoration-line:none;float:left;padding-left:17px;line-height:16px;height:16px;background-image:url(&quot;background-repeat:no-repeat;cursor:pointer;margin:6px 6px 6px 0px;background-position:0px -104px !important;"></a><a href="http://blog.csdn.net/cdefg198/article/details/6732767#" class="bds_tqq" data-cmd="tqq" title="分享到腾讯微博" target="_blank" style="color:#6A3906;text-decoration-line:none;float:left;padding-left:17px;line-height:16px;height:16px;background-image:url(&quot;background-repeat:no-repeat;cursor:pointer;margin:6px 6px 6px 0px;background-position:0px -260px !important;"></a><a href="http://blog.csdn.net/cdefg198/article/details/6732767#" class="bds_renren" data-cmd="renren" title="分享到人人网" target="_blank" style="color:#6A3906;text-decoration-line:none;float:left;padding-left:17px;line-height:16px;height:16px;background-image:url(&quot;background-repeat:no-repeat;cursor:pointer;margin:6px 6px 6px 0px;background-position:0px -208px !important;"></a><a href="http://blog.csdn.net/cdefg198/article/details/6732767#" class="bds_weixin" data-cmd="weixin" title="分享到微信" target="_blank" style="color:#6A3906;text-decoration-line:none;float:left;padding-left:17px;line-height:16px;height:16px;background-image:url(&quot;background-repeat:no-repeat;cursor:pointer;margin:6px 6px 6px 0px;background-position:0px -1612px !important;"></a>
	</div>
</span>
</p>
<p>
	<br />
</p>