<p style="font-size:14px;white-space:normal;background-color:#FFFFFF;clear:both;overflow:hidden;color:#555555;line-height:28px;font-family:宋体, &quot;height:auto;">
	<span style="color:#000000;">sshpass下载地址：http://sourceforge<a href="http://lib.csdn.net/base/dotnet" class="replace_word" title=".NET知识库" target="_blank" style="color:#DF3434;text-decoration:none;font-weight:bold;">.NET</a>/projects/sshpass/</span>
</p>
<p style="font-size:14px;white-space:normal;background-color:#FFFFFF;clear:both;overflow:hidden;color:#555555;line-height:28px;font-family:宋体, &quot;height:auto;">
	<span style="color:#000000;"><strong style="padding:0px;margin:0px;">安装</strong></span>
</p>
<p style="font-size:14px;white-space:normal;background-color:#FFFFFF;clear:both;overflow:hidden;color:#555555;line-height:28px;font-family:宋体, &quot;height:auto;">
	<span style="color:#000000;">tar zxvf sshpass-1.05.tar.gz</span>
</p>
<p style="font-size:14px;white-space:normal;background-color:#FFFFFF;clear:both;overflow:hidden;color:#555555;line-height:28px;font-family:宋体, &quot;height:auto;">
	<span style="color:#000000;">cd sshpass-1.05</span>
</p>
<p style="font-size:14px;white-space:normal;background-color:#FFFFFF;clear:both;overflow:hidden;color:#555555;line-height:28px;font-family:宋体, &quot;height:auto;">
	<span style="color:#000000;">./configure --prefix=/opt/sshpass</span>
</p>
<p style="font-size:14px;white-space:normal;background-color:#FFFFFF;clear:both;overflow:hidden;color:#555555;line-height:28px;font-family:宋体, &quot;height:auto;">
	<span style="color:#000000;">make</span>
</p>
<p style="font-size:14px;white-space:normal;background-color:#FFFFFF;clear:both;overflow:hidden;color:#555555;line-height:28px;font-family:宋体, &quot;height:auto;">
	<span style="color:#000000;">make install</span>
</p>
<p style="font-size:14px;white-space:normal;background-color:#FFFFFF;clear:both;overflow:hidden;color:#555555;line-height:28px;font-family:宋体, &quot;height:auto;">
	<span style="color:#000000;"><strong style="padding:0px;margin:0px;">结合使用：</strong></span>
</p>
<p style="font-size:14px;white-space:normal;background-color:#FFFFFF;clear:both;overflow:hidden;color:#555555;line-height:28px;font-family:宋体, &quot;height:auto;">
	<span style="color:#000000;">sshpass 和ssh,scp,sftp一起使用</span>
</p>
<p style="font-size:14px;white-space:normal;background-color:#FFFFFF;clear:both;overflow:hidden;color:#555555;line-height:28px;font-family:宋体, &quot;height:auto;">
	<span style="color:#000000;"><strong style="padding:0px;margin:0px;">实例：</strong>&nbsp;</span>
</p>
<p style="font-size:14px;white-space:normal;background-color:#FFFFFF;clear:both;overflow:hidden;color:#555555;line-height:28px;font-family:宋体, &quot;height:auto;">
	<span style="color:#000000;">[root@fs bin]# ./sshpass -p 123456 &nbsp;ssh -o StrictHostKeyChecking=no &nbsp; &nbsp;root@192.168.1.15 "ls -t | head -n 1"</span>
</p>
<p style="font-size:14px;white-space:normal;background-color:#FFFFFF;clear:both;overflow:hidden;color:#555555;line-height:28px;font-family:宋体, &quot;height:auto;">
	<span style="color:#000000;">[root@fs bin]# ./sshpass -p 123456 scp -o StrictHostKeyChecking=no &nbsp;/root/abc.sh &nbsp;192.168.1.15:/root</span>
</p>
<p style="font-size:14px;white-space:normal;background-color:#FFFFFF;clear:both;overflow:hidden;color:#555555;line-height:28px;font-family:宋体, &quot;height:auto;">
	<span style="color:#000000;">-p:指定ssh的密码</span>
</p>
<p style="font-size:14px;white-space:normal;background-color:#FFFFFF;clear:both;overflow:hidden;color:#555555;line-height:28px;font-family:宋体, &quot;height:auto;">
	<span style="color:#000000;">-o StrictHostKeyChecking=no 避免第一次登录出现公钥检查。也就是避免出现</span>
</p>
<p style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	sshpass: 用于非交互的ssh 密码验证
</p>
<div style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;line-height:26px;">
	&nbsp;ssh登陆不能在命令行中指定密码，也不能以shell中随处可见的，sshpass 的出现，解决了这一问题。它允许你用 -p 参数指定明文密码，然后直接登录远程服务器。 它支持密码从命令行,文件,环境变量中读取
</div>
<div style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;line-height:26px;">
	$&gt; sshpass -h
</div>
<div style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;line-height:26px;">
	&nbsp;Usage: sshpass [-f|-d|-p|-e] [-hV] command parameters
</div>
<div style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;line-height:26px;">
	&nbsp;&nbsp; -f filename Take password to use from file
</div>
<div style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;line-height:26px;">
	&nbsp;&nbsp; -d number Use number as file descriptor for getting password
</div>
<div style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;line-height:26px;">
	&nbsp;&nbsp; -p password Provide password as argument (security unwise)
</div>
<div style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;line-height:26px;">
	&nbsp;&nbsp; -e Password is passed as env-var "SSHPASS"
</div>
<div style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;line-height:26px;">
	&nbsp;&nbsp; With no parameters - password will be taken from stdin
</div>
<div style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;line-height:26px;">
	&nbsp;&nbsp;-h Show help (this screen)
</div>
<div style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;line-height:26px;">
	&nbsp;&nbsp; -V Print version information
</div>
<div style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;line-height:26px;">
	At most one of -f, -d, -p or -e should be used
</div>
<div style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;line-height:26px;">
	&nbsp;sshpass [-f|-d|-p|-e] [-hV] command parameters 中的 command parameters 和使用交互式密码验证的使用方法相同
</div>
<div style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;line-height:26px;">
	&nbsp;#从命令行方式传递密码
</div>
<div style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;line-height:26px;">
	&nbsp; &nbsp;&nbsp;$&gt; sshpass -p user_password ssh user_name@192.168..1.2
</div>
<div style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;line-height:26px;">
	&nbsp;&nbsp;&nbsp; $&gt; sshpass -p user_password scp -P22 192.168.1.2:/home/test/t .&nbsp;
</div>
<div style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;line-height:26px;">
	&nbsp;#从文件读取密码
</div>
<div style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;line-height:26px;">
	&nbsp; &nbsp; &nbsp;$&gt;　echo "user_password" &gt; user.passwd
</div>
<div style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;line-height:26px;">
	&nbsp;&nbsp;&nbsp; $&gt; sshpass -f user.passwd ssh user_name@192.168..1.2
</div>
<div style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;line-height:26px;">
	&nbsp;#从环境变量获取密码
</div>
<div style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;line-height:26px;">
	&nbsp; &nbsp; $&gt; export SSHPASS="user_password"
</div>
<div style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;line-height:26px;">
	&nbsp;&nbsp;&nbsp; $&gt; sshpass -e ssh user_name@192.168..1.2&nbsp;
</div>
<div style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;line-height:26px;">
	<span style="font-family:Tahoma, Helvetica, Arial, STHeiti;font-size:12px;color:#454545;line-height:21px;">----------------------------------------------------------------------------------------------------</span>
</div>
<div style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;line-height:26px;">
	<span style="font-family:Tahoma, Helvetica, Arial, STHeiti;color:#454545;line-height:21px;">用sshpass实现ssh的自动登陆&nbsp;</span>
</div>
<div style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;line-height:26px;">
	<p style="color:#454545;line-height:21px;font-family:Tahoma, Helvetica, Arial, STHeiti;">
		要实现ssh自动登录，网上搜了一下，主要有两种方法：1、生成公钥。2、编写expect脚本。这两种方法，用起来都有点复杂。在新立得上安装ssh的时候，偶然发现一个sshpass，百度谷歌之，英文资料甚多，而中文资料寥寥。其实sshpass的用法很简单。<br />
用法：<br />
&nbsp;&nbsp;&nbsp; sshpass 参数 SSH命令(ssh，sftp，scp等)。<br />
&nbsp;&nbsp;&nbsp; 参数:<br />
&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; -p password&nbsp;&nbsp;&nbsp; //将参数password作为密码。<br />
&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; -f passwordfile //提取文件passwordfile的第一行作为密码。<br />
&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; -e&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; //将环境变量SSHPASS作为密码。<br />
&nbsp;&nbsp;&nbsp; 比如说：<br />
&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; scp abc@192.168.0.5:/home/xxx/test /root&nbsp;&nbsp; 这个命令的作用是将服务器端文件test传到本地文件夹/root下。<br />
&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; 利用sshpass，假设密码为efghi，则可写作：<br />
&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; ssh -p efghi scp abc@192.168.0.5:/home/xxx/test /root<br />
另外，对于ssh的第一次登陆，会提示：“Are you sure you want to continue connecting (yes/no)”，这时用sshpass会不好使，可以在ssh命令后面加上 -o StrictHostKeyChecking=no来解决。比如说上面的命令，就可以写作ssh -p efghi scp abc@192.168.0.5:/home/xxx/test /root -o StrictHostKeyChecking=no。
	</p>
</div>