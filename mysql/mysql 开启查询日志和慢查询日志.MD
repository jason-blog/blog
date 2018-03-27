<pre class="prettyprint lang-py linenums">mysql 5.6+


#开启 mysql执行log
general_log=ON
general_log_file=/home/mysql/mysql.log

#开启慢查询log
long_query_time=1
slow_query_log=1
slow_query_log_file="/home/mysql/log-slow-queries.log"

mysql5.0+
#查询日志
log=mysqlquery.log
#慢查询日志
#slow-query-log=1
#long_query_time = 2 
#log-slow-queries= "slow.log"</pre>
<p>
	<br />
</p>