linux刷新dns的缓存方法是：

sudo /etc/init.d/nscd restart
如果发现提示命令找不到：

sudo: /etc/init.d/nscd: command not found
后来发现是需要先安装nscd包：

sudo apt-get install nscd
最暴力的方法刷dns，重启网络：

sudo /etc/init.d/networking restart
