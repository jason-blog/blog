<p>
	http://www.cnblogs.com/digdeep/p/4859575.html
</p>
<p>
	<br />
</p>
<p>
	<br />
</p>
<p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		OpenResty 官网：http://openresty.org/
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		OpenResty 是一个nginx和它的各种三方模块的一个打包而成的软件平台。最重要的一点是它将lua/luajit打包了进来，使得我们可以使用lua脚本来进行web的开发。有了lua，我们可以借助于nginx的异步非阻塞的功能，达到<span style="line-height:1.5;color:#800000;"><strong>使用 lua 异步并发访问后端的 MySQL, PostgreSQL, Memcached, Redis等等服务</strong></span>。特别是特有的 ngx.location.capture_multi 功能让人印象深刻，其可以达到极大的<span style="line-height:1.5;color:#800000;"><strong>减少浏览器的http连接数量，并且可以异步并发的访问后台 Java/PHP/Python 等等接口</strong></span>。OpenResty 架构的web可以轻松超越Node.js的性能，并且对后端语言没有限制，你可以使用Java/PHP/Python等等各种语言。OpenResty(nginx+lua)可以替代node.js的前端渲染的功能。
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		OpenResty (aka. ngx_openresty) is a full-fledged web application server by bundling the standard&nbsp;<a class="tiddlyLink tiddlyLinkExisting" title="Nginx - YichunZhang, 2011/6/21 下午4:24:00">Nginx</a>&nbsp;core, lots of&nbsp;<a class="externalLink" title="External link to http://wiki.nginx.org/3rdPartyModules" href="http://wiki.nginx.org/3rdPartyModules" target="_blank" style="color:navy;text-decoration-line:none;">3rd-party Nginx modules</a>, as well as most of their external dependencies.<br />
By taking advantage of various well-designed Nginx modules, OpenResty effectively turns the nginx server into a powerful web app server, in which the web developers&nbsp;<span style="line-height:1.5;color:#800000;">can use the Lua programming language to script various existing nginx C modules and Lua modules</span>&nbsp;and construct extremely high-performance web applications that are capable to handle 10K+ connections.<br />
OpenResty aims to run your server-side web app completely in the Nginx server, leveraging Nginx's event model to&nbsp;<span style="line-height:1.5;color:#800000;">do non-blocking I/O not only with the HTTP clients,&nbsp;<span style="line-height:1.5;text-decoration-line:underline;">but also with remote backends like MySQL, PostgreSQL, Memcached, and Redis</span></span>.
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		<span style="line-height:1.5;color:#FF0000;"><strong>1. 安装OpenResty</strong></span>
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		先安装依赖：yum install readline-devel pcre-devel openssl-devel gcc
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		解压： tar zxvf ngx_openresty-1.9.3.1.tar.gz
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		建立一个软连接：ln -s ngx_openresty-1.9.3.1 openresty
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		进入目录：cd openresty
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		编译：
	</p>
	<div class="cnblogs_code" style="background-color:#F5F5F5;border:1px solid #CCCCCC;padding:5px;overflow:auto;margin:5px 0px;white-space:normal;font-family:&quot;">
		<div class="cnblogs_code_toolbar" style="margin-top:5px;">
			<span class="cnblogs_code_copy" style="padding-right:5px;line-height:1.5 !important;"><a title="复制代码" style="color:navy;border:none !important;"><img src="http://common.cnblogs.com/images/copycode.gif" alt="复制代码" style="max-width:900px;border-width:initial !important;border-style:none !important;" /></a></span>
		</div>
<pre style="margin-top:0px;margin-bottom:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">./configure \
             --with-cc-opt=<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">-I/usr/local/include</span><span style="font-weight:bold;line-height:1.5 !important;">"</span> \
             --with-ld-opt=<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">-L/usr/local/lib</span><span style="font-weight:bold;line-height:1.5 !important;">"</span> \
             --prefix=/opt/openresty 
... ...
Configuration summary
&nbsp; + using system PCRE library
&nbsp; + using system OpenSSL library
&nbsp; + md5: using OpenSSL library
&nbsp; + sha1: using OpenSSL library
&nbsp; + using system zlib library
&nbsp; nginx path prefix: "/opt/openresty/nginx"
&nbsp; nginx binary file: "/opt/openresty/nginx/sbin/nginx"
&nbsp; nginx configuration prefix: "/opt/openresty/nginx/conf"
&nbsp; nginx configuration file: "/opt/openresty/nginx/conf/nginx.conf"
&nbsp; nginx pid file: "/opt/openresty/nginx/logs/nginx.pid"
&nbsp; nginx error log file: "/opt/openresty/nginx/logs/error.log"
&nbsp; nginx http access log file: "/opt/openresty/nginx/logs/access.log"
&nbsp; nginx http client request body temporary files: "client_body_temp"
&nbsp; nginx http proxy temporary files: "proxy_temp"
&nbsp; nginx http fastcgi temporary files: "fastcgi_temp"
&nbsp; nginx http uwsgi temporary files: "uwsgi_temp"
&nbsp; nginx http scgi temporary files: "scgi_temp"</pre>
		<div class="cnblogs_code_toolbar" style="margin-top:5px;">
			<span class="cnblogs_code_copy" style="padding-right:5px;line-height:1.5 !important;"><a title="复制代码" style="color:navy;border:none !important;"><img src="http://common.cnblogs.com/images/copycode.gif" alt="复制代码" style="max-width:900px;border-width:initial !important;border-style:none !important;" /></a></span>
		</div>
	</div>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		其中 --prefix=/opt/openresty 指定了安装目录，不指定的话默认会安装到 /usr/local/openresty 目录下。<code></code>
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		编译安装： make &amp;&amp; make install
	</p>
	<div class="cnblogs_code" style="background-color:#F5F5F5;border:1px solid #CCCCCC;padding:5px;overflow:auto;margin:5px 0px;white-space:normal;font-family:&quot;">
<pre style="margin-top:0px;margin-bottom:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">[root<span style="color:#800080;line-height:1.5 !important;">@localhost</span> src]<span style="color:#008000;line-height:1.5 !important;">#</span><span style="color:#008000;line-height:1.5 !important;"> cd /opt/openresty/</span> [root<span style="color:#800080;line-height:1.5 !important;">@localhost</span> openresty]<span style="color:#008000;line-height:1.5 !important;">#</span><span style="color:#008000;line-height:1.5 !important;"> ls</span> bin  luajit  lualib  nginx</pre>
	</div>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		可以看到 /opt/openresty 目录下四个文件夹，其中包括了 luajit，nginx。
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		启动openresty: /opt/openresty/nginx/sbin/nginx -c /opt/openresty/nginx/conf/nginx.conf -p /opt/openresty/nginx/
	</p>
	<div class="cnblogs_code" style="background-color:#F5F5F5;border:1px solid #CCCCCC;padding:5px;overflow:auto;margin:5px 0px;white-space:normal;font-family:&quot;">
<pre style="margin-top:0px;margin-bottom:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">[root<span style="color:#800080;line-height:1.5 !important;">@localhost</span> src]<span style="color:#008000;line-height:1.5 !important;">#</span><span style="color:#008000;line-height:1.5 !important;"> ps -elf|grep nginx</span> <span style="color:#800000;line-height:1.5 !important;">1</span> S root <span style="color:#800000;line-height:1.5 !important;">2076</span> <span style="color:#800000;line-height:1.5 !important;">1</span> <span style="color:#800000;line-height:1.5 !important;">0</span> <span style="color:#800000;line-height:1.5 !important;">80</span> <span style="color:#800000;line-height:1.5 !important;">0</span> - <span style="color:#800000;line-height:1.5 !important;">34999</span> - <span style="color:#800000;line-height:1.5 !important;">21</span>:<span style="color:#800000;line-height:1.5 !important;">24</span> ? <span style="color:#800000;line-height:1.5 !important;">00</span>:<span style="color:#800000;line-height:1.5 !important;">00</span>:<span style="color:#800000;line-height:1.5 !important;">00</span> nginx: master process /opt/openresty/nginx/sbin/nginx -c /opt/openresty/nginx/conf/nginx.conf -p /opt/openresty/nginx/ <span style="color:#800000;line-height:1.5 !important;">5</span> S nobody <span style="color:#800000;line-height:1.5 !important;">2077</span> <span style="color:#800000;line-height:1.5 !important;">2076</span> <span style="color:#800000;line-height:1.5 !important;">0</span> <span style="color:#800000;line-height:1.5 !important;">80</span> <span style="color:#800000;line-height:1.5 !important;">0</span> - <span style="color:#800000;line-height:1.5 !important;">35045</span> - <span style="color:#800000;line-height:1.5 !important;">21</span>:<span style="color:#800000;line-height:1.5 !important;">24</span> ? <span style="color:#800000;line-height:1.5 !important;">00</span>:<span style="color:#800000;line-height:1.5 !important;">00</span>:<span style="color:#800000;line-height:1.5 !important;">00</span> nginx:<span style="line-height:1.5 !important;"> worker process </span><span style="color:#800000;line-height:1.5 !important;">0</span> S root <span style="color:#800000;line-height:1.5 !important;">2079</span> <span style="color:#800000;line-height:1.5 !important;">1678</span> <span style="color:#800000;line-height:1.5 !important;">0</span> <span style="color:#800000;line-height:1.5 !important;">80</span> <span style="color:#800000;line-height:1.5 !important;">0</span> - <span style="color:#800000;line-height:1.5 !important;">1088</span> - <span style="color:#800000;line-height:1.5 !important;">21</span>:<span style="color:#800000;line-height:1.5 !important;">24</span> pts/<span style="color:#800000;line-height:1.5 !important;">1</span> <span style="color:#800000;line-height:1.5 !important;">00</span>:<span style="color:#800000;line-height:1.5 !important;">00</span>:<span style="color:#800000;line-height:1.5 !important;">00</span> <span style="color:#0000FF;line-height:1.5 !important;">grep</span> nginx</pre>
	</div>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		验证可以访问： curl 127.0.0.1
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		<strong><span style="line-height:1.5;color:#FF0000;">2. content_by_lua 和 content_by_lua_file</span></strong>
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		nginx 如何嵌入 lua 脚本。方法就是在nginx的配置文件nginx.conf 中使用 content_by_lua 或者 cotent_by_lua_file 指令：
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		1) content_by_lua 一般在很简单的lua脚本时使用：
	</p>
	<div class="cnblogs_code" style="background-color:#F5F5F5;border:1px solid #CCCCCC;padding:5px;overflow:auto;margin:5px 0px;white-space:normal;font-family:&quot;">
		<div class="cnblogs_code_toolbar" style="margin-top:5px;">
			<span class="cnblogs_code_copy" style="padding-right:5px;line-height:1.5 !important;"><a title="复制代码" style="color:navy;border:none !important;"><img src="http://common.cnblogs.com/images/copycode.gif" alt="复制代码" style="max-width:900px;border-width:initial !important;border-style:none !important;" /></a></span>
		</div>
<pre style="margin-top:0px;margin-bottom:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">        location /<span style="line-height:1.5 !important;">lua {
                set </span><span style="color:#800080;line-height:1.5 !important;">$test</span> <span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">hello, world.</span><span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="line-height:1.5 !important;">;
                content_by_lua </span><span style="font-weight:bold;line-height:1.5 !important;">'</span><span style="font-weight:bold;line-height:1.5 !important;"> ngx.header.content_type = "text/plain";
                        ngx.say(ngx.var.test); </span><span style="font-weight:bold;line-height:1.5 !important;">'</span><span style="line-height:1.5 !important;">;
        }</span></pre>
		<div class="cnblogs_code_toolbar" style="margin-top:5px;">
			<span class="cnblogs_code_copy" style="padding-right:5px;line-height:1.5 !important;"><a title="复制代码" style="color:navy;border:none !important;"><img src="http://common.cnblogs.com/images/copycode.gif" alt="复制代码" style="max-width:900px;border-width:initial !important;border-style:none !important;" /></a></span>
		</div>
	</div>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		访问 http://localhost/lua 可以看到输出到页面的&nbsp;&nbsp;<span style="line-height:1.5;">hello, world.</span>
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		2）cotent_by_lua_file 适应于复杂的 lua 脚本，专门放入一个文件中：
	</p>
	<div class="cnblogs_code" style="background-color:#F5F5F5;border:1px solid #CCCCCC;padding:5px;overflow:auto;margin:5px 0px;white-space:normal;font-family:&quot;">
<pre style="margin-top:0px;margin-bottom:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">        location /<span style="line-height:1.5 !important;">lua2 { </span><span style="color:#008000;line-height:1.5 !important;">#</span><span style="color:#008000;line-height:1.5 !important;">lua_code_cache off;</span> content_by_lua_file lua/hello.<span style="line-height:1.5 !important;">lua;
        }</span></pre>
	</div>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		路径相对于 /opt/openresty/nginx
	</p>
	<div class="cnblogs_code" style="background-color:#F5F5F5;border:1px solid #CCCCCC;padding:5px;overflow:auto;margin:5px 0px;white-space:normal;font-family:&quot;">
<pre style="margin-top:0px;margin-bottom:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">[root<span style="color:#800080;line-height:1.5 !important;">@localhost</span> lua]<span style="color:#008000;line-height:1.5 !important;">#</span><span style="color:#008000;line-height:1.5 !important;"> pwd</span> /opt/openresty/nginx/<span style="line-height:1.5 !important;">lua
[root</span><span style="color:#800080;line-height:1.5 !important;">@localhost</span> lua]<span style="color:#008000;line-height:1.5 !important;">#</span><span style="color:#008000;line-height:1.5 !important;"> cat hello.lua</span> ngx.say(<span style="font-weight:bold;line-height:1.5 !important;">'</span><span style="font-weight:bold;line-height:1.5 !important;">hello ngx_lua!!!!</span><span style="font-weight:bold;line-height:1.5 !important;">'</span>);</pre>
	</div>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		本例子中 hello.lua 只包含一句： ngx.say('hello ngx_lua!!!!');
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		访问 /lua2 :
	</p>
	<div class="cnblogs_code" style="background-color:#F5F5F5;border:1px solid #CCCCCC;padding:5px;overflow:auto;margin:5px 0px;white-space:normal;font-family:&quot;">
<pre style="margin-top:0px;margin-bottom:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">[root<span style="color:#800080;line-height:1.5 !important;">@localhost</span> lua]<span style="color:#008000;line-height:1.5 !important;">#</span><span style="color:#008000;line-height:1.5 !important;"> curl localhost/lua</span> hello ngx_lua!!!!</pre>
	</div>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		可以看到访问成功。
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		在 nginx.conf 文件的 server {.. ...} 中加入&nbsp;<span style="line-height:1.5;color:#800000;"><strong>lua_code_cache off;</strong></span>&nbsp;可以方便调试lua脚本，修改lua脚本之后，不需要 reload nginx.
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		openresty 中的 nginx 嵌入 luajit 的原理：
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		<img src="http://images2015.cnblogs.com/blog/699877/201510/699877-20151007215256909-481452862.png" alt="" style="max-width:900px;" />
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		每一个nginx的进程中都嵌入了一个 luajit的虚拟机，来执行lua脚本。nginx将lua脚本的执行交给了luajit vm.
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		<span style="line-height:1.5;color:#FF0000;"><strong>3. ngx_lua 的指令 和 API</strong></span>
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		上面我们说到 nginx 嵌入 lua 脚本可以使用 content_by_lua 和 content_by_lua_file，它们其实是<span style="line-height:1.5;color:#FF0000;"><strong>指令(Directives)</strong></span>，类似的指令还有很多，
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		具体参见：https://www.nginx.com/resources/wiki/modules/lua/#directives
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		<img src="http://images2015.cnblogs.com/blog/699877/201510/699877-20151008103305893-1052305317.png" alt="" style="max-width:900px;" />
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		这些指令都是 nginx 访问 lua 脚本的入口。
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		ngx_lua API：
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		指令是 nginx 访问 lua 脚本的入口。那么lua脚本如何调用nginx中的函数呢？就是通过 ngx_lua 的API 。
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		具体介绍参见：https://www.nginx.com/resources/wiki/modules/lua/#nginx-api-for-lua
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		<strong>The various&nbsp;<span style="line-height:1.5;color:#0000FF;"><code class="docutils literal"><span class="pre" style="line-height:1.5;">*_by_lua</span></code>&nbsp;and&nbsp;<code class="docutils literal"><span class="pre" style="line-height:1.5;">*_by_lua_file</span></code></span>&nbsp;<span style="line-height:1.5;color:#FF0000;">configuration</span>&nbsp;<span style="line-height:1.5;color:#FF0000;">directives&nbsp;<span style="line-height:1.5;color:#0000FF;">serve as gateways</span></span>&nbsp;to the Lua API within the&nbsp;<code class="docutils literal"><span class="pre" style="line-height:1.5;">nginx.conf</span></code>&nbsp;file</strong>. The&nbsp;<span style="line-height:1.5;color:#0000FF;">NGINX Lua API described below can only be called within the user Lua code</span>&nbsp;run in the context of these configuration directives.
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		The API is exposed to Lua in the form of two standard packages&nbsp;<code class="docutils literal">ngx</code>&nbsp;and&nbsp;<code class="docutils literal">ndk</code>. These packages are in the default global scope within ngx_lua and are always available within ngx_lua directives.
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		<img src="http://images2015.cnblogs.com/blog/699877/201510/699877-20151008103930753-1256123840.png" alt="" style="max-width:900px;" />
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		<span style="line-height:1.5;text-decoration-line:underline;">其实nginx和Lua的交互开发主要就是<span style="line-height:1.5;color:#0000FF;"><strong>指令和API</strong></span>，当然还有<span style="line-height:1.5;color:#0000FF;"><strong>lua脚本的语法</strong></span></span>。指令是nginx访问lua的入口，API是lua调用nginx的函数，lua是脚本编程语言。
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		指令其实很简单，所以主要就是熟悉ngx_lua的 API 和Lua语法。
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		<span style="line-height:1.5;color:#FF0000;"><strong>4. lua 访问 redis</strong></span>
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		lua-resty-redis 模块：https://github.com/openresty/lua-resty-redis （有文档可以参考）
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		在nginx.conf中加入：
	</p>
	<div class="cnblogs_code" style="background-color:#F5F5F5;border:1px solid #CCCCCC;padding:5px;overflow:auto;margin:5px 0px;white-space:normal;font-family:&quot;">
<pre style="margin-top:0px;margin-bottom:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">        location /<span style="line-height:1.5 !important;">redis_test{
            content_by_lua_file lua</span>/redis_test.<span style="line-height:1.5 !important;">lua;
        }</span></pre>
	</div>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		redis_test.lua 内容:
	</p>
	<div class="cnblogs_code" style="background-color:#F5F5F5;border:1px solid #CCCCCC;padding:5px;overflow:auto;margin:5px 0px;white-space:normal;font-family:&quot;">
		<div class="cnblogs_code_toolbar" style="margin-top:5px;">
			<span class="cnblogs_code_copy" style="padding-right:5px;line-height:1.5 !important;"><a title="复制代码" style="color:navy;border:none !important;"><img src="http://common.cnblogs.com/images/copycode.gif" alt="复制代码" style="max-width:900px;border-width:initial !important;border-style:none !important;" /></a></span>
		</div>
<pre style="margin-top:0px;margin-bottom:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">[root<span style="color:#800080;line-height:1.5 !important;">@localhost</span> lua]<span style="color:#008000;line-height:1.5 !important;">#</span><span style="color:#008000;line-height:1.5 !important;"> cat redis_test.lua</span> <span style="color:#0000FF;line-height:1.5 !important;">local</span> redis = <span style="color:#0000FF;line-height:1.5 !important;">require</span> <span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">resty.redis</span><span style="font-weight:bold;line-height:1.5 !important;">"</span> <span style="color:#0000FF;line-height:1.5 !important;">local</span> red = redis:<span style="line-height:1.5 !important;">new()

red</span>:set_timeout(<span style="color:#800000;line-height:1.5 !important;">1000</span><span style="line-height:1.5 !important;">) </span><span style="color:#0000FF;line-height:1.5 !important;">local</span> ok, err = red:<span style="color:#0000FF;line-height:1.5 !important;">connect</span>(<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">127.0.0.1</span><span style="font-weight:bold;line-height:1.5 !important;">"</span>, <span style="color:#800000;line-height:1.5 !important;">6379</span><span style="line-height:1.5 !important;">) </span><span style="color:#0000FF;line-height:1.5 !important;">if</span><span style="line-height:1.5 !important;"> not ok then
        ngx</span>.say(<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">failed to connect: </span><span style="font-weight:bold;line-height:1.5 !important;">"</span>,<span style="line-height:1.5 !important;"> err) </span><span style="color:#0000FF;line-height:1.5 !important;">return</span><span style="line-height:1.5 !important;"> end

ngx</span>.say(<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">set result: </span><span style="font-weight:bold;line-height:1.5 !important;">"</span>,<span style="line-height:1.5 !important;"> ok) </span><span style="color:#0000FF;line-height:1.5 !important;">local</span> res, err = red:get(<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">dog</span><span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="line-height:1.5 !important;">) </span><span style="color:#0000FF;line-height:1.5 !important;">if</span><span style="line-height:1.5 !important;"> not res then
        ngx</span>.say(<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">failed to get doy: </span><span style="font-weight:bold;line-height:1.5 !important;">"</span>,<span style="line-height:1.5 !important;"> err) </span><span style="color:#0000FF;line-height:1.5 !important;">return</span><span style="line-height:1.5 !important;"> end </span><span style="color:#0000FF;line-height:1.5 !important;">if</span> res == ngx.<span style="line-height:1.5 !important;">null then
        ngx</span>.say(<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">dog not found.</span><span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="line-height:1.5 !important;">) </span><span style="color:#0000FF;line-height:1.5 !important;">return</span><span style="line-height:1.5 !important;"> end

ngx</span>.say(<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">dog: </span><span style="font-weight:bold;line-height:1.5 !important;">"</span>,<span style="line-height:1.5 !important;"> res) </span><span style="line-height:1.5 !important;"> [root</span><span style="color:#800080;line-height:1.5 !important;">@localhost</span> lua]<span style="color:#008000;line-height:1.5 !important;">#</span></pre>
		<div class="cnblogs_code_toolbar" style="margin-top:5px;">
			<span class="cnblogs_code_copy" style="padding-right:5px;line-height:1.5 !important;"><a title="复制代码" style="color:navy;border:none !important;"><img src="http://common.cnblogs.com/images/copycode.gif" alt="复制代码" style="max-width:900px;border-width:initial !important;border-style:none !important;" /></a></span>
		</div>
	</div>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		访问：
	</p>
	<div class="cnblogs_code" style="background-color:#F5F5F5;border:1px solid #CCCCCC;padding:5px;overflow:auto;margin:5px 0px;white-space:normal;font-family:&quot;">
<pre style="margin-top:0px;margin-bottom:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">[root<span style="color:#800080;line-height:1.5 !important;">@localhost</span> lua]<span style="color:#008000;line-height:1.5 !important;">#</span><span style="color:#008000;line-height:1.5 !important;"> curl localhost/redis_test</span> set result: <span style="color:#800000;line-height:1.5 !important;">1</span><span style="line-height:1.5 !important;"> dog</span>:<span style="line-height:1.5 !important;"> an animal
[root</span><span style="color:#800080;line-height:1.5 !important;">@localhost</span> lua]<span style="color:#008000;line-height:1.5 !important;">#</span></pre>
	</div>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		我们看到访问成功。
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		<span style="line-height:1.5;color:#FF0000;"><strong>5. lua 访问mysql</strong></span>
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		openresty的mysql模块：lua-resty-mysql :https://github.com/openresty/lua-resty-mysql（有文档可以参考）
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		在nginx.conf加入如下配置：
	</p>
	<div class="cnblogs_code" style="background-color:#F5F5F5;border:1px solid #CCCCCC;padding:5px;overflow:auto;margin:5px 0px;white-space:normal;font-family:&quot;">
<pre style="margin-top:0px;margin-bottom:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">        location /<span style="line-height:1.5 !important;">mysql_test {
            content_by_lua_file lua</span>/mysql_test.<span style="line-height:1.5 !important;">lua;
        }</span></pre>
	</div>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		mysql_test.lua脚本内容：
	</p>
	<div class="cnblogs_code" style="background-color:#F5F5F5;border:1px solid #CCCCCC;padding:5px;overflow:auto;margin:5px 0px;white-space:normal;font-family:&quot;">
		<div class="cnblogs_code_toolbar" style="margin-top:5px;">
			<span class="cnblogs_code_copy" style="padding-right:5px;line-height:1.5 !important;"><a title="复制代码" style="color:navy;border:none !important;"><img src="http://common.cnblogs.com/images/copycode.gif" alt="复制代码" style="max-width:900px;border-width:initial !important;border-style:none !important;" /></a></span>
		</div>
<pre style="margin-top:0px;margin-bottom:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">[root<span style="color:#800080;line-height:1.5 !important;">@localhost</span> lua]<span style="color:#008000;line-height:1.5 !important;">#</span><span style="color:#008000;line-height:1.5 !important;"> pwd</span> /opt/openresty/nginx/<span style="line-height:1.5 !important;">lua
[root</span><span style="color:#800080;line-height:1.5 !important;">@localhost</span> lua]<span style="color:#008000;line-height:1.5 !important;">#</span><span style="color:#008000;line-height:1.5 !important;"> cat mysql_test.lua</span> <span style="color:#0000FF;line-height:1.5 !important;">local</span> mysql = <span style="color:#0000FF;line-height:1.5 !important;">require</span> <span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">resty.mysql</span><span style="font-weight:bold;line-height:1.5 !important;">"</span> <span style="color:#0000FF;line-height:1.5 !important;">local</span> db, err = mysql:<span style="line-height:1.5 !important;">new() </span><span style="color:#0000FF;line-height:1.5 !important;">if</span><span style="line-height:1.5 !important;"> not db then
        ngx</span>.say(<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">failed to instantiate mysql: </span><span style="font-weight:bold;line-height:1.5 !important;">"</span>,<span style="line-height:1.5 !important;"> err) </span><span style="color:#0000FF;line-height:1.5 !important;">return</span><span style="line-height:1.5 !important;"> end

db</span>:set_timeout(<span style="color:#800000;line-height:1.5 !important;">1000</span><span style="line-height:1.5 !important;">) </span><span style="color:#0000FF;line-height:1.5 !important;">local</span> ok, err, errno, sqlstate = db:<span style="color:#0000FF;line-height:1.5 !important;">connect</span><span style="line-height:1.5 !important;">{
        host </span>= <span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">127.0.0.1</span><span style="font-weight:bold;line-height:1.5 !important;">"</span>,<span style="line-height:1.5 !important;"> port </span>= <span style="color:#800000;line-height:1.5 !important;">3306</span>,<span style="line-height:1.5 !important;"> database </span>= <span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">ngx_lua</span><span style="font-weight:bold;line-height:1.5 !important;">"</span>,<span style="line-height:1.5 !important;"> user </span>= <span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">root</span><span style="font-weight:bold;line-height:1.5 !important;">"</span>,<span style="line-height:1.5 !important;"> password</span>=<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">digdeep</span><span style="font-weight:bold;line-height:1.5 !important;">"</span>,<span style="line-height:1.5 !important;"> max_packet_size </span>= <span style="color:#800000;line-height:1.5 !important;">1024</span> * <span style="color:#800000;line-height:1.5 !important;">1024</span><span style="line-height:1.5 !important;"> } </span><span style="color:#0000FF;line-height:1.5 !important;">if</span><span style="line-height:1.5 !important;"> not ok then
        ngx</span>.say(<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">failed to connect: </span><span style="font-weight:bold;line-height:1.5 !important;">"</span>, err, <span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">: </span><span style="font-weight:bold;line-height:1.5 !important;">"</span>, errno, <span style="font-weight:bold;line-height:1.5 !important;">"</span> <span style="font-weight:bold;line-height:1.5 !important;">"</span>,<span style="line-height:1.5 !important;"> sqlstate) </span><span style="color:#0000FF;line-height:1.5 !important;">return</span><span style="line-height:1.5 !important;"> end

ngx</span>.say(<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">connected to mysql.</span><span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="line-height:1.5 !important;">) </span><span style="color:#0000FF;line-height:1.5 !important;">local</span> res, err, errno, sqlstate = db:query(<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">drop table if exists cats</span><span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="line-height:1.5 !important;">) </span><span style="color:#0000FF;line-height:1.5 !important;">if</span><span style="line-height:1.5 !important;"> not res then
        ngx</span>.say(<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">bad result: </span><span style="font-weight:bold;line-height:1.5 !important;">"</span>, err, <span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">: </span><span style="font-weight:bold;line-height:1.5 !important;">"</span>, errno, <span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">: </span><span style="font-weight:bold;line-height:1.5 !important;">"</span>, sqlstate, <span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">.</span><span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="line-height:1.5 !important;">) </span><span style="color:#0000FF;line-height:1.5 !important;">return</span><span style="line-height:1.5 !important;"> end

res</span>, err, errno, sqlstate = db:query(<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">create table cats </span><span style="font-weight:bold;line-height:1.5 !important;">"</span> .. <span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">(id int not null primary key auto_increment, </span><span style="font-weight:bold;line-height:1.5 !important;">"</span> .. <span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">name varchar(30))</span><span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="line-height:1.5 !important;">) </span><span style="color:#0000FF;line-height:1.5 !important;">if</span><span style="line-height:1.5 !important;"> not res then
        ngx</span>.say(<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">bad result: </span><span style="font-weight:bold;line-height:1.5 !important;">"</span>, err, <span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">: </span><span style="font-weight:bold;line-height:1.5 !important;">"</span>, errno, <span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">: </span><span style="font-weight:bold;line-height:1.5 !important;">"</span>, sqlstate, <span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">.</span><span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="line-height:1.5 !important;">) </span><span style="color:#0000FF;line-height:1.5 !important;">return</span><span style="line-height:1.5 !important;"> end

ngx</span>.say(<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">table cats created.</span><span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="line-height:1.5 !important;">)

res</span>, err, errno, sqlstate = db:query(<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">insert into cats(name) </span><span style="font-weight:bold;line-height:1.5 !important;">"</span> .. <span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">values (\'Bob\'),(\'\'),(null)</span><span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="line-height:1.5 !important;">) </span><span style="color:#0000FF;line-height:1.5 !important;">if</span><span style="line-height:1.5 !important;"> not res then
        ngx</span>.say(<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">bad request: </span><span style="font-weight:bold;line-height:1.5 !important;">"</span>, err, <span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">: </span><span style="font-weight:bold;line-height:1.5 !important;">"</span>, errno, <span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">: </span><span style="font-weight:bold;line-height:1.5 !important;">"</span>, sqlstate, <span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">.</span><span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="line-height:1.5 !important;">) </span><span style="color:#0000FF;line-height:1.5 !important;">return</span><span style="line-height:1.5 !important;"> end

ngx</span>.say(res.affected_rows, <span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;"> rows inserted into table cats </span><span style="font-weight:bold;line-height:1.5 !important;">"</span>, <span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">(last insert id: </span><span style="font-weight:bold;line-height:1.5 !important;">"</span>, res.insert_id, <span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">)</span><span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="line-height:1.5 !important;">)

res</span>, err, errno, sqlstate = db:query(<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">select * from cats order by id asc</span><span style="font-weight:bold;line-height:1.5 !important;">"</span>, <span style="color:#800000;line-height:1.5 !important;">10</span><span style="line-height:1.5 !important;">) </span><span style="color:#0000FF;line-height:1.5 !important;">if</span><span style="line-height:1.5 !important;"> not res then
        ngx</span>.say(<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">bad result </span><span style="font-weight:bold;line-height:1.5 !important;">"</span>, err, <span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">: </span><span style="font-weight:bold;line-height:1.5 !important;">"</span>, errno, <span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">: </span><span style="font-weight:bold;line-height:1.5 !important;">"</span>, sqlstate, <span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">.</span><span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="line-height:1.5 !important;">) </span><span style="color:#0000FF;line-height:1.5 !important;">return</span><span style="line-height:1.5 !important;"> end </span><span style="color:#0000FF;line-height:1.5 !important;">local</span> cjson = <span style="color:#0000FF;line-height:1.5 !important;">require</span> <span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">cjson</span><span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="line-height:1.5 !important;"> ngx</span>.say(<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">result: </span><span style="font-weight:bold;line-height:1.5 !important;">"</span>, cjson.<span style="line-height:1.5 !important;">encode(res)) </span><span style="color:#0000FF;line-height:1.5 !important;">local</span> ok, err = db:set_keepalive(<span style="color:#800000;line-height:1.5 !important;">1000</span>, <span style="color:#800000;line-height:1.5 !important;">100</span><span style="line-height:1.5 !important;">) </span><span style="color:#0000FF;line-height:1.5 !important;">if</span><span style="line-height:1.5 !important;"> not ok then
        ngx</span>.say(<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">failed to set keepalive: </span><span style="font-weight:bold;line-height:1.5 !important;">"</span>,<span style="line-height:1.5 !important;"> err) </span><span style="color:#0000FF;line-height:1.5 !important;">return</span><span style="line-height:1.5 !important;"> end</span></pre>
		<div class="cnblogs_code_toolbar" style="margin-top:5px;">
			<span class="cnblogs_code_copy" style="padding-right:5px;line-height:1.5 !important;"><a title="复制代码" style="color:navy;border:none !important;"><img src="http://common.cnblogs.com/images/copycode.gif" alt="复制代码" style="max-width:900px;border-width:initial !important;border-style:none !important;" /></a></span>
		</div>
	</div>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		测试：
	</p>
	<div class="cnblogs_code" style="background-color:#F5F5F5;border:1px solid #CCCCCC;padding:5px;overflow:auto;margin:5px 0px;white-space:normal;font-family:&quot;">
<pre style="margin-top:0px;margin-bottom:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">[root<span style="color:#800080;line-height:1.5 !important;">@localhost</span> lua]<span style="color:#008000;line-height:1.5 !important;">#</span><span style="color:#008000;line-height:1.5 !important;"> curl localhost/mysql_test</span> connected to mysql.<span style="line-height:1.5 !important;"> table cats created</span>. <span style="color:#800000;line-height:1.5 !important;">3</span> rows inserted into table cats (<span style="color:#0000FF;line-height:1.5 !important;">last</span> insert id: <span style="color:#800000;line-height:1.5 !important;">1</span><span style="line-height:1.5 !important;">)
result</span>: [{<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">name</span><span style="font-weight:bold;line-height:1.5 !important;">"</span>:<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">Bob</span><span style="font-weight:bold;line-height:1.5 !important;">"</span>,<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">id</span><span style="font-weight:bold;line-height:1.5 !important;">"</span>:<span style="color:#800000;line-height:1.5 !important;">1</span>},{<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">name</span><span style="font-weight:bold;line-height:1.5 !important;">"</span>:<span style="font-weight:bold;line-height:1.5 !important;">""</span>,<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">id</span><span style="font-weight:bold;line-height:1.5 !important;">"</span>:<span style="color:#800000;line-height:1.5 !important;">2</span>},{<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">name</span><span style="font-weight:bold;line-height:1.5 !important;">"</span>:null,<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">id</span><span style="font-weight:bold;line-height:1.5 !important;">"</span>:<span style="color:#800000;line-height:1.5 !important;">3</span>}]</pre>
	</div>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		测试通过。
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		<span style="line-height:1.5;color:#FF0000;"><strong>5. lua 的 capture 和 capture_multi(子查询)</strong></span>
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		<span style="line-height:1.5;color:#0000FF;">capture_multi 是 openresty 一个十分强大的功能</span>。它能<span style="line-height:1.5;color:#0000FF;">极大的减少前端浏览器发送的http请求的数量，突破了浏览器对于同一个服务器并发请求数量的限制</span>，因为他可以<span style="line-height:1.5;color:#0000FF;">将前端的多个http请求减少为只要一个http请求到nginx，然后nginx使用capture_multi特性，对后端发起多个异步并发请求，然后统一将结果返回给前端</span>。下面看一个例子：
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		首先在nginx.conf中加入下面的 location 配置，并且配置好 nginx 访问 php 的配置：
	</p>
	<div class="cnblogs_code" style="background-color:#F5F5F5;border:1px solid #CCCCCC;padding:5px;overflow:auto;margin:5px 0px;white-space:normal;font-family:&quot;">
		<div>
			按 Ctrl+C 复制代码
		</div>
<textarea style="font-size:12px;font-family:&quot;width:1648px;height:220.8px;line-height:1.5;"></textarea>
		<div>
			按 Ctrl+C 复制代码
		</div>
	</div>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		capture.lua 的代码如下：
	</p>
	<div class="cnblogs_code" style="background-color:#F5F5F5;border:1px solid #CCCCCC;padding:5px;overflow:auto;margin:5px 0px;white-space:normal;font-family:&quot;">
		<div>
			按 Ctrl+C 复制代码
		</div>
<textarea style="font-size:12px;font-family:&quot;width:1648px;height:326.4px;line-height:1.5;"></textarea>
		<div>
			按 Ctrl+C 复制代码
		</div>
	</div>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		index.php 代码：
	</p>
	<div class="cnblogs_code" style="background-color:#F5F5F5;border:1px solid #CCCCCC;padding:5px;overflow:auto;margin:5px 0px;white-space:normal;font-family:&quot;">
<pre style="margin-top:0px;margin-bottom:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">[root<span style="color:#800080;line-height:1.5 !important;">@localhost</span> html]<span style="color:#008000;line-height:1.5 !important;">#</span><span style="color:#008000;line-height:1.5 !important;"> pwd</span> /opt/openresty/nginx/<span style="line-height:1.5 !important;">html
[root</span><span style="color:#800080;line-height:1.5 !important;">@localhost</span> html]<span style="color:#008000;line-height:1.5 !important;">#</span><span style="color:#008000;line-height:1.5 !important;"> cat index.php</span> &lt;?<span style="line-height:1.5 !important;">php
        echo phpinfo(); </span>?&gt;</pre>
	</div>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		访问：
	</p>
	<div class="cnblogs_code" style="background-color:#F5F5F5;border:1px solid #CCCCCC;padding:5px;overflow:auto;margin:5px 0px;white-space:normal;font-family:&quot;">
		<div class="cnblogs_code_toolbar" style="margin-top:5px;">
			<span class="cnblogs_code_copy" style="padding-right:5px;line-height:1.5 !important;"><a title="复制代码" style="color:navy;border:none !important;"><img src="http://common.cnblogs.com/images/copycode.gif" alt="复制代码" style="max-width:900px;border-width:initial !important;border-style:none !important;" /></a></span>
		</div>
<pre style="margin-top:0px;margin-bottom:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">[root<span style="color:#800080;line-height:1.5 !important;">@localhost</span> html]<span style="color:#008000;line-height:1.5 !important;">#</span><span style="color:#008000;line-height:1.5 !important;"> curl localhost/capture</span> connected to mysql.<span style="line-height:1.5 !important;"> table cats created</span>. <span style="color:#800000;line-height:1.5 !important;">3</span> rows inserted into table cats (<span style="color:#0000FF;line-height:1.5 !important;">last</span> insert id: <span style="color:#800000;line-height:1.5 !important;">1</span><span style="line-height:1.5 !important;">)
result</span>: [{<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">name</span><span style="font-weight:bold;line-height:1.5 !important;">"</span>:<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">Bob</span><span style="font-weight:bold;line-height:1.5 !important;">"</span>,<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">id</span><span style="font-weight:bold;line-height:1.5 !important;">"</span>:<span style="color:#800000;line-height:1.5 !important;">1</span>},{<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">name</span><span style="font-weight:bold;line-height:1.5 !important;">"</span>:<span style="font-weight:bold;line-height:1.5 !important;">""</span>,<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">id</span><span style="font-weight:bold;line-height:1.5 !important;">"</span>:<span style="color:#800000;line-height:1.5 !important;">2</span>},{<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">name</span><span style="font-weight:bold;line-height:1.5 !important;">"</span>:null,<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">id</span><span style="font-weight:bold;line-height:1.5 !important;">"</span>:<span style="color:#800000;line-height:1.5 !important;">3</span><span style="line-height:1.5 !important;">}]

set result</span>: <span style="color:#800000;line-height:1.5 !important;">1</span><span style="line-height:1.5 !important;"> dog</span>:<span style="line-height:1.5 !important;"> an animal

hello ngx_lua</span>!!!!<span style="line-height:1.5 !important;"> false </span><span style="color:#800000;line-height:1.5 !important;">200</span><span style="line-height:1.5 !important;"> nil</span></pre>
		<div class="cnblogs_code_toolbar" style="margin-top:5px;">
			<span class="cnblogs_code_copy" style="padding-right:5px;line-height:1.5 !important;"><a title="复制代码" style="color:navy;border:none !important;"><img src="http://common.cnblogs.com/images/copycode.gif" alt="复制代码" style="max-width:900px;border-width:initial !important;border-style:none !important;" /></a></span>
		</div>
	</div>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		可以看到访问成功了。<span style="line-height:1.5;font-weight:bold;">/mysql_test</span>，<span style="line-height:1.5;font-weight:bold;">/redis_test,&nbsp;<span style="line-height:1.5;">/lua,&nbsp;<span style="line-height:1.5;">/index.php 四个请求的结果都输出了。</span></span></span>
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		<span style="line-height:1.5;">注意：</span>
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		<span style="line-height:1.5;">ngx.location.<span style="line-height:1.5;">capture_multi{... ...</span>} 中的多个异步并发请求<span style="line-height:1.5;color:#0000FF;">可以是 nginx.conf 中配置的 location</span>(比如 /mysql_test, /redis_test, /lua)，<span style="line-height:1.5;color:#0000FF;">也可以不是 location配置的路径，比如 index.php 就不是</span>。index.php 就是一个简单的后台php 脚本。当然也可以是一个 java 实现的后台接口。</span>
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		<span style="line-height:1.5;color:#FF0000;"><strong>6. openresty的缓存 lua_shared_dict<br />
</strong></span>
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		定义一个缓存：
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		在nginx的配置文件 nginx.conf 的 http 端下面加入指令：
	</p>
	<div class="cnblogs_code" style="background-color:#F5F5F5;border:1px solid #CCCCCC;padding:5px;overflow:auto;margin:5px 0px;white-space:normal;font-family:&quot;">
<pre style="margin-top:0px;margin-bottom:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">lua_shared_dict ngx_cache 128m;</pre>
	</div>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		就定义了一个 名称为 ngx_cache 大小为128m的内存用于缓存，注意该缓存是所有nginx work process所共享的。
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		在lua脚本中访问缓存：
	</p>
	<div class="cnblogs_code" style="background-color:#F5F5F5;border:1px solid #CCCCCC;padding:5px;overflow:auto;margin:5px 0px;white-space:normal;font-family:&quot;">
<pre style="margin-top:0px;margin-bottom:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;"><span style="color:#0000FF;line-height:1.5 !important;">local</span> ngx_cache = ngx.shared.<span style="line-height:1.5 !important;">ngx_cache </span><span style="color:#0000FF;line-height:1.5 !important;">local</span> value = ngx_cache:<span style="line-height:1.5 !important;">get(key) </span><span style="color:#0000FF;line-height:1.5 !important;">local</span> succ, err, forcible = ngx_cache:set(key, value, exptime)</pre>
	</div>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		下面测试一下，首先在 nginx.conf的server端中加入：
	</p>
	<div class="cnblogs_code" style="background-color:#F5F5F5;border:1px solid #CCCCCC;padding:5px;overflow:auto;margin:5px 0px;white-space:normal;font-family:&quot;">
<pre style="margin-top:0px;margin-bottom:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">        location /<span style="line-height:1.5 !important;">cache {
            content_by_lua_file lua</span>/cache.<span style="line-height:1.5 !important;">lua;
        }</span></pre>
	</div>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		然后编写 cache.lua 脚本：
	</p>
	<div class="cnblogs_code" style="background-color:#F5F5F5;border:1px solid #CCCCCC;padding:5px;overflow:auto;margin:5px 0px;white-space:normal;font-family:&quot;">
		<div class="cnblogs_code_toolbar" style="margin-top:5px;">
			<span class="cnblogs_code_copy" style="padding-right:5px;line-height:1.5 !important;"><a title="复制代码" style="color:navy;border:none !important;"><img src="http://common.cnblogs.com/images/copycode.gif" alt="复制代码" style="max-width:900px;border-width:initial !important;border-style:none !important;" /></a></span>
		</div>
<pre style="margin-top:0px;margin-bottom:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">[root<span style="color:#800080;line-height:1.5 !important;">@localhost</span> lua]<span style="color:#008000;line-height:1.5 !important;">#</span><span style="color:#008000;line-height:1.5 !important;"> cat cache.lua</span> <span style="color:#0000FF;line-height:1.5 !important;">local</span> redis = <span style="color:#0000FF;line-height:1.5 !important;">require</span> <span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">resty.redis</span><span style="font-weight:bold;line-height:1.5 !important;">"</span> <span style="color:#0000FF;line-height:1.5 !important;">local</span> red = redis:<span style="line-height:1.5 !important;">new()

function set_to_cache(key</span>, value,<span style="line-height:1.5 !important;"> exptime) </span><span style="color:#0000FF;line-height:1.5 !important;">if</span><span style="line-height:1.5 !important;"> not exptime then
                exptime </span>= <span style="color:#800000;line-height:1.5 !important;">0</span><span style="line-height:1.5 !important;"> end </span><span style="color:#0000FF;line-height:1.5 !important;">local</span> ngx_cache = ngx.shared.<span style="line-height:1.5 !important;">ngx_cache </span><span style="color:#0000FF;line-height:1.5 !important;">local</span> succ, err, forcible = ngx_cache:set(key, value,<span style="line-height:1.5 !important;"> exptime) </span><span style="color:#0000FF;line-height:1.5 !important;">return</span><span style="line-height:1.5 !important;"> succ
end

function get_from_cache(key) </span><span style="color:#0000FF;line-height:1.5 !important;">local</span> ngx_cache = ngx.shared.<span style="line-height:1.5 !important;">ngx_cache; </span><span style="color:#0000FF;line-height:1.5 !important;">local</span> value = ngx_cache:<span style="line-height:1.5 !important;">get(key) </span><span style="color:#0000FF;line-height:1.5 !important;">if</span><span style="line-height:1.5 !important;"> not value then
                value </span>=<span style="line-height:1.5 !important;"> get_from_redis(key)
                set_to_cache(key</span>,<span style="line-height:1.5 !important;"> value) </span><span style="color:#0000FF;line-height:1.5 !important;">return</span><span style="line-height:1.5 !important;"> value
        end

        ngx</span>.say(<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">get from cache.</span><span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="line-height:1.5 !important;">) </span><span style="color:#0000FF;line-height:1.5 !important;">return</span><span style="line-height:1.5 !important;"> value
end

function get_from_redis(key)
        red</span>:set_timeout(<span style="color:#800000;line-height:1.5 !important;">1000</span><span style="line-height:1.5 !important;">) </span><span style="color:#0000FF;line-height:1.5 !important;">local</span> ok, err = red:<span style="color:#0000FF;line-height:1.5 !important;">connect</span>(<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">127.0.0.1</span><span style="font-weight:bold;line-height:1.5 !important;">"</span>, <span style="color:#800000;line-height:1.5 !important;">6379</span><span style="line-height:1.5 !important;">) </span><span style="color:#0000FF;line-height:1.5 !important;">if</span><span style="line-height:1.5 !important;"> not ok then
                ngx</span>.say(<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">failed to connect: </span><span style="font-weight:bold;line-height:1.5 !important;">"</span>,<span style="line-height:1.5 !important;"> err) </span><span style="color:#0000FF;line-height:1.5 !important;">return</span><span style="line-height:1.5 !important;"> end </span><span style="color:#0000FF;line-height:1.5 !important;">local</span> res, err = red:<span style="line-height:1.5 !important;">get(key) </span><span style="color:#0000FF;line-height:1.5 !important;">if</span><span style="line-height:1.5 !important;"> not res then
                ngx</span>.say(<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">failed to get doy: </span><span style="font-weight:bold;line-height:1.5 !important;">"</span>,<span style="line-height:1.5 !important;"> err) </span><span style="color:#0000FF;line-height:1.5 !important;">return</span> ngx.<span style="line-height:1.5 !important;">null
        end

        ngx</span>.say(<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">get from redis.</span><span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="line-height:1.5 !important;">) </span><span style="color:#0000FF;line-height:1.5 !important;">return</span><span style="line-height:1.5 !important;"> res
end

function set_to_redis(key</span>,<span style="line-height:1.5 !important;"> value)
        red</span>:set_timeout(<span style="color:#800000;line-height:1.5 !important;">1000</span><span style="line-height:1.5 !important;">) </span><span style="color:#0000FF;line-height:1.5 !important;">local</span> ok, err = red:<span style="color:#0000FF;line-height:1.5 !important;">connect</span>(<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">127.0.0.1</span><span style="font-weight:bold;line-height:1.5 !important;">"</span>, <span style="color:#800000;line-height:1.5 !important;">6379</span><span style="line-height:1.5 !important;">) </span><span style="color:#0000FF;line-height:1.5 !important;">if</span><span style="line-height:1.5 !important;"> not ok then
                ngx</span>.say(<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">failed to connect: </span><span style="font-weight:bold;line-height:1.5 !important;">"</span>,<span style="line-height:1.5 !important;"> err) </span><span style="color:#0000FF;line-height:1.5 !important;">return</span><span style="line-height:1.5 !important;"> end </span><span style="color:#0000FF;line-height:1.5 !important;">local</span> ok, err = red:set(key,<span style="line-height:1.5 !important;"> value) </span><span style="color:#0000FF;line-height:1.5 !important;">if</span><span style="line-height:1.5 !important;"> not ok then
                ngx</span>.say(<span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">failed to set to redis: </span><span style="font-weight:bold;line-height:1.5 !important;">"</span>,<span style="line-height:1.5 !important;"> err) </span><span style="color:#0000FF;line-height:1.5 !important;">return</span><span style="line-height:1.5 !important;"> end </span><span style="color:#0000FF;line-height:1.5 !important;">return</span><span style="line-height:1.5 !important;"> ok
end

set_to_redis(</span><span style="font-weight:bold;line-height:1.5 !important;">'</span><span style="font-weight:bold;line-height:1.5 !important;">dog</span><span style="font-weight:bold;line-height:1.5 !important;">'</span>, <span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="font-weight:bold;line-height:1.5 !important;">Bob</span><span style="font-weight:bold;line-height:1.5 !important;">"</span><span style="line-height:1.5 !important;">) </span><span style="color:#0000FF;line-height:1.5 !important;">local</span> rs = get_from_cache(<span style="font-weight:bold;line-height:1.5 !important;">'</span><span style="font-weight:bold;line-height:1.5 !important;">dog</span><span style="font-weight:bold;line-height:1.5 !important;">'</span><span style="line-height:1.5 !important;">)
ngx</span>.say(rs)</pre>
		<div class="cnblogs_code_toolbar" style="margin-top:5px;">
			<span class="cnblogs_code_copy" style="padding-right:5px;line-height:1.5 !important;"><a title="复制代码" style="color:navy;border:none !important;"><img src="http://common.cnblogs.com/images/copycode.gif" alt="复制代码" style="max-width:900px;border-width:initial !important;border-style:none !important;" /></a></span>
		</div>
	</div>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		测试：
	</p>
	<div class="cnblogs_code" style="background-color:#F5F5F5;border:1px solid #CCCCCC;padding:5px;overflow:auto;margin:5px 0px;white-space:normal;font-family:&quot;">
		<div class="cnblogs_code_toolbar" style="margin-top:5px;">
			<span class="cnblogs_code_copy" style="padding-right:5px;line-height:1.5 !important;"><a title="复制代码" style="color:navy;border:none !important;"><img src="http://common.cnblogs.com/images/copycode.gif" alt="复制代码" style="max-width:900px;border-width:initial !important;border-style:none !important;" /></a></span>
		</div>
<pre style="margin-top:0px;margin-bottom:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">[root<span style="color:#800080;line-height:1.5 !important;">@localhost</span> ~]<span style="color:#008000;line-height:1.5 !important;">#</span><span style="color:#008000;line-height:1.5 !important;"> curl localhost/cache</span> get from redis.<span style="line-height:1.5 !important;"> Bob
[root</span><span style="color:#800080;line-height:1.5 !important;">@localhost</span> ~]<span style="color:#008000;line-height:1.5 !important;">#</span><span style="color:#008000;line-height:1.5 !important;"> curl localhost/cache</span> get from cache.<span style="line-height:1.5 !important;"> Bob
[root</span><span style="color:#800080;line-height:1.5 !important;">@localhost</span> ~]<span style="color:#008000;line-height:1.5 !important;">#</span><span style="color:#008000;line-height:1.5 !important;"> curl localhost/cache</span> get from cache.<span style="line-height:1.5 !important;"> Bob</span></pre>
		<div class="cnblogs_code_toolbar" style="margin-top:5px;">
			<span class="cnblogs_code_copy" style="padding-right:5px;line-height:1.5 !important;"><a title="复制代码" style="color:navy;border:none !important;"><img src="http://common.cnblogs.com/images/copycode.gif" alt="复制代码" style="max-width:900px;border-width:initial !important;border-style:none !important;" /></a></span>
		</div>
	</div>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		第一次从 redis中获取，以后每次都从cache中获取。
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		可以使用 ab 测试一下rps(Requests per second):
	</p>
	<div class="cnblogs_code" style="background-color:#F5F5F5;border:1px solid #CCCCCC;padding:5px;overflow:auto;margin:5px 0px;white-space:normal;font-family:&quot;">
<pre style="margin-top:0px;margin-bottom:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;"> ab -n <span style="color:#800000;line-height:1.5 !important;">1000</span> -c <span style="color:#800000;line-height:1.5 !important;">100</span> -k http://<span style="color:#800000;line-height:1.5 !important;">127.0</span>.<span style="color:#800000;line-height:1.5 !important;">0.1</span>/cache</pre>
	</div>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		<span style="line-height:1.5;color:#FF0000;"><strong>7. 解决缓存失效风暴 lua-resty-lock<br />
</strong></span>
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		缓存失效风暴是指缓存因为时间过期而失效时，会导致所有的请求都去访问 后台的redis或者mysql，而导致CPU性能即刻增长的现象。所以关键是当缓存失效时，用lock保证只有一个线程去访问后台的redis或者mysql，然后更新缓存。需要使用到 lua-resty-lock 模块的加锁、解锁功能。
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		lua-resty-lock 文档：https://github.com/openresty/lua-resty-lock
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		首先在nginx.conf 的 http 端下面加入指令：
	</p>
	<div class="cnblogs_code" style="background-color:#F5F5F5;border:1px solid #CCCCCC;padding:5px;overflow:auto;margin:5px 0px;white-space:normal;font-family:&quot;">
<pre style="margin-top:0px;margin-bottom:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">lua_shared_dict ngx_cache 128m; <span style="color:#008000;line-height:1.5 !important;">#</span><span style="color:#008000;line-height:1.5 !important;"> cache</span> lua_shared_dict cache_lock 100k; <span style="color:#008000;line-height:1.5 !important;">#</span><span style="color:#008000;line-height:1.5 !important;"> lock for cache</span></pre>
	</div>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		然后在nginx.conf的server端中加入：
	</p>
	<div class="cnblogs_code" style="background-color:#F5F5F5;border:1px solid #CCCCCC;padding:5px;overflow:auto;margin:5px 0px;white-space:normal;font-family:&quot;">
<pre style="margin-top:0px;margin-bottom:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">        location /<span style="line-height:1.5 !important;">cache_lock {
            content_by_lua_file lua</span>/cache_lock.<span style="line-height:1.5 !important;">lua;
        }</span></pre>
	</div>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		cache_lock.lua代码：
	</p>
	<div class="cnblogs_code" style="background-color:#F5F5F5;border:1px solid #CCCCCC;padding:5px;overflow:auto;margin:5px 0px;white-space:normal;font-family:&quot;">
		<img id="code_img_closed_24d153bf-23d6-4cfa-8f7b-a77525a9e52d" class="code_img_closed" src="http://images.cnblogs.com/OutliningIndicators/ContractedBlock.gif" alt="" style="vertical-align:middle;padding-right:5px;max-width:900px;" />&nbsp;<span class="cnblogs_code_collapse" style="border-width:1px;border-style:solid;border-color:gray;background-color:#FFFFFF;padding:2px;line-height:1.5 !important;">View Code</span>
	</div>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		测试：
	</p>
	<div class="cnblogs_code" style="background-color:#F5F5F5;border:1px solid #CCCCCC;padding:5px;overflow:auto;margin:5px 0px;white-space:normal;font-family:&quot;">
<pre style="margin-top:0px;margin-bottom:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">[root<span style="color:#800080;line-height:1.5 !important;">@localhost</span> lua]<span style="color:#008000;line-height:1.5 !important;">#</span><span style="color:#008000;line-height:1.5 !important;"> curl localhost/cache_lock</span> get from cache.<span style="line-height:1.5 !important;"> Bob
[root</span><span style="color:#800080;line-height:1.5 !important;">@localhost</span> lua]<span style="color:#008000;line-height:1.5 !important;">#</span><span style="color:#008000;line-height:1.5 !important;"> curl localhost/cache_lock</span> get from cache.<span style="line-height:1.5 !important;"> Bob</span></pre>
	</div>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		<span style="line-height:1.5;color:#FF0000;"><strong>7. openresty 执行阶段</strong></span>
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		nginx的执行阶段分成了很多个阶段,所以第三方模块就可以在某个适当的阶段加入一些处理。openresty进行了简化成了7个阶段：
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		<img src="http://images2015.cnblogs.com/blog/699877/201510/699877-20151008205649174-725211688.png" alt="" style="max-width:900px;" />
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		7个阶段的执行顺序如下：
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		set_by_lua: 流程分支判断，判断变量初始哈
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		rewrite_by_lua: 用lua脚本实现nginx rewrite
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		access_by_lua: ip准入，是否能合法性访问，防火墙
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		content_by_lua: 内存生成
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		header_filter_by_lua：过滤http头信息，增加头信息
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		body_filter_by_lua: 内容大小写，内容加密
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		log_by_lua: 本地/远程记录日志
	</p>
	<p style="font-size:13px;line-height:1.5;margin:10px auto;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
		但是其实我们可以只用 content_by_lua，所有功能都在该阶段完成，也是可以的。
	</p>
</p>