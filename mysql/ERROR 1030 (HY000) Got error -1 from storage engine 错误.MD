<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	遇到这个问题 真是快要崩溃，放弃了 ：<strong style="box-sizing:border-box;">ERROR 1030 (HY000): Got error -1 from storage engine</strong>
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	该错误操作步骤为，从一台服务器通过 phpmyadmin 导出的数据库，想导入到另外一台服务器，查看 MySQL 用户手册，在my.ini 中加入了&nbsp;<strong style="box-sizing:border-box;">innodb_force_recovery = 4</strong>
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	然后通过命令
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<strong style="box-sizing:border-box;">mysql -u root -p</strong>
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<strong style="box-sizing:border-box;">use &lt;databasename&gt;</strong>
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<strong style="box-sizing:border-box;">source &lt;path&gt;</strong>
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<strong style="box-sizing:border-box;"><br style="box-sizing:border-box;" />
</strong>
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<strong style="box-sizing:border-box;">ERROR 1030 (HY000): Got error -1 from storage engine</strong>
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	万念俱灰，
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	终于发现是&nbsp;<strong style="box-sizing:border-box;">innodb_force_recovery = 4&nbsp;</strong>的问题，应该设为&nbsp;<strong style="box-sizing:border-box;">innodb_force_recovery = 0</strong>&nbsp;，再重新导入，就OK。
</p>