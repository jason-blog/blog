<span style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">今天项目例会时提到一个这样的问题，我们公司做的一个产品是和客户公司共同开发、需要两边公司都有svn库，这样就导致两个svn库的代码不同步，所以这样就需要设置成两个svn库进行同步，google了一下发现网上好多大虾都已经搞过，所以顺手牵样搞下来学习一下，供大家分享一下&nbsp;</span>
<div id="cnblogs_post_body" style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<div>
		试验下来，SVNSync除了目标库为只读之外，其它功能都很强大，实现也相对简单。
	</div>
	<div>
		http://www.svn8.com/svnsy/20090624/6785.html
	</div>
	<div>
		<br />
	</div>
	<div>
		如用svnsync 同步备份linux 下svn版本库到Windows
	</div>
	<div>
		要同步的项目名称：MU
	</div>
	<div>
		svn版本库1。4以上
	</div>
	<div>
		源目录：svn://192.168.1.196/mu
	</div>
	<div>
		目标目录:svn://192.168.1.205/mu
	</div>
	<div>
		&nbsp;
	</div>
	<div>
		方法：
	</div>
	<div>
		1.如果目标目录存在相同的项目，请先清除，重新建立空项目
	</div>
	<div>
		svnadmin create mu
	</div>
	<div>
		2.在mu目录下hooks目录下，建立
	</div>
	<div>
		pre_revprop-change.bat 全部内容只有一行：exit 0
	</div>
	<div>
		如果用拷贝同目录下的pre_revprop-change.tmpl 则必须删除最后三行的内容或替换为只有一行：exit 0
	</div>
	<div>
		不然下面初始化同步的时候，将停顿
	</div>
	<div>
		&nbsp;
	</div>
	<div>
		3. 执行 初始化
	</div>
	<div>
		svnsync init svn://192.168.1.205/mu svn://192.168.1.196/mu
	</div>
	<div>
		即svnsync init 目标库 源库
	</div>
	<div>
		将向你询问登录目标库和源库的用户名和密码，建议为两个库设置相同的用户名及相同的密码
	</div>
	<div>
		正确后，显示
	</div>
	<div>
		Copied properties for revision 0.
	</div>
	<div>
		<br />
	</div>
	<div>
		4.执行同步
	</div>
	<div>
		svnsync sync svn://192.168.1.205/mu
	</div>
	<div>
		即svnsync sync 目标库
	</div>
	<div>
		正确执行后，显示
	</div>
	<div>
		Committed revision 1.
	</div>
	<div>
		Copied properties for revision 1.
	</div>
	<div>
		Committed revision 2.
	</div>
	<div>
		Copied properties for revision 2.
	</div>
	<div>
		Committed revision 3.
	</div>
	<div>
		Copied properties for revision 3.
	</div>
	<div>
		Committed revision 4.
	</div>
	<div>
		Copied properties for revision 4.
	</div>
	<div>
		Committed revision 5.
	</div>
	<div>
		Copied properties for revision 5.
	</div>
	<div>
		Committed revision 6.
	</div>
	<div>
		Copied properties for revision 6.
	</div>
	<div>
		Committed revision 7.
	</div>
	<div>
		Copied properties for revision 7.
	</div>
	<div>
		Committed revision 8.
	</div>
	<div>
		...
	</div>
	<div>
		<br />
	</div>
	<div>
		5.更新同步
	</div>
	<div>
		在源库的hooks下面，添加post-commit 脚本
	</div>
	<div>
		可拷贝post-commit.tmpl
	</div>
	<div>
		即
	</div>
	<div>
		&nbsp;
	</div>
	<div>
		cp post-commit.tmpl post-commit
	</div>
	<div>
		然后
	</div>
	<div>
		把 post-commit 中，最后两行替换为
	</div>
	<div>
		&nbsp;
	</div>
	<div>
		svnsync sync &nbsp;--non-interactive svn://192.168.1.205/mu --sync-username user --sync-password user
	</div>
	<div>
		即提交更新后，即执行同步命令，不进行交互
	</div>
	<div>
		把post-commit 设为755权限。
	</div>
	<div>
		&nbsp;
	</div>
	<div>
		ps：
	</div>
	<div>
		如果post-commit脚本出错，或者无可执行权限，在提交更新时会报错
	</div>
</div>