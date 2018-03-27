<p style="margin-top:0px;margin-bottom:0px;padding:10px 0px;color:#333333;font-family:&quot;font-size:17px;white-space:normal;background-color:#FFFFFF;">
	今天遇到个问题,就是在mysql数据库新建或者保存表的时候会提示
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:10px 0px;color:#333333;font-family:&quot;font-size:17px;white-space:normal;background-color:#FFFFFF;">
	1548-Cannot&nbsp;load&nbsp;from&nbsp;mysql.proc.&nbsp;The&nbsp;table&nbsp;is&nbsp;probably&nbsp;corrupted
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:10px 0px;color:#333333;font-family:&quot;font-size:17px;white-space:normal;background-color:#FFFFFF;">
	新建不了表,刚刚开始以为是用户的权限出现问题,用root超级管理员登陆后也一样的提示..这个时候怀疑是数据库本身有问题,重启数据库后发现问题依然存在,于是拿出万能的百度,很快找到解决办法!!
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:10px 0px;color:#333333;font-family:&quot;font-size:17px;white-space:normal;background-color:#FFFFFF;">
	解决方法为:&nbsp;在dos下输入&nbsp;mysql_upgrade&nbsp;-uroot&nbsp;-p&nbsp;回车后会要求您输入密码,输入完密码后他会自动滚屏,提示一大堆ok什么之类的提示!!
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:10px 0px;color:#333333;font-family:&quot;font-size:17px;white-space:normal;background-color:#FFFFFF;">
	等他运行完毕后在连接数据库,进去新建表则一切正常!!
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:10px 0px;color:#333333;font-family:&quot;font-size:17px;white-space:normal;background-color:#FFFFFF;">
	问题解决了!!!
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:10px 0px;color:#333333;font-family:&quot;font-size:17px;white-space:normal;background-color:#FFFFFF;">
	什么原理我不清楚,只是找到个解决办法,特地记录以备后来需要的时候能查找到!!
</p>