iptables -L -n 查看所有<br />
<p>
	<br />
</p>
<p>
	iptables -I INPUT -s 10.1.1.111/32 -p tcp -m multiport --dports 22,80,443,9998,9999 -m comment --comment "test" -j ACCEPT
</p>
<p>
	<br />
</p>
iptables -A INPUT -s 192.168.0.3 -p tcp --dport 22 -j ACCEPT<br />
<br />
<br />
<br />
&nbsp;iptables -nvL --line-number //显示行数<br />
<br />
&nbsp;iptables -D INPUT -s 192.168.1.5 -j DROP //删除<br />
&nbsp;<br />
&nbsp;iptables -D INPUT 2 //删除第二行<br />
&nbsp;<br />
&nbsp;<br />
&nbsp;iptables -A INPUT -s 114.198.146.186 -p tcp --dport 3306 -j ACCEPT<br />
&nbsp;<br />
&nbsp;iptables -A INPUT -m state --state NEW -m tcp -s 114.198.146.186 -p tcp --dport 3306 -j ACCEPT |DROP<br />
&nbsp;<br />
&nbsp;<br />
&nbsp;&nbsp;<br />
&nbsp;<br />
&nbsp; ip段<br />
&nbsp;192.168.0.0/24可用IP：192.168.0.0--192.168.0.255<br style="line-height:28px;" />
172.16.0.0/16可用IP：172.16.0.0---172.16.255.255<br style="line-height:28px;" />
10.0.0.0/8可用IP：10.0.0.0---10.255.255.255 &nbsp;<br />
&nbsp;<br />
&nbsp;1、打开防火墙配置文件<br />
vi &nbsp;/etc/sysconfig/iptables<br />
2、增加下面一行<br />
-A INPUT -m state --state NEW -m tcp -p tcp --dport 3306 -j ACCEPT<br />
3、重启防火墙<br />
service &nbsp;iptables restart<br />