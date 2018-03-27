默认log&nbsp; /var/log/audit/audit.log<br />
<br />
查看状态 /usr/sbin/sestatus -v&nbsp; 或 getenforce<br />
<br />
<br />
临时关闭<br />
setenforce 0&nbsp;<br />
临时开启<br />
setenforce 1<br />
<br />
如果要彻底关闭SeLinux请使用下面的命令<br />
#vim /etc/selinux/config<br />
将 SELINUX=enforcing 改为 SELINUX=disabled&nbsp;<br />
重启服务器即可。<br />
<p>
	<br />
</p>
<p>
	ls -LZ&nbsp;
</p>
chcon -R -t httpd_sys_content_t www<br />
授权&nbsp;<br />