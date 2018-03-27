SOCK5代理服务器<br />
官网: http://ss5.sourceforge.net/&nbsp;<br />
yum -y install gcc gcc-c++ automake make pam-devel openldap-devel cyrus-sasl-devel&nbsp;<br />
<br />
yum install openssl-devel(这个也要装)<br />
<br />
一、安装<br />
# tar xvf ss5-3.8.9-5.tar.gz<br />
# cd ss5-3.8.9-5<br />
# ./configure &amp;&amp; make &amp;&amp; make install<br />
<br />
二、修改配置文件<br />
1、修改/etc/opt/ss5/ss5.conf&nbsp;<br />
auth &nbsp; &nbsp; &nbsp;0.0.0.0/0 &nbsp; &nbsp; &nbsp; - &nbsp; &nbsp; &nbsp; &nbsp; u<br />
permit u &nbsp; &nbsp; &nbsp; &nbsp;0.0.0.0/0 &nbsp; &nbsp; &nbsp; - &nbsp; &nbsp; &nbsp; 0.0.0.0/0 &nbsp; &nbsp; &nbsp; - &nbsp; &nbsp; &nbsp; - &nbsp; &nbsp; &nbsp; - &nbsp; &nbsp; &nbsp; - &nbsp; &nbsp; &nbsp; -<br />
<br />
2、在/etc/rc.d/init.d/ss5 文件修改自定义端口，默认为1080<br />
daemon /usr/sbin/ss5 -t $SS5_OPTS -b 0.0.0.0:10888<br />
<br />
3、在/etc/sysconfig/ss5 中，取消注释。&nbsp;<br />
SS5_OPTS=” -u root”<br />
<br />
4、添加验证用户及密码，由于密码是明文的，注意控制权限。<br />
# cat ss5.passwd &nbsp; #一行一个用户+密码<br />
test 123<br />
lxsym 123 &nbsp;<br />
<br />
# chmod 700 /etc/rc.d/init.d/ss5<br />
# chmod/etc/rc.d/init.d/ss5<br />
<br />
[root@lx_web_s1 ss5-3.8.9]# /etc/rc.d/init.d/ss5 restart &nbsp;<br />
Restarting ss5... Shutting down ss5...&nbsp;<br />
done &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; [ &nbsp;OK &nbsp;]<br />
doneting ss5... &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;[ &nbsp;OK &nbsp;]<br />
服务端安装成功，现在就可以使用服务器的IP, 端口10888, 用户test, 密码123来测试你的socks5服务器了。<br />
<br />
最后加入开机自动启动<br />
chkconfig --add ss5<br />
chkconfig --level 345 ss5 on<br />
<br />
比如代理上QQ，当ssh跳板机，后面会介绍。它还有很多用途~~<br />