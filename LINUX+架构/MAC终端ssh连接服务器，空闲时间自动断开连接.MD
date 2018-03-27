<h1 style="font-family:&quot;margin:8px 0px 16px;padding:0px;box-sizing:border-box;color:#4F4F4F;font-size:28px;line-height:36px;white-space:normal;background-color:#FFFFFF;">
	方法一 ： &nbsp;&nbsp;<span style="margin:0px;padding:0px;font-weight:400;box-sizing:border-box;font-family:&quot;font-size:14px;">配置“/etc/ssh/ssh_config”文件</span>
</h1>
<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;font-size:16px;color:#4F4F4F;line-height:26px;min-height:26px;text-align:justify;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
	<br />
</p>
<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;font-size:16px;color:#4F4F4F;line-height:26px;min-height:26px;text-align:justify;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
	（60有点长 我改成20了好用）
</p>
<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;font-size:16px;color:#4F4F4F;line-height:26px;min-height:26px;text-align:justify;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
	1 打开MAC终端 &nbsp;<span style="margin:0px;padding:0px;box-sizing:border-box;font-family:&quot;font-size:14px;">/etc/ssh/ &nbsp; enter</span>
</p>
<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;font-size:16px;color:#4F4F4F;line-height:26px;min-height:26px;text-align:justify;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;box-sizing:border-box;font-family:&quot;font-size:14px;">2 sudo vim&nbsp;<span style="margin:0px;padding:0px;box-sizing:border-box;">ssh_config (必须用管理员权限编辑，否则无法编辑)</span></span>
</p>
<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;font-size:16px;color:#4F4F4F;line-height:26px;min-height:26px;text-align:justify;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;box-sizing:border-box;font-family:&quot;font-size:14px;"><span style="margin:0px;padding:0px;box-sizing:border-box;">3 shift + i 进入编辑模式， &nbsp;在host*下面加入&nbsp;<span style="margin:0px;padding:0px;box-sizing:border-box;"><span class="tcnt" style="margin:0px;padding:0px;box-sizing:border-box;">ServerAliveInterval 60 &nbsp; 一项， 如下图</span></span></span></span>
</p>
<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;font-size:16px;color:#4F4F4F;line-height:26px;min-height:26px;text-align:justify;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;box-sizing:border-box;font-family:&quot;font-size:14px;"><img src="http://img.blog.csdn.net/20170711160033272?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvU2FuZHlMb28=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center" alt="" style="outline:0px;box-sizing:border-box;max-width:100%;margin:0px;" /><br style="box-sizing:border-box;" />
</span>
</p>
<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;font-size:16px;color:#4F4F4F;line-height:26px;min-height:26px;text-align:justify;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;box-sizing:border-box;font-family:&quot;font-size:14px;">4 &nbsp;shift + : 输入wq退出</span>
</p>
<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;font-size:16px;color:#4F4F4F;line-height:26px;min-height:26px;text-align:justify;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;box-sizing:border-box;font-family:&quot;font-size:14px;">5 到此完成， 连接你的服务器试试效果吧。&nbsp;</span>
</p>
<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;font-size:16px;color:#4F4F4F;line-height:26px;min-height:26px;text-align:justify;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
	<br />
</p>