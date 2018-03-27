<br />
<p>
	http://www.cnblogs.com/zz0412/p/install_Subversion_edge_4-0-1.html
</p>
<p>
	<br />
</p>
<p>
	<span style="font-size:16px;">CSVN官网&nbsp;</span><span style="font-size:16px;"> <a href="http://www.collab.net/downloads/subversion#tab-1/cn">http://www.collab.net/downloads/subversion#tab-1/cn</a></span> 
</p>
<br />
2014-04-14:修正部分描述。添加JAVA_HOME报错处理步骤。添加配置sudoers<br />
<br />
系统：CentOS 5.8 ，6.4<br />
<br />
Subversion版本：Subversion Edge 4.0.1 (Linux 64-bit)（点我去下载）<br />
<br />
环境要求：<br />
<br />
* Java 1.6+ JRE/JDK must be installed.<br />
* Python 2.4 to 2.6 must be installed.&nbsp;<br />
<br />
注意事项：<br />
<br />
解压时不能用root权限或加sudo命令。测试时发现，使用JDK6可以自动识别，JDK7需要手动设置JAVA_HOME<br />
<br />
原因：<br />
<br />
IMPORTANT: Do not untar CollabNet Subversion Edge using root or sudo.<br />
<br />
This will cause the UID/GID on the files to carry the values from our build<br />
system instead of being reset.<br />
<br />
&nbsp;<br />
<br />
&nbsp;下载软件，上传到服务器及相应的环境依赖都略过不提。<br />
安装Subversion edge<br />
<br />
(文件放在/home/test目录下)<br />
<br />
&nbsp; &nbsp; 新建用户（因为不能用root解压和启动）<br />
<br />
&nbsp; &nbsp; #使用root用户<br />
&nbsp; &nbsp; useradd test<br />
<br />
&nbsp; &nbsp; &nbsp;<br />
&nbsp; &nbsp; 修改密码<br />
<br />
&nbsp; &nbsp; #使用root用户<br />
&nbsp; &nbsp; passwd test<br />
&nbsp; &nbsp; #输入俩次密码<br />
<br />
&nbsp; &nbsp; &nbsp;<br />
&nbsp; &nbsp; 解压tar<br />
<br />
&nbsp; &nbsp; su test　　#切换用户<br />
&nbsp; &nbsp; cd ~　　#回到test用户目录<br />
&nbsp; &nbsp; #上传文件略过<br />
&nbsp; &nbsp; tar xf /home/test/CollabNetSubversionEdge-*.tar.gz -C /home/test<br />
<br />
&nbsp; &nbsp; &nbsp;<br />
&nbsp; &nbsp; 配置csvn使用1-1023端口的权限[可选]<br />
<br />
&nbsp; &nbsp; #使用root用户<br />
&nbsp; &nbsp; chown root:test /home/test/csvn/lib/httpd_bind/httpd_bind　　#root:test的test更换成你的用户，后面的路径同理<br />
&nbsp; &nbsp; chmod u+s /home/test/csvn/lib/httpd_bind/httpd_bind<br />
<br />
&nbsp; &nbsp; &nbsp;<br />
&nbsp; &nbsp; 配置开机启动[可选]<br />
<br />
&nbsp; &nbsp; sudo bin/csvn-httpd install &nbsp; &nbsp; #svn服务端<br />
&nbsp; &nbsp; sudo -E bin/csvn install &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; #web页面<br />
<br />
&nbsp; &nbsp; centos默认是不允许普通用户使用sudo命令，需要配置sudoers文件。ubuntu没有这个烦恼。<br />
<br />
&nbsp; &nbsp; &nbsp;使用root用户配置如下：<br />
<br />
&nbsp; &nbsp; #使用root用户<br />
&nbsp; &nbsp; visudo #编辑sudoers文件<br />
&nbsp; &nbsp; #在root &nbsp; &nbsp;ALL=(ALL) &nbsp; &nbsp; &nbsp; ALL下添加<br />
&nbsp; &nbsp; test &nbsp; ALL=(ALL) &nbsp; &nbsp; &nbsp; ALL &nbsp; &nbsp;#test是你的用户<br />
&nbsp; &nbsp; #保存退出即可<br />
<br />
&nbsp; &nbsp; &nbsp;<br />
&nbsp; &nbsp; 启动Subversion edge<br />
&nbsp; &nbsp; 复制代码<br />
<br />
&nbsp; &nbsp; cd csvn/bin/<br />
&nbsp; &nbsp; sh csvn start　　#启动<br />
&nbsp; &nbsp; #如果使用start启动失败，可以使用下面的命令<br />
&nbsp; &nbsp; sh csvn console　　#此命令会在控制台输出启动日志，便于确定是什么错误导致启动失败<br />
<br />
&nbsp; &nbsp; #注意：如果确认已经安装JDK，但是程序依然提示没有找到。请配置如下<br />
&nbsp; &nbsp; vim data/conf/csvn.conf<br />
&nbsp; &nbsp; #在#JAVA_HOME下添加如下<br />
&nbsp; &nbsp; JAVA_HOME="/usr/java/xxxx" &nbsp; #/usr/java/xxxx是你自己的JDK路径<br />
<br />
&nbsp; &nbsp; 复制代码<br />
<br />
&nbsp; &nbsp; &nbsp;<br />
<br />
&nbsp; &nbsp; &nbsp;<br />
&nbsp; &nbsp; 访问Subversion edge<br />
&nbsp; &nbsp; 复制代码<br />
<br />
&nbsp; &nbsp; Address: http://localhost:3343/csvn<br />
&nbsp; &nbsp; You can access the SSL version on this URL:<br />
&nbsp; &nbsp; Address: https://localhost:4434/csvn<br />
&nbsp; &nbsp; #根据自己的需求选择Address，如果是在其他机器上访问，记得把localhost换成ip，下面的防火墙规则同理<br />
&nbsp; &nbsp; Username: admin<br />
&nbsp; &nbsp; Password: admin<br />
&nbsp; &nbsp; #如果开启了防火墙，需要添加防火墙规则<br />
<br />
&nbsp; &nbsp; iptables -A INPUT -m state --state NEW -m tcp -p tcp --dport 3343 -j ACCEPT<br />
&nbsp; &nbsp; #或者<br />
&nbsp; &nbsp; iptables -A INPUT -m state --state NEW -m tcp -p tcp --dport 4434 -j ACCEPT<br />
<br />
&nbsp; &nbsp; #保存防火墙规则<br />
&nbsp; &nbsp; /etc/init.d/iptables save<br />
<br />
&nbsp; &nbsp; #重启防火墙<br />
&nbsp; &nbsp; /etc/init.d/iptables restart<br />
<br />
&nbsp; &nbsp; #注意：如果依然不能访问，请查看防火墙规则的顺序。<br />
<br />
&nbsp; &nbsp; 复制代码<br />
<br />
&nbsp; &nbsp; &nbsp;<br />
<br />
&nbsp;好了，到此就安装完成了。<br />
配置Subversion edge<br />
<br />
&nbsp; &nbsp; 登陆(默认用户名admin、密码admin)&nbsp;<br />