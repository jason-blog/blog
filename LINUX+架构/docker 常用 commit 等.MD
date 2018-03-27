<p>
	<span style="color:#333333;">docker ps -a&nbsp;</span> 
</p>
<p>
	<span style="color:#333333;font-family:&quot;font-size:12.6px;white-space:pre;background-color:rgba(128, 128, 128, 0.05);">docker </span><span class="hljs-operator" style="box-sizing:border-box;margin:0px;padding:0px;color:#333333;font-family:&quot;font-size:12.6px;white-space:pre;background-color:rgba(128, 128, 128, 0.05);"><span class="hljs-keyword" style="box-sizing:border-box;margin:0px;padding:0px;color:#000088;">commit [上一步中的id] [image名称]&nbsp;</span></span> 
</p>
<p>
	docker&nbsp;images //查看所有镜像
</p>
<p>
	<span style="color:#333333;font-family:&quot;font-size:12.6px;white-space:pre;background-color:rgba(128, 128, 128, 0.05);">docker pull centos //下载镜像</span> 
</p>
<p>
	docker&nbsp;build [dockerfile] //启动dockerfile
</p>
<p>
	docker run -p 10022:22 -v /dockertasks:/tasks/ -d sshd-centos /usr/sbin/sshd -D //启动docker镜像
</p>
<p>
	docker-compose up -d //启动docker-compose
</p>
<p>
	<br />
</p>
<p>
	<span style="font-family:Consolas, &quot;white-space:normal;background-color:#FFFFFF;">docker&nbsp;save [image id] &gt;&nbsp;/opt/soft/postgres.img&nbsp;&nbsp;</span> //导出
</p>
<p>
	<span style="font-family:Consolas, &quot;white-space:normal;background-color:#F8F8F8;">docker&nbsp;</span><span class="keyword" style="box-sizing:border-box;margin:0px;padding:0px;font-weight:bold;background:#F8F8F8;color:#006699;font-size:14px;border-radius:2px;word-wrap:normal;border:none;font-family:Consolas, &quot;white-space:normal;">load</span><span style="box-sizing:border-box;margin:0px;padding:0px;border:none;background-color:#F8F8F8;font-family:Consolas, &quot;white-space:normal;">&nbsp;&lt;&nbsp;postgres.img&nbsp;&nbsp;</span>//导入
</p>
<p>
	批量删除&nbsp;<strong style="box-sizing:border-box;color:#3F3F3F;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">官方建议的批量删除停止容器使用<code style="box-sizing:border-box;font-family:&quot;font-size:14.4px;padding:2px 4px;white-space:nowrap;background-color:rgba(128, 128, 128, 0.075);border-radius:0px;">docker rm $(sudo docker ps -a -q)</code></strong> 
</p>
<p>
	<span style="box-sizing:border-box;"><code style="box-sizing:border-box;"><span style="font-family:'sans serif, tahoma, verdana, helvetica';">批量删除镜像&nbsp;</span><span style="color:#333333;font-family:&quot;font-size:12.6px;white-space:pre;background-color:rgba(128, 128, 128, 0.05);font-weight:bold;">docker rmi </span><span class="hljs-variable" style="color:#660066;font-family:&quot;font-size:12.6px;white-space:pre;background-color:rgba(128, 128, 128, 0.05);font-weight:bold;box-sizing:border-box;margin:0px;padding:0px;">$(</span><span style="color:#333333;font-family:&quot;font-size:12.6px;white-space:pre;background-color:rgba(128, 128, 128, 0.05);font-weight:bold;">docker images | grep </span><span class="hljs-string" style="color:#008800;font-family:&quot;font-size:12.6px;white-space:pre;background-color:rgba(128, 128, 128, 0.05);font-weight:bold;box-sizing:border-box;margin:0px;padding:0px;">"none"</span><span style="color:#333333;font-family:&quot;font-size:12.6px;white-space:pre;background-color:rgba(128, 128, 128, 0.05);font-weight:bold;"> | awk </span><span class="hljs-string" style="color:#008800;font-family:&quot;font-size:12.6px;white-space:pre;background-color:rgba(128, 128, 128, 0.05);font-weight:bold;box-sizing:border-box;margin:0px;padding:0px;">'{print $3}'</span><span style="color:#333333;font-family:&quot;font-size:12.6px;white-space:pre;background-color:rgba(128, 128, 128, 0.05);font-weight:bold;">)&nbsp;</span></code></span> 
</p>
<p>
	<strong style="box-sizing:border-box;color:#3F3F3F;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;"><code style="box-sizing:border-box;font-family:&quot;font-size:14.4px;padding:2px 4px;white-space:nowrap;background-color:rgba(128, 128, 128, 0.075);border-radius:0px;"><br />
</code></strong> 
</p>
<p>
	通过实验一个docker&nbsp;image&nbsp;是可以启动多次的
</p>
<p>
	也就是说可以一个docker&nbsp;image做宿主&nbsp;挂载不同本机目录
</p>
<p>
	<br />
</p>
<p>
	==========================================================
</p>
<p>
	<span class="hljs-operator" style="box-sizing:border-box;margin:0px;padding:0px;color:#333333;font-family:&quot;font-size:12.6px;white-space:pre;background-color:rgba(128, 128, 128, 0.05);"><span class="hljs-keyword" style="box-sizing:border-box;margin:0px;padding:0px;color:#000088;"><span style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-size:16px;white-space:normal;font-family:Simsun;">镜像管理</span><span style="color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;"></span> </span></span> 
</p>
<blockquote style="box-sizing:border-box;padding:0px;margin:0px 0px 0px 40px;border:none;color:#454545;font-family:&quot;font-size:16px;white-space:normal;">
	<div style="box-sizing:border-box;margin:0px;padding:0px;">
		<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;">docker images：列出本地所有镜像</span> 
	</div>
</blockquote>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;">
	<blockquote style="box-sizing:border-box;padding:0px;margin:0px 0px 0px 40px;border:none;">
		<div style="box-sizing:border-box;margin:0px;padding:0px;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;line-height:1.875;">docker search &lt;IMAGE_ID/NAME&gt;：<span style="box-sizing:border-box;margin:0px;padding:0px;font-size:14px;line-height:1.5;">查找image</span></span> 
		</div>
		<div style="box-sizing:border-box;margin:0px;padding:0px;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;line-height:1.875;">docker pull&nbsp;</span><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;line-height:1.85714;">&lt;IMAGE_ID&gt;</span><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;line-height:1.875;">：</span><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;line-height:1.5;">下载image</span> 
		</div>
		<div style="box-sizing:border-box;margin:0px;padding:0px;">
			<div style="box-sizing:border-box;margin:0px;padding:0px;line-height:1.875;">
				<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;">docker push&nbsp;<span style="box-sizing:border-box;margin:0px;padding:0px;font-size:14px;line-height:1.78571;">&lt;IMAGE_ID&gt;：<span style="box-sizing:border-box;margin:0px;padding:0px;line-height:1.5;">上传image</span></span></span> 
			</div>
		</div>
		<div style="box-sizing:border-box;margin:0px;padding:0px;">
			<div style="box-sizing:border-box;margin:0px;padding:0px;line-height:1.875;">
				<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;">docker rmi&nbsp;<span style="box-sizing:border-box;margin:0px;padding:0px;font-size:14px;line-height:1.71429;">&lt;IMAGE_ID&gt;：<span style="box-sizing:border-box;margin:0px;padding:0px;line-height:1.5;">删除image</span></span></span> 
			</div>
		</div>
	</blockquote>
	<div style="box-sizing:border-box;margin:0px;padding:0px;">
		<div style="box-sizing:border-box;margin:0px;padding:0px;line-height:1.875;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;"><span style="box-sizing:border-box;margin:0px;padding:0px;font-size:14px;line-height:1.71429;"></span></span> 
		</div>
	</div>
	<div style="box-sizing:border-box;margin:0px;padding:0px;">
		<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Monaco, Menlo, Consolas, &quot;color:#333333;"><br style="box-sizing:border-box;" />
</span> 
	</div>
	<div style="box-sizing:border-box;margin:0px;padding:0px;">
		<span style="box-sizing:border-box;margin:0px;padding:0px;"><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;">容器管理<br style="box-sizing:border-box;" />
</span></span> 
	</div>
	<blockquote style="box-sizing:border-box;padding:0px;margin:0px 0px 0px 40px;border:none;">
		<div style="box-sizing:border-box;margin:0px;padding:0px;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;"><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;"></span></span> 
			<div style="box-sizing:border-box;margin:0px;padding:0px;font-family:微软雅黑;font-size:14px;line-height:1.5;">
				<span style="box-sizing:border-box;margin:0px;padding:0px;"><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;">docker run -i -t &lt;IMAGE_ID&gt; /bin/bash：-i：标准输入给容器 &nbsp; &nbsp;-t：分配一个虚拟终端 &nbsp; &nbsp;/bin/bash：执行bash脚本</span></span> 
			</div>
		</div>
	</blockquote>
	<blockquote style="box-sizing:border-box;padding:0px;margin:0px 0px 0px 40px;border:none;">
		<blockquote style="box-sizing:border-box;padding:0px;margin:0px 0px 0px 40px;border:none;">
			<div style="box-sizing:border-box;margin:0px;padding:0px;">
				<span style="box-sizing:border-box;margin:0px;padding:0px;"><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;"></span></span> 
				<div style="box-sizing:border-box;margin:0px;padding:0px;font-family:微软雅黑;font-size:14px;line-height:1.5;">
					<span style="box-sizing:border-box;margin:0px;padding:0px;"><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;">-d：以守护进程方式运行（后台）</span></span> 
				</div>
			</div>
		</blockquote>
		<blockquote style="box-sizing:border-box;padding:0px;margin:0px 0px 0px 40px;border:none;">
			<div style="box-sizing:border-box;margin:0px;padding:0px;">
				<span style="box-sizing:border-box;margin:0px;padding:0px;"><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;"></span></span> 
				<div style="box-sizing:border-box;margin:0px;padding:0px;font-family:微软雅黑;font-size:14px;line-height:1.5;">
					<span style="box-sizing:border-box;margin:0px;padding:0px;"><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;">-P：默认匹配docker容器的5000端口号到宿主机的<span style="box-sizing:border-box;margin:0px;padding:0px;">49153 to 65535端口</span></span></span> 
				</div>
			</div>
		</blockquote>
		<blockquote style="box-sizing:border-box;padding:0px;margin:0px 0px 0px 40px;border:none;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;"><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;"></span></span> 
			<div style="box-sizing:border-box;margin:0px;padding:0px;font-family:微软雅黑;font-size:14px;line-height:1.5;">
				<span style="box-sizing:border-box;margin:0px;padding:0px;"><span style="box-sizing:border-box;margin:0px;padding:0px;"><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;">-p &lt;HOT_PORT&gt;:&lt;CONTAINER_PORT&gt;：指定端口号</span></span></span> 
			</div>
			<div style="box-sizing:border-box;margin:0px;padding:0px;font-size:14px;line-height:1.5;">
				- -name： 指定容器的名称
			</div>
			<div style="box-sizing:border-box;margin:0px;padding:0px;font-size:14px;line-height:1.5;">
				- -rm：退出时删除容器
			</div>
			<div style="box-sizing:border-box;margin:0px;padding:0px;font-family:微软雅黑;font-size:14px;line-height:1.5;">
				<span style="box-sizing:border-box;margin:0px;padding:0px;"><span style="box-sizing:border-box;margin:0px;padding:0px;"><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;"><br style="box-sizing:border-box;" />
</span></span></span> 
			</div>
		</blockquote>
<span style="box-sizing:border-box;margin:0px;padding:0px;line-height:1.5;font-family:Simsun;">docker stop&nbsp;<span style="box-sizing:border-box;margin:0px;padding:0px;line-height:1.5;">&lt;CONTAINER_ID&gt;</span>：</span><span style="box-sizing:border-box;margin:0px;padding:0px;line-height:1.5;font-family:Simsun;">停止container</span><br style="box-sizing:border-box;" />
<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;line-height:1.5;">docker start</span><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;line-height:1.5;">&nbsp;</span><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;line-height:1.5;">&lt;CONTAINER_ID&gt;</span><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;line-height:1.5;">：</span><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;line-height:1.5;">重新启动container</span> 
	</blockquote>
	<blockquote style="box-sizing:border-box;padding:0px;margin:0px 0px 0px 40px;border:none;">
		<div style="box-sizing:border-box;margin:0px;padding:0px;">
			<div style="box-sizing:border-box;margin:0px;padding:0px;">
				<div style="box-sizing:border-box;margin:0px;padding:0px;">
					<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;"><span style="box-sizing:border-box;margin:0px;padding:0px;">docker ps</span>&nbsp;- Lists containers.</span> 
				</div>
			</div>
		</div>
	</blockquote>
	<blockquote style="box-sizing:border-box;padding:0px;margin:0px 0px 0px 40px;border:none;">
		<blockquote style="box-sizing:border-box;padding:0px;margin:0px 0px 0px 40px;border:none;">
			<div style="box-sizing:border-box;margin:0px;padding:0px;">
				<div style="box-sizing:border-box;margin:0px;padding:0px;">
					<div style="box-sizing:border-box;margin:0px;padding:0px;">
						<div style="box-sizing:border-box;margin:0px;padding:0px;">
							<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;">-l：显示最后启动的容器</span> 
						</div>
					</div>
				</div>
			</div>
		</blockquote>
	</blockquote>
	<blockquote style="box-sizing:border-box;padding:0px;margin:0px 0px 0px 40px;border:none;">
		<blockquote style="box-sizing:border-box;padding:0px;margin:0px 0px 0px 40px;border:none;">
			<div style="box-sizing:border-box;margin:0px;padding:0px;">
				<div style="box-sizing:border-box;margin:0px;padding:0px;">
					<div style="box-sizing:border-box;margin:0px;padding:0px;">
						<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;">-a：同时显示停止的容器，默认只显示启动状态</span> 
					</div>
				</div>
			</div>
		</blockquote>
	</blockquote>
	<blockquote style="box-sizing:border-box;padding:0px;margin:0px 0px 0px 40px;border:none;">
		<br style="box-sizing:border-box;" />
	</blockquote>
	<blockquote style="box-sizing:border-box;padding:0px;margin:0px 0px 0px 40px;border:none;">
		<div style="box-sizing:border-box;margin:0px;padding:0px;">
			<div style="box-sizing:border-box;margin:0px;padding:0px;">
				<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;">docker attach &lt;CONTAINER_ID&gt; 连接到启动的容器</span> 
			</div>
		</div>
		<div style="box-sizing:border-box;margin:0px;padding:0px;">
			<div style="box-sizing:border-box;margin:0px;padding:0px;">
				<div style="box-sizing:border-box;margin:0px;padding:0px;">
					<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;">docker logs &lt;CONTAINER_ID&gt; &nbsp;: 输出容器日志</span> 
				</div>
			</div>
			<blockquote style="box-sizing:border-box;padding:10px 20px;margin:0px 0px 20px;border-left:5px solid #EEEEEE;font-family:微软雅黑;font-size:14px;line-height:1.5;">
				<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;">-f：实时输出</span> 
			</blockquote>
<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;">docker cp &lt;CONTAINER_ID&gt;:path hostpath：复制容器内的文件到宿主机目录上</span> 
		</div>
		<div style="box-sizing:border-box;margin:0px;padding:0px;">
			<div style="box-sizing:border-box;margin:0px;padding:0px;">
				<div style="box-sizing:border-box;margin:0px;padding:0px;">
					<div style="box-sizing:border-box;margin:0px;padding:0px;">
						<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Monaco, Consolas, Courier, &quot;line-height:1.5;"></span> 
					</div>
				</div>
			</div>
		</div>
	</blockquote>
	<blockquote style="box-sizing:border-box;padding:0px;margin:0px 0px 0px 40px;border:none;">
		<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;"><span style="box-sizing:border-box;margin:0px;padding:0px;">docker rm&nbsp;</span><span style="box-sizing:border-box;margin:0px;padding:0px;">&lt;CONTAINER_ID&gt;</span><span style="box-sizing:border-box;margin:0px;padding:0px;">：</span><span style="box-sizing:border-box;margin:0px;padding:0px;">删除container</span></span> 
	</blockquote>
	<blockquote style="box-sizing:border-box;padding:0px;margin:0px 0px 0px 40px;border:none;">
		<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;">docker rm `docker ps -a -q`：删除所有容器</span> 
	</blockquote>
	<blockquote style="box-sizing:border-box;padding:0px;margin:0px 0px 0px 40px;border:none;">
		<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;">docker kill `docker ps -q`</span> 
	</blockquote>
	<blockquote style="box-sizing:border-box;padding:0px;margin:0px 0px 0px 40px;border:none;">
		<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;">docker rmi `docker images -q -a`</span> 
	</blockquote>
	<blockquote style="box-sizing:border-box;padding:0px;margin:0px 0px 0px 40px;border:none;">
		<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;">docker wait &lt;CONTAINER_ID&gt;：阻塞对容器的其他调用方法，直到容器停止后退出</span> 
	</blockquote>
	<blockquote style="box-sizing:border-box;padding:0px;margin:0px 0px 0px 40px;border:none;">
		<br style="box-sizing:border-box;" />
	</blockquote>
	<blockquote style="box-sizing:border-box;padding:0px;margin:0px 0px 0px 40px;border:none;">
		<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;">docker top &lt;CONTAINER_ID&gt;：查看容器中运行的进程</span> 
	</blockquote>
	<blockquote style="box-sizing:border-box;padding:0px;margin:0px 0px 0px 40px;border:none;">
		<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;"><span style="box-sizing:border-box;margin:0px;padding:0px;">docker diff&nbsp;<span style="box-sizing:border-box;margin:0px;padding:0px;font-size:14px;line-height:1.5;">&lt;CONTAINER_ID&gt;：查看容器中的变化</span></span></span> 
	</blockquote>
	<blockquote style="box-sizing:border-box;padding:0px;margin:0px 0px 0px 40px;border:none;">
		<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;"><span style="box-sizing:border-box;margin:0px;padding:0px;">docker inspect&nbsp;<span style="box-sizing:border-box;margin:0px;padding:0px;font-size:14px;line-height:1.5;">&lt;CONTAINER_ID&gt;：查看容器详细信息（输出为Json）</span></span></span> 
	</blockquote>
	<blockquote style="box-sizing:border-box;padding:0px;margin:0px 0px 0px 40px;border:none;">
		<blockquote style="box-sizing:border-box;padding:0px;margin:0px 0px 0px 40px;border:none;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;"><span style="box-sizing:border-box;margin:0px;padding:0px;"><span style="box-sizing:border-box;margin:0px;padding:0px;font-size:14px;line-height:1.5;">-f：查找特定信息，如</span></span></span><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Monaco, Consolas, Courier, &quot;line-height:1.5;color:#48484C;">docker inspect&nbsp;</span><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Monaco, Consolas, Courier, &quot;line-height:1.5;color:#93A1A1;">-</span><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Monaco, Consolas, Courier, &quot;line-height:1.5;color:#48484C;">f&nbsp;</span><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Monaco, Consolas, Courier, &quot;line-height:1.5;color:#48484C;">'{{ .NetworkSettings.IPAddress }}'</span> 
		</blockquote>
	</blockquote>
	<div style="box-sizing:border-box;margin:0px;padding:0px;">
	</div>
</div>
<span style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-size:16px;white-space:normal;font-family:Simsun;">&nbsp; &nbsp; &nbsp; docker commit -m "comment" -a "author" &lt;CONTAINER_ID&gt; &nbsp;ouruser/imagename:tag</span><span style="color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;"></span> 
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;"><br style="box-sizing:border-box;" />
</span> 
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;">&nbsp; &nbsp; &nbsp; docker extc -it &lt;CONTAINER&gt; &lt;COMMAND&gt;：在容器里执行命令，并输出结果</span> 
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;"><br style="box-sizing:border-box;" />
</span> 
	<div style="box-sizing:border-box;margin:0px;padding:0px;">
		<div style="box-sizing:border-box;margin:0px;padding:0px;">
		</div>
		<div style="box-sizing:border-box;margin:0px;padding:0px;">
			<ul style="box-sizing:border-box;margin:0px;padding:0px;list-style-position:initial;list-style-image:initial;">
				<li style="box-sizing:border-box;margin:0px 0px 0px 40px;padding:0px;list-style:disc;">
					<br style="box-sizing:border-box;" />
				</li>
			</ul>
		</div>
		<div style="box-sizing:border-box;margin:0px;padding:0px;">
		</div>
	</div>
<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;">网络管理</span> 
	<blockquote style="box-sizing:border-box;padding:0px;margin:0px 0px 0px 40px;border:none;">
		<div style="box-sizing:border-box;margin:0px;padding:0px;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;">docker run -P：随机分配端口号</span> 
		</div>
		<div style="box-sizing:border-box;margin:0px;padding:0px;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;">docker run -p 5000:5000：绑定特定端口号（主机的所有网络接口的5000端口均绑定容器的5000端口）</span> 
		</div>
		<div style="box-sizing:border-box;margin:0px;padding:0px;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;">docker run -p 127.0.0.1:5000:5000：绑定主机的特定接口的端口号</span> 
		</div>
		<div style="box-sizing:border-box;margin:0px;padding:0px;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;line-height:1.5;">docker run&nbsp;</span><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;line-height:1.5;">-</span><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;line-height:1.5;">d&nbsp;</span><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;line-height:1.5;">-</span><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;line-height:1.5;">p&nbsp;</span><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;line-height:1.5;">127.0</span><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;line-height:1.5;">.</span><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;line-height:1.5;">0.1</span><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;line-height:1.5;">:</span><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;line-height:1.5;">5000</span><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;line-height:1.5;">:</span><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;line-height:1.5;">5000</span><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;line-height:1.5;">/</span><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;line-height:1.5;">udp training</span><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;line-height:1.5;">/</span><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;line-height:1.5;">webapp python app</span><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;line-height:1.5;">.</span><span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;line-height:1.5;">py：绑定udp端口号</span> 
		</div>
		<div style="box-sizing:border-box;margin:0px;padding:0px;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;font-family:Simsun;line-height:1.5;"><span style="box-sizing:border-box;margin:0px;padding:0px;font-size:14px;line-height:1.5;">docker port<span style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;</span><span style="box-sizing:border-box;margin:0px;padding:0px;line-height:1.5;">&lt;CONTAINER_ID&gt;&nbsp;</span></span><span style="box-sizing:border-box;margin:0px;padding:0px;font-size:14px;line-height:1.5;">5000：查看容器的5000端口对应本地机器的IP和端口号</span></span> 
		</div>
	</blockquote>
</div>
<br />
<p>
	<br />
</p>