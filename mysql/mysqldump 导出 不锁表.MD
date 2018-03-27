<p>
	&nbsp;mysqldump -h localhost -uroot -p testdb --lock-tables=false &gt;testdb.sql<span style="color:#333333;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#F5F5F5;"></span> 
</p>
<p>
	<br />
</p>
<p>
	<span style="color:#333333;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#F5F5F5;"><span style="white-space:normal;">&nbsp;mysqldump -h localhost -uroot -p testdb --lock-tables=false |gzip &gt;testdb.sql</span>.gzip<br />
</span> 
</p>
<p>
	<span style="color:#333333;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#F5F5F5;"><br />
</span> 
</p>
<p>
	<span style="color:#333333;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#F5F5F5;">./mysqldump -hlocalhost -uroot -p -q -e -t&nbsp; testdb testtable-lock-tables=false<br />
</span> 
</p>
<p>
	<span style="color:#333333;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#F5F5F5;"><br />
</span>
</p>
<p>
	<span style="color:#333333;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#F5F5F5;"><span style="font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">导出存储过程以及自定义函数。</span><br />
</span>
</p>
<p>
	<span style="color:#333333;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#F5F5F5;"><span style="font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">mysqldump&nbsp;&nbsp;-uroot&nbsp;-p&nbsp;--host=localhost&nbsp;--all-databases&nbsp;--routines&nbsp;</span><strong style="font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">--triggers</strong><br />
</span>
</p>
<p>
	<span style="color:#333333;font-family:'Helvetica, Tahoma, Arial, sans-serif';"><span style="font-size:14px;background-color:#F5F5F5;">详细介绍</span></span>
</p>
<p>
	<span style="color:#333333;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#F5F5F5;">https://www.cnblogs.com/qq78292959/p/3637135.html<br />
</span>
</p>