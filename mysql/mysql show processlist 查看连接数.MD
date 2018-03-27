show full processlist&nbsp;<br />
<br />
命令： show processlist;<br />
如果是root帐号，你能看到所有用户的当前连接。如果是其它普通帐号，只能看到自己占用的连接。<br />
show processlist;只列出前100条，如果想全列出请使用show full processlist;<br />
mysql&gt; show processlist;<br />
&nbsp;<br />
命令： show status;<br />
命令：show status like '%下面变量%';<br />
Aborted_clients 由于客户没有正确关闭连接已经死掉，已经放弃的连接数量。<br />
Aborted_connects 尝试已经失败的MySQL服务器的连接的次数。<br />
Connections 试图连接MySQL服务器的次数。<br />
Created_tmp_tables 当执行语句时，已经被创造了的隐含临时表的数量。<br />
Delayed_insert_threads 正在使用的延迟插入处理器线程的数量。<br />
Delayed_writes 用INSERT DELAYED写入的行数。<br />
Delayed_errors 用INSERT DELAYED写入的发生某些错误(可能重复键值)的行数。<br />
Flush_commands 执行FLUSH命令的次数。<br />
Handler_delete 请求从一张表中删除行的次数。<br />
Handler_read_first 请求读入表中第一行的次数。<br />
Handler_read_key 请求数字基于键读行。<br />
Handler_read_next 请求读入基于一个键的一行的次数。<br />
Handler_read_rnd 请求读入基于一个固定位置的一行的次数。<br />
Handler_update 请求更新表中一行的次数。<br />
Handler_write 请求向表中插入一行的次数。<br />
Key_blocks_used 用于关键字缓存的块的数量。<br />
Key_read_requests 请求从缓存读入一个键值的次数。<br />
Key_reads 从磁盘物理读入一个键值的次数。<br />
Key_write_requests 请求将一个关键字块写入缓存次数。<br />
Key_writes 将一个键值块物理写入磁盘的次数。<br />
Max_used_connections 同时使用的连接的最大数目。<br />
Not_flushed_key_blocks 在键缓存中已经改变但是还没被清空到磁盘上的键块。<br />
Not_flushed_delayed_rows 在INSERT DELAY队列中等待写入的行的数量。<br />
Open_tables 打开表的数量。<br />
Open_files 打开文件的数量。<br />
Open_streams 打开流的数量(主要用于日志记载）<br />
Opened_tables 已经打开的表的数量。<br />
Questions 发往服务器的查询的数量。<br />
Slow_queries 要花超过long_query_time时间的查询数量。<br />
Threads_connected 当前打开的连接的数量。<br />
Threads_running 不在睡眠的线程数量。<br />
Uptime 服务器工作了多少秒。<br />