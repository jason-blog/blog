<p>
	这里说明，Ubuntu 中系统没有了RH系统中的 chkconfig 命令 ！
</p>
<p>
	<br />
</p>
<p>
	可用一些小工具来管理 Ubuntu 的启动选项：
</p>
<p>
	小工具 rcconf：
</p>
<p>
	#sudo apt-get rcconf
</p>
<p>
	#sudo apt-get install rcconf
</p>
<p>
	root 下运行: #sudo rcconf
</p>
<p>
	功能更全的工具：sysv-rc-conf
</p>
<p>
	#sudo apt-get update
</p>
<p>
	#sudo apt-get install sysv-rc-conf
</p>
<p>
	运行：#sudo sysv-rc-conf
</p>
<p>
	也可以直接加入启动程序，例如把 /etc/init.d/red5 加入到系统自动启动列表中：
</p>
<p>
	#sudo sysv-rc-conf red5 on
</p>
<p>
	其他使用方法见: google::Ubuntu::sysv-rc-conf 命令用法
</p>
<p>
	<br />
</p>
<p>
	也可以直接修改
</p>
<p>
	直接改 /etc/rc0.d ~ /etc/rc6.d 和 /etc/rcS.d 下的东西，S开头的表示启动，K开头的表示不启动，
</p>
<p>
	例如：想关闭 Red5 的开机自动启动，只需 #sudo mv /etc/rc2.d/S20red5 /etc/rc2.d/K20red5 就可以了。
</p>
<p>
	<br />
</p>
<p>
	Ubuntu自动启动程序
</p>
<p>
	<br />
</p>
<p>
	首 先，linux随机启动的服务程序都在/etc/init.d这个文件夹里，里面的文件全部都是脚本文件（脚本程序简单的说就是把要运行的程序写 到一个 文件里让系统能够按顺序执行，类似windows下的autorun.dat文件），另外在/etc这个文件夹里还有诸如名为rc1.d, rc2.d一直到rc6.d的文件夹，这些都是linux不同的runlevel，我们一般进入的X windows多用户的运行级别是第5级，也就是rc5.d，在这个文件夹下的脚本文件就是运行第5级时要随机启动的服务程序。需要注意的是，在每个rc (1-6).d文件夹下的文件其实都是/etc/init.d文件夹下的文件的一个软连接（类似windows中的快捷方式），也就是说，在 /etc/init.d文件夹下是全部的服务程序，而每个rc(1-6).d只链接它自己启动需要的相应的服务程序！
</p>
<p>
	<br />
</p>
<p>
	要 启动scim (某一程序)，我们首先要知道scim程序在哪里，用locate命令可以找到，scim在/usr/bin/scim这里，其中usr表 示是 属于用户的，bin在linux里表示可以执行的程序。这样，我就可以编写一个脚本程序，把它放到/etc/init.d里，然后在rc5.d里做一个相 应的软链接就可以了。
</p>
<p>
	<br />
</p>
<p>
	这个脚本其实很简单，就两行：
</p>
<p>
	<br />
</p>
<p>
	#!/bin/bash
</p>
<p>
	<br />
</p>
<p>
	/usr/bin/scim
</p>
<p>
	<br />
</p>
<p>
	第一行是声明用什么终端运行这个脚本，第二行就是要运行的命令。
</p>
<p>
	<br />
</p>
<p>
	还 需要注意的一点是，在rc5.d里，每个链接的名字都是以S或者K开头的，S开头的表示是系统启动是要随机启动的，K开头的是不随机启动的。这 样，你就可以知道，如果我要哪个服务随机启动，就把它名字第一个字母K改成S就可以了，当然，把S改成K后，这个服务就不能随机启动了。因此，我这个链接 还要起名为SXXX，这样系统才能让它随机启动。
</p>
<p>
	<br />
</p>
<p>
	在RH下，rc.local是默认启动的最后一个脚本文件，所以，
</p>
<p>
	如果你想要随机启动，还有一种方法就是在rc.local的尾部加入/usr/bin/scim，这样就可以了。
</p>
<p>
	Linux 自动启动程序
</p>
<p>
	<br />
</p>
<p>
	1．开机启动时自动运行程序
</p>
<p>
	<br />
</p>
<p>
	Linux 加载后, 它将初始化硬件和设备驱动, 然后运行第一个进程init。init根据配置文件继续引导过程，启动其它进程。通常情况下，修改放置在 /etc/rc或 /etc/rc.d 或 /etc/rc?.d 目录下的脚本文件，可以使init自动启动其它程序。例如：编辑 /etc/rc.d/rc.local 文件(该文件通常是系统最后启动的脚本)，在文件最末加上一行“xinit”或“startx”，可以在开机启动后直接进入X－Window。
</p>
<p>
	<br />
</p>
<p>
	2．登录时自动运行程序
</p>
<p>
	<br />
</p>
<p>
	用 户登录时，bash首先自动执行系统管理员建立的全局登录script ：/ect/profile。然后bash在用户起始目录下按顺序查找三个特殊文件中的一个：/.bash_profile、/.bash_login、 /.profile，但只执行最先找到的一个。
</p>
<p>
	因此，只需根据实际需要在上述文件中加入命令就可以实现用户登录时自动运行某些程序（类似于DOS下的Autoexec.bat）。
</p>
<p>
	<br />
</p>
<p>
	3．退出登录时自动运行程序
</p>
<p>
	<br />
</p>
<p>
	退出登录时，bash自动执行个人的退出登录脚本/.bash_logout。例如，在/.bash_logout中加入命令“tar －cvzf c.source.tgz ＊.c”，则在每次退出登录时自动执行 “tar” 命令备份 ＊.c 文件。
</p>
<p>
	<br />
</p>
<p>
	4．定期自动运行程序
</p>
<p>
	<br />
</p>
<p>
	Linux有一个称为crond的守护程序，主要功能是周期性地检查 /var/spool/cron目录下的一组命令文件的内容，并在设定的时间执行这些文件中的命令。用户可以通过crontab 命令来建立、修改、删除这些命令文件。
</p>
<p>
	<br />
</p>
<p>
	例如，建立文件crondFile，内容为“00 9 23 Jan ＊ HappyBirthday”，运行“crontab cronFile”命令后，每当元月23日上午9:00系统自动执行“HappyBirthday”的程序（“＊”表示不管当天是星期几）。
</p>
<p>
	<br />
</p>
<p>
	5．定时自动运行程序一次
</p>
<p>
	<br />
</p>
<p>
	定时执行命令at 与crond 类似（但它只执行一次）：命令在给定的时间执行，但不自动重复。at命令的一般格式为：at [ －f file ] time ，在指定的时间执行file文件中所给出的所有命令。也可直接从键盘输入命令：
</p>
<p>
	<br />
</p>
<p>
	＄ at 12:00
</p>
<p>
	at&gt;mailto Roger －s ″Have a lunch″ &lt; plan.txt
</p>
<p>
	at&gt;Ctr－D
</p>
<p>
	Job 1 at 2000－11－09 12:00
</p>
<p>
	2000－11－09 12:00时候自动发一标题为“Have a lunch”，内容为plan.txt文件内容的邮件给Roger。?9 12:00
</p>
<p>
	2000－11－09 12:00时候自动发一标题为“Have a lunch”，内容为plan.txt文件内容的邮件给Roger。er。ger。er。
</p>
<p>
	<br />
</p>
<p>
	Ubuntu 开机自动挂载windows分区
</p>
<p>
	<br />
</p>
<p>
	要挂载NTFS格式分区，需要NTFS-3g这个软件。它短小精悍，而且功能强大。
</p>
<p>
	NTFS-3g是一个开源软件，它支持在Windows下面读写NTFS格式的分区。它非常的快速，同时也很安全。它支持Windows 2000、XP和2003，并且支持所有的符合POSIX标准的磁盘操作。
</p>
<p>
	<br />
</p>
<p>
	首先要编辑sources.list
</p>
<p>
	#sudo gedit /etc/apt/sources.list
</p>
<p>
	<br />
</p>
<p>
	Ubuntu Drapper添加：
</p>
<p>
	deb http://givre.cabspace.com/ubuntu/ dapper main main-all
</p>
<p>
	deb http://ntfs-3g.sitesweetsite.info/ubuntu/ dapper main main-all
</p>
<p>
	deb http://flomertens.keo.in/ubuntu/ dapper main main-all
</p>
<p>
	<br />
</p>
<p>
	Ubuntu Edgy添加：
</p>
<p>
	deb http://givre.cabspace.com/ubuntu/ edgy main
</p>
<p>
	deb http://ntfs-3g.sitesweetsite.info/ubuntu/ edgy main
</p>
<p>
	deb http://flomertens.keo.in/ubuntu/ edgy main
</p>
<p>
	<br />
</p>
<p>
	同时必须导入GPG-Key，可以这样：
</p>
<p>
	#wget http://flomertens.keo.in/ubuntu/givre_key.asc -O- | sudo apt-key add -
</p>
<p>
	#wget http://givre.cabspace.com/ubuntu/givre_key.asc -O- | sudo apt-key add -
</p>
<p>
	<br />
</p>
<p>
	现在更新一下源：
</p>
<p>
	#sudo aptitude update
</p>
<p>
	<br />
</p>
<p>
	正式安装
</p>
<p>
	<br />
</p>
<p>
	在“终端”下面运行：
</p>
<p>
	#sudo apt-get install ntfs-3g
</p>
<p>
	<br />
</p>
<p>
	配置NTFS-3g
</p>
<p>
	<br />
</p>
<p>
	首先看一些硬盘分区的分区类型
</p>
<p>
	#sudo fdisk -l
</p>
<p>
	<br />
</p>
<p>
	现在就可以修改 /etc/fstab，来让Ubuntu启动的时候自动挂载NTFS分区了。但是首先请备份一下这个文件：
</p>
<p>
	#sudo cp /etc/fstab /etc/fstab.bak
</p>
<p>
	<br />
</p>
<p>
	建立挂载点，譬如挂载在 /media/windows 下面
</p>
<p>
	#sudo mkdir /media/windows
</p>
<p>
	<br />
</p>
<p>
	现在可以在 /etc/fstab 的后面添加
</p>
<p>
	/dev/hda1 /media/ ntfs-3g defaults,locale=zh_CN.utf8 0 0
</p>
<p>
	根据自己的情况进行修改。
</p>
<p>
	<br />
</p>
<p>
	一些示例
</p>
<p>
	<br />
</p>
<p>
	挂载 /dev/hda3
</p>
<p>
	添加 /dev/hda3 /media/windows ntfs-3g ro,locale=zh_CN.utf8,uid=1000 0 0
</p>
<p>
	<br />
</p>
<p>
	关于自己的locale
</p>
<p>
	<br />
</p>
<p>
	可以用下面的命令查看所有的locale
</p>
<p>
	#locale -a
</p>
<p>
	<br />
</p>
<p>
	如果不想重新启动，就可以
</p>
<p>
	#sudo umount -a
</p>
<p>
	#sudo mount -a
</p>
<p>
	<br />
</p>
<p>
	最后一个挂载FAT分区的命令
</p>
<p>
	#sudo mount /dev/hda3 /media/windows/ -t vfat -o iocharset=utf8,umask=000
</p>
<p>
	<br />
</p>
<p>
	当然可以在/etc/fstab里面添加
</p>
<p>
	/dev/hda3 /media/windows vfat iocharset=utf8,umask=000 0 0
</p>
<p>
	<br />
</p>
<p>
	Openfire随着Ubuntu自动启动
</p>
<p>
	<br />
</p>
<p>
	openfire缺省情况下，是不随机启动的。为了解决每次都要手工启动的麻烦，我编写了一个脚本，放在/etc/init.d目录里面
</p>
<p>
	#sudo vim /etc/init.d/openfire
</p>
<p>
	内容如下：
</p>
<p>
	<br />
</p>
<p>
	#!/bin/sh
</p>
<p>
	<br />
</p>
<p>
	openfire_start(){
</p>
<p>
	/etc/openfire/bin/openfire start
</p>
<p>
	}
</p>
<p>
	<br />
</p>
<p>
	openfire_stop(){
</p>
<p>
	/etc/openfire/bin/openfire stop
</p>
<p>
	}
</p>
<p>
	<br />
</p>
<p>
	case $1 in
</p>
<p>
	start)
</p>
<p>
	openfire_start
</p>
<p>
	;;
</p>
<p>
	stop)
</p>
<p>
	openfrie_stop
</p>
<p>
	;;
</p>
<p>
	*)
</p>
<p>
	echo ‘Usage:openfire start|stop’
</p>
<p>
	;;
</p>
<p>
	esac
</p>