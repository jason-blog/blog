<p style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;margin-top:0px;margin-bottom:0px;padding-top:0px;padding-bottom:0px;color:#333333;line-height:26px;">
	<strong><span style="font-size:18px;">遇到问题描述：</span></strong>
</p>
<p style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;margin-top:0px;margin-bottom:0px;padding-top:0px;padding-bottom:0px;color:#333333;line-height:26px;">
	运行<a href="http://lib.csdn.net/base/android" class="replace_word" title="Android知识库" target="_blank" style="color:#DF3434;text-decoration:none;font-weight:bold;">Android</a>程序控制台输出
</p>
<p style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;margin-top:0px;margin-bottom:0px;padding-top:0px;padding-bottom:0px;color:#333333;line-height:26px;">
	&nbsp;&nbsp; &nbsp;[2013-10-13 16:45:50 - ] The connection to adb is down, and a severe error has occured.<br />
&nbsp;&nbsp; &nbsp;[<span style="line-height:26px;">2013-10-13</span><span style="line-height:26px;">16:45:50</span>&nbsp;- ] You must restart adb and Eclipse.<br />
&nbsp;&nbsp; &nbsp;[<span style="line-height:26px;">2013-10-13</span><span style="line-height:26px;">16:45:50</span>&nbsp;- ] Please ensure that adb is correctly located at '&lt;--此处显示adb.exe的全路径--&gt;' and can be executed.
</p>
<p style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;margin-top:0px;margin-bottom:0px;padding-top:0px;padding-bottom:0px;color:#333333;line-height:26px;">
	&nbsp;
</p>
<p style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;margin-top:0px;margin-bottom:0px;padding-top:0px;padding-bottom:0px;color:#333333;line-height:26px;">
	<span style="line-height:26px;">&nbsp;&nbsp;<strong><span style="font-size:18px;">问题分析1</span></strong></span>：
</p>
<p style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;margin-top:0px;margin-bottom:0px;padding-top:0px;padding-bottom:0px;color:#333333;line-height:26px;">
	<span style="white-space:pre;"></span>关闭eclipse，打开windows任务管理器，查看进程中是否有adb.exe或adb.exe *32。
</p>
<p style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;margin-top:0px;margin-bottom:0px;padding-top:0px;padding-bottom:0px;color:#333333;line-height:26px;">
	<span style="line-height:26px;">&nbsp;&nbsp;<strong><span style="font-size:18px;">解决方案1</span></strong>：</span>
</p>
<p style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;margin-top:0px;margin-bottom:0px;padding-top:0px;padding-bottom:0px;color:#333333;line-height:26px;">
	<span style="white-space:pre;"></span>如果有则关闭该进程，重新启动eclipse即可；
</p>
<p style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;margin-top:0px;margin-bottom:0px;padding-top:0px;padding-bottom:0px;color:#333333;line-height:26px;">
	<strong><span style="font-size:18px;">&nbsp;&nbsp;<span style="line-height:26px;">问题分析</span>2：</span></strong>
</p>
<p style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;margin-top:0px;margin-bottom:0px;padding-top:0px;padding-bottom:0px;color:#333333;line-height:26px;">
	<span style="white-space:pre;"></span>windows任务管理器中就找不到<span style="line-height:26px;">adb.exe或adb.exe *32的进程，可以尝试手动启动adb.exe ；如果手动启动后还找不到adb.exe进程，则 &nbsp; &nbsp;只有一种可能就是adb.exe进程的端口被占用，导致adb.exe未能正常启动所致（adb默认端口为5037）。</span>
</p>
<p style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;margin-top:0px;margin-bottom:0px;padding-top:0px;padding-bottom:0px;color:#333333;line-height:26px;">
	<span style="line-height:26px;">&nbsp;</span><span style="line-height:26px;"><span style="font-size:18px;"><strong>&nbsp;<span style="line-height:26px;">解决方案2：</span></strong></span></span>
</p>
<p style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;margin-top:0px;margin-bottom:0px;padding-top:0px;padding-bottom:0px;color:#333333;line-height:26px;">
	<span style="line-height:26px;">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;1、查看端口使用情况：</span>
</p>
<p style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;margin-top:0px;margin-bottom:0px;padding-top:0px;padding-bottom:0px;color:#333333;line-height:26px;">
	<span style="line-height:26px;">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;</span>netstat -aon|findstr "5037"
</p>
<p style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;margin-top:0px;margin-bottom:0px;padding-top:0px;padding-bottom:0px;color:#333333;line-height:26px;">
	&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; TCP &nbsp; &nbsp;127.0.0.1:5037 &nbsp; &nbsp; &nbsp; &nbsp; 0.0.0.0:0 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;LISTENING &nbsp; &nbsp; &nbsp; 5004
</p>
<p style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;margin-top:0px;margin-bottom:0px;padding-top:0px;padding-bottom:0px;color:#333333;line-height:26px;">
	&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 2、发现5004占用5037端口，查看5004的task：
</p>
<p style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;margin-top:0px;margin-bottom:0px;padding-top:0px;padding-bottom:0px;color:#333333;line-height:26px;">
	&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;tasklist|findstr "5004"
</p>
<p style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;margin-top:0px;margin-bottom:0px;padding-top:0px;padding-bottom:0px;color:#333333;line-height:26px;">
	&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; wandoujia_daemon.exe &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;5004 Console &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;1 &nbsp; &nbsp; &nbsp;4,276 K
</p>
<p style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;margin-top:0px;margin-bottom:0px;padding-top:0px;padding-bottom:0px;color:#333333;line-height:26px;">
	&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 打开windows管理器结束<span style="line-height:26px;">wandoujia_daemon.exe该进程，启动eclipse，如果adb.exe未能启动，手动启动即可；</span>
</p>
<div>
	<br />
</div>