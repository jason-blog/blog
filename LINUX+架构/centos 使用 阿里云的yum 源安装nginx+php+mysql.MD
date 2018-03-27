<p>
	http://blog.csdn.net/xiao_xiao_meng/article/details/70053828?locationNum=12&amp;fps=1
</p>
<p>
	<br />
</p>
<p>
	<h1 class="page-header" style="font-family:&quot;margin:35px 0px 30px;padding:0px 117px;font-weight:lighter;box-sizing:border-box;color:#333333;font-size:46px;line-height:1.3;white-space:normal;border-bottom:none;background-color:#F8F8F8;">
		本文<a href="https://ninghao.net/blog/1368" target="_blank" style="color:#6795B5;outline:0px;margin:0px;padding:0px;box-sizing:border-box;text-decoration-line:none;font-family:&quot;font-size:14px;">原地址</a><span style="margin:0px;padding:0px;box-sizing:border-box;color:#999999;font-family:&quot;font-size:14px;">&nbsp; 百度找的些资料都是老的，到谷歌上搜到一套比较齐全的 顺便拿下来保存 转载了</span>
	</h1>
	<div id="node-1368" class="node node-blog view-mode-full clearfix" style="margin:0px;padding:0px;box-sizing:border-box;white-space:normal;color:#333333;font-family:&quot;font-size:14px;background-color:#F8F8F8;">
		<div class="node-content" style="margin:0px;padding:0px 117px;box-sizing:border-box;border-bottom:1px solid #E8E8E8;">
			<div class="content" style="margin:0px;padding:0px;box-sizing:border-box;">
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					阿里云的云服务器（ECS）可以选择多种操作系统，打算用它运行&nbsp;<a href="https://ninghao.net/course/tag/drupal" target="_blank" style="color:#333333;outline:0px;margin:0px;padding:0px 0px 2px;box-sizing:border-box;text-decoration-line:none;border-bottom:1px dotted #333333;">Drupal&nbsp;</a>或者&nbsp;<a href="https://ninghao.net/course/tag/wordpress" target="_blank" style="color:#333333;outline:0px;margin:0px;padding:0px 0px 2px;box-sizing:border-box;text-decoration-line:none;border-bottom:1px dotted #333333;">WordPress</a>&nbsp;，你最好选择 Linux 系统，这篇文章的演示是基于阿里云的&nbsp;<a href="http://www.centos.org/" target="_blank" style="color:#333333;outline:0px;margin:0px;padding:0px 0px 2px;box-sizing:border-box;text-decoration-line:none;border-bottom:1px dotted #333333;">CentOS</a>&nbsp;操作系统的服务器。我们在上面搭建一个&nbsp;<a href="http://nginx.org/" target="_blank" style="color:#333333;outline:0px;margin:0px;padding:0px 0px 2px;box-sizing:border-box;text-decoration-line:none;border-bottom:1px dotted #333333;">nginx</a>&nbsp;+ mysql + php-fpm 的环境，这就是常说的 LEMP（Linux NGINX MySQL / MariaDB PHP） 。我们不过多解释什么是什么，而是着重讲流程与方法，想了解具体的细节，去搜索下吧：）这个手册是在阿里云上测试的，不过应该也适用于其它使用 CentOS 系统的服务器。
				</p>
				<blockquote style="box-sizing:border-box;margin:0px 0px 20px -22px;font-size:16px;line-height:26px;color:#4F4F4F;padding:0px 0px 0px 15px;border-left:5px solid #EEEEEE;">
					<p style="margin-top:0px;margin-bottom:0px;padding:0px;box-sizing:border-box;font-size:17px;line-height:1.7;min-height:26px;text-align:justify;font-style:italic;font-family:&quot;">
						2016.12.05：更新了安装配置的方法，适用 CentOS 7.x，另外运行环境上的软件也都更新了，比如之前是 PHP 5.3，现在是 PHP 7。还有一篇在<a href="https://ninghao.net/blog/3630" target="_blank" style="color:#333333;outline:0px;margin:0px;padding:0px 0px 2px;box-sizing:border-box;text-decoration-line:none;border-bottom:1px dotted #333333;">本地使用虚拟机搭建这套环境</a>的方法，可以参考。我还专门做了一套视频课程《&nbsp;<a href="https://ninghao.net/course/2522" target="_blank" style="color:#333333;outline:0px;margin:0px;padding:0px 0px 2px;box-sizing:border-box;text-decoration-line:none;border-bottom:1px dotted #333333;">LEMP 网站应用运行环境</a>》，介绍了搭建 PHP 运行环境的整个过程，包括解决遇到的一些问题。了解更多关于 Linux 的东西，可以参考 &nbsp;《&nbsp;<a href="https://ninghao.net/package/centos" target="_blank" style="color:#333333;outline:0px;margin:0px;padding:0px 0px 2px;box-sizing:border-box;text-decoration-line:none;border-bottom:1px dotted #333333;">CentOS</a>》这个课程包。现在我更推荐使用 Docker 来做网站的运行环境，可以参考 《&nbsp;<a href="https://ninghao.net/package/docker" target="_blank" style="color:#333333;outline:0px;margin:0px;padding:0px 0px 2px;box-sizing:border-box;text-decoration-line:none;border-bottom:1px dotted #333333;">Docker</a>&nbsp;》课程包。
					</p>
				</blockquote>
				<h2 style="font-family:inherit;margin:30px 0px;padding:0px;font-weight:300;box-sizing:border-box;color:inherit;font-size:31.5px;line-height:40px;">
					<a name="t1"></a>背景
				</h2>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					宁皓网的《&nbsp;<a title="课程页面" href="https://ninghao.net/course/514" target="_blank" style="color:#333333;outline:0px;margin:0px;padding:0px 0px 2px;box-sizing:border-box;text-decoration-line:none;border-bottom:1px dotted #333333;">CentOS：在阿里云上运行网站</a>&nbsp;》这个课程里面演示了在阿里云服务器上搭建 AMP 环境，也就是 Apache + MySQL + PHP，并且介绍了 Linux 系统的基本的操作，还有文件目录权限的问题。这些非常重要，可以先看看。
				</p>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					这次想用 Nginx 代替 Apache 服务器，宁皓网现在用的是 Apache 服务器，最近出了点<a href="https://ninghao.net/blog/1366" target="_blank" style="color:#333333;outline:0px;margin:0px;padding:0px 0px 2px;box-sizing:border-box;text-decoration-line:none;border-bottom:1px dotted #333333;">问题</a>。所以想更换服务器的系统，并且把 Web Server 换成 Nginx。顺便也去学习一下环境的优化，还有打算把&nbsp;<a href="http://memcached.org/" target="_blank" style="color:#333333;outline:0px;margin:0px;padding:0px 0px 2px;box-sizing:border-box;text-decoration-line:none;border-bottom:1px dotted #333333;">memcache</a>&nbsp;也用上，也可能会加上&nbsp;<a href="https://www.varnish-cache.org/" target="_blank" style="color:#333333;outline:0px;margin:0px;padding:0px 0px 2px;box-sizing:border-box;text-decoration-line:none;border-bottom:1px dotted #333333;">varnish&nbsp;</a>，我会把整个过程写下来与大伙分享。下面开始第一步，创建一个阿里云服务器的实例。
				</p>
				<h2 style="font-family:inherit;margin:30px 0px;padding:0px;font-weight:300;box-sizing:border-box;color:inherit;font-size:31.5px;line-height:40px;">
					<a name="t2"></a>创建服务器实例
				</h2>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					创建一个服务器实例其实就是去购买一台相应配置的云服务器。注册并登录到阿里云的网站，在 产品服务 里选择&nbsp;云服务器 ECS ，点击页面上的 立即购买。可以 包年包月 的购买，也可以 按量付费，也就是用多少花多少，不过这种方式不支持网站的备案。
				</p>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					确定后，可以按需要去配置服务器，建议最初可以选择最低配置，因为后续升级也非常容易。选择 CPU，内存，带宽，不同的配置价格不同。你还要选择&nbsp;地域 ，也就是云服务器所在的地方，目前只有 青岛 与 杭州。再去选择操作系统，这篇文章所做的测试用的是&nbsp;<em style="box-sizing:border-box;">CentOS 6.3</em>&nbsp;64 位。需要的话可以再增加一块数据盘，默认会带一个系统盘，一共 20 G ，足够我们测试用了。
				</p>
				<blockquote style="box-sizing:border-box;margin:0px 0px 20px -22px;font-size:16px;line-height:26px;color:#4F4F4F;padding:0px 0px 0px 15px;border-left:5px solid #EEEEEE;">
					<p style="margin-top:0px;margin-bottom:0px;padding:0px;box-sizing:border-box;font-size:17px;line-height:1.7;min-height:26px;text-align:justify;font-style:italic;font-family:&quot;">
						2016.12.05：现在推荐使用 CentOS 7 64 位。
					</p>
				</blockquote>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					<img class="alignnone size-full wp-image-326" src="http://work.ninghao.net/magazine/wp-content/uploads/sites/2/2014/03/aliyun-05.png" alt="aliyun-05" width="1152" height="675" style="outline:0px;box-sizing:border-box;max-width:100%;margin:10px 0px;vertical-align:middle;" />
				</p>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					点击&nbsp;<span style="margin:0px;padding:0px;font-weight:700;box-sizing:border-box;">立即购买</span>，预览一下所选的服务器，然后&nbsp;<span style="margin:0px;padding:0px;font-weight:700;box-sizing:border-box;">提交订单</span>。
				</p>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					<img class="alignnone size-full wp-image-319" src="http://work.ninghao.net/magazine/wp-content/uploads/sites/2/2014/03/aliyun-01.png" alt="aliyun-01" width="1150" height="567" style="outline:0px;box-sizing:border-box;max-width:100%;margin:10px 0px;vertical-align:middle;" />
				</p>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					选择支付方式，然后点击&nbsp;<span style="margin:0px;padding:0px;font-weight:700;box-sizing:border-box;">确认支付</span>。
				</p>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					<img class="alignnone size-full wp-image-320" src="http://work.ninghao.net/magazine/wp-content/uploads/sites/2/2014/03/aliyun-02.png" alt="aliyun-02" width="1150" height="657" style="outline:0px;box-sizing:border-box;max-width:100%;margin:10px 0px;vertical-align:middle;" />
				</p>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					注意支付以后，可能会等一小会儿订单才能生效。至少我是等了一会儿，也可能是因为我用的手机版的支付宝。支付成功以后，打开你的个人账户页面，选择 管理控制台，在这里，你可以找到购买的云服务器。云服务器默认的&nbsp;<span style="margin:0px;padding:0px;font-weight:700;box-sizing:border-box;">root</span>（超级管理员） 用户的密码，会发送到你的手机上，你也可以点击&nbsp;<span style="margin:0px;padding:0px;font-weight:700;box-sizing:border-box;">修改密码</span>，去修改 root 用户密码。
				</p>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					在这个界面，你还可以 停止 &nbsp;或 重启 去服务器。也可以找到你的服务器的公众的 IP 地址。我购买的这台服务器地址是 218.244.147.196，使用这个地址配合 root 用户和密码，你可以使用工具登录到服务器，对它进行远程管理，比如安装软件，修改设置，重启服务等等。
				</p>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					<img class="alignnone size-full wp-image-322" src="http://work.ninghao.net/magazine/wp-content/uploads/sites/2/2014/03/aliyun-04.png" alt="aliyun-04" width="1150" height="612" style="outline:0px;box-sizing:border-box;max-width:100%;margin:10px 0px;vertical-align:middle;" />
				</p>
				<h2 style="font-family:inherit;margin:30px 0px;padding:0px;font-weight:300;box-sizing:border-box;color:inherit;font-size:31.5px;line-height:40px;">
					<a name="t3"></a>远程控制你的服务器
				</h2>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					远程控制 Linux 类型的系统的服务器，比如 CentOS 系统的服务器，一般不像 Windows 服务器那样，使用图形界面的远程控制。我们需要使用命令行工具，远程连接到服务器，然后使用命令去控制服务器。Windows 用户可以使用&nbsp;<a href="http://www.chiark.greenend.org.uk/~sgtatham/putty/" target="_blank" style="color:#333333;outline:0px;margin:0px;padding:0px 0px 2px;box-sizing:border-box;text-decoration-line:none;border-bottom:1px dotted #333333;">Putty&nbsp;</a>，Mac 用户可以使用系统自带的终端工具。然后用 ssh 命令，连接到你的服务器。像这样：
				</p>
<pre class="hljs css" name="code" style="margin-top:0px;margin-bottom:30px;padding:16px;box-sizing:border-box;color:#ABB2BF;background:#282C34;font-family:Monaco, Menlo, Consolas, &quot;font-size:15px;line-height:1.5;white-space:pre-wrap;"><span class="hljs-selector-tag" style="margin:0px;padding:0px;box-sizing:border-box;color:#E06C75;">ssh</span> <span class="hljs-selector-tag" style="margin:0px;padding:0px;box-sizing:border-box;color:#E06C75;">root</span>@<span class="hljs-keyword" style="margin:0px;padding:0px;box-sizing:border-box;color:#C678DD;">218</span>.<span class="hljs-keyword" style="margin:0px;padding:0px;box-sizing:border-box;color:#C678DD;">244</span>.<span class="hljs-keyword" style="margin:0px;padding:0px;box-sizing:border-box;color:#C678DD;">147</span>.<span class="hljs-keyword" style="margin:0px;padding:0px;box-sizing:border-box;color:#C678DD;">196</span></pre>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					@ 左边的 root 是连接时使用的用户的名字，@ 右边的数字是你的服务器的 IP 地址。这行命令的意思就是，使用 root 用户，登录到&nbsp;218.244.147.196 这台服务器上。回车以后，会提示你输入 root 用户的密码（这个密码阿里云会发送到你手机上）。
				</p>
				<h2 style="font-family:inherit;margin:30px 0px;padding:0px;font-weight:300;box-sizing:border-box;color:inherit;font-size:31.5px;line-height:40px;">
					<a name="t4"></a>添加新用户并分配 Root 权限
				</h2>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					为了安全，我们可以单独创建一个平时操作服务器的用户，并且给这个用户分配可以使用 Root 的权限，也就是如果需要 Root 权限，可以在命令的前面加上 sudo 获取到 Root 用户的权限。
				</p>
				<h3 style="font-family:inherit;margin:30px 0px;padding:0px;font-weight:300;box-sizing:border-box;color:inherit;font-size:24.5px;line-height:40px;">
					<a name="t5"></a>添加新用户
				</h3>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					比如添加一个名字是 wanghao 的用户，可以这样：
				</p>
<pre class="hljs nginx" name="code" style="margin-top:0px;margin-bottom:30px;padding:16px;box-sizing:border-box;color:#ABB2BF;background:#282C34;font-family:Monaco, Menlo, Consolas, &quot;font-size:15px;line-height:1.5;white-space:pre-wrap;"><span class="hljs-attribute" style="margin:0px;padding:0px;box-sizing:border-box;color:#98C379;">adduser</span> wanghao</pre>
				<h3 style="font-family:inherit;margin:30px 0px;padding:0px;font-weight:300;box-sizing:border-box;color:inherit;font-size:24.5px;line-height:40px;">
					<a name="t6"></a>设置密码
				</h3>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					为用户设置密码：
				</p>
<pre class="hljs nginx" name="code" style="margin-top:0px;margin-bottom:30px;padding:16px;box-sizing:border-box;color:#ABB2BF;background:#282C34;font-family:Monaco, Menlo, Consolas, &quot;font-size:15px;line-height:1.5;white-space:pre-wrap;"><span class="hljs-attribute" style="margin:0px;padding:0px;box-sizing:border-box;color:#98C379;">passwd</span> wanghao</pre>
				<h3 style="font-family:inherit;margin:30px 0px;padding:0px;font-weight:300;box-sizing:border-box;color:inherit;font-size:24.5px;line-height:40px;">
					<a name="t7"></a>分配 Root 权限
				</h3>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					让我们新创建的用户拥有 Root 用户的权限，执行：
				</p>
<pre class="hljs bash" name="code" style="margin-top:0px;margin-bottom:30px;padding:16px;box-sizing:border-box;color:#ABB2BF;background:#282C34;font-family:Monaco, Menlo, Consolas, &quot;font-size:15px;line-height:1.5;white-space:pre-wrap;">gpasswd <span class="hljs-_" style="margin:0px;padding:0px;box-sizing:border-box;">-a</span> wanghao wheel</pre>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					把 wanghao 这个用户名换成你自己的用户名。
				</p>
				<h3 style="font-family:inherit;margin:30px 0px;padding:0px;font-weight:300;box-sizing:border-box;color:inherit;font-size:24.5px;line-height:40px;">
					<a name="t8"></a>用新用户登录服务器
				</h3>
<pre class="hljs css" name="code" style="margin-top:0px;margin-bottom:30px;padding:16px;box-sizing:border-box;color:#ABB2BF;background:#282C34;font-family:Monaco, Menlo, Consolas, &quot;font-size:15px;line-height:1.5;white-space:pre-wrap;"><span class="hljs-selector-tag" style="margin:0px;padding:0px;box-sizing:border-box;color:#E06C75;">ssh</span> <span class="hljs-selector-tag" style="margin:0px;padding:0px;box-sizing:border-box;color:#E06C75;">wanghao</span>@<span class="hljs-keyword" style="margin:0px;padding:0px;box-sizing:border-box;color:#C678DD;">218</span>.<span class="hljs-keyword" style="margin:0px;padding:0px;box-sizing:border-box;color:#C678DD;">244</span>.<span class="hljs-keyword" style="margin:0px;padding:0px;box-sizing:border-box;color:#C678DD;">147</span>.<span class="hljs-keyword" style="margin:0px;padding:0px;box-sizing:border-box;color:#C678DD;">196</span></pre>
				<h2 style="font-family:inherit;margin:30px 0px;padding:0px;font-weight:300;box-sizing:border-box;color:inherit;font-size:31.5px;line-height:40px;">
					<a name="t9"></a>仓库
				</h2>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					为了可以使用 CentOS 系统的包管理工具去安装更多的东西，我们需要单独安装一些额外的软件仓库。
				</p>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					EPEL
				</p>
<pre class="hljs sql" name="code" style="margin-top:0px;margin-bottom:30px;padding:16px;box-sizing:border-box;color:#ABB2BF;background:#282C34;font-family:Monaco, Menlo, Consolas, &quot;font-size:15px;line-height:1.5;white-space:pre-wrap;">sudo yum <span class="hljs-keyword" style="margin:0px;padding:0px;box-sizing:border-box;color:#C678DD;">install</span> epel-<span class="hljs-keyword" style="margin:0px;padding:0px;box-sizing:border-box;color:#C678DD;">release</span> -y</pre>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					IUS
				</p>
<pre class="hljs nginx" name="code" style="margin-top:0px;margin-bottom:30px;padding:16px;box-sizing:border-box;color:#ABB2BF;background:#282C34;font-family:Monaco, Menlo, Consolas, &quot;font-size:15px;line-height:1.5;white-space:pre-wrap;"><span class="hljs-attribute" style="margin:0px;padding:0px;box-sizing:border-box;color:#98C379;">sudo</span> yum install https://centos7.iuscommunity.org/ius-release.rpm -y</pre>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					IUS 仓库里面有我们需要的一些新的软件包，比如 PHP 7。注意我们安装的是为 CentOS &nbsp;7 这个系统准备的 IUS 仓库，如果你的系统是 CentOS 6，你需要到 IUS 网站上去查找适合的仓库的下载地址。
				</p>
				<h2 style="font-family:inherit;margin:30px 0px;padding:0px;font-weight:300;box-sizing:border-box;color:inherit;font-size:31.5px;line-height:40px;">
					<a name="t10"></a>安装 NGINX
				</h2>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					NGINX 这个软件包已经包装在 EPEL 仓库里了，之前我们已经安装了这个仓库，所以可以直接使用包管理工具去安装 NGINX。
				</p>
<pre class="hljs nginx" name="code" style="margin-top:0px;margin-bottom:30px;padding:16px;box-sizing:border-box;color:#ABB2BF;background:#282C34;font-family:Monaco, Menlo, Consolas, &quot;font-size:15px;line-height:1.5;white-space:pre-wrap;"><span class="hljs-attribute" style="margin:0px;padding:0px;box-sizing:border-box;color:#98C379;">sudo</span> yum install nginx -y</pre>
				<h3 style="font-family:inherit;margin:30px 0px;padding:0px;font-weight:300;box-sizing:border-box;color:inherit;font-size:24.5px;line-height:40px;">
					<a name="t11"></a>启动
				</h3>
<pre class="hljs nginx" name="code" style="margin-top:0px;margin-bottom:30px;padding:16px;box-sizing:border-box;color:#ABB2BF;background:#282C34;font-family:Monaco, Menlo, Consolas, &quot;font-size:15px;line-height:1.5;white-space:pre-wrap;"><span class="hljs-attribute" style="margin:0px;padding:0px;box-sizing:border-box;color:#98C379;">sudo</span> systemctl start nginx</pre>
				<h3 style="font-family:inherit;margin:30px 0px;padding:0px;font-weight:300;box-sizing:border-box;color:inherit;font-size:24.5px;line-height:40px;">
					<a name="t12"></a>开启自启动
				</h3>
<pre class="hljs bash" name="code" style="margin-top:0px;margin-bottom:30px;padding:16px;box-sizing:border-box;color:#ABB2BF;background:#282C34;font-family:Monaco, Menlo, Consolas, &quot;font-size:15px;line-height:1.5;white-space:pre-wrap;">sudo systemctl <span class="hljs-built_in" style="margin:0px;padding:0px;box-sizing:border-box;color:#E6C07B;">enable</span> nginx</pre>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					&nbsp;
				</p>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					服务启动以后，你就可以在浏览器上使用服务器的 IP 地址，或者指向这个地址的域名访问服务器指定的目录了。你会看到类似下面的这些文字。
				</p>
				<p class="alert alert-info" style="margin-top:0px;margin-bottom:20px;padding:8px 35px 8px 14px;box-sizing:border-box;font-size:17px;color:#3A87AD;line-height:1.7;min-height:26px;text-align:justify;background-color:#D9EDF7;border:1px solid #BCE8F1;font-family:&quot;">
					Welcome to nginx! If you see this page, the nginx web server is successfully installed and working. Further configuration is required. For online documentation and support please refer to nginx.org. Commercial support is available at nginx.com. Thank you for using nginx.
				</p>
				<h3 id="virtual-host" style="font-family:inherit;margin:30px 0px;padding:0px;font-weight:300;box-sizing:border-box;color:inherit;font-size:24.5px;line-height:40px;">
					<a name="t13"></a>配置 nginx 虚拟主机
				</h3>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					安装完 nginx 以后，第一件想到的事应该就是去创建虚拟主机，虚拟主机允许我们在同一台服务器上运行多个网站，我们可以为不同的域名绑定不同的目录，访问这个域名的时候，会打开对应目录里面的东西。之前介绍过为&nbsp;<a href="https://ninghao.net/blog/1293" target="_blank" style="color:#333333;outline:0px;margin:0px;padding:0px 0px 2px;box-sizing:border-box;text-decoration-line:none;border-bottom:1px dotted #333333;">Apache 服务器创建虚拟主机</a>，下面来看一下为 nginx 配置虚拟主机。先进入到 nginx 配置文件目录：
				</p>
<pre class="hljs bash" name="code" style="margin-top:0px;margin-bottom:30px;padding:16px;box-sizing:border-box;color:#ABB2BF;background:#282C34;font-family:Monaco, Menlo, Consolas, &quot;font-size:15px;line-height:1.5;white-space:pre-wrap;"><span class="hljs-built_in" style="margin:0px;padding:0px;box-sizing:border-box;color:#E6C07B;">cd</span>&nbsp;/etc/nginx/conf.d</pre>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					创建一个新的配置文件，比如我要为 nginx.ninghao.net 这个主机名创建一个虚拟主机，可以这样：
				</p>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					&nbsp;
				</p>
<pre class="hljs css" name="code" style="margin-top:0px;margin-bottom:30px;padding:16px;box-sizing:border-box;color:#ABB2BF;background:#282C34;font-family:Monaco, Menlo, Consolas, &quot;font-size:15px;line-height:1.5;white-space:pre-wrap;"><span class="hljs-selector-tag" style="margin:0px;padding:0px;box-sizing:border-box;color:#E06C75;">vim</span> <span class="hljs-selector-tag" style="margin:0px;padding:0px;box-sizing:border-box;color:#E06C75;">nginx</span><span class="hljs-selector-class" style="margin:0px;padding:0px;box-sizing:border-box;color:#D19A66;">.ninghao</span><span class="hljs-selector-class" style="margin:0px;padding:0px;box-sizing:border-box;color:#D19A66;">.net</span><span class="hljs-selector-class" style="margin:0px;padding:0px;box-sizing:border-box;color:#D19A66;">.conf</span></pre>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					把下面的配置代码放到这个配置文件里：
				</p>
<pre class="hljs nginx" name="code" style="margin-top:0px;margin-bottom:30px;padding:16px;box-sizing:border-box;color:#ABB2BF;background:#282C34;font-family:Monaco, Menlo, Consolas, &quot;font-size:15px;line-height:1.5;white-space:pre-wrap;"><span class="hljs-section" style="margin:0px;padding:0px;box-sizing:border-box;color:#E06C75;">server</span> { <span class="hljs-attribute" style="margin:0px;padding:0px;box-sizing:border-box;color:#98C379;">listen</span> <span class="hljs-number" style="margin:0px;padding:0px;box-sizing:border-box;color:#D19A66;">80</span>; <span class="hljs-attribute" style="margin:0px;padding:0px;box-sizing:border-box;color:#98C379;">server_name</span> nginx.ninghao.net; <span class="hljs-attribute" style="margin:0px;padding:0px;box-sizing:border-box;color:#98C379;">root</span> /home/www/nginx.ninghao.net; <span class="hljs-attribute" style="margin:0px;padding:0px;box-sizing:border-box;color:#98C379;">index</span> index.php index.html; <span class="hljs-attribute" style="margin:0px;padding:0px;box-sizing:border-box;color:#98C379;">location</span> / { <span class="hljs-attribute" style="margin:0px;padding:0px;box-sizing:border-box;color:#98C379;">try_files</span> <span class="hljs-variable" style="margin:0px;padding:0px;box-sizing:border-box;color:#D19A66;">$uri</span> <span class="hljs-variable" style="margin:0px;padding:0px;box-sizing:border-box;color:#D19A66;">$uri</span>/ /index.php?<span class="hljs-variable" style="margin:0px;padding:0px;box-sizing:border-box;color:#D19A66;">$query_string</span>;
  } <span class="hljs-attribute" style="margin:0px;padding:0px;box-sizing:border-box;color:#98C379;">location</span> <span class="hljs-regexp" style="margin:0px;padding:0px;box-sizing:border-box;color:#98C379;">~ \.php$</span> { <span class="hljs-attribute" style="margin:0px;padding:0px;box-sizing:border-box;color:#98C379;">fastcgi_pass</span> <span class="hljs-number" style="margin:0px;padding:0px;box-sizing:border-box;color:#D19A66;">127.0.0.1:9000</span>; <span class="hljs-attribute" style="margin:0px;padding:0px;box-sizing:border-box;color:#98C379;">fastcgi_index</span> index.php; <span class="hljs-attribute" style="margin:0px;padding:0px;box-sizing:border-box;color:#98C379;">include</span> fastcgi.conf;
  }
}</pre>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					上面这个配置文件支持一些的 PHP 应用，比如 WordPress，Drupal，Laravel。第一个 location 区块可以让 PHP 应用支持地址的重写功能，第二个 Location 设置了让虚拟主机可以去处理 PHP 的请求。注意这里用了 include 命令，包含进来一个 fastcgi.conf 文件，你要确定这个文件存在。
				</p>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					你也可能会找到&nbsp;fastcgi_params 这个文件，如果没有 fastcgi.conf 就把&nbsp;fastcgi_params 这个文件包含进来，并且在处理 php 的那个 location 区块里再添加一条配置：
				</p>
<pre class="hljs nginx" name="code" style="margin-top:0px;margin-bottom:30px;padding:16px;box-sizing:border-box;color:#ABB2BF;background:#282C34;font-family:Monaco, Menlo, Consolas, &quot;font-size:15px;line-height:1.5;white-space:pre-wrap;"><span class="hljs-attribute" style="margin:0px;padding:0px;box-sizing:border-box;color:#98C379;">fastcgi_param</span> SCRIPT_FILENAME <span class="hljs-variable" style="margin:0px;padding:0px;box-sizing:border-box;color:#D19A66;">$document_root</span><span class="hljs-variable" style="margin:0px;padding:0px;box-sizing:border-box;color:#D19A66;">$fastcgi_script_name</span>;</pre>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					<em style="box-sizing:border-box;">server_name</em>&nbsp;就是主机名，也就是跟这个虚拟主机绑定在一块儿的域名，我事先把&nbsp;<em style="box-sizing:border-box;">nginx.ninghao.net</em>&nbsp;指向了服务器，这个虚拟主机就是为它准备的，所以，<em style="box-sizing:border-box;">server_name</em>&nbsp;后面的东西就是&nbsp;<em style="box-sizing:border-box;">nginx.ninghao.net</em>&nbsp;。紧接着&nbsp;<em style="box-sizing:border-box;">server_name</em>&nbsp;下面可以是一个&nbsp;<em style="box-sizing:border-box;">root</em>，就是这个虚拟主机的根目录，也就是网站所在的目录。比如我们要把&nbsp;<em style="box-sizing:border-box;">nginx.ninghao.net</em>&nbsp;这个网站的文件放在&nbsp;<em style="box-sizing:border-box;">/home/www/nginx.ninghao.net</em>&nbsp;下面，那么这个&nbsp;<em style="box-sizing:border-box;">root</em>&nbsp;就是这个路径。
				</p>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					然后去掉 location / 里面的 root 这行代码。再在 index 后面加上一种索引文件名，也就是默认打开的文件，这里要加上一个 index.php ，这样访问 nginx.ninghao.net 就可以直接打开 root 目录下面的 index.php 了。稍后我们再去安装 php 。
				</p>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					保存一下，按&nbsp;<em style="box-sizing:border-box;">esc</em>&nbsp;，输入&nbsp;<em style="box-sizing:border-box;">:wp</em>（保存并退出）。现在虚拟主机应该就可以使用了。主机的域名是&nbsp;<em style="box-sizing:border-box;">nginx.ninghao.net</em>，访问它的时候，打开的是&nbsp;<em style="box-sizing:border-box;">/home/www/nginx.ninghao.net</em>&nbsp;这个目录里面的东西，你可以在这个目录下放点东西。
				</p>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					重启 nginx 或者重新加载 nginx 可以让配置文件生效。
				</p>
<pre class="hljs nginx" name="code" style="margin-top:0px;margin-bottom:30px;padding:16px;box-sizing:border-box;color:#ABB2BF;background:#282C34;font-family:Monaco, Menlo, Consolas, &quot;font-size:15px;line-height:1.5;white-space:pre-wrap;"><span class="hljs-attribute" style="margin:0px;padding:0px;box-sizing:border-box;color:#98C379;">sudo</span> systemctl reload nginx</pre>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					现在，打开浏览器，输入你为虚拟主机设置的域名，看看是否能打开你指定的目录里的东西。
				</p>
				<h2 style="font-family:inherit;margin:30px 0px;padding:0px;font-weight:300;box-sizing:border-box;color:inherit;font-size:31.5px;line-height:40px;">
					<a name="t14"></a>PHP
				</h2>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					要让 nginx 能够执行 php 文件，需要去安装一下&nbsp;<a href="http://php-fpm.org/" target="_blank" style="color:#333333;outline:0px;margin:0px;padding:0px 0px 2px;box-sizing:border-box;text-decoration-line:none;border-bottom:1px dotted #333333;">php-fpm</a>，我要安装的是比较新的 PHP 7 ，这个软件包可以在 IUS 仓库里找到，所以你需要先安装 IUS 仓库。
				</p>
<pre class="hljs nginx" name="code" style="margin-top:0px;margin-bottom:30px;padding:16px;box-sizing:border-box;color:#ABB2BF;background:#282C34;font-family:Monaco, Menlo, Consolas, &quot;font-size:15px;line-height:1.5;white-space:pre-wrap;"><span class="hljs-attribute" style="margin:0px;padding:0px;box-sizing:border-box;color:#98C379;">sudo</span> yum install php70u-fpm -y</pre>
				<h3 style="font-family:inherit;margin:30px 0px;padding:0px;font-weight:300;box-sizing:border-box;color:inherit;font-size:24.5px;line-height:40px;">
					<a name="t15"></a>启动
				</h3>
<pre class="hljs nginx" name="code" style="margin-top:0px;margin-bottom:30px;padding:16px;box-sizing:border-box;color:#ABB2BF;background:#282C34;font-family:Monaco, Menlo, Consolas, &quot;font-size:15px;line-height:1.5;white-space:pre-wrap;"><span class="hljs-attribute" style="margin:0px;padding:0px;box-sizing:border-box;color:#98C379;">sudo</span> systemctl start php-fpm</pre>
				<h3 style="font-family:inherit;margin:30px 0px;padding:0px;font-weight:300;box-sizing:border-box;color:inherit;font-size:24.5px;line-height:40px;">
					<a name="t16"></a>开机自启动
				</h3>
<pre class="hljs bash" name="code" style="margin-top:0px;margin-bottom:30px;padding:16px;box-sizing:border-box;color:#ABB2BF;background:#282C34;font-family:Monaco, Menlo, Consolas, &quot;font-size:15px;line-height:1.5;white-space:pre-wrap;">sudo systemctl <span class="hljs-built_in" style="margin:0px;padding:0px;box-sizing:border-box;color:#E6C07B;">enable</span> php-fpm</pre>
				<h3 style="font-family:inherit;margin:30px 0px;padding:0px;font-weight:300;box-sizing:border-box;color:inherit;font-size:24.5px;line-height:40px;">
					<a name="t17"></a>安装 PHP 扩展
				</h3>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					为了可以正常运行一般的 PHP 应用，你需要再安装一些其它的 PHP 扩展，通常你在安装 PHP 应用，比如 WordPress，Drupal，Laravel 的时候，都会提示你缺少的 PHP 扩展。下面是一些常用的 PHP 扩展：
				</p>
<pre class="hljs sql" name="code" style="margin-top:0px;margin-bottom:30px;padding:16px;box-sizing:border-box;color:#ABB2BF;background:#282C34;font-family:Monaco, Menlo, Consolas, &quot;font-size:15px;line-height:1.5;white-space:pre-wrap;">sudo yum <span class="hljs-keyword" style="margin:0px;padding:0px;box-sizing:border-box;color:#C678DD;">install</span> php70u-gd &nbsp;php70u-mysqlnd&nbsp;php70u-pdo&nbsp;php70u-mcrypt&nbsp;php70u-mbstring php70u-<span class="hljs-keyword" style="margin:0px;padding:0px;box-sizing:border-box;color:#C678DD;">json</span> php70u-opcache php70u-<span class="hljs-keyword" style="margin:0px;padding:0px;box-sizing:border-box;color:#C678DD;">xml</span> -y</pre>
				<h3 style="font-family:inherit;margin:30px 0px;padding:0px;font-weight:300;box-sizing:border-box;color:inherit;font-size:24.5px;line-height:40px;">
					<a name="t18"></a>重新加载 PHP-FPM
				</h3>
<pre class="hljs nginx" name="code" style="margin-top:0px;margin-bottom:30px;padding:16px;box-sizing:border-box;color:#ABB2BF;background:#282C34;font-family:Monaco, Menlo, Consolas, &quot;font-size:15px;line-height:1.5;white-space:pre-wrap;"><span class="hljs-attribute" style="margin:0px;padding:0px;box-sizing:border-box;color:#98C379;">sudo</span> systemctl reload php-fpm</pre>
				<h3 style="font-family:inherit;margin:30px 0px;padding:0px;font-weight:300;box-sizing:border-box;color:inherit;font-size:24.5px;line-height:40px;">
					<a name="t19"></a>测试是否可以执行 php
				</h3>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					现在，我们已经安装了 php-fpm，并修改了 nginx 的配置文件让它可以去执行 php，下面，我们得去测试一下，可以使用 php 的&nbsp;<em style="box-sizing:border-box;">phpinfo();</em>&nbsp;函数，方法是在你的虚拟主机根目录下面，创建一个 php 文件，命名为&nbsp;<em style="box-sizing:border-box;">phpinfo.php</em>，然后在这个文件里输入：
				</p>
<pre class="hljs xml" name="code" style="margin-top:0px;margin-bottom:30px;padding:16px;box-sizing:border-box;color:#ABB2BF;background:#282C34;font-family:Monaco, Menlo, Consolas, &quot;font-size:15px;line-height:1.5;white-space:pre-wrap;"><span class="php" style="margin:0px;padding:0px;box-sizing:border-box;"><span class="hljs-meta" style="margin:0px;padding:0px;box-sizing:border-box;color:#61AEEE;">&lt;?php</span> phpinfo(); <span class="hljs-meta" style="margin:0px;padding:0px;box-sizing:border-box;color:#61AEEE;">?&gt;</span></span></pre>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					保存文件并退出。在浏览器里打开刚才创建的这个 php 文件。我这里应该是&nbsp;<em style="box-sizing:border-box;"><a href="http://nginx.ninghao.net/phpinfo.php" target="_blank" style="color:#333333;outline:0px;margin:0px;padding:0px 0px 2px;box-sizing:border-box;text-decoration-line:none;border-bottom:1px dotted #333333;">http://nginx.ninghao.net/phpinfo.php</a></em>。打开以后，你应该能看到像下面这样的界面，如果能，说明 nginx 已经可以执行 php 了。
				</p>
				<h2 id="repo" style="font-family:inherit;margin:30px 0px;padding:0px;font-weight:300;box-sizing:border-box;color:inherit;font-size:31.5px;line-height:40px;">
					<a name="t20"></a>安装 MySQL&nbsp;/ MariaDB
				</h2>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					MySQL 与 MariaDB 是相互兼容的，现在社区推荐使用 MariaDB，所以我们可以去安装一下 MariaDB ，用它代替 MySQL 。
				</p>
<pre class="hljs sql" name="code" style="margin-top:0px;margin-bottom:30px;padding:16px;box-sizing:border-box;color:#ABB2BF;background:#282C34;font-family:Monaco, Menlo, Consolas, &quot;font-size:15px;line-height:1.5;white-space:pre-wrap;">sudo yum <span class="hljs-keyword" style="margin:0px;padding:0px;box-sizing:border-box;color:#C678DD;">install</span> mariadb101u-<span class="hljs-keyword" style="margin:0px;padding:0px;box-sizing:border-box;color:#C678DD;">server</span> -y</pre>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					如果出现冲突的提示，是因为系统本身自带 MariaDB，我们需要先删除掉系统本身带的，才能正常安装比较新的。一般可以这样来删除：
				</p>
<pre class="hljs nginx" name="code" style="margin-top:0px;margin-bottom:30px;padding:16px;box-sizing:border-box;color:#ABB2BF;background:#282C34;font-family:Monaco, Menlo, Consolas, &quot;font-size:15px;line-height:1.5;white-space:pre-wrap;"><span class="hljs-attribute" style="margin:0px;padding:0px;box-sizing:border-box;color:#98C379;">sudo</span> yum remove mariadb-libs -y</pre>
				<h3 style="font-family:inherit;margin:30px 0px;padding:0px;font-weight:300;box-sizing:border-box;color:inherit;font-size:24.5px;line-height:40px;">
					<a name="t21"></a>启动
				</h3>
<pre class="hljs nginx" name="code" style="margin-top:0px;margin-bottom:30px;padding:16px;box-sizing:border-box;color:#ABB2BF;background:#282C34;font-family:Monaco, Menlo, Consolas, &quot;font-size:15px;line-height:1.5;white-space:pre-wrap;"><span class="hljs-attribute" style="margin:0px;padding:0px;box-sizing:border-box;color:#98C379;">sudo</span> systemctl start mariadb</pre>
				<h3 style="font-family:inherit;margin:30px 0px;padding:0px;font-weight:300;box-sizing:border-box;color:inherit;font-size:24.5px;line-height:40px;">
					<a name="t22"></a>开机自启动
				</h3>
<pre class="hljs bash" name="code" style="margin-top:0px;margin-bottom:30px;padding:16px;box-sizing:border-box;color:#ABB2BF;background:#282C34;font-family:Monaco, Menlo, Consolas, &quot;font-size:15px;line-height:1.5;white-space:pre-wrap;">sudo systemctl <span class="hljs-built_in" style="margin:0px;padding:0px;box-sizing:border-box;color:#E6C07B;">enable</span> mariadb</pre>
				<h3 style="font-family:inherit;margin:30px 0px;padding:0px;font-weight:300;box-sizing:border-box;color:inherit;font-size:24.5px;line-height:40px;">
					<a name="t23"></a>安全配置
				</h3>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					然后我们需要简单配置一下 mysql ，默认安装以后 mysql 的 root 用户是没有密码的，对于生产环境来说，这肯定是不行的，另外还有一些安全相关的设置，可以使用下面这行命令去配置一下，它是一个向导，问你一些问题，你要给出答案，比如是否要设置 root 用户的密码， 密码是什么等等。
				</p>
<pre class="hljs" name="code" style="margin-top:0px;margin-bottom:30px;padding:16px;box-sizing:border-box;color:#ABB2BF;background:#282C34;font-family:Monaco, Menlo, Consolas, &quot;font-size:15px;line-height:1.5;white-space:pre-wrap;">mysql_secure_installation</pre>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					<em style="box-sizing:border-box;">Enter current password for root (enter for none):</em><br style="box-sizing:border-box;" />
解释：输入当前 root 用户密码，默认为空，直接回车。<br style="box-sizing:border-box;" />
<em style="box-sizing:border-box;">Set root password? [Y/n] &nbsp;y</em><br style="box-sizing:border-box;" />
解释：要设置 root 密码吗？输入 y 表示愿意。<br style="box-sizing:border-box;" />
<em style="box-sizing:border-box;">Remove anonymous users? [Y/n] &nbsp;y</em><br style="box-sizing:border-box;" />
解释：要移除掉匿名用户吗？输入 y 表示愿意。<br style="box-sizing:border-box;" />
<em style="box-sizing:border-box;">Disallow root login remotely? [Y/n] &nbsp;y</em><br style="box-sizing:border-box;" />
解释：不想让 root 远程登陆吗？输入 y 表示愿意。<br style="box-sizing:border-box;" />
<em style="box-sizing:border-box;">Remove test database and access to it? [Y/n] &nbsp;y</em><br style="box-sizing:border-box;" />
解释：要去掉 test 数据库吗？输入 y 表示愿意。<br style="box-sizing:border-box;" />
<em style="box-sizing:border-box;">Reload privilege tables now? [Y/n] &nbsp;y</em><br style="box-sizing:border-box;" />
解释：想要重新加载权限吗？输入 y 表示愿意。
				</p>
				<h2 style="font-family:inherit;margin:30px 0px;padding:0px;font-weight:300;box-sizing:border-box;color:inherit;font-size:31.5px;line-height:40px;">
					<a name="t24"></a>
				</h2>
				<h2 style="font-family:inherit;margin:30px 0px;padding:0px;font-weight:300;box-sizing:border-box;color:inherit;font-size:31.5px;line-height:40px;">
					<a name="t25"></a>目录与文件的权限问题
				</h2>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					网站上面有些目录或文件需要有写入权限，这样你得为这些目录和文件分配合适的权限，一般可以把它们的拥有者设置成 php-fpm 使用的用户，查看一下谁在运行 php-fpm 这个服务：
				</p>
<pre class="hljs nginx" name="code" style="margin-top:0px;margin-bottom:30px;padding:16px;box-sizing:border-box;color:#ABB2BF;background:#282C34;font-family:Monaco, Menlo, Consolas, &quot;font-size:15px;line-height:1.5;white-space:pre-wrap;"><span class="hljs-attribute" style="margin:0px;padding:0px;box-sizing:border-box;color:#98C379;">sudo</span> ps aux|grep php</pre>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					修改所使用的用户，php-fpm 的配置文件是：<em style="box-sizing:border-box;">/etc/php-fpm.conf</em>，还有在&nbsp;<em style="box-sizing:border-box;">/etc/php-fpm.d/*</em>&nbsp;这个目录里的所有文件都是 php-fpm 的配置文件。默认这个目录里有一个&nbsp;<em style="box-sizing:border-box;"><a href="http://www.conf/" target="_blank" style="color:#333333;outline:0px;margin:0px;padding:0px 0px 2px;box-sizing:border-box;text-decoration-line:none;border-bottom:1px dotted #333333;">www.conf</a></em>&nbsp;，你可以编辑这个文件来修改 php-fpm 所使用的用户名称。使用&nbsp;<em style="box-sizing:border-box;">vim</em>&nbsp;命令：
				</p>
<pre class="hljs nginx" name="code" style="margin-top:0px;margin-bottom:30px;padding:16px;box-sizing:border-box;color:#ABB2BF;background:#282C34;font-family:Monaco, Menlo, Consolas, &quot;font-size:15px;line-height:1.5;white-space:pre-wrap;"><span class="hljs-attribute" style="margin:0px;padding:0px;box-sizing:border-box;color:#98C379;">vim</span> /etc/php-fpm.d/www.conf</pre>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					打开文件以后你可以搜索下关键词&nbsp;<em style="box-sizing:border-box;">user</em>&nbsp;，输入&nbsp;<em style="box-sizing:border-box;">:/user</em>&nbsp;&nbsp;，会搜索到结果，按小&nbsp;<em style="box-sizing:border-box;">n</em>&nbsp;可以继续向下查找，按大&nbsp;<em style="box-sizing:border-box;">N</em>&nbsp;可以向上查找。直到你看到：
				</p>
<pre class="hljs nginx" name="code" style="margin-top:0px;margin-bottom:30px;padding:16px;box-sizing:border-box;color:#ABB2BF;background:#282C34;font-family:Monaco, Menlo, Consolas, &quot;font-size:15px;line-height:1.5;white-space:pre-wrap;"><span class="hljs-attribute" style="margin:0px;padding:0px;box-sizing:border-box;color:#98C379;">user</span> = php-fpm</pre>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					这个 php-fpm 就是运行 PHP-FPM 的用户的名字，你看到的也可能是其它的名字，这不重要。你只要知道这个用户是谁，在哪里可以修改这个用户就行了。在遇到目录写入权限的问题，比如不能正常上传网站的文件，你可以把保存上传文件的那个目录的拥有者修改成运行 PHP-FPM 的用户就可以了。
				</p>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					修改目录的拥有者可以使用这样的命名：
				</p>
<pre class="hljs nginx" name="code" style="margin-top:0px;margin-bottom:30px;padding:16px;box-sizing:border-box;color:#ABB2BF;background:#282C34;font-family:Monaco, Menlo, Consolas, &quot;font-size:15px;line-height:1.5;white-space:pre-wrap;"><span class="hljs-attribute" style="margin:0px;padding:0px;box-sizing:border-box;color:#98C379;">sudo</span> chown -R 用户名 目录</pre>
				<p style="margin-top:0px;margin-bottom:20px;padding:0px;box-sizing:border-box;font-size:17px;color:#4F4F4F;line-height:1.7;min-height:26px;text-align:justify;font-family:&quot;">
					这样就会把指定的目录的拥有者修改成指定的用户了。也就是如果你把目录的拥有者修改成运行 PHP-FPM 的那个用户，那么在网站上再去上传文件就不会有权限的问题了，因为目录的拥有者一般都会拥有可以写入的权限。
				</p>
			</div>
		</div>
	</div>
</p>