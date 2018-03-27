<div id="cnblogs_post_body" class="blogpost-body" style="margin:0px 0px 20px;padding:0px;word-break:break-word;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:13px;white-space:normal;background-color:#FEFEF2;">
	<p style="margin:10px auto;padding:0px;line-height:1.5;">
		1、下载并解压到：/Users/xiechunping/Softwares/mysql-5.7.17<br style="margin:0px;padding:0px;" />
下载地址：http://ftp.ntu.edu.tw/pub/MySQL/Downloads/MySQL-5.7/mysql-boost-5.7.17.tar.gz
	</p>
	<p style="margin:10px auto;padding:0px;line-height:1.5;">
		2、进入mysql-5.7.17，执行cmake<br style="margin:0px;padding:0px;" />
cd ../mysql-5.7.17<br style="margin:0px;padding:0px;" />
cmake -DCMAKE_INSTALL_PREFIX=/usr/local/mysql -DMYSQL_UNIX_ADDR=/tmp/mysql.sock -DDEFAULT_CHARSET=utf8 -DDEFAULT_COLLATION=utf8_general_ci -DWITH_INNOBASE_STORAGE_ENGINE=1-DWITH_ARCHIVE_STORAGE_ENGINE=1 -DWITH_BLACKHOLE_STORAGE_ENGINE=1 -DWITH_PARTITION_STORAGE_ENGINE=1 -DENABLED_LOCAL_INFILE=1 -DMYSQL_USER=_mysql -DMYSQL_TCP_PORT=3306 -DMYSQL_DATADIR=/usr/local/mysql/db_data -DDOWNLOAD_BOOST=1 -DWITH_BOOST=/Users/xiechunping/Softwares/mysql-5.7.17/boost
	</p>
	<p style="margin:10px auto;padding:0px;line-height:1.5;">
		3、配置数据目录权限<br style="margin:0px;padding:0px;" />
chown -R _mysql:_mysql /usr/local/mysql/db_data
	</p>
	<p style="margin:10px auto;padding:0px;line-height:1.5;">
		4、编译并安装<br style="margin:0px;padding:0px;" />
make&amp;&amp;make install
	</p>
	<p style="margin:10px auto;padding:0px;line-height:1.5;">
		5、安装数据库并启动<br style="margin:0px;padding:0px;" />
cd /usr/local/mysql<br style="margin:0px;padding:0px;" />
bin/mysql_install_db --user=mysql --datadir=/usr/local/mysql/db_data<br style="margin:0px;padding:0px;" />
support-files/mysql.server start
	</p>
	<p style="margin:10px auto;padding:0px;line-height:1.5;">
		6、修改数据库root用户密码（首次进入密码为空）<br style="margin:0px;padding:0px;" />
修改：/usr/local/mysql/support-files/mysql.server第280行<br style="margin:0px;padding:0px;" />
为mysql的启动选项增加：--user=mysql --skip-grant-tables --skip-networking<br style="margin:0px;padding:0px;" />
执行：<br style="margin:0px;padding:0px;" />
support-files/mysql.server stop &amp;&amp; support-files/mysql.server stop<br style="margin:0px;padding:0px;" />
bin/mysql -u root mysql<br style="margin:0px;padding:0px;" />
mysql&gt;UPDATE user SET authentication_string=PASSWORD('mysql54321') where USER='root';<br style="margin:0px;padding:0px;" />
mysql&gt;FLUSH PRIVILEGES;<br style="margin:0px;padding:0px;" />
mysql&gt;quit;
	</p>
	<p style="margin:10px auto;padding:0px;line-height:1.5;">
		support-files/mysql.server stop<br style="margin:0px;padding:0px;" />
还原/usr/local/mysql/support-files/mysql.server文件<br style="margin:0px;padding:0px;" />
support-files/mysql.server start
	</p>
	<p style="margin:10px auto;padding:0px;line-height:1.5;">
		bin/mysql -uroot -p<br style="margin:0px;padding:0px;" />
Enter password: &lt;输入新设的密码mysql54321&gt;<br style="margin:0px;padding:0px;" />
mysql&gt;SET PASSWORD = PASSWORD('mysql54321');<br style="margin:0px;padding:0px;" />
mysql&gt;ALTER USER 'root'@'localhost' PASSWORD EXPIRE NEVER;<br style="margin:0px;padding:0px;" />
mysql&gt;flush privileges;<br style="margin:0px;padding:0px;" />
mysql&gt;quit;&nbsp;
	</p>
	<div>
		<br />
	</div>
</div>
<div id="MySignature" style="margin:0px;padding:0px;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:13px;white-space:normal;background-color:#FEFEF2;">
</div>