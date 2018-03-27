<p>
	用途说明
</p>
<p>
	true命令啥都不做，只设置退出码为0。在Linux底下，每个程序执行完毕都会返回一个退出码给调用者，一般情况下0表示成功，其他值表明有问题，当然某些程序的退出码有特殊含义。有些shell下true可能是个内建命令，至少bash下是。（do nothing, successfully。Exit with a status code indicating success. NOTE: your shell may have its own version of true, which usually supersedes the version described here. &nbsp;Please refer to your shell’s documentation for details about the options it supports.）相对应的命令是false，也是啥都不干，但退出码设置为1。
</p>
<p>
	<br />
</p>
<p>
	常用参数
</p>
<p>
	显示退出码的方式：echo $?
</p>
<p>
	死循环的写法：while true; do commands; done
</p>
<p>
	另外一个内建命令:，就是一个冒号，也可达到true一样的效果。
</p>
<p>
	死循环的写法二：while : ;do commands; done
</p>
<p>
	<br />
</p>
<p>
	使用示例
</p>
<p>
	示例一 Bash下true是个内建命令
</p>
<p>
	[root@new55 ~]# type -a true
</p>
<p>
	true is a shell builtin
</p>
<p>
	true is /bin/true
</p>
<p>
	[root@new55 ~]#
</p>
<p>
	<br />
</p>
<p>
	示例二
</p>
<p>
	[root@web186 root]# true; echo $?
</p>
<p>
	0
</p>
<p>
	空指令:也可达到true命令一样的效果。
</p>
<p>
	[root@web186 root]# false; echo $?; :; echo $? &nbsp; &nbsp; &nbsp;
</p>
<p>
	1
</p>
<p>
	0
</p>
<p>
	[root@web186 root]#
</p>