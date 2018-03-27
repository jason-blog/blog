<p>
	更新
</p>
<p>
	&nbsp;&nbsp;&nbsp;&nbsp;git pull origin master
</p>
<p>
	提交&nbsp;
</p>
<p>
	&nbsp; &nbsp; 首先添加文件 git add -u [path]
</p>
<p>
	&nbsp; &nbsp; 然后添加注释 git commit -m&nbsp;
</p>
<p>
	&nbsp; &nbsp; 最后提交 git push origin master
</p>
<p>
	查看所有分支
</p>
<p>
	&nbsp;&nbsp;&nbsp;&nbsp;git branch
</p>
<p>
	&nbsp; &nbsp; git branch -a 查看所有分支&nbsp;
</p>
<p>
	新建分支
</p>
<p>
	&nbsp;&nbsp;&nbsp;&nbsp;git branch ***
</p>
<p>
	&nbsp;&nbsp;&nbsp;&nbsp;切换到分支
</p>
<p>
	&nbsp;&nbsp;&nbsp;&nbsp;git checkout ***
</p>
<p>
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;新建分支并切换到新建的分支中
</p>
<p>
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;git checkout -b ***
</p>
<p>
	新建分支提交到远程
</p>
<p>
	&nbsp;&nbsp;&nbsp;&nbsp;git push origin ***
</p>
<p>
	合并代码到主干
</p>
<p>
	&nbsp;&nbsp;&nbsp;&nbsp;首先切换到主分支 git checkout master
</p>
<p>
	&nbsp;&nbsp;&nbsp;&nbsp;在主分支中合并 git merge ***
</p>
<p>
	删除本地分支
</p>
<p>
	&nbsp;&nbsp;&nbsp;&nbsp;git branch -d ***
</p>
<p>
	&nbsp; &nbsp; 删除远程分支 git push origin :***
</p>
<p>
	查看某一文件改动历史&nbsp;
</p>
<p>
	&nbsp; &nbsp;git log --pretty=oneline pom.xml
</p>
<p>
	&nbsp; &nbsp;git log -n [num] 显示log条数
</p>
<p>
	&nbsp; &nbsp;git log --stat 查看提交的详情<span style="font-family:Monaco, Menlo, Consolas, &quot;font-size:13px;white-space:pre-wrap;padding:0px;margin-top:0px;margin-bottom:0px;line-height:1.42857;color:#333333;word-break:break-all;word-wrap:break-word;background-color:#F5F5F5;border:1px solid #CCCCCC;border-radius:4px;"></span> 
</p>
<p>
	&nbsp; &nbsp;git --follow -p filename
</p>
<p>
	&nbsp; &nbsp;show [commit id]
</p>
<p>
	显示git提交状态 git status&nbsp;<br />
重置提交 git reset HEAD &lt;file&gt;
</p>
<p>
	重置提交&nbsp;git&nbsp;reset HEAD *<br />
回滚 git reset —hard [版本id]<br />
撤销修改 &nbsp;git checkout -- README.md<br />
查看修改 git diff ***(文件)<br />
github配置<br />
&nbsp;查看<br />
&nbsp; &nbsp; git config user.name&nbsp;<br />
&nbsp; &nbsp; git config user.email &nbsp;
</p>
<p style="white-space:pre-wrap;word-wrap:break-word;box-sizing:border-box;margin-top:0px;margin-bottom:10.5px;font-family:&quot;padding:10px;font-size:14px;line-height:1.45;word-break:break-all;color:#333333;background-color:rgba(128, 128, 128, 0.05);border:1px solid rgba(128, 128, 128, 0.075);border-radius:0px;">
	配置<br />
&nbsp;git config --global user.name "username"&nbsp;<br />
&nbsp;git config --global user.email "email" &nbsp;<br />
强制更新放弃本地修改&nbsp;<br />
&nbsp;git fetch --all&nbsp;<br />
&nbsp;git reset --hard origin/master&nbsp;<br />
初始化<br />
git init<br />
git add README.md<br />
git commit -m "first commit"
</p>
<p style="white-space:pre-wrap;word-wrap:break-word;box-sizing:border-box;margin-top:0px;margin-bottom:10.5px;font-family:&quot;padding:10px;font-size:14px;line-height:1.45;word-break:break-all;color:#333333;background-color:rgba(128, 128, 128, 0.05);border:1px solid rgba(128, 128, 128, 0.075);border-radius:0px;">
	git commit 命令的verbose参数，会列出 diff 的结果。
</p>
<p style="white-space:pre-wrap;word-wrap:break-word;box-sizing:border-box;margin-top:0px;margin-bottom:10.5px;font-family:&quot;padding:10px;font-size:14px;line-height:1.45;word-break:break-all;color:#333333;background-color:rgba(128, 128, 128, 0.05);border:1px solid rgba(128, 128, 128, 0.075);border-radius:0px;">
	git remote add origin YourGithubAddress<br />
git push -u origin master
</p>
<p style="white-space:pre-wrap;word-wrap:break-word;box-sizing:border-box;margin-top:0px;margin-bottom:10.5px;font-family:&quot;padding:10px;font-size:14px;line-height:1.45;word-break:break-all;color:#333333;background-color:rgba(128, 128, 128, 0.05);border:1px solid rgba(128, 128, 128, 0.075);border-radius:0px;">
	<span style="font-family:&quot;padding:0px;font-size:inherit;color:inherit;background-color:transparent;white-space:pre;border-radius:0px;word-wrap:normal;">git clean  -d  -fx ""</span> 
</p>
<p style="white-space:pre-wrap;word-wrap:break-word;box-sizing:border-box;margin-top:0px;margin-bottom:10.5px;font-family:&quot;padding:10px;font-size:14px;line-height:1.45;word-break:break-all;color:#333333;background-color:rgba(128, 128, 128, 0.05);border:1px solid rgba(128, 128, 128, 0.075);border-radius:0px;">
	<code style="box-sizing:border-box;font-family:&quot;padding:0px;font-size:inherit;color:inherit;background-color:transparent;white-space:pre;border-radius:0px;word-wrap:normal;">&nbsp;&nbsp;&nbsp;&nbsp;1. x ：表示删除忽略文件已经对Git来说不识别的文件&nbsp;<br />
2. d: 删除未被添加到git的路径中的文件&nbsp;<br />
3. f: 强制执行<br />
</code> 
</p>
<p>
	<code style="box-sizing:border-box;font-family:&quot;padding:0px;font-size:inherit;color:inherit;background-color:transparent;white-space:pre;border-radius:0px;word-wrap:normal;"> </code> 
</p>
<p>
	<code style="box-sizing:border-box;font-family:&quot;padding:0px;font-size:inherit;color:inherit;background-color:transparent;white-space:pre;border-radius:0px;word-wrap:normal;"> git submodule init</code> 
</p>
<p>
	<code style="box-sizing:border-box;font-family:&quot;padding:0px;font-size:inherit;color:inherit;background-color:transparent;white-space:pre;border-radius:0px;word-wrap:normal;"> git submodule update</code> 
</p>
<code style="box-sizing:border-box;font-family:&quot;padding:0px;font-size:inherit;color:inherit;background-color:transparent;white-space:pre;border-radius:0px;word-wrap:normal;"> </code> git submodule foreach --recursive git branch
<p>
	<br />
</p>
<p>
	<br />
</p>
<p style="white-space:pre-wrap;word-wrap:break-word;box-sizing:border-box;margin-top:0px;margin-bottom:10.5px;font-family:&quot;padding:10px;font-size:14px;line-height:1.45;word-break:break-all;color:#333333;background-color:rgba(128, 128, 128, 0.05);border:1px solid rgba(128, 128, 128, 0.075);border-radius:0px;">
	强制推送<br />
git push --fetch
</p>
<p style="white-space:pre-wrap;word-wrap:break-word;box-sizing:border-box;margin-top:0px;margin-bottom:10.5px;font-family:&quot;padding:10px;font-size:14px;line-height:1.45;word-break:break-all;color:#333333;background-color:rgba(128, 128, 128, 0.05);border:1px solid rgba(128, 128, 128, 0.075);border-radius:0px;">
	git push origin master -f
</p>
<p style="white-space:pre-wrap;word-wrap:break-word;box-sizing:border-box;margin-top:0px;margin-bottom:10.5px;font-family:&quot;padding:10px;font-size:14px;line-height:1.45;word-break:break-all;color:#333333;background-color:rgba(128, 128, 128, 0.05);border:1px solid rgba(128, 128, 128, 0.075);border-radius:0px;">
	回到第一个commit
</p>
<p style="white-space:pre-wrap;word-wrap:break-word;box-sizing:border-box;margin-top:0px;margin-bottom:10.5px;font-family:&quot;padding:10px;font-size:14px;line-height:1.45;word-break:break-all;color:#333333;background-color:rgba(128, 128, 128, 0.05);border:1px solid rgba(128, 128, 128, 0.075);border-radius:0px;">
<pre style="box-sizing:border-box;font-family:SFMono-Regular, Consolas, &quot;font-size:13.6px;margin-top:0px;margin-bottom:0px;word-wrap:normal;padding:16px;overflow:auto;line-height:1.45;background-color:#F6F8FA;border-radius:3px;word-break:normal;color:#24292E;">  git update-ref -d HEAD</pre>
</p>
<p style="white-space:pre-wrap;word-wrap:break-word;box-sizing:border-box;margin-top:0px;margin-bottom:10.5px;font-family:&quot;padding:10px;font-size:14px;line-height:1.45;word-break:break-all;color:#333333;background-color:rgba(128, 128, 128, 0.05);border:1px solid rgba(128, 128, 128, 0.075);border-radius:0px;">
	<span style="font-weight:600;color:#262626;font-family:-apple-system, BlinkMacSystemFont, &quot;font-size:15px;white-space:pre-wrap;background-color:#FFFFFF;">rebase</span> 
</p>
&nbsp;&nbsp;<span style="font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">git reabse –i develop</span> 
<p>
	<br />
</p>