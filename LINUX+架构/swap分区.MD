<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	http://www.cnblogs.com/kerrycode/p/5246383.html&nbsp; &nbsp;
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	&nbsp;swap分区
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	在安装oracle数据库之前还有一个重要的准备前提，挂载swap分区。Swap分区的大小和Linux内存的大小有关系（关系自己计算）。如果增加1G内存，swap分区就要增加2G.
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	首先是检查swap分区是否存在，检查的命令为 free –m&nbsp;
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	<img src="http://www.linuxidc.com/upload/2016_03/1603282113820010.png" alt="" /> 
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	如上图所示的Swap显示为0，表示swap分区不存在，那么在安装前就要自己先创建一个swap交换分区。 创建的步骤如下：
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	1、决定创建swap大小，首先在空间合适处创建用于分区的swap文件：如/swap1
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	命令为&nbsp; dd if=/dev/zero of=/swap1 bs=1M count=2048
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	<img src="http://www.linuxidc.com/upload/2016_03/1603282113820011.png" alt="" /> 
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	If表示infile, of表示outfile, bs=1M代表增加的模块大小,count=2048代表是2048个模块，也就是2G空间大小
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	2、将目的文件设置为swap分区文件:
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	#mkswap /swap1
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	<img src="http://www.linuxidc.com/upload/2016_03/1603282113820012.png" alt="" /> 
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	3、激活swap，立即启用交换分区文件：
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	#swapon /swap1
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	<img src="http://www.linuxidc.com/upload/2016_03/1603282113820013.png" alt="" /> 
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	以上操作重启系统后swap空间将会失去/swap1,将/swap1加入到/etc/fstab条目将可以使用得系统在init进程中调用swapon –a来自动挂载/swap1，这样每次机器重启后/swap1都处于有效的swap空间. 修改命令 vi /etc/fstab
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	<img src="http://www.linuxidc.com/upload/2016_03/1603282113820014.png" alt="" /> 
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	在/etc/fstab编辑中加入swap1&nbsp; swap swap default 0 0 命令，然后保存退出
</p>
<p style="color:#333333;font-family:tahoma, 宋体;font-size:14px;text-align:justify;white-space:normal;background-color:#FAFAFC;">
	修改后使用swapon –s 或者free –m可以查看
</p>