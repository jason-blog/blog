<p style="margin:10px auto;padding:0px;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	session.gc_maxlifetime
</p>
<p style="margin:10px auto;padding:0px;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	session.gc_probability&nbsp;&nbsp;
</p>
<p style="margin:10px auto;padding:0px;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	session.gc_divisor&nbsp;
</p>
<p style="margin:10px auto;padding:0px;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	session.gc_divisor 与 session.gc_probability 合起来定义了在每个会话初始化时启动 gc（garbage collection 垃圾回收）进程的概率。此概率用 gc_probability/gc_divisor 计算得来。例如 1/100 意味着在每个请求中有 1% 的概率启动 gc 进程。session.gc_divisor 默认为 100。
</p>
<p style="margin:10px auto;padding:0px;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	比如：session.gc_maxlifetime=30，session.gc_divisor=1000，session.gc_probability=1，就表示每一千个用户调用session_start()的时候，就百分百的会执行一次垃圾回收机制，将磁盘上没用的session文件删除。
</p>
<p style="margin:10px auto;padding:0px;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	注意：一般对于一些大型的门户网站，建议将session.gc_divisor调大一点，减少开销
</p>
<p style="margin:10px auto;padding:0px;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	接下来，我通过一个例子演示下，如何配置才能让调用gc（垃圾回收）进程呢！
</p>
<p style="margin:10px auto;padding:0px;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	通过配置php.ini文件，修改以下几个信息：
</p>
<ol style="margin:0px;padding:0px 0px 0px 40px;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<li style="margin:0px 0px 1em;padding:0px;list-style:decimal;">
		session.gc_maxlifetime = 60//当session文件在60s后还没有被访问的话，则该session文件将会被视为“垃圾文件”，并且等待gc（垃圾回收）进程的调用的时候被清理掉
	</li>
	<li style="margin:0px 0px 1em;padding:0px;list-style:decimal;">
		session.gc_probability = 1000
	</li>
</ol>
<p style="margin:10px auto;padding:0px;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	因为gc进程被调用的概率是通过gc_probability/gc_divisor 计算得来的，这里我将session.gc_probability改成1000，而session.gc_divisor 默认情况下也是1000。则gc进程在每次执行session_start()函数的时候都会被调用到。
</p>
<p style="margin:10px auto;padding:0px;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	以下我通过截图简单的说明下：
</p>
<p style="margin:10px auto;padding:0px;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<img src="http://pic002.cnblogs.com/images/2012/350329/2012061710320461.png" alt="" style="margin:0px;padding:0px;max-width:900px;" />
</p>
<p style="margin:10px auto;padding:0px;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	我开启三个会话，则创建三个对应的session文件，当每个文件在30秒内都没被调用的话，就会被当成是“垃圾文件”，等到gc进程调用的时候，“垃圾文件”就会被unlink，因为之前我已经通过修改php.ini配置文件，将gc被调用的概率改成百分百，所以接下来，如果我重新使用任何一个浏览器刷新下页面的时候，三个session文件，应该只剩下一个了
</p>
<p style="margin:10px auto;padding:0px;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<img src="http://pic002.cnblogs.com/images/2012/350329/2012061710331085.png" alt="" style="margin:0px;padding:0px;max-width:900px;" />
</p>