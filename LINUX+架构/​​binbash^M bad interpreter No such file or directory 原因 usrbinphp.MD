<p>
	/bin/bash^M: bad interpreter: No such file or directory原因
</p>
<p>
	这个原因相信不少人都碰到过，也知道个大概原因，这里我就再述说一遍。一般都是不同的系统对换行符的理解不同，即对\r的理解不同，所以就会出现这种情况。
</p>
<p>
	解决/bin/bash^M: bad interpreter: No such file or directory
</p>
<p>
	第1步：登录系统终端。
</p>
<p>
	第2步：执行以下命令并确定。
</p>
<p>
	sed -i 's/\r$//' /mnt/www/nginx_log.sh
</p>