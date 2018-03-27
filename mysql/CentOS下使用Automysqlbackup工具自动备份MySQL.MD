<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	本来看到旧版的server administration可以自动备份的，想着workbench应该也可以……没想到竟然不行，而且mysql只是考虑将这个功能加到community plugin中。忧桑……还好有人写了个AutoMySQLBackup共享在了sourceforge上。试试看怎么样吧。
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	人家在sourceforge上的介绍：
</p>
<h2 style="margin:0px;padding:0px;line-height:1.5;font-size:21px;font-family:verdana, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
	Description
</h2>
<p id="description" style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	AutoMySQLBackup with a basic configuration will create Daily, Weekly and Monthly backups of one or more of your MySQL databases from one or more of your MySQL servers.<br style="margin:0px;padding:0px;" />
<br style="margin:0px;padding:0px;" />
Other Features include:<br style="margin:0px;padding:0px;" />
- Email notification of backups （会有email通知）<br style="margin:0px;padding:0px;" />
- Backup Compression and Encryption （使用压缩和加密）<br style="margin:0px;padding:0px;" />
- Configurable backup rotation （保存的备份文件时间）<br style="margin:0px;padding:0px;" />
- Incremental database backups （增量型备份）
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<strong style="margin:0px;padding:0px;">1.下载AutoMySQLBackup</strong>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	http://sourceforge.net/projects/automysqlbackup/
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<strong style="margin:0px;padding:0px;">2.解压缩</strong>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	把下载的automysqlbackup-v3.0_rc6.tar.gz文件拷贝到/usr/tmp下面
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	在/usr/local下面新建一个automysqlbackup文件夹，并进入这个文件夹
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">cd /usr/local</span>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">mkdir automysqlbackup</span>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">cd&nbsp;<span style="margin:0px;padding:0px;line-height:1.8;">automysqlbackup</span></span>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	然后terminal解压缩一下。
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">tar -xzvf /usr/tmp/automysqlbackup-v3.0_rc6.tar.gz<br style="margin:0px;padding:0px;" />
</span>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<strong style="margin:0px;padding:0px;">3. 安装</strong>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	安装一下，命令为
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">./install.sh</span>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	中途会有两个询问配置文件安装目录的地方，之间回车就好
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<img src="http://images.cnitblog.com/blog/189953/201303/19164551-d4cce90a0b744c46b469d3f0182c98cd.jpg" alt="" style="margin:0px;padding:0px;max-width:900px;" />
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	安装完以后会有提示信息，告诉你如果不是当前用户下使用这个命令要怎么办：
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<img src="http://images.cnitblog.com/blog/189953/201303/19164634-e09817a20d394d148eeb3dd8362550f3.jpg" alt="" style="margin:0px;padding:0px;max-width:900px;" />
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	我们先到/etc/automysqlbackup下面看看有什么东西好了
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<img src="http://images.cnitblog.com/blog/189953/201303/19170858-1965fc4dfcfa4337a1f2d967eb365a12.jpg" alt="" style="margin:0px;padding:0px;max-width:900px;" />
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	目测有四个文件……
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<strong style="margin:0px;padding:0px;">4.修改配置文件</strong>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	我们要用到的是automysqlbackup.conf文件：
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	文件里有一些基本的配置信息，比如连接mysql server的用户名、密码、IP地址神马的。
</p>
<div class="cnblogs_code" style="margin:5px 0px;padding:5px;background-color:#F5F5F5;border:1px solid #CCCCCC;overflow:auto;white-space:normal;font-family:&quot;">
	<div class="cnblogs_code_toolbar" style="margin:5px 0px 0px;padding:0px;">
		<span class="cnblogs_code_copy" style="margin:0px;padding:0px 5px 0px 0px;line-height:1.8;"><a title="复制代码" style="margin:0px;padding:0px;border:none !important;"><img src="http://common.cnblogs.com/images/copycode.gif" alt="复制代码" style="margin:0px;padding:0px;max-width:900px;border-width:initial !important;border-style:none !important;" /></a></span>
	</div>
<pre style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;"><span style="margin:0px;padding:0px;line-height:1.8;"># Username to access the MySQL server e.g. dbuser
CONFIG_mysql_dump_username</span>=<span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">'</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">root</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">'</span><span style="margin:0px;padding:0px;line-height:1.8;"> # Password to access the MySQL server e.g. password
CONFIG_mysql_dump_password</span>=<span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">'</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">1234</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">'</span><span style="margin:0px;padding:0px;line-height:1.8;"> # Host name (or IP address) of MySQL server e.g localhost
CONFIG_mysql_dump_host</span>=<span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">'</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">localhost</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">'</span></pre>
	<div class="cnblogs_code_toolbar" style="margin:5px 0px 0px;padding:0px;">
		<span class="cnblogs_code_copy" style="margin:0px;padding:0px 5px 0px 0px;line-height:1.8;"><a title="复制代码" style="margin:0px;padding:0px;border:none !important;"><img src="http://common.cnblogs.com/images/copycode.gif" alt="复制代码" style="margin:0px;padding:0px;max-width:900px;border-width:initial !important;border-style:none !important;" /></a></span>
	</div>
</div>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	继续，有个重要的配置，就是<strong style="margin:0px;padding:0px;"><span style="margin:0px;padding:0px;line-height:1.8;color:#FF0000;">backup存放的地方</span></strong>咯！
</p>
<div class="cnblogs_code" style="margin:5px 0px;padding:5px;background-color:#F5F5F5;border:1px solid #CCCCCC;overflow:auto;white-space:normal;font-family:&quot;">
<pre style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;"># Backup directory location e.g /<span style="margin:0px;padding:0px;line-height:1.8;">backups
CONFIG_backup_dir</span>=<span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">'</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">/var/backup/db</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">'</span></pre>
</div>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	往下看，还有你要配置的database的名称，当然可以精确到表名，也可以只指定到database的名称。或者干脆直接留空，不过留空的话会默认备份所有的数据库……这样磁盘可能会爆炸吧……
</p>
<div class="cnblogs_code" style="margin:5px 0px;padding:5px;background-color:#F5F5F5;border:1px solid #CCCCCC;overflow:auto;white-space:normal;font-family:&quot;">
	<div class="cnblogs_code_toolbar" style="margin:5px 0px 0px;padding:0px;">
		<span class="cnblogs_code_copy" style="margin:0px;padding:0px 5px 0px 0px;line-height:1.8;"><a title="复制代码" style="margin:0px;padding:0px;border:none !important;"><img src="http://common.cnblogs.com/images/copycode.gif" alt="复制代码" style="margin:0px;padding:0px;max-width:900px;border-width:initial !important;border-style:none !important;" /></a></span>
	</div>
<pre style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;"><span style="margin:0px;padding:0px;line-height:1.8;"># Databases to backup

# List of databases </span><span style="margin:0px;padding:0px;line-height:1.8;color:#0000FF;">for</span> Daily/Weekly Backup e.g. ( <span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">'</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">DB1</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">'</span> <span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">'</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">DB2</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">'</span> <span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">'</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">DB3</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">'</span><span style="margin:0px;padding:0px;line-height:1.8;"> ... )
# set to (), i.e. empty, </span><span style="margin:0px;padding:0px;line-height:1.8;color:#0000FF;">if</span><span style="margin:0px;padding:0px;line-height:1.8;"> you want to backup all databases
CONFIG_db_names</span>=<span style="margin:0px;padding:0px;line-height:1.8;">()
# You can use
#declare </span>-a MDBNAMES=( <span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">"</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">${DBNAMES[@]}</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">"</span> <span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">'</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">added entry1</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">'</span> <span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">'</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">added entry2</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">'</span><span style="margin:0px;padding:0px;line-height:1.8;"> ... )
# INSTEAD to copy the contents of $DBNAMES and add further entries (optional).

# List of databases </span><span style="margin:0px;padding:0px;line-height:1.8;color:#0000FF;">for</span><span style="margin:0px;padding:0px;line-height:1.8;"> Monthly Backups.
# set to (), i.e. empty, </span><span style="margin:0px;padding:0px;line-height:1.8;color:#0000FF;">if</span><span style="margin:0px;padding:0px;line-height:1.8;"> you want to backup all databases
CONFIG_db_month_names</span>=<span style="margin:0px;padding:0px;line-height:1.8;">()

# List of DBNAMES to EXLUCDE </span><span style="margin:0px;padding:0px;line-height:1.8;color:#0000FF;">if</span><span style="margin:0px;padding:0px;line-height:1.8;"> DBNAMES is empty, i.e. ().
CONFIG_db_exclude</span>=( <span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">'</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">information_schema</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">'</span> <span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">'</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">wiqun</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">'</span> )</pre>
	<div class="cnblogs_code_toolbar" style="margin:5px 0px 0px;padding:0px;">
		<span class="cnblogs_code_copy" style="margin:0px;padding:0px 5px 0px 0px;line-height:1.8;"><a title="复制代码" style="margin:0px;padding:0px;border:none !important;"><img src="http://common.cnblogs.com/images/copycode.gif" alt="复制代码" style="margin:0px;padding:0px;max-width:900px;border-width:initial !important;border-style:none !important;" /></a></span>
	</div>
</div>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	另外，还有配置weekly、monthly、daily之类的时间间隔的设置
</p>
<div class="cnblogs_code" style="margin:5px 0px;padding:5px;background-color:#F5F5F5;border:1px solid #CCCCCC;overflow:auto;white-space:normal;font-family:&quot;">
	<div class="cnblogs_code_toolbar" style="margin:5px 0px 0px;padding:0px;">
		<span class="cnblogs_code_copy" style="margin:0px;padding:0px 5px 0px 0px;line-height:1.8;"><a title="复制代码" style="margin:0px;padding:0px;border:none !important;"><img src="http://common.cnblogs.com/images/copycode.gif" alt="复制代码" style="margin:0px;padding:0px;max-width:900px;border-width:initial !important;border-style:none !important;" /></a></span>
	</div>
<pre style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;"><span style="margin:0px;padding:0px;line-height:1.8;"># Rotation Settings

# Which day </span><span style="margin:0px;padding:0px;line-height:1.8;color:#0000FF;">do</span> you want monthly backups? (<span style="margin:0px;padding:0px;line-height:1.8;color:#800080;">01</span> to <span style="margin:0px;padding:0px;line-height:1.8;color:#800080;">31</span><span style="margin:0px;padding:0px;line-height:1.8;">)
# If the chosen day is greater than the </span><span style="margin:0px;padding:0px;line-height:1.8;color:#0000FF;">last</span> day of the month, it will be <span style="margin:0px;padding:0px;line-height:1.8;color:#0000FF;">done</span><span style="margin:0px;padding:0px;line-height:1.8;"> # on the </span><span style="margin:0px;padding:0px;line-height:1.8;color:#0000FF;">last</span><span style="margin:0px;padding:0px;line-height:1.8;"> day of the month.
# Set to </span><span style="margin:0px;padding:0px;line-height:1.8;color:#800080;">0</span><span style="margin:0px;padding:0px;line-height:1.8;"> to disable monthly backups.
CONFIG_do_monthly</span>=<span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">"</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">22</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">"</span><span style="margin:0px;padding:0px;line-height:1.8;"> # Which day </span><span style="margin:0px;padding:0px;line-height:1.8;color:#0000FF;">do</span> you want weekly backups? (<span style="margin:0px;padding:0px;line-height:1.8;color:#800080;">1</span> to <span style="margin:0px;padding:0px;line-height:1.8;color:#800080;">7</span> where <span style="margin:0px;padding:0px;line-height:1.8;color:#800080;">1</span><span style="margin:0px;padding:0px;line-height:1.8;"> is Monday)
# Set to </span><span style="margin:0px;padding:0px;line-height:1.8;color:#800080;">0</span><span style="margin:0px;padding:0px;line-height:1.8;"> to disable weekly backups.
CONFIG_do_weekly</span>=<span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">"</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">7</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">"</span><span style="margin:0px;padding:0px;line-height:1.8;"> # Set rotation of daily backups. VALUE</span>*<span style="margin:0px;padding:0px;line-height:1.8;">24hours
# If you want to keep only today</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">'</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">s backups, you could choose 1, i.e. everything older than 24hours will be removed.</span> CONFIG_rotation_daily=<span style="margin:0px;padding:0px;line-height:1.8;color:#800080;">7</span><span style="margin:0px;padding:0px;line-height:1.8;"> # Set rotation </span><span style="margin:0px;padding:0px;line-height:1.8;color:#0000FF;">for</span> weekly backups. VALUE*<span style="margin:0px;padding:0px;line-height:1.8;">24hours
CONFIG_rotation_weekly</span>=<span style="margin:0px;padding:0px;line-height:1.8;color:#800080;">35</span><span style="margin:0px;padding:0px;line-height:1.8;"> # Set rotation </span><span style="margin:0px;padding:0px;line-height:1.8;color:#0000FF;">for</span> monthly backups. VALUE*<span style="margin:0px;padding:0px;line-height:1.8;">24hours
CONFIG_rotation_monthly</span>=<span style="margin:0px;padding:0px;line-height:1.8;color:#800080;">150</span></pre>
	<div class="cnblogs_code_toolbar" style="margin:5px 0px 0px;padding:0px;">
		<span class="cnblogs_code_copy" style="margin:0px;padding:0px 5px 0px 0px;line-height:1.8;"><a title="复制代码" style="margin:0px;padding:0px;border:none !important;"><img src="http://common.cnblogs.com/images/copycode.gif" alt="复制代码" style="margin:0px;padding:0px;max-width:900px;border-width:initial !important;border-style:none !important;" /></a></span>
	</div>
</div>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	前两个都比较好理解，就是每个月或者每一周的什么时候进行自动备份，如果不想使用每周备份或者每月备份的话，相应的地方设置0即可。那么后面的rotation又是什么意思呢？其实就是日志保存的期限啦。
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	比如说CONFIG_rotation_weekly=35的意思就是说按周存储的备份最多保留35天。
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	再继续，可以配置发送邮件的一些配置，比如邮件地址啦、还有附件的内容啦。
</p>
<div class="cnblogs_code" style="margin:5px 0px;padding:5px;background-color:#F5F5F5;border:1px solid #CCCCCC;overflow:auto;white-space:normal;font-family:&quot;">
	<div class="cnblogs_code_toolbar" style="margin:5px 0px 0px;padding:0px;">
		<span class="cnblogs_code_copy" style="margin:0px;padding:0px 5px 0px 0px;line-height:1.8;"><a title="复制代码" style="margin:0px;padding:0px;border:none !important;"><img src="http://common.cnblogs.com/images/copycode.gif" alt="复制代码" style="margin:0px;padding:0px;max-width:900px;border-width:initial !important;border-style:none !important;" /></a></span>
	</div>
<pre style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;"># What would you like to be mailed to you?<span style="margin:0px;padding:0px;line-height:1.8;"> # </span>- log   : send only log <span style="margin:0px;padding:0px;line-height:1.8;color:#0000FF;">file</span><span style="margin:0px;padding:0px;line-height:1.8;"> # </span>- files : send log <span style="margin:0px;padding:0px;line-height:1.8;color:#0000FF;">file</span><span style="margin:0px;padding:0px;line-height:1.8;"> and sql files as attachments (see docs)
# </span>- stdout : will simply output the log to the screen <span style="margin:0px;padding:0px;line-height:1.8;color:#0000FF;">if</span><span style="margin:0px;padding:0px;line-height:1.8;"> run manually.
# </span>- quiet : Only send logs <span style="margin:0px;padding:0px;line-height:1.8;color:#0000FF;">if</span><span style="margin:0px;padding:0px;line-height:1.8;"> an error occurs to the MAILADDR.
CONFIG_mailcontent</span>=<span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">'</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">files</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">'</span><span style="margin:0px;padding:0px;line-height:1.8;"> # Set the maximum allowed email size </span><span style="margin:0px;padding:0px;line-height:1.8;color:#0000FF;">in</span> k. (<span style="margin:0px;padding:0px;line-height:1.8;color:#800080;">4000</span> =<span style="margin:0px;padding:0px;line-height:1.8;"> approx 5MB email [see docs])
CONFIG_mail_maxattsize</span>=<span style="margin:0px;padding:0px;line-height:1.8;color:#800080;">4000</span><span style="margin:0px;padding:0px;line-height:1.8;"> # Allow packing of files with </span><span style="margin:0px;padding:0px;line-height:1.8;color:#0000FF;">tar</span> and splitting it <span style="margin:0px;padding:0px;line-height:1.8;color:#0000FF;">in</span><span style="margin:0px;padding:0px;line-height:1.8;"> pieces of CONFIG_mail_maxattsize.
CONFIG_mail_splitandtar</span>=<span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">'</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">yes</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">'</span><span style="margin:0px;padding:0px;line-height:1.8;"> # Use uuencode instead of mutt. WARNING: Not all email clients work well with uuencoded attachments.
#CONFIG_mail_use_uuencoded_attachments</span>=<span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">'</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">no</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">'</span><span style="margin:0px;padding:0px;line-height:1.8;"> # Email Address to send mail to</span>?<span style="margin:0px;padding:0px;line-height:1.8;"> (user@domain.com)
CONFIG_mail_address</span>=<span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">'</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">elarwei@gmail.com</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">'</span></pre>
	<div class="cnblogs_code_toolbar" style="margin:5px 0px 0px;padding:0px;">
		<span class="cnblogs_code_copy" style="margin:0px;padding:0px 5px 0px 0px;line-height:1.8;"><a title="复制代码" style="margin:0px;padding:0px;border:none !important;"><img src="http://common.cnblogs.com/images/copycode.gif" alt="复制代码" style="margin:0px;padding:0px;max-width:900px;border-width:initial !important;border-style:none !important;" /></a></span>
	</div>
</div>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<strong style="margin:0px;padding:0px;">5. 运行Automysqlbackup<br style="margin:0px;padding:0px;" />
</strong>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	要运行automysqlbackup之前呢，不要忘了先新建我们存放备份数据库文件的地方，即在配置文件中设定的“<span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">/var/backup/db</span>”，现在我们来新建这个目录。
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">mkdir /var/backup</span>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">mkdir /var/backup/db</span>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;line-height:1.8;color:#000000;">好了，现在我们可以run一下automysqlbackup了。命令是：</span>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">automysqlbackup /etc/automyslqbackup/automysqlbackup.conf</span>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;line-height:1.8;color:#000000;">噔噔，怎么报错了呢？</span>
</p>
<div class="cnblogs_code" style="margin:5px 0px;padding:5px;background-color:#F5F5F5;border:1px solid #CCCCCC;overflow:auto;white-space:normal;font-family:&quot;">
	<div class="cnblogs_code_toolbar" style="margin:5px 0px 0px;padding:0px;">
		<span class="cnblogs_code_copy" style="margin:0px;padding:0px 5px 0px 0px;line-height:1.8;"><a title="复制代码" style="margin:0px;padding:0px;border:none !important;"><img src="http://common.cnblogs.com/images/copycode.gif" alt="复制代码" style="margin:0px;padding:0px;max-width:900px;border-width:initial !important;border-style:none !important;" /></a></span>
	</div>
<pre style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">Parsed config <span style="margin:0px;padding:0px;line-height:1.8;color:#0000FF;">file</span> <span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">"</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">/etc/automysqlbackup/automysqlbackup.conf</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">"</span><span style="margin:0px;padding:0px;line-height:1.8;"> # Checking </span><span style="margin:0px;padding:0px;line-height:1.8;color:#0000FF;">for</span> permissions to <span style="margin:0px;padding:0px;line-height:1.8;color:#0000FF;">write</span><span style="margin:0px;padding:0px;line-height:1.8;"> to folders:
base folder </span>/var/<span style="margin:0px;padding:0px;line-height:1.8;">backup ... exists ... ok.
backup folder </span>/var/backup/db ... exists ... writable?<span style="margin:0px;padding:0px;line-height:1.8;"> yes. Proceeding. </span>/usr/local/bin/automysqlbackup: line <span style="margin:0px;padding:0px;line-height:1.8;color:#800080;">139</span>: mutt: command not found</pre>
	<div class="cnblogs_code_toolbar" style="margin:5px 0px 0px;padding:0px;">
		<span class="cnblogs_code_copy" style="margin:0px;padding:0px 5px 0px 0px;line-height:1.8;"><a title="复制代码" style="margin:0px;padding:0px;border:none !important;"><img src="http://common.cnblogs.com/images/copycode.gif" alt="复制代码" style="margin:0px;padding:0px;max-width:900px;border-width:initial !important;border-style:none !important;" /></a></span>
	</div>
</div>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	好吧，有事问Google。
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	sourceForge上果然也有人遇到过这个问题……，解答是
</p>
<div class="cnblogs_code" style="margin:5px 0px;padding:5px;background-color:#F5F5F5;border:1px solid #CCCCCC;overflow:auto;white-space:normal;font-family:&quot;">
<pre style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">Please set CONFIG_mailcontent=<span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">'</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">stdout</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">'</span> <span style="margin:0px;padding:0px;line-height:1.8;color:#0000FF;">in</span> your config <span style="margin:0px;padding:0px;line-height:1.8;color:#0000FF;">file</span> and try again from your console.
 The output should directly be displayed. 
It seems some error occured before the check <span style="margin:0px;padding:0px;line-height:1.8;color:#0000FF;">for</span> config variables could determine 
whether there is a need <span style="margin:0px;padding:0px;line-height:1.8;color:#0000FF;">for</span> checking <span style="margin:0px;padding:0px;line-height:1.8;color:#0000FF;">if</span> mutt (mail program) is installed and can be used. 
Therefore the error handler tried to mail the errors using mutt (your configuration choice), <span style="margin:0px;padding:0px;line-height:1.8;color:#0000FF;">which</span> isn<span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">'</span><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">t there.</span></pre>
</div>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	大 意就是说在配置文件里面使用了发送email来报告error这个东东，但是你的机子上却没安装mutt这个程序，所以在检测配置的时候就发生了错误。解 决的方法是把报错改成“stdout”，不过如果改成“stdout”不就失去了我们发送报告到email 的本意了吗……so，我们安装一下mutt这个程序好了。
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	（<span style="margin:0px;padding:0px;line-height:1.8;color:#FF0000;">PS：如果不使用发送邮件则不需要这个步骤</span>）
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<strong style="margin:0px;padding:0px;">5.1 安装mutt</strong>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	命令是
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">yum install mutt</span>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	安装完了以后我们再重新run一下automysqlbackup。
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	这次没有报错了。我们到/var/backup/db下面看一下有没有什么变化
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">cd /var/backup/db</span>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">ls</span>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	出现了几个文件夹哦
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<img src="http://images.cnitblog.com/blog/189953/201303/20093903-08ba04868fd043c48f78f68d6c0e87f4.jpg" alt="" style="margin:0px;padding:0px;max-width:900px;" />
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<strong style="margin:0px;padding:0px;">6. 设定Cron Job</strong>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	Cron 是一个可以让系统定时运行后台脚本的工具。
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<strong style="margin:0px;padding:0px;">6.1 编写可执行脚本</strong>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	我们在/usr/local/bin目录下编写一个要定时执行的脚本
</p>
<div class="cnblogs_code" style="margin:5px 0px;padding:5px;background-color:#F5F5F5;border:1px solid #CCCCCC;overflow:auto;white-space:normal;font-family:&quot;">
<pre style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">#!/bin/<span style="margin:0px;padding:0px;line-height:1.8;color:#0000FF;">sh</span> /usr/local/bin/automysqlbackup /etc/automysqlbackup/automysqlbackup.conf</pre>
</div>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	保存为backupscript.sh
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	然后改变其模式为root可以执行、读写的方式
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">chmod 744 /usr/local/bin/backupscript.sh</span>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<strong style="margin:0px;padding:0px;">6.2 将可执行脚本加入定时任务中</strong>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	先使用命令
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">crontab -l</span>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	看一下现在cron中的定时程序有哪些。
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	如果提示“<span style="margin:0px;padding:0px;line-height:1.8;color:#FF0000;">no crontab for root</span>”的话，说明root用户下现在还没有定时任务。我们可以新建一个文件，用来配置root用户下的定时任务。
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">vi root-conf</span>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;line-height:1.8;color:#000000;">然后在vi中输入</span>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">0-59/10 * * * * /usr/local/bin/backupscript.sh<br style="margin:0px;padding:0px;" />
</span>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;line-height:1.8;color:#000000;">意思是每十分钟执行一下备份脚本程序（比较夸张啦，为了能在短时间内看到比较多备份的结果，一般都是设定某一天的一个时刻来执行）然后保存退出。</span>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;line-height:1.8;color:#000000;">接着，使用命令</span>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">crontab -u root root-conf</span>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;line-height:1.8;color:#000000;">来将刚才编辑的文件作为root下的定时任务列表文件。这样再键入<span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">crontab -l</span>命令时，就可以查看到我们刚才设定的定时任务了。另外，使用<span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">crontab -e<span style="margin:0px;padding:0px;line-height:1.8;color:#000000;">命令可以编辑我们的定时任务。具体的设定时间的方法可以看<span class="headermaintitle" style="margin:0px;padding:0px;line-height:1.8;">Kaixuan</span>的这篇文章《<a id="cb_post_title_url" class="postTitle2" href="http://www.cnblogs.com/kaixuan/archive/2009/05/31/1492889.html" style="margin:0px;padding:0px;text-decoration:none;color:#000000;border-bottom:1px dotted #333333;">Linux下使用crontab来执行定时任务计划</a>》。</span></span></span>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<strong style="margin:0px;padding:0px;"><span style="margin:0px;padding:0px;line-height:1.8;color:#000000;">7.查看备份结果</span></strong>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;line-height:1.8;color:#000000;">我们进入备份的目录看一下有什么变化</span>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;line-height:1.8;color:#000000;"><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">cd</span>&nbsp;<span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">/var/backup/db/daily</span><br style="margin:0px;padding:0px;" />
</span>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;line-height:1.8;color:#000000;"><span style="margin:0px;padding:0px;line-height:1.8;color:#800000;">ls</span></span>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;line-height:1.8;color:#000000;">可以看到两个目录</span>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;<img src="http://images.cnitblog.com/blog/189953/201303/22170443-2fbd3b915a604a7b8005a015425e94e9.jpg" alt="" style="margin:0px;padding:0px;max-width:900px;" />
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;进入mysql
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	14:52的时候daily目录内的备份如下图：
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<img src="http://images.cnitblog.com/blog/189953/201303/22170516-a096f874b22943a0bfc57ac6dee4cff2.jpg" alt="" style="margin:0px;padding:0px;max-width:900px;" />
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	17:05的时候daily目录内的备份如下图：
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<img src="http://images.cnitblog.com/blog/189953/201303/22170544-9bf08c5b36424ac3903f1b0a3f4f14bb.jpg" alt="" style="margin:0px;padding:0px;max-width:900px;" />
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	查看邮件里面，也可以看到发送的备份email，截图如下
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<img src="http://images.cnitblog.com/blog/189953/201303/22171932-a8e82553138e455686438c5fad4084e6.jpg" alt="" style="margin:0px;padding:0px;max-width:900px;" />
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	不过gmail自动把这些邮件当成垃圾邮件了，所以如果邮箱里看不到的话找找垃圾邮件里面……
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<strong style="margin:0px;padding:0px;">Reference</strong>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<a class="contentpagetitle" href="http://www.linux.com/learn/tutorials/659107-how-to-do-painless-mysql-server-backups-with-automysqlbackup" style="margin:0px;padding:0px;text-decoration:none;color:#000000;border-bottom:1px dotted #333333;">How to do Painless MySQL Server Backups with AutoMySQLBackup</a>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<strong style="margin:0px;padding:0px;">其他的备份工具还有</strong>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<a href="http://www.cnblogs.com/cosiray/archive/2012/03/02/2376595.html" style="margin:0px;padding:0px;text-decoration:none;color:#000000;border-bottom:1px dotted #333333;">XtraBackup</a>
</p>