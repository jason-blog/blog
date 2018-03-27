<p>
	ssh 开隧道不能外部访问
</p>
<p>
	netstat -ntl 发现 对应端口为127.0.0.1 并没有 0.0.0.0
</p>
<p>
	上网一顿搜找到对应解决方案
</p>
<p>
<pre style="box-sizing:inherit;font-family:monospace, monospace;font-size:13px;max-width:100%;margin-top:1em;margin-bottom:1em;background:#F7F7F7;padding:15px 20px;overflow:auto;color:#444444;"><code style="box-sizing:inherit;font-family:monospace, monospace;max-width:100%;margin:1em 0px;background:none;padding:0px;overflow:auto;">GatewayPorts yes </code></pre>
	<p style="box-sizing:inherit;max-width:100%;color:#444444;font-family:&quot;font-size:15px;white-space:normal;">
		然后重启sshd。这个作用是把转发的端口绑定在0.0.0.0的接口上，让外部地址也可以访问。
	</p>
</p>