http://www.programgo.com/article/74773263570/<br />
<h1 accuse="qTitle" style="margin:0px;padding:0px;font-size:16px;font-stretch:normal;line-height:26px;font-family:&quot;word-break:break-all;position:relative;color:#333333;white-space:normal;">
	<span class="ask-title " style="display:inline;font-size:24px;line-height:34px;font-weight:400;overflow:hidden;">mysql主从同步中show master status，结果为空</span> 
</h1>
<br />
<p>
	<br />
</p>
<p>
	<br />
</p>
<div id="answer-content-1484062898" accuse="aContent" class="answer-text line" style="line-height:24px;">
	没有开启二进制日志<br />
mysql&gt;show variables like '%log_bin%';&nbsp;如果是off表示你没有开启
</div>
<div class="replyask-box mb-15" style="margin-bottom:15px;position:relative;overflow:hidden;">
	<div class="replyask line replyask-ask 0" id="replyask-124139895" style="position:relative;padding-bottom:0px;padding-top:14px;">
		<div class="ask-supply-line" style="width:1px;height:38px;background-image:initial;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;line-height:0;position:absolute;left:25px;top:14px;">
		</div>
		<div class="ask ask-supply f-12 grid" style="display:inline-block;float:left;position:relative;width:50px;height:22px;line-height:22px;border-radius:11px;border:1px solid #E8ECEE;text-align:center;margin-right:12px;background-image:initial;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;">
			追问
		</div>
		<div class="replyask-content line ml-10" accuse="qRA" id="replyask-content-124139895" style="margin-left:64px;word-break:break-all;">
<pre accuse="qRA" style="margin-top:0px;margin-bottom:0px;padding:0px;">还真是off，怎么开启二进制日志啊？？</pre>
		</div>
	</div>
	<div class="replyask line replyask-ans 1" id="replyask-124141802" style="position:relative;padding-bottom:0px;padding-top:14px;">
		<div class="ask-supply-line" style="width:1px;height:110px;background-image:initial;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;line-height:0;position:absolute;left:25px;top:14px;">
		</div>
		<div class="reply ask-supply f-12 grid" style="display:inline-block;float:left;width:50px;height:22px;line-height:22px;border-radius:11px;border:1px solid #E8ECEE;text-align:center;margin-right:12px;background-image:initial;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;position:relative;">
			追答
		</div>
		<div class="replyask-content line ml-10" accuse="aRA" id="replyask-content-124141802" style="margin-left:64px;word-break:break-all;">
<pre accuse="aRA" style="margin-top:0px;margin-bottom:0px;padding:0px;">在my.cnf中添加一条语句
log_bin=/var/log/mysqld/mysql-bin      
重启mysql</pre>
		</div>
	</div>
</div>
<p>
	<br />
</p>
<p>
	<br />
</p>
重点：主服务器需要执行 show master status ; 查看file和position在从服务器中对应<br />
<br />
change master to &nbsp;&nbsp;<br />
master_host='10.1.2.162', &nbsp;<br />
master_user='root', &nbsp;<br />
master_password='root', &nbsp;<br />
master_log_file='mysql-bin.000001', &nbsp;//SHOW MASTER STATUS;中的file&nbsp;<br />
master_log_pos=1832; //SHOW MASTER STATUS;中的position&nbsp;<br />
<br />
<br />
主服务器 &nbsp;auto_increment_offset＝1 设置步长<br />
<br />
<br />
编辑my.cnf&nbsp;<br />
在【mysqld】中去除下面注释：&nbsp;<br />
servier-id &nbsp;= 1&nbsp;<br />
log_bin &nbsp;= /var/log/mysql/mysql-bin.log&nbsp;<br />
binlog-do-db=test &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; //如果有多个数据库需要同步，重复此参数，每个数据库一行&nbsp;<br />
binlog-ignore-db=mysql //不同步的数据库&nbsp;<br />
<br />
<br />
重新启动mysql&nbsp;<br />
service mysql restart&nbsp;<br />
通过命令查看：&nbsp;<br />
show master status ; &nbsp;//通过该命令获取file和position，这个在配置slave的时候有用&nbsp;<br />
<br />
<br />
<br />
<br />
从机配置&nbsp;<br />
编辑【mysqld】&nbsp;<br />
server-id &nbsp;= 2&nbsp;<br />
replicate-do-db=test&nbsp;<br />
replicate-ignore-db=mysql &nbsp;<br />
<br />
replicate-wild-do-table = mysys.channel &nbsp; &nbsp;#需要同步的一个表<br />
replicate-wild-do-table = mysys.isp_channel &nbsp; #需要同步的一个表<br />
slave-skip-errors= 1062 &nbsp; //加上这条&nbsp;<br />
重启mysql服务&nbsp;<br />
service mysql restart&nbsp;<br />
<br />
4)在从服务器上执行如下命令&nbsp;<br />
mysql&gt;stop slave;&nbsp;<br />
mysql&gt;change master to master_host='192.168.0.123',master_user=’root',master_password='passwd',master_port=3306,&nbsp;<br />
master_log_file='mysql-bin.000001',master_log_pos=107;<br />
<br />
/////////////////////like//////////////////////////<br />
change master to &nbsp;&nbsp;<br />
master_host='10.1.2.162', &nbsp;<br />
master_user='root', &nbsp;<br />
master_password='root', &nbsp;<br />
master_log_file='mysql-bin.000001', &nbsp;//SHOW MASTER STATUS;中的file&nbsp;<br />
master_log_pos=1832; //SHOW MASTER STATUS;中的position&nbsp;<br />
<br />
<br />
常用命令&nbsp;<br />
<br />
<br />
SHOW SLAVE STATUS;<br />
START SLAVE;<br />
STOP SLAVE;<br />
/////////////////////////////////////////////<br />
<br />
&nbsp;<br />
mysql&gt;start slave;&nbsp;<br />
mysql&gt;show slave status&nbsp;<br />
如果slave_IO_running:yes &nbsp; &nbsp;&nbsp;<br />
slave_sql_running:yes,那说明没有问题了，就可以再主机上面建库建表写测试数据了<br />
<br />
<br />
Got fatal error 1236 from master when reading data from binary log: 'Could not find first log file name in binary log index file'”等或由于清数据导致主从库不同步了，解决办法如下：&nbsp;<br />
先进入slave中执行:"slave stop;"来停止从库同步；&nbsp;<br />
再去master中执行:"flush logs;"来清空日志；&nbsp;<br />
然后在master中执行:"show master status;"查看下主库的状态，主要是日志的文件和position；&nbsp;<br />
<br />
<br />
<br />
mysql&gt; show master status;&nbsp;<br />
+------------------+----------+--------------+------------------+-------------------+&nbsp;<br />
| File &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; | Position | Binlog_Do_DB | Binlog_Ignore_DB | Executed_Gtid_Set |&nbsp;<br />
+------------------+----------+--------------+------------------+-------------------+&nbsp;<br />
| mysql-bin.000006 | &nbsp; &nbsp; &nbsp;120 | DATABASSE &nbsp; &nbsp; | mysql &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;| &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; |&nbsp;<br />
+------------------+----------+--------------+------------------+-------------------+&nbsp;<br />
1 row in set (0.00 sec)&nbsp;<br />
<br />
然后回到slave中，执行:"CHANGE MASTER TO MASTER_LOG_FILE='log-bin.000004',MASTER_LOG_POS=106;"，文件和位置对应master中的;&nbsp;<br />
最后在slave中执行:"slave start;"来启动同步。&nbsp;<br />
当你幸福的时候，我不在，当我幸福的时候，你也不在&nbsp;<br />
<br />
change master to master_host='172.16.8.66',master_user='root',master_password='PASSWD',master_port=3306,master_log_file='mysql-bin.000006',master_log_pos=120;&nbsp;<br />
<div style="white-space:nowrap;">
	<br />
</div>