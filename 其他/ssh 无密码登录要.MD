<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	ssh 无密码登录要使用公钥与私钥。linux下可以用用ssh-keygen生成公钥/私钥对，下面我以CentOS为例。<br />
有机器A(192.168.1.155)，B(192.168.1.181)。现想A通过ssh免密码登录到B。<br />
1.在A机下生成公钥/私钥对。
</p>
<div style="font-family:Helvetica, Tahoma, Arial, sans-serif;white-space:normal;border-width:1px;border-style:solid;border-color:#CCCCCC;padding:4px 5px 4px 4px;font-size:13px;width:686px;background-color:#EEEEEE;">
	[chenlb@A&nbsp;~]$&nbsp;ssh-keygen&nbsp;-t&nbsp;rsa&nbsp;-P&nbsp;<span style="color:#800000;">''</span>
</div>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<br />
-P表示密码，-P '' 就表示空密码，也可以不用-P参数，这样就要三车回车，用-P就一次回车。<br />
它在/home/chenlb下生成.ssh目录，.ssh下有id_rsa和id_rsa.pub。<br />
2.把A机下的id_rsa.pub复制到B机下，在B机的.ssh/authorized_keys文件里，我用scp复制。
</p>
<div style="font-family:Helvetica, Tahoma, Arial, sans-serif;white-space:normal;border-width:1px;border-style:solid;border-color:#CCCCCC;padding:4px 5px 4px 4px;font-size:13px;width:686px;background-color:#EEEEEE;">
	[chenlb@A&nbsp;~]$&nbsp;scp&nbsp;.ssh/id_rsa.pub&nbsp;chenlb@192.168.1.181:/home/chenlb/id_rsa.pub&nbsp;<br />
chenlb@192.168.1.181<span style="color:#800000;">'</span><span style="color:#800000;">s&nbsp;password:</span><span style="color:#800000;"><br />
</span>id_rsa.pub&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;100%&nbsp;&nbsp;223&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;0.2KB/s&nbsp;&nbsp;&nbsp;00:00
</div>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<br />
由于还没有免密码登录的，所以要输入密码。<br />
3.B机把从A机复制的id_rsa.pub添加到.ssh/authorzied_keys文件里。
</p>
<div style="font-family:Helvetica, Tahoma, Arial, sans-serif;white-space:normal;border-width:1px;border-style:solid;border-color:#CCCCCC;padding:4px 5px 4px 4px;font-size:13px;width:686px;background-color:#EEEEEE;">
	[chenlb@B&nbsp;~]$&nbsp;cat&nbsp;id_rsa.pub&nbsp;&gt;&gt;&nbsp;.ssh/authorized_keys<br />
[chenlb@B&nbsp;~]$&nbsp;chmod&nbsp;600&nbsp;.ssh/authorized_keys
</div>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<br />
<strong style="color:#FF6600;">authorized_keys的权限要是600</strong>。<br />
4.A机登录B机。
</p>
<div style="font-family:Helvetica, Tahoma, Arial, sans-serif;white-space:normal;border-width:1px;border-style:solid;border-color:#CCCCCC;padding:4px 5px 4px 4px;font-size:13px;width:686px;background-color:#EEEEEE;">
	[chenlb@A&nbsp;~]$&nbsp;ssh&nbsp;192.168.1.181<br />
The&nbsp;authenticity&nbsp;of&nbsp;host&nbsp;<span style="color:#800000;">'</span><span style="color:#800000;">192.168.1.181&nbsp;(192.168.1.181)</span><span style="color:#800000;">'</span>&nbsp;can<span style="color:#800000;">'</span><span style="color:#800000;">t&nbsp;be&nbsp;established.</span><span style="color:#800000;"><br />
</span>RSA&nbsp;key&nbsp;fingerprint&nbsp;<span style="color:#0000FF;">is</span>&nbsp;00:a6:a8:87:eb:c7:40:10:39:cc:a0:eb:50:d9:6a:5b.<br />
Are&nbsp;you&nbsp;sure&nbsp;you&nbsp;want&nbsp;to&nbsp;<span style="color:#0000FF;">continue</span>&nbsp;connecting&nbsp;(yes/no)?&nbsp;yes<br />
Warning:&nbsp;Permanently&nbsp;added&nbsp;<span style="color:#800000;">'</span><span style="color:#800000;">192.168.1.181</span><span style="color:#800000;">'</span>&nbsp;(RSA)&nbsp;to&nbsp;the&nbsp;list&nbsp;of&nbsp;known&nbsp;hosts.<br />
Last&nbsp;login:&nbsp;Thu&nbsp;Jul&nbsp;&nbsp;3&nbsp;09:53:18&nbsp;2008&nbsp;<span style="color:#0000FF;">from</span>&nbsp;chenlb<br />
[chenlb@B&nbsp;~]$
</div>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<br />
第一次登录是时要你输入yes。<br />
现在A机可以无密码登录B机了。<br />
小结：登录的机子可有私钥，被登录的机子要有登录机子的公钥。这个公钥/私钥对一般在私钥宿主机产生。上面是用rsa算法的公钥/私钥对，当然也可以用dsa(对应的文件是id_dsa，id_dsa.pub)<br />
想让A，B机无密码互登录，那B机以上面同样的方式配置即可。
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<br />
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<br />
</p>