<p>
	ls --full-time 查看创建时间精确到秒
</p>
<p>
	#查看链接ip去重复
</p>
<p>
	netstat -apn |grep 80 |grep ESTA |awk '{print$5 "\n"}' |awk 'BEGIN {FS=":"} {print $1 "\n"}' |sort |uniq
</p>
<p>
	<p>
		<br />
	</p>
	<p>
		ps -eLf | grep java | wc -l
	</p>
	<p>
		<br />
	</p>
</p>
<p>
	<br />
</p>
<pre class="prettyprint lang-js linenums">     netstat -n | awk '/^tcp/ {++S[$NF]} END {for(a in S) print a, S[a]}'
返回结果示例：
　　LAST_ACK 5
　　SYN_RECV 30
　　ESTABLISHED 1597
　　FIN_WAIT1 51
　　FIN_WAIT2 504
　　TIME_WAIT 1057




说明:
   SYN_RECV表示正在等待处理的请求数；
   ESTABLISHED表示正常数据传输状态；
   TIME_WAIT表示处理完毕，等待超时结束的请求数。</pre>
<p>
	<br />
</p>
<ol style="margin:0px;padding:0px;border:0px;vertical-align:baseline;list-style-type:none;white-space:pre;">
	<li style="margin:0px;padding:0px;border:0px;vertical-align:baseline;">
		$ cat /proc/meminfo //查看内存使用情况
	</li>
</ol>
<p>
	<br />
</p>
<p>
	ps -aux | grep pid&nbsp;
</p>
ps -aux 查看所有<br />
<br />
pidof mysqld<br />
<br />
netstat &nbsp; -anp &nbsp; | &nbsp; grep &nbsp;portno<br />
<br />
netstat –apn | grep 8080 查看对应端口程序 ///root权限<br />
<br />
netstat -pnt |grep :80 |wc -l 连接数 /////// netstat -nat | grep -i "80" |wc -l<br />
<br />
netstat -tln 查看当前已经开放的端口<br />
//连接信息<br />
netstat -ntu | awk '{print $5}' | cut -d: -f1 | sort | uniq -c | sort -n&nbsp;<br />
<br />
<br />
$ ps -e -o 'pid,comm,args,pcpu,rsz,vsz,stime,user,uid' &nbsp;其中rsz是是实际内存<br />
$ ps -e -o 'pid,comm,args,pcpu,rsz,vsz,stime,user,uid' | grep oracle | &nbsp;sort -nrk<br />
<br />
////////////////////////lsof/////////////////////<br />
lsof abc.txt 显示开启文件abc.txt的进程<br />
lsof -c abc 显示abc进程现在打开的文件<br />
lsof -c -p 1234 列出进程号为1234的进程所打开的文件<br />
lsof -g gid 显示归属gid的进程情况<br />
lsof +d /usr/local/ 显示目录下被进程开启的文件<br />
lsof +D /usr/local/ 同上，但是会搜索目录下的目录，时间较长<br />
lsof -d 4 显示使用fd为4的进程<br />
lsof -i 用以显示符合条件的进程情况<br />
lsof -i[46] [protocol][@hostname|hostaddr][:service|port]<br />
--&gt; IPv4 or IPv6<br />
&nbsp; protocol --&gt; TCP or UDP<br />
&nbsp; hostname --&gt; Internet host name<br />
&nbsp; hostaddr --&gt; IPv4地址<br />
&nbsp; service --&gt; /etc/service中的 service name (可以不止一个)<br />
&nbsp; port --&gt; 端口号 (可以不止一个)<br />
------------------------------------------------------------------------<br />
<br />
lsof `which httpd` //那个进程在使用apache的可执行文件<br />
lsof /etc/passwd //那个进程在占用/etc/passwd<br />
lsof /dev/hda6 //那个进程在占用hda6<br />
lsof /dev/cdrom //那个进程在占用光驱<br />
lsof -c sendmail //查看sendmail进程的文件使用情况<br />
lsof -c courier -u ^zahn //显示出那些文件被以courier打头的进程打开，但是并不属于用户zahn<br />
lsof -p 30297 //显示那些文件被pid为30297的进程打开<br />
lsof -D /tmp 显示所有在/tmp文件夹中打开的instance和文件的进程。但是symbol文件并不在列<br />
<br />
lsof -u1000 //查看uid是100的用户的进程的文件使用情况<br />
lsof -utony //查看用户tony的进程的文件使用情况<br />
lsof -u^tony //查看不是用户tony的进程的文件使用情况(^是取反的意思)<br />
lsof -i //显示所有打开的端口<br />
lsof -i:80 //显示所有打开80端口的进程<br />
lsof -i -U //显示所有打开的端口和UNIX domain文件<br />
lsof -i UDP@[url]www.akadia.com:123 //显示那些进程打开了到www.akadia.com的UDP的123(ntp)端口的链接<br />
lsof -i tcp@ohaha.ks.edu.tw:ftp -r //不断查看目前ftp连接的情况(-r，lsof会永远不断的执行，直到收到中断信号,+r，lsof会一直执行，直到没有档案被显示,缺省是15s刷新)<br />
lsof -i tcp@ohaha.ks.edu.tw:ftp -n //lsof -n 不将IP转换为hostname，缺省是不加上-n参数<br />
<br />
<br />
////////////////////////////////////////////////<br />
//////////////awk///////////////////<br />
<br />
&nbsp;ps -aux |grep sshd |awk '{print $2 "\t" $3}'<br />
&nbsp;<br />
//////////////////////////////////////////<br />
<br />
<br />
tail -f **** 实时查看<br />
<br />
du -sh **** 文件大小<br />
<br />
df -lh 硬盘<br />
<br />
linux后台运行：<br />
nohup node index.js &gt; myLog.log 2&gt;&amp;1 &amp;&nbsp;<br />
<br />
结束<br />
fg +nohup[0]<br />
<br />
jobs //查看当前后台运行的程序<br />
<br />
<br />
<br />
<br />
二、tail命令使用方法演示例子<br />
1、tail -f filename<br />
说明：监视filename文件的尾部内容（默认10行，相当于增加参数 -n 10），刷新显示在屏幕上。退出，按下CTRL+C。<br />
2、tail -n 20 filename<br />
说明：显示filename最后20行。<br />
3、tail -n +20 filename<br />
说明：显示filename前面20行。<br />
4、tail -r -n 10 filename<br />
说明：逆序显示filename最后10行。<br />
<br />
<br />
在指定目录下查找字符串<br />
grep -rn "hello,world!" ./<br />
sudo grep -r -n '3690' ./* &nbsp;&gt; /home/jason/a.log<br />
<br />
<br />
sudo cat /etc/group | grep -C 10 'apache' &nbsp; ///// -C 前后多少行<br />
<br />
<br />
cat filename | tail -n +3000 | head -n 1000<br />
<br />
<br />
du -h --max-depth=1 /path...<br />
<br />
<br />
查看网络占用<br />
1、iptraf 工具(http://iptraf.seul.org),提供了每个网卡吞吐量的仪表盘：iptraf -d eth0。<br />
<p>
	2、watch命令：watch -n 1 "/sbin/ifconfig eth0 | grep bytes" &nbsp;//TX代表传送数据，RX是接收数据 Transmit 和 Receive 的缩，
</p>
<p>
	<br />
</p>
<p>
	w 命令&nbsp;<span style="color:#CC0000;font-family:arial;font-size:13px;white-space:normal;background-color:#FFFFFF;">Load</span><span style="color:#333333;font-family:arial;font-size:13px;white-space:normal;background-color:#FFFFFF;">&nbsp;</span><span style="color:#CC0000;font-family:arial;font-size:13px;white-space:normal;background-color:#FFFFFF;">Average</span><span style="color:#333333;font-family:arial;font-size:13px;white-space:normal;background-color:#FFFFFF;">&nbsp;就是一段时间(1分钟、5分钟、15分钟)内平均</span><span style="color:#CC0000;font-family:arial;font-size:13px;white-space:normal;background-color:#FFFFFF;">Load</span> 
</p>
<div>
	<span style="font-family:tahoma, arial, 宋体;font-size:14px;white-space:normal;background-color:#DDEDFB;"><br />
</span>
</div>