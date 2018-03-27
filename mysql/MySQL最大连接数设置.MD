<p>
	&nbsp;在使用MySQL数据库的时候，经常会遇到这么一个问题，就是“Can not connect to MySQL server. Too many connections”-mysql 1040错误，这是因为访问MySQL且还未释放的连接数目已经达到MySQL的上限。通常，mysql的最大连接数默认是100, 最大可以达到16384。
</p>
<p>
	<br />
</p>
<p>
	&nbsp; &nbsp; 在Windows下常用的有两种方式修改最大连接数。
</p>
<p>
	<br />
</p>
<p>
	&nbsp; &nbsp; 第一种：命令行修改。
</p>
<p>
	<br />
</p>
<p>
	&nbsp; &nbsp;&gt;mysql -uuser -ppassword(命令行登录MySQL)
</p>
<p>
	<br />
</p>
<p>
	&nbsp; &nbsp;mysql&gt;show variables like 'max_connections';(查可以看当前的最大连接数)
</p>
<p>
	<br />
</p>
<p>
	&nbsp; &nbsp;msyql&gt;set global max_connections=1000;(设置最大连接数为1000，可以再次查看是否设置成功)
</p>
<p>
	<br />
</p>
<p>
	&nbsp; &nbsp;mysql&gt;exit(推出)
</p>
<p>
	<br />
</p>
<p>
	&nbsp; &nbsp;这种方式有个问题，就是设置的最大连接数只在mysql当前服务进程有效，一旦mysql重启，又会恢复到初始状态。因为mysql启动后的初始化工作是从其配置文件中读取数据的，而这种方式没有对其配置文件做更改。
</p>
<p>
	<br />
</p>
<p>
	&nbsp; &nbsp;第二种：修改配置文件。
</p>
<p>
	<br />
</p>
<p>
	&nbsp; 这 种方式说来很简单，只要修改MySQL配置文件my.ini 或 my.cnf的参数max_connections，将其改为max_connections=1000，然后重启MySQL即可。但是有一点最难的就是my.ini这个文件在哪找。通常有两种可能，一个是在安装目录下（这是比较理想的情况），另一种是在数据文件的目录下，安装的时候如果没有人为改变目录的话，一般就在C:/ProgramData/MySQL往下的目录下。
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
	与连接数相关的几个参数：
</p>
<p>
	<br />
</p>
<p>
	&nbsp; &nbsp; 在修改最大连接数的时候会有这样一个疑问—这个值是不是越大越好，或者设置为多大才合适？这个参数的大小要综合很多因素来考虑，比如使用的平台所支持的线程库数量（windows只能支持到2048）、服务器的配置（特别是内存大小）、每个连接占用资源（内存和负载）的多少、系统需要的响应时间等。可以在global或session范围内修改这个参数。连接数的增加会带来很多连锁反应，需要在实际中避免由此引发的负面影响。
</p>
<p>
	<br />
</p>
<p>
	&nbsp; &nbsp;首先看一下MySQL的状态：
</p>
<p>
	<br />
</p>
<p>
	mysql&gt; status;
</p>
<p>
	--------------
</p>
<p>
	mysql &nbsp;Ver 14.14 Distrib 5.5.15, for Win32 (x86)
</p>
<p>
	<br />
</p>
<p>
	Connection id: &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;1
</p>
<p>
	Current database:
</p>
<p>
	Current user: &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; root@localhost
</p>
<p>
	SSL: &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;Not in use
</p>
<p>
	Using delimiter: &nbsp; &nbsp; &nbsp; &nbsp;;
</p>
<p>
	Server version: &nbsp; &nbsp; &nbsp; &nbsp; 5.5.15 MySQL Community Server (GPL)
</p>
<p>
	Protocol version: &nbsp; &nbsp; &nbsp; 10
</p>
<p>
	Connection: &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; localhost via TCP/IP
</p>
<p>
	Server characterset: &nbsp; &nbsp;utf8
</p>
<p>
	Db &nbsp; &nbsp; characterset: &nbsp; &nbsp;utf8
</p>
<p>
	Client characterset: &nbsp; &nbsp;gbk
</p>
<p>
	Conn. &nbsp;characterset: &nbsp; &nbsp;gbk
</p>
<p>
	TCP port: &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 3306
</p>
<p>
	Uptime: &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 1 hour 3 min 27 sec
</p>
<p>
	<br />
</p>
<p>
	Threads: 12 &nbsp;Questions: 18 &nbsp;Slow queries: 10 &nbsp;Opens: 33 &nbsp;Flush tables: 5 &nbsp;Open tab
</p>
<p>
	les: 34 &nbsp;Queries per second avg: 6.256
</p>
<p>
	--------------
</p>
<p>
	<br />
</p>
<p>
	Open tables:34,即当前数据库打开表的数量是34个，注意这个34并不是实际的34个表，因为MySQL是多线程的系统，几个不同的并发连接可能打开同一个表，这就需要为不同的连接session分配独立的内存空间来存储这些信息以避免冲突。因此连接数的增加会导致MySQL需要的文件描述符数目的增加。另外对于MyISAM表，还会建立一个共享的索引文件描述符。
</p>
<p>
	<br />
</p>
<p>
	&nbsp; &nbsp;在MySQL数据库层面，有几个系统参数决定了可同时打开的表的数量和要使用的文件描述符，那就是table_open_cache、max_tmp_tables和open_files_limit。
</p>
<p>
	<br />
</p>
<p>
	mysql&gt; show variables like 'table_open%';
</p>
<p>
	+------------------+-------+
</p>
<p>
	| Variable_name &nbsp; &nbsp;| Value |
</p>
<p>
	+------------------+-------+
</p>
<p>
	| table_open_cache | 256 &nbsp; |
</p>
<p>
	+------------------+-------+
</p>
<p>
	1 row in set (0.00 sec)
</p>
<p>
	<br />
</p>
<p>
	table_open_cache:256，这就是说所有的MySQL线程一共能同时打开256个表，我们可以搜集系统的打开表的数量的历史记录和这个参数来对比，决定是否要增加这个参数的大小。查看当前的打开表的数目(Open tables)可用上边提到过的status命令，另外可以直接查询这个系统变量的值：
</p>
<p>
	<br />
</p>
<p>
	mysql&gt; show status like 'open_tables';
</p>
<p>
	+---------------+-------+
</p>
<p>
	| Variable_name | Value |
</p>
<p>
	+---------------+-------+
</p>
<p>
	| Open_tables &nbsp; | 3 &nbsp; &nbsp; |
</p>
<p>
	+---------------+-------+
</p>
<p>
	1 row in set (0.00 sec)
</p>
<p>
	<br />
</p>
<p>
	Open_tables就是当前打开表的数目，通过flush tables命令可以关闭当前打开的表。 这个值如果过大，并且如果没有经常的执行flush tables命令，可以考虑增加table_open_cache参数的大小。
</p>
<p>
	<br />
</p>
<p>
	接下来看max_tmp_tables:
</p>
<p>
	mysql&gt; show variables like 'max_tmp%';
</p>
<p>
	+----------------+-------+
</p>
<p>
	| Variable_name &nbsp;| Value |
</p>
<p>
	+----------------+-------+
</p>
<p>
	| max_tmp_tables | 32 &nbsp; &nbsp;|
</p>
<p>
	+----------------+-------+
</p>
<p>
	1 row in set (0.00 sec)
</p>
<p>
	max_tmp_tables:32即单个客户端连接能打开的临时表数目。查看当前已打开的临时表的信息：
</p>
<p>
	mysql&gt; show global status like '%tmp%table%';
</p>
<p>
	+-------------------------+-------+
</p>
<p>
	| Variable_name &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; | Value |
</p>
<p>
	+-------------------------+-------+
</p>
<p>
	| Created_tmp_disk_tables | 0 &nbsp; &nbsp; |
</p>
<p>
	| Created_tmp_tables &nbsp; &nbsp; &nbsp;| 11 &nbsp; &nbsp;|
</p>
<p>
	+-------------------------+-------+
</p>
<p>
	2 rows in set (0.00 sec)
</p>
<p>
	根据这两个值可以判断临时表的创建位置，一般选取BLOB和TEXT列、Group by 和 Distinct语句的数据量超过512 bytes，或者union的时候select某列的数据超过512 bytes的时候，就直接在磁盘上创建临时表了，另外内存中的临时表变大的时候，也可能被MySQL自动转移到磁盘上（由tmp_table_size和max_heap_table_size参数决定）。
</p>
<p>
	<br />
</p>
<p>
	增加table_open_cache或max_tmp_tables 参数的大小后，从操作系统的角度看，mysqld进程需要使用的文件描述符的个数就要相应的增加，这个是由open_files_limit参数控制的。
</p>
<p>
	mysql&gt; show variables like 'open_files%';
</p>
<p>
	+------------------+-------+
</p>
<p>
	| Variable_name &nbsp; &nbsp;| Value |
</p>
<p>
	+------------------+-------+
</p>
<p>
	| open_files_limit | 2670 &nbsp;|
</p>
<p>
	+------------------+-------+
</p>
<p>
	1 row in set (0.00 sec)
</p>
<p>
	但是这个参数是OS限制的，所以我们设定的值并不一定总是生效。如果OS限制MySQL不能修改这个值，那么置为0。如果是专用的MySQL服务器上，这个值一般要设置的尽量大，就是设为没有报Too many open files错误的最大值，这样就能一劳永逸了。当操作系统无法分配足够的文件描述符的时候，mysqld进程会在错误日志里记录警告信息。
</p>
<p>
	相应的，有两个状态变量记录了当前和历史的文件打开信息：
</p>
<p>
	mysql&gt; show global status like '%open%file%';
</p>
<p>
	+---------------+-------+
</p>
<p>
	| Variable_name | Value |
</p>
<p>
	+---------------+-------+
</p>
<p>
	| Open_files &nbsp; &nbsp;| 0 &nbsp; &nbsp; |
</p>
<p>
	| Opened_files &nbsp;| 76 &nbsp; &nbsp;|
</p>
<p>
	+---------------+-------+
</p>
<p>
	2 rows in set (0.00 sec)
</p>
<p>
	MySQL为每个连接分配线程来处理，可以通过threads_connected参数查看当前分配的线程数量：
</p>
<p>
	mysql&gt; show status like '%thread%';
</p>
<p>
	+------------------------------------------+-------+
</p>
<p>
	| Variable_name &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;| Value |
</p>
<p>
	+------------------------------------------+-------+
</p>
<p>
	| Delayed_insert_threads &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; | 0 &nbsp; &nbsp; |
</p>
<p>
	| Performance_schema_thread_classes_lost &nbsp; | 0 &nbsp; &nbsp; |
</p>
<p>
	| Performance_schema_thread_instances_lost | 0 &nbsp; &nbsp; |
</p>
<p>
	| Slow_launch_threads &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;| 0 &nbsp; &nbsp; |
</p>
<p>
	| Threads_cached &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; | 0 &nbsp; &nbsp; |
</p>
<p>
	| Threads_connected &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;| 1 &nbsp; &nbsp; |
</p>
<p>
	| Threads_created &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;| 1 &nbsp; &nbsp; |
</p>
<p>
	| Threads_running &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;| 1 &nbsp; &nbsp; |
</p>
<p>
	+------------------------------------------+-------+
</p>
<p>
	8 rows in set (0.00 sec)
</p>
<p>
	比较threads_connected参数和前面提到的max_connections参数，也可以作为目前的系统负载的参照，决定是否需要修改连接数。
</p>
<p>
	<br />
</p>
<p>
	查看每个线程的详细信息：mysql&gt;show processlist;对影响系统运行的线程：kill connection|query threadid的命令杀死。
</p>
<p>
	<br />
</p>
<p>
	<br />
</p>