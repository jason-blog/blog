<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-size:small;"><span style="font-size:medium;">AB在APACHE的bin目录下，以命令行的方式执行：</span></span>
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-size:small;"><span style="font-size:medium;">格式： ./ab [options] [http://]hostname[:port]/path</span></span>
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-size:small;"><span style="font-size:medium;">参数说明：</span></span>
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-size:small;"><span style="font-size:medium;">-n requests //在测试会话中所执行的请求个数。默认时，仅执行一个请求</span></span>
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-size:small;"><span style="font-size:medium;">-c concurrency //一次产生的请求个数。默认是一次一个</span></span>
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-size:small;"><span style="font-size:medium;">t timelimit //测试所进行的最大秒数</span></span>
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-size:small;"><span style="font-size:medium;"><br />
</span></span>
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-size:small;"><span style="font-size:medium;">其他的参数看中就用。</span></span>
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-size:small;"><span style="font-size:medium;">参数很多,一般我们用 -c 和 -n 参数就可以了. 例如:<br />
./ab -c 1000 -n 1000&nbsp;<a href="http://127.0.0.1/index.jsp" style="color:black;">http://127.0.0.1/index.jsp</a></span></span>
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-size:small;"><span style="font-size:medium;">这个表示同时处理1000个请求并运行1000次index.jsp文件.</span></span>
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-size:small;"><span style="font-size:medium;">其返回的结果集是有很多内容，我们选择关键的几个看看就大概知道我们的模块性能了</span></span>
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-size:small;"><span style="font-size:medium;">我比较关心的几个结果：</span></span>
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-size:small;"><span style="font-size:medium;">Concurrency Level: 1000<br />
Time taken for tests: 1.190 seconds&nbsp;<strong><span style="color:#003399;">//处理1000个并发请求总共花了1.19秒</span></strong><br />
Complete requests: 1000&nbsp;<strong>//完成处理的请求量</strong><br />
Failed requests: 0&nbsp;<strong>//请求失败数</strong><br />
Write errors: 0<br />
Non-2xx responses: 1000<br />
Total transferred: 164000 bytes&nbsp;<strong>//总共传输了多少流量</strong><br />
HTML transferred: 0 bytes<br />
Requests per second: 840.58 [#/sec] (mean)&nbsp;<strong>//平均一个请求花840.58毫秒 大家最关心的指标之一，相当于 LR 中的每秒事务数，后面括号中的 mean 表示这是一个平均值</strong><br />
Time per request: 1189.651 [ms] (mean)&nbsp;<strong>//</strong><strong>大家最关心的指标之二，相当于 LR 中的平均事务响应时间，后面括号中的 mean 表示这是一个平均值</strong><br />
Time per request: 1.190 [ms] (mean, across all concurrent requests)&nbsp;<strong>/</strong><strong>/每个请求实际运行时间的平均值 ms是毫秒</strong><br />
Transfer rate: 134.62 [Kbytes/sec] received&nbsp;<strong>//传输速率 可以帮助排除是否存在网络流量过大导致响应时间延长的问题</strong></span></span>
</p>
<div>
	<strong><br />
</strong>
</div>