//导出<br />
mysqldump -u root -p DB table &gt;/home/table.sql<br />
<br />
//导入<br />
<br />
<br />
mysql&gt; use mycms<br />
Database changed<br />
mysql&gt; source testdb.sql;<br />
<br />
<br />
<br />
<br />
mysqldump -u用户名 -p密码 -h主机 数据库 &lt; 路径<br />
<br />
<br />
mysql -uroot -p1234 db1 &lt; c:\a.txt<br />
<br />
<br />