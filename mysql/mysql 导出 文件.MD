方法一：<br style="white-space:normal;line-height:21px;" />
直接执行命令：<br style="white-space:normal;line-height:21px;" />
mysql&gt; select count(1) from table&nbsp;<wbr style="white-space:normal;line-height:21px;">&nbsp;<wbr style="white-space:normal;line-height:21px;">&nbsp;into outfile '/tmp/test.xls';<br style="white-space:normal;line-height:21px;" />
Query OK, 31 rows affected (0.00 sec)<br style="white-space:normal;line-height:21px;" />
在目录/tmp/下会产生文件test.xls<br style="white-space:normal;line-height:21px;" />
遇到的问题：<br style="white-space:normal;line-height:21px;" />
mysql&gt; select count(1) from table&nbsp;<wbr style="white-space:normal;line-height:21px;">&nbsp;<wbr style="white-space:normal;line-height:21px;">&nbsp;into outfile '/data/test.xls';<br style="white-space:normal;line-height:21px;" />
报错：<br style="white-space:normal;line-height:21px;" />
ERROR 1 (HY000): Can't create/write to file '/data/test.xls' (Errcode: 13)<br style="white-space:normal;line-height:21px;" />
可能原因：mysql没有向/data/下写的权限，没有深究<br style="white-space:normal;line-height:21px;" />
<br style="white-space:normal;line-height:21px;" />
方法二：<br style="white-space:normal;line-height:21px;" />
查询都自动写入文件：<br style="white-space:normal;line-height:21px;" />
mysql&gt; pager cat &gt; /tmp/test.txt ;<br style="white-space:normal;line-height:21px;" />
PAGER set to 'cat &gt; /tmp/test.txt'<br style="white-space:normal;line-height:21px;" />
之后的所有查询结果都自动写入/tmp/test.txt'，并前后覆盖<br style="white-space:normal;line-height:21px;" />
mysql&gt; select * from table ;<br style="white-space:normal;line-height:21px;" />
30 rows in set (0.59 sec)<br style="white-space:normal;line-height:21px;" />
在框口不再显示查询结果<br style="white-space:normal;line-height:21px;" />
以上参考：http://blog.163.com/cpu_driver/blog/static/117663448201111295420990<wbr style="white-space:normal;line-height:21px;">/<br style="white-space:normal;line-height:21px;" />
<br style="white-space:normal;line-height:21px;" />
方法三：<br style="white-space:normal;line-height:21px;" />
跳出mysql命令行<br style="white-space:normal;line-height:21px;" />
[root@SHNHDX63-146 ~]# mysql -h127.0.0.1 -uroot -pXXXX -P3306 -e"select * from table" &gt; /tmp/test/txt<br />