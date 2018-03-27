<p>
	<a href="http://blog.csdn.net/u011630575/article/details/48287361" style="color:#000000;text-decoration-line:none;font-family:&quot;font-size:20px;white-space:normal;background-color:#FFFFFF;">nginx中php-fpm使用sock方式配置的例子</a>
</p>
<p>
	<br />
</p>
<p>
	<br />
</p>
<p>
	<p style="color:#333333;font-family:Arial, 宋体;font-size:14px;white-space:normal;background-color:#FFFFFF;margin-top:10px;margin-bottom:10px;padding-top:0px;padding-bottom:0px;clear:both;line-height:24px;">
		sock方式配置nginx的<a target="_blank" href="http://www.jbxue.com/zt/php-fpm/" class="infotextkey" style="color:#0033CC;text-decoration-line:none;margin:0px;padding:0px;height:24px;line-height:24px;font-weight:bold;">php-fpm</a>，如下：<br style="margin:0px;padding:0px;" />
&nbsp;
	</p>
	<div class="codetitle" style="color:#333333;font-family:Arial, 宋体;font-size:14px;white-space:normal;margin:3px auto 0px;padding:2px 3px;border-left:1px solid #A2B7DB;width:625px;background-color:#F2F6FB;clear:both;border-top:1px solid #A2B7DB;border-right:1px solid #A2B7DB;">
		<span style="margin:0px;padding:0px;float:right;"><span style="margin:0px;padding:0px;">复制代码</span></span>代码示例:
	</div>
	<div id="c_yZJ9SPCX" class="codebody" style="color:#333333;white-space:normal;margin:0px auto 3px;padding:0px 3px 5px 5px;border:1px solid #A2B7DB;width:623px;clear:both;font-family:Arial;background-color:#CCCCCC;font-size:18px;line-height:30px;">
		location ~ \.php$ {<br style="margin:0px;padding:0px;" />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<a target="_blank" href="http://www.jbxue.com/zt/fastcgi/" class="infotextkey" style="color:#0033CC;text-decoration-line:none;margin:0px;padding:0px;font-size:14px;height:24px;line-height:24px;font-weight:bold;">fastcgi</a>_pass&nbsp;&nbsp; unix:/dev/shm/php-fpm.sock;<br style="margin:0px;padding:0px;" />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; fastcgi_index&nbsp; index.php;<br style="margin:0px;padding:0px;" />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; fastcgi_param&nbsp; SCRIPT_FILENAME&nbsp; $document_root$fastcgi_script_name;<br style="margin:0px;padding:0px;" />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<a target="_blank" href="http://www.jbxue.com/zt/include/" class="infotextkey" style="color:#0033CC;text-decoration-line:none;margin:0px;padding:0px;font-size:14px;height:24px;line-height:24px;font-weight:bold;">include</a>&nbsp;fastcgi_params;<br style="margin:0px;padding:0px;" />
}
	</div>
	<p style="color:#333333;font-family:Arial, 宋体;font-size:14px;white-space:normal;background-color:#FFFFFF;margin-top:10px;margin-bottom:10px;padding-top:0px;padding-bottom:0px;clear:both;line-height:24px;">
		配置<a href="http://lib.csdn.net/base/php" class="replace_word" title="PHP知识库" target="_blank" style="color:#DF3434;text-decoration-line:none;font-weight:bold;">PHP</a>-fpm：<br style="margin:0px;padding:0px;" />
&nbsp;
	</p>
	<div class="codetitle" style="color:#333333;font-family:Arial, 宋体;font-size:14px;white-space:normal;margin:3px auto 0px;padding:2px 3px;border-left:1px solid #A2B7DB;width:625px;background-color:#F2F6FB;clear:both;border-top:1px solid #A2B7DB;border-right:1px solid #A2B7DB;">
		<span style="margin:0px;padding:0px;float:right;"><span style="margin:0px;padding:0px;">复制代码</span></span>代码示例:
	</div>
	<div id="c_unTAg7NQ" class="codebody" style="color:#333333;white-space:normal;margin:0px auto 3px;padding:0px 3px 5px 5px;border:1px solid #A2B7DB;width:623px;clear:both;font-family:Arial;background-color:#CCCCCC;font-size:18px;line-height:30px;">
		listen = /dev/shm/php-fpm.sock
	</div>
	<p style="color:#333333;font-family:Arial, 宋体;font-size:14px;white-space:normal;background-color:#FFFFFF;margin-top:10px;margin-bottom:10px;padding-top:0px;padding-bottom:0px;clear:both;line-height:24px;">
		将socket置于内存中，提高响应速度。
	</p>
</p>