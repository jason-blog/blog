<div class="main">
	<div class="breadcrumb">
		<br />
	</div>
	<div class="post_hd clearfix">
		<h1 class="l">
			dstat命令
		</h1>
		<div class="tag f_yh r">
			<a href="http://man.linuxde.net/sub/%e6%80%a7%e8%83%bd%e7%9b%91%e6%b5%8b%e4%b8%8e%e4%bc%98%e5%8c%96" rel="tag">性能监测与优化</a> 
		</div>
	</div>
	<div class="post_bd post">
		<p>
			<strong>dstat命令</strong>是一个用来替换<span class="wp_keywordlink"><a href="http://man.linuxde.net/vmstat" title="vmstat命令" target="_blank">vmstat</a></span>、<span class="wp_keywordlink"><a href="http://man.linuxde.net/iostat" title="iostat命令" target="_blank">iostat</a></span>、<span class="wp_keywordlink"><a href="http://man.linuxde.net/netstat" title="netstat命令" target="_blank">netstat</a></span>、<span class="wp_keywordlink"><a href="http://man.linuxde.net/nfsstat" title="nfsstat命令" target="_blank">nfsstat</a></span>和<span class="wp_keywordlink"><a href="http://man.linuxde.net/ifstat" title="ifstat命令" target="_blank">ifstat</a></span>这些命令的工具，是一个全能系统信息统计工具。与sysstat相比，dstat拥有一个彩色的界面，在手动观察性能状况时，数据比较显眼容易观察；而且dstat支持即时刷新，譬如输入<code>dstat 3</code>即每三秒收集一次，但最新的数据都会每秒刷新显示。和sysstat相同的是，dstat也可以收集指定的性能资源，譬如<code>dstat -c</code>即显示CPU的使用情况。
		</p>
		<h3>
			下载安装<br />
		</h3>
		<p>
			<strong>方法一</strong> 
		</p>
<pre><span class="wp_keywordlink"><a href="http://man.linuxde.net/yum" title="yum命令" target="_blank">yum</a></span> <span class="wp_keywordlink"><a href="http://man.linuxde.net/install" title="install命令" target="_blank">install</a></span> -y dstat</pre>
		<p>
			<strong>方法二</strong> 
		</p>
		<p>
			官网下载地址：http://dag.wieers.com/<span class="wp_keywordlink"><a href="http://man.linuxde.net/rpm" title="rpm命令" target="_blank">rpm</a></span>/packages/dstat
		</p>
<pre><span class="wp_keywordlink"><a href="http://man.linuxde.net/wget" title="wget命令" target="_blank">wget</a></span> http://dag.wieers.com/rpm/packages/dstat/dstat-0.6.7-1.rh7.rf.noarch.rpm
rpm -ivh dstat-0.6.7-1.rh7.rf.noarch.rpm</pre>
		<h3>
			使用说明<br />
		</h3>
		<p>
			安装完后就可以使用了，dstat非常强大，可以实时的监控cpu、磁盘、网络、IO、内存等使用情况。
		</p>
		<p>
			直接使用dstat，默认使用的是<code>-cdngy</code>参数，分别显示cpu、disk、net、page、system信息，默认是1s显示一条信息。可以在最后指定显示一条信息的时间间隔，如<code>dstat&nbsp;5</code>是没5s显示一条，<code>dstat&nbsp;5&nbsp;10</code>表示没5s显示一条，一共显示10条。
		</p>
<pre>[root@iZ23uulau1tZ ~]# dstat
----total-cpu-usage---- -dsk/total- -net/total- ---paging-- ---system--
usr sys idl wai hiq siq| <span class="wp_keywordlink"><a href="http://man.linuxde.net/read" title="read命令" target="_blank">read</a></span> writ| recv  send|  in   out | int   csw
  0   0  99   0   0   0|7706B  164k|   0     0 |   0     0 | 189   225
  0   0 100   0   0   0|   0     0 |4436B  826B|   0     0 | 195   248
  1   0  99   0   0   0|   0     0 |4744B  346B|   0     0 | 203   242
  0   0 100   0   0   0|   0     0 |5080B  346B|   0     0 | 206   242
  0   1  99   0   0   0|   0     0 |5458B  444B|   0     0 | 214   244
  1   0  99   0   0   0|   0     0 |5080B  346B|   0     0 | 208   242</pre>
		<p>
			下面对显示出来的部分信息作一些说明：
		</p>
		<ol>
			<li>
				cpu：hiq、siq分别为硬中断和软中断次数。
			</li>
			<li>
				system：int、csw分别为系统的中断次数（interrupt）和上下文切换（context&nbsp;switch）。
			</li>
		</ol>
		<p>
			其他的都很好理解。
		</p>
		<h3>
			语法<br />
		</h3>
<pre>dstat [-afv] [options..] [delay [count]]</pre>
		<h3>
			常用选项<br />
		</h3>
<pre>-c：显示CPU系统占用，用户占用，空闲，等待，中断，软件中断等信息。
-C：当有多个CPU时候，此参数可按需分别显示cpu状态，例：-C 0,1 是显示cpu0和cpu1的信息。
-d：显示磁盘读写数据大小。
-D hda,total：include hda and total。
-n：显示网络状态。
-N eth1,total：有多块网卡时，指定要显示的网卡。
-l：显示系统负载情况。
-m：显示内存使用情况。
-g：显示页面使用情况。
-p：显示进程状态。
-s：显示交换分区使用情况。
-S：类似D/N。
-r：I/O请求情况。
-y：系统状态。
--ipc：显示ipc消息队列，信号等信息。
--socket：用来显示tcp udp端口状态。
-a：此为默认选项，等同于-cdngy。
-v：等同于 -pmgdsc -D total。
--output 文件：此选项也比较有用，可以把状态信息以csv的格式重定向到指定的文件中，以便日后查看。例：dstat --output /root/dstat.csv &amp; 此时让程序默默的在后台运行并把结果输出到/root/dstat.csv文件中。</pre>
		<p>
			当然dstat还有很多更高级的用法，常用的基本这些选项，更高级的用法可以结合<span class="wp_keywordlink"><a href="http://man.linuxde.net/man" title="man命令" target="_blank">man</a></span>文档。
		</p>
		<h3>
			实例<br />
		</h3>
		<p>
			如想监控swap，process，sockets，filesystem并显示监控的时间：
		</p>
<pre>[root@iZ23uulau1tZ ~]# dstat -tsp --socket --fs
----system---- ----swap--- ---procs--- ------sockets------ --filesystem- <span class="wp_keywordlink"><a href="http://man.linuxde.net/date" title="date命令" target="_blank">date</a></span>/<span class="wp_keywordlink"><a href="http://man.linuxde.net/time" title="time命令" target="_blank">time</a></span> | used <span class="wp_keywordlink"><a href="http://man.linuxde.net/free" title="free命令" target="_blank">free</a></span>|run blk new|tot tcp udp raw frg|files  inodes
26-07 09:23:48|   0     0 |  0   0 0.0|104   8   5   0   0|  704   6488
26-07 09:23:49|   0     0 |  0   0   0|104   8   5   0   0|  704   6488
26-07 09:23:50|   0     0 |  0   0   0|104   8   5   0   0|  704   6489
26-07 09:23:51|   0     0 |  0   0   0|104   8   5   0   0|  704   6489
26-07 09:23:52|   0     0 |  0   0   0|104   8   5   0   0|  704   6489
26-07 09:23:53|   0     0 |  0   0   0|104   8   5   0   0|  704   6489</pre>
		<p>
			若要将结果输出到文件可以加<code>--output&nbsp;filename</code>：
		</p>
<pre>[root@iZ23uulau1tZ ~]# dstat -tsp --socket --fs --output /tmp/ds.csv
----system---- ----swap--- ---procs--- ------sockets------ --filesystem-
  date/time   | used  free|run blk new|tot tcp udp raw frg|files  inodes
26-07 09:25:31|   0     0 |  0   0 0.0|104   8   5   0   0|  736   6493
26-07 09:25:32|   0     0 |  0   0   0|104   8   5   0   0|  736   6493
26-07 09:25:33|   0     0 |  0   0   0|104   8   5   0   0|  736   6493
26-07 09:25:34|   0     0 |  0   0   0|104   8   5   0   0|  736   6493
26-07 09:25:35|   0     0 |  0   0   0|104   8   5   0   0|  736   6494
26-07 09:25:36|   0     0 |  0   0   0|104   8   5   0   0|  736   6494</pre>
		<p>
			这样生成的csv文件可以用excel打开，然后生成图表。
		</p>
		<p>
			通过<code>dstat&nbsp;--list</code>可以查看dstat能使用的所有参数，其中上面internal是dstat本身自带的一些监控参数，下面<code>/usr/share/dstat</code>中是dstat的插件，这些插件可以扩展dstat的功能，如可以监控电源（battery）、<span class="wp_keywordlink"><a href="http://man.linuxde.net/mysql" title="mysql命令" target="_blank">mysql</a></span>等。
		</p>
		<p>
			下面这些插件并不是都可以直接使用的，有的还依赖其他包，如想监控mysql，必须要装python连接mysql的一些包。
		</p>
<pre>[root@iZ23uulau1tZ ~]# dstat --list
internal:
        aio, cpu, cpu24, disk, disk24, disk24old, epoch, fs, int, int24, io, ipc, load, lock, mem, net, page, page24, proc, raw, socket, swap, swapold, sys, tcp, time, udp, unix, vm
/usr/share/dstat:
        battery, battery-remain, cpufreq, dbus, disk-util, fan, freespace, gpfs, gpfs-ops, helloworld, innodb-buffer, innodb-io, innodb-ops, lustre, memcache-hits, mysql-io, mysql-keys, mysql5-cmds, mysql5-conn, mysql5-io, mysql5-keys,
        net-packets, nfs3, nfs3-ops, nfsd3, nfsd3-ops, ntp, postfix, power, proc-count, rpc, rpcd, <span class="wp_keywordlink"><a href="http://man.linuxde.net/sendmail" title="sendmail命令" target="_blank">sendmail</a></span>, snooze, thermal, <span class="wp_keywordlink"><a href="http://man.linuxde.net/top" title="top命令" target="_blank">top</a></span>-bio, top-cpu, top-cputime, top-cputime-avg, top-io, top-latency, top-latency-avg, top-mem, top-oom, utmp,
        vm-memctl, vmk-hba, vmk-int, vmk-nic, vz-cpu, vz-io, vz-ubc, wifi</pre>
		<p>
			dstat命令的基本用法就说到这里，更多用法有待摸索，如果您需要补充内容请给我们发邮件，谢谢！
		</p>
	</div>
	<div id="comments">
		<!-- You can start editing here. -->
	</div>
</div>