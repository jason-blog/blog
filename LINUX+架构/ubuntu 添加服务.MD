Ubuntu也提供了另外一个简单的命令来实现管理。但首先服务必须已在/etc/init.d目录中存在。如：<br />
添加一个服务: sudo update-rc.d ServiceName defaults<br />
删除一个服务: sudo update-rc.d ServiceName remove<br />
<br />
查看所有服务<br />
service --status-all<br />
<br />