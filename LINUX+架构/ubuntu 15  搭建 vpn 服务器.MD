<p style="box-sizing:border-box;margin-top:0px;margin-bottom:10px;color:#6B6B6B;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	在ubuntu下配置vpn的方式有很多种，其中比较常见的是pptpd,它配置简单，但是安全性不高，不过对于一般使用来说足够了，我按照程搭建了一个VPN的服务器，但是由于服务器系统是ubuntu 15.10，按照ubuntu 12.04或者ubuntu 12.10的教程搭建，总是出现无法连接服务器，后来经过查看服务器的日志，终于找到了解决在ubuntu 15下无法安装配置VPN的方法，现在将<a href="http://blog.lxx1.com/1209" target="_blank" style="box-sizing:border-box;background-color:transparent;color:#DA4453;text-decoration-line:none;transition:all 0.3s;">ubuntu使用pptpd搭建vpn服务器</a>的完整方法分享出来。<span id="more-1209" style="box-sizing:border-box;"></span>
</p>
<h1 style="box-sizing:border-box;margin:20px 0px 10px;font-size:28px;font-family:&quot;line-height:1.1;color:#DA4453;white-space:normal;background-color:#FFFFFF;">
	一、vpn搭建方法
</h1>
<h3 style="box-sizing:border-box;font-family:&quot;line-height:1.1;color:#DA4453;margin-top:20px;margin-bottom:10px;font-size:20px;white-space:normal;background-color:#FFFFFF;">
	1.安装pptpd
</h3>
<pre style="box-sizing:border-box;overflow:auto;font-family:Menlo, Monaco, Consolas, &quot;font-size:13px;padding:9.5px;margin-top:0px;margin-bottom:10px;line-height:1.42857;color:#333333;word-break:break-all;word-wrap:break-word;background-color:#F5F5F5;border:1px solid #CCCCCC;border-radius:4px;">sudo apt-get install pptpd</pre>
<h3 style="box-sizing:border-box;font-family:&quot;line-height:1.1;color:#DA4453;margin-top:20px;margin-bottom:10px;font-size:20px;white-space:normal;background-color:#FFFFFF;">
	2.配置内网ip策略
</h3>
<pre style="box-sizing:border-box;overflow:auto;font-family:Menlo, Monaco, Consolas, &quot;font-size:13px;padding:9.5px;margin-top:0px;margin-bottom:10px;line-height:1.42857;color:#333333;word-break:break-all;word-wrap:break-word;background-color:#F5F5F5;border:1px solid #CCCCCC;border-radius:4px;">sudo nano /etc/pptpd.conf</pre>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:10px;color:#6B6B6B;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	1、注释logwtmp，即在logwtmp这一行前面添加一个#号。
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:10px;color:#6B6B6B;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	2、在# TAG: localip后增加2行
</p>
<pre style="box-sizing:border-box;overflow:auto;font-family:Menlo, Monaco, Consolas, &quot;font-size:13px;padding:9.5px;margin-top:0px;margin-bottom:10px;line-height:1.42857;color:#333333;word-break:break-all;word-wrap:break-word;background-color:#F5F5F5;border:1px solid #CCCCCC;border-radius:4px;">localip 192.168.0.1</pre>
<pre style="box-sizing:border-box;overflow:auto;font-family:Menlo, Monaco, Consolas, &quot;font-size:13px;padding:9.5px;margin-top:0px;margin-bottom:10px;line-height:1.42857;color:#333333;word-break:break-all;word-wrap:break-word;background-color:#F5F5F5;border:1px solid #CCCCCC;border-radius:4px;">remoteip 192.168.0.234-238,192.168.0.245</pre>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:10px;color:#6B6B6B;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	上面配置的localip为服务器的ip地址，在搭建vpn的时候要根据自己服务器的地址来设置。
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:10px;color:#6B6B6B;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	remoteip为连接vpn的客户端ip地址，一般情况下不需要更改。
</p>
<h3 style="box-sizing:border-box;font-family:&quot;line-height:1.1;color:#DA4453;margin-top:20px;margin-bottom:10px;font-size:20px;white-space:normal;background-color:#FFFFFF;">
	3.配置dns
</h3>
<pre style="box-sizing:border-box;overflow:auto;font-family:Menlo, Monaco, Consolas, &quot;font-size:13px;padding:9.5px;margin-top:0px;margin-bottom:10px;line-height:1.42857;color:#333333;word-break:break-all;word-wrap:break-word;background-color:#F5F5F5;border:1px solid #CCCCCC;border-radius:4px;">sudo nano /etc/ppp/pptpd-options</pre>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:10px;color:#6B6B6B;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	在#ms-dns后增加2行，也可以配置其他dns
</p>
<pre style="box-sizing:border-box;overflow:auto;font-family:Menlo, Monaco, Consolas, &quot;font-size:13px;padding:9.5px;margin-top:0px;margin-bottom:10px;line-height:1.42857;color:#333333;word-break:break-all;word-wrap:break-word;background-color:#F5F5F5;border:1px solid #CCCCCC;border-radius:4px;">ms-dns 121.42.42.51</pre>
<pre style="box-sizing:border-box;overflow:auto;font-family:Menlo, Monaco, Consolas, &quot;font-size:13px;padding:9.5px;margin-top:0px;margin-bottom:10px;line-height:1.42857;color:#333333;word-break:break-all;word-wrap:break-word;background-color:#F5F5F5;border:1px solid #CCCCCC;border-radius:4px;">ms-dns 114.114.114.114</pre>
<h3 style="box-sizing:border-box;font-family:&quot;line-height:1.1;color:#DA4453;margin-top:20px;margin-bottom:10px;font-size:20px;white-space:normal;background-color:#FFFFFF;">
	4.配置VPN帐号
</h3>
<pre style="box-sizing:border-box;overflow:auto;font-family:Menlo, Monaco, Consolas, &quot;font-size:13px;padding:9.5px;margin-top:0px;margin-bottom:10px;line-height:1.42857;color:#333333;word-break:break-all;word-wrap:break-word;background-color:#F5F5F5;border:1px solid #CCCCCC;border-radius:4px;">sudo nano /etc/ppp/chap-secrets</pre>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:10px;color:#6B6B6B;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	在其中依次添加账号、服务器名、密码和IP限制，一个帐号一行，每个参数中间用tab或者空格间隔。如：
</p>
<pre style="box-sizing:border-box;overflow:auto;font-family:Menlo, Monaco, Consolas, &quot;font-size:13px;padding:9.5px;margin-top:0px;margin-bottom:10px;line-height:1.42857;color:#333333;word-break:break-all;word-wrap:break-word;background-color:#F5F5F5;border:1px solid #CCCCCC;border-radius:4px;">zhangsan pptpd 123456 *</pre>
<pre style="box-sizing:border-box;overflow:auto;font-family:Menlo, Monaco, Consolas, &quot;font-size:13px;padding:9.5px;margin-top:0px;margin-bottom:10px;line-height:1.42857;color:#333333;word-break:break-all;word-wrap:break-word;background-color:#F5F5F5;border:1px solid #CCCCCC;border-radius:4px;">lisi pptpd 123456 *</pre>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:10px;color:#6B6B6B;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	其中user、passwd为自己设置的账户名以及密码
</p>
<h3 style="box-sizing:border-box;font-family:&quot;line-height:1.1;color:#DA4453;margin-top:20px;margin-bottom:10px;font-size:20px;white-space:normal;background-color:#FFFFFF;">
	5. 设置TCP/IP数据转发
</h3>
<pre style="box-sizing:border-box;overflow:auto;font-family:Menlo, Monaco, Consolas, &quot;font-size:13px;padding:9.5px;margin-top:0px;margin-bottom:10px;line-height:1.42857;color:#333333;word-break:break-all;word-wrap:break-word;background-color:#F5F5F5;border:1px solid #CCCCCC;border-radius:4px;">sudo nano /etc/sysctl.conf</pre>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:10px;color:#6B6B6B;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	插入一行：
</p>
<pre style="box-sizing:border-box;overflow:auto;font-family:Menlo, Monaco, Consolas, &quot;font-size:13px;padding:9.5px;margin-top:0px;margin-bottom:10px;line-height:1.42857;color:#333333;word-break:break-all;word-wrap:break-word;background-color:#F5F5F5;border:1px solid #CCCCCC;border-radius:4px;">net.ipv4.ip_forward=1</pre>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:10px;color:#6B6B6B;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	保存并退出vim
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:10px;color:#6B6B6B;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	执行
</p>
<pre style="box-sizing:border-box;overflow:auto;font-family:Menlo, Monaco, Consolas, &quot;font-size:13px;padding:9.5px;margin-top:0px;margin-bottom:10px;line-height:1.42857;color:#333333;word-break:break-all;word-wrap:break-word;background-color:#F5F5F5;border:1px solid #CCCCCC;border-radius:4px;">sudo sysctl –p</pre>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:10px;color:#6B6B6B;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	提示net.ipv4.ip_forward = 1，说明配置生效
</p>
<h3 style="box-sizing:border-box;font-family:&quot;line-height:1.1;color:#DA4453;margin-top:20px;margin-bottom:10px;font-size:20px;white-space:normal;background-color:#FFFFFF;">
	6.开放网络端口
</h3>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:10px;color:#6B6B6B;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	安装iptables(已安装请忽略)
</p>
<pre style="box-sizing:border-box;overflow:auto;font-family:Menlo, Monaco, Consolas, &quot;font-size:13px;padding:9.5px;margin-top:0px;margin-bottom:10px;line-height:1.42857;color:#333333;word-break:break-all;word-wrap:break-word;background-color:#F5F5F5;border:1px solid #CCCCCC;border-radius:4px;">sudo apt-get install iptables</pre>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:10px;color:#6B6B6B;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	开放1723端口
</p>
<pre style="box-sizing:border-box;overflow:auto;font-family:Menlo, Monaco, Consolas, &quot;font-size:13px;padding:9.5px;margin-top:0px;margin-bottom:10px;line-height:1.42857;color:#333333;word-break:break-all;word-wrap:break-word;background-color:#F5F5F5;border:1px solid #CCCCCC;border-radius:4px;">sudo iptables -I INPUT -p tcp –dport 1723 -j ACCEPT</pre>
<h3 style="box-sizing:border-box;font-family:&quot;line-height:1.1;color:#DA4453;margin-top:20px;margin-bottom:10px;font-size:20px;white-space:normal;background-color:#FFFFFF;">
	7.配置NAT网络地址转换
</h3>
<pre style="box-sizing:border-box;overflow:auto;font-family:Menlo, Monaco, Consolas, &quot;font-size:13px;padding:9.5px;margin-top:0px;margin-bottom:10px;line-height:1.42857;color:#333333;word-break:break-all;word-wrap:break-word;background-color:#F5F5F5;border:1px solid #CCCCCC;border-radius:4px;">sudo iptables –table nat –append POSTROUTING –out-interface eth0 –jump MASQUERADE</pre>
<h3 style="box-sizing:border-box;font-family:&quot;line-height:1.1;color:#DA4453;margin-top:20px;margin-bottom:10px;font-size:20px;white-space:normal;background-color:#FFFFFF;">
	8.重启pptpd
</h3>
<pre style="box-sizing:border-box;overflow:auto;font-family:Menlo, Monaco, Consolas, &quot;font-size:13px;padding:9.5px;margin-top:0px;margin-bottom:10px;line-height:1.42857;color:#333333;word-break:break-all;word-wrap:break-word;background-color:#F5F5F5;border:1px solid #CCCCCC;border-radius:4px;">sudo /etc/init.d/procps restart</pre>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:10px;color:#6B6B6B;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	搭建完毕。
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:10px;color:#6B6B6B;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	注：如果6、7、8这三个步骤执行不成功，可以用以下方法代替：
</p>
<blockquote style="box-sizing:border-box;padding:10px 20px;margin:0px 0px 20px;font-size:17.5px;border-left:5px solid #EEEEEE;color:#6B6B6B;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:10px;">
		6、然后我们需要安装iptables，用来实现请求的NAT转发
	</p>
	<div style="box-sizing:border-box;">
		<div id="highlighter_329195" class="syntaxhighlighter shell" style="box-sizing:border-box;">
<pre class="toolbar" style="box-sizing:border-box;overflow:auto;font-family:Menlo, Monaco, Consolas, &quot;font-size:13px;padding:9.5px;margin-top:0px;margin-bottom:10px;line-height:1.42857;color:#333333;word-break:break-all;word-wrap:break-word;background-color:#F5F5F5;border:1px solid #CCCCCC;border-radius:4px;"><span style="box-sizing:border-box;line-height:1.5;"><code class="shell functions" style="box-sizing:border-box;font-family:Menlo, Monaco, Consolas, &quot;font-size:inherit;padding:0px;color:inherit;background-color:transparent;border-radius:0px;white-space:pre-wrap;">sudo</code>&nbsp;<code class="shell plain" style="box-sizing:border-box;font-family:Menlo, Monaco, Consolas, &quot;font-size:inherit;padding:0px;color:inherit;background-color:transparent;border-radius:0px;white-space:pre-wrap;">apt-get&nbsp;</code><code class="shell functions" style="box-sizing:border-box;font-family:Menlo, Monaco, Consolas, &quot;font-size:inherit;padding:0px;color:inherit;background-color:transparent;border-radius:0px;white-space:pre-wrap;">install</code>&nbsp;<code class="shell plain" style="box-sizing:border-box;font-family:Menlo, Monaco, Consolas, &quot;font-size:inherit;padding:0px;color:inherit;background-color:transparent;border-radius:0px;white-space:pre-wrap;">iptables</code></span></pre>
			<div class="toolbar" style="box-sizing:border-box;">
				<span style="box-sizing:border-box;line-height:1.5;">7、然后开启NAT转发.</span>
			</div>
		</div>
	</div>
<pre style="box-sizing:border-box;overflow:auto;font-family:Menlo, Monaco, Consolas, &quot;font-size:13px;padding:9.5px;margin-top:0px;margin-bottom:10px;line-height:1.42857;color:#333333;word-break:break-all;word-wrap:break-word;background-color:#F5F5F5;border:1px solid #CCCCCC;border-radius:4px;"><code class="shell functions" style="box-sizing:border-box;font-family:Menlo, Monaco, Consolas, &quot;font-size:inherit;padding:0px;color:inherit;background-color:transparent;border-radius:0px;white-space:pre-wrap;">sudo</code>&nbsp;<code class="shell plain" style="box-sizing:border-box;font-family:Menlo, Monaco, Consolas, &quot;font-size:inherit;padding:0px;color:inherit;background-color:transparent;border-radius:0px;white-space:pre-wrap;">iptables&nbsp;-t&nbsp;nat&nbsp;-A&nbsp;POSTROUTING&nbsp;-s&nbsp;192.168.0.0</code><code class="shell plain" style="box-sizing:border-box;font-family:Menlo, Monaco, Consolas, &quot;font-size:inherit;padding:0px;color:inherit;background-color:transparent;border-radius:0px;white-space:pre-wrap;">/24</code>&nbsp;<code class="shell plain" style="box-sizing:border-box;font-family:Menlo, Monaco, Consolas, &quot;font-size:inherit;padding:0px;color:inherit;background-color:transparent;border-radius:0px;white-space:pre-wrap;">-o&nbsp;eth0&nbsp;-j&nbsp;MASQUERADE</code></pre>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:10px;">
		192.168.0.0/24是你在上面设置的IP段，让这个段转发
	</p>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:10px;">
		注意eth0是你连接外网的那块网卡，不一定是0也有可能是1或者看你的机器哪块网卡连的外网了。这样就以NAT的方式请求外网的东西了。不知道你的机器哪块网卡连的外网的话ifconfig一下看看哪个网卡是外网IP就知道了。
	</p>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:10px;">
		8、最后，我们需要重启服务，让配置生效 .
	</p>
<pre style="box-sizing:border-box;overflow:auto;font-family:Menlo, Monaco, Consolas, &quot;font-size:13px;padding:9.5px;margin-top:0px;margin-bottom:10px;line-height:1.42857;color:#333333;word-break:break-all;word-wrap:break-word;background-color:#F5F5F5;border:1px solid #CCCCCC;border-radius:4px;"><code class="shell functions" style="box-sizing:border-box;font-family:Menlo, Monaco, Consolas, &quot;font-size:inherit;padding:0px;color:inherit;background-color:transparent;border-radius:0px;white-space:pre-wrap;">sudo</code>&nbsp;<code class="shell plain" style="box-sizing:border-box;font-family:Menlo, Monaco, Consolas, &quot;font-size:inherit;padding:0px;color:inherit;background-color:transparent;border-radius:0px;white-space:pre-wrap;">service&nbsp;pptpd&nbsp;restart</code></pre>
</blockquote>
<h1 style="box-sizing:border-box;margin:20px 0px 10px;font-size:28px;font-family:&quot;line-height:1.1;color:#DA4453;white-space:normal;background-color:#FFFFFF;">
	二、设置失败的解决办法
</h1>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:10px;color:#6B6B6B;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;font-weight:700;">问题</span>：搭建后连接vpn服务器失败，提示“无法连接vpn服务器，连接端口已经关闭”。
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:10px;color:#6B6B6B;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;font-weight:700;">日志</span>：使用 tail -f /var/log/ syslog 来查看日志，提示如下：
</p>
<pre style="box-sizing:border-box;overflow:auto;font-family:Menlo, Monaco, Consolas, &quot;font-size:13px;padding:9.5px;margin-top:0px;margin-bottom:10px;line-height:1.42857;color:#333333;word-break:break-all;word-wrap:break-word;background-color:#F5F5F5;border:1px solid #CCCCCC;border-radius:4px;">Dec 29 09:39:33 linux-server pptpd[2228]: CTRL: Client 10.12.8.197 control connection started
Dec 29 09:39:33 linux-server pptpd[2228]: CTRL: Starting call (launching pppd, opening GRE)
Dec 29 09:39:33 linux-server pptpd[2156]: /usr/sbin/pppd: Plugin /usr/lib/pptpd/pptpd-logwtmp.so is for pppd version 2.4.5, this is 2.4.6
Dec 29 09:39:33 linux-server pppd[2229]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so is for pppd version 2.4.5, this is 2.4.6
Dec 29 09:39:33 linux-server pptpd[2228]: GRE: read(fd=6,buffer=800cb480,len=8196) from PTY failed: status = -1 error = Input/output error, usually caused by unexpected termination of pppd, check option syntax and pppd logs
Dec 29 09:39:33 linux-server pptpd[2228]: CTRL: PTY read or GRE write failed (pty,gre)=(6,7)
Dec 29 09:39:33 linux-server pptpd[2228]: CTRL: Reaping child PPP[2229]
Dec 29 09:39:33 linux-server pptpd[2228]: CTRL: Client 10.12.8.197 control connection finished</pre>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:10px;color:#6B6B6B;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;font-weight:700;">解决办法</span>：
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:10px;color:#6B6B6B;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	这是由于服务器升级到ubuntu 15 后引起的，在配置pptpd 时需要注释logwtmp，即在logwtmp这一行前面添加一个#号。
</p>