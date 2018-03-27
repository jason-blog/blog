<div style="border-width:0px;padding:0px;margin:0px;list-style:none;color:#333333;font-family:宋体;font-size:14px;white-space:normal;background-color:#F9F9F9;">
	dpkg: error processing /var/cache/apt/archives/python-apport_2.0.1-0ubuntu9_all.deb解决方法
</div>
<div style="border-width:0px;padding:0px;margin:0px;list-style:none;color:#333333;font-family:宋体;font-size:14px;white-space:normal;background-color:#F9F9F9;">
	&nbsp;
</div>
<div style="border-width:0px;padding:0px;margin:0px;list-style:none;color:#333333;font-family:宋体;font-size:14px;white-space:normal;background-color:#F9F9F9;">
	如果在使用apt-get时出现类似下面错误：
</div>
<div style="border-width:0px;padding:0px;margin:0px;list-style:none;color:#333333;font-family:宋体;font-size:14px;white-space:normal;background-color:#F9F9F9;">
	&nbsp;
</div>
<div style="border-width:0px;padding:0px;margin:0px;list-style:none;color:#333333;font-family:宋体;font-size:14px;white-space:normal;background-color:#F9F9F9;">
	dpkg: error processing /var/cache/apt/archives/python-apport_2.0.1-0ubuntu9_all.deb
</div>
<div style="border-width:0px;padding:0px;margin:0px;list-style:none;color:#333333;font-family:宋体;font-size:14px;white-space:normal;background-color:#F9F9F9;">
	&nbsp;
</div>
<div style="border-width:0px;padding:0px;margin:0px;list-style:none;color:#333333;font-family:宋体;font-size:14px;white-space:normal;background-color:#F9F9F9;">
	解决方法：
</div>
<div style="border-width:0px;padding:0px;margin:0px;list-style:none;color:#333333;font-family:宋体;font-size:14px;white-space:normal;background-color:#F9F9F9;">
	&nbsp;
</div>
<div style="border-width:0px;padding:0px;margin:0px;list-style:none;color:#333333;font-family:宋体;font-size:14px;white-space:normal;background-color:#F9F9F9;">
	[plain]&nbsp;
</div>
<div style="border-width:0px;padding:0px;margin:0px;list-style:none;color:#333333;font-family:宋体;font-size:14px;white-space:normal;background-color:#F9F9F9;">
	sudo dpkg -i --force-overwrite /var/cache/apt/archives/python-problem-report_2.0.1-0ubuntu9_all.deb &nbsp;<br />
&nbsp;
</div>
<div style="border-width:0px;padding:0px;margin:0px;list-style:none;color:#333333;font-family:宋体;font-size:14px;white-space:normal;background-color:#F9F9F9;">
	sudo apt-get -f install &nbsp;
</div>
<div style="border-width:0px;padding:0px;margin:0px;list-style:none;color:#333333;font-family:宋体;font-size:14px;white-space:normal;background-color:#F9F9F9;">
	&nbsp;
</div>