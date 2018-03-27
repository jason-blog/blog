<p>
	http://blog.csdn.net/thundermeng/article/details/51097832
</p>
<p>
	<br />
</p>
<p>
	<h1 style="margin:0px;padding:0px;color:#555555;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		1&nbsp;&nbsp;Incption概述
	</h1>
	<h2 style="margin:0px;padding:0px;color:#555555;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		<a name="t1"></a>1.1&nbsp; Inception简介
	</h2>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		<span style="background:#FCFCFC;">Inception</span><span style="background:#FCFCFC;">是集审核、执行、回滚于一体的一个自动化运维系统</span><span style="background:#FCFCFC;">，</span><span style="background:#FCFCFC;">它可以对提交的所有语句的语法分析，如果语法有问题，都会将相应的错误信息返回给审核者。</span><span style="color:#404040;background:#FCFCFC;">&nbsp;</span><span style="background:#FCFCFC;">还提供</span><span style="background:#FCFCFC;">SQL</span><span style="background:#FCFCFC;">语句的执行功能，可执行的语句类型包括常用的</span><span style="background:#FCFCFC;">DML</span><span style="background:#FCFCFC;">及</span><span style="background:#FCFCFC;">DDL</span><span style="background:#FCFCFC;">语句及</span><span style="background:#FCFCFC;">truncate table</span><span style="background:#FCFCFC;">等操作。</span><span style="background:#FCFCFC;">&nbsp;Inception</span><span style="background:#FCFCFC;">在执行</span><span style="background:#FCFCFC;">DML</span><span style="background:#FCFCFC;">时还提供生成回滚语句的功能，对应的操作记录及回滚语句会被存储在备份机器上面，备份机器通过配置</span><span style="background:#FCFCFC;">Inception</span><span style="background:#FCFCFC;">参数来指定</span><span style="background:#FCFCFC;">。</span>
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		<span style="background:#FCFCFC;">源码地址：</span><span style="background:#FCFCFC;">https://github.com/mysql-inception/inception</span>
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		<span style="background:#FCFCFC;">文档地址：</span><span style="background:#FCFCFC;">http://mysql-inception.github.io/inception-document/</span>
	</p>
	<h1 style="margin:0px;padding:0px;color:#555555;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		<a name="t2"></a>2&nbsp;&nbsp;Incption安装
	</h1>
	<h2 style="margin:0px;padding:0px;color:#555555;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		<a name="t3"></a>2.1&nbsp; 下载源码包
	</h2>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		<a target="_blank" href="https://github.com/mysql-inception/inception" style="text-decoration-line:none;color:#0C89CF;">https://github.com/mysql-inception/inception</a>
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		download zip
	</p>
	<h2 style="margin:0px;padding:0px;color:#555555;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		<a name="t4"></a>2.2&nbsp; 安装编译时的依赖
	</h2>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		yum install gcc gcc-c++ cmake bison openssl-devel ncurses-devel –y
	</p>
	<h2 style="margin:0px;padding:0px;color:#555555;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		<a name="t5"></a>2.3&nbsp; 开始安装
	</h2>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		unzip inception-master.zip
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		cd inception-master
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		./inception_build.sh debug [Xcode]
	</p>
	<h2 style="margin:0px;padding:0px;color:#555555;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		<a name="t6"></a>2.4&nbsp; 编辑配置文件
	</h2>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		vim /etc/inc.cnf
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		[inception]
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		general_log=1
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		general_log_file=inc.log
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		port=6669
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		socket=/tmp/inc.socket
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		character-set-client-handshake=0
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		character-set-server=utf8
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		inception_remote_system_password=thunder
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		inception_remote_system_user=thunder
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		inception_remote_backup_port=3306
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		inception_remote_backup_host=127.0.0.1
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		inception_support_charset=utf8
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		inception_enable_nullable=0
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		inception_check_primary_key=1
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		inception_check_column_comment=1
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		inception_check_table_comment=1
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		inception_osc_min_table_size=1
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		inception_osc_bin_dir=/usr/bin
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		inception_osc_chunk_time=0.1
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		inception_ddl_support=1
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		inception_enable_blob_type=1
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		inception_check_column_default_value=1
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		&nbsp;
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		#相关配置说明请参见官方文档，在概述中已给出地址
	</p>
	<h2 style="margin:0px;padding:0px;color:#555555;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		<a name="t7"></a>2.5&nbsp; 启动Inception服务，类似mysql启动方式
	</h2>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		/opt/thunder/inception-master/debug/mysql/bin/Inception --defaults-file=/etc/inc.cnf &amp;
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		登陆测试，可通过sock或者端口，上面配置文件中配置的端口为6669
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		mysql –h127.0.0.1 –P6669 –uroot
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		mysql&gt; inception get variables;
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		输出相关变量则安装成功
	</p>
	<h2 style="margin:0px;padding:0px;color:#555555;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		<a name="t8"></a>2.6&nbsp; 用脚本测试相关审核语句
	</h2>
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">#!/usr/bin/python&nbsp;</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">import MySQLdb&nbsp;</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">sql='/*--user=thunder;--password=thunder;--host=127.0.0.1;--enable-remote-backup=0;--execute;--port=3306;*/\&nbsp;</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">inception_magic_start;\&nbsp;</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">use test;\&nbsp;</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">CREATE TABLE `alifeba_user` (\&nbsp;</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">&nbsp; &nbsp; &nbsp;`ID` int(11) unsigned NOT NULL auto_increment comment "aaa",\&nbsp;</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">&nbsp; &nbsp; &nbsp;`username` varchar(50) NOT NULL Default "" comment "aaa",\&nbsp;</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">&nbsp; &nbsp; &nbsp;`realName` varchar(50) NOT NULL Default "" comment "aaa",\&nbsp;</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">&nbsp; &nbsp; &nbsp;`age` int(11) NOT NULL Default 0 comment "aaa",\&nbsp;</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">&nbsp; &nbsp; &nbsp;PRIMARY KEY (`ID`)\&nbsp;</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">)ENGINE=INNODB DEFAULT CHARSET=utf8 COMMENT="AAAA";\&nbsp;</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">inception_magic_commit;'&nbsp;</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">try:&nbsp;</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">&nbsp; &nbsp; conn=MySQLdb.connect(host='127.0.0.1',user='',passwd='',db='',port=6669)&nbsp;</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">&nbsp; &nbsp; cursor=conn.cursor()&nbsp;</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">&nbsp; &nbsp; cursor.execute(sql)&nbsp;</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">&nbsp; &nbsp; results = cursor.fetchall()&nbsp;</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">&nbsp; &nbsp; column_name_max_size=max(len(i[0]) for i in cursor.description)&nbsp;</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">&nbsp; &nbsp; row_num=0&nbsp;</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">&nbsp; &nbsp; for result in results:&nbsp;</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">&nbsp; &nbsp; &nbsp; &nbsp; row_num=row_num+1&nbsp;</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">&nbsp; &nbsp; &nbsp; &nbsp; print '*'.ljust(27,'*'),row_num,'.row', '*'.ljust(27,'*')&nbsp;</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">&nbsp; &nbsp; &nbsp; &nbsp; row = map(lambda x, y: (x,y), (i[0] for i in cursor.description), result)&nbsp;</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">&nbsp; &nbsp; &nbsp; &nbsp; for each_column in row:&nbsp;</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; if each_column[0] != 'errormessage':&nbsp;</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; print each_column[0].rjust(column_name_max_size),":",each_column[1]&nbsp;</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; else:&nbsp;</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; print each_column[0].rjust(column_name_max_size),':',each_column[1].replace('\n','\n'.ljust(column_name_max_size+4))&nbsp;</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">&nbsp; &nbsp; cursor.close()&nbsp;</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">&nbsp; &nbsp; conn.close()&nbsp;</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">except MySQLdb.Error,e:&nbsp;</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">&nbsp; &nbsp; &nbsp;print "Mysql Error %d: %s" % (e.args[0], e.args[1])&nbsp;</span>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		<span style="font-family:&quot;"></span>
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		执行测试脚本
	</p>
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">python inc.py&nbsp;</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">*************************** 1 .row ***************************</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;ID : 1</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">&nbsp; &nbsp; &nbsp; &nbsp; stage : RERUN</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">&nbsp; &nbsp; &nbsp;errlevel : 0</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">&nbsp; stagestatus : Execute Successfully</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">&nbsp;errormessage : None</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; SQL : use test</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">Affected_rows : 0</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">&nbsp; &nbsp; &nbsp;sequence : '1487924011_2298_0'</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">backup_dbname : None</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">&nbsp;execute_time : 0.000</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">&nbsp; &nbsp; &nbsp; sqlsha1 :&nbsp;</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">*************************** 2 .row ***************************</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;ID : 2</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">&nbsp; &nbsp; &nbsp; &nbsp; stage : EXECUTED</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">&nbsp; &nbsp; &nbsp;errlevel : 0</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">&nbsp; stagestatus : Execute Successfully</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">&nbsp;errormessage : None</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; SQL : CREATE TABLE `alifeba_user` ( &nbsp; &nbsp; `ID` int(11) unsigned NOT NULL auto_increment comment "aaa", &nbsp; &nbsp; `username` varchar(50) NOT NULL Default "" comment "aaa", &nbsp; &nbsp; `realName` varchar(50) NOT NULL Default "" comment "aaa", &nbsp; &nbsp; `age` int(11) NOT NULL Default 0 comment "aaa", &nbsp; &nbsp; PRIMARY KEY (`ID`))ENGINE=INNODB DEFAULT CHARSET=utf8 COMMENT="AAAA"</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">Affected_rows : 0</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">&nbsp; &nbsp; &nbsp;sequence : '1487924011_2298_1'</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">backup_dbname : 127_0_0_1_3306_test</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">&nbsp;execute_time : 0.010</span><br style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">&nbsp; &nbsp; &nbsp; sqlsha1 :&nbsp;</span>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		成功
	</p>
	<h1 style="margin:0px;padding:0px;color:#555555;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		<a name="t9"></a>3&nbsp;&nbsp;inception_web安装
	</h1>
	<h2 style="margin:0px;padding:0px;color:#555555;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		<a name="t10"></a>3.1&nbsp; inception_web简介
	</h2>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		inception_web是web封装的界面，可以通过web界面来实现相关功能，用python写的，目前比较简单，后面的需求需要自己开发
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		源码地址：<a target="_blank" href="https://github.com/dbalihui/inception_web" style="text-decoration-line:none;color:#0C89CF;">https://github.com/dbalihui/inception_web</a>
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		打开地址后，可以看到：
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		数据库运维平台
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		已实现功能:
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		表结构语法审核
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		环境配置
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		python2.7 + flask
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		先安装依赖模块
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		pip install flask_wtf
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		pip install flask-script
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		pip install flask-debugtoolbar
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		pip install MySQL-python
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		使用方法
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		先将app目录中的inception.py文件里的账号密码改成自己的
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		记得use sql_check这里要改成自己的数据库名字
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		在inception_web目录下运行./run.py runserver --host 0.0.0.0
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		使用浏览器访问你的IP http://192.168.xx.xxx:5000/
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		运行报错的话是因为没有安装flask组件，请使用pipinstall xx安装相关组件
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		我的系统是python版本为2.6.6所以我们需要先升级python
	</p>
	<h2 style="margin:0px;padding:0px;color:#555555;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		<a name="t11"></a>3.2&nbsp; 升级python到2.7
	</h2>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		# wget https://www.python.org/ftp/python/2.7.10/Python-2.7.10.tgz --no-check-certificate
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		#&nbsp;tar -xvf Python-2.7.10.tar
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		#&nbsp;cd Python-2.7.10
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		#&nbsp;./configure
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		# make –j 8 &amp;&amp; make install
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		#&nbsp;/usr/local/bin/python -V
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		#&nbsp;mv /usr/bin/python /usr/bin/python2.6.6
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		#&nbsp;ln -s /usr/local/bin/python /usr/bin/python
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		#&nbsp;python -V //验证版本
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		#&nbsp;vim /usr/bin/yum &nbsp; //修改#!/usr/bin/python 为#!/usr/bin/python2.6.6,因为yum安装依赖的是2.6版本的python
	</p>
	<h2 style="margin:0px;padding:0px;color:#555555;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		<a name="t12"></a>3.3&nbsp; 安装incpetion_web依赖模块
	</h2>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		#&nbsp;yum -y install python-pip &nbsp; //yum安装的是2.6版本的pip
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		# wget https://bootstrap.pypa.io/ez_setup.py&nbsp; --no-check-certificate&nbsp; //下载一个ez_setup 安装pip2.7版本的
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		# python2.7 ez_setup.py
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		# easy_install-2.7 pip
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		# pip2.7 install flask_wtf
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		# pip2.7 install flask-script
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		# pip2.7 install flask-debugtoolbar
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		# pip2.7 install MySQL-python //如果安装报错yuminstall mysql-devel –y
	</p>
	<h2 style="margin:0px;padding:0px;color:#555555;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		<a name="t13"></a>3.4&nbsp; 修改配置文件
	</h2>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		# unzip inception_web-master.zip
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		#&nbsp;cd inception_web-master/app
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		# vim inception.py
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		#coding=utf-8
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		&nbsp;
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		import MySQLdb
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		&nbsp;
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		def table_structure(mysql_structure):
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		&nbsp;&nbsp;&nbsp; sql1=' /*--user=thunder;--password=thunder;--host=127.0.0.1;--execute=1;--port=3307;*/\
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;inception_magic_start;\
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; use test;' //此处为默认选择数据库，如果在web不加use会默认对该库操作，对于生产库请慎重选择，建议最好创建一下与业务无关的库，在执行SQL的时候加上usedbname;
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		&nbsp;&nbsp;&nbsp;sql2='inception_magic_commit;'
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		&nbsp;&nbsp;&nbsp; sql = sql1 +mysql_structure + sql2
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		&nbsp;&nbsp;&nbsp; try:
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;conn=MySQLdb.connect(host='127.0.0.1',user='root',passwd='',db='',port=6669,use_unicode=True,charset="utf8")
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; cur=conn.cursor()
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ret=cur.execute(sql)
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;result=cur.fetchall()
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; num_fields =len(cur.description)
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; field_names = [i[0]for i in cur.description]
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; print field_names
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; for row in result:
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; print row[0],"|",row[1],"|",row[2],"|",row[3],"|",row[4],"|",row[5],"|",row[6],"|",row[7],"|",row[8],"|",row[9],"|",row[10]
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; cur.close()
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; conn.close()
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		&nbsp;&nbsp;&nbsp; except MySQLdb.Error,e:
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; print "MysqlError %d: %s" % (e.args[0], e.args[1])
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		returnresult[1][4].split("\n")
	</p>
	<h2 style="margin:0px;padding:0px;color:#555555;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		<a name="t14"></a>3.5&nbsp; 启动inception_web
	</h2>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		# cd inception_web-master
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		# ./run.py runserver --host 0.0.0.0
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		在浏览器中访问服务器http://IP:5000就可以访问页面了
	</p>
</p>