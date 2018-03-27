<p>
	<span style="color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">1.到官网注册账号：</span><a target="_blank" href="https://hub.docker.com/" style="box-sizing:border-box;background:#FFFFFF;color:#CA0C16;text-decoration-line:none;margin:0px;padding:0px;outline:none;font-family:&quot;font-size:16px;white-space:normal;">https://hub.docker.com/</a> 
</p>
<p>
	<span style="color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">2.在本地Linux登录docker：</span> 
</p>
<p>
	&nbsp; &nbsp;docker&nbsp;login
</p>
<p>
	3.docker推送规范为
</p>
<p>
	&nbsp; &nbsp;docker push 注册用户名/镜像名
</p>
<p>
	&nbsp; &nbsp;所以得将dockerimage名改为&nbsp;登录用户名/docker镜像名
</p>
<p>
	&nbsp; &nbsp;例如&nbsp;
</p>
<p>
	&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;docker tag&nbsp;dockeruser/linux-centos linux-centos
</p>
<p>
	&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;docker tag [newname] [oldname]
</p>
<p>
	&nbsp;4.推送docker镜像
</p>
<p>
	&nbsp; &nbsp;&nbsp;docker push&nbsp;[new-docker-name]&nbsp;<span style="color:#333333;font-family:&quot;font-size:12.6px;white-space:pre;background-color:rgba(128, 128, 128, 0.05);">:</span><span class="hljs-tag" style="box-sizing:border-box;margin:0px;padding:0px;color:#006666;font-family:&quot;font-size:12.6px;white-space:pre;background-color:rgba(128, 128, 128, 0.05);">&lt;<span class="hljs-title" style="box-sizing:border-box;margin:0px;padding:0px;color:#000088;">tag</span>&gt;</span>
</p>
<p>
	&nbsp; &nbsp; docker&nbsp;push&nbsp;<span style="white-space:normal;">dockeruser/linux-centos&nbsp;:latest</span> 
</p>
<p>
	<span style="white-space:normal;"><br />
</span> 
</p>