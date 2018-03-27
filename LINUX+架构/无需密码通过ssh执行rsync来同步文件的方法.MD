<b>
<p style="margin-top:0px;margin-bottom:0px;padding:5px 0px;font-size:14px;font-family:tahoma, arial, 宋体;white-space:normal;background-color:#FFFFFF;">
	<strong>1.通过ssh执行rsync(需要密码)</strong>
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:5px 0px;font-size:14px;font-family:tahoma, arial, 宋体;white-space:normal;background-color:#FFFFFF;">
	通过ssh帐户(需要密码)执行rsync，将文件同步镜像到远程服务器。<br />
下面这个例子将本地的/home/ramesh同步到远程目录/backup/ramesh(服务器地址192.168.200.10)。<br />
执行以下操作时，服务器将会提示需要用户使用密码登录。
</p>
<div class="codetitle" style="margin:3px auto 0px;padding:0px 3px;background:#F2F6FB;width:640px;clear:both;font-size:14px;border-top:1px solid #0099CC;border-right:1px solid #0099CC;border-left:1px solid #0099CC;line-height:25.2px;font-family:tahoma, arial, 宋体;white-space:normal;">
	<span style="line-height:21.6px;font-size:12px;float:right;"><a data="75243" class="copybut" id="copybut75243" style="color:#333333;cursor:pointer;"><u>复制代码</u></a></span>代码如下:
</div>
<div class="codebody" id="code75243" style="margin:0px auto 3px;padding:0px 3px 0px 5px;line-height:25.2px;font-size:14px;background:#DDEDFB;border:1px solid #0099CC;width:638px;clear:both;font-family:tahoma, arial, 宋体;white-space:normal;">
	<br />
rsync -avz -e ssh /home/ramesh/ ramesh@192.168.200.10:/backup/ramesh/<br />
</div>
<p style="margin-top:0px;margin-bottom:0px;padding:5px 0px;font-size:14px;font-family:tahoma, arial, 宋体;white-space:normal;background-color:#FFFFFF;">
	<strong>2.使用ssh-keygen生成密匙</strong>
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:5px 0px;font-size:14px;font-family:tahoma, arial, 宋体;white-space:normal;background-color:#FFFFFF;">
	现在我们来设置ssh,以便在执行ssh操作时不需要密码，使用ssh-keygen在本地生成公钥和私钥。
</p>
<div class="codetitle" style="margin:3px auto 0px;padding:0px 3px;background:#F2F6FB;width:640px;clear:both;font-size:14px;border-top:1px solid #0099CC;border-right:1px solid #0099CC;border-left:1px solid #0099CC;line-height:25.2px;font-family:tahoma, arial, 宋体;white-space:normal;">
	<span style="line-height:21.6px;font-size:12px;float:right;"><a data="66957" class="copybut" id="copybut66957" style="color:#333333;cursor:pointer;"><u>复制代码</u></a></span>代码如下:
</div>
<div class="codebody" id="code66957" style="margin:0px auto 3px;padding:0px 3px 0px 5px;line-height:25.2px;font-size:14px;background:#DDEDFB;border:1px solid #0099CC;width:638px;clear:both;font-family:tahoma, arial, 宋体;white-space:normal;">
	<br />
$ ssh-keygen<br />
Enter passphrase (empty for no passphrase):<br />
Enter same passphrase again:<br />
</div>
<p style="margin-top:0px;margin-bottom:0px;padding:5px 0px;font-size:14px;font-family:tahoma, arial, 宋体;white-space:normal;background-color:#FFFFFF;">
	提示：当提示输入密码时，只需输入两次回车键，不指配密码字符。
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:5px 0px;font-size:14px;font-family:tahoma, arial, 宋体;white-space:normal;background-color:#FFFFFF;">
	<strong>3.使用ssh-copy-id将公匙拷贝至远程主机</strong>
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:5px 0px;font-size:14px;font-family:tahoma, arial, 宋体;white-space:normal;background-color:#FFFFFF;">
	执行ssh-copy-id,将通过ssh-keygen生成的公匙拷贝至远程主机。
</p>
<div class="codetitle" style="margin:3px auto 0px;padding:0px 3px;background:#F2F6FB;width:640px;clear:both;font-size:14px;border-top:1px solid #0099CC;border-right:1px solid #0099CC;border-left:1px solid #0099CC;line-height:25.2px;font-family:tahoma, arial, 宋体;white-space:normal;">
	<span style="line-height:21.6px;font-size:12px;float:right;"><a data="44931" class="copybut" id="copybut44931" style="color:#333333;cursor:pointer;"><u>复制代码</u></a></span>代码如下:
</div>
<div class="codebody" id="code44931" style="margin:0px auto 3px;padding:0px 3px 0px 5px;line-height:25.2px;font-size:14px;background:#DDEDFB;border:1px solid #0099CC;width:638px;clear:both;font-family:tahoma, arial, 宋体;white-space:normal;">
	<br />
ssh-copy-id -i ~/.ssh/id_rsa.pub 192.168.200.10<br />
</div>
<p style="margin-top:0px;margin-bottom:0px;padding:5px 0px;font-size:14px;font-family:tahoma, arial, 宋体;white-space:normal;background-color:#FFFFFF;">
	提示：执行以上操作时，将会提示输入远程主机帐户和密码，然后就会自动将公匙拷贝至远程目录。
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:5px 0px;font-size:14px;font-family:tahoma, arial, 宋体;white-space:normal;background-color:#FFFFFF;">
	<strong>4.无需密码通过ssh来执行rsync</strong>
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:5px 0px;font-size:14px;font-family:tahoma, arial, 宋体;white-space:normal;background-color:#FFFFFF;">
	现在，你可以不需要密码就可以ssh连接到远程主机
</p>
<div class="codetitle" style="margin:3px auto 0px;padding:0px 3px;background:#F2F6FB;width:640px;clear:both;font-size:14px;border-top:1px solid #0099CC;border-right:1px solid #0099CC;border-left:1px solid #0099CC;line-height:25.2px;font-family:tahoma, arial, 宋体;white-space:normal;">
	<span style="line-height:21.6px;font-size:12px;float:right;"><a data="84452" class="copybut" id="copybut84452" style="color:#333333;cursor:pointer;"><u>复制代码</u></a></span>代码如下:
</div>
<div class="codebody" id="code84452" style="margin:0px auto 3px;padding:0px 3px 0px 5px;line-height:25.2px;font-size:14px;background:#DDEDFB;border:1px solid #0099CC;width:638px;clear:both;font-family:tahoma, arial, 宋体;white-space:normal;">
	<br />
ssh 192.168.200.10<br />
</div>
<p style="margin-top:0px;margin-bottom:0px;padding:5px 0px;font-size:14px;font-family:tahoma, arial, 宋体;white-space:normal;background-color:#FFFFFF;">
	重新来执行rsync，现在应该就不会提示输入密码了
</p>
<div class="codetitle" style="margin:3px auto 0px;padding:0px 3px;background:#F2F6FB;width:640px;clear:both;font-size:14px;border-top:1px solid #0099CC;border-right:1px solid #0099CC;border-left:1px solid #0099CC;line-height:25.2px;font-family:tahoma, arial, 宋体;white-space:normal;">
	<span style="line-height:21.6px;font-size:12px;float:right;"><a data="75243" class="copybut" id="copybut75243" style="color:#333333;cursor:pointer;"><u>复制代码</u></a></span>代码如下:
</div>
<div class="codebody" id="code75243" style="margin:0px auto 3px;padding:0px 3px 0px 5px;line-height:25.2px;font-size:14px;background:#DDEDFB;border:1px solid #0099CC;width:638px;clear:both;font-family:tahoma, arial, 宋体;white-space:normal;">
	<br />
rsync -avz -e ssh /home/ramesh/ ramesh@192.168.200.10:/backup/ramesh/
</div>
</b>