<p>
	linux&nbsp;sudo是有自己的环境变量的
</p>
<p>
	所以你会发现，在/etc/profile&nbsp;中设置好环境变量之后
</p>
<p>
	sudo&nbsp;su&nbsp;
</p>
<p>
	并没有生效
</p>
<p>
	原因是 /etc/sudoer&nbsp;中开启了重置环境变量&nbsp;
</p>
<p>
	需要修改两处
</p>
<p>
	Defaults&nbsp; &nbsp; !env_reset
</p>
<p>
	#Defaults&nbsp; &nbsp; secure_path = /sbin:/bin:/usr/sbin:/usr/bin
</p>