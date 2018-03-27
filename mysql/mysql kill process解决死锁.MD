<p>
	<br />
</p>
<h2 style="margin:2px 0px 3px;padding:0px;font-size:12px;line-height:14.4px;overflow:hidden;">
	<p>
		<br />
	</p>
	<p>
		mysql kill process解决死锁 - [mysql]
	</p>
	<p>
		Tag：mysql processlist 死锁
	</p>
	<p>
		版权声明：转载时请以超链接形式标明文章原始出处和作者信息及本声明
	</p>
	<p>
		http://www.blogbus.com/ri0day-logs/59186177.html
	</p>
	<p>
		<br />
	</p>
	<p>
		mysql使用myisam的时候锁表比较多，尤其有慢查询的时候，造成死锁.这时需要手动kill掉locked的process.使他释放.
	</p>
<br />
</h2>
<p>
	实例：
</p>
<p>
	<span style="font-family:Verdana, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">mysql&gt; show processlist;</span><br style="margin:0px;padding:0px;font-family:Verdana, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Verdana, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">+----+------+-----------+------+---------+------+-------+------------------+</span><br style="margin:0px;padding:0px;font-family:Verdana, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Verdana, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">| Id | User | Host&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | db&nbsp;&nbsp; | Command | Time | State | Info&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |</span><br style="margin:0px;padding:0px;font-family:Verdana, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Verdana, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">+----+------+-----------+------+---------+------+-------+------------------+</span><br style="margin:0px;padding:0px;font-family:Verdana, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Verdana, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">|&nbsp; 7 | root | localhost | yy&nbsp;&nbsp; | Sleep&nbsp;&nbsp; |&nbsp; 154 |&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | NULL&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |&nbsp;</span><br style="margin:0px;padding:0px;font-family:Verdana, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Verdana, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">|&nbsp; 8 | root | localhost | NULL | Query&nbsp;&nbsp; |&nbsp;&nbsp;&nbsp; 0 | NULL&nbsp; | show processlist |&nbsp;</span><br style="margin:0px;padding:0px;font-family:Verdana, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Verdana, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">+----+------+-----------+------+---------+------+-------+------------------+</span><br style="margin:0px;padding:0px;font-family:Verdana, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Verdana, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">2 rows in set (0.00 sec)</span><br style="margin:0px;padding:0px;font-family:Verdana, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;" />
<br style="margin:0px;padding:0px;font-family:Verdana, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Verdana, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">mysql&gt; kill 7</span>
</p>
<p>
	<br />
</p>