<div class="postTitle" style="padding:10px 10px 10px 0px;font-size:14px;font-weight:bold;margin:0px;font-family:verdana, Arial, Helvetica, sans-serif;white-space:normal;">
	<a id="cb_post_title_url" class="postTitle2" href="http://www.cnblogs.com/liaojie970/p/5753587.html" style="color:#FF3366;text-decoration-line:none;">Linux系统中的运行级别</a>
</div>
<div id="cnblogs_post_body" style="margin:0px 0px 20px;word-break:break-word;line-height:1.8;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;">
	<p style="margin:10px auto;">
		<img src="http://images2015.cnblogs.com/blog/697878/201608/697878-20160809154717168-220145957.png" alt="" style="max-width:900px;" />
	</p>
	<p style="margin:10px auto;">
		&nbsp;
	</p>
	<p style="margin:10px auto;">
		什么是运行级呢？简单的说，运行级就是操作系统当前正在运行的功能级别。 它让一些程序在一个级别启动，而另外一个级别的时候不启动。
	</p>
	<p style="margin:10px auto;">
		Linux系统的有效登录模式有0~9共十种，不过沿用UNIX系统的至多6种的限制，一般只有1到6有效。从1到6 ，具有不同的功能。
	</p>
	<p style="margin:10px auto;">
		/etc/rc.d/init.d中放着各种脚本，每个运行级别对应的文件/etc/rc.d/rcN.d中，选择你想在该级别运行的脚本， 从/etc/rc.d/init.d中链接过来。
	</p>
	<p style="margin:10px auto;">
		<img src="http://images2015.cnblogs.com/blog/697878/201608/697878-20160809160123324-2110442085.png" alt="" style="max-width:900px;" />
	</p>
	<p style="margin:10px auto;">
		而运行级别的文件定义在/etc/inittab下面。这个文件是init程序寻找的主要文件,
	</p>
	<p style="margin:10px auto;">
		init是Linux系统里的根进程，是系统所有进程的祖先。它的主要作用是根据记录在/etc/inittab里的一个脚本（script）程序产生进程。 这个文件通常用于控制用户的登录模式。
	</p>
	<p style="margin:10px auto;">
		&nbsp;
	</p>
	<p style="margin:10px auto;">
		标准的Linux运行级为3或者5，如果是3的话，系统就在多用户状态。如果是5的话，则是运行着X Window 系统。如果目前正在3或5，而你把运行级降低到2的话，init就会执行K45named脚本。
	</p>
	<p style="margin:10px auto;">
		不同的运行级定义如下：(可以参考Linux里面的/etc/inittab)
	</p>
	<p style="margin:10px auto;">
		# 缺省的运行级，RHS用到的级别如下：
	</p>
	<p style="margin:10px auto;">
		# 0 - 停机 ，机器关闭。
	</p>
	<p style="margin:10px auto;">
		# 1 - 单用户模式 。就像Win9x下的安全模式类似
	</p>
	<p style="margin:10px auto;">
		# 2 - 多用户，但是没有NFS&nbsp; 进入无网络服务的多用户模式
	</p>
	<p style="margin:10px auto;">
		# 3 - 完全多用户模式 ，是标准的运行级。
	</p>
	<p style="margin:10px auto;">
		# 4 - 没有用到 ，一般不用，在一些特殊情况下可以用它来做一些事情。例如在笔记本 电脑的电池用尽时，可以切换到这个模式来
	</p>
	<p style="margin:10px auto;">
		# 5 - X11&nbsp;&nbsp; ，进到X Window系统了。&nbsp;
	</p>
	<p style="margin:10px auto;">
		# 6 - 重新启动 ，运行init 6机器就会重启
	</p>
	<p style="margin:10px auto;">
		init一般在系统启动时自动运行，也可以由root用户调用。它的作用是切换系统的运行状态。
	</p>
	<p style="margin:10px auto;">
		它的命令格式是：init NUM〈回车〉，其中NUM表示1到6的任一数字。
	</p>
	<p style="margin:10px auto;">
		6种模式中有两种是系统内定的：
	</p>
	<p style="margin:10px auto;">
		0：停止系统运行。init 0〈回车〉相当于 halt〈回车〉。
	</p>
	<p style="margin:10px auto;">
		6：重启系统。init 6〈回车〉相当于 reboot〈回车〉。
	</p>
	<p style="margin:10px auto;">
		&nbsp;
	</p>
	<p style="margin:10px auto;">
		在终端中，我们可以键入 init &lt;运行级别&gt; 来切换运行级别来达到某种目的，
	</p>
	<p style="margin:10px auto;">
		如输入 init 0 使系统关机，输入 init 6 使系统重启。
	</p>
	<p style="margin:10px auto;">
		&nbsp;
	</p>
	<p style="margin:10px auto;">
		如果你使用的是文本登录屏幕，你是在运行级别 3 中操作。如果你使用的是图形化登录屏幕，你是在运行级别 5 中操作。
	</p>
	<p style="margin:10px auto;">
		默认的运行级别可以通过修改 /etc/inittab 文件来改变，该文件在接近开头的地方有一行与下面相似：
	</p>
	<p style="margin:10px auto;">
		id:5:initdefault:
	</p>
	<p style="margin:10px auto;">
		把这一行中的数字改成你想要的运行级别。所做改变在系统重新引导之后才会生效。
	</p>
	<p style="margin:10px auto;">
		要立即改变运行级别，使用命令 telinit，其后跟随运行级别数字。你必须是根用户才能使用这项命令
	</p>
	<p style="margin:10px auto;">
		不同的运行级有不同的用处，也应该根据自己的不同情形来设置。
	</p>
	<p style="margin:10px auto;">
		例如，如果丢失了root口令，那么可以让机器启动进入单用户状态来设置。
	</p>
	<p style="margin:10px auto;">
		在启动后的lilo提示符下输入：
	</p>
	<p style="margin:10px auto;">
		init=/bin/sh rw
	</p>
	<p style="margin:10px auto;">
		就可以使机器进入运行级1 ，并把root文件系统挂为读写。它会跳过所有系统认证，让你使用passwd程序来改变root口令，然后启动到一个新的运行级
	</p>
</div>