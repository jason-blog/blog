正向 SSH -L<br />
<p>
	<br />
</p>
<p>
	<br />
</p>
将连接到<span style="white-space:normal;">192.168.1.2</span>的22222端口映射到 <span style="white-space:normal;">192.168.1.3</span> （相当于<span style="white-space:normal;"><span style="white-space:normal;">192.168.1.3</span></span>也可以换为其他域名或ip）<br />
SSH -C -L 22222:192.168.1.3:80 jason@192.168.1.2<br />
<br />
<br />
反向<br />
<p>
	<br />
</p>
<p>
	在localhost中执行
</p>
ssh -R 22222:localhost:80 root@192.168.1.2<br />
<br />
键入<span style="white-space:normal;">192.168.1.2</span>的root用户密码， 那么这个tunnel就建了了。<br />
<p>
	<br />
</p>
<p>
	<br />
</p>
<p>
	访问&nbsp;<span style="white-space:normal;">192.168.1.2:22222 相当于 localhost:80</span> 
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
	<br />
</p>