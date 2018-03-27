<p style="border:0px;margin-top:0px;margin-bottom:20px;padding:0px;outline:none;line-height:1.8;font-size:16px;overflow:hidden;color:#273746;font-family:Arial, &quot;white-space:normal;background-color:#FFFFFF;">
	CentOS 7系统服务启动、重启、设置服务启动项命令以合并为,systemctl . 现在用service 或/etc/init.d/命令,重启,重新启动,停止等没效果,因为命令合并为systemctl. 新命令具体内容如下:
</p>
<p style="border:0px;margin-top:0px;margin-bottom:20px;padding:0px;outline:none;line-height:1.8;font-size:16px;overflow:hidden;color:#273746;font-family:Arial, &quot;white-space:normal;background-color:#FFFFFF;">
	以启动httpd和设置Apache httpd为服务启动为例子:
</p>
<p style="border:0px;margin-top:0px;margin-bottom:20px;padding:0px;outline:none;line-height:1.8;font-size:16px;overflow:hidden;color:#273746;font-family:Arial, &quot;white-space:normal;background-color:#FFFFFF;">
	<strong style="border:0px;margin:0px;padding:0px;outline:none;">CentOS 7之前的命令是这样:</strong>
</p>
<p style="border:0px;margin-top:0px;margin-bottom:20px;padding:0px;outline:none;line-height:1.8;font-size:16px;overflow:hidden;color:#273746;font-family:Arial, &quot;white-space:normal;background-color:#FFFFFF;">
	service httpd start 启动Apache httpd
</p>
<p style="border:0px;margin-top:0px;margin-bottom:20px;padding:0px;outline:none;line-height:1.8;font-size:16px;overflow:hidden;color:#273746;font-family:Arial, &quot;white-space:normal;background-color:#FFFFFF;">
	service httpd restart 重新启动
</p>
<p style="border:0px;margin-top:0px;margin-bottom:20px;padding:0px;outline:none;line-height:1.8;font-size:16px;overflow:hidden;color:#273746;font-family:Arial, &quot;white-space:normal;background-color:#FFFFFF;">
	service httpd stop 停止服务
</p>
<p style="border:0px;margin-top:0px;margin-bottom:20px;padding:0px;outline:none;line-height:1.8;font-size:16px;overflow:hidden;color:#273746;font-family:Arial, &quot;white-space:normal;background-color:#FFFFFF;">
	chkconfig –levels 235 httpd on 开机启动httpd
</p>
<p style="border:0px;margin-top:0px;margin-bottom:20px;padding:0px;outline:none;line-height:1.8;font-size:16px;overflow:hidden;color:#273746;font-family:Arial, &quot;white-space:normal;background-color:#FFFFFF;">
	或是:
</p>
<p style="border:0px;margin-top:0px;margin-bottom:20px;padding:0px;outline:none;line-height:1.8;font-size:16px;overflow:hidden;color:#273746;font-family:Arial, &quot;white-space:normal;background-color:#FFFFFF;">
	/etc/init.d/ httpd start 启动
</p>
<p style="border:0px;margin-top:0px;margin-bottom:20px;padding:0px;outline:none;line-height:1.8;font-size:16px;overflow:hidden;color:#273746;font-family:Arial, &quot;white-space:normal;background-color:#FFFFFF;">
	/etc/init.d/ httpd restart 重新启动
</p>
<p style="border:0px;margin-top:0px;margin-bottom:20px;padding:0px;outline:none;line-height:1.8;font-size:16px;overflow:hidden;color:#273746;font-family:Arial, &quot;white-space:normal;background-color:#FFFFFF;">
	/etc/init.d/ httpd stop 停止服务
</p>
<p style="border:0px;margin-top:0px;margin-bottom:20px;padding:0px;outline:none;line-height:1.8;font-size:16px;overflow:hidden;color:#273746;font-family:Arial, &quot;white-space:normal;background-color:#FFFFFF;">
	CentOS 7吧这些命令全部合并了,使用也更加方便,当然也是习惯问题,如果习惯了之前命令,centos新命令还得适应适应,其实很简单,只要这样记忆,使用就比较方便了.
</p>
<p style="border:0px;margin-top:0px;margin-bottom:20px;padding:0px;outline:none;line-height:1.8;font-size:16px;overflow:hidden;color:#273746;font-family:Arial, &quot;white-space:normal;background-color:#FFFFFF;">
	systemctl 动作 服务名.service
</p>
<p style="border:0px;margin-top:0px;margin-bottom:20px;padding:0px;outline:none;line-height:1.8;font-size:16px;overflow:hidden;color:#273746;font-family:Arial, &quot;white-space:normal;background-color:#FFFFFF;">
	<strong style="border:0px;margin:0px;padding:0px;outline:none;">一些centos7 systemctl命令简单实用实例:</strong>
</p>
<p style="border:0px;margin-top:0px;margin-bottom:20px;padding:0px;outline:none;line-height:1.8;font-size:16px;overflow:hidden;color:#273746;font-family:Arial, &quot;white-space:normal;background-color:#FFFFFF;">
	systemctl start httpd.service /启动Apache httpd
</p>
<p style="border:0px;margin-top:0px;margin-bottom:20px;padding:0px;outline:none;line-height:1.8;font-size:16px;overflow:hidden;color:#273746;font-family:Arial, &quot;white-space:normal;background-color:#FFFFFF;">
	systemctl restart httpd.service /重新启动
</p>
<p style="border:0px;margin-top:0px;margin-bottom:20px;padding:0px;outline:none;line-height:1.8;font-size:16px;overflow:hidden;color:#273746;font-family:Arial, &quot;white-space:normal;background-color:#FFFFFF;">
	systemctl stop httpd.service /停止服务
</p>
<p style="border:0px;margin-top:0px;margin-bottom:20px;padding:0px;outline:none;line-height:1.8;font-size:16px;overflow:hidden;color:#273746;font-family:Arial, &quot;white-space:normal;background-color:#FFFFFF;">
	systemctl enable httpd.service /开机启动httpd
</p>
<p style="border:0px;margin-top:0px;margin-bottom:20px;padding:0px;outline:none;line-height:1.8;font-size:16px;overflow:hidden;color:#273746;font-family:Arial, &quot;white-space:normal;background-color:#FFFFFF;">
	systemctl disable httpd.service /禁止开机启动httpd
</p>
<p style="border:0px;margin-top:0px;margin-bottom:20px;padding:0px;outline:none;line-height:1.8;font-size:16px;overflow:hidden;color:#273746;font-family:Arial, &quot;white-space:normal;background-color:#FFFFFF;">
	systemctl status httpd.service /httpd当前状态
</p>