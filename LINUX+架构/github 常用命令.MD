<br />
<p>
	<span style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">git remote add origin YourGithubAddress</span> 
</p>
<p>
	<br />
</p>
git clone git://github.com:xxxx/test.git ##以gitreadonly方式克隆到本地，只可以读 &nbsp;<br />
git clone git@github.com:xxx/test.git &nbsp;##以SSH方式克隆到本地，可以读写 &nbsp;<br />
git clone https://github.com/xxx/test.git ##以https方式克隆到本地，可以读写 &nbsp;<br />
git fetch git@github.com:xxx/xxx.git &nbsp;##获取到本地但不合并 &nbsp;<br />
git pull git@github.com:xxx/xxx.git ##获取并合并内容到本地 &nbsp;<br />
<br />
git commit -a -m "added initial version of page cache" &nbsp;<br />
<br />
git push origin new-feature&nbsp;<br />
<br />
<br />
<br />
<br />
git pull origin master<br />
<br />
git add .<br />
git commit -m "content"<br />
<p>
	git push origin master
</p>
<p>
	<br />
</p>
<p>
	<span style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">git init</span><br style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">git add README.md</span><br style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">git commit -m "first commit"</span><br style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">git remote add origin <span style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">YourGithubAddress</span></span><br style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">git push -u origin master</span> 
</p>
<p>
	<br />
</p>
<p>
	删除某一文件的历史提交版本
</p>
<pre style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;"> git filter-branch -f --tree-filter <span style="margin:0px;padding:0px;color:#800000;line-height:1.5 !important;">'</span><span style="margin:0px;padding:0px;color:#800000;line-height:1.5 !important;">rm -rf vendor/gems</span><span style="margin:0px;padding:0px;color:#800000;line-height:1.5 !important;">'</span><span style="margin:0px;padding:0px;line-height:1.5 !important;"> HEAD </span></pre>
<pre style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;"> git push origin --force</pre>
<br />
<br />