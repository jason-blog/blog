<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:&quot;"><strong style="box-sizing:border-box;">1、MySQL checksum命令</strong></span>
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:&quot;"><br style="box-sizing:border-box;" />
</span>
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:&quot;">在执行checksum命令时，表会被加一个读锁(read lock)，checksum table的原理是对表中的数据进行一行一行的较验和计算，因些对于大表，这是一个很耗时的过程。</span>
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:&quot;">如果对于myisam表，建表时加上CHECKSUM=1选项，那么在对这样的表进行checksum table时将会非常快</span>
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:&quot;"><br style="box-sizing:border-box;" />
</span>
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:&quot;">checksum table test.tbname;</span>
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:&quot;">root@test09:43:36&gt;checksum table test.tbname;</span>
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:&quot;">+-------------+------------+</span>
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:&quot;">| Table &nbsp; &nbsp; &nbsp; | Checksum &nbsp; |</span>
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:&quot;">+-------------+------------+</span>
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:&quot;">| test.tbname | 1105600045 |</span>
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:&quot;">+-------------+------------+</span>
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:&quot;">1 row in set (0.00 sec)</span>
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:&quot;">具体逻辑见MySQL源码(MySQL 5.7.17)：</span>
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:&quot;">sql/sql_table.cc</span>
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:&quot;">bool mysql_checksum_table(THD *thd, TABLE_LIST *tables,HA_CHECK_OPT *check_opt)</span>
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:&quot;"><br style="box-sizing:border-box;" />
</span>
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:&quot;"><strong style="box-sizing:border-box;">2、mysqldiff</strong></span>
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:&quot;"><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;">mysqldiff该工具是官方mysql-utilities工具集的一个脚本，可以用来对比不同数据库之间的表结构，或者同个数据库间的表结构。</span></span>
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:&quot;"><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;">下载地址：</span></span>
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:&quot;"><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;"><a target="_blank" href="https://dev.mysql.com/downloads/utilities/" style="box-sizing:border-box;background:transparent;color:#CA0C16;text-decoration-line:none;margin:0px;padding:0px;outline:none;">https://dev.mysql.com/downloads/utilities/</a><br style="box-sizing:border-box;" />
</span></span>
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:&quot;">示例一：检查server1,server2上的某个表结构是否一致</span>
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:&quot;">mysqldiff --server1=user:pwd@host:port --server2=user:pwd@host:port --changes-for=server2&nbsp; dbname.tablename:dbname.tablename<br style="box-sizing:border-box;" />
</span>
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:&quot;">示例二：检查server1,server2上的两个数据库中的表结构是否一致</span>
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:&quot;">mysqldiff --server1=user:pwd@host:port --server2=user:pwd@host:port dbname:dbname --changes-for=server2<br style="box-sizing:border-box;" />
</span>
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:&quot;"><br style="box-sizing:border-box;" />
</span>
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:&quot;"><strong style="box-sizing:border-box;">3、mysqldbcompare</strong></span>
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:&quot;"><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;">mysqldiff该工具是官方mysql-utilities工具集的一个脚本，可以用来检查不同数据库之间的数据一致性，检查内容包括数据库字符集、表结构、数据内容，只要有一个不一样，则检查不通过。</span><br style="box-sizing:border-box;" />
</span>
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:&quot;"><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;">示例：</span></span>
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:&quot;">mysqldbcompare --server1=user:pwd@192.168.56.110:3306 --server2=user:pwd@192.168.56.111:3306&nbsp;--changes-for=server1 dbname:dbname<br style="box-sizing:border-box;" />
</span>
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:&quot;"><br style="box-sizing:border-box;" />
</span>
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:&quot;"><strong style="box-sizing:border-box;">4、pt-table-checksum</strong></span>
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:&quot;">pt-table-checksum是在线的主从数据一致性检查工具，能够对大数据量的数据库进行高效的主从数据一致性检查，能够自动控制检查数据量的大小，避免对线上业务造成较大的影响。下面对展示该工具的常见几种用法，更多细节见pt-table-checksum官方帮助文档。</span>
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:&quot;"><br style="box-sizing:border-box;" />
</span>
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:&quot;"><br style="box-sizing:border-box;" />
</span>
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:&quot;">示例一：对特定表的一致性进行检查</span>
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:&quot;">pt-table-checksum --host='192.168.56.110' --user='admin' --password='pwd' --port=3306 --recursion-method=processlist --replicate=percona.checksums --no-check-binlog-format</span>&nbsp;--chunk-time=0.5 --tables='dbname.tb1,dbname2.tb2'
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<br style="box-sizing:border-box;" />
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	示例二：对特定数据库的一致性进行检查
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	pt-table-checksum --host='<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:&quot;">192.168.56.110</span>' --user='admin' --password='pwd' --port=3306 --recursion-method=processlist --replicate=percona.checksums --no-check-binlog-format --chunk-time=0.5&nbsp;--databases='dbname1,dbname2'
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<br style="box-sizing:border-box;" />
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	示例三：对所有数据库的一致性进行检查
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	pt-table-checksum --host='<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:&quot;">192.168.56.110</span>' --user='admin' --password='pwd' --port=3306 --recursion-method=processlist --replicate=percona.checksums --no-check-binlog-format --chunk-time=0.5
</div>