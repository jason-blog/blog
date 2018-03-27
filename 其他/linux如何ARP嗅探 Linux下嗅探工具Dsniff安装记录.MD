<span style="color:#333333;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">先来下载依赖包 和一些必须要用到的工具</span>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	我这里用的是 dsniff-2.3 的版本
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	wget http://www.monkey.org/~dugsong/dsniff/dsniff-2.3.tar.gz<br style="margin:0px;padding:0px;" />
wget http://www.8090sec.com/uploads/soft/dsniff-2.3.tar.gz 备用下载
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<br style="margin:0px;padding:0px;" />
<span style="margin:0px;padding:0px;color:#FF0000;"><span style="margin:0px;padding:0px;font-family:黑体;"><strong style="margin:0px;padding:0px;">一、安装gcc</strong></span></span>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	# yum -y install gcc
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<br style="margin:0px;padding:0px;" />
<span style="margin:0px;padding:0px;color:#FF0000;"><span style="margin:0px;padding:0px;font-family:黑体;"><strong style="margin:0px;padding:0px;">二、安装 openssl 直接yum安装也可以的</strong></span></span>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	# tar zxvf openssl-0.9.7i.tar.gz<br style="margin:0px;padding:0px;" />
# cd openssl-0.9.7i<br style="margin:0px;padding:0px;" />
# ./config<br style="margin:0px;padding:0px;" />
# make<br style="margin:0px;padding:0px;" />
# make install
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<br style="margin:0px;padding:0px;" />
<span style="margin:0px;padding:0px;color:#FF0000;"><span style="margin:0px;padding:0px;font-family:黑体;"><strong style="margin:0px;padding:0px;">三、安装flex 和 bison</strong></span></span>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	# yum -y install flex<br style="margin:0px;padding:0px;" />
# yum -y install bison
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<br style="margin:0px;padding:0px;" />
<span style="margin:0px;padding:0px;color:#FF0000;"><span style="margin:0px;padding:0px;font-family:黑体;"><strong style="margin:0px;padding:0px;">四、安装 libpcap 直接yum安装也可以</strong><br style="margin:0px;padding:0px;" />
&nbsp;<br style="margin:0px;padding:0px;" />
#wget http://www.tcpdump.org/release/libpcap-0.7.2.tar.gz<br style="margin:0px;padding:0px;" />
# tar zxvf libpcap-0.7.2.tar.gz<br style="margin:0px;padding:0px;" />
# cd libpcap-0.7.2<br style="margin:0px;padding:0px;" />
# ./configure<br style="margin:0px;padding:0px;" />
# make<br style="margin:0px;padding:0px;" />
# make install<br style="margin:0px;padding:0px;" />
# wget http://www.8090sec.com/uploads/soft/libpcap-0.7.2.tar.gz 备用下载</span></span>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;color:#FF0000;"><span style="margin:0px;padding:0px;font-family:黑体;"><strong style="margin:0px;padding:0px;">五、安装 libnet</strong><br style="margin:0px;padding:0px;" />
# wget http://ips-builder.googlecode.com/files/libnet-1.0.2a.tar.gz<br style="margin:0px;padding:0px;" />
# tar zxvf libnet-1.0.2a.tar.gz<br style="margin:0px;padding:0px;" />
# cd Libnet-1.0.2a<br style="margin:0px;padding:0px;" />
# ./configure<br style="margin:0px;padding:0px;" />
# make<br style="margin:0px;padding:0px;" />
# make install<br style="margin:0px;padding:0px;" />
# wget http://www.8090sec.com/uploads/soft/libnet-1.0.2a.tar.gz 备用下载</span></span>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<br style="margin:0px;padding:0px;" />
<span style="margin:0px;padding:0px;color:#FF0000;"><span style="margin:0px;padding:0px;font-family:黑体;"><strong style="margin:0px;padding:0px;">六、安装 libnids</strong><br style="margin:0px;padding:0px;" />
# wget http://distro.ibiblio.org/openwall/projects/scanlogd/lib/libnids-1.18.tar.gz<br style="margin:0px;padding:0px;" />
# tar zxvf libnids-1.18.tar.gz<br style="margin:0px;padding:0px;" />
# cd libnids-1.18<br style="margin:0px;padding:0px;" />
# ./configure<br style="margin:0px;padding:0px;" />
# make<br style="margin:0px;padding:0px;" />
# make install<br style="margin:0px;padding:0px;" />
# wget http://www.8090sec.com/uploads/soft/libnids-1.18.tar.gz 备用下载</span></span>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;color:#FF0000;"><span style="margin:0px;padding:0px;font-family:黑体;"><strong style="margin:0px;padding:0px;">七、安装BerkeleyDB</strong><br style="margin:0px;padding:0px;" />
# wget http://download.oracle.com/berkeley-db/db-4.7.25.tar.gz<br style="margin:0px;padding:0px;" />
# tar zxvf db-4.7.25.tar.gz<br style="margin:0px;padding:0px;" />
# cd db-4.7.25/build_unix<br style="margin:0px;padding:0px;" />
# ../dist/configure --enable-compat185<br style="margin:0px;padding:0px;" />
# make<br style="margin:0px;padding:0px;" />
# make install</span></span>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<br style="margin:0px;padding:0px;" />
<span style="margin:0px;padding:0px;color:#FF0000;"><span style="margin:0px;padding:0px;font-family:黑体;"><strong style="margin:0px;padding:0px;">八、安装dsniff</strong></span></span>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	# tar zxvf dsniff-2.3.tar.gz<br style="margin:0px;padding:0px;" />
# cd dsniff-2.3<br style="margin:0px;padding:0px;" />
# vi arp.c 加入 #include "memory.h"<br style="margin:0px;padding:0px;" />
# ./configure --enable-compat185 --with-db=/usr/local/BerkeleyDB.4.7<br style="margin:0px;padding:0px;" />
# make<br style="margin:0px;padding:0px;" />
# make install
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;color:#FF0000;"><span style="margin:0px;padding:0px;font-family:黑体;"><strong style="margin:0px;padding:0px;">九、其它设置</strong></span></span>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	# vi /etc/sysctl.conf
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	修改 net.ipv4.ip_forward = 1
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	# sysctl -p
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;color:#FF0000;"><span style="margin:0px;padding:0px;font-family:黑体;"><strong style="margin:0px;padding:0px;">十、使用dsniff</strong></span></span>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	# cp /usr/local/BerkeleyDB.4.7/lib/libdb-4.7.so /usr/lib<br style="margin:0px;padding:0px;" />
# cd /usr/local/sbin;ls<br style="margin:0px;padding:0px;" />
# ./dsniff --help
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	环境：
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	网关--&gt; 192.168.1.1
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	路人甲 --&gt; 192.168.1.123 (CentOS6.0 + dsniff-2.3)
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	路人乙 --&gt; 192.168.1.125(Cent0S6.0 + Apache + Mysql)
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<br style="margin:0px;padding:0px;" />
目的：
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	使用 路人甲 嗅探 路人乙 的FTP、http 登录密码
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<br style="margin:0px;padding:0px;" />
1. 使用 arpspoof 对目标机实施ARP欺骗攻击<br style="margin:0px;padding:0px;" />
# arpspoof -i eth0 -t 192.168.1.125 192.168.1.1
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	2. 使用 dsniff 取得指定端口的数据信息&nbsp;<br style="margin:0px;padding:0px;" />
# dsniff -i eth0 -t 21/tcp=ftp,80/tcp=http
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;<br style="margin:0px;padding:0px;" />
&nbsp;
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	Dsniff支持的协议类型包括：&nbsp;&nbsp;<br style="margin:0px;padding:0px;" />
FTP，Telnet，SMTP，HTTP，POP，NNTP，IMAP，SNMP，LDAP，Rlogin，RIP，OSP&nbsp;&nbsp;<br style="margin:0px;padding:0px;" />
F，PPTP，MS-CHAP，NFS，VRRP，YP/NIS，SOCKS，X11，CVS，IRC，AIM，ICQ，Napster，ostgreSQL，Meeting Maker，Citrix ICA，Symantec，pcAnywhere，NA&nbsp;&nbsp;<br style="margin:0px;padding:0px;" />
I Sniffer，Microsoft SMB，Oracle QL*Net，Sybase及Microsoft SQL认证信息
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<br style="margin:0px;padding:0px;" />
编译遇到的问题可能有:<br style="margin:0px;padding:0px;" />
http://distro.ibiblio.org/openwall/projects/scanlogd/lib/<br style="margin:0px;padding:0px;" />
3个环境配子的文件 libnet libpcap libnids 注意安装编译的顺序,不然会无法成功 如果遇到编译错误无法解决更换版本多试试看.不一定要以上几个版本才行
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	另外推荐大家适应另外一个Linux下的嗅探工具&nbsp;ettercap NG 后期我会给大家更新
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;font-family:黑体;"><strong style="margin:0px;padding:0px;">ettercap嗅探工具</strong></span>
</p>
<div style="margin:0px;padding:0px;color:#333333;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<iframe id="iframe_0.41943203142494045" src="data:text/html;charset=utf8,%3Cstyle%3Ebody%7Bmargin:0;padding:0%7D%3C/style%3E%3Cimg%20id=%22img%22%20src=%22http://www.2cto.com/uploadfile/2014/0628/20140628114850270.jpg?_=5889659%22%20style=%22border:none;max-width:848px%22%3E%3Cscript%3Ewindow.onload%20=%20function%20()%20%7Bvar%20img%20=%20document.getElementById('img');%20window.parent.postMessage(%7BiframeId:'iframe_0.41943203142494045',width:img.width,height:img.height%7D,%20'http://www.cnblogs.com');%7D%3C/script%3E" frameborder="0" scrolling="no" style="margin:0px;padding:0px;border-width:initial;border-style:none;width:578px;height:461px;">
	</iframe>
</div>