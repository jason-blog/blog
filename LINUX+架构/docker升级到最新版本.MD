<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
	&nbsp; &nbsp; &nbsp;1：首先执行docker -v &nbsp;， 查看当前版本
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
	&nbsp; &nbsp; &nbsp;<img src="http://blog.csdn.net/mellymengyan/article/details/77895905" alt="" style="border-width:initial;border-style:none;max-width:602px;max-height:100%;height:auto;" />
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
	&nbsp; &nbsp; &nbsp;2：执行：&nbsp;rpm -qa | grep docker &nbsp;， 查看当前存在的docker旧版
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
	&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;有就执行apt remove XXXXX命令将其删除，没有就进行下一步
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
	&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;（我就没有旧版，直接安装新版本）
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
	&nbsp; &nbsp; &nbsp;3：从源下载最新版本：curl -fsSL https://get.docker.com/ | sh &nbsp; &nbsp; &nbsp;&nbsp;<img src="http://blog.csdn.net/mellymengyan/article/details/77895905" alt="" style="border-width:initial;border-style:none;max-width:602px;max-height:100%;height:auto;" />
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
	&nbsp; &nbsp; &nbsp; &nbsp;最后出现该画面表明更新完毕：
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;&nbsp;<img src="http://blog.csdn.net/mellymengyan/article/details/77895905" alt="" style="border-width:initial;border-style:none;max-width:602px;max-height:100%;height:auto;" />
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
	&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;4：这时候重新启动docker 服务：&nbsp;systemctl restart docker
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
	&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;5：查看版本：&nbsp;docker version # docker -v
</p>