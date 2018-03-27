<p>
	http://www.cnblogs.com/gabin/p/6385908.html
</p>
<p>
	<br />
</p>
<p>
	<br />
</p>
<h4 style="margin:10px 0px;padding:0px;font-size:14px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;line-height:28px;font-size:14pt;">社区版</span> 
</h4>
<h4 style="margin:10px 0px;padding:0px;font-size:14px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	1. 安装配置依赖项
</h4>
<p style="margin:10px auto;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	如想使用Postfix来发送邮件,在安装期间请选择'Internet Site'. 您也可以用sendmai或者&nbsp;<a href="https://gitlab.com/gitlab-org/omnibus-gitlab/blob/master/doc/settings/smtp.md" style="margin:0px;padding:0px;color:#3B5999;text-decoration-line:none;">配置SMTP服务</a>&nbsp;并&nbsp;<a href="https://gitlab.com/gitlab-org/omnibus-gitlab/blob/master/doc/settings/smtp.md#smtp-on-localhost" style="margin:0px;padding:0px;color:#3B5999;text-decoration-line:none;">使用SMTP发送邮件.</a> 
</p>
<p style="margin:10px auto;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	在 Centos 6 和 7 系统上, 下面的命令将在系统防火墙里面开放HTTP和SSH端口.
</p>
<div class="cnblogs_code" style="margin:5px 0px;padding:5px;background-color:#F5F5F5;border:1px solid #CCCCCC;overflow:auto;white-space:normal;font-family:&quot;">
<pre style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;"><span style="margin:0px;padding:0px;line-height:18px;color:#0000FF;">sudo</span> apt-get <span style="margin:0px;padding:0px;line-height:18px;color:#0000FF;">install</span> curl openssh-server ca-certificates postfix</pre>
</div>
<h4 style="margin:10px 0px;padding:0px;font-size:14px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	2. 添加GitLab仓库,并安装到服务器上(将gitlab安装源添加到apt中，然后通过apt-get安装，最好先将apt源修改成国内的)
</h4>
<div class="cnblogs_code" style="margin:5px 0px;padding:5px;background-color:#F5F5F5;border:1px solid #CCCCCC;overflow:auto;white-space:normal;font-family:&quot;">
<pre style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">curl -sS http:<span style="margin:0px;padding:0px;line-height:18px;color:#008000;">//</span><span style="margin:0px;padding:0px;line-height:18px;color:#008000;">packages.gitlab.cc/install/gitlab-ce/script.deb.sh | sudo bash</span> <span style="margin:0px;padding:0px;line-height:18px;color:#0000FF;">sudo</span> apt-get <span style="margin:0px;padding:0px;line-height:18px;color:#0000FF;">install</span> gitlab-ce # 考验网速的时候到了</pre>
</div>
<p style="margin:10px auto;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	如果你不习惯使用命令管道的安装方式, 你可以在这里下载&nbsp;<a href="http://packages.gitlab.cc/install/gitlab-ce/" style="margin:0px;padding:0px;color:#3B5999;text-decoration-line:none;">安装脚本</a>&nbsp;或者&nbsp;<a href="https://mirrors.tuna.tsinghua.edu.cn/gitlab-ce/" style="margin:0px;padding:0px;color:#3B5999;text-decoration-line:none;">手动下载您使用的系统相应的安装包(RPM/Deb)</a>&nbsp;然后安装（手动下载需要自己找一下安装包，否则速度很慢很慢。。。）
</p>
<div class="cnblogs_code" style="margin:5px 0px;padding:5px;background-color:#F5F5F5;border:1px solid #CCCCCC;overflow:auto;white-space:normal;font-family:&quot;">
<pre style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">curl -LJO https://mirrors.tuna.tsinghua.edu.cn/gitlab-ce/ubuntu/pool/xenial/main/g/gitlab-ce/gitlab-ce-XXX.deb
dpkg -i gitlab-ce-XXX.deb</pre>
</div>
<h4 style="margin:10px 0px;padding:0px;font-size:14px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	3. 启动GitLab
</h4>
<div class="cnblogs_code" style="margin:5px 0px;padding:5px;background-color:#F5F5F5;border:1px solid #CCCCCC;overflow:auto;white-space:normal;font-family:&quot;">
<pre style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">gitlab-ctl reconfigure</pre>
</div>
<h4 style="margin:10px 0px;padding:0px;font-size:14px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	4. 使用浏览器访问GitLab&nbsp;
</h4>
<p style="margin:10px auto;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	首次访问GitLab,系统会让你重新设置管理员的密码,设置成功后会返回登录界面.
</p>
<p style="margin:10px auto;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	默认的管理员账号是<strong style="margin:0px;padding:0px;">root</strong>,如果你想更改默认管理员账号,请输入上面设置的新密码登录系统后修改帐号名.
</p>
<p style="margin:10px auto;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin:10px auto;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin:10px auto;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;line-height:28px;font-size:14pt;"><strong style="margin:0px;padding:0px;">企业版</strong></span> 
</p>
<p style="margin:10px auto;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;line-height:28px;font-size:14pt;"><strong style="margin:0px;padding:0px;">其实唯一不同的，大概就是安装的是gitlab-ee了</strong></span> 
</p>
<p style="margin:10px auto;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<h4 style="margin:10px 0px;padding:0px;font-size:14px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	1. 安装配置依赖项&nbsp;
</h4>
<p style="margin:10px auto;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	如想使用Postfix来发送邮件,在安装期间请选择'Internet Site'. 您也可以用sendmai或者&nbsp;<a href="https://gitlab.com/gitlab-org/omnibus-gitlab/blob/master/doc/settings/smtp.md" style="margin:0px;padding:0px;color:#3B5999;text-decoration-line:none;">配置SMTP服务</a>&nbsp;并&nbsp;<a href="https://gitlab.com/gitlab-org/omnibus-gitlab/blob/master/doc/settings/smtp.md#smtp-on-localhost" style="margin:0px;padding:0px;color:#3B5999;text-decoration-line:none;">使用SMTP发送邮件.</a> 
</p>
<p style="margin:10px auto;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	在 Centos 6 和 7 系统上, 下面的命令将在系统防火墙里面开放HTTP和SSH端口.&nbsp;
</p>
<div class="cnblogs_code" style="margin:5px 0px;padding:5px;background-color:#F5F5F5;border:1px solid #CCCCCC;overflow:auto;white-space:normal;font-family:&quot;">
<pre style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;"><span style="margin:0px;padding:0px;line-height:18px;color:#0000FF;">sudo</span> apt-get <span style="margin:0px;padding:0px;line-height:18px;color:#0000FF;">install</span> curl openssh-server ca-certificates postfix</pre>
</div>
<div class="tab-step" style="margin:0px;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	<h4 style="margin:10px 0px;padding:0px;font-size:14px;">
		2. 添加GitLab仓库,并安装到服务器上&nbsp;
	</h4>
	<div class="cnblogs_code" style="margin:5px 0px;padding:5px;background-color:#F5F5F5;border:1px solid #CCCCCC;overflow:auto;font-family:&quot;">
<pre style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">curl https:<span style="margin:0px;padding:0px;line-height:18px;color:#008000;">//</span><span style="margin:0px;padding:0px;line-height:18px;color:#008000;">packages.gitlab.com/install/repositories/gitlab/gitlab-ee/script.deb.sh | sudo bash</span> <span style="margin:0px;padding:0px;line-height:18px;color:#0000FF;">sudo</span> apt-get <span style="margin:0px;padding:0px;line-height:18px;color:#0000FF;">install</span> gitlab-ee</pre>
	</div>
	<p style="margin:10px auto;padding:0px;">
		如果你不习惯使用命令管道的安装方式, 你可以在这里下载&nbsp;<a href="http://packages.gitlab.cc/install/gitlab-ce/" style="margin:0px;padding:0px;color:#3B5999;text-decoration-line:none;">安装脚本</a>&nbsp;或者&nbsp;<a href="https://mirrors.tuna.tsinghua.edu.cn/gitlab-ce/" style="margin:0px;padding:0px;color:#3B5999;text-decoration-line:none;">手动下载您使用的系统相应的安装包(RPM/Deb)</a>&nbsp;然后安装&nbsp;
	</p>
	<div class="cnblogs_code" style="margin:5px 0px;padding:5px;background-color:#F5F5F5;border:1px solid #CCCCCC;overflow:auto;font-family:&quot;">
<pre style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">dpkg -i gitlab-ee-XXX.deb</pre>
	</div>
</div>
<div class="tab-step" style="margin:0px;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	<h4 style="margin:10px 0px;padding:0px;font-size:14px;">
		3. 启动GitLab&nbsp;
	</h4>
	<div class="cnblogs_code" style="margin:5px 0px;padding:5px;background-color:#F5F5F5;border:1px solid #CCCCCC;overflow:auto;font-family:&quot;">
<pre style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;"><span style="margin:0px;padding:0px;line-height:18px;color:#0000FF;">sudo</span> gitlab-ctl reconfigure</pre>
	</div>
	<h4 style="margin:10px 0px;padding:0px;font-size:14px;">
		4. 使用浏览器访问GitLab&nbsp;
	</h4>
</div>
<p>
	<br />
</p>
<p style="margin:10px auto;padding:0px;">
	首次访问GitLab,系统会让你重新设置管理员的密码,设置成功后会返回登录界面.
</p>
<p style="margin:10px auto;padding:0px;">
	默认的管理员账号是<strong style="margin:0px;padding:0px;">root</strong>,如果你想更改默认管理员账号,请输入上面设置的新密码登录系统后修改帐号名.
</p>
<p style="margin:10px auto;padding:0px;">
	<br />
</p>
<p style="margin:10px auto;padding:0px;">
	默认账号密码&nbsp;
<pre style="color:#333333;font-size:14px;text-align:justify;background-color:#FAFAFC;">Username: root Password: 5iveL!fe </pre>
</p>
<p>
	<br />
</p>
<p>
	<br />
</p>