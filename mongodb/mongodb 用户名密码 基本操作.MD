添加用户<br />
<p>
	db.createUser({user:"root",pwd:"root123",roles:["userAdminAnyDatabase"]})
</p>
<p>
	<span style="color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">db.createUser({user:'root',pwd:'root',roles:[{ "role" : "root", "db" : "admin" }]});</span>
</p>
<p>
	db.createUser({user:"testuser",pwd:"testpass",roles:["readWrite"]})
</p>
<p>
	修改密码
</p>
<p>
	<span style="margin:0px;padding:0px;border:0px;outline:0px;vertical-align:baseline;background:0px 0px #FFFFFF;font-family:Consolas, &quot;white-space:normal;">db.changeUserPassword(</span><span class="string" style="margin:0px;padding:0px;border:0px;outline:0px;vertical-align:baseline;background:0px 0px #FFFFFF;color:#0000FF;font-family:Consolas, &quot;white-space:normal;">'tank2'</span><span style="margin:0px;padding:0px;border:0px;outline:0px;vertical-align:baseline;background:0px 0px #FFFFFF;font-family:Consolas, &quot;white-space:normal;">,</span><span class="string" style="margin:0px;padding:0px;border:0px;outline:0px;vertical-align:baseline;background:0px 0px #FFFFFF;color:#0000FF;font-family:Consolas, &quot;white-space:normal;">'test'</span><span style="margin:0px;padding:0px;border:0px;outline:0px;vertical-align:baseline;background:0px 0px #FFFFFF;font-family:Consolas, &quot;white-space:normal;">);&nbsp;&nbsp;</span> 
</p>
<br />
角色说明：&nbsp;<br />
Read：允许用户读取指定数据库&nbsp;<br />
readWrite：允许用户读写指定数据库&nbsp;<br />
dbAdmin：允许用户在指定数据库中执行管理函数，如索引创建、删除，查看统计或访问system.profile&nbsp;<br />
userAdmin：允许用户向system.users集合写入，可以找指定数据库里创建、删除和管理用户&nbsp;<br />
clusterAdmin：只在admin数据库中可用，赋予用户所有分片和复制集相关函数的管理权限。&nbsp;<br />
readAnyDatabase：只在admin数据库中可用，赋予用户所有数据库的读权限&nbsp;<br />
readWriteAnyDatabase：只在admin数据库中可用，赋予用户所有数据库的读写权限&nbsp;<br />
userAdminAnyDatabase：只在admin数据库中可用，赋予用户所有数据库的userAdmin权限&nbsp;<br />
dbAdminAnyDatabase：只在admin数据库中可用，赋予用户所有数据库的dbAdmin权限。&nbsp;<br />
root：只在admin数据库中可用。超级账号，超级权限<br />
<br />
删除用户<br />
<p>
	db.dropUser('test')
</p>
<p>
	<br />
</p>
mongod --dbpath [数据存放path]&nbsp; // 基本命令<br />
mongod --dbpath [数据存放path] --auth //开启授权启动<br />
<br />
//连接远程数据库<br />
mongo 192.168.1.200:27017/test -u user -p password<br />
<br />