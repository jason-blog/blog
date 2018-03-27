<p>
	http://www.ttlsa.com/mysql/pt-online-schema-change-mysql-structure/
</p>
<p>
	<br />
</p>
<p>
	<br />
</p>
<p>
	pt-online-schema-change --user=root --password=123123 --host=localhost&nbsp; --alter "ADD INDEX index_xx&nbsp;( `test` ,`test`) USING BTREE;" D=test,t=abc --print --execute --preserve-triggers
</p>