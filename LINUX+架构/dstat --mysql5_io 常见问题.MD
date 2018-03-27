<p style="margin:10px auto;white-space:normal;padding:0px;">
	使用dstat竟然还可以查看mysql的状态， man dstat之后发现的，原来在/usr/share/dstat目录下藏有很多python脚本作为插件帮助dstat搜集各类信息。<br />
<br />
不过通常有可能会<br />
<br />
如果你执行dstat --mysql5_io 出现了<br />
<br />
1<br />
Module dstat_mysql5_io failed to load. (No module named MySQLdb)<br />
那么你可能需要安装python-mysqldb来使用python driver连接mysql.<br />
<br />
安装方法： sudo apt-get install python-mysqldb， 或者pip install<br />
<br />
如果依然出现问题，那可以尝试使用自己编写的python脚本来查看失败的详细原因：<br />
<br />
1<br />
2<br />
import MySQLdb<br />
MySQLdb.connect(user=mysql_user, passwd=mysql_pwd)<br />
比如我这里出现了：<br />
<br />
_mysql_exceptions.OperationalError: (2002, "Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock'<br />
<br />
这是由于我的mysql已经启动且安装 配置都是自定义的，因此需要查看下连接sock地址， 可以使用如下命令查看<br />
<br />
lsof -p PIDofMySql<br />
<br />
打开/usr/share/dstat目录下的dstat_mysql5_io.py<br />
<br />
根据lsof结果修改以上代码为：！important<br />
<br />
1<br />
self.db = MySQLdb.connect(user=mysql_user, passwd=mysql_pwd,db="redmine", unix_socket="/opt/mysql/tmp/mysql.sock")<br />
上述socket地址根据你自己的情况定义。<br />
<br />
&nbsp;<br />
<br />
创建脚本，自动运行<br />
<br />
1<br />
2<br />
3<br />
4<br />
5<br />
6<br />
#!/bin/bash<br />
&nbsp;<br />
export DSTAT_MYSQL_USER='root'<br />
export DSTAT_MYSQL_PWD='111111'<br />
&nbsp;<br />
dstat --mysql5-io $@<br />
<br />
</p>