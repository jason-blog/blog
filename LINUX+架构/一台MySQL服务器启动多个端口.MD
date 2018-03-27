<p class="p0" style="margin-top:0pt;margin-bottom:0pt;padding:0px;white-space:normal;">
	详细步骤：
</p>
<p class="p0" style="margin-top:0pt;margin-bottom:0pt;padding:0px;white-space:normal;">
	<br />
</p>
<p class="p0" style="margin-top:0pt;margin-bottom:0pt;padding:0px;white-space:normal;">
	1、首先要先把my.cnf配置文件复制一份，开几个端口要复制几份当然要重新命名.
</p>
<p class="p0" style="margin-top:0pt;margin-bottom:0pt;padding:0px;white-space:normal;">
	如：
</p>
<p class="p0" style="margin-top:0pt;margin-bottom:0pt;padding:0px;white-space:normal;">
	<br />
</p>
<p class="p0" style="margin-top:0pt;margin-bottom:0pt;padding:0px;white-space:normal;">
<pre class="prettyprint lang-js linenums">cp /etc/my.cnf /etc/my3306.cnf

cp /etc/my.cnf /etc/my3307.cnf

cp /etc/my.cnf /etc/my3308.cnf</pre>
</p>
<br style="word-wrap:break-word;white-space:normal;" />
<p class="p0" style="margin-top:0pt;margin-bottom:0pt;padding:0px;white-space:normal;">
	2、修改my_1.cnf&nbsp;my_2.cnf&nbsp;my_3.cnf文件把默认的3306端口改成&nbsp;3307&nbsp;3308&nbsp;3309.
</p>
<p class="p0" style="margin-top:0pt;margin-bottom:0pt;padding:0px;white-space:normal;">
	如：
</p>
<p class="p0" style="margin-top:0pt;margin-bottom:0pt;padding:0px;white-space:normal;">
	<br />
</p>
<p class="p0" style="margin-top:0pt;margin-bottom:0pt;padding:0px;white-space:normal;">
<pre class="prettyprint lang-js linenums">[client]

port = 3308

socket = /tmp/mysql3308.sock

default-character-set=UTF

[mysqld]

port = 3308

socket = /tmp/mysql3308.sock

basedir=/usr/local/mysql

datadir=/www/mysqldata8</pre>
</p>
<p class="p0" style="margin-top:0pt;margin-bottom:0pt;padding:0px;white-space:normal;">
	<br />
</p>
<p class="p0" style="margin-top:0pt;margin-bottom:0pt;padding:0px;white-space:normal;">
	3、创建数据库指定存放数据的目录
</p>
<p class="p0" style="margin-top:0pt;margin-bottom:0pt;padding:0px;white-space:normal;">
	<br />
</p>
<p class="p0" style="margin-top:0pt;margin-bottom:0pt;padding:0px;white-space:normal;">
<pre class="prettyprint lang-js linenums">mkdir /www/mysqldata3306

mkdir /www/mysqldata3307

mkdir /www/mysqldata3308</pre>
</p>
<br style="word-wrap:break-word;white-space:normal;" />
<p class="p0" style="margin-top:0pt;margin-bottom:0pt;padding:0px;white-space:normal;">
	4、初始化数据库
</p>
<p class="p0" style="margin-top:0pt;margin-bottom:0pt;padding:0px;white-space:normal;">
	<br />
</p>
<p class="p0" style="margin-top:0pt;margin-bottom:0pt;padding:0px;white-space:normal;">
<pre class="prettyprint lang-js linenums">/usr/local/mysql/scripts/mysql_install_db --datadir=/www/mysqldata3306/ --user=mysql --basedir=/usr/local/mysql

/usr/local/mysql/scripts/mysql_install_db --datadir=/www/mysqldata3307/ --user=mysql --basedir=/usr/local/mysql

/usr/local/mysql/scripts/mysql_install_db --datadir=/www/mysqldata3308/ --user=mysql --basedir=/usr/local/mysql</pre>
</p>
<br style="word-wrap:break-word;white-space:normal;" />
<p class="p0" style="margin-top:0pt;margin-bottom:0pt;padding:0px;white-space:normal;">
	5、启动mysql，要指定.cnf文件和目录启动
</p>
<p class="p0" style="margin-top:0pt;margin-bottom:0pt;padding:0px;white-space:normal;">
	<br />
</p>
<p class="p0" style="margin-top:0pt;margin-bottom:0pt;padding:0px;white-space:normal;">
<pre class="prettyprint lang-js linenums">/usr/local/mysql/bin/mysqld_safe --defaults-extra-file=/etc/my3306.cnf --datadir=/www/mysqldata3306 --user=mysql &amp;

/usr/local/mysql/bin/mysqld_safe --defaults-extra-file=/etc/my3307.cnf --datadir=/www/mysqldata3307 --user=mysql &amp;

/usr/local/mysql/bin/mysqld_safe --defaults-extra-file=/etc/my3308.cnf --datadir=/www/mysqldata3308 --user=mysql &amp;</pre>
</p>
<p class="p0" style="margin-top:0pt;margin-bottom:0pt;padding:0px;white-space:normal;">
	<br />
</p>
<p class="p0" style="margin-top:0pt;margin-bottom:0pt;padding:0px;white-space:normal;">
	<a href="http://blog.chinaunix.net/attachment/201208/21/25266990_13455270887MnW.png" target="_blank" style="word-wrap:break-word;"><img src="http://blog.chinaunix.net/attachment/201208/21/25266990_13455270887MnW.png" ;="" border="0" height="51" width="554" style="word-wrap: break-word;"></a> 
</p>
<p class="p0" style="margin-top:0pt;margin-bottom:0pt;padding:0px;white-space:normal;">
	6、停止MYSQL，对应的sock文件。
</p>
<p class="p0" style="margin-top:0pt;margin-bottom:0pt;padding:0px;white-space:normal;">
	<br />
</p>
<p class="p0" style="margin-top:0pt;margin-bottom:0pt;padding:0px;white-space:normal;">
<pre class="prettyprint lang-js linenums">/usr/local/mysql/bin/mysqladmin -uroot -S /tmp/mysql3308.sock shutdown</pre>
</p>
<br style="word-wrap:break-word;white-space:normal;" />
<p class="p0" style="margin-top:0pt;margin-bottom:0pt;padding:0px;white-space:normal;">
	<br />
</p>
<p class="p0" style="margin-top:0pt;margin-bottom:0pt;padding:0px;white-space:normal;">
	<br />
</p>
<p class="p0" style="margin-top:0pt;margin-bottom:0pt;padding:0px;white-space:normal;">
	7、登陆mysql
</p>
<p class="p0" style="margin-top:0pt;margin-bottom:0pt;padding:0px;white-space:normal;">
	<br />
</p>
<p class="p0" style="margin-top:0pt;margin-bottom:0pt;padding:0px;white-space:normal;">
<pre class="prettyprint lang-js linenums">mysql -S /tmp/mysq3308.sock -P 3308</pre>
</p>