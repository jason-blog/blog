<p>
	MySQLdump是MySQL自带的导出数据工具，通常我们用它来导出MySQL中，但是有时候我们需要导出MySQL数据库中某个表的部分数据，这时该怎么办呢？
</p>
<p>
	<br />
</p>
<p>
	mysqldump命令中带有一个 --where/-w 参数，它用来设定数据导出的条件，使用方式和SQL查询命令中中的where基本上相同，有了它，我们就可以从数据库中导出你需要的那部分数据了。
</p>
<p>
	<br />
</p>
<p>
	命令格式如下：
</p>
<p>
	<br />
</p>
<p>
	mysqldump -u用户名 -p密码 数据库名 表名 --where="筛选条件" &gt; 导出文件路径
</p>
<p>
	<br />
</p>
<p>
	例子：
</p>
<p>
	<br />
</p>
<p>
	从meteo数据库的sdata表中导出sensorid=11 且 fieldid=0的数据到 /home/xyx/Temp.sql 这个文件中
</p>
<p>
	<br />
</p>
<p>
	mysqldump -uroot -p123456 meteo sdata --where=" sensorid=11 and fieldid=0" &gt; /home/xyx/Temp.sql
</p>
<p>
	<br />
</p>
<p>
	<br />
</p>
<p>
	<br />
</p>
<p>
	另外你还可以直接导出 文本文件*.txt
</p>
<p>
	<br />
</p>
<p>
	<br />
</p>
<p>
	<br />
</p>
<p>
	mysqldump -uroot -p123456 meteo sdata --where=" sensorid=11 and fieldid=0" &gt; /home/xyx/Temp.txt
</p>
<p>
	<br />
</p>
<p>
	<br />
</p>
<p>
	<br />
</p>
<p>
	<br />
</p>
<p>
	<br />
</p>
<p>
	///////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
</p>
<p>
	<br />
</p>
<p>
	以下是 mysqldump 的一些使用参数
</p>
<p>
	<br />
</p>
<p>
	备份数据库
</p>
<p>
	#mysqldump 数据库名 &gt;数据库备份名
</p>
<p>
	<br />
</p>
<p>
	#mysqldump -A -u用户名 -p密码 数据库名&gt;数据库备份名
</p>
<p>
	#指定导出范围
</p>
<p>
	#mysqldump -d -A --add-drop-table -uroot -p <span style="color:#454545;font-family:&quot;font-size:18px;white-space:normal;background-color:#FFFFFF;">--where=" sensorid=11 and fieldid=0"&nbsp;&nbsp;</span>&gt;xxx.sql
</p>
<p>
	<br />
</p>
<p>
	1.导出结构不导出数据
</p>
<p>
	<br />
</p>
<p>
	mysqldump -d 数据库名 -uroot -p &gt; xxx.sql
</p>
<p>
	<br />
</p>
<p>
	2.导出数据不导出结构
</p>
<p>
	<br />
</p>
<p>
	mysqldump -t 数据库名 -uroot -p &gt; xxx.sql
</p>
<p>
	<br />
</p>
<p>
	3.导出数据和表结构
</p>
<p>
	<br />
</p>
<p>
	mysqldump 数据库名 -uroot -p &gt; xxx.sql
</p>
<p>
	<br />
</p>
<p>
	4.导出特定表的结构
</p>
<p>
	<br />
</p>
<p>
	mysqldump -uroot -p -B数据库名 --table 表名 &gt; xxx.sql
</p>
<p>
	<br />
</p>
<p>
	#mysqldump [OPTIONS] database [tables]
</p>
<p>
	<br />
</p>
<p>
	mysqldump支持下列选项：
</p>
<p>
	<br />
</p>
<p>
	--add-locks &nbsp;
</p>
<p>
	在每个表导出之前增加LOCK TABLES并且之后UNLOCK TABLE。(为了使得更快地插入到MySQL)。 &nbsp;
</p>
<p>
	--add-drop-table &nbsp;
</p>
<p>
	在每个create语句之前增加一个drop table。 &nbsp;
</p>
<p>
	--allow-keywords &nbsp;
</p>
<p>
	允许创建是关键词的列名字。这由表名前缀于每个列名做到。 &nbsp;
</p>
<p>
	-c, --complete-insert &nbsp;
</p>
<p>
	使用完整的insert语句(用列名字)。 &nbsp;
</p>
<p>
	-C, --compress &nbsp;
</p>
<p>
	如果客户和服务器均支持压缩，压缩两者间所有的信息。 &nbsp;
</p>
<p>
	--delayed &nbsp;
</p>
<p>
	用INSERT DELAYED命令插入行。 &nbsp;
</p>
<p>
	-e, --extended-insert &nbsp;
</p>
<p>
	使用全新多行INSERT语法。（给出更紧缩并且更快的插入语句） &nbsp;
</p>
<p>
	-#, --debug[=option_string] &nbsp;
</p>
<p>
	跟踪程序的使用(为了调试)。 &nbsp;
</p>
<p>
	--help &nbsp;
</p>
<p>
	显示一条帮助消息并且退出。 &nbsp;
</p>
<p>
	--fields-terminated-by=... &nbsp;
</p>
<p>
	&nbsp;
</p>
<p>
	--fields-enclosed-by=... &nbsp;
</p>
<p>
	&nbsp;
</p>
<p>
	--fields-optionally-enclosed-by=... &nbsp;
</p>
<p>
	&nbsp;
</p>
<p>
	--fields-escaped-by=... &nbsp;
</p>
<p>
	&nbsp;
</p>
<p>
	--fields-terminated-by=... &nbsp;
</p>
<p>
	这些选择与-T选择一起使用，并且有相应的LOAD DATA INFILE子句相同的含义。 &nbsp;
</p>
<p>
	LOAD DATA INFILE语法。 &nbsp;
</p>
<p>
	-F, --flush-logs &nbsp;
</p>
<p>
	在开始导出前，洗掉在MySQL服务器中的日志文件。 &nbsp;
</p>
<p>
	-f, --force, &nbsp;
</p>
<p>
	即使我们在一个表导出期间得到一个SQL错误，继续。 &nbsp;
</p>
<p>
	-h, --host=.. &nbsp;
</p>
<p>
	从命名的主机上的MySQL服务器导出数据。缺省主机是localhost。 &nbsp;
</p>
<p>
	-l, --lock-tables. &nbsp;
</p>
<p>
	为开始导出锁定所有表。 &nbsp;
</p>
<p>
	-t, --no-create-info &nbsp;
</p>
<p>
	不写入表创建信息(CREATE TABLE语句） &nbsp;
</p>
<p>
	-d, --no-data &nbsp;
</p>
<p>
	不写入表的任何行信息。如果你只想得到一个表的结构的导出，这是很有用的！ &nbsp;
</p>
<p>
	--opt &nbsp;
</p>
<p>
	同--quick --add-drop-table --add-locks --extended-insert --lock-tables。 &nbsp;
</p>
<p>
	应该给你为读入一个MySQL服务器的尽可能最快的导出。 &nbsp;
</p>
<p>
	-pyour_pass, --password[=your_pass] &nbsp;
</p>
<p>
	与服务器连接时使用的口令。如果你不指定“=your_pass”部分，mysqldump需要来自终端的口令。 &nbsp;
</p>
<p>
	-P port_num, --port=port_num &nbsp;
</p>
<p>
	与一台主机连接时使用的TCP/IP端口号。（这用于连接到localhost以外的主机，因为它使用 Unix套接字。） &nbsp;
</p>
<p>
	-q, --quick &nbsp;
</p>
<p>
	不缓冲查询，直接导出至stdout；使用mysql_use_result()做它。 &nbsp;
</p>
<p>
	-S /path/to/socket, --socket=/path/to/socket &nbsp;
</p>
<p>
	与localhost连接时（它是缺省主机)使用的套接字文件。 &nbsp;
</p>
<p>
	-T, --tab=path-to-some-directory &nbsp;
</p>
<p>
	对于每个给定的表，创建一个table_name.sql文件，它包含SQL CREATE 命令，和一个table_name.txt文件，它包含数据。注意：这只有在mysqldump运行在mysqld守护进程运行的同一台机器上的时候才工作。.txt文件的格式根据--fields-xxx和 --lines--xxx选项来定。 &nbsp;
</p>
<p>
	-u user_name, --user=user_name &nbsp;
</p>
<p>
	与服务器连接时，MySQL使用的用户名。缺省值是你的Unix登录名。 &nbsp;
</p>
<p>
	-O var=option, --set-variable var=option设置一个变量的值。可能的变量被列在下面。 &nbsp;
</p>
<p>
	-v, --verbose &nbsp;
</p>
<p>
	冗长模式。打印出程序所做的更多的信息。 &nbsp;
</p>
<p>
	-V, --version &nbsp;
</p>
<p>
	打印版本信息并且退出。 &nbsp;
</p>
<p>
	-w, --where='where-condition' &nbsp;
</p>
<p>
	只导出被选择了的记录；注意引号是强制的！ &nbsp;
</p>
<p>
	"--where=user='jimf'" "-wuserid&gt;1" "-wuserid&lt;1"
</p>
<p>
	<br />
</p>
<p>
	导入数据：
</p>
<p>
	<br />
</p>
<p>
	由于mysqldump导出的是完整的SQL语句，所以用mysql客户程序很容易就能把数据导入了：
</p>
<p>
	<br />
</p>
<p>
	#mysql 数据库名 &lt; 文件名
</p>
<p>
	<br />
</p>
<p>
	or:
</p>
<p>
	<br />
</p>
<p>
	#show databases;
</p>
<p>
	<br />
</p>
<p>
	然后选择被导入的数据库：
</p>
<p>
	<br />
</p>
<p>
	#use ***；
</p>
<p>
	<br />
</p>
<p>
	#source /tmp/xxx.sql
</p>
<p>
	<br />
</p>
<p>
	///////////////////////////////////////////////////////////////////////////////////////////////////////////////
</p>