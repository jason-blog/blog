&nbsp;查看所有数据库<br />
&nbsp;show dbs<br />
&nbsp;<br />
&nbsp;删除数据库<br />
&nbsp;db.dropDatabase()<br />
&nbsp;<br />
&nbsp;查看所有集合<br />
<br />
============================== 查询 ========================================<br />
use wocao<br />
<br />
show collections;<br />
<br />
db.col.insert({title: 'MongoDB 教程'})<br />
<br />
db.col.find()<br />
<br />
db.col.find().limit(5);<br />
<br />
如果你需要以易读的方式来读取数据，可以使用 pretty() 方法，语法格式如下：<br />
&gt;db.col.find().pretty()<br />
<br />
等于	{&lt;key&gt;:&lt;value&gt;}	db.col.find({"by":"菜鸟教程"}).pretty()	where by = '菜鸟教程'<br />
小于	{&lt;key&gt;:{$lt:&lt;value&gt;}}	db.col.find({"likes":{$lt:50}}).pretty()	where likes &lt; 50<br />
小于或等于	{&lt;key&gt;:{$lte:&lt;value&gt;}}	db.col.find({"likes":{$lte:50}}).pretty()	where likes &lt;= 50<br />
大于	{&lt;key&gt;:{$gt:&lt;value&gt;}}	db.col.find({"likes":{$gt:50}}).pretty()	where likes &gt; 50<br />
大于或等于	{&lt;key&gt;:{$gte:&lt;value&gt;}}	db.col.find({"likes":{$gte:50}}).pretty()	where likes &gt;= 50<br />
不等于	{&lt;key&gt;:{$ne:&lt;value&gt;}}	db.col.find({"likes":{$ne:50}}).pretty()	where likes != 50<br />
<br />
<br />
============================== 修改 ==========================================<br />
<br />
&gt;db.col.update({'title':'MongoDB'},{$set:{'title':'MongoDB'}},{multi:true})<br />
<br />
<br />
只更新第一条记录：<br />
db.col.update( { "count" : { $gt : 1 } } , { $set : { "test2" : "OK"} } );<br />
全部更新：<br />
db.col.update( { "count" : { $gt : 3 } } , { $set : { "test2" : "OK"} },false,true );<br />
只添加第一条：<br />
db.col.update( { "count" : { $gt : 4 } } , { $set : { "test5" : "OK"} },true,false );<br />
全部添加加进去:<br />
db.col.update( { "count" : { $gt : 5 } } , { $set : { "test5" : "OK"} },true,true );<br />
全部更新：<br />
db.col.update( { "count" : { $gt : 15 } } , { $inc : { "count" : 1} },false,true );<br />
只更新第一条记录：<br />
db.col.update( { "count" : { $gt : 10 } } , { $inc : { "count" : 1} },false,false );<br />
<br />
========================================== 删除 ==========================================<br />
&gt;db.col.remove({'title':'MongoDB'})<br />
删除集合<br />
&gt;db.col.drop()<br />
<br />
http://www.runoob.com/mongodb/mongodb-operators.html<br />
<br />
db.help(); 查看帮助<br />
<br />
http://www.jb51.net/article/48217.htm<br />
<br />
副本集实验<br />
http://blog.csdn.net/cscscscsc/article/details/51237055<br />