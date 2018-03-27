<h1 style="margin:0px 0px 5px;">
	dstat mysql5-io 模块使用 - 漫步的影子
</h1>
<div class="article_meta" style="padding-bottom:5px;border-bottom:1px dashed #D3D3D3;">
	<div style="margin-bottom:5px;">
		时间&nbsp;2014-07-19 17:21:00&nbsp;&nbsp;<a class="cut cut28 from" href="http://www.tuicool.com/sites/QbYvau" target="_blank" style="transition:0.25s;outline:none 0px;overflow:hidden;white-space:nowrap;word-break:keep-all;text-overflow:ellipsis;max-width:28%;display:inline;">博客园-所有随笔区</a> 
	</div>
	<div class="source">
		原文&nbsp;&nbsp;<a class="cut cut70" href="http://www.cnblogs.com/jachin/p/3855290.html?utm_source=tuicool&amp;utm_medium=referral" style="transition:0.25s;outline:none 0px;overflow:hidden;white-space:nowrap;word-break:keep-all;text-overflow:ellipsis;max-width:69%;display:inline-block;">http://www.cnblogs.com/jachin/p/3855290.html</a> 
	</div>
	<div>
		主题&nbsp;<a href="http://www.tuicool.com/topics/11030000" target="_blank" style="transition:0.25s;outline:none 0px;">MySQL&nbsp;</a><a href="http://www.tuicool.com/topics/11040000" target="_blank" style="transition:0.25s;outline:none 0px;">IO</a> 
	</div>
</div>
<div class="article_body" id="nei" style="padding:20px 5px 25px;margin-bottom:0px;overflow-x:hidden;word-break:break-all;min-height:340px;line-height:1.7em;">
	<div style="line-height:1.7em;">
<pre class="prettyprint sql" style="padding:0.3em;">[root@shylock dstat]# dstat --list
internal:  aio, cpu, cpu24, disk, disk24, disk24old, epoch, fs, int, int24, io, ipc, load, lock, mem, net, page, page24, proc, raw, socket, swap, swapold, sys, tcp,  time, udp, unix, vm /usr/share/dstat:  battery, battery-remain, cpufreq, dbus, disk-util, fan, freespace, gpfs, gpfs-ops, helloworld, innodb-buffer, innodb-io, innodb-ops, lustre, memcache-hits,  mysql-io, mysql-keys, mysql5-cmds, mysql5-conn, mysql5-io, mysql5-keys, net-packets, nfs3, nfs3-ops, nfsd3, nfsd3-ops, ntp, postfix, power, proc-count, rpc,  rpcd, sendmail, snooze, thermal, top-bio, top-cpu, top-cputime, top-cputime-avg, top-io, top-latency, top-latency-avg, top-mem, top-oom, utmp, vm-memctl,  vmk-hba, vmk-int, vmk-nic, vz-cpu, vz-io, vz-ubc, wifi</pre>
		<p style="margin-top:0px;margin-bottom:0.75em;line-height:1.7em;">
			当运行dstat 监控mysql io 的时候报连接不到mysql server
		</p>
<pre class="prettyprint java" style="padding:0.3em;">[root@shylock ~]# dstat --mysql5-io Module dstat_mysql5_io failed to load. (Cannot interface with MySQL server) None of the stats you selected are available.</pre>
<pre class="prettyprint ruby" style="padding:0.3em;">[root@shylock ~]# cd /usr/share/dstat [root@shylock dstat]# vi dstat_mysql5_io.py  3 global mysql_user  4 mysql_user = os.getenv('DSTAT_MYSQL_USER') or os.getenv('USER')  5  6 global mysql_pwd  7 mysql_pwd = os.getenv('DSTAT_MYSQL_PWD')

在/usr/shared/dstat目录下有dstat的命令和插件 vi dstat_mysql5_io.py
在3-7行里有声明mysql_user 和mysql_pwd 
os.getenv(环境变量名称) 从环境变量中获取MYSQL的用户名密码</pre>
<pre class="prettyprint bash" style="padding:0.3em;">#!/bin/bash #file:mysql5io.sh export DSTAT_MYSQL_USER='user' export DSTAT_MYSQL_PWD='pwd' dstat --mysql5-io $@</pre>
		<p style="margin-top:0px;margin-bottom:0.75em;line-height:1.7em;">
			编写shell脚本 --"$@" 数组 &nbsp;"$*" 字符串
		</p>
		<div style="line-height:1.7em;">
<pre class="prettyprint bash" style="padding:0.3em;">chmod 700 mysql5io.sh ./mysql5io.sh 3 5 #停3秒，获取5次结果</pre>
			<div style="line-height:1.7em;">
				<p style="margin-top:0px;margin-bottom:0.75em;line-height:1.7em;">
					-mysql5-io-
				</p>
				<p style="margin-top:0px;margin-bottom:0.75em;line-height:1.7em;">
					recv sent
				</p>
				<p style="margin-top:0px;margin-bottom:0.75em;line-height:1.7em;">
					1.00B 3.34B
				</p>
				<p style="margin-top:0px;margin-bottom:0.75em;line-height:1.7em;">
					778B 2618B
				</p>
				<p style="margin-top:0px;margin-bottom:0.75em;line-height:1.7em;">
					791B 2677B
				</p>
				<p style="margin-top:0px;margin-bottom:0.75em;line-height:1.7em;">
					804B 2736B
				</p>
				<p style="margin-top:0px;margin-bottom:0.75em;line-height:1.7em;">
					817B 2794B
				</p>
				<p style="margin-top:0px;margin-bottom:0.75em;line-height:1.7em;">
					830B 2853B
				</p>
			</div>
		</div>
		<p style="margin-top:0px;margin-bottom:0.75em;line-height:1.7em;">
			因为在脚本里 dstat --mysql5_io $@ 运行脚本传参数(参考dstat -h)
		</p>
<pre class="prettyprint perl" style="padding:0.3em;">[root@shylock ~]# ./mysql5io.sh -c -s -m 3 5 -mysql5-io- ----total-cpu-usage---- ----swap--- ------memory-usage----- recv sent|usr sys idl wai hiq siq| used free| used  buff  cach free 1.11B 3.75B| 16 2 78 4 0 0| 0 2016M|95.7M 41.5M 276M 594M 885B 2996B| 0 0 100 0 0 0| 0 2016M|95.8M 41.5M 276M 594M 898B 3055B| 0 0 99 0 0 0| 0 2016M|95.8M 41.5M 276M 594M 911B 3114B| 0 0 100 0 0 0| 0 2016M|95.8M 41.5M 276M 594M 924B 3172B| 0 0 100 0 0 0| 0 2016M|95.8M 41.5M 276M 594M 937B 3231B| 0 0 100 0 0 0| 0 2016M|95.8M 41.5M 276M 594M</pre>
	</div>
</div>