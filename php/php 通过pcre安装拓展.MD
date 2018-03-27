<p>
	linux 安装pecl&nbsp;
</p>
<p>
	<br />
</p>
<p>
	yum install php-pear
</p>
<p>
	<br />
</p>
<p>
	apt install php-pear
</p>
<p>
	<br />
</p>
<p>
	<p style="margin-top:0px;margin-bottom:10px;padding:0px;border:0px;font-size:13px;background:#FFFFFF;font-family:&quot;white-space:normal;">
		<span style="margin:0px;padding:0px;border:0px;font-size:14px;background:transparent;">&nbsp;&nbsp;</span><span style="margin:0px;padding:0px;border:0px;font-size:18px;background:transparent;">&nbsp;<strong>1. 组件安装</strong></span>
	</p>
	<p style="margin-top:0px;margin-bottom:10px;padding:0px;border:0px;font-size:13px;background:#FFFFFF;font-family:&quot;white-space:normal;">
		<span style="margin:0px;padding:0px;border:0px;font-size:14px;background:transparent;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 1.1 安装php-devel开发组件</span><br />
<span style="margin:0px;padding:0px;border:0px;font-size:14px;background:transparent;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; yum install php-devel</span>
	</p>
	<p style="margin-top:0px;margin-bottom:10px;padding:0px;border:0px;font-size:13px;background:#FFFFFF;font-family:&quot;white-space:normal;">
		<span style="margin:0px;padding:0px;border:0px;font-size:14px;background:transparent;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 1.2 安装php-pecl组件</span><br />
<span style="margin:0px;padding:0px;border:0px;font-size:14px;background:transparent;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; yum install php-pecl-memcache</span>
	</p>
	<p style="margin-top:0px;margin-bottom:10px;padding:0px;border:0px;font-size:13px;background:#FFFFFF;font-family:&quot;white-space:normal;">
		<span style="margin:0px;padding:0px;border:0px;font-size:14px;background:transparent;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 1.3 安装pecl_http的扩展包</span><br />
<span style="margin:0px;padding:0px;border:0px;font-size:14px;background:transparent;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; pecl install pecl_http</span>
	</p>
	<p style="margin-top:0px;margin-bottom:10px;padding:0px;border:0px;font-size:13px;background:#FFFFFF;font-family:&quot;white-space:normal;">
		<span style="margin:0px;padding:0px;border:0px;font-size:14px;background:transparent;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 命令pecl install pecl_http的安装过程中可能会出现如下的错误：</span>
	</p>
	<p style="margin-top:0px;margin-bottom:10px;padding:0px;border:0px;font-size:13px;background:#FFFFFF;font-family:&quot;white-space:normal;">
		<span style="margin:0px;padding:0px;border:0px;font-size:14px;background:transparent;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp; a. configure: error: could not find zlib.h</span><br />
<span style="margin:0px;padding:0px;border:0px;font-size:14px;background:transparent;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 解决方法: yum install zlib-devel</span>
	</p>
	<p style="margin-top:0px;margin-bottom:10px;padding:0px;border:0px;font-size:13px;background:#FFFFFF;font-family:&quot;white-space:normal;">
		<span style="margin:0px;padding:0px;border:0px;font-size:14px;background:transparent;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; b.&nbsp; configure: error: could not find curl/curl.h</span><br />
<span style="margin:0px;padding:0px;border:0px;font-size:14px;background:transparent;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 解决方法: yum install curl-devel</span>
	</p>
	<p style="margin-top:0px;margin-bottom:10px;padding:0px;border:0px;font-size:13px;background:#FFFFFF;font-family:&quot;white-space:normal;">
		<span style="margin:0px;padding:0px;border:0px;font-size:18px;background:transparent;">&nbsp;&nbsp;&nbsp;&nbsp;<strong>2. 组件配置</strong></span>
	</p>
	<p style="margin-top:0px;margin-bottom:10px;padding:0px;border:0px;font-size:13px;background:#FFFFFF;font-family:&quot;white-space:normal;">
		<span style="margin:0px;padding:0px;border:0px;font-size:14px;background:transparent;">&nbsp;&nbsp;&nbsp;&nbsp; pecl install pecl_http成功结束后执行如下命令，添加php对http.so的支持</span>
	</p>
	<p style="margin-top:0px;margin-bottom:10px;padding:0px;border:0px;font-size:13px;background:#FFFFFF;font-family:&quot;white-space:normal;">
		<span style="margin:0px;padding:0px;border:0px;font-size:14px;background:transparent;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; touch /etc/php.d/http.ini</span><br />
<span style="margin:0px;padding:0px;border:0px;font-size:14px;background:transparent;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; echo "; Enable http extension module" &gt;&gt; /etc/php.d/http.ini</span>
	</p>
	<p style="margin-top:0px;margin-bottom:10px;padding:0px;border:0px;font-size:13px;background:#FFFFFF;font-family:&quot;white-space:normal;">
		<span style="margin:0px;padding:0px;border:0px;font-size:14px;background:transparent;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; echo "extension=http.so" &gt;&gt; /etc/php.d/http.ini</span>
	</p>
</p>