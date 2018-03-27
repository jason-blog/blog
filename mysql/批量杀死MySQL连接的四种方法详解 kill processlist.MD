<p>
	通过information_schema.processlist表中的连接信息生成需要处理掉的MySQL连接的语句临时文件，然后执行临时文件中生成的指令。
</p>
<p>
	复制代码 代码如下:
</p>
<p>
	<br />
</p>
<p>
	mysql&gt; select concat('KILL ',id,';') from information_schema.processlist where user='root';
</p>
<p>
	+------------------------+
</p>
<p>
	| concat('KILL ',id,';') |
</p>
<p>
	+------------------------+
</p>
<p>
	| KILL 3101; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; |
</p>
<p>
	| KILL 2946; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; |
</p>
<p>
	+------------------------+
</p>
<p>
	2 rows in set (0.00 sec)
</p>
<p>
	<br />
</p>
<p>
	mysql&gt;select concat('KILL ',id,';') from information_schema.processlist where user='root' into outfile '/tmp/a.txt';
</p>
<p>
	Query OK, 2 rows affected (0.00 sec)
</p>
<p>
	<br />
</p>
<p>
	mysql&gt;source /tmp/a.txt;
</p>
<p>
	Query OK, 0 rows affected (0.00 sec)
</p>
<p>
	方法二
</p>
<p>
	杀掉当前所有的MySQL连接
</p>
<p>
	复制代码 代码如下:
</p>
<p>
	<br />
</p>
<p>
	mysqladmin -uroot -p processlist|awk -F "|" '{print $2}'|xargs -n 1 mysqladmin -uroot -p kill
</p>
<p>
	<br />
</p>
<p>
	杀掉指定用户运行的连接，这里为Mike
</p>
<p>
	复制代码 代码如下:
</p>
<p>
	<br />
</p>
<p>
	mysqladmin -uroot -p processlist|awk -F "|" '{if($3 == "Mike")print $2}'|xargs -n 1 mysqladmin -uroot -p kill
</p>
<p>
	<br />
</p>
<p>
	方法三
</p>
<p>
	通过SHEL脚本实现
</p>
<p>
	复制代码 代码如下:
</p>
<p>
	<br />
</p>
<p>
	#杀掉锁定的MySQL连接
</p>
<p>
	for id in `mysqladmin processlist|grep -i locked|awk '{print $1}'`
</p>
<p>
	do
</p>
<p>
	&nbsp; mysqladmin kill ${id}
</p>
<p>
	done
</p>
<p>
	<br />
</p>
<p>
	方法四
</p>
<p>
	通过Maatkit工具集中提供的mk-kill命令进行
</p>
<p>
	复制代码 代码如下:
</p>
<p>
	<br />
</p>
<p>
	#杀掉超过60秒的sql
</p>
<p>
	mk-kill -busy-time 60 -kill
</p>
<p>
	#如果你想先不杀，先看看有哪些sql运行超过60秒
</p>
<p>
	mk-kill -busy-time 60 -print
</p>
<p>
	#如果你想杀掉，同时输出杀掉了哪些进程
</p>
<p>
	mk-kill -busy-time 60 -print –kill
</p>
<p>
	mk-kill更多用法可参考：
</p>
<p>
	http://www.maatkit.org/doc/mk-kill.html
</p>