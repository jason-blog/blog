<div class="Blog_wz1">
	<p style="padding:0px;">
		<b style="word-wrap:break-word;">mysql</b><b style="word-wrap:break-word;">升级</b><b style="word-wrap:break-word;"></b>
	</p>
	<p style="padding:0px;">
		<b style="word-wrap:break-word;">1&nbsp;</b><b style="word-wrap:break-word;">升级方式</b>
	</p>
	<p style="padding:0px;">
		分为In-place和out-of-place，前者直接覆盖当前版本，后者在新路径安装然后加载数据库；
	</p>
	<p style="padding:0px;">
		升级不可跳级，即5.1要想升级成5.6，必须先升级到5.5；
	</p>
	<p style="padding:0px;">
		注：oracle的out-of-place upgrade采用新binary直接加载原数据文件，而mysql需要导出--导入数据；
	</p>
	<p style="padding:0px;">
		&nbsp;
	</p>
	<p style="padding:0px;">
		&nbsp;
	</p>
	<p style="padding:0px;">
		<b style="word-wrap:break-word;">2</b><b style="word-wrap:break-word;">&nbsp;大致步骤</b>
	</p>
	<p style="padding:0px;">
		1&nbsp;备份
	</p>
	<p style="padding:0px;">
		2&nbsp;升级
	</p>
	<p style="padding:0px;">
		3 mysql_upgrade检查不兼容的表，更新grant表；
	</p>
	<p style="padding:0px;">
		<b style="word-wrap:break-word;">5.5</b><b style="word-wrap:break-word;">升级5.6</b>
	</p>
	<p style="padding:0px;">
		1&nbsp;备份&nbsp;&nbsp;mysqldump –all-databases –routines - events
	</p>
	<p style="padding:0px;">
		2&nbsp;升级前，检查表和索引是否兼容<a href="http://dev.mysql.com/doc/refman/5.6/en/checking-table-incompatibilities.html" style="word-wrap:break-word;text-decoration-line:none;color:#8E0300;">http://dev.mysql.com/doc/refman/5.6/en/checking-table-incompatibilities.html</a>
	</p>
	<p style="padding:0px;">
		3&nbsp;升级后调用mysql_upgrade，
	</p>
	<p style="padding:0px;">
		注：对于大数据库，in-place upgrade可能要花费很长时间进行数据转换，对此可以创建一个dummy实例：包含mysql数据库和其他数据库的结构(不含数据)，升级dummy并查看可能遇到的问题；
	</p>
	<p style="padding:0px;">
		5.6很多参数的默认值都做了调整，详细可参考<a href="http://dev.mysql.com/doc/refman/5.6/en/upgrading-from-previous-series.html" style="word-wrap:break-word;text-decoration-line:none;color:#8E0300;">http://dev.mysql.com/doc/refman/5.6/en/upgrading-from-previous-series.html</a>
	</p>
	<p style="padding:0px;">
		&nbsp;
	</p>
	<p style="padding:0px;">
		&nbsp;
	</p>
	<p style="padding:0px;">
		<b style="word-wrap:break-word;">3 mysql_upgrade</b>
	</p>
	<p style="padding:0px;">
		本质上为一个封装了mysqlcheck命令的脚本，流程如下：
	</p>
<pre style="word-wrap:break-word;margin-top:0px;margin-bottom:0px;padding:0px;"><span style="word-wrap:break-word;">1 </span>mysqlcheck --no-defaults --databases --fix-db-names --fix-table-names mysql</pre>
<pre style="word-wrap:break-word;margin-top:0px;margin-bottom:0px;padding:0px;"><span style="word-wrap:break-word;">2 </span>mysqlcheck --no-defaults --check-upgrade --databases --auto-repair mysql</pre>
<pre style="word-wrap:break-word;margin-top:0px;margin-bottom:0px;padding:0px;"><span style="word-wrap:break-word;">3 </span>mysql &lt; fix_priv_tables</pre>
<pre style="word-wrap:break-word;margin-top:0px;margin-bottom:0px;padding:0px;"><span style="word-wrap:break-word;">4 </span>mysqlcheck --no-defaults --all-databases --skip-database=mysql --fix-db-names --fix-table-names</pre>
<pre style="word-wrap:break-word;margin-top:0px;margin-bottom:0px;padding:0px;"><span style="word-wrap:break-word;">5 </span>mysqlcheck --no-defaults --check-upgrade --all-databases --skip-database=mysql --auto-repair</pre>
	<p style="padding:0px;">
		执行完毕后在数据目录生成mysql_upgrade_info文件，记录检查过的表，下次再调用时可以跳过；
	</p>
	<p style="padding:0px;">
		&nbsp;
	</p>
	<p style="padding:0px;">
		执行步骤
	</p>
	<p style="padding:0px;">
		1检查所有数据表同当前binary的兼容性，若不兼容则尝试修复，修复失败则必须手工执行；
	</p>
	<p style="padding:0px;">
		手工修复：mysqldump重新加载或者null alternation(alter table t engine=innodb)；
	</p>
	<p style="padding:0px;">
		如果仅仅是修改表的collation，则可调用ALTER TABLE t1 CONVERT TO CHARACTER SET utf8 COLLATE utf8_general_mysql500_ci;
	</p>
	<p style="padding:0px;">
		2升级mysql系统表；
	</p>
	<p style="padding:0px;">
		调用mysql_upgrade后，需要重启mysql才能让系统表更新生效；
	</p>
	<p style="padding:0px;">
		如果单机运行了多个mysql实例，则指定连接参数
	</p>
<pre style="word-wrap:break-word;margin-top:0px;margin-bottom:0px;padding:0px;">shell&gt;<b style="word-wrap:break-word;">mysql_upgrade --protocol=tcp -P 3306 [<i style="word-wrap:break-word;">other_options</i>]</b></pre>
<pre style="word-wrap:break-word;margin-top:0px;margin-bottom:0px;padding:0px;">shell&gt;<b style="word-wrap:break-word;">mysql_upgrade --protocol=tcp -P 3307 [<i style="word-wrap:break-word;">other_options</i>]</b></pre>
	<p style="padding:0px;">
		输出结果
	</p>
	<p style="padding:0px;">
		Table upgrade required.
	</p>
	<p style="padding:0px;">
		Please do "REPAIR TABLE `tbl_name`" or dump/reload to fix it!
	</p>
	<p style="padding:0px;">
		&nbsp;
	</p>
	<p style="padding:0px;">
		&nbsp;
	</p>
	<p style="padding:0px;">
		<b style="word-wrap:break-word;">4 Tip</b>
	</p>
	<p style="padding:0px;">
		1&nbsp;可备份old mysqld，如果new mysqld运行出错可迅速切换；
	</p>
	<p style="padding:0px;">
		2对于GA(general availability)版本间的升级，同一架构下的系统可以在两个版本间copy&nbsp;&nbsp;mysql format file和数据文件；
	</p>
	<p style="padding:0px;">
		3&nbsp;不要使用old my.cnf，mysqld –print-defaults检查；
	</p>
	<p style="padding:0px;">
		4重新安装perl DBD::mysql，以及PHP和Python相应的驱动包；
	</p>
	<p style="padding:0px;">
		&nbsp;
	</p>
	<p style="padding:0px;">
		&nbsp;
	</p>
	<p style="padding:0px;">
		<b style="word-wrap:break-word;">5&nbsp;</b><b style="word-wrap:break-word;">升级replication</b>
	</p>
	<p style="padding:0px;">
		同oracle一样，mysql支持low master – high slave复制模式(部分sql可能会出现错误)，顺序颠倒过来则可能遭遇一系列错误(比如binlog不兼容/)，因此升级master前须先升级slave；
	</p>
	<p style="padding:0px;">
		对于需要重建表或索引的操作(collation变化需要重建index)，最安全的办法是各自在master/slave单独执行期间(禁用replication)；
	</p>
	<p style="padding:0px;">
		1&nbsp;关闭slave并升级，以—skip-slave-start选项启动，执行重建
	</p>
	<p style="padding:0px;">
		2 master禁用binlog，执行重建
	</p>
	<p style="padding:0px;">
		3&nbsp;恢复原来设置，slave正常连接master
	</p>
	<p style="padding:0px;">
		注：GTID=on会导致更新mysql系统表(myisam)失败，<a href="http://dev.mysql.com/doc/refman/5.6/en/mysql-upgrade.html" style="word-wrap:break-word;text-decoration-line:none;color:#8E0300;">http://dev.mysql.com/doc/refman/5.6/en/mysql-upgrade.html</a>
	</p>
</div>
<div style="clear:both;">
</div>
<div class="Blog_con2_1 Blog_con3_2" style="margin-top:50px;position:relative;line-height:22px;">
	<div class="bdsharebuttonbox bdshare-button-style0-24" data-bd-bind="1495635913232" style="zoom:1;">
		<a href="http://blog.itpub.net/15480802/viewspace-1412259/#" class="bds_more" data-cmd="more" style="word-wrap:break-word;text-decoration-line:none;color:#333333;float:left;font-size:18px;padding-left:25px;line-height:24px;height:24px;background-image:url(&quot;background-repeat:no-repeat;cursor:pointer;margin:6px 6px 6px 0px;background-position:0px 0px;font-family:宋体, Arial;white-space:normal;background-color:#FFFFFF;"></a><a href="http://blog.itpub.net/15480802/viewspace-1412259/#" class="bds_weixin" data-cmd="weixin" title="分享到微信" style="word-wrap:break-word;text-decoration-line:none;color:#9C2423;float:left;font-size:18px;padding-left:25px;line-height:24px;height:24px;background-image:url(&quot;background-repeat:no-repeat;cursor:pointer;margin:6px 6px 6px 0px;background-position:0px -1612px;font-family:宋体, Arial;white-space:normal;background-color:#FFFFFF;"></a><a href="http://blog.itpub.net/15480802/viewspace-1412259/#" class="bds_tsina" data-cmd="tsina" title="分享到新浪微博" style="word-wrap:break-word;text-decoration-line:none;color:#9C2423;float:left;font-size:18px;padding-left:25px;line-height:24px;height:24px;background-image:url(&quot;background-repeat:no-repeat;cursor:pointer;margin:6px 6px 6px 0px;background-position:0px -104px;font-family:宋体, Arial;white-space:normal;background-color:#FFFFFF;"></a><a href="http://blog.itpub.net/15480802/viewspace-1412259/#" class="bds_tqq" data-cmd="tqq" title="分享到腾讯微博" style="word-wrap:break-word;text-decoration-line:none;color:#9C2423;float:left;font-size:18px;padding-left:25px;line-height:24px;height:24px;background-image:url(&quot;background-repeat:no-repeat;cursor:pointer;margin:6px 6px 6px 0px;background-position:0px -260px;font-family:宋体, Arial;white-space:normal;background-color:#FFFFFF;"></a><a href="http://blog.itpub.net/15480802/viewspace-1412259/#" class="bds_qzone" data-cmd="qzone" title="分享到QQ空间" style="word-wrap:break-word;text-decoration-line:none;color:#9C2423;float:left;font-size:18px;padding-left:25px;line-height:24px;height:24px;background-image:url(&quot;background-repeat:no-repeat;cursor:pointer;margin:6px 6px 6px 0px;background-position:0px -52px;font-family:宋体, Arial;white-space:normal;background-color:#FFFFFF;"></a>
	</div>
</div>