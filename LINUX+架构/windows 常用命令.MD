#查看路由<br />
tracert www.baidu.com<br />
<br />
<br />
/////杀进程///////<br />
1.开始——&gt;运行——&gt;cmd<br />
<br />
2.命令行输入：netstat -ano | findstr 端口（被占用的端口号）<br />
<br />
3.输入：tasklist | findstr 端口(获取步骤2里面的端口，实际就是拿到了pid)<br />
<br />
<p>
	4.taskkill /pid 端口（步骤3里面的端口） /F
</p>
<p>
	<br />
</p>
<p>
	<br />
</p>
<p>
	<br />
</p>
<p>
	1. netstat -ano |findstr 端口号
</p>
<p>
	<br />
</p>
<p>
	2.tasklist|findstr 进程号
</p>
<p>
	<br />
</p>
<p>
	3.taskkill -f -t -im 文件名
</p>