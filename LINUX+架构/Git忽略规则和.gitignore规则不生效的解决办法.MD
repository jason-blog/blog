<h1 class="postTitle" style="margin:0px 0px 20px;padding:0px;font-size:28px;font-weight:400;line-height:1.8;color:#333333;font-family:Verdana, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
	<a id="cb_post_title_url" class="postTitle2" href="http://www.cnblogs.com/zhangxiaoliu/p/6008038.html" style="margin:0px;padding:0px;color:#333333;text-decoration-line:none;">Git忽略规则和.gitignore规则不生效的解决办法</a>
</h1>
<div class="clear" style="margin:0px;padding:0px;clear:both;color:#7D8B8D;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
</div>
<div class="postBody" style="margin:0px;padding:0px;color:#7D8B8D;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<div id="cnblogs_post_body" class="blogpost-body" style="margin:0px 0px 20px;padding:0px;word-break:break-word;color:#333333;line-height:1.8;">
		<p style="margin:10px auto;padding:0px;">
			<span style="margin:0px;padding:0px;color:#FF6600;">Git忽略规则：</span>
		</p>
		<p style="margin:10px auto;padding:0px;">
			<span style="margin:0px;padding:0px;color:#000000;">在git中如果想忽略掉某个文件，不让这个文件提交到版本库中，可以使用修改根目录中 .gitignore 文件的方法（如果没有这个文件，则需自己手工建立此文件）。这个文件每一行保存了一个匹配的规则例如：</span>
		</p>
		<p style="margin:10px auto;padding:0px;">
			# 此为注释 – 将被 Git 忽略<br style="margin:0px;padding:0px;" />
<br style="margin:0px;padding:0px;" />
*.sample&nbsp;　　 # 忽略所有 .sample 结尾的文件<br style="margin:0px;padding:0px;" />
!lib.sample&nbsp;　　 # 但 lib.sample 除外<br style="margin:0px;padding:0px;" />
/TODO 　　 # 仅仅忽略项目根目录下的 TODO 文件，不包括 subdir/TODO<br style="margin:0px;padding:0px;" />
build/ 　　 # 忽略 build/ 目录下的所有文件<br style="margin:0px;padding:0px;" />
doc/*.txt 　　# 会忽略 doc/notes.txt 但不包括 doc/server/arch.txt
		</p>
		<p style="margin:10px auto;padding:0px;">
			<span style="margin:0px;padding:0px;color:#FF6600;">.gitignore规则不生效的解决办法</span>
		</p>
		<p style="margin:10px auto;padding:0px;">
			把某些目录或文件加入忽略规则，按照上述方法定义后发现并未生效，原因是.gitignore只能忽略那些原来没有被追踪的文件，如果某些文件已经被纳入了版本管理中，则修改.gitignore是无效的。那么解决方法就是先把本地缓存删除（改变成未被追踪状态），然后再提交：
		</p>
		<p style="margin:10px auto;padding:0px;">
			git rm -r --cached .<br style="margin:0px;padding:0px;" />
git add .<br style="margin:0px;padding:0px;" />
git commit -m 'update .gitignore'
		</p>
	</div>
</div>