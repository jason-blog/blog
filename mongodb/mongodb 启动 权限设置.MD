<br />
&nbsp;./mongod --dbpath=/root/Mango/mongodb-linux-x86_64-3.2.9/data --logpath=/root/Mango/mongodb-linux-x86_64-3.2.9/mongo.log --logappend&amp;<br />
&nbsp;<br />
&nbsp;./mongod -f /root/Mango/mongodb-linux-x86_64-3.2.9/mongo.conf --auth&amp;<br />
<br />
<br />
======================mongo.conf 内容===================<br />
#默认端口27017<br />
port=10001&nbsp;<br />
dbpath=/root/Mango/mongodb-linux-x86_64-3.2.9/data<br />
logpath=/root/Mango/mongodb-linux-x86_64-3.2.9/mongo.log<br />
logappend=true<br />
<br />
=========================================================== &nbsp;<br />
&nbsp;&nbsp;<br />
&nbsp; 链接<br />
&nbsp; &nbsp;./mongo --port=10001<br />
&nbsp;&nbsp;<br />
==================权限===================<br />
<br />
<br />
<br />
use admin<br />
db.createUser({ user: "root",pwd: "spade9.inc",roles:[{roles: "userAdminAnyDatabase",db: "admin"}]})<br />
&nbsp;&nbsp;<br />
&nbsp; &nbsp;<br />
&nbsp; &nbsp;<br />
&nbsp; &nbsp;&nbsp;<br />
db.createUser( { "user" : "root","pwd": "spade9.inc","customData" : { employeeId: 12345 },"roles" : [ { role: "clusterAdmin", db: "admin" },{ role: "readAnyDatabase", db: "admin" }, "readWrite"] }, { w: "majority" , wtimeout: 5000 } )<br />
<br />
#对单独数据库权限<br />
db.createUser( { "user" : "wocao","pwd": "spade9.inc","customData" : { employeeId: 12345 },"roles" : [ { role: "readWrite", db: "wocao" }, "readWrite"] }, { w: "majority" , wtimeout: 5000 } )<br />
<br />
<br />
mongo --port=10001 -u root -p spade9.inc --authenticationDatabase admin<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br />
use admin<br />
db.auth('root','spade9.inc'); &nbsp; &nbsp;<br />
<br />
show dbs;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br />
&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
<br />
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp;&nbsp;<br />
<br />
==================权限===================<br />
&nbsp;&nbsp;<br />
&nbsp;&nbsp;<br />