<h1 style="margin:0px;padding:0px;font-family:Arial;white-space:normal;background-color:#FFFFFF;">
	OpenResty
</h1>
<span style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">OpenResty ™ 是一个基于 Nginx 与 Lua 的高性能 Web 平台，其内部集成了大量精良的 Lua 库、第三方模块以及大多数的依赖项。用于方便地搭建能够处理超高并发、扩展性极高的动态 Web 应用、Web 服务和动态网关。</span><br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">OpenResty 通过汇聚各种设计精良的 Nginx 模块（主要由 OpenResty 团队自主开发），从而将 Nginx 有效地变成一个强大的通用 Web 应用平台。这样，Web 开发人员和系统工程师可以使用 Lua 脚本语言调动 Nginx 支持的各种 C 以及 Lua 模块，快速构造出足以胜任 10K 乃至 1000K 以上单机并发连接的高性能 Web 应用系统。</span><br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	OpenResty 的目标是让你的Web服务直接跑在 Nginx 服务内部，充分利用 Nginx 的非阻塞 I/O 模型，不仅仅对 HTTP 客户端请求,甚至于对远程后端诸如&nbsp;<a href="http://lib.csdn.net/base/mysql" class="replace_word" title="MySQL知识库" target="_blank" style="color:#DF3434;text-decoration-line:none;font-weight:bold;">MySQL</a>、PostgreSQL、Memcached 以及&nbsp;<a href="http://lib.csdn.net/base/redis" class="replace_word" title="Redis知识库" target="_blank" style="color:#DF3434;text-decoration-line:none;font-weight:bold;">Redis</a>&nbsp;等都进行一致的高性能响应。
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<br />
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	目前openresty的组件包括：<a target="_blank" href="http://openresty.org/en/components.html" style="color:#FF9900;text-decoration-line:none;">http://openresty.org/en/components.html</a>
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<br />
</p>
<h1 style="margin:0px;padding:0px;font-family:Arial;white-space:normal;background-color:#FFFFFF;">
	<a name="t1"></a>安装
</h1>
<div style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	您必须将这些库 perl 5.6.1+, libreadline, libpcre, libssl安装在您的电脑之中。 对于 Linux来说, 您需要确认使用 ldconfig 命令，让其在您的系统环境路径中能找到它们。<br />
<br />
	<h2 style="margin:0px;padding:0px;">
		<a name="t2"></a>Debian 和 Ubuntu 用户
	</h2>
推荐您使用 apt-get安装以下的开发库:<br />
	<div class="dp-highlighter bg_html" style="font-family:Consolas, &quot;font-size:12px;background-color:#E7E5DC;width:936.531px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;margin:18px 0px !important;">
		<div class="bar" style="padding-left:45px;">
			<div class="tools" style="padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;">
				<b>[html]</b>&nbsp;<a href="http://blog.csdn.net/yoara/article/details/52484268#" class="ViewSource" title="view plain" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span data-mod="popu_168">&nbsp;<a href="http://blog.csdn.net/yoara/article/details/52484268#" class="CopyToClipboard" title="copy" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a>
				<div style="position:absolute;left:723px;top:1091px;width:18px;height:18px;z-index:99;">
				</div>
</span><span data-mod="popu_169">&nbsp;</span><span class="tracking-ad" data-mod="popu_167"><a href="https://code.csdn.net/snippets/1873126" target="_blank" title="在CODE上查看代码片" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;"><img src="https://code.csdn.net/assets/CODE_ico.png" width="12" height="12" alt="在CODE上查看代码片" style="border-width:initial;border-style:none;max-width:100%;position:relative;top:1px;left:2px;" /></a></span><span class="tracking-ad" data-mod="popu_170"><a href="https://code.csdn.net/snippets/1873126/fork" target="_blank" title="派生到我的代码片" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;"><img src="https://code.csdn.net/assets/ico_fork.svg" width="12" height="12" alt="派生到我的代码片" style="border-width:initial;border-style:none;max-width:100%;position:relative;top:2px;left:2px;" /></a></span>
			</div>
		</div>
		<ol start="1" class="dp-xml" style="padding:0px;border:none;list-style-position:initial;list-style-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span style="margin:0px;padding:0px;border:none;background-color:inherit;">apt-get&nbsp;install&nbsp;libreadline-dev&nbsp;libncurses5-dev&nbsp;libpcre3-dev&nbsp;libssl-dev&nbsp;perl&nbsp;make&nbsp;build-essential&nbsp;&nbsp;</span></span>
			</li>
		</ol>
	</div>
<br />
	<h2 style="margin:0px;padding:0px;">
		<a name="t3"></a>Fedora 和 RedHat 用户
	</h2>
推荐您使用yum安装以下的开发库:<br />
	<div class="dp-highlighter bg_html" style="font-family:Consolas, &quot;font-size:12px;background-color:#E7E5DC;width:936.531px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;margin:18px 0px !important;">
		<div class="bar" style="padding-left:45px;">
			<div class="tools" style="padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;">
				<b>[html]</b>&nbsp;<a href="http://blog.csdn.net/yoara/article/details/52484268#" class="ViewSource" title="view plain" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span data-mod="popu_168">&nbsp;<a href="http://blog.csdn.net/yoara/article/details/52484268#" class="CopyToClipboard" title="copy" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a>
				<div style="position:absolute;left:723px;top:1256px;width:18px;height:18px;z-index:99;">
				</div>
</span><span data-mod="popu_169">&nbsp;</span><span class="tracking-ad" data-mod="popu_167"><a href="https://code.csdn.net/snippets/1873126" target="_blank" title="在CODE上查看代码片" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;"><img src="https://code.csdn.net/assets/CODE_ico.png" width="12" height="12" alt="在CODE上查看代码片" style="border-width:initial;border-style:none;max-width:100%;position:relative;top:1px;left:2px;" /></a></span><span class="tracking-ad" data-mod="popu_170"><a href="https://code.csdn.net/snippets/1873126/fork" target="_blank" title="派生到我的代码片" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;"><img src="https://code.csdn.net/assets/ico_fork.svg" width="12" height="12" alt="派生到我的代码片" style="border-width:initial;border-style:none;max-width:100%;position:relative;top:2px;left:2px;" /></a></span>
			</div>
		</div>
		<ol start="1" class="dp-xml" style="padding:0px;border:none;list-style-position:initial;list-style-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span style="margin:0px;padding:0px;border:none;background-color:inherit;">yum&nbsp;install&nbsp;readline-devel&nbsp;pcre-devel&nbsp;openssl-devel&nbsp;gcc&nbsp;&nbsp;</span></span>
			</li>
		</ol>
	</div>
	<h2 style="margin:0px;padding:0px;">
		<a name="t4"></a><br />
./configure
	</h2>
下载<a target="_blank" href="http://openresty.org/en/download.html" style="color:#FF9900;text-decoration-line:none;">预编译包</a>，然后在进入 openresty-VERSION/ 目录, 然后输入以下命令配置:<br />
<br />
./configure<br />
默认, --prefix=/usr/local/openresty 程序会被安装到/usr/local/openresty目录。<br />
您可以指定各种选项，比如<br />
	<div class="dp-highlighter bg_html" style="font-family:Consolas, &quot;font-size:12px;background-color:#E7E5DC;width:936.531px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;margin:18px 0px !important;">
		<div class="bar" style="padding-left:45px;">
			<div class="tools" style="padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;">
				<b>[html]</b>&nbsp;<a href="http://blog.csdn.net/yoara/article/details/52484268#" class="ViewSource" title="view plain" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span data-mod="popu_168">&nbsp;<a href="http://blog.csdn.net/yoara/article/details/52484268#" class="CopyToClipboard" title="copy" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a>
				<div style="position:absolute;left:723px;top:1577px;width:18px;height:18px;z-index:99;">
				</div>
</span><span data-mod="popu_169">&nbsp;</span><span class="tracking-ad" data-mod="popu_167"><a href="https://code.csdn.net/snippets/1873126" target="_blank" title="在CODE上查看代码片" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;"><img src="https://code.csdn.net/assets/CODE_ico.png" width="12" height="12" alt="在CODE上查看代码片" style="border-width:initial;border-style:none;max-width:100%;position:relative;top:1px;left:2px;" /></a></span><span class="tracking-ad" data-mod="popu_170"><a href="https://code.csdn.net/snippets/1873126/fork" target="_blank" title="派生到我的代码片" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;"><img src="https://code.csdn.net/assets/ico_fork.svg" width="12" height="12" alt="派生到我的代码片" style="border-width:initial;border-style:none;max-width:100%;position:relative;top:2px;left:2px;" /></a></span>
			</div>
		</div>
		<ol start="1" class="dp-xml" style="padding:0px;border:none;list-style-position:initial;list-style-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span style="margin:0px;padding:0px;border:none;background-color:inherit;">./configure&nbsp;</span><span class="attribute" style="margin:0px;padding:0px;border:none;color:red;background-color:inherit;">--prefix</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">=/opt/openresty&nbsp;\&nbsp;&nbsp;</span></span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;--with-luajit&nbsp;\&nbsp;&nbsp;</span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;--without-http_redis2_module&nbsp;\&nbsp;&nbsp;</span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;--with-http_iconv_module&nbsp;\&nbsp;&nbsp;</span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;--with-http_postgres_module&nbsp;&nbsp;</span>
			</li>
		</ol>
	</div>
<br />
试着使用 ./configure --help 查看更多的选项。<br />
配置文件（./configure script）运行出错可以到 build/nginx-VERSION/objs/autoconf.err 找到。 VERSION 的地方必须与OpenResty版本号相对应, 比如 1.11.2.1。<br />
</div>
<div style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<br />
</div>
<div style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	接着：
</div>
<div style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<div class="dp-highlighter bg_html" style="font-family:Consolas, &quot;font-size:12px;background-color:#E7E5DC;width:936.531px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;margin:18px 0px !important;">
		<div class="bar" style="padding-left:45px;">
			<div class="tools" style="padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;">
				<b>[html]</b>&nbsp;<a href="http://blog.csdn.net/yoara/article/details/52484268#" class="ViewSource" title="view plain" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span data-mod="popu_168">&nbsp;<a href="http://blog.csdn.net/yoara/article/details/52484268#" class="CopyToClipboard" title="copy" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a>
				<div style="position:absolute;left:723px;top:1918px;width:18px;height:18px;z-index:99;">
				</div>
</span><span data-mod="popu_169">&nbsp;</span><span class="tracking-ad" data-mod="popu_167"><a href="https://code.csdn.net/snippets/1873126" target="_blank" title="在CODE上查看代码片" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;"><img src="https://code.csdn.net/assets/CODE_ico.png" width="12" height="12" alt="在CODE上查看代码片" style="border-width:initial;border-style:none;max-width:100%;position:relative;top:1px;left:2px;" /></a></span><span class="tracking-ad" data-mod="popu_170"><a href="https://code.csdn.net/snippets/1873126/fork" target="_blank" title="派生到我的代码片" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;"><img src="https://code.csdn.net/assets/ico_fork.svg" width="12" height="12" alt="派生到我的代码片" style="border-width:initial;border-style:none;max-width:100%;position:relative;top:2px;left:2px;" /></a></span>
			</div>
		</div>
		<ol start="1" class="dp-xml" style="padding:0px;border:none;list-style-position:initial;list-style-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span style="margin:0px;padding:0px;border:none;background-color:inherit;">make&nbsp;&nbsp;</span></span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;</span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">make&nbsp;install&nbsp;&nbsp;</span>
			</li>
		</ol>
	</div>
<br />
安装完成后的目录大概是这样的
</div>
<div style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<div class="dp-highlighter bg_html" style="font-family:Consolas, &quot;font-size:12px;background-color:#E7E5DC;width:936.531px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;margin:18px 0px !important;">
		<div class="bar" style="padding-left:45px;">
			<div class="tools" style="padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;">
				<b>[html]</b>&nbsp;<a href="http://blog.csdn.net/yoara/article/details/52484268#" class="ViewSource" title="view plain" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span data-mod="popu_168">&nbsp;<a href="http://blog.csdn.net/yoara/article/details/52484268#" class="CopyToClipboard" title="copy" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a>
				<div style="position:absolute;left:723px;top:2093px;width:18px;height:18px;z-index:99;">
				</div>
</span><span data-mod="popu_169">&nbsp;</span><span class="tracking-ad" data-mod="popu_167"><a href="https://code.csdn.net/snippets/1873126" target="_blank" title="在CODE上查看代码片" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;"><img src="https://code.csdn.net/assets/CODE_ico.png" width="12" height="12" alt="在CODE上查看代码片" style="border-width:initial;border-style:none;max-width:100%;position:relative;top:1px;left:2px;" /></a></span><span class="tracking-ad" data-mod="popu_170"><a href="https://code.csdn.net/snippets/1873126/fork" target="_blank" title="派生到我的代码片" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;"><img src="https://code.csdn.net/assets/ico_fork.svg" width="12" height="12" alt="派生到我的代码片" style="border-width:initial;border-style:none;max-width:100%;position:relative;top:2px;left:2px;" /></a></span>
			</div>
		</div>
		<ol start="1" class="dp-xml" style="padding:0px;border:none;list-style-position:initial;list-style-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span style="margin:0px;padding:0px;border:none;background-color:inherit;">drwxr-xr-x.&nbsp;&nbsp;2&nbsp;root&nbsp;root&nbsp;&nbsp;&nbsp;4096&nbsp;9月&nbsp;&nbsp;&nbsp;1&nbsp;15:45&nbsp;bin&nbsp;&nbsp;</span></span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">drwxr-xr-x.&nbsp;&nbsp;6&nbsp;root&nbsp;root&nbsp;&nbsp;&nbsp;4096&nbsp;9月&nbsp;&nbsp;&nbsp;1&nbsp;15:45&nbsp;luajit&nbsp;&nbsp;</span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">drwxr-xr-x.&nbsp;&nbsp;6&nbsp;root&nbsp;root&nbsp;&nbsp;&nbsp;4096&nbsp;9月&nbsp;&nbsp;&nbsp;1&nbsp;15:45&nbsp;lualib&nbsp;&nbsp;</span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">drwxr-xr-x.&nbsp;11&nbsp;root&nbsp;root&nbsp;&nbsp;&nbsp;4096&nbsp;9月&nbsp;&nbsp;&nbsp;1&nbsp;15:46&nbsp;nginx&nbsp;&nbsp;</span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">drwxr-xr-x.&nbsp;41&nbsp;root&nbsp;root&nbsp;&nbsp;&nbsp;4096&nbsp;9月&nbsp;&nbsp;&nbsp;1&nbsp;15:45&nbsp;pod&nbsp;&nbsp;</span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">-rw-r--r--.&nbsp;&nbsp;1&nbsp;root&nbsp;root&nbsp;157757&nbsp;9月&nbsp;&nbsp;&nbsp;1&nbsp;15:45&nbsp;resty.index&nbsp;&nbsp;</span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">drwxr-xr-x.&nbsp;&nbsp;3&nbsp;root&nbsp;root&nbsp;&nbsp;&nbsp;4096&nbsp;9月&nbsp;&nbsp;&nbsp;1&nbsp;15:45&nbsp;site&nbsp;&nbsp;</span>
			</li>
		</ol>
	</div>
</div>
<div style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<br />
</div>
<h2 style="margin:0px;padding:0px;font-family:Arial;white-space:normal;background-color:#FFFFFF;">
	<a name="t5"></a>配置nginx
</h2>
<div style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	进入xx/openresty/nginx/conf目录
</div>
<div style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	编辑nginx.conf文件
</div>
<div style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	1.在http模块下加入：（路径替换成自己的）
</div>
<div style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<div class="dp-highlighter bg_html" style="font-family:Consolas, &quot;font-size:12px;background-color:#E7E5DC;width:936.531px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;margin:18px 0px !important;">
		<div class="bar" style="padding-left:45px;">
			<div class="tools" style="padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;">
				<b>[html]</b>&nbsp;<a href="http://blog.csdn.net/yoara/article/details/52484268#" class="ViewSource" title="view plain" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span data-mod="popu_168">&nbsp;<a href="http://blog.csdn.net/yoara/article/details/52484268#" class="CopyToClipboard" title="copy" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a>
				<div style="position:absolute;left:723px;top:2418px;width:18px;height:18px;z-index:99;">
				</div>
</span><span data-mod="popu_169">&nbsp;</span><span class="tracking-ad" data-mod="popu_167"><a href="https://code.csdn.net/snippets/1873126" target="_blank" title="在CODE上查看代码片" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;"><img src="https://code.csdn.net/assets/CODE_ico.png" width="12" height="12" alt="在CODE上查看代码片" style="border-width:initial;border-style:none;max-width:100%;position:relative;top:1px;left:2px;" /></a></span><span class="tracking-ad" data-mod="popu_170"><a href="https://code.csdn.net/snippets/1873126/fork" target="_blank" title="派生到我的代码片" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;"><img src="https://code.csdn.net/assets/ico_fork.svg" width="12" height="12" alt="派生到我的代码片" style="border-width:initial;border-style:none;max-width:100%;position:relative;top:2px;left:2px;" /></a></span>
			</div>
		</div>
		<ol start="1" class="dp-xml" style="padding:0px;border:none;list-style-position:initial;list-style-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span style="margin:0px;padding:0px;border:none;background-color:inherit;">lua_package_path&nbsp;"/opt/openresty/lualib/?.lua;;";&nbsp;&nbsp;#lua&nbsp;模块&nbsp;&nbsp;&nbsp;&nbsp;</span></span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">lua_package_cpath&nbsp;"/opt/openresty/lualib/?.so;;";&nbsp;&nbsp;#c模块&nbsp;&nbsp;&nbsp;&nbsp;</span>
			</li>
		</ol>
	</div>
	<div>
		<br />
	</div>
2.在server模块下引入，将所有需要lua处理的单独放在一个文件中
</div>
<div style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<div class="dp-highlighter bg_html" style="font-family:Consolas, &quot;font-size:12px;background-color:#E7E5DC;width:936.531px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;margin:18px 0px !important;">
		<div class="bar" style="padding-left:45px;">
			<div class="tools" style="padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;">
				<b>[html]</b>&nbsp;<a href="http://blog.csdn.net/yoara/article/details/52484268#" class="ViewSource" title="view plain" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span data-mod="popu_168">&nbsp;<a href="http://blog.csdn.net/yoara/article/details/52484268#" class="CopyToClipboard" title="copy" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a>
				<div style="position:absolute;left:723px;top:2575px;width:18px;height:18px;z-index:99;">
				</div>
</span><span data-mod="popu_169">&nbsp;</span><span class="tracking-ad" data-mod="popu_167"><a href="https://code.csdn.net/snippets/1873126" target="_blank" title="在CODE上查看代码片" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;"><img src="https://code.csdn.net/assets/CODE_ico.png" width="12" height="12" alt="在CODE上查看代码片" style="border-width:initial;border-style:none;max-width:100%;position:relative;top:1px;left:2px;" /></a></span><span class="tracking-ad" data-mod="popu_170"><a href="https://code.csdn.net/snippets/1873126/fork" target="_blank" title="派生到我的代码片" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;"><img src="https://code.csdn.net/assets/ico_fork.svg" width="12" height="12" alt="派生到我的代码片" style="border-width:initial;border-style:none;max-width:100%;position:relative;top:2px;left:2px;" /></a></span>
			</div>
		</div>
		<ol start="1" class="dp-xml" style="padding:0px;border:none;list-style-position:initial;list-style-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span style="margin:0px;padding:0px;border:none;background-color:inherit;">include&nbsp;../conf/myconf/luatest.conf;&nbsp;&nbsp;</span></span>
			</li>
		</ol>
	</div>
	<div>
		<br />
	</div>
luatest.con配置如下
</div>
<div style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<div class="dp-highlighter bg_html" style="font-family:Consolas, &quot;font-size:12px;background-color:#E7E5DC;width:936.531px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;margin:18px 0px !important;">
		<div class="bar" style="padding-left:45px;">
			<div class="tools" style="padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;">
				<b>[html]</b>&nbsp;<a href="http://blog.csdn.net/yoara/article/details/52484268#" class="ViewSource" title="view plain" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span data-mod="popu_168">&nbsp;<a href="http://blog.csdn.net/yoara/article/details/52484268#" class="CopyToClipboard" title="copy" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a>
				<div style="position:absolute;left:723px;top:2714px;width:18px;height:18px;z-index:99;">
				</div>
</span><span data-mod="popu_169">&nbsp;</span><span class="tracking-ad" data-mod="popu_167"><a href="https://code.csdn.net/snippets/1873126" target="_blank" title="在CODE上查看代码片" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;"><img src="https://code.csdn.net/assets/CODE_ico.png" width="12" height="12" alt="在CODE上查看代码片" style="border-width:initial;border-style:none;max-width:100%;position:relative;top:1px;left:2px;" /></a></span><span class="tracking-ad" data-mod="popu_170"><a href="https://code.csdn.net/snippets/1873126/fork" target="_blank" title="派生到我的代码片" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;"><img src="https://code.csdn.net/assets/ico_fork.svg" width="12" height="12" alt="派生到我的代码片" style="border-width:initial;border-style:none;max-width:100%;position:relative;top:2px;left:2px;" /></a></span>
			</div>
		</div>
		<ol start="1" class="dp-xml" style="padding:0px;border:none;list-style-position:initial;list-style-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span style="margin:0px;padding:0px;border:none;background-color:inherit;">location&nbsp;~&nbsp;/openapi/test/.*&nbsp;{&nbsp;&nbsp;</span></span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;default_type&nbsp;'text/html';&nbsp;&nbsp;</span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">#&nbsp;&nbsp;&nbsp;&nbsp;content_by_lua&nbsp;'ngx.say("hello")';&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;content_by_lua_file&nbsp;conf/myconf/lua/redis.lua;&nbsp;&nbsp;&nbsp;&nbsp;</span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">}&nbsp;&nbsp;</span>
			</li>
		</ol>
	</div>
<br />
redis.lua 脚本处理了一个非常常见的业务场景，就是使用nginx直接访问redis，脚本文件redis.lua内容如下
</div>
<div style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<div class="dp-highlighter bg_html" style="font-family:Consolas, &quot;font-size:12px;background-color:#E7E5DC;width:936.531px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;margin:18px 0px !important;">
		<div class="bar" style="padding-left:45px;">
			<div class="tools" style="padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;">
				<b>[html]</b>&nbsp;<a href="http://blog.csdn.net/yoara/article/details/52484268#" class="ViewSource" title="view plain" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span data-mod="popu_168">&nbsp;<a href="http://blog.csdn.net/yoara/article/details/52484268#" class="CopyToClipboard" title="copy" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a>
				<div style="position:absolute;left:723px;top:2925px;width:18px;height:18px;z-index:99;">
				</div>
</span><span data-mod="popu_169">&nbsp;</span><span class="tracking-ad" data-mod="popu_167"><a href="https://code.csdn.net/snippets/1873126" target="_blank" title="在CODE上查看代码片" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;"><img src="https://code.csdn.net/assets/CODE_ico.png" width="12" height="12" alt="在CODE上查看代码片" style="border-width:initial;border-style:none;max-width:100%;position:relative;top:1px;left:2px;" /></a></span><span class="tracking-ad" data-mod="popu_170"><a href="https://code.csdn.net/snippets/1873126/fork" target="_blank" title="派生到我的代码片" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;"><img src="https://code.csdn.net/assets/ico_fork.svg" width="12" height="12" alt="派生到我的代码片" style="border-width:initial;border-style:none;max-width:100%;position:relative;top:2px;left:2px;" /></a></span>
			</div>
		</div>
		<ol start="1" class="dp-xml" style="padding:0px;border:none;list-style-position:initial;list-style-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span style="margin:0px;padding:0px;border:none;background-color:inherit;">local&nbsp;function&nbsp;close_redis(red)&nbsp;&nbsp;</span></span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;if&nbsp;not&nbsp;red&nbsp;then&nbsp;&nbsp;</span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;return&nbsp;&nbsp;</span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;end&nbsp;&nbsp;</span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;</span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">--&nbsp;&nbsp;&nbsp;&nbsp;local&nbsp;ok,&nbsp;<span class="attribute" style="margin:0px;padding:0px;border:none;color:red;background-color:inherit;">err</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;=&nbsp;</span><span class="attribute-value" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">red</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">:close()&nbsp;&nbsp;&nbsp;&nbsp;</span></span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">--&nbsp;&nbsp;&nbsp;&nbsp;if&nbsp;not&nbsp;ok&nbsp;then&nbsp;&nbsp;&nbsp;&nbsp;</span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">--&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ngx.say("close&nbsp;redis&nbsp;error&nbsp;:&nbsp;",&nbsp;err)&nbsp;&nbsp;&nbsp;&nbsp;</span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">--&nbsp;&nbsp;&nbsp;&nbsp;end&nbsp;&nbsp;&nbsp;&nbsp;</span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;--释放连接(连接池实现)&nbsp;&nbsp;</span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;ngx.say("aaa")&nbsp;&nbsp;&nbsp;</span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;local&nbsp;<span class="attribute" style="margin:0px;padding:0px;border:none;color:red;background-color:inherit;">pool_max_idle_time</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;=&nbsp;</span><span class="attribute-value" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">10000</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;--毫秒&nbsp;&nbsp;&nbsp;&nbsp;</span></span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;local&nbsp;<span class="attribute" style="margin:0px;padding:0px;border:none;color:red;background-color:inherit;">pool_size</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;=&nbsp;</span><span class="attribute-value" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">100</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;--连接池大小&nbsp;&nbsp;&nbsp;&nbsp;</span></span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;local&nbsp;ok,&nbsp;<span class="attribute" style="margin:0px;padding:0px;border:none;color:red;background-color:inherit;">err</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;=&nbsp;</span><span class="attribute-value" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">red</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">:set_keepalive(pool_max_idle_time,&nbsp;pool_size)&nbsp;&nbsp;&nbsp;&nbsp;</span></span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;if&nbsp;not&nbsp;ok&nbsp;then&nbsp;&nbsp;&nbsp;&nbsp;</span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ngx.say("set&nbsp;keepalive&nbsp;error&nbsp;:&nbsp;",&nbsp;err)&nbsp;&nbsp;&nbsp;&nbsp;</span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;end&nbsp;&nbsp;&nbsp;&nbsp;</span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">end&nbsp;&nbsp;</span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;--&nbsp;&nbsp;</span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">local&nbsp;<span class="attribute" style="margin:0px;padding:0px;border:none;color:red;background-color:inherit;">redis</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;=&nbsp;</span><span class="attribute-value" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">require</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">("resty.redis")&nbsp;&nbsp;</span></span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">--创建实例&nbsp;&nbsp;</span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">local&nbsp;<span class="attribute" style="margin:0px;padding:0px;border:none;color:red;background-color:inherit;">red</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;=&nbsp;</span><span class="attribute-value" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">redis</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">:new()&nbsp;&nbsp;</span></span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">--设置超时（毫秒&nbsp;&nbsp;</span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">red:set_timeout(1000)&nbsp;&nbsp;</span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">--建立连接&nbsp;&nbsp;</span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">local&nbsp;<span class="attribute" style="margin:0px;padding:0px;border:none;color:red;background-color:inherit;">ip</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;=&nbsp;</span><span class="attribute-value" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">"192.168.0.43"</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;&nbsp;</span></span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">local&nbsp;<span class="attribute" style="margin:0px;padding:0px;border:none;color:red;background-color:inherit;">port</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;=&nbsp;</span><span class="attribute-value" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">6381</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;&nbsp;</span></span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">local&nbsp;ok,&nbsp;<span class="attribute" style="margin:0px;padding:0px;border:none;color:red;background-color:inherit;">err</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;=&nbsp;</span><span class="attribute-value" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">red</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">:connect(ip,&nbsp;port)&nbsp;&nbsp;</span></span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">--调用API获取数据&nbsp;&nbsp;</span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">local&nbsp;resp,&nbsp;<span class="attribute" style="margin:0px;padding:0px;border:none;color:red;background-color:inherit;">err</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;=&nbsp;</span><span class="attribute-value" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">red</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">:get("DB_SMS:openresty")&nbsp;&nbsp;</span></span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">if&nbsp;not&nbsp;resp&nbsp;then&nbsp;&nbsp;&nbsp;</span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;ngx.say("get&nbsp;msg&nbsp;error&nbsp;:&nbsp;",&nbsp;err)&nbsp;&nbsp;&nbsp;&nbsp;</span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;return&nbsp;close_redis(red)&nbsp;&nbsp;&nbsp;&nbsp;</span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">end&nbsp;&nbsp;</span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">ngx.say(resp)&nbsp;&nbsp;</span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">close_redis(red)&nbsp;&nbsp;</span>
			</li>
		</ol>
	</div>
<br />
这样，openresty就算入门了。
</div>
<div style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<br />
</div>
<div style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<h1 style="margin:0px;padding:0px;">
		<a name="t6"></a>使用
	</h1>
性能对比，直接通过nginx访问redis和直接访问应用服务器
</div>
<div style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<div>
		<img src="file://C:/Users/Administrator/Documents/Tencent%20Files/278703880/Image/Group/Image3/9F7UV8PXN)%60923%M]_AS@1H.png" alt="" style="border-width:initial;border-style:none;max-width:100%;" />
	</div>
<br />
</div>
<h2 style="margin:0px;padding:0px;font-family:Arial;white-space:normal;background-color:#FFFFFF;">
	<a name="t7"></a>通过nginx
</h2>
<div style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<img src="http://img.blog.csdn.net/20160909095746840?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center" alt="" style="border-width:initial;border-style:none;max-width:100%;" /><br />
</div>
<div style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<br />
</div>
<div style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<br />
</div>
<h2 style="margin:0px;padding:0px;font-family:Arial;white-space:normal;background-color:#FFFFFF;">
	<a name="t8"></a>直接访问应用服务器
</h2>
<div style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<img src="http://img.blog.csdn.net/20160909095752987?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center" alt="" style="border-width:initial;border-style:none;max-width:100%;" /><br />
</div>
<div style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<br />
</div>
<h1 style="margin:0px;padding:0px;font-family:Arial;white-space:normal;background-color:#FFFFFF;">
	<a name="t9"></a>其他配置案例
</h1>
<h2 style="margin:0px;padding:0px;font-family:Arial;white-space:normal;background-color:#FFFFFF;">
	<a name="t10"></a>mysql使用案例
</h2>
<div style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<div class="dp-highlighter bg_java" style="font-family:Consolas, &quot;font-size:12px;background-color:#E7E5DC;width:936.531px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;margin:18px 0px !important;">
		<div class="bar" style="padding-left:45px;">
			<div class="tools" style="padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;">
				<b>[java]</b>&nbsp;<a href="http://blog.csdn.net/yoara/article/details/52484268#" class="ViewSource" title="view plain" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span data-mod="popu_168">&nbsp;<a href="http://blog.csdn.net/yoara/article/details/52484268#" class="CopyToClipboard" title="copy" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a>
				<div style="position:absolute;left:721px;top:4601px;width:18px;height:18px;z-index:99;">
				</div>
</span><span data-mod="popu_169">&nbsp;</span><span class="tracking-ad" data-mod="popu_167"><a href="https://code.csdn.net/snippets/1873126" target="_blank" title="在CODE上查看代码片" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;"><img src="https://code.csdn.net/assets/CODE_ico.png" width="12" height="12" alt="在CODE上查看代码片" style="border-width:initial;border-style:none;max-width:100%;position:relative;top:1px;left:2px;" /></a></span><span class="tracking-ad" data-mod="popu_170"><a href="https://code.csdn.net/snippets/1873126/fork" target="_blank" title="派生到我的代码片" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;"><img src="https://code.csdn.net/assets/ico_fork.svg" width="12" height="12" alt="派生到我的代码片" style="border-width:initial;border-style:none;max-width:100%;position:relative;top:2px;left:2px;" /></a></span>
			</div>
		</div>
		<ol start="1" class="dp-j" style="padding:0px;border:none;list-style-position:initial;list-style-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span style="margin:0px;padding:0px;border:none;background-color:inherit;">local&nbsp;function&nbsp;close_mysql(db)&nbsp;&nbsp;</span></span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;<span class="keyword" style="margin:0px;padding:0px;border:none;color:#006699;background-color:inherit;font-weight:bold;">if</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;not&nbsp;db&nbsp;then&nbsp;&nbsp;</span></span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="keyword" style="margin:0px;padding:0px;border:none;color:#006699;background-color:inherit;font-weight:bold;">return</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;&nbsp;</span></span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;end&nbsp;&nbsp;</span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;</span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;--(连接池实现)&nbsp;&nbsp;</span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;local&nbsp;pool_max_idle_time&nbsp;=&nbsp;<span class="number" style="margin:0px;padding:0px;border:none;color:#C00000;background-color:inherit;">10000</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;--毫秒&nbsp;&nbsp;&nbsp;&nbsp;</span></span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;local&nbsp;pool_size&nbsp;=&nbsp;<span class="number" style="margin:0px;padding:0px;border:none;color:#C00000;background-color:inherit;">100</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;--连接池大小&nbsp;&nbsp;&nbsp;&nbsp;</span></span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;local&nbsp;ok,&nbsp;err&nbsp;=&nbsp;db:set_keepalive(pool_max_idle_time,&nbsp;pool_size)&nbsp;&nbsp;&nbsp;&nbsp;</span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;<span class="keyword" style="margin:0px;padding:0px;border:none;color:#006699;background-color:inherit;font-weight:bold;">if</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;not&nbsp;ok&nbsp;then&nbsp;&nbsp;&nbsp;&nbsp;</span></span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ngx.say(<span class="string" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">"set&nbsp;mysql&nbsp;keepalive&nbsp;error&nbsp;:&nbsp;"</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">,&nbsp;err)&nbsp;&nbsp;</span></span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="keyword" style="margin:0px;padding:0px;border:none;color:#006699;background-color:inherit;font-weight:bold;">return</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;&nbsp;</span></span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;end&nbsp;&nbsp;&nbsp;&nbsp;</span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">end&nbsp;&nbsp;</span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;</span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">local&nbsp;function&nbsp;getUrlResourceName(strurl)&nbsp;&nbsp;&nbsp;&nbsp;</span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;local&nbsp;ts&nbsp;=&nbsp;string.reverse(strurl)&nbsp;&nbsp;&nbsp;&nbsp;</span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;local&nbsp;param1,&nbsp;param2&nbsp;=&nbsp;string.find(ts,&nbsp;<span class="string" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">"/"</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">)&nbsp;&nbsp;--&nbsp;这里以</span><span class="string" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">"/"</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">为例&nbsp;&nbsp;&nbsp;&nbsp;</span></span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;local&nbsp;m&nbsp;=&nbsp;string.len(strurl)&nbsp;-&nbsp;param2&nbsp;+&nbsp;<span class="number" style="margin:0px;padding:0px;border:none;color:#C00000;background-color:inherit;">1</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span></span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;local&nbsp;result&nbsp;=&nbsp;string.sub(strurl,&nbsp;m+<span class="number" style="margin:0px;padding:0px;border:none;color:#C00000;background-color:inherit;">1</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">,&nbsp;string.len(strurl))&nbsp;&nbsp;</span></span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;<span class="keyword" style="margin:0px;padding:0px;border:none;color:#006699;background-color:inherit;font-weight:bold;">return</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;result&nbsp;&nbsp;&nbsp;&nbsp;</span></span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">end&nbsp;&nbsp;&nbsp;&nbsp;</span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;</span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">local&nbsp;mysql&nbsp;=&nbsp;require&nbsp;<span class="string" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">"resty.mysql"</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;&nbsp;</span></span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">local&nbsp;db,&nbsp;err&nbsp;=&nbsp;mysql:<span class="keyword" style="margin:0px;padding:0px;border:none;color:#006699;background-color:inherit;font-weight:bold;">new</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">()&nbsp;&nbsp;</span></span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span class="keyword" style="margin:0px;padding:0px;border:none;color:#006699;background-color:inherit;font-weight:bold;">if</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;not&nbsp;db&nbsp;then&nbsp;&nbsp;</span></span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;ngx.say(<span class="string" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">"failed&nbsp;to&nbsp;instantiate&nbsp;mysql:&nbsp;"</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">,&nbsp;err)&nbsp;&nbsp;</span></span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;<span class="keyword" style="margin:0px;padding:0px;border:none;color:#006699;background-color:inherit;font-weight:bold;">return</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;&nbsp;</span></span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">end&nbsp;&nbsp;</span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">db:set_timeout(<span class="number" style="margin:0px;padding:0px;border:none;color:#C00000;background-color:inherit;">1000</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">)&nbsp;&nbsp;</span></span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">local&nbsp;ok,&nbsp;err,&nbsp;errcode,&nbsp;sqlstate&nbsp;=&nbsp;db:connect{&nbsp;&nbsp;</span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;host&nbsp;=&nbsp;<span class="string" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">"192.168.0.109"</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">,&nbsp;&nbsp;</span></span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;port&nbsp;=&nbsp;<span class="number" style="margin:0px;padding:0px;border:none;color:#C00000;background-color:inherit;">3306</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">,&nbsp;&nbsp;</span></span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;database&nbsp;=&nbsp;<span class="string" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">"platform_qfang"</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">,&nbsp;&nbsp;</span></span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;user&nbsp;=&nbsp;<span class="string" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">"root"</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">,&nbsp;&nbsp;</span></span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;password&nbsp;=&nbsp;<span class="string" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">"123456"</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">,&nbsp;&nbsp;</span></span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;max_packet_size&nbsp;=&nbsp;<span class="number" style="margin:0px;padding:0px;border:none;color:#C00000;background-color:inherit;">1024</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;*&nbsp;</span><span class="number" style="margin:0px;padding:0px;border:none;color:#C00000;background-color:inherit;">1024</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;}&nbsp;&nbsp;</span></span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span class="keyword" style="margin:0px;padding:0px;border:none;color:#006699;background-color:inherit;font-weight:bold;">if</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;not&nbsp;ok&nbsp;then&nbsp;&nbsp;</span></span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;ngx.say(<span class="string" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">"failed&nbsp;to&nbsp;connect:&nbsp;"</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">,&nbsp;err,&nbsp;</span><span class="string" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">":&nbsp;"</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">,&nbsp;errcode,&nbsp;</span><span class="string" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">"&nbsp;"</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">,&nbsp;sqlstate)&nbsp;&nbsp;</span></span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;<span class="keyword" style="margin:0px;padding:0px;border:none;color:#006699;background-color:inherit;font-weight:bold;">return</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;&nbsp;</span></span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">end&nbsp;&nbsp;</span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">local&nbsp;uri=&nbsp;getUrlResourceName(ngx.var.uri)&nbsp;&nbsp;</span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">local&nbsp;res,&nbsp;err,&nbsp;errcode,&nbsp;sqlstate&nbsp;=&nbsp;&nbsp;</span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;db:query(<span class="string" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">"select&nbsp;FName&nbsp;from&nbsp;t_base_position&nbsp;where&nbsp;fid='"</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">..uri..</span><span class="string" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">"'"</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">,</span><span class="number" style="margin:0px;padding:0px;border:none;color:#C00000;background-color:inherit;">1</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">)&nbsp;&nbsp;</span></span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span class="keyword" style="margin:0px;padding:0px;border:none;color:#006699;background-color:inherit;font-weight:bold;">if</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;not&nbsp;res&nbsp;then&nbsp;&nbsp;</span></span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;ngx.say(<span class="string" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">"bad&nbsp;result:&nbsp;"</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">,&nbsp;err,&nbsp;</span><span class="string" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">":&nbsp;"</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">,&nbsp;errcode,&nbsp;</span><span class="string" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">":&nbsp;"</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">,&nbsp;sqlstate,&nbsp;</span><span class="string" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">"."</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">)&nbsp;&nbsp;</span></span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;<span class="keyword" style="margin:0px;padding:0px;border:none;color:#006699;background-color:inherit;font-weight:bold;">return</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;&nbsp;</span></span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">end&nbsp;&nbsp;</span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">--local&nbsp;cjson&nbsp;=&nbsp;require&nbsp;<span class="string" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">"cjson"</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;&nbsp;</span></span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">--ngx.say(<span class="string" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">"result,json:&nbsp;"</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">,&nbsp;cjson.encode(res))&nbsp;&nbsp;</span></span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">local&nbsp;size=table.getn(res)&nbsp;&nbsp;</span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span class="keyword" style="margin:0px;padding:0px;border:none;color:#006699;background-color:inherit;font-weight:bold;">if</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;size&gt;</span><span class="number" style="margin:0px;padding:0px;border:none;color:#C00000;background-color:inherit;">0</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;then&nbsp;&nbsp;</span></span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;ngx.say(<span class="string" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">"result:"</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">,res[</span><span class="number" style="margin:0px;padding:0px;border:none;color:#C00000;background-color:inherit;">1</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">].FName)&nbsp;&nbsp;</span></span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span class="keyword" style="margin:0px;padding:0px;border:none;color:#006699;background-color:inherit;font-weight:bold;">else</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;&nbsp;</span></span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;ngx.say(<span class="string" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">"no&nbsp;result"</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">)&nbsp;&nbsp;</span></span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">end&nbsp;&nbsp;</span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">close_mysql(db)&nbsp;&nbsp;</span>
			</li>
			<li>
			</li>
		</ol>
	</div>
</div>