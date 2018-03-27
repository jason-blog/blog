<p>
	Linux为我们提供了两个用于文件copy的命令，一个是cp，一个是scp，但是他们略有不同。
</p>
<p>
	<br />
</p>
<p>
	cp --- 主要是用于在同一台电脑上，在不同的目录之间来回copy文件
</p>
<p>
	scp --- 主要是在不同的Linux系统之间来回copy文件
</p>
<p>
	<br />
</p>
<p>
	关于cp的具体用法：
</p>
<p>
	<br />
</p>
<p>
	命令基本格式：
</p>
<p>
	cp [OPTIONS] SOURCE DEST --- 从源路径copy文件到目的路径
</p>
<p>
	cp [OPTIONS] SOURCE... DIRECTORY --- 将多个源文件copy到指定的目录（多个源文件用空格分隔）
</p>
<p>
	<br />
</p>
<p>
	OPTIONS：
</p>
<p>
	-a same as -dpR 尽可能将源文件状态、权限等资料都照原装予以复制，并且是递归copy；
</p>
<p>
	-r 表示递归copy，若source中含有目录名，则将目录下之档案亦皆依序拷贝至目的地；
</p>
<p>
	-f 表示force，若目的地已经有相同档名的档案存在，则在复制前先予以删除再行复制；
</p>
<p>
	范例：
</p>
<p>
	1. 将档案 aaa 复制(已存在)，并命名为 bbb：
</p>
<p>
	cp aaa bbb
</p>
<p>
	2. 将所有的C语言程式拷贝至 Finished 子目录中：
</p>
<p>
	cp *.c Finished/
</p>
<p>
	<br />
</p>
<p>
	关于scp的具体用法：
</p>
<p>
	<br />
</p>
<p>
	不同的Linux之间copy文件常用有3种方法：
</p>
<p>
	<br />
</p>
<p>
	第一种就是ftp，也就是其中一台Linux安装ftp Server，这样可以在另外一台机器使用ftp的client程序来进行文件的copy。
</p>
<p>
	第二种方法就是采用samba服务，类似Windows文件copy 的方式来操作，比较简洁方便。
</p>
<p>
	第三种就是利用scp命令来进行文件复制。
</p>
<p>
	<br />
</p>
<p>
	<br />
</p>
<p>
	scp是有Security的文件copy，基于ssh登录。
</p>
<p>
	<br />
</p>
<p>
	命令基本格式：
</p>
<p>
	scp [OPTIONS] file_source file_target
</p>
<p>
	<br />
</p>
<p>
	<br />
</p>
<p>
	OPTIONS：
</p>
<p>
	-v 和大多数 linux 命令中的 -v 意思一样 , 用来显示进度 . 可以用来查看连接、认证、 或是配置错误
</p>
<p>
	-C 使能压缩选项
</p>
<p>
	-P 选择端口 . 注意 -p 已经被 rcp 使用
</p>
<p>
	<br />
</p>
<p>
	<br />
</p>
<p>
	从 本地 复制到 远程
</p>
<p>
	scp /home/daisy/full.tar.gz root@172.19.2.75:/home/root （然后会提示你输入另外那台172.19.2.75主机的root用户的登录密码，接着就开始copy了），复制目录加参数 -r 即可
</p>
<p>
	<br />
</p>
<p>
	从 远程 复制到 本地
</p>
<p>
	scp root@/172.19.2.75:/home/root/full.tar.gz /home/daisy/full.tar.gz
</p>
<p>
	<br />
</p>
<p>
	以下是补充：
</p>
<p>
	<br />
</p>
<p>
	命令：cp
</p>
<p>
	<br />
</p>
<p>
	使用权限：所有使用者
</p>
<p>
	<br />
</p>
<p>
	使用方式：
</p>
<p>
	<br />
</p>
<p>
	cp [options] source dest
</p>
<p>
	<br />
</p>
<p>
	cp [options] source... directory
</p>
<p>
	<br />
</p>
<p>
	说明：将一个档案拷贝至另一档案，或将数个档案拷贝至另一目录。
</p>
<p>
	<br />
</p>
<p>
	把计
</p>
<p>
	<br />
</p>
<p>
	-a 尽可能将档案状态、权限等资料都照原状予以复制。
</p>
<p>
	<br />
</p>
<p>
	-r 若 source 中含有目录名，则将目录下之档案亦皆依序拷贝至目的地。
</p>
<p>
	<br />
</p>
<p>
	-f 若目的地已经有相同档名的档案存在，则在复制前先予以删除再行复制。
</p>
<p>
	<br />
</p>
<p>
	范例：
</p>
<p>
	<br />
</p>
<p>
	将档案 aaa 复制(已存在)，并命名为 bbb :
</p>
<p>
	<br />
</p>
<p>
	cp aaa bbb
</p>
<p>
	<br />
</p>
<p>
	将所有的C语言程式拷贝至 Finished 子目录中 :
</p>
<p>
	<br />
</p>
<p>
	cp *.c Finished
</p>
<p>
	<br />
</p>
<p>
	命令：scp
</p>
<p>
	<br />
</p>
<p>
	不同的Linux之间copy文件常用有3种方法：
</p>
<p>
	<br />
</p>
<p>
	第一种就是ftp，也就是其中一台Linux安装ftp Server，这样可以另外一台使用ftp的client程序来进行文件的copy。
</p>
<p>
	<br />
</p>
<p>
	第二种方法就是采用samba服务，类似Windows文件copy 的方式来操作，比较简洁方便。
</p>
<p>
	<br />
</p>
<p>
	第三种就是利用scp命令来进行文件复制。
</p>
<p>
	<br />
</p>
<p>
	scp是有Security的文件copy，基于ssh登录。操作起来比较方便，比如要把当前一个文件copy到远程另外一台主机上，可以如下命令。
</p>
<p>
	<br />
</p>
<p>
	scp /home/daisy/full.tar.gz root@172.19.2.75:/home/root
</p>
<p>
	<br />
</p>
<p>
	然后会提示你输入另外那台172.19.2.75主机的root用户的登录密码，接着就开始copy了。
</p>
<p>
	<br />
</p>
<p>
	如果想反过来操作，把文件从远程主机copy到当前系统，也很简单。
</p>
<p>
	linux之cp/scp命令＋scp命令详解(转) - linmaogan - 独木★不成林scp root@/full.tar.gz 172.19.2.75:/home/root/full.tar.gz home/daisy/full.tar.gz
</p>
<p>
	<br />
</p>
<p>
	linux 的 scp 命令 可以 在 linux 之间复制 文件 和 目录；
</p>
<p>
	<br />
</p>
<p>
	==================
</p>
<p>
	scp 命令
</p>
<p>
	==================
</p>
<p>
	scp 可以在 2个 linux 主机间复制文件；
</p>
<p>
	<br />
</p>
<p>
	命令基本格式：
</p>
<p>
	scp [可选参数] file_source file_target
</p>
<p>
	<br />
</p>
<p>
	======
</p>
<p>
	从 本地 复制到 远程
</p>
<p>
	======
</p>
<p>
	* 复制文件：
</p>
<p>
	* 命令格式：
</p>
<p>
	scp local_file remote_username@remote_ip:remote_folder
</p>
<p>
	或者
</p>
<p>
	scp local_file remote_username@remote_ip:remote_file
</p>
<p>
	或者
</p>
<p>
	scp local_file remote_ip:remote_folder
</p>
<p>
	或者
</p>
<p>
	scp local_file remote_ip:remote_file
</p>
<p>
	<br />
</p>
<p>
	第1,2个指定了用户名，命令执行后需要再输入密码，第1个仅指定了远程的目录，文件名字不变，第2个指定了文件名；
</p>
<p>
	第3,4个没有指定用户名，命令执行后需要输入用户名和密码，第3个仅指定了远程的目录，文件名字不变，第4个指定了文件名；
</p>
<p>
	* 例子：
</p>
<p>
	scp /home/space/music/1.mp3 root@www.cumt.edu.cn:/home/root/others/music
</p>
<p>
	scp /home/space/music/1.mp3 root@www.cumt.edu.cn:/home/root/others/music/001.mp3
</p>
<p>
	scp /home/space/music/1.mp3 www.cumt.edu.cn:/home/root/others/music
</p>
<p>
	scp /home/space/music/1.mp3 www.cumt.edu.cn:/home/root/others/music/001.mp3
</p>
<p>
	<br />
</p>
<p>
	* 复制目录：
</p>
<p>
	* 命令格式：
</p>
<p>
	scp -r local_folder remote_username@remote_ip:remote_folder
</p>
<p>
	或者
</p>
<p>
	scp -r local_folder remote_ip:remote_folder
</p>
<p>
	<br />
</p>
<p>
	第1个指定了用户名，命令执行后需要再输入密码；
</p>
<p>
	第2个没有指定用户名，命令执行后需要输入用户名和密码；
</p>
<p>
	* 例子：
</p>
<p>
	scp -r /home/space/music/ root@www.cumt.edu.cn:/home/root/others/
</p>
<p>
	scp -r /home/space/music/ www.cumt.edu.cn:/home/root/others/
</p>
<p>
	<br />
</p>
<p>
	上面 命令 将 本地 music 目录 复制 到 远程 others 目录下，即复制后有 远程 有 ../others/music/ 目录
</p>
<p>
	<br />
</p>
<p>
	<br />
</p>
<p>
	======
</p>
<p>
	从 远程 复制到 本地
</p>
<p>
	======
</p>
<p>
	从 远程 复制到 本地，只要将 从 本地 复制到 远程 的命令 的 后2个参数 调换顺序 即可；
</p>
<p>
	<br />
</p>
<p>
	例如：
</p>
<p>
	scp root@www.cumt.edu.cn:/home/root/others/music /home/space/music/1.mp3
</p>
<p>
	scp -r www.cumt.edu.cn:/home/root/others/ /home/space/music/
</p>
<p>
	<br />
</p>
<p>
	最简单的应用如下 :
</p>
<p>
	<br />
</p>
<p>
	scp 本地用户名 @IP 地址 : 文件名 1 远程用户名 @IP 地址 : 文件名 2
</p>
<p>
	<br />
</p>
<p>
	[ 本地用户名 @IP 地址 :] 可以不输入 , 可能需要输入远程用户名所对应的密码 .
</p>
<p>
	<br />
</p>
<p>
	可能有用的几个参数 :
</p>
<p>
	<br />
</p>
<p>
	-v 和大多数 linux 命令中的 -v 意思一样 , 用来显示进度 . 可以用来查看连接 , 认证 , 或是配置错误 .
</p>
<p>
	<br />
</p>
<p>
	-C 使能压缩选项 .
</p>
<p>
	<br />
</p>
<p>
	-P 选择端口 . 注意 -p 已经被 rcp 使用 .
</p>
<p>
	<br />
</p>
<p>
	-4 强行使用 IPV4 地址 .
</p>
<p>
	<br />
</p>
<p>
	-6 强行使用 IPV6 地址 .
</p>