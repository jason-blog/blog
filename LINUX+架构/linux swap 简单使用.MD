&nbsp;free -m 查看使用情况<br />
&nbsp;swapon -s 验证状态<br />
&nbsp;<br />
&nbsp;mkswap /home/swap<br />
&nbsp;swapon /home/swap<br />
&nbsp;&nbsp;<br />
&nbsp;swapoff -v /dev/sda1 //关闭swap分区swapoff -a 关闭所有<br />
&nbsp;<br />
&nbsp;<br />
&nbsp;为避免重启后swapfile生效，可以将启用swap的代码加入启动文件中，对于ubuntu server，编辑/etc/rc.local文件，加入以下内容（具体文件路径自定）：<br />
<br />
swapon /srv/SWAPFILE<br />
&nbsp;<br />
&nbsp;　2.3 设置扩展的swap分区为自动挂载<br />
不过当计算机重启了以后，发现swap还是原来那么大，新的swap没有自动启动，还要手动启动。<br />
那我们需要修改/etc/fstab文件，增加如下一行如下自动挂载命令行<br />
/home/swap swap swap defaults 0 0<br />
<br />
<br />
要删除交换文件：<br />
在 shell 提示下以根用户身份执行以下命令来禁用交换文件(这里的 /swapfile 是交换文件)：swapoff /swapfile<br />
从 /etc/fstab 中删除该项目。删除实际文件：rm /swapfile。 这样，我们就完成了删除Swap space的操作。<br />
<br />
<br />
swappiness<br />
<br />
1.查看你的系统里面的swappiness<br />
$ cat /proc/sys/vm/swappiness<br />
不出意外的话，你应该看到是 60<br />
2.修改swappiness值为10<br />
$ sudo sysctl vm.swappiness=10<br />
但是这只是临时性的修改，在你重启系统后会恢复默认的60，为长治久安，还要更进一步：<br />
$ sudo gedit /etc/sysctl.conf<br />
在这个文档的最后加上这样一行:<br />
vm.swappiness=10<br />
然后保存，重启。ok，你的设置就生效了。<br />