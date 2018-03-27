<div id="article_content" class="article_content csdn-tracking-statistics" data-pid="blog" data-mod="popu_307" data-dsm="post" style="margin:35px 0px;font-size:15px;color:#555555;line-height:35px;word-break:break-all;font-family:&quot;white-space:normal;overflow:hidden;">
	<p>
		<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;color:#4F4F4F;line-height:26px;text-align:justify;word-break:normal;">
			http://blog.csdn.net/fungleo/article/details/49888685
		</p>
		<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;color:#4F4F4F;line-height:26px;text-align:justify;word-break:normal;">
			CentOS7.1出来已经很久了，我的服务器也顺利的配置为了7.1，但是是运维同事帮我操作的。而上次出现问题，我重启了一下，出现了很多问题，折腾了很久才把问题解决。
		</p>
		<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;color:#4F4F4F;line-height:26px;text-align:justify;word-break:normal;">
			因此，我决定，好好的学习一下 CentOS 7 的日常使用。
		</p>
		<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;color:#4F4F4F;line-height:26px;text-align:justify;word-break:normal;">
			折腾虚拟机，怎么安装，这个就不说了。说说遇到的问题，和相应的解决方法
		</p>
		<h2 id="安装完成后配置网络的问题" style="margin:8px 0px 16px;padding:0px;box-sizing:border-box;font-family:inherit;line-height:32px;color:#4F4F4F;font-size:24px;">
			<a name="t1"></a>安装完成后，配置网络的问题
		</h2>
		<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;color:#4F4F4F;line-height:26px;text-align:justify;word-break:normal;">
			安装完成后，ping 一下百度，不能访问。说明网络不通。
		</p>
		<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;color:#4F4F4F;line-height:26px;text-align:justify;word-break:normal;">
			查看本机IP 发现ifconfig命令不好使了。百度一下，知道用IP命令替代了原来的 ifconfig 好啊，这个命令要短很多基本不用记忆了。
		</p>
		<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;color:#4F4F4F;line-height:26px;text-align:justify;word-break:normal;">
			收集一下IP命令方法如下：
		</p>
<pre class="prettyprint" name="code" style="white-space:nowrap;word-wrap:break-word;box-sizing:border-box;position:relative;overflow-y:hidden;overflow-x:auto;margin-top:0px;margin-bottom:24px;font-family:Consolas, Inconsolata, Courier, monospace;padding:8px 16px 4px 56px;font-size:14px;line-height:22px;word-break:break-all;color:#000000;background-color:#F6F8FA;border:none;border-radius:0px;"><code class="language-language hljs livecodeserver has-numbering" style="display:block;padding:0px;background-image:initial;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;box-sizing:border-box;font-family:Consolas, Inconsolata, Courier, monospace;white-space:pre;border-radius:4px;line-height:22px;overflow-x:auto;word-wrap:normal;">ip link show <span class="hljs-comment" style="color:#880000;box-sizing:border-box;"># 显示网络接口信息</span> ip link <span class="hljs-built_in" style="color:#4F4F4F;box-sizing:border-box;">set</span> eth0 upi <span class="hljs-comment" style="color:#880000;box-sizing:border-box;"># 开启网卡</span> ip link <span class="hljs-built_in" style="color:#4F4F4F;box-sizing:border-box;">set</span> eth0 down <span class="hljs-comment" style="color:#880000;box-sizing:border-box;"># 关闭网卡</span> ip link <span class="hljs-built_in" style="color:#4F4F4F;box-sizing:border-box;">set</span> eth0 promisc <span class="hljs-command" style="box-sizing:border-box;"><span class="hljs-keyword" style="color:#000088;box-sizing:border-box;">on</span> # 开启网卡的混合模式</span> ip link <span class="hljs-built_in" style="color:#4F4F4F;box-sizing:border-box;">set</span> eth0 promisc offi <span class="hljs-comment" style="color:#880000;box-sizing:border-box;"># 关闭网卡的混个模式</span> ip link <span class="hljs-built_in" style="color:#4F4F4F;box-sizing:border-box;">set</span> eth0 txqueuelen <span class="hljs-number" style="color:#006666;box-sizing:border-box;">1200</span> <span class="hljs-comment" style="color:#880000;box-sizing:border-box;"># 设置网卡队列长度</span> ip link <span class="hljs-built_in" style="color:#4F4F4F;box-sizing:border-box;">set</span> eth0 mtu <span class="hljs-number" style="color:#006666;box-sizing:border-box;">1400</span> <span class="hljs-comment" style="color:#880000;box-sizing:border-box;"># 设置网卡最大传输单元</span> ip addr show <span class="hljs-comment" style="color:#880000;box-sizing:border-box;"># 显示网卡IP信息</span> ip addr <span class="hljs-built_in" style="color:#4F4F4F;box-sizing:border-box;">add</span> <span class="hljs-number" style="color:#006666;box-sizing:border-box;">192.168</span><span class="hljs-number" style="color:#006666;box-sizing:border-box;">.0</span><span class="hljs-number" style="color:#006666;box-sizing:border-box;">.1</span>/<span class="hljs-number" style="color:#006666;box-sizing:border-box;">24</span> dev eth0 <span class="hljs-comment" style="color:#880000;box-sizing:border-box;"># 设置eth0网卡IP地址192.168.0.1</span> ip addr del <span class="hljs-number" style="color:#006666;box-sizing:border-box;">192.168</span><span class="hljs-number" style="color:#006666;box-sizing:border-box;">.0</span><span class="hljs-number" style="color:#006666;box-sizing:border-box;">.1</span>/<span class="hljs-number" style="color:#006666;box-sizing:border-box;">24</span> dev eth0 <span class="hljs-comment" style="color:#880000;box-sizing:border-box;"># 删除eth0网卡IP地址</span> ip route list <span class="hljs-comment" style="color:#880000;box-sizing:border-box;"># 查看路由信息</span> ip route <span class="hljs-built_in" style="color:#4F4F4F;box-sizing:border-box;">add</span> <span class="hljs-number" style="color:#006666;box-sizing:border-box;">192.168</span><span class="hljs-number" style="color:#006666;box-sizing:border-box;">.4</span><span class="hljs-number" style="color:#006666;box-sizing:border-box;">.0</span>/<span class="hljs-number" style="color:#006666;box-sizing:border-box;">24</span>via192<span class="hljs-number" style="color:#006666;box-sizing:border-box;">.168</span><span class="hljs-number" style="color:#006666;box-sizing:border-box;">.0</span><span class="hljs-number" style="color:#006666;box-sizing:border-box;">.254</span> dev eth0 <span class="hljs-comment" style="color:#880000;box-sizing:border-box;"># 设置192.168.4.0网段的网关为192.168.0.254,数据走eth0接口</span> ip route <span class="hljs-built_in" style="color:#4F4F4F;box-sizing:border-box;">add</span> default via192<span class="hljs-number" style="color:#006666;box-sizing:border-box;">.168</span><span class="hljs-number" style="color:#006666;box-sizing:border-box;">.0</span><span class="hljs-number" style="color:#006666;box-sizing:border-box;">.254</span>dev eth0 <span class="hljs-comment" style="color:#880000;box-sizing:border-box;"># 设置默认网关为192.168.0.254</span> ip route del <span class="hljs-number" style="color:#006666;box-sizing:border-box;">192.168</span><span class="hljs-number" style="color:#006666;box-sizing:border-box;">.4</span><span class="hljs-number" style="color:#006666;box-sizing:border-box;">.0</span>/<span class="hljs-number" style="color:#006666;box-sizing:border-box;">24</span> <span class="hljs-comment" style="color:#880000;box-sizing:border-box;"># 删除192.168.4.0网段的网关</span> ip route del default <span class="hljs-comment" style="color:#880000;box-sizing:border-box;"># 删除默认路由</span></code>
		<ul class="pre-numbering" style="box-sizing:border-box;margin:0px;padding:8px 0px;position:absolute;width:48px;background-color:#EEF0F4;top:0px;left:0px;border-right:1px solid #DDDDDD;list-style:none;text-align:right;">
			
			<li style="box-sizing:border-box;list-style:none;margin:0px;padding:0px 5px;">
				1
			</li>

			<li style="box-sizing:border-box;list-style:none;margin:0px;padding:0px 5px;">
				2
			</li>

			<li style="box-sizing:border-box;list-style:none;margin:0px;padding:0px 5px;">
				3
			</li>

			<li style="box-sizing:border-box;list-style:none;margin:0px;padding:0px 5px;">
				4
			</li>

			<li style="box-sizing:border-box;list-style:none;margin:0px;padding:0px 5px;">
				5
			</li>

			<li style="box-sizing:border-box;list-style:none;margin:0px;padding:0px 5px;">
				6
			</li>

			<li style="box-sizing:border-box;list-style:none;margin:0px;padding:0px 5px;">
				7
			</li>

			<li style="box-sizing:border-box;list-style:none;margin:0px;padding:0px 5px;">
				8
			</li>

			<li style="box-sizing:border-box;list-style:none;margin:0px;padding:0px 5px;">
				9
			</li>

			<li style="box-sizing:border-box;list-style:none;margin:0px;padding:0px 5px;">
				10
			</li>

			<li style="box-sizing:border-box;list-style:none;margin:0px;padding:0px 5px;">
				11
			</li>

			<li style="box-sizing:border-box;list-style:none;margin:0px;padding:0px 5px;">
				12
			</li>

			<li style="box-sizing:border-box;list-style:none;margin:0px;padding:0px 5px;">
				13
			</li>

			<li style="box-sizing:border-box;list-style:none;margin:0px;padding:0px 5px;">
				14
			</li>

			<li style="box-sizing:border-box;list-style:none;margin:0px;padding:0px 5px;">
				15
			</li>

			<li style="box-sizing:border-box;list-style:none;margin:0px;padding:0px 5px;">
				16
			</li>

		</ul>
</pre>
		<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;color:#4F4F4F;line-height:26px;text-align:justify;word-break:normal;">
			使用 ip addr 命令看了一下，果然没有没有配置IP地址。进入&nbsp;<code style="box-sizing:border-box;font-family:Consolas, Inconsolata, Courier, monospace;padding:4px 2px 0px;font-size:14px;color:#C7254E;background-color:#F9F2F4;white-space:nowrap;border-radius:2px;line-height:22px;">/etc/sysconfig/network-scripts/</code>&nbsp;查看&nbsp;<code style="box-sizing:border-box;font-family:Consolas, Inconsolata, Courier, monospace;padding:4px 2px 0px;font-size:14px;color:#C7254E;background-color:#F9F2F4;white-space:nowrap;border-radius:2px;line-height:22px;">ifcfg-eth0</code>&nbsp;文件，我去，没有这个文件-_-!!!
		</p>
		<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;color:#4F4F4F;line-height:26px;text-align:justify;word-break:normal;">
			看看有啥呢？发现一个文件，文件名为：<code style="box-sizing:border-box;font-family:Consolas, Inconsolata, Courier, monospace;padding:4px 2px 0px;font-size:14px;color:#C7254E;background-color:#F9F2F4;white-space:nowrap;border-radius:2px;line-height:22px;">ifcfg-eno16777736</code>&nbsp;我勒个去，这是什么奇葩名字啊？ vi 打开瞅一眼
		</p>
		<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;color:#4F4F4F;line-height:26px;text-align:justify;word-break:normal;">
			果然，这是网卡配置信息。不过奇葩的是 它的&nbsp;<code style="box-sizing:border-box;font-family:Consolas, Inconsolata, Courier, monospace;padding:4px 2px 0px;font-size:14px;color:#C7254E;background-color:#F9F2F4;white-space:nowrap;border-radius:2px;line-height:22px;">ONBOOT=no</code>&nbsp;好像就是这个原因导致不能正常上网的。改成&nbsp;<code style="box-sizing:border-box;font-family:Consolas, Inconsolata, Courier, monospace;padding:4px 2px 0px;font-size:14px;color:#C7254E;background-color:#F9F2F4;white-space:nowrap;border-radius:2px;line-height:22px;">ONBOOT=yes</code>&nbsp;:wq 保存文件。重启网络服务&nbsp;<code style="box-sizing:border-box;font-family:Consolas, Inconsolata, Courier, monospace;padding:4px 2px 0px;font-size:14px;color:#C7254E;background-color:#F9F2F4;white-space:nowrap;border-radius:2px;line-height:22px;">service network restart</code>&nbsp;。然后在ping一下百度，果然ping通了。这就说明网络正常了。
		</p>
		<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;color:#4F4F4F;line-height:26px;text-align:justify;word-break:normal;">
			不过这里有一个问题，我需要把虚拟机里面的IP给定死，否则每次访问都不知道IP是啥，这是个问题。
		</p>
		<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;color:#4F4F4F;line-height:26px;text-align:justify;word-break:normal;">
			再次VI这个文件。再里面添加上
		</p>
<pre class="prettyprint" name="code" style="white-space:nowrap;word-wrap:break-word;box-sizing:border-box;position:relative;overflow-y:hidden;overflow-x:auto;margin-top:0px;margin-bottom:24px;font-family:Consolas, Inconsolata, Courier, monospace;padding:8px 16px 4px 56px;font-size:14px;line-height:22px;word-break:break-all;color:#000000;background-color:#F6F8FA;border:none;border-radius:0px;"><code class="language-language hljs makefile has-numbering" style="display:block;padding:0px;background-image:initial;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;box-sizing:border-box;font-family:Consolas, Inconsolata, Courier, monospace;white-space:pre;border-radius:4px;line-height:22px;overflow-x:auto;word-wrap:normal;"><span class="hljs-comment" style="color:#880000;box-sizing:border-box;">#BOOTPROTO=dhcp</span> <span class="hljs-constant" style="box-sizing:border-box;color:#009900;">IPADDR0</span>=192.168.1.254 <span class="hljs-constant" style="box-sizing:border-box;color:#009900;">PREFIX0</span>=24 <span class="hljs-constant" style="box-sizing:border-box;color:#009900;">GATEWAY0</span>=192.168.1.1 <span class="hljs-constant" style="box-sizing:border-box;color:#009900;">DNS1</span>=114.114.114.114</code>
		<ul class="pre-numbering" style="box-sizing:border-box;margin:0px;padding:8px 0px;position:absolute;width:48px;background-color:#EEF0F4;top:0px;left:0px;border-right:1px solid #DDDDDD;list-style:none;text-align:right;">
			
			<li style="box-sizing:border-box;list-style:none;margin:0px;padding:0px 5px;">
				1
			</li>

			<li style="box-sizing:border-box;list-style:none;margin:0px;padding:0px 5px;">
				2
			</li>

			<li style="box-sizing:border-box;list-style:none;margin:0px;padding:0px 5px;">
				3
			</li>

			<li style="box-sizing:border-box;list-style:none;margin:0px;padding:0px 5px;">
				4
			</li>

			<li style="box-sizing:border-box;list-style:none;margin:0px;padding:0px 5px;">
				5
			</li>

		</ul>
</pre>
		<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;color:#4F4F4F;line-height:26px;text-align:justify;word-break:normal;">
			这里要把dhcp给关闭，所以在前面加上一个#号，注释掉。
		</p>
		<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;color:#4F4F4F;line-height:26px;text-align:justify;word-break:normal;">
			再次保存，然后重启网络服务&nbsp;<code style="box-sizing:border-box;font-family:Consolas, Inconsolata, Courier, monospace;padding:4px 2px 0px;font-size:14px;color:#C7254E;background-color:#F9F2F4;white-space:nowrap;border-radius:2px;line-height:22px;">service network restart</code>&nbsp;。
		</p>
		<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;color:#4F4F4F;line-height:26px;text-align:justify;word-break:normal;">
			好了，在宿主机上用putty连接一下，果然连上了。
		</p>
		<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;color:#4F4F4F;line-height:26px;text-align:justify;word-break:normal;">
			PS：文章技术资料来自于网络。
		</p>
		<div>
			<br />
		</div>
	</p>
</div>
<ul class="article_next_prev" style="margin-top:0px;font-family:&quot;white-space:normal;">
</ul>