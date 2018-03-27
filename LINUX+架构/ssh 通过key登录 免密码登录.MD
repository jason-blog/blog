<span style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">1 、 登录148,执行命令 ssh-keygen -t rsa 之后一路回 车，查看刚生成的无密码钥对： cd .ssh 后 执行 ll</span><br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">2 、把 id_rsa.pub 追加到授权的 key 里面去。 执行命令 cat ~/.ssh/id_rsa.pub &gt;&gt;~/.ssh/authorized_keys</span><br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">3 、修改权限： 执行 chmod 600 ~/.ssh/authorized_keys</span><br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">4 、确保 cat /etc/ssh/sshd_config 中存在如下内容</span><br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">RSAAuthentication yes</span><br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">&nbsp;</span><br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">PubkeyAuthentication yes</span><br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">&nbsp;</span><br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">AuthorizedKeysFile &nbsp; &nbsp; &nbsp;.ssh/authorized_keys</span><br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">如需修改， 则在修改后执行重启 SSH 服 务命令使其生效 :service sshd restart</span><br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">5 、将公 钥复制到所有其他机器上 :scp ~/.ssh/id_rsa.pub root@147:~/ 然后 输入 yes ，最后 输入 147机器的密 码</span><br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">6 、在 147 机器上 创建 .ssh 文件夹 :</span><br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">mkdir ~/.ssh</span><br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">然后 执行 chmod 700 ~/.ssh （若文件夹以存在 则不需要创建）</span><br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">7 、追加到授权文件 authorized_keys 执行命令 :</span><br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">cat ~/id_rsa.pub &gt;&gt; ~/.ssh/authorized_keys</span><br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">然后 执行 chmod 600 ~/.ssh/authorized_keys</span><br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">8 、重复第 4 步</span><br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">9 、 验证命令 : 在 148机器上 执行 ssh 147发现主机名由 148变成 147即成功，最后 删除 id_rsa.pub 文件 :rm -r id_rsa.pub</span><br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">问题出现了：</span><br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">148机器已经生产rsa密钥</span><br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">且已经将public key添加到47机器/root/.ssh/authorized_keys</span><br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">但是ssh root@147机器时仍然需要输入密码，即无密码认证失败，</span><br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">解决办法：</span><br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">查看权限：</span><br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">用ssh -v debug访问，日志如下，但是从日志看不到失败原因，只知道在用publickey认证时，对端没有reply;</span><br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">再查看/var/log/secure日志</span><br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">权限问题总结如下：</span><br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">1) .ssh目录的权限必须是700</span><br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">2) 用户目录的权限必须是700，比如我是用root用户操作的，则/root的权限必须是700</span><br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">3) .ssh/authorized_keys文件权限必须是600</span><br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<p>
	<span style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">4)setenforce 0把SELinux关闭(很重要)</span> 
</p>
<p>
	<br />
</p>
<p>
	<span style="font-family:Arial;"><span style="font-size:14px;background-color:#FFFFFF;">Bitvise 导入的是private key</span></span> 
</p>