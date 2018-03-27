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
=================================================================== &nbsp;<br />
<br />
一、安装PHP的MongoDB数据库扩展（在Web服务器192.168.21.127上操作）<br />
<br />
下载地址：http://pecl.php.net/get/mongo-1.5.1.tgz<br />
<br />
上传mongo-1.5.1.tgz到/usr/local/src目录<br />
<br />
tar &nbsp;zxvf mongo-1.5.1.tgz &nbsp;#解压<br />
<br />
cd mongo-1.5.1<br />
<br />
/usr/local/php/bin/phpize<br />
<br />
./configure --with-php-config=/usr/local/php/bin/php-config<br />
<br />
make &nbsp;#编译<br />
<br />
make install &nbsp;#安装，完成之后出现下面的界面<br />
<br />
/usr/local/php/lib/php/extensions/no-debug-non-zts-20090626/<br />
<br />
vi /usr/local/php/etc/php.ini &nbsp;#编辑，在最后一行添加下面的代码<br />
<br />
extension="mongo.so"<br />
<br />
:wq! #保存退出<br />
<br />
service php-fpm reload &nbsp;#重新加载php-fpm<br />
<br />
在站点根目录下添加php测试页面<br />
<br />
vi /usr/local/nginx/html/phpinfo.php &nbsp;#编辑<br />
<br />
&lt;?php<br />
<br />
phpinfo();<br />
<br />
?&gt;<br />
<br />
:wq! &nbsp;#保存退出<br />
=================================================================== &nbsp;<br />
<br />
<br />
<br />
<br />
php 链接<br />
<br />
<br />
六，php客户端连接<br />
1， 推荐方法一<br />
<br />
$mongo = new Mongo(); &nbsp;<br />
&nbsp;<br />
$db = $mongo-&gt;selectDB('tank'); &nbsp;//切换到tank数据库&nbsp;<br />
&nbsp;<br />
$db-&gt;authenticate("tank3", "test"); &nbsp;//认证<br />
&nbsp;<br />
$users= $db-&gt;selectCollection("users"); //选取users表<br />
&nbsp;<br />
$cursor = $users-&gt;find(); &nbsp;//读取数据<br />
&nbsp;<br />
foreach ($cursor as $id =&gt; $value) {<br />
&nbsp; echo "$id: "; print_r($value); echo "&lt;br&gt;";<br />
}<br />
这种方式比较好理解，根命令行下的操作过程差不多。<br />
<br />
<br />
<br />
2，推荐方法二<br />
<br />
$mongo = new Mongo("mongodb://tank3:test@127.0.0.1:27017/tank"); &nbsp;//认证用户，这里的数据库，只启认证作用<br />
&nbsp;<br />
$db = $mongo-&gt;selectDB('tank'); //选取数据库<br />
&nbsp;<br />
$users= $db-&gt;selectCollection("users");<br />
&nbsp;<br />
$cursor = $users-&gt;find();<br />
&nbsp;<br />
foreach ($cursor as $id =&gt; $value) {<br />
&nbsp; echo "$id: "; print_r($value); echo "&lt;br&gt;";<br />
}<br />