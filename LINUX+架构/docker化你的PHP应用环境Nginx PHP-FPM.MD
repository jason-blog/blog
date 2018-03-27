https://www.centos.bz/2016/11/dockerise-your-php-application-with-nginx-and-php-fpm/
<h2 id="开始之前" style="box-sizing:border-box;font-family:&quot;line-height:18px;color:#444444;margin:16px 0px;font-size:18px;padding:10px 0px;border-bottom:1px solid #EEEEEE;white-space:normal;background-color:#FFFFFF;">
	开始之前
</h2>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:16px;color:#444444;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
	<br\ style="box-sizing: border-box;"><br style="box-sizing:border-box;" />
在开始之前，我们假设你对<a href="https://www.centos.bz/tag/docker/" style="box-sizing:border-box;background:transparent;color:#428BCA;">Docker</a>使用已经有了一些经验。本文尝试使用Docker官方存储库来运行一个简单的PHP应用程序，环境是<a href="https://www.centos.bz/category/web-server/nginx/" style="box-sizing:border-box;background:transparent;color:#428BCA;">Nginx</a>和PHP。首先第一件事当然是安装Docker（如果你还没安装）。第二获取<a href="https://www.centos.bz/tag/docker-compose/" style="box-sizing:border-box;background:transparent;color:#428BCA;">Docker Compose</a>。</br\>
</p>
<h2 id="配置Nginx" style="box-sizing:border-box;font-family:&quot;line-height:18px;color:#444444;margin:16px 0px;font-size:18px;padding:10px 0px;border-bottom:1px solid #EEEEEE;white-space:normal;background-color:#FFFFFF;">
	配置Nginx
</h2>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:16px;color:#444444;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
	<br\ style="box-sizing: border-box;"><br style="box-sizing:border-box;" />
我们从配置Web服务器开始，这里我们使用Docker官方的<a href="https://www.centos.bz/tag/nginx-2/" style="box-sizing:border-box;background:transparent;color:#428BCA;">Nginx</a>镜像。既然我们准备使用Docker Compose，我们接下来先创建docker-compose.yml文件，其实docker nginx的80端口映射到宿主机的8080端口：</br\>
</p>
<div class="hl-surround" style="box-sizing:border-box;background-color:#F9FBFC;border:1px solid #C3CED9;margin:0px 0px 5px;width:auto;height:auto;overflow:auto;font-family:Fixedsys, &quot;color:#444444;font-size:15px;white-space:normal;">
	<ol class="hl-main ln-show" title="Double click to hide line number." style="box-sizing:border-box;margin:0px;padding:0px 12px 0px 56px;background-image:url(&quot;background-color:transparent;background-repeat:no-repeat;background-position:5px 5px;list-style-position:outside !important;list-style-image:initial !important;">
		<li class="hl-firstline" style="box-sizing:border-box;border-top-width:1px;border-top-style:solid;border-left:1px solid #C3CED9;list-style:decimal outside !important;border-top-color:#E3EEF9 !important;font-size:12px !important;margin:0px !important;line-height:20px !important;padding:0px 0px 0px 12px !important;">
			web:
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;image: nginx:latest
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;ports:
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;- "8080:80"
		</li>
	</ol>
</div>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:16px;color:#444444;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
	现在我们运行：
</p>
<div class="hl-surround" style="box-sizing:border-box;background-color:#F9FBFC;border:1px solid #C3CED9;margin:0px 0px 5px;width:auto;height:auto;overflow:auto;font-family:Fixedsys, &quot;color:#444444;font-size:15px;white-space:normal;">
	<ol class="hl-main ln-show" title="Double click to hide line number." style="box-sizing:border-box;margin:0px;padding:0px 12px 0px 56px;background-image:url(&quot;background-color:transparent;background-repeat:no-repeat;background-position:5px 5px;list-style-position:outside !important;list-style-image:initial !important;">
		<li class="hl-firstline" style="box-sizing:border-box;border-top-width:1px;border-top-style:solid;border-left:1px solid #C3CED9;list-style:decimal outside !important;border-top-color:#E3EEF9 !important;font-size:12px !important;margin:0px !important;line-height:20px !important;padding:0px 0px 0px 12px !important;">
			docker-compose up
		</li>
	</ol>
</div>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:16px;color:#444444;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
	现在我们应该通过ip:8080会得到nginx的默认页面了。<br style="box-sizing:border-box;" />
<a href="https://www.centos.bz/wp-content/uploads/2016/11/pic1-1.png" rel="attachment wp-att-5967" style="box-sizing:border-box;background:transparent;color:#428BCA;"><img src="https://www.centos.bz/wp-content/uploads/2016/11/pic1-1.png" alt="pic1" width="1024" height="434" class="aligncenter size-full wp-image-5967" srcset="https://www.centos.bz/wp-content/uploads/2016/11/pic1-1.png 1024w, https://www.centos.bz/wp-content/uploads/2016/11/pic1-1-768x326.png 768w, https://www.centos.bz/wp-content/uploads/2016/11/pic1-1-200x85.png 200w" sizes="(max-width: 1024px) 100vw, 1024px" data-tag="bdshare" style="box-sizing:border-box;vertical-align:middle;max-width:100%;margin:0px auto;display:block;height:auto;text-align:center;" /></a><br style="box-sizing:border-box;" />
现在nginx是启动了，让我们再来添加一些配置。首先更新docker-compose.yml使它挂载到一个本地目录。我们使用目录code。
</p>
<div class="hl-surround" style="box-sizing:border-box;background-color:#F9FBFC;border:1px solid #C3CED9;margin:0px 0px 5px;width:auto;height:auto;overflow:auto;font-family:Fixedsys, &quot;color:#444444;font-size:15px;white-space:normal;">
	<ol class="hl-main ln-show" title="Double click to hide line number." style="box-sizing:border-box;margin:0px;padding:0px 12px 0px 56px;background-image:url(&quot;background-color:transparent;background-repeat:no-repeat;background-position:5px 5px;list-style-position:outside !important;list-style-image:initial !important;">
		<li class="hl-firstline" style="box-sizing:border-box;border-top-width:1px;border-top-style:solid;border-left:1px solid #C3CED9;list-style:decimal outside !important;border-top-color:#E3EEF9 !important;font-size:12px !important;margin:0px !important;line-height:20px !important;padding:0px 0px 0px 12px !important;">
			web:
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp;image: nginx:latest
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp;ports:
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp; &nbsp; &nbsp;- "8080:80"
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp;volumes:
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp; &nbsp; &nbsp;- ./code:/code
		</li>
	</ol>
</div>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:16px;color:#444444;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
	下一步我们创建一个虚拟机配置文件site.conf，设置其根目录为/code，把该文件放置到与docker-compose.yml同级目录。
</p>
<div class="hl-surround" style="box-sizing:border-box;background-color:#F9FBFC;border:1px solid #C3CED9;margin:0px 0px 5px;width:auto;height:auto;overflow:auto;font-family:Fixedsys, &quot;color:#444444;font-size:15px;white-space:normal;">
	<ol class="hl-main ln-show" title="Double click to hide line number." style="box-sizing:border-box;margin:0px;padding:0px 12px 0px 56px;background-image:url(&quot;background-color:transparent;background-repeat:no-repeat;background-position:5px 5px;list-style-position:outside !important;list-style-image:initial !important;">
		<li class="hl-firstline" style="box-sizing:border-box;border-top-width:1px;border-top-style:solid;border-left:1px solid #C3CED9;list-style:decimal outside !important;border-top-color:#E3EEF9 !important;font-size:12px !important;margin:0px !important;line-height:20px !important;padding:0px 0px 0px 12px !important;">
			server {
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp;index index.html;
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp;server_name php-docker.local;
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp;error_log&nbsp; /var/log/nginx/error.log;
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp;access_log /var/log/nginx/access.log;
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp;root /code;
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			}
		</li>
	</ol>
</div>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:16px;color:#444444;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
	为了让这个虚拟机配置生效，我们还需要再次更改docker-compose.yml文件：
</p>
<div class="hl-surround" style="box-sizing:border-box;background-color:#F9FBFC;border:1px solid #C3CED9;margin:0px 0px 5px;width:auto;height:auto;overflow:auto;font-family:Fixedsys, &quot;color:#444444;font-size:15px;white-space:normal;">
	<ol class="hl-main ln-show" title="Double click to hide line number." style="box-sizing:border-box;margin:0px;padding:0px 12px 0px 56px;background-image:url(&quot;background-color:transparent;background-repeat:no-repeat;background-position:5px 5px;list-style-position:outside !important;list-style-image:initial !important;">
		<li class="hl-firstline" style="box-sizing:border-box;border-top-width:1px;border-top-style:solid;border-left:1px solid #C3CED9;list-style:decimal outside !important;border-top-color:#E3EEF9 !important;font-size:12px !important;margin:0px !important;line-height:20px !important;padding:0px 0px 0px 12px !important;">
			web:
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp;image: nginx:latest
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp;ports:
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp; &nbsp; &nbsp;- "8080:80"
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp;volumes:
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp; &nbsp; &nbsp;- ./code:/code
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp; &nbsp; &nbsp;- ./site.conf:/etc/nginx/conf.d/site.conf
		</li>
	</ol>
</div>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:16px;color:#444444;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
	此次更新是把本地的site.conf挂载docker nginx里的/etc/nginx/conf.d/site.conf，这样这个配置文件就被添加到docker nginx里了。下面我们执行这个命令生效它：
</p>
<div class="hl-surround" style="box-sizing:border-box;background-color:#F9FBFC;border:1px solid #C3CED9;margin:0px 0px 5px;width:auto;height:auto;overflow:auto;font-family:Fixedsys, &quot;color:#444444;font-size:15px;white-space:normal;">
	<ol class="hl-main ln-show" title="Double click to hide line number." style="box-sizing:border-box;margin:0px;padding:0px 12px 0px 56px;background-image:url(&quot;background-color:transparent;background-repeat:no-repeat;background-position:5px 5px;list-style-position:outside !important;list-style-image:initial !important;">
		<li class="hl-firstline" style="box-sizing:border-box;border-top-width:1px;border-top-style:solid;border-left:1px solid #C3CED9;list-style:decimal outside !important;border-top-color:#E3EEF9 !important;font-size:12px !important;margin:0px !important;line-height:20px !important;padding:0px 0px 0px 12px !important;">
			docker-compose up
		</li>
	</ol>
</div>
<h2 id="配置PHP" style="box-sizing:border-box;font-family:&quot;line-height:18px;color:#444444;margin:16px 0px;font-size:18px;padding:10px 0px;border-bottom:1px solid #EEEEEE;white-space:normal;background-color:#FFFFFF;">
	配置PHP
</h2>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:16px;color:#444444;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
	<br\ style="box-sizing: border-box;"><br style="box-sizing:border-box;" />
现在我们已经把nginx配置好了，接下来配置PHP。首先是拉取官方的PHP7-FPM镜像，并链接到Nginx容器，docker-compose.yml如下：</br\>
</p>
<div class="hl-surround" style="box-sizing:border-box;background-color:#F9FBFC;border:1px solid #C3CED9;margin:0px 0px 5px;width:auto;height:auto;overflow:auto;font-family:Fixedsys, &quot;color:#444444;font-size:15px;white-space:normal;">
	<ol class="hl-main ln-show" title="Double click to hide line number." style="box-sizing:border-box;margin:0px;padding:0px 12px 0px 56px;background-image:url(&quot;background-color:transparent;background-repeat:no-repeat;background-position:5px 5px;list-style-position:outside !important;list-style-image:initial !important;">
		<li class="hl-firstline" style="box-sizing:border-box;border-top-width:1px;border-top-style:solid;border-left:1px solid #C3CED9;list-style:decimal outside !important;border-top-color:#E3EEF9 !important;font-size:12px !important;margin:0px !important;line-height:20px !important;padding:0px 0px 0px 12px !important;">
			web:
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp;image: nginx:latest
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp;ports:
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp; &nbsp; &nbsp;- "8080:80"
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp;volumes:
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp; &nbsp; &nbsp;- ./code:/code
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp; &nbsp; &nbsp;- ./site.conf:/etc/nginx/conf.d/site.conf
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp;links:
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp; &nbsp; &nbsp;- php
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			php:
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp;image: php:7-fpm
		</li>
	</ol>
</div>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:16px;color:#444444;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
	下一步是配置nginx使用<a href="https://www.centos.bz/tag/php-fpm/" style="box-sizing:border-box;background:transparent;color:#428BCA;">php-fpm</a>容器来解析php文件。更新后的site.conf如下：
</p>
<div class="hl-surround" style="box-sizing:border-box;background-color:#F9FBFC;border:1px solid #C3CED9;margin:0px 0px 5px;width:auto;height:auto;overflow:auto;font-family:Fixedsys, &quot;color:#444444;font-size:15px;white-space:normal;">
	<ol class="hl-main ln-show" title="Double click to hide line number." style="box-sizing:border-box;margin:0px;padding:0px 12px 0px 56px;background-image:url(&quot;background-color:transparent;background-repeat:no-repeat;background-position:5px 5px;list-style-position:outside !important;list-style-image:initial !important;">
		<li class="hl-firstline" style="box-sizing:border-box;border-top-width:1px;border-top-style:solid;border-left:1px solid #C3CED9;list-style:decimal outside !important;border-top-color:#E3EEF9 !important;font-size:12px !important;margin:0px !important;line-height:20px !important;padding:0px 0px 0px 12px !important;">
			server {
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp;index index.php index.html;
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp;server_name php-docker.local;
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp;error_log&nbsp; /var/log/nginx/error.log;
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp;access_log /var/log/nginx/access.log;
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp;root /code;
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp;location ~ \.php$ {
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp; &nbsp; &nbsp;try_files $uri =404;
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp; &nbsp; &nbsp;fastcgi_split_path_info ^(.+\.php)(/.+)$;
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp; &nbsp; &nbsp;fastcgi_pass php:9000;
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp; &nbsp; &nbsp;fastcgi_index index.php;
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp; &nbsp; &nbsp;include fastcgi_params;
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp; &nbsp; &nbsp;fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp; &nbsp; &nbsp;fastcgi_param PATH_INFO $fastcgi_path_info;
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp;}
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			}
		</li>
	</ol>
</div>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:16px;color:#444444;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
	为了测试，让我们在./code目录新建一个index.php，内容如下：
</p>
<div class="hl-surround" style="box-sizing:border-box;background-color:#F9FBFC;border:1px solid #C3CED9;margin:0px 0px 5px;width:auto;height:auto;overflow:auto;font-family:Fixedsys, &quot;color:#444444;font-size:15px;white-space:normal;">
	<ol class="hl-main ln-show" title="Double click to hide line number." style="box-sizing:border-box;margin:0px;padding:0px 12px 0px 56px;background-image:url(&quot;background-color:transparent;background-repeat:no-repeat;background-position:5px 5px;list-style-position:outside !important;list-style-image:initial !important;">
		<li class="hl-firstline" style="box-sizing:border-box;border-top-width:1px;border-top-style:solid;border-left:1px solid #C3CED9;list-style:decimal outside !important;border-top-color:#E3EEF9 !important;font-size:12px !important;margin:0px !important;line-height:20px !important;padding:0px 0px 0px 12px !important;">
			&lt;?php
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			phpinfo();
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			?&gt;
		</li>
	</ol>
</div>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:16px;color:#444444;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
	然后通过ip:8080打开，但出现File not found错误。这是因为PHP容器找不到此文件，我们也需要像nginx一样挂载code目录，更新docker-compose.yml文件如下：
</p>
<div class="hl-surround" style="box-sizing:border-box;background-color:#F9FBFC;border:1px solid #C3CED9;margin:0px 0px 5px;width:auto;height:auto;overflow:auto;font-family:Fixedsys, &quot;color:#444444;font-size:15px;white-space:normal;">
	<ol class="hl-main ln-show" title="Double click to hide line number." style="box-sizing:border-box;margin:0px;padding:0px 12px 0px 56px;background-image:url(&quot;background-color:transparent;background-repeat:no-repeat;background-position:5px 5px;list-style-position:outside !important;list-style-image:initial !important;">
		<li class="hl-firstline" style="box-sizing:border-box;border-top-width:1px;border-top-style:solid;border-left:1px solid #C3CED9;list-style:decimal outside !important;border-top-color:#E3EEF9 !important;font-size:12px !important;margin:0px !important;line-height:20px !important;padding:0px 0px 0px 12px !important;">
			web:
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp;image: nginx:latest
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp;ports:
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp; &nbsp; &nbsp;- "8080:80"
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp;volumes:
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp; &nbsp; &nbsp;- ./code:/code
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp; &nbsp; &nbsp;- ./site.conf:/etc/nginx/conf.d/site.conf
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp;links:
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp; &nbsp; &nbsp;- php
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			php:
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp;image: php:7-fpm
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp;volumes:
		</li>
		<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
			&nbsp;&nbsp; &nbsp; &nbsp; &nbsp;- ./code:/code
		</li>
	</ol>
</div>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:16px;color:#444444;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
	最后，启动容器：
</p>
<div class="hl-surround" style="box-sizing:border-box;background-color:#F9FBFC;border:1px solid #C3CED9;margin:0px 0px 5px;width:auto;height:auto;overflow:auto;font-family:Fixedsys, &quot;color:#444444;font-size:15px;white-space:normal;">
	<ol class="hl-main ln-show" title="Double click to hide line number." style="box-sizing:border-box;margin:0px;padding:0px 12px 0px 56px;background-image:url(&quot;background-color:transparent;background-repeat:no-repeat;background-position:5px 5px;list-style-position:outside !important;list-style-image:initial !important;">
		<li class="hl-firstline" style="box-sizing:border-box;border-top-width:1px;border-top-style:solid;border-left:1px solid #C3CED9;list-style:decimal outside !important;border-top-color:#E3EEF9 !important;font-size:12px !important;margin:0px !important;line-height:20px !important;padding:0px 0px 0px 12px !important;">
			docker-compose up
		</li>
	</ol>
</div>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:16px;color:#444444;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
	我们将会看到正常的phpinfo页面<br style="box-sizing:border-box;" />
<a href="https://www.centos.bz/wp-content/uploads/2016/11/pic2-1.png" rel="attachment wp-att-5966" style="box-sizing:border-box;background:transparent;color:#428BCA;"><img src="https://www.centos.bz/wp-content/uploads/2016/11/pic2-1.png" alt="pic2" width="1024" height="820" class="aligncenter size-full wp-image-5966" srcset="https://www.centos.bz/wp-content/uploads/2016/11/pic2-1.png 1024w, https://www.centos.bz/wp-content/uploads/2016/11/pic2-1-768x615.png 768w, https://www.centos.bz/wp-content/uploads/2016/11/pic2-1-187x150.png 187w" sizes="(max-width: 1024px) 100vw, 1024px" data-tag="bdshare" style="box-sizing:border-box;vertical-align:middle;max-width:100%;margin:0px auto;display:block;height:auto;text-align:center;" /></a> 
</p>
<p class="post-copyright" style="box-sizing:border-box;margin-top:10px;margin-bottom:16px;clear:both;background-color:#F2F2F2;color:#999999;padding:6px 15px 5px;border-radius:2px;text-align:center;font-family:&quot;white-space:normal;">
	转载请保留原文链接：<a href="https://www.centos.bz/" style="box-sizing:border-box;background:transparent;color:#999999;text-decoration-line:none;">Linux运维日志</a>&nbsp;»&nbsp;<a href="https://www.centos.bz/2016/11/dockerise-your-php-application-with-nginx-and-php-fpm/" style="box-sizing:border-box;background:transparent;color:#999999;text-decoration-line:none;">docker化你的PHP应用环境Nginx PHP-FPM</a> 
</p>
<p class="post-copyright" style="box-sizing:border-box;margin-top:10px;margin-bottom:16px;clear:both;background-color:#F2F2F2;color:#999999;padding:6px 15px 5px;border-radius:2px;text-align:center;font-family:&quot;white-space:normal;">
	<br />
</p>