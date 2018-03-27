<p>
	alter table tablename add column is_third int(5) default 1 COMMENT 'commit' &nbsp;;
</p>
<p>
	<br />
</p>
<p>
	<br />
</p>
<p>
	<br />
1.增加一个字段<br />
alter table user add COLUMN new1 VARCHAR(20) DEFAULT NULL COMMENT '这是表的注释'; &nbsp;//增加一个字段，默认为空<br />
alter table user add COLUMN new2 VARCHAR(20) NOT NULL; &nbsp;//增加一个字段，默认不能为空 &nbsp;www.2cto.com &nbsp;<br />
&nbsp;<br />
2.删除一个字段<br />
alter table user DROP COLUMN new2; 　 //删除一个字段<br />
&nbsp;<br />
3.修改一个字段<br />
alter table user MODIFY new1 VARCHAR(10); 　//修改一个字段的类型<br />
&nbsp;<br />
alter table user CHANGE new1 new4 int;　 //修改一个字段的名称，此时一定要重新指定该字段的类型<br />
</p>