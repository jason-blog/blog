<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">&nbsp;mysqldiff该工具是官方mysql-utilities工具集的一个脚本，可以用来对比不同数据库之间的表结构，或者同个数据库间的表结构&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">&nbsp;&nbsp; 如果在windows下，直接下载mysql-utilities安装就可以了，然后运行后，会跑到命令行下：&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">1） 基本用法&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">&nbsp;&nbsp; mysqldiff --server1=admin:123456@192.168.79.10 --server2=admin:123456@192.168.79.11&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">--difftype=differ test:test&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">&nbsp; 这样就比较两个不同库中的数据库test，假设两个库中库名都是test&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">也可以比较不同的表&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">mysqldiff --server1=user@host1 --server2=user@host2 testdb.table1:anotherdb.anothertable&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">&nbsp;&nbsp;&nbsp;&nbsp; 就是使用库名.表名的方式就可以了&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">&nbsp; 下面是出来的一个效果&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;"># mysqldiff --force --server1=root:msandbox@127.0.0.1:21489 --server2=root:msandbox@127.0.0.1:21490 employees:employees&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;"># WARNING: Using a password on the command line interface can be insecure.&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;"># server1 on 127.0.0.1: ... connected.&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;"># server2 on 127.0.0.1: ... connected.&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;"># Comparing `employees` to `employees`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [PASS]&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;"># Comparing `employees`.`departments` to `employees`.`departments`&nbsp;&nbsp; [FAIL]&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;"># Object definitions differ. (--changes-for=server1)&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">#&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">--- `employees`.`departments`&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">+++ `employees`.`departments`&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">@@ -1,6 +1,6 @@&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">CREATE TABLE `departments` (&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">&nbsp;&nbsp; `dept_no` char(4) NOT NULL,&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">-&nbsp; `dept_name` varchar(40) NOT NULL,&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">+&nbsp; `dept_name` varchar(256) DEFAULT NULL,&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">&nbsp;&nbsp; PRIMARY KEY (`dept_no`),&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">&nbsp;&nbsp; UNIQUE KEY `dept_name` (`dept_name`)&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">) ENGINE=InnoDB DEFAULT CHARSET=latin1&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">&nbsp; 可以看到，默认-号代表左边要比较的server1的变化，+号代表右边server2的不同，&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">如果要交换，可以使用参数：&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">&nbsp;&nbsp;&nbsp;<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">--</span>changes-for=server2&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">&nbsp; 如果要在比较不同的时候，强行继续比较下去，要增加--force选项&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">2） 可以生成差异化的SQL，因为方法1）中，只产生了不同的地方，但如为了生产考虑，&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">要生成达到server2的脚本，则可以使用参数&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">&nbsp; --difftype=sql，&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">则：&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">&nbsp; mysqldiff --server1=admin:123456@192.168.79.10 --server2=admin:123456@192.168.79.11&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">--difftype=sql test:test&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<p>
	<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">mysqldiff的核心是使用INFORMATION_SCHEMA&nbsp;</span> 
</p>
<p>
	<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;"><br />
</span> 
</p>
<p>
	<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;"> </span>
</p>
<pre class="prettyprint lang-js linenums">SHOW CREATE TABLE `departments`;  
SELECT TABLE_SCHEMA, TABLE_NAME, ENGINE, AUTO_INCREMENT, AVG_ROW_LENGTH, CHECKSUM, TABLE_COLLATION, TABLE_COMMENT, ROW_FORMAT, CREATE_OPTIONS  
  FROM INFORMATION_SCHEMA.TABLES WHERE TABLE_SCHEMA = 'employees' AND TABLE_NAME = 'departments';  
SELECT ORDINAL_POSITION, COLUMN_NAME, COLUMN_TYPE, IS_NULLABLE,  
         COLUMN_DEFAULT, EXTRA, COLUMN_COMMENT, COLUMN_KEY  
  FROM INFORMATION_SCHEMA.COLUMNS  
  WHERE TABLE_SCHEMA = 'employees' AND TABLE_NAME = 'departments';  
SELECT PARTITION_NAME, SUBPARTITION_NAME, PARTITION_ORDINAL_POSITION,  
         SUBPARTITION_ORDINAL_POSITION, PARTITION_METHOD, SUBPARTITION_METHOD,  
         PARTITION_EXPRESSION, SUBPARTITION_EXPRESSION, PARTITION_DESCRIPTION  
  FROM INFORMATION_SCHEMA.PARTITIONS  
  WHERE TABLE_SCHEMA = 'employees' AND TABLE_NAME = 'departments';  
SELECT CONSTRAINT_NAME, COLUMN_NAME, REFERENCED_TABLE_SCHEMA,  
         REFERENCED_TABLE_NAME, REFERENCED_COLUMN_NAME  
  FROM INFORMATION_SCHEMA.KEY_COLUMN_USAGE  
  WHERE TABLE_SCHEMA = 'employees' AND TABLE_NAME = 'departments' AND  
        REFERENCED_TABLE_SCHEMA IS NOT NULL;  
SELECT TABLE_SCHEMA, TABLE_NAME, ENGINE, AUTO_INCREMENT, AVG_ROW_LENGTH, CHECKSUM, TABLE_COLLATION, TABLE_COMMENT, ROW_FORMAT, CREATE_OPTIONS  
  FROM INFORMATION_SCHEMA.TABLES WHERE TABLE_SCHEMA = 'employees' AND TABLE_NAME = 'departments';  
SELECT ORDINAL_POSITION, COLUMN_NAME, COLUMN_TYPE, IS_NULLABLE,  
         COLUMN_DEFAULT, EXTRA, COLUMN_COMMENT, COLUMN_KEY  
  FROM INFORMATION_SCHEMA.COLUMNS  
  WHERE TABLE_SCHEMA = 'employees' AND TABLE_NAME = 'departments';  
SELECT PARTITION_NAME, SUBPARTITION_NAME, PARTITION_ORDINAL_POSITION,  
         SUBPARTITION_ORDINAL_POSITION, PARTITION_METHOD, SUBPARTITION_METHOD,  
         PARTITION_EXPRESSION, SUBPARTITION_EXPRESSION, PARTITION_DESCRIPTION  
  FROM INFORMATION_SCHEMA.PARTITIONS  
  WHERE TABLE_SCHEMA = 'employees' AND TABLE_NAME = 'departments';  </pre>
<br />
<p>
	<br />
</p>