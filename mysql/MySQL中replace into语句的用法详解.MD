<p style="margin-top:0px;margin-bottom:0px;padding:5px 0px;font-size:14px;font-family:tahoma, arial, 宋体;white-space:normal;background-color:#FFFFFF;">
	<br />
</p>
<pre class="prettyprint lang-js linenums">在向表中插入数据的时候，经常遇到这样的情况：
1、首先判断数据是否存在；
2、如果不存在，则插入；
3、如果存在，则更新。
 
在 SQL Server 中可以这样写：
复制代码代码如下:

if not exists (select 1 from table where id = 1) insert into table(id, update_time) values(1, getdate()) else update table set update_time = getdate() where id = 1

在MySQL 中也可以先select，判断是否存在，存在则 update 否则 insert
但在MySQL 中有更简单的方法，使用 replace into关键字
复制代码代码如下:
replace into table(id, update_time) values(1, now());

或
复制代码代码如下:

replace into table(id, update_time) select 1, now();

replace into 跟 insert 功能类似，不同点在于：replace into 首先尝试插入数据到表中。
1、如果发现表中已经有此行数据（根据主键或者唯一索引判断）则先删除此行数据，然后插入新的数据。
2、 否则，直接插入新数据。
要注意的是：插入数据的表必须有主键或者是唯一索引！否则的话，replace into 会直接插入数据，这将导致表中出现重复的数据。
 
MySQL中replace into有三种写法：
复制代码代码如下:

1. replace into table(col, ...) values(...)
2. replace into table(col, ...) select ...
3. replace into table set col=value, ...

前两种形式用的多些。其中 “into” 关键字可以省略，不过最好加上 “into”，这样意思更加直观。
另外，对于那些没有给予值的列，MySQL 将自动为这些列赋上默认值。
 
可惜的是replace不支持update某些特性，也就不能直接当作update使用：
常见update写法：update table set col=col+1 where id=1;
使用replace into不支持这样的写法：replace into table set col=col+1,id=1;
1、首先判断数据是否存在；（没问题）
2、如果不存在，则插入；（没问题）
3、如果存在，某字段值在原来的基础上加上或减去某个数，如加一操作。（不支持）</pre>
<p>
	<br />
</p>