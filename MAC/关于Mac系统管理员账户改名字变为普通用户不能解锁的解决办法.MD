<h1 class="postTitle" style="margin:0px 0px 20px;padding:0px;font-size:28px;font-weight:400;line-height:35px;color:#333333;height:35px;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
	<a id="cb_post_title_url" class="postTitle2" href="http://www.cnblogs.com/code-f/articles/8064947.html" style="margin:0px;padding:0px;color:#333333;text-decoration-line:none;">关于Mac系统管理员账户改名字变为普通用户不能解锁的解决办法</a> 
</h1>
<div class="clear" style="margin:0px;padding:0px;clear:both;color:#7D8B8D;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">
</div>
<div class="postBody" style="margin:0px;padding:0px;color:#7D8B8D;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<div id="cnblogs_post_body" class="blogpost-body" style="margin:0px 0px 20px;padding:0px;word-break:break-word;color:#333333;line-height:1.8;">
		<p style="margin:10px auto;padding:0px;">
			第一步：开机
		</p>
		<p style="margin:10px auto;padding:0px;">
			第二步：在没有亮屏幕前，一直按住command+s 进入命令行状态
		</p>
		<p style="margin:10px auto;padding:0px;">
			第三部：当光标稳定后 回车2次
		</p>
		<p style="margin:10px auto;padding:0px;">
			第四步：输入：mount -rw空格／
		</p>
		<p style="margin:10px auto;padding:0px;">
			第五步：输入：cd var
		</p>
		<p style="margin:10px auto;padding:0px;">
			第六步：输入：cd db 每段要回车
		</p>
		<p style="margin:10px auto;padding:0px;">
			第七步：输入：rm .AppleSetupDone回车 注意，那几个大写
		</p>
		<p style="margin:10px auto;padding:0px;">
			第八步：输入：reboot
		</p>
		<p style="margin:10px auto;padding:0px;">
			第九步：重启
		</p>
		<p style="margin:10px auto;padding:0px;">
			第十步：重新注册账户，登陆
		</p>
		<p style="margin:10px auto;padding:0px;">
			然后就可以进入用户控制用当前的账户去解锁了。
		</p>
		<p style="margin:10px auto;padding:0px;">
			解锁后点击之前的账户勾选"允许用户管理这台电脑"就设置成管理员了。
		</p>
		<p style="margin:10px auto;padding:0px;">
			不建议删除新建的用户，以防以后还有此类问题出现留着以备后用。
		</p>
		<blockquote style="margin:0px;padding:5px 10px;background:none;border-top:none;border-right:none;border-bottom:none;border-left:5px solid #DDDDDD;border-image:initial;">
			<p style="margin-top:0px;margin-bottom:0px;padding:0px;color:#777777;">
				问题解决请推荐让更多人看见并解决问题！谢谢！
			</p>
		</blockquote>
	</div>
	<div id="MySignature" style="margin:0px;padding:0px;">
		回首向来萧瑟处，也无风雨也无晴。
	</div>
	<div class="clear" style="margin:0px;padding:0px;clear:both;">
	</div>
	<div id="blog_post_info_block" style="margin:20px 0px 0px;padding:0px;">
		<div id="BlogPostCategory" style="margin:0px 0px 10px;padding:0px;">
			分类:&nbsp;<a href="http://www.cnblogs.com/code-f/category/1133590.html" target="_blank" style="margin:0px 0px 0px 10px;padding:0px;color:#000000;text-decoration-line:none;">关于电脑的各种问题解决</a> 
		</div>
	</div>
</div>