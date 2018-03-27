<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	# whereis iptables #查看系统是否安装防火墙可以看到:<br />
iptables: /sbin/iptables /usr/share/iptables /usr/share/man/man8/iptables.8.gz #表示已经安装iptables<br />
apt-get install iptables #如果默认没有安装，请运行此命令安装防火墙
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	# iptables -L #查看防火墙配置信息，显示如下:<br />
Chain INPUT (policy ACCEPT)<br />
target prot opt source destination<br />
Chain FORWARD (policy ACCEPT)<br />
target prot opt source destination<br />
Chain OUTPUT (policy ACCEPT)<br />
target prot opt source destination
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	# vi /etc/iptables.rules
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	添加以下内容(备注:80是指web服务器端口,3306是指MySQL数据库链接端口,22是指SSH远程管理端口.)<br />
*filter<br />
:INPUT DROP [0:0]<br />
:FORWARD ACCEPT [0:0]<br />
:OUTPUT ACCEPT [0:0]<br />
:syn-flood - [0:0]<br />
-A INPUT -i lo -j ACCEPT<br />
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT<br />
-A INPUT -p tcp -m state --state NEW -m tcp --dport 22 -j ACCEPT<br />
-A INPUT -p tcp -m state --state NEW -m tcp --dport 80 -j ACCEPT<br />
-A INPUT -p tcp -m state --state NEW -m tcp --dport 443 -j ACCEPT<br />
-A INPUT -p icmp -m limit --limit 100/sec --limit-burst 100 -j ACCEPT<br />
-A INPUT -p icmp -m limit --limit 1/s --limit-burst 10 -j ACCEPT<br />
-A INPUT -p tcp -m tcp --tcp-flags FIN,SYN,RST,ACK SYN -j syn-flood<br />
-A INPUT -j REJECT --reject-with icmp-host-prohibited<br />
-A syn-flood -p tcp -m limit --limit 3/sec --limit-burst 6 -j RETURN<br />
-A syn-flood -j REJECT --reject-with icmp-port-unreachable<br />
COMMIT
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	# iptables-restore &lt; /etc/iptables.rules #使防火墙规则生效
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	# vi /etc/network/if-pre-up.d/iptables #创建文件，添加以下内容，使防火墙开机启动<br />
#!/bin/bash<br />
iptables-restore &lt; /etc/iptables.rules
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	# chmod +x /etc/network/if-pre-up.d/iptables #添加执行权限
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	# iptables -L -n查看规则是否生效.
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	<span style="color:#032F62;font-family:SFMono-Regular, Consolas, &quot;white-space:pre;background-color:#FFFFFF;">iptables-save &gt; /tmp/current.ipt&nbsp; #备份原有策略</span>
</p>