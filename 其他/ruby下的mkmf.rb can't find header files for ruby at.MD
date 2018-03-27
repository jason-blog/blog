<p style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp; &nbsp; 有时候在ruby下使用gem安装包的时候，会报错如下：
</p>
<p style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp; &nbsp; &nbsp;ERROR: &nbsp;Error installing bluecloth: &nbsp;<br />
&nbsp; ERROR: Failed to build gem native extension. &nbsp;<br />
&nbsp;&nbsp;<br />
/System/Library/Frameworks/Ruby.framework/Versions/2.1/usr/bin/ruby &nbsp;<br />
extconf.rb &nbsp;<br />
mkmf.rb can't find header files for ruby at &nbsp;<br />
/System/Library/Frameworks/Ruby.framework/Versions/2.1/usr/lib/ruby/ruby.h&nbsp;
</p>
<p style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<br />
</p>
<p style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;<span style="color:#FF0000;">&nbsp;如果是在centos等系统下面，执行命令：yum &nbsp;install &nbsp; ruby-devel&nbsp;</span>
</p>
<p style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="color:#FF0000;">&nbsp; 如果是在Ubuntu等系统下面，执行命令:apt-get &nbsp;isntall &nbsp; ruby-dev &nbsp;</span>
</p>