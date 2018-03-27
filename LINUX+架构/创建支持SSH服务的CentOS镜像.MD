<p>
	http://blog.csdn.net/cmzsteven/article/details/49081913
</p>
<p>
	<br />
</p>
<p>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:1.7em;padding:0px;line-height:27.2px;word-break:normal;color:#3F3F3F;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		现在很多关于docker的资料都是以ubuntu为基础进行讲解的。从宿主机到docker镜像，执行的命令也都是基于ubuntu的。&nbsp;<br style="box-sizing:border-box;" />
本文旨在以centos为宿主的环境下，在centos的docker镜像中安装sshd服务，使生成的容器可以从远程通过ssh进行登录。&nbsp;<br style="box-sizing:border-box;" />
本文的宿主选择的是centos6.7, docker镜像是centos7.0&nbsp;<br style="box-sizing:border-box;" />
1 、在宿主centos上安装docker
	</p>
<pre class="prettyprint" style="box-sizing:border-box;font-family:&quot;font-size:14px;white-space:nowrap;padding:5px 5px 5px 60px;margin-top:0px;margin-bottom:1.7em;line-height:23.8px;color:#333333;word-break:break-all;word-wrap:break-word;background-color:rgba(128, 128, 128, 0.05);border:1px solid rgba(128, 128, 128, 0.075);border-radius:0px;position:relative;overflow-y:hidden;overflow-x:auto;"><code class="hljs lasso has-numbering" style="box-sizing:border-box;font-family:&quot;font-size:12.6px;padding:0px;color:inherit;white-space:pre;background:transparent;border-radius:0px;display:block;word-wrap:normal;">yum install <span class="hljs-attribute" style="box-sizing:border-box;margin:0px;padding:0px;">-y</span> epel<span class="hljs-attribute" style="box-sizing:border-box;margin:0px;padding:0px;">-release</span> yum install <span class="hljs-attribute" style="box-sizing:border-box;margin:0px;padding:0px;">-y</span> docker<span class="hljs-attribute" style="box-sizing:border-box;margin:0px;padding:0px;">-io</span></code>
	<ul class="pre-numbering" style="box-sizing:border-box;margin:0px;padding:6px 0px 40px;list-style:none;line-height:23.8px;position:absolute;width:50px;background-color:#EEEEEE;top:0px;left:0px;border-right:1px solid #DDDDDD;text-align:right;">
		
		<li style="box-sizing:border-box;margin:0px;padding:0px 5px;list-style:none;color:#999999;">
			1
		</li>

		<li style="box-sizing:border-box;margin:0px;padding:0px 5px;list-style:none;color:#999999;">
			2
		</li>

	</ul>
</pre>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:1.7em;padding:0px;line-height:27.2px;word-break:normal;color:#3F3F3F;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		2、启动docker服务
	</p>
<pre class="prettyprint" style="box-sizing:border-box;font-family:&quot;font-size:14px;white-space:nowrap;padding:5px 5px 5px 60px;margin-top:0px;margin-bottom:1.7em;line-height:23.8px;color:#333333;word-break:break-all;word-wrap:break-word;background-color:rgba(128, 128, 128, 0.05);border:1px solid rgba(128, 128, 128, 0.075);border-radius:0px;position:relative;overflow-y:hidden;overflow-x:auto;"><code class="hljs sql has-numbering" style="box-sizing:border-box;font-family:&quot;font-size:12.6px;padding:0px;color:inherit;white-space:pre;background:transparent;border-radius:0px;display:block;word-wrap:normal;">service docker <span class="hljs-operator" style="box-sizing:border-box;margin:0px;padding:0px;"><span class="hljs-keyword" style="box-sizing:border-box;margin:0px;padding:0px;color:#000088;">start</span></span></code>
	<ul class="pre-numbering" style="box-sizing:border-box;margin:0px;padding:6px 0px 40px;list-style:none;line-height:23.8px;position:absolute;width:50px;background-color:#EEEEEE;top:0px;left:0px;border-right:1px solid #DDDDDD;text-align:right;">
		
		<li style="box-sizing:border-box;margin:0px;padding:0px 5px;list-style:none;color:#999999;">
			1
		</li>

	</ul>
</pre>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:1.7em;padding:0px;line-height:27.2px;word-break:normal;color:#3F3F3F;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		3、下载centos 的 docker 镜像
	</p>
<pre class="prettyprint" style="box-sizing:border-box;font-family:&quot;font-size:14px;white-space:nowrap;padding:5px 5px 5px 60px;margin-top:0px;margin-bottom:1.7em;line-height:23.8px;color:#333333;word-break:break-all;word-wrap:break-word;background-color:rgba(128, 128, 128, 0.05);border:1px solid rgba(128, 128, 128, 0.075);border-radius:0px;position:relative;overflow-y:hidden;overflow-x:auto;"><code class="hljs has-numbering" style="box-sizing:border-box;font-family:&quot;font-size:12.6px;padding:0px;color:inherit;white-space:pre;background:transparent;border-radius:0px;display:block;word-wrap:normal;">docker pull centos</code>
	<ul class="pre-numbering" style="box-sizing:border-box;margin:0px;padding:6px 0px 40px;list-style:none;line-height:23.8px;position:absolute;width:50px;background-color:#EEEEEE;top:0px;left:0px;border-right:1px solid #DDDDDD;text-align:right;">
		
		<li style="box-sizing:border-box;margin:0px;padding:0px 5px;list-style:none;color:#999999;">
			1
		</li>

	</ul>
</pre>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:1.7em;padding:0px;line-height:27.2px;word-break:normal;color:#3F3F3F;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		4、启动centos的docker容器
	</p>
<pre class="prettyprint" style="box-sizing:border-box;font-family:&quot;font-size:14px;white-space:nowrap;padding:5px 5px 5px 60px;margin-top:0px;margin-bottom:1.7em;line-height:23.8px;color:#333333;word-break:break-all;word-wrap:break-word;background-color:rgba(128, 128, 128, 0.05);border:1px solid rgba(128, 128, 128, 0.075);border-radius:0px;position:relative;overflow-y:hidden;overflow-x:auto;"><code class="hljs applescript has-numbering" style="box-sizing:border-box;font-family:&quot;font-size:12.6px;padding:0px;color:inherit;white-space:pre;background:transparent;border-radius:0px;display:block;word-wrap:normal;">docker <span class="hljs-command" style="box-sizing:border-box;margin:0px;padding:0px;">run</span> -<span class="hljs-keyword" style="box-sizing:border-box;margin:0px;padding:0px;color:#000088;">it</span> <span class="hljs-comment" style="box-sizing:border-box;margin:0px;padding:0px;color:#880000;">--name=cenots-ssh centos /bin/bash</span></code>
	<ul class="pre-numbering" style="box-sizing:border-box;margin:0px;padding:6px 0px 40px;list-style:none;line-height:23.8px;position:absolute;width:50px;background-color:#EEEEEE;top:0px;left:0px;border-right:1px solid #DDDDDD;text-align:right;">
		
		<li style="box-sizing:border-box;margin:0px;padding:0px 5px;list-style:none;color:#999999;">
			1
		</li>

	</ul>
</pre>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:1.7em;padding:0px;line-height:27.2px;word-break:normal;color:#3F3F3F;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		5、进入到容器的交互模式后，升级系统并安装openssh-server
	</p>
<pre class="prettyprint" style="box-sizing:border-box;font-family:&quot;font-size:14px;white-space:nowrap;padding:5px 5px 5px 60px;margin-top:0px;margin-bottom:1.7em;line-height:23.8px;color:#333333;word-break:break-all;word-wrap:break-word;background-color:rgba(128, 128, 128, 0.05);border:1px solid rgba(128, 128, 128, 0.075);border-radius:0px;position:relative;overflow-y:hidden;overflow-x:auto;"><code class="hljs lasso has-numbering" style="box-sizing:border-box;font-family:&quot;font-size:12.6px;padding:0px;color:inherit;white-space:pre;background:transparent;border-radius:0px;display:block;word-wrap:normal;">yum <span class="hljs-attribute" style="box-sizing:border-box;margin:0px;padding:0px;">-y</span> update
yum install <span class="hljs-attribute" style="box-sizing:border-box;margin:0px;padding:0px;">-y</span> openssh<span class="hljs-attribute" style="box-sizing:border-box;margin:0px;padding:0px;">-server</span></code>
	<ul class="pre-numbering" style="box-sizing:border-box;margin:0px;padding:6px 0px 40px;list-style:none;line-height:23.8px;position:absolute;width:50px;background-color:#EEEEEE;top:0px;left:0px;border-right:1px solid #DDDDDD;text-align:right;">
		
		<li style="box-sizing:border-box;margin:0px;padding:0px 5px;list-style:none;color:#999999;">
			1
		</li>

		<li style="box-sizing:border-box;margin:0px;padding:0px 5px;list-style:none;color:#999999;">
			2
		</li>

	</ul>
</pre>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:1.7em;padding:0px;line-height:27.2px;word-break:normal;color:#3F3F3F;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		6、编辑sshd的配置文件/etc/ssh/sshd_config，将其中UsePAM参数设置成“no”
	</p>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:1.7em;padding:0px;line-height:27.2px;word-break:normal;color:#3F3F3F;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		7、生成RSA密钥对
	</p>
<pre class="prettyprint" style="box-sizing:border-box;font-family:&quot;font-size:14px;white-space:nowrap;padding:5px 5px 5px 60px;margin-top:0px;margin-bottom:1.7em;line-height:23.8px;color:#333333;word-break:break-all;word-wrap:break-word;background-color:rgba(128, 128, 128, 0.05);border:1px solid rgba(128, 128, 128, 0.075);border-radius:0px;position:relative;overflow-y:hidden;overflow-x:auto;"><code class="hljs lasso has-numbering" style="box-sizing:border-box;font-family:&quot;font-size:12.6px;padding:0px;color:inherit;white-space:pre;background:transparent;border-radius:0px;display:block;word-wrap:normal;"> ssh<span class="hljs-attribute" style="box-sizing:border-box;margin:0px;padding:0px;">-keygen</span> <span class="hljs-attribute" style="box-sizing:border-box;margin:0px;padding:0px;">-t</span> rsa <span class="hljs-attribute" style="box-sizing:border-box;margin:0px;padding:0px;">-b</span> <span class="hljs-number" style="box-sizing:border-box;margin:0px;padding:0px;color:#006666;">2048</span> <span class="hljs-attribute" style="box-sizing:border-box;margin:0px;padding:0px;">-f</span> /etc/ssh/ssh_host_rsa_key</code>
	<ul class="pre-numbering" style="box-sizing:border-box;margin:0px;padding:6px 0px 40px;list-style:none;line-height:23.8px;position:absolute;width:50px;background-color:#EEEEEE;top:0px;left:0px;border-right:1px solid #DDDDDD;text-align:right;">
		
		<li style="box-sizing:border-box;margin:0px;padding:0px 5px;list-style:none;color:#999999;">
			1
		</li>

	</ul>
</pre>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:1.7em;padding:0px;line-height:27.2px;word-break:normal;color:#3F3F3F;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		出现下面的提示的时候直接回车就行，需要按二次回车：
	</p>
<pre class="prettyprint" style="box-sizing:border-box;font-family:&quot;font-size:14px;white-space:nowrap;padding:5px 5px 5px 60px;margin-top:0px;margin-bottom:1.7em;line-height:23.8px;color:#333333;word-break:break-all;word-wrap:break-word;background-color:rgba(128, 128, 128, 0.05);border:1px solid rgba(128, 128, 128, 0.075);border-radius:0px;position:relative;overflow-y:hidden;overflow-x:auto;"><code class="hljs mathematica has-numbering" style="box-sizing:border-box;font-family:&quot;font-size:12.6px;padding:0px;color:inherit;white-space:pre;background:transparent;border-radius:0px;display:block;word-wrap:normal;"><span class="hljs-keyword" style="box-sizing:border-box;margin:0px;padding:0px;color:#000088;">Enter</span> passphrase (empty for no passphrase): <span class="hljs-keyword" style="box-sizing:border-box;margin:0px;padding:0px;color:#000088;">Enter</span> same passphrase again: </code>
	<ul class="pre-numbering" style="box-sizing:border-box;margin:0px;padding:6px 0px 40px;list-style:none;line-height:23.8px;position:absolute;width:50px;background-color:#EEEEEE;top:0px;left:0px;border-right:1px solid #DDDDDD;text-align:right;">
		
		<li style="box-sizing:border-box;margin:0px;padding:0px 5px;list-style:none;color:#999999;">
			1
		</li>

		<li style="box-sizing:border-box;margin:0px;padding:0px 5px;list-style:none;color:#999999;">
			2
		</li>

	</ul>
</pre>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:1.7em;padding:0px;line-height:27.2px;word-break:normal;color:#3F3F3F;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		同时需要在宿主机也生成密钥对，然后再将生成的公钥文件的内容复制到容器的/root/.ssh/authorized_keys文件中，如果文件不存在，新建一个。
	</p>
<pre class="prettyprint" style="box-sizing:border-box;font-family:&quot;font-size:14px;white-space:nowrap;padding:5px 5px 5px 60px;margin-top:0px;margin-bottom:1.7em;line-height:23.8px;color:#333333;word-break:break-all;word-wrap:break-word;background-color:rgba(128, 128, 128, 0.05);border:1px solid rgba(128, 128, 128, 0.075);border-radius:0px;position:relative;overflow-y:hidden;overflow-x:auto;"><code class="hljs ruby has-numbering" style="box-sizing:border-box;font-family:&quot;font-size:12.6px;padding:0px;color:inherit;white-space:pre;background:transparent;border-radius:0px;display:block;word-wrap:normal;">[root<span class="hljs-variable" style="box-sizing:border-box;margin:0px;padding:0px;color:#660066;">@localhost</span> ~]<span class="hljs-comment" style="box-sizing:border-box;margin:0px;padding:0px;color:#880000;"># cat /etc/ssh/ssh_host_rsa_key.pub</span> ssh-rsa <span class="hljs-constant" style="box-sizing:border-box;margin:0px;padding:0px;">AAAAB3NzaC1yc2EAAAABIwAAAQEArj0Qpmd2hWKsqOGa</span>/jvlXtFXQigz7rtiBbQUq0lA4OInWtUCmIj8076+<span class="hljs-constant" style="box-sizing:border-box;margin:0px;padding:0px;">PzYuSdnEznp3Gu4QD4TvQOrGby1Ui5hPaB</span>+lkkLTY/d7Mhx4fYMUcglMBz4aY5+<span class="hljs-constant" style="box-sizing:border-box;margin:0px;padding:0px;">ZloYzlfBkOHntOpimZ2NoL798bR0KYPGJvqEfRQnjkXmQOaRKJyTzYqqMBhPXOG2dn4</span>/<span class="hljs-constant" style="box-sizing:border-box;margin:0px;padding:0px;">TcPxbcgCmlcvcRpcW9a3DferFNXu27tQojtamGC1vUJ4Pyb3wd3WYINNyr0aY0gomHUbqTcGVUBAXpB</span>/<span class="hljs-constant" style="box-sizing:border-box;margin:0px;padding:0px;">QvI3Pdi9afXdFBnC</span>/<span class="hljs-constant" style="box-sizing:border-box;margin:0px;padding:0px;">F0sGECjftIVQfNCBBPCE9f4ZYbw</span>+<span class="hljs-constant" style="box-sizing:border-box;margin:0px;padding:0px;">JwVz</span>+yi8BoYrtelRRlfN2bbVvmN1Sw== root<span class="hljs-variable" style="box-sizing:border-box;margin:0px;padding:0px;color:#660066;">@localhost</span>.localdomain</code>
	<ul class="pre-numbering" style="box-sizing:border-box;margin:0px;padding:6px 0px 40px;list-style:none;line-height:23.8px;position:absolute;width:50px;background-color:#EEEEEE;top:0px;left:0px;border-right:1px solid #DDDDDD;text-align:right;">
		
		<li style="box-sizing:border-box;margin:0px;padding:0px 5px;list-style:none;color:#999999;">
			1
		</li>

		<li style="box-sizing:border-box;margin:0px;padding:0px 5px;list-style:none;color:#999999;">
			2
		</li>

	</ul>
</pre>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:1.7em;padding:0px;line-height:27.2px;word-break:normal;color:#3F3F3F;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		8、设置容器的root密码
	</p>
<pre class="prettyprint" style="box-sizing:border-box;font-family:&quot;font-size:14px;white-space:nowrap;padding:5px 5px 5px 60px;margin-top:0px;margin-bottom:1.7em;line-height:23.8px;color:#333333;word-break:break-all;word-wrap:break-word;background-color:rgba(128, 128, 128, 0.05);border:1px solid rgba(128, 128, 128, 0.075);border-radius:0px;position:relative;overflow-y:hidden;overflow-x:auto;"><code class="hljs bash has-numbering" style="box-sizing:border-box;font-family:&quot;font-size:12.6px;padding:0px;color:inherit;white-space:pre;background:transparent;border-radius:0px;display:block;word-wrap:normal;"><span class="hljs-built_in" style="box-sizing:border-box;margin:0px;padding:0px;color:#660066;">echo</span> <span class="hljs-string" style="box-sizing:border-box;margin:0px;padding:0px;color:#008800;">"root:147258"</span>|chpasswd</code>
	<ul class="pre-numbering" style="box-sizing:border-box;margin:0px;padding:6px 0px 40px;list-style:none;line-height:23.8px;position:absolute;width:50px;background-color:#EEEEEE;top:0px;left:0px;border-right:1px solid #DDDDDD;text-align:right;">
		
		<li style="box-sizing:border-box;margin:0px;padding:0px 5px;list-style:none;color:#999999;">
			1
		</li>

	</ul>
</pre>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:1.7em;padding:0px;line-height:27.2px;word-break:normal;color:#3F3F3F;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		9、启动sshd服务并退出容器
	</p>
<pre class="prettyprint" style="box-sizing:border-box;font-family:&quot;font-size:14px;white-space:nowrap;padding:5px 5px 5px 60px;margin-top:0px;margin-bottom:1.7em;line-height:23.8px;color:#333333;word-break:break-all;word-wrap:break-word;background-color:rgba(128, 128, 128, 0.05);border:1px solid rgba(128, 128, 128, 0.075);border-radius:0px;position:relative;overflow-y:hidden;overflow-x:auto;"><code class="hljs bash has-numbering" style="box-sizing:border-box;font-family:&quot;font-size:12.6px;padding:0px;color:inherit;white-space:pre;background:transparent;border-radius:0px;display:block;word-wrap:normal;">/usr/sbin/sshd -D <span class="hljs-keyword" style="box-sizing:border-box;margin:0px;padding:0px;color:#000088;">exit</span></code>
	<ul class="pre-numbering" style="box-sizing:border-box;margin:0px;padding:6px 0px 40px;list-style:none;line-height:23.8px;position:absolute;width:50px;background-color:#EEEEEE;top:0px;left:0px;border-right:1px solid #DDDDDD;text-align:right;">
		
		<li style="box-sizing:border-box;margin:0px;padding:0px 5px;list-style:none;color:#999999;">
			1
		</li>

		<li style="box-sizing:border-box;margin:0px;padding:0px 5px;list-style:none;color:#999999;">
			2
		</li>

	</ul>
</pre>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:1.7em;padding:0px;line-height:27.2px;word-break:normal;color:#3F3F3F;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		10、生成支持ssh的新的centos镜像&nbsp;<br style="box-sizing:border-box;" />
先查看刚刚运行过的窗口的ID
	</p>
<pre class="prettyprint" style="box-sizing:border-box;font-family:&quot;font-size:14px;white-space:nowrap;padding:5px 5px 5px 60px;margin-top:0px;margin-bottom:1.7em;line-height:23.8px;color:#333333;word-break:break-all;word-wrap:break-word;background-color:rgba(128, 128, 128, 0.05);border:1px solid rgba(128, 128, 128, 0.075);border-radius:0px;position:relative;overflow-y:hidden;overflow-x:auto;"><code class="hljs bash has-numbering" style="box-sizing:border-box;font-family:&quot;font-size:12.6px;padding:0px;color:inherit;white-space:pre;background:transparent;border-radius:0px;display:block;word-wrap:normal;">docker ps <span class="hljs-operator" style="box-sizing:border-box;margin:0px;padding:0px;">-a</span></code>
	<ul class="pre-numbering" style="box-sizing:border-box;margin:0px;padding:6px 0px 40px;list-style:none;line-height:23.8px;position:absolute;width:50px;background-color:#EEEEEE;top:0px;left:0px;border-right:1px solid #DDDDDD;text-align:right;">
		
		<li style="box-sizing:border-box;margin:0px;padding:0px 5px;list-style:none;color:#999999;">
			1
		</li>

	</ul>
</pre>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:1.7em;padding:0px;line-height:27.2px;word-break:normal;color:#3F3F3F;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		运行结果里有一个CONTAINER ID&nbsp;<br style="box-sizing:border-box;" />
比如我的运行结果是&nbsp;<br style="box-sizing:border-box;" />
6c40d0d2d8be
	</p>
<pre class="prettyprint" style="box-sizing:border-box;font-family:&quot;font-size:14px;white-space:nowrap;padding:5px 5px 5px 60px;margin-top:0px;margin-bottom:1.7em;line-height:23.8px;color:#333333;word-break:break-all;word-wrap:break-word;background-color:rgba(128, 128, 128, 0.05);border:1px solid rgba(128, 128, 128, 0.075);border-radius:0px;position:relative;overflow-y:hidden;overflow-x:auto;"><code class="hljs sql has-numbering" style="box-sizing:border-box;font-family:&quot;font-size:12.6px;padding:0px;color:inherit;white-space:pre;background:transparent;border-radius:0px;display:block;word-wrap:normal;">docker <span class="hljs-operator" style="box-sizing:border-box;margin:0px;padding:0px;"><span class="hljs-keyword" style="box-sizing:border-box;margin:0px;padding:0px;color:#000088;">commit</span> <span class="hljs-number" style="box-sizing:border-box;margin:0px;padding:0px;color:#006666;">6</span>c40d0d2d8be sshd-centos</span></code>
	<ul class="pre-numbering" style="box-sizing:border-box;margin:0px;padding:6px 0px 40px;list-style:none;line-height:23.8px;position:absolute;width:50px;background-color:#EEEEEE;top:0px;left:0px;border-right:1px solid #DDDDDD;text-align:right;">
		
		<li style="box-sizing:border-box;margin:0px;padding:0px 5px;list-style:none;color:#999999;">
			1
		</li>

	</ul>
</pre>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:1.7em;padding:0px;line-height:27.2px;word-break:normal;color:#3F3F3F;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		然后查看新生成的镜像：
	</p>
<pre class="prettyprint" style="box-sizing:border-box;font-family:&quot;font-size:14px;white-space:nowrap;padding:5px 5px 5px 60px;margin-top:0px;margin-bottom:1.7em;line-height:23.8px;color:#333333;word-break:break-all;word-wrap:break-word;background-color:rgba(128, 128, 128, 0.05);border:1px solid rgba(128, 128, 128, 0.075);border-radius:0px;position:relative;overflow-y:hidden;overflow-x:auto;"><code class="hljs has-numbering" style="box-sizing:border-box;font-family:&quot;font-size:12.6px;padding:0px;color:inherit;white-space:pre;background:transparent;border-radius:0px;display:block;word-wrap:normal;">docker images</code>
	<ul class="pre-numbering" style="box-sizing:border-box;margin:0px;padding:6px 0px 40px;list-style:none;line-height:23.8px;position:absolute;width:50px;background-color:#EEEEEE;top:0px;left:0px;border-right:1px solid #DDDDDD;text-align:right;">
		
		<li style="box-sizing:border-box;margin:0px;padding:0px 5px;list-style:none;color:#999999;">
			1
		</li>

	</ul>
</pre>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:1.7em;padding:0px;line-height:27.2px;word-break:normal;color:#3F3F3F;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		运行结果里就会有&nbsp;<br style="box-sizing:border-box;" />
sshd-centos
	</p>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:1.7em;padding:0px;line-height:27.2px;word-break:normal;color:#3F3F3F;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		11、根据新生成的镜像运行容器
	</p>
<pre class="prettyprint" style="box-sizing:border-box;font-family:&quot;font-size:14px;white-space:nowrap;padding:5px 5px 5px 60px;margin-top:0px;margin-bottom:1.7em;line-height:23.8px;color:#333333;word-break:break-all;word-wrap:break-word;background-color:rgba(128, 128, 128, 0.05);border:1px solid rgba(128, 128, 128, 0.075);border-radius:0px;position:relative;overflow-y:hidden;overflow-x:auto;"><code class="hljs lasso has-numbering" style="box-sizing:border-box;font-family:&quot;font-size:12.6px;padding:0px;color:inherit;white-space:pre;background:transparent;border-radius:0px;display:block;word-wrap:normal;">docker run <span class="hljs-attribute" style="box-sizing:border-box;margin:0px;padding:0px;">-p</span> <span class="hljs-number" style="box-sizing:border-box;margin:0px;padding:0px;color:#006666;">10022</span>:<span class="hljs-number" style="box-sizing:border-box;margin:0px;padding:0px;color:#006666;">22</span> <span class="hljs-attribute" style="box-sizing:border-box;margin:0px;padding:0px;">-d</span> sshd<span class="hljs-attribute" style="box-sizing:border-box;margin:0px;padding:0px;">-centos</span> /usr/sbin/sshd <span class="hljs-attribute" style="box-sizing:border-box;margin:0px;padding:0px;">-D</span></code>
	<ul class="pre-numbering" style="box-sizing:border-box;margin:0px;padding:6px 0px 40px;list-style:none;line-height:23.8px;position:absolute;width:50px;background-color:#EEEEEE;top:0px;left:0px;border-right:1px solid #DDDDDD;text-align:right;">
		
		<li style="box-sizing:border-box;margin:0px;padding:0px 5px;list-style:none;color:#999999;">
			1
		</li>

	</ul>
</pre>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:1.7em;padding:0px;line-height:27.2px;word-break:normal;color:#3F3F3F;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		新生成的窗口会将22端口映射到宿主机的10022端口，所以使用ssh登录该窗口的时候需要指定10022端口。
	</p>
</p>