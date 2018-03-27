<h1 class="title" id="page-title" style="margin:0px;font-size:1.3em;color:#777777;font-family:Verdana, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
	使用ssh正向连接、反向连接、做socks代理的方法
</h1>
<div class="tabs" style="font-family:Verdana, Arial, Helvetica, sans-serif;font-size:12.16px;white-space:normal;background-color:#FFFFFF;">
</div>
<div class="region region-content" style="font-family:Verdana, Arial, Helvetica, sans-serif;font-size:12.16px;white-space:normal;background-color:#FFFFFF;">
	<div id="block-system-main" class="block block-system" style="border-bottom:none;padding:0px 0px 0.75em;margin-bottom:1.5em;">
		<div class="content">
			<div id="node-755" class="node node-blog node-promoted clearfix" style="margin:0.5em 0px 2em;">
				<span class="submitted" style="color:#999999;font-size:0.8em;">Sat, 12/01/2012 - 20:54 -&nbsp;<span class="username">tlbluestar</span></span>
				<div class="content" style="line-height:1.4em;margin:0.5em 0px;">
					<div class="field field-name-body field-type-text-with-summary field-label-hidden">
						<div class="field-items">
							<div class="field-item even">
								<p style="margin-top:0.5em;margin-bottom:0.9em;">
									来源地址：&nbsp;<a href="http://dzmailbox.blog.163.com/blog/static/120534385201232642637847/" style="text-decoration:none;font-weight:bold;color:#336699;">http://dzmailbox.blog.163.com/blog/static/120534385201232642637847/</a>
								</p>
								<h1 style="margin-bottom:0.5em;font-size:1.3em;">
									【原创】使用ssh正向连接、反向连接、做socks代理的方法
								</h1>
								<p style="margin-top:0.5em;margin-bottom:0.9em;">
									最近才发现ssh有多么的强大！<br />
在网上搜了半天，发现大多数人都是一瓶子不满的水平，浅尝辄止。就没有几个人有点儿科学研究的精神吗？为啥不把它搞明白呢？<br />
当然，相信有不少人是很明白的，但是不愿意写博文来公开。其实这样大可不必，独乐乐不如众乐乐，何必那么小肚鸡肠？
								</p>
								<h2 style="margin-bottom:0.5em;font-size:1.2em;">
									1、用ssh做正向连接
								</h2>
								<p style="margin-top:0.5em;margin-bottom:0.9em;">
									啥叫正向连接？就是client连上server，然后把server能访问的机器地址和端口（当然也包括server自己）镜像到client的端口上。<br />
命令：
								</p>
								<div class="codeblock" style="padding:5px;border:1px solid #CCCCCC;background-color:#EEEEEE;">
									<code>ssh -L [客户端IP或省略]:[客户端端口]:[服务器侧能访问的IP]:[服务器侧能访问的IP的端口] [登陆服务器的用户名@服务器IP] -p [服务器ssh服务端口（默认22）]</code>
								</div>
								<p style="margin-top:0.5em;margin-bottom:0.9em;">
									其中，客户端IP可以省略，省略的话就是127.0.0.1了，也就是说只能在客户端本地访问。服务器IP都可以用域名来代替。
								</p>
								<p style="margin-top:0.5em;margin-bottom:0.9em;">
									举例说明：<br />
你的IP是192.168.1.2，你可以ssh到某台服务器8.8.8.8，8.8.8.8可以访问8.8.4.4，你内网里还有一台机器可以访问你。<br />
如果你想让内网里的另外一台电脑访问8.8.4.4的80端口的http服务，那么可以执行：
								</p>
								<div class="codeblock" style="padding:5px;border:1px solid #CCCCCC;background-color:#EEEEEE;">
									<code>ssh -L 192.168.1.2:8080:8.8.4.4:80 test@8.8.8.8</code>
								</div>
								<p style="margin-top:0.5em;margin-bottom:0.9em;">
									也就是说，ssh到8.8.8.8上，然后让8.8.8.8把8.8.4.4的80端口映射到本地的8080端口上，而且和本地192.168.1.2这个IP绑定。
								</p>
								<p style="margin-top:0.5em;margin-bottom:0.9em;">
									内网里的另外一台机器可以通过IE浏览器中输入<a href="http://192.168.1.2:8080/" style="text-decoration:none;font-weight:bold;color:#336699;">http://192.168.1.2:8080</a>查看8.8.4.4的网页。<br />
当然，如果是其他服务，比如ftp、ssh、远程桌面也是可以的。不过，VPN貌似是不行的，可能是因为GRE协议无法通过。
								</p>
								<h2 style="margin-bottom:0.5em;font-size:1.2em;">
									2、用ssh做反向连接
								</h2>
								<p style="margin-top:0.5em;margin-bottom:0.9em;">
									啥叫反向连接？就是client连上server，然后把client能访问的机器地址和端口（也包括client自己）镜像到server的端口上。<br />
反向连接用得可能更多一些。比如你的客户端在内网，在外网是无法直接访问到的，这时用反向连接打通一条隧道，就可以从外网通过这条隧道进来了。
								</p>
								<p style="margin-top:0.5em;margin-bottom:0.9em;">
									命令：
								</p>
								<div class="codeblock" style="padding:5px;border:1px solid #CCCCCC;background-color:#EEEEEE;">
									<code>ssh -R [服务器IP或省略]:[服务器端口]:[客户端侧能访问的IP]:[客户端侧能访问的IP的端口] [登陆服务器的用户名@服务器IP] -p [服务器ssh服务端口（默认22）]</code>
								</div>
								<p style="margin-top:0.5em;margin-bottom:0.9em;">
									其中，服务器IP如果省略，则默认为127.0.0.1，只有服务器自身可以访问。指定服务器外网IP的话，任何人都可以通过[服务器IP:端口]来访问服务。当然，这个时候服务器本机也要输入外网IP:端口来访问。
								</p>
								<p style="margin-top:0.5em;margin-bottom:0.9em;">
									举例说明：<br />
你的IP是192.168.1.2，你可以ssh到外网某台服务器8.8.8.8，你内网里有一台机器192.168.1.3。<br />
如果你想让外网所有的能访问8.8.8.8的IP都能访问192.168.1.3的http服务，那么可以执行：
								</p>
								<div class="codeblock" style="padding:5px;border:1px solid #CCCCCC;background-color:#EEEEEE;">
									<code>ssh -R 8.8.8.8:8080:192.168.1.3:80 test@8.8.8.8</code>
								</div>
								<p style="margin-top:0.5em;margin-bottom:0.9em;">
									也就是说，ssh到8.8.8.8上，然后把本地局域网内192.168.1.3的80端口映射到8.8.8.8的8080端口上，这样外网任何一台可以访问8.8.8.8的机器都可以通过8080端口访问到内网192.168.1.3机器的80端口了。<br />
反向连接同样支持各种服务。
								</p>
								<h2 style="margin-bottom:0.5em;font-size:1.2em;">
									3、用ssh做socks代理
								</h2>
								<p style="margin-top:0.5em;margin-bottom:0.9em;">
									假设你内网里某台机器可以上网，但是你不能上网，如果你有ssh到那台机器的权限，那么就可以利用ssh方式建立一个代理socks5，通过代理来上网。
								</p>
								<p style="margin-top:0.5em;margin-bottom:0.9em;">
									命令：
								</p>
								<div class="codeblock" style="padding:5px;border:1px solid #CCCCCC;background-color:#EEEEEE;">
									<code>ssh -D [本地IP或省略]:[本地端口] [登陆服务器的用户名@服务器IP] -p [服务器ssh服务端口（默认22）]</code>
								</div>
								<p style="margin-top:0.5em;margin-bottom:0.9em;">
									道理和上面是一样的，执行这个命令之后，本地会监听指定的端口等待连接。<br />
网上好多文章说Firefox和Chrome要下载什么插件才能支持，其实都是扯淡。<br />
在配置代理的时候直接选择Sock5就可以了，不需要用户名和密码验证。另外，IE也是支持Sock5的，具体配置方法是：勾选为LAN使用代理服务器，然后任何字段都不要填，点“高级”按钮，在套接字里面填好相应的配置，其他都留空。<br />
Chrome默认采用IE的配置，所以如果IE配置好了，Chrome也是可以上网的。<br />
另外，可以使用一个叫做Sockscap的软件，把应用扔进去就能以代理的方式上网了。（部分需要调用多个进程的应用可能不行）
								</p>
								<p style="margin-top:0.5em;margin-bottom:0.9em;">
									说句题外话，QQ2012版目前的Socks5代理上网功能貌似不支持本地Socks5代理，不过可以选择“浏览器配置”方式来规避。
								</p>
								<h4 style="margin-bottom:0.5em;font-size:1.1em;">
									把socks代理转换成http代理
								</h4>
								<p style="margin-top:0.5em;margin-bottom:0.9em;">
									如果你想把socks代理转换成http代理，可以用privoxy这个东东。去官网下载个.zip的文件包，然后解压到任意目录，执行可执行文件。<br />
在主界面点击Options菜单-&gt;Edit Main Configuration，在弹出的文本文件中搜索forward-socks5，找到的章节就是讲socks5转换的。<br />
回车新建一行，输入forward-socks5 / [本地IP]:[本地端口] . 注意后面还有个“.”，然后保存。<br />
这样就可以实现把socks5代理转换成127.0.0.1:8118的http代理了。程序可以通过127.0.0.1:8118这个http代理上网。<br />
如果你想让局域网内其他IP也能通过你的机器上网，需要修改配置文件中的listen-address部分，搜索一下相信你就会看明白了。
								</p>
								<h2 style="margin-bottom:0.5em;font-size:1.2em;">
									4、Windows下的ssh和ssh server
								</h2>
								<p style="margin-top:0.5em;margin-bottom:0.9em;">
									不要以为只有Linux下才能用ssh，Windows下一样有强大的ssh命令行工具和ssh服务器。并且对以上功能支持的都很好。<br />
那就是伟大的PuTTY！去官方网站下载吧！<br />
ssh命令行客户端对应的是plink.exe，命令稍微有一点不同（比如指定端口是大写的P），具体看帮助文件稍作修改就好了。<br />
ssh服务器端是WinSSHD，傻瓜式安装，默认配置支持windows用户认证。
								</p>
								<h2 style="margin-bottom:0.5em;font-size:1.2em;">
									5、自动连接和防断线脚本
								</h2>
								<p style="margin-top:0.5em;margin-bottom:0.9em;">
									如果你想让连接长期保持，可以写个脚本来保证因为网络原因断线的话可以自动重连。<br />
先说Windows平台，用plink -pw参数可以指定密码，所以只要写个批处理：
								</p>
								<div class="codeblock" style="padding:5px;border:1px solid #CCCCCC;background-color:#EEEEEE;">
									<code>:1<br />
plink -pw “password” -D 7070&nbsp;<a href="mailto:user@serverip" style="text-decoration:none;font-weight:bold;color:#336699;">user@serverip</a><br />
goto 1</code>
								</div>
								<p style="margin-top:0.5em;margin-bottom:0.9em;">
									这样应该就可以解决大多数问题造成的断线。
								</p>
								<p style="margin-top:0.5em;margin-bottom:0.9em;">
									Linux平台ssh默认不支持把密码作为参数，不过有sshpass可以搞定<br />
<a href="http://sourceforge.net/projects/sshpass/files/latest/download" style="text-decoration:none;font-weight:bold;color:#336699;">http://sourceforge.net/projects/sshpass/files/latest/download</a><br />
下载，解压，编译，把可执行文件拷贝到合适的目录，执行命令格式如下：
								</p>
								<div class="codeblock" style="padding:5px;border:1px solid #CCCCCC;background-color:#EEEEEE;">
									<code>sshpass -p "password" ssh -D 7070&nbsp;<a href="mailto:user@serverip" style="text-decoration:none;font-weight:bold;color:#336699;">user@serverip</a></code>
								</div>
								<p style="margin-top:0.5em;margin-bottom:0.9em;">
									貌似ubuntu下可以直接apt-get install sshpass<br />
然后写脚本autossh.sh，内容如下：
								</p>
								<div class="codeblock" style="padding:5px;border:1px solid #CCCCCC;background-color:#EEEEEE;">
									<code>#!/bin/bash
									<p style="margin-top:0.5em;margin-bottom:0.9em;">
										while [ '' == '' ]<br />
do<br />
ssh_d_process_num=`ps aux|grep -E 'ssh \-' |grep -v grep |wc -l`<br />
if [ "$ssh_d_process_num" == "0" ]; then<br />
&nbsp; /home/user/sshpass -p "password" ssh -D 7070&nbsp;<a href="mailto:user@ServerIP" style="text-decoration:none;font-weight:bold;color:#336699;">user@ServerIP</a>&nbsp;&amp;<br />
fi
									</p>
</code>
									<p style="margin-top:0.5em;margin-bottom:0.9em;">
										<code>sleep 300<br />
done</code>
									</p>
								</div>
								<p style="margin-top:0.5em;margin-bottom:0.9em;">
									执行一下这个脚本就可以了。sleep 300代表300秒查看一次，可以根据需要调整。
								</p>
								<h2 style="margin-bottom:0.5em;font-size:1.2em;">
									6、常用参数
								</h2>
								<p style="margin-top:0.5em;margin-bottom:0.9em;">
									其实一般来说不是很有必要加特殊的参数，不过以下几个可以根据需要选择<br />
-q 静默运行，就算出错也啥都不提示<br />
-f 后台运行<br />
-C 压缩，带宽很差的时候压缩会快一些，否则会更慢<br />
-i xxx.file 提供公钥文件直接验证<br />
-l 指定用户名，其实就是@前面写的那个。<br />
其他的不太常用，自己查手册吧~
								</p>
							</div>
						</div>
					</div>
					<div class="field field-name-taxonomy-vocabulary-1 field-type-taxonomy-term-reference field-label-above">
						<div class="field-label" style="font-weight:bold;">
							Topics:&nbsp;
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</div>