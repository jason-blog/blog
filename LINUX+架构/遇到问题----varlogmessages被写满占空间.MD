<p>
	http://blog.csdn.net/zzq900503/article/details/79345929
</p>
<p>
	<br />
</p>
<p>
	<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;font-size:16px;color:#4F4F4F;line-height:26px;text-align:justify;word-break:normal;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		我们之前遇到过一个问题，日志文件把服务器空间占完了导致web服务不正常。&nbsp;<br style="box-sizing:border-box;" />
<a href="http://blog.csdn.net/zzq900503/article/details/79328595" target="_blank" style="text-decoration-line:none;box-sizing:border-box;color:#0C89CF;">遇到问题——tomcat重新启动Insufficient space for shared memory file</a>
	</p>
	<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;font-size:16px;color:#4F4F4F;line-height:26px;text-align:justify;word-break:normal;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		解决方式是把日志文件删除后恢复正常。
	</p>
	<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;font-size:16px;color:#4F4F4F;line-height:26px;text-align:justify;word-break:normal;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		但是过一段时间发现又满了。
	</p>
	<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;font-size:16px;color:#4F4F4F;line-height:26px;text-align:justify;word-break:normal;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		要彻底解决这个问题还得从日志文件的配置入手。
	</p>
	<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;font-size:16px;color:#4F4F4F;line-height:26px;text-align:justify;word-break:normal;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		/var/log/messages – 包含整个系统的信息，包括系统启动期间被记录的日志。mail, cron, daemon, kern, auth等相关的日志信息在这里记录。
	</p>
	<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;font-size:16px;color:#4F4F4F;line-height:26px;text-align:justify;word-break:normal;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		使用命令
	</p>
<pre class="prettyprint" name="code" style="white-space:nowrap;word-wrap:break-word;box-sizing:border-box;position:relative;overflow-y:hidden;overflow-x:auto;margin-top:0px;margin-bottom:24px;font-family:Consolas, Inconsolata, Courier, monospace;padding:8px 16px 4px 56px;font-size:14px;line-height:22px;word-break:break-all;background-color:#F6F8FA;border:none;border-radius:0px;"><code class="hljs lasso has-numbering" style="display:block;padding:0px;background-image:initial;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;box-sizing:border-box;font-family:Consolas, Inconsolata, Courier, monospace;white-space:pre;border-radius:4px;line-height:22px;overflow-x:auto;word-wrap:normal;">less /<span class="hljs-built_in" style="color:#4F4F4F;box-sizing:border-box;">var</span>/<span class="hljs-keyword" style="color:#000088;box-sizing:border-box;">log</span>/messages</code>
	<ul class="pre-numbering" style="box-sizing:border-box;margin:0px;padding:8px 0px;position:absolute;width:48px;background-color:#EEF0F4;top:0px;left:0px;border-right:1px solid #DDDDDD;list-style:none;text-align:right;">
		
		<li style="box-sizing:border-box;list-style:none;margin:0px;padding:0px 5px;">
			1
		</li>

	</ul>
</pre>
	<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;font-size:16px;color:#4F4F4F;line-height:26px;text-align:justify;word-break:normal;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		Feb 18 04:16:59 instance-1 kernel: Cannot read proc file system: 9 - Bad file descriptor.&nbsp;<br style="box-sizing:border-box;" />
Feb 18 04:16:59 instance-1 kernel: Cannot read proc file system: 9 - Bad file descriptor.&nbsp;<br style="box-sizing:border-box;" />
Feb 18 04:16:59 instance-1 kernel: Cannot read proc file system: 9 - Bad file descriptor.&nbsp;<br style="box-sizing:border-box;" />
Feb 18 04:16:59 instance-1 kernel: Cannot read proc file system: 9 - Bad file descriptor.&nbsp;<br style="box-sizing:border-box;" />
Feb 18 04:16:59 instance-1 kernel: Cannot read proc file system: 9 - Bad file descriptor.&nbsp;<br style="box-sizing:border-box;" />
Feb 18 04:16:59 instance-1 kernel: Cannot read proc file system: 9 - Bad file descriptor.&nbsp;<br style="box-sizing:border-box;" />
Feb 18 04:16:59 instance-1 kernel: Cannot read proc file system: 9 - Bad file descriptor.&nbsp;<br style="box-sizing:border-box;" />
Feb 18 04:16:59 instance-1 kernel: Cannot read proc file system: 9 - Bad file descriptor.&nbsp;<br style="box-sizing:border-box;" />
Feb 18 04:16:59 instance-1 kernel: Cannot read proc file system: 9 - Bad file descriptor.&nbsp;<br style="box-sizing:border-box;" />
Feb 18 04:16:59 instance-1 kernel: Cannot read proc file system: 9 - Bad file descriptor.&nbsp;<br style="box-sizing:border-box;" />
Feb 18 04:16:59 instance-1 kernel: Cannot read proc file system: 9 - Bad file descriptor.&nbsp;<br style="box-sizing:border-box;" />
Feb 18 04:16:59 instance-1 kernel: Cannot read proc file system: 9 - Bad file descriptor.&nbsp;<br style="box-sizing:border-box;" />
Feb 18 04:16:59 instance-1 kernel: Cannot read proc file system: 9 - Bad file descriptor.&nbsp;<br style="box-sizing:border-box;" />
Feb 18 04:16:59 instance-1 kernel: Cannot read proc file system: 9 - Bad file descriptor.&nbsp;<br style="box-sizing:border-box;" />
Feb 18 04:16:59 instance-1 kernel: Cannot read proc file system: 9 - Bad file descriptor.
	</p>
	<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;font-size:16px;color:#4F4F4F;line-height:26px;text-align:justify;word-break:normal;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		可以看到频繁报错的原因。
	</p>
	<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;font-size:16px;color:#4F4F4F;line-height:26px;text-align:justify;word-break:normal;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		如果有严重的问题，就需要相应的去解决。
	</p>
	<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;font-size:16px;color:#4F4F4F;line-height:26px;text-align:justify;word-break:normal;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		如果没有的话，则可以屏蔽到相关信息。&nbsp;<br style="box-sizing:border-box;" />
比如Cannot read proc file system是因为权限问题导致的，但是一直重复记录。
	</p>
	<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;font-size:16px;color:#4F4F4F;line-height:26px;text-align:justify;word-break:normal;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		/etc/rsyslog.conf文件决定了哪些内容会被写入到对应的日志文件中，例如，这是/var/log/messages再rsyslog.conf中的相关内容：&nbsp;<br style="box-sizing:border-box;" />
使用命令
	</p>
<pre class="prettyprint" name="code" style="white-space:nowrap;word-wrap:break-word;box-sizing:border-box;position:relative;overflow-y:hidden;overflow-x:auto;margin-top:0px;margin-bottom:24px;font-family:Consolas, Inconsolata, Courier, monospace;padding:8px 16px 4px 56px;font-size:14px;line-height:22px;word-break:break-all;background-color:#F6F8FA;border:none;border-radius:0px;"><code class="hljs perl has-numbering" style="display:block;padding:0px;background-image:initial;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;box-sizing:border-box;font-family:Consolas, Inconsolata, Courier, monospace;white-space:pre;border-radius:4px;line-height:22px;overflow-x:auto;word-wrap:normal;"> <span class="hljs-keyword" style="color:#000088;box-sizing:border-box;">grep</span> <span class="hljs-string" style="color:#009900;box-sizing:border-box;">"/var/log/messages"</span> /etc/rsyslog.conf</code>
	<ul class="pre-numbering" style="box-sizing:border-box;margin:0px;padding:8px 0px;position:absolute;width:48px;background-color:#EEF0F4;top:0px;left:0px;border-right:1px solid #DDDDDD;list-style:none;text-align:right;">
		
		<li style="box-sizing:border-box;list-style:none;margin:0px;padding:0px 5px;">
			1
		</li>

	</ul>
</pre>
	<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;font-size:16px;color:#4F4F4F;line-height:26px;text-align:justify;word-break:normal;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		输出如下:&nbsp;<br style="box-sizing:border-box;" />
$ grep “/var/log/messages” /etc/rsyslog.conf&nbsp;<br style="box-sizing:border-box;" />
*.info;mail.none;authpriv.none;cron.none /var/log/messages
	</p>
	<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;font-size:16px;color:#4F4F4F;line-height:26px;text-align:justify;word-break:normal;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		上述的输出中：
	</p>
	<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;font-size:16px;color:#4F4F4F;line-height:26px;text-align:justify;word-break:normal;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		*.info 表明所有带有 INFO 标志的日志信息会被记录。&nbsp;<br style="box-sizing:border-box;" />
mail.none,authpriv.none,cron.none 表明这三种错误信息不会在messages。&nbsp;<br style="box-sizing:border-box;" />
你也可以指定 *.none，这样将没有任何日志信息被记录
	</p>
	<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;font-size:16px;color:#4F4F4F;line-height:26px;text-align:justify;word-break:normal;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		我们这里就设置为*.none即可。&nbsp;<br style="box-sizing:border-box;" />
使用命令
	</p>
<pre class="prettyprint" name="code" style="white-space:nowrap;word-wrap:break-word;box-sizing:border-box;position:relative;overflow-y:hidden;overflow-x:auto;margin-top:0px;margin-bottom:24px;font-family:Consolas, Inconsolata, Courier, monospace;padding:8px 16px 4px 56px;font-size:14px;line-height:22px;word-break:break-all;background-color:#F6F8FA;border:none;border-radius:0px;"><code class="hljs avrasm has-numbering" style="display:block;padding:0px;background-image:initial;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;box-sizing:border-box;font-family:Consolas, Inconsolata, Courier, monospace;white-space:pre;border-radius:4px;line-height:22px;overflow-x:auto;word-wrap:normal;">vim /etc/rsyslog<span class="hljs-preprocessor" style="color:#009900;box-sizing:border-box;">.conf</span></code>
	<ul class="pre-numbering" style="box-sizing:border-box;margin:0px;padding:8px 0px;position:absolute;width:48px;background-color:#EEF0F4;top:0px;left:0px;border-right:1px solid #DDDDDD;list-style:none;text-align:right;">
		
		<li style="box-sizing:border-box;list-style:none;margin:0px;padding:0px 5px;">
			1
		</li>

	</ul>
</pre>
	<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;font-size:16px;color:#4F4F4F;line-height:26px;text-align:justify;word-break:normal;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		/ /var/log/messages 快速查找到/var/log/messages的配置&nbsp;<br style="box-sizing:border-box;" />
修改为*.none&nbsp;<br style="box-sizing:border-box;" />
esc输入:wq保存退出即可。
	</p>
</p>