<p>
	MyISAM:这个是默认类型,它是基于传统的ISAM类型,ISAM是Indexed Sequential Access Method 
(有索引的顺序访问方法) 的缩写,它是存储记录和文件的标准方法.与其他存储引擎比较,MyISAM具有检查和修复表格的大多数工具. 
MyISAM表格可以被压缩,而且它们支持全文搜索.它们不是事务安全的,而且也不支持外键。如果事物回滚将造成不完全回滚，不具有原子性。如果执行大量的SELECT，MyISAM是更好的选择。
</p>
<p>
	<br />
InnoDB:这种类型是事务安全的.它与BDB类型具有相同的特性,它们还支持外键.InnoDB表格速度很快.具有比BDB还丰富的特性,因此如果需要一个事务安全的存储引擎,建议使用它.如果你的数据执行大量的INSERT或UPDATE,出于性能方面的考虑，应该使用InnoDB表,
</p>
<p>
	对于支持事物的InnoDB类型的标，影响速度的主要原因是AUTOCOMMIT默认设置是打开的，而且程序没有显式调用BEGIN 
开始事务，导致每插入一条都自动Commit，严重影响了速度。可以在执行sql前调用begin，多条sql形成一个事物（即使autocommit打开也可以），将大大提高性能。<br />
1. 4.0以上mysqld都支持事务，包括非max版本。3.23的需要max版本mysqld才能支持事务。
</p>
<p>
	2. 创建表时如果不指定type则默认为myisam，不支持事务。<br />
可以用 show create table tablename 命令看表的类型。
</p>
<p>
	2.1 对不支持事务的表做start/commit操作没有任何效果，在执行commit前已经提交，测试：<br />
执行一个msyql：<br />
use test;<br />
drop table if exists tn;<br />
create table tn (a varchar(10)) type=myisam;<br />
drop table if exists ty;<br />
create table ty (a varchar(10)) type=innodb;
</p>
<p>
	begin;<br />
insert into tn values(’a');<br />
insert into ty values(’a');<br />
select * from tn;<br />
select * from ty;<br />
都能看到一条记录
</p>
<p>
	执行另一个mysql：<br />
use test;<br />
select * from tn;<br />
select * from ty;<br />
只有tn能看到一条记录<br />
然后在另一边<br />
commit;<br />
才都能看到记录。
</p>
<p>
	3. 可以执行以下命令来切换非事务表到事务（数据不会丢失），innodb表比myisam表更安全：<br />
alter table tablename type=innodb;
</p>
<p>
	3.1 innodb表不能用repair table命令和myisamchk -r table_name<br />
但可以用check table，以及mysqlcheck [OPTIONS] database [tables]
</p>
<p>
	4. 启动mysql<a href="http://lib.csdn.net/base/mysql" class="replace_word" title="MySQL知识库" target="_blank" style="color:#df3434;font-weight:bold;">数据库</a>的命令行中添加了以下参数可以使新发布的mysql数据表都默认为使用事务（<br />
只影响到create语句。）<br />
–default-table-type=InnoDB
</p>
<p>
	测试命令：<br />
use test;<br />
drop table if exists tn;<br />
create table tn (a varchar(10));<br />
show create table tn;
</p>
<p>
	5. 临时改变默认表类型可以用：<br />
set table_type=InnoDB;<br />
show variables like ‘table_type’;<br />
或：<br />
c:mysqlbinmysqld-max-nt –standalone –default-table-type=InnoDB
</p>
<p>
	于mysql来说，最具有代表性的表存储引擎就是InnoDB和MyISAM.两者之间最主要的区别就是是否进行：是否进行外键的数据完整性检查。
</p>
<p>
	InnoDB 存储引擎支持对外键约束的检查功能，这些约束包括 delete,update,cascade(这个具体是什么含义，留待以后补充) 。
</p>
<p>
	外键约束检查（外键增强）的好处或者优点是：
</p>
<p>
	1&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 如果关联设计恰当，可以使程序员更难将数据不一致性引入数据库
</p>
<p>
	2&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 数据库服务器具有集中式约束检查功能，就可以不必再应用程序一侧对数据进行该类检查，从而避免了不同的引用程序使用不同的方式去检查约束。
</p>
<p>
	3&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 使用级联更新和删除，简化了应用程序代码
</p>
<p>
	4&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 设计欠当的关联，有助于使用文档的方式记录表间的关系
</p>
<p>
	但是以上的好处，需要数据库服务器为执行此类检查花费额外的开销，增加了数据库服务器的负担，进而影响数据库的性能。
</p>
<p>
	如果在表中不需要外键，也想避免引用完整性的检查，则可以选择使用MyISAM存储
</p>
<p>
	引擎。对于那些只有insert和select的应用程序，选择MyISAM会获得更好的性能。但是如果使用MyISAM引擎时，如果有外键关联，那么需要再应用程序级的层面上处理这类关联，使得数据的完整性获得保证。
</p>
<p>
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; DBA（数据库管理员）要创建拓扑关联，这样会导致恢复单个表变的困难（加载依赖其他表的表时，MySQL允许你临时禁止外键检查，从而降低了该难度）。对于存在外键的表的，需要注意这个问题。
</p>