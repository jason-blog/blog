<p style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	GET_LOCK(name,time)函数定义一个名称为name、持续时间长度为time秒的锁。
</p>
<ul style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<li>
		如果锁定成功，返回1。
	</li>
	<li>
		如果操作超时，返回0。
	</li>
	<li>
		如果发生错误，返回NULL。
	</li>
</ul>
<br style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<p style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	（1）get_lock会按照key来加锁，别的客户端再以同样的key加锁时就加不了了，处于等待状态。&nbsp;<br />
（2）当调用release_lock来释放上面加的锁或客户端断线了，上面的锁才会释放，其它的客户端才能进来。
</p>
<p style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<br />
</p>
<ul style="color:#362E2B;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<li>
		GET_LOCK('MySQL',10)返回结果为1，说明成功得到了一个名称为'MySQL'的锁，持续时间为10秒。
	</li>
	<li>
		IS_USED_LOCK('MySQL')返回结果为当前连接ID，表示名称为'MySQL'的锁正在被使用。
	</li>
	<li>
		IS_FREE_LOCK('MySQL')返回结果为0，说明名称为'MySQL'的锁正在被使用。
	</li>
	<li>
		RELEASE_LOCK('MySQL')返回值为1，说明解锁成功。
	</li>
</ul>