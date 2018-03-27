<p>
	http://blog.csdn.net/u010397369/article/details/41045251
</p>
<p>
	<br />
</p>
<p>
	<h1 style="margin:0px;padding:0px;color:#362E2B;font-family:Arial;white-space:normal;background-color:#FFFFFF;">
		概述
	</h1>
	<p style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
		在使用<a href="http://lib.csdn.net/base/docker" class="replace_word" title="Docker知识库" target="_blank" style="color:#DF3434;text-decoration-line:none;font-weight:bold;">Docker</a>创建了容器之后，大家比较关心的就是如何进入该容器了，其实进入<a href="http://lib.csdn.net/base/docker" class="replace_word" title="Docker知识库" target="_blank" style="color:#DF3434;text-decoration-line:none;font-weight:bold;">docker</a>容器有好几多种方式，这里我们就讲一下常用的几种进入Docker容器的方法。
	</p>
	<p style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
		进入Docker容器比较常见的几种做法如下：
	</p>
	<ul style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
		<li>
			使用docker attach
		</li>
		<li>
			使用SSH
		</li>
		<li>
			使用nsenter
		</li>
		<li>
			使用exec<br />
		</li>
	</ul>
	<p style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
		下面我们来逐一讲一下每种方式。
	</p>
	<h1 style="margin:0px;padding:0px;color:#362E2B;font-family:Arial;white-space:normal;background-color:#FFFFFF;">
		<a name="t1"></a>一、使用docker attach进入Docker容器
	</h1>
	<p style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
		Docker提供了attach命令来进入Docker容器。
	</p>
	<p style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
		<img src="http://img.blog.csdn.net/20141112160853687" alt="" style="border-width:initial;border-style:none;max-width:100%;" />
	</p>
	<p style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
		接下来我们创建一个守护态的Docker容器，然后使用docker attach命令进入该容器。
	</p>
	<div class="dp-highlighter bg_plain" style="font-family:Consolas, &quot;background-color:#E7E5DC;width:712.797px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;color:#362E2B;white-space:normal;margin:18px 0px !important;">
		<div class="bar" style="padding-left:45px;">
			<div class="tools" style="padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;">
				<b>[plain]</b>&nbsp;<a href="http://blog.csdn.net/u010397369/article/details/41045251#" class="ViewSource" title="view plain" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span data-mod="popu_168">&nbsp;<a href="http://blog.csdn.net/u010397369/article/details/41045251#" class="CopyToClipboard" title="copy" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a>
				<div style="position:absolute;left:846px;top:1089px;width:18px;height:18px;z-index:99;">
				</div>
</span><span data-mod="popu_169"></span>
			</div>
		</div>
		<ol start="1" style="padding:0px;border:none;list-style-position:initial;list-style-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span style="margin:0px;padding:0px;border:none;background-color:inherit;">$&nbsp;sudo&nbsp;docker&nbsp;run&nbsp;-itd&nbsp;ubuntu:14.04&nbsp;/bin/bash&nbsp;&nbsp;</span></span>
			</li>
		</ol>
	</div>
<img src="http://img.blog.csdn.net/20141112161118609" alt="" style="border-width:initial;border-style:none;max-width:100%;color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" /><span style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;"></span>
	<p style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
		然后我们使用docker ps查看到该容器信息，接下来就使用docker attach进入该容器
	</p>
	<div class="dp-highlighter bg_plain" style="font-family:Consolas, &quot;background-color:#E7E5DC;width:712.797px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;color:#362E2B;white-space:normal;margin:18px 0px !important;">
		<div class="bar" style="padding-left:45px;">
			<div class="tools" style="padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;">
				<b>[plain]</b>&nbsp;<a href="http://blog.csdn.net/u010397369/article/details/41045251#" class="ViewSource" title="view plain" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span data-mod="popu_168">&nbsp;<a href="http://blog.csdn.net/u010397369/article/details/41045251#" class="CopyToClipboard" title="copy" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a>
				<div style="position:absolute;left:846px;top:1288px;width:18px;height:18px;z-index:99;">
				</div>
</span><span data-mod="popu_169"></span>
			</div>
		</div>
		<ol start="1" style="padding:0px;border:none;list-style-position:initial;list-style-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span style="margin:0px;padding:0px;border:none;background-color:inherit;">$&nbsp;sudo&nbsp;docker&nbsp;attach&nbsp;44fc0f0582d9&nbsp;&nbsp;</span></span>
			</li>
		</ol>
	</div>
<img src="http://img.blog.csdn.net/20141112161322515" alt="" style="border-width:initial;border-style:none;max-width:100%;color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" /><br style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">可以看到我们已经进入到该容器中了。</span>
	<p style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
		但在，使用该命令有一个问题。当多个窗口同时使用该命令进入该容器时，所有的窗口都会同步显示。如果有一个窗口阻塞了，那么其他窗口也无法再进行操作。下来我们来演示一下。打开两个窗口，都使用attach命令进入同一个容器里面。如下所示：
	</p>
	<p style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
		<img src="http://img.blog.csdn.net/20141112161800343" alt="" style="border-width:initial;border-style:none;max-width:100%;" />
	</p>
	<p style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
		接下来我们只在第一个窗口进行操作，可以看到第一个窗口的操作同步到第二个窗口显示了，如下：
	</p>
	<p style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
		<img src="http://img.blog.csdn.net/20141112161943118" alt="" style="border-width:initial;border-style:none;max-width:100%;" />
	</p>
	<p style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
		因为这个原因，所以docker attach命令不太适合于生产环境，平时自己开发应用时可以使用该命令。
	</p>
	<h1 style="margin:0px;padding:0px;color:#362E2B;font-family:Arial;white-space:normal;background-color:#FFFFFF;">
		<a name="t2"></a>二、使用SSH进入Docker容器
	</h1>
	<p style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
		在生产环境中排除了使用docker attach命令进入容器之后，相信大家第一个想到的就是ssh。在镜像（或容器）中安装SSH Server，这样就能保证多人进入容器且相互之间不受干扰了，相信大家在当前的生产环境中（没有使用Docker的情况）也是这样做的。但是使用了Docker容器之后不建议使用ssh进入到Docker容器内。关于为什么不建议使用，请参考如下几篇文章：
	</p>
	<p style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
		<a target="_blank" href="http://blog.docker.com/tag/nsenter/" style="color:#6A3906;text-decoration-line:none;">Why you don't need to run SSHd in your Docker containers</a>
	</p>
	<p style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
		上面这篇文章是英文的，如果英语不好的话可以参考如下译文
	</p>
	<p style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
		<a target="_blank" href="http://www.oschina.net/translate/why-you-dont-need-to-run-sshd-in-docker?cmp" style="color:#6A3906;text-decoration-line:none;">为什么不需要在 Docker 容器中运行 sshd</a>
	</p>
	<h1 style="margin:0px;padding:0px;color:#362E2B;font-family:Arial;white-space:normal;background-color:#FFFFFF;">
		<a name="t3"></a>三、使用nsenter进入Docker容器
	</h1>
	<p style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
		在上面两种方式都不适合的情况下，还有一种比较方便的方法，即使用nsenter进入Docker容器。关于什么是nsenter请参考如下文章：
	</p>
	<p style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
		<a target="_blank" href="https://github.com/jpetazzo/nsenter" style="color:#6A3906;text-decoration-line:none;">https://github.com/jpetazzo/nsenter</a>
	</p>
	<p style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
		在了解了什么是nsenter之后，我们需要把nsenter安装到主机中（注意是主机而非容器或镜像），具体的安装命令如下：
	</p>
	<div class="dp-highlighter bg_plain" style="font-family:Consolas, &quot;background-color:#E7E5DC;width:712.797px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;color:#362E2B;white-space:normal;margin:18px 0px !important;">
		<div class="bar" style="padding-left:45px;">
			<div class="tools" style="padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;">
				<b>[plain]</b>&nbsp;<a href="http://blog.csdn.net/u010397369/article/details/41045251#" class="ViewSource" title="view plain" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span data-mod="popu_168">&nbsp;<a href="http://blog.csdn.net/u010397369/article/details/41045251#" class="CopyToClipboard" title="copy" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a>
				<div style="position:absolute;left:846px;top:2502px;width:18px;height:18px;z-index:99;">
				</div>
</span><span data-mod="popu_169"></span>
			</div>
		</div>
		<ol start="1" style="padding:0px;border:none;list-style-position:initial;list-style-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span style="margin:0px;padding:0px;border:none;background-color:inherit;">$&nbsp;wget&nbsp;https://www.kernel.org/pub/linux/utils/util-linux/v2.24/util-linux-2.24.tar.gz&nbsp;&nbsp;</span></span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">$&nbsp;tar&nbsp;-xzvf&nbsp;util-linux-2.24.tar.gz&nbsp;&nbsp;</span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">$&nbsp;cd&nbsp;util-linux-2.24/&nbsp;&nbsp;</span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">$&nbsp;./configure&nbsp;--without-ncurses&nbsp;&nbsp;</span>
			</li>
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">$&nbsp;make&nbsp;nsenter&nbsp;&nbsp;</span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">$&nbsp;sudo&nbsp;cp&nbsp;nsenter&nbsp;/usr/local/bin&nbsp;&nbsp;</span>
			</li>
		</ol>
	</div>
<span style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">安装好nsenter之后可以查看一下该命令的使用。</span>
	<p style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
		<img src="http://img.blog.csdn.net/20141112163549540" alt="" style="border-width:initial;border-style:none;max-width:100%;" />
	</p>
	<p style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
		nsenter可以访问另一个进程的名称空间。所以为了连接到某个容器我们还需要获取该容器的第一个进程的PID。可以使用docker inspect命令来拿到该PID。
	</p>
	<p style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
		docker inspect命令使用如下：
	</p>
	<div class="dp-highlighter bg_plain" style="font-family:Consolas, &quot;background-color:#E7E5DC;width:712.797px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;color:#362E2B;white-space:normal;margin:18px 0px !important;">
		<div class="bar" style="padding-left:45px;">
			<div class="tools" style="padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;">
				<b>[plain]</b>&nbsp;<a href="http://blog.csdn.net/u010397369/article/details/41045251#" class="ViewSource" title="view plain" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span data-mod="popu_168">&nbsp;<a href="http://blog.csdn.net/u010397369/article/details/41045251#" class="CopyToClipboard" title="copy" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a>
				<div style="position:absolute;left:846px;top:3207px;width:18px;height:18px;z-index:99;">
				</div>
</span><span data-mod="popu_169"></span>
			</div>
		</div>
		<ol start="1" style="padding:0px;border:none;list-style-position:initial;list-style-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span style="margin:0px;padding:0px;border:none;background-color:inherit;">$&nbsp;sudo&nbsp;docker&nbsp;inspect&nbsp;--help&nbsp;&nbsp;</span></span>
			</li>
		</ol>
	</div>
<img src="http://img.blog.csdn.net/20141112164451454" alt="" style="border-width:initial;border-style:none;max-width:100%;color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" /><span style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;"></span>
	<p style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
		inspect命令可以分层级显示一个镜像或容器的信息。比如我们当前有一个正在运行的容器
	</p>
	<p style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
		<img src="http://img.blog.csdn.net/20141112164701308" alt="" style="border-width:initial;border-style:none;max-width:100%;" />
	</p>
	<p style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
		可以使用docker inspect来查看该容器的详细信息。
	</p>
	<div class="dp-highlighter bg_plain" style="font-family:Consolas, &quot;background-color:#E7E5DC;width:712.797px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;color:#362E2B;white-space:normal;margin:18px 0px !important;">
		<div class="bar" style="padding-left:45px;">
			<div class="tools" style="padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;">
				<b>[plain]</b>&nbsp;<a href="http://blog.csdn.net/u010397369/article/details/41045251#" class="ViewSource" title="view plain" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span data-mod="popu_168">&nbsp;<a href="http://blog.csdn.net/u010397369/article/details/41045251#" class="CopyToClipboard" title="copy" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a>
				<div style="position:absolute;left:846px;top:3603px;width:18px;height:18px;z-index:99;">
				</div>
</span><span data-mod="popu_169"></span>
			</div>
		</div>
		<ol start="1" style="padding:0px;border:none;list-style-position:initial;list-style-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span style="margin:0px;padding:0px;border:none;background-color:inherit;">$&nbsp;sudo&nbsp;docker&nbsp;inspect&nbsp;44fc0f0582d9&nbsp;&nbsp;</span></span>
			</li>
		</ol>
	</div>
<img src="http://img.blog.csdn.net/20141112164820057" alt="" style="border-width:initial;border-style:none;max-width:100%;color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" /><br style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">由其该信息非常多，此处只截取了其中一部分进行展示。如果要显示该容器第一个进行的PID可以使用如下方式</span>
	<div class="dp-highlighter bg_plain" style="font-family:Consolas, &quot;background-color:#E7E5DC;width:712.797px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;color:#362E2B;white-space:normal;margin:18px 0px !important;">
		<div class="bar" style="padding-left:45px;">
			<div class="tools" style="padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;">
				<b>[plain]</b>&nbsp;<a href="http://blog.csdn.net/u010397369/article/details/41045251#" class="ViewSource" title="view plain" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span data-mod="popu_168">&nbsp;<a href="http://blog.csdn.net/u010397369/article/details/41045251#" class="CopyToClipboard" title="copy" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a>
				<div style="position:absolute;left:846px;top:4067px;width:18px;height:18px;z-index:99;">
				</div>
</span><span data-mod="popu_169"></span>
			</div>
		</div>
		<ol start="1" style="padding:0px;border:none;list-style-position:initial;list-style-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span style="margin:0px;padding:0px;border:none;background-color:inherit;">$&nbsp;sudo&nbsp;docker&nbsp;inspect&nbsp;-f&nbsp;{{.State.Pid}}&nbsp;44fc0f0582d9&nbsp;&nbsp;</span></span>
			</li>
		</ol>
	</div>
<img src="http://img.blog.csdn.net/20141112165049131" alt="" style="border-width:initial;border-style:none;max-width:100%;color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" /><span style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;"></span>
	<p style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
		在拿到该进程PID之后我们就可以使用nsenter命令访问该容器了。
	</p>
	<div class="dp-highlighter bg_plain" style="font-family:Consolas, &quot;background-color:#E7E5DC;width:712.797px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;color:#362E2B;white-space:normal;margin:18px 0px !important;">
		<div class="bar" style="padding-left:45px;">
			<div class="tools" style="padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;">
				<b>[plain]</b>&nbsp;<a href="http://blog.csdn.net/u010397369/article/details/41045251#" class="ViewSource" title="view plain" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span data-mod="popu_168">&nbsp;<a href="http://blog.csdn.net/u010397369/article/details/41045251#" class="CopyToClipboard" title="copy" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a>
				<div style="position:absolute;left:846px;top:4273px;width:18px;height:18px;z-index:99;">
				</div>
</span><span data-mod="popu_169"></span>
			</div>
		</div>
		<ol start="1" style="padding:0px;border:none;list-style-position:initial;list-style-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span style="margin:0px;padding:0px;border:none;background-color:inherit;">$&nbsp;sudo&nbsp;nsenter&nbsp;--target&nbsp;3326&nbsp;--mount&nbsp;--uts&nbsp;--ipc&nbsp;--net&nbsp;--pid&nbsp;&nbsp;</span></span>
			</li>
		</ol>
	</div>
<span style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">其中的3326即刚才拿到的进程的PID</span>
	<p style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
		<img src="http://img.blog.csdn.net/20141112165415520" alt="" style="border-width:initial;border-style:none;max-width:100%;" />
	</p>
	<p style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
		当然，如果你认为每次都输入那么多参数太麻烦的话，网上也有许多做好的脚本供大家使用。
	</p>
	<p style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
		地址如下：
	</p>
	<p style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
		<a target="_blank" href="http://yeasy.gitbooks.io/docker_practice/content/container/enter.html" style="color:#6A3906;text-decoration-line:none;">http://yeasy.gitbooks.io/docker_practice/content/container/enter.html</a>
	</p>
	<p style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
		<a target="_blank" href="http://www.tuicool.com/articles/eYnUBrR" style="color:#6A3906;text-decoration-line:none;">http://www.tuicool.com/articles/eYnUBrR</a>
	</p>
	<p style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
		<br />
	</p>
	<h1 style="margin:0px;padding:0px;color:#362E2B;font-family:Arial;white-space:normal;background-color:#FFFFFF;">
		<a name="t4"></a>四、使用docker exec进入Docker容器
	</h1>
<span style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">除了上面几种做法之外，docker在1.3.X版本之后还提供了一个新的命令exec用于进入容器，这种方式相对更简单一些，下面我们来看一下该命令的使用：</span>
	<div class="dp-highlighter bg_plain" style="font-family:Consolas, &quot;background-color:#E7E5DC;width:712.797px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;color:#362E2B;white-space:normal;margin:18px 0px !important;">
		<div class="bar" style="padding-left:45px;">
			<div class="tools" style="padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;">
				<b>[plain]</b>&nbsp;<a href="http://blog.csdn.net/u010397369/article/details/41045251#" class="ViewSource" title="view plain" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span data-mod="popu_168">&nbsp;<a href="http://blog.csdn.net/u010397369/article/details/41045251#" class="CopyToClipboard" title="copy" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a>
				<div style="position:absolute;left:846px;top:4774px;width:18px;height:18px;z-index:99;">
				</div>
</span><span data-mod="popu_169"></span>
			</div>
		</div>
		<ol start="1" style="padding:0px;border:none;list-style-position:initial;list-style-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span style="margin:0px;padding:0px;border:none;background-color:inherit;">$&nbsp;sudo&nbsp;docker&nbsp;exec&nbsp;--help&nbsp;&nbsp;</span></span>
			</li>
		</ol>
	</div>
<img src="http://img.blog.csdn.net/20150105125735137" alt="" style="border-width:initial;border-style:none;max-width:100%;color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" /><span style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;"></span>
	<p style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
		接下来我们使用该命令进入一个已经在运行的容器
	</p>
	<div class="dp-highlighter bg_plain" style="font-family:Consolas, &quot;background-color:#E7E5DC;width:712.797px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;color:#362E2B;white-space:normal;margin:18px 0px !important;">
		<div class="bar" style="padding-left:45px;">
			<div class="tools" style="padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;">
				<b>[plain]</b>&nbsp;<a href="http://blog.csdn.net/u010397369/article/details/41045251#" class="ViewSource" title="view plain" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span data-mod="popu_168">&nbsp;<a href="http://blog.csdn.net/u010397369/article/details/41045251#" class="CopyToClipboard" title="copy" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a>
				<div style="position:absolute;left:846px;top:5079px;width:18px;height:18px;z-index:99;">
				</div>
</span><span data-mod="popu_169"></span>
			</div>
		</div>
		<ol start="1" style="padding:0px;border:none;list-style-position:initial;list-style-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
			<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span style="margin:0px;padding:0px;border:none;background-color:inherit;">$&nbsp;sudo&nbsp;docker&nbsp;ps&nbsp;&nbsp;</span></span>
			</li>
			<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
				<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">$&nbsp;sudo&nbsp;docker&nbsp;exec&nbsp;-it&nbsp;775c7c9ee1e1&nbsp;/bin/bash&nbsp;&nbsp;</span>
			</li>
		</ol>
	</div>
<img src="http://img.blog.csdn.net/20150105130038079" alt="" style="border-width:initial;border-style:none;max-width:100%;color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" /><br style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
	<p style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
		网上还有一种做法是使用nsinit，没有亲身实践过所以不在此罗列了，有兴趣的话可以尝试一下。
	</p>
</p>