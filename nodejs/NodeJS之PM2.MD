<h1 class="postTitle">
	<a id="cb_post_title_url" class="postTitle2" href="http://www.cnblogs.com/xiaopohou/articles/5690263.html">NodeJS之PM2</a> 
</h1>
<div class="clear">
</div>
<div class="postBody">
	<div id="cnblogs_post_body">
		<p>
			最近把DoraCMS迁移到的linux上，由于node使用npm start开启服务，当ssh关闭，进程就断了，另外我在服务器上挂了3个node服务，管理起来非常不方便，于是朋友介绍了pm2，目前我只用到了一小部分功能，已经感觉很强大了。
		</p>
		<p>
			<br />
		</p>
		<p>
			pm2 是一个带有负载均衡功能的Node应用的进程管理器. 
当你要把你的独立代码利用全部的服务器上的所有CPU，并保证进程永远都活着，0秒的重载， 
PM2是非常不错的选择的。它非常适合IaaS结构，但不要把它用于PaaS方案（随后将开发Paas的解决方案）.
		</p>
		<p>
			&nbsp;
		</p>
		<p>
			主要特性：
		</p>
		<p>
			&nbsp;
		</p>
		<p>
			内建负载均衡（使用Node cluster 集群模块）
		</p>
		<p>
			后台运行
		</p>
		<p>
			0秒停机重载，我理解大概意思是维护升级的时候不需要停机.
		</p>
		<p>
			具有Ubuntu和CentOS 的启动脚本
		</p>
		<p>
			停止不稳定的进程（避免无限循环）
		</p>
		<p>
			控制台检测
		</p>
		<p>
			提供 HTTP API
		</p>
		<p>
			远程控制和实时的接口API ( Nodejs 模块,允许和PM2进程管理器交互 )
		</p>
		<p>
			&nbsp;
		</p>
		<p>
			测试过Nodejs v0.11 v0.10 v0.8版本，兼容CoffeeScript,基于Linux 和MacOS.
		</p>
		<p>
			&nbsp;
		</p>
		<p>
			安装
		</p>
		<div>
			<div id="highlighter_817946" class="syntaxhighlighter js">
				<table cellspacing="0" cellpadding="0" border="0" class="ke-zeroborder">
					<tbody>
						<tr>
							<td class="gutter">
								<div class="line number1 index0 alt2">
									1
								</div>
							</td>
							<td class="code">
								<div class="container">
									<div class="line number1 index0 alt2">
										<code class="js plain">npm&nbsp;install&nbsp;-g&nbsp;pm2</code>
									</div>
								</div>
							</td>
						</tr>
					</tbody>
				</table>
			</div>
		</div>
		<p>
			&nbsp;
		</p>
		<p>
			用法
		</p>
		<div>
			<div id="highlighter_582573" class="syntaxhighlighter js">
				<table cellspacing="0" cellpadding="0" border="0" class="ke-zeroborder">
					<tbody>
						<tr>
							<td class="gutter">
								<div class="line number1 index0 alt2">
									1
								</div>
								<div class="line number2 index1 alt1">
									2
								</div>
								<div class="line number3 index2 alt2">
									3
								</div>
								<div class="line number4 index3 alt1">
									4
								</div>
								<div class="line number5 index4 alt2">
									5
								</div>
								<div class="line number6 index5 alt1">
									6
								</div>
								<div class="line number7 index6 alt2">
									7
								</div>
								<div class="line number8 index7 alt1">
									8
								</div>
								<div class="line number9 index8 alt2">
									9
								</div>
								<div class="line number10 index9 alt1">
									10
								</div>
								<div class="line number11 index10 alt2">
									11
								</div>
								<div class="line number12 index11 alt1">
									12
								</div>
								<div class="line number13 index12 alt2">
									13
								</div>
								<div class="line number14 index13 alt1">
									14
								</div>
								<div class="line number15 index14 alt2">
									15
								</div>
								<div class="line number16 index15 alt1">
									16
								</div>
								<div class="line number17 index16 alt2">
									17
								</div>
							</td>
							<td class="code">
								<div class="container">
									<div class="line number1 index0 alt2">
										<code class="js plain">$&nbsp;npm&nbsp;install&nbsp;pm2&nbsp;-g&nbsp;</code><code class="js preprocessor">#&nbsp;命令行安装&nbsp;pm2</code>
									</div>
									<div class="line number2 index1 alt1">
										<code class="js plain">$&nbsp;pm2&nbsp;start&nbsp;app.js&nbsp;-i&nbsp;4&nbsp;</code><code class="js preprocessor">#后台运行pm2，启动4个app.js</code>
									</div>
									<div class="line number3 index2 alt2">
										<code class="js spaces">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</code><code class="js preprocessor">#&nbsp;也可以把'max'&nbsp;参数传递给&nbsp;start</code>
									</div>
									<div class="line number4 index3 alt1">
										<code class="js spaces">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</code><code class="js preprocessor">#&nbsp;正确的进程数目依赖于Cpu的核心数目</code>
									</div>
									<div class="line number5 index4 alt2">
										<code class="js plain">$&nbsp;pm2&nbsp;start&nbsp;app.js&nbsp;--name&nbsp;my-api&nbsp;</code><code class="js preprocessor">#&nbsp;命名进程</code>
									</div>
									<div class="line number6 index5 alt1">
										<code class="js plain">$&nbsp;pm2&nbsp;list&nbsp;</code><code class="js preprocessor">#&nbsp;显示所有进程状态</code>
									</div>
									<div class="line number7 index6 alt2">
										<code class="js plain">$&nbsp;pm2&nbsp;monit&nbsp;</code><code class="js preprocessor">#&nbsp;监视所有进程</code>
									</div>
									<div class="line number8 index7 alt1">
										<code class="js plain">$&nbsp;pm2&nbsp;logs&nbsp;</code><code class="js preprocessor">#&nbsp;显示所有进程日志</code>
									</div>
									<div class="line number9 index8 alt2">
										<code class="js plain">$&nbsp;pm2&nbsp;stop&nbsp;all&nbsp;</code><code class="js preprocessor">#&nbsp;停止所有进程</code>
									</div>
									<div class="line number10 index9 alt1">
										<code class="js plain">$&nbsp;pm2&nbsp;restart&nbsp;all&nbsp;</code><code class="js preprocessor">#&nbsp;重启所有进程</code>
									</div>
									<div class="line number11 index10 alt2">
										<code class="js plain">$&nbsp;pm2&nbsp;reload&nbsp;all&nbsp;</code><code class="js preprocessor">#&nbsp;0秒停机重载进程&nbsp;(用于&nbsp;NETWORKED&nbsp;进程)</code>
									</div>
									<div class="line number12 index11 alt1">
										<code class="js plain">$&nbsp;pm2&nbsp;stop&nbsp;0&nbsp;</code><code class="js preprocessor">#&nbsp;停止指定的进程</code>
									</div>
									<div class="line number13 index12 alt2">
										<code class="js plain">$&nbsp;pm2&nbsp;restart&nbsp;0&nbsp;</code><code class="js preprocessor">#&nbsp;重启指定的进程</code>
									</div>
									<div class="line number14 index13 alt1">
										<code class="js plain">$&nbsp;pm2&nbsp;startup&nbsp;</code><code class="js preprocessor">#&nbsp;产生&nbsp;init&nbsp;脚本&nbsp;保持进程活着</code>
									</div>
									<div class="line number15 index14 alt2">
										<code class="js plain">$&nbsp;pm2&nbsp;web&nbsp;</code><code class="js preprocessor">#&nbsp;运行健壮的&nbsp;computer&nbsp;API&nbsp;endpoint&nbsp;(http://localhost:9615)</code>
									</div>
									<div class="line number16 index15 alt1">
										<code class="js plain">$&nbsp;pm2&nbsp;</code><code class="js keyword">delete</code>&nbsp;<code class="js plain">0&nbsp;</code><code class="js preprocessor">#&nbsp;杀死指定的进程</code>
									</div>
									<div class="line number17 index16 alt2">
										<code class="js plain">$&nbsp;pm2&nbsp;</code><code class="js keyword">delete</code>&nbsp;<code class="js plain">all&nbsp;</code><code class="js preprocessor">#&nbsp;杀死全部进程</code>
									</div>
								</div>
							</td>
						</tr>
					</tbody>
				</table>
			</div>
		</div>
		<p>
			&nbsp;
		</p>
		<p>
			运行进程的不同方式：
		</p>
		<div>
			<div id="highlighter_219304" class="syntaxhighlighter js">
				<table cellspacing="0" cellpadding="0" border="0" class="ke-zeroborder">
					<tbody>
						<tr>
							<td class="gutter">
								<div class="line number1 index0 alt2">
									1
								</div>
								<div class="line number2 index1 alt1">
									2
								</div>
								<div class="line number3 index2 alt2">
									3
								</div>
								<div class="line number4 index3 alt1">
									4
								</div>
								<div class="line number5 index4 alt2">
									5
								</div>
								<div class="line number6 index5 alt1">
									6
								</div>
								<div class="line number7 index6 alt2">
									7
								</div>
								<div class="line number8 index7 alt1">
									8
								</div>
								<div class="line number9 index8 alt2">
									9
								</div>
							</td>
							<td class="code">
								<div class="container">
									<div class="line number1 index0 alt2">
										<code class="js plain">$&nbsp;pm2&nbsp;start&nbsp;app.js&nbsp;-i&nbsp;max&nbsp;</code><code class="js preprocessor">#&nbsp;根据有效CPU数目启动最大进程数目</code>
									</div>
									<div class="line number2 index1 alt1">
										<code class="js plain">$&nbsp;pm2&nbsp;start&nbsp;app.js&nbsp;-i&nbsp;3&nbsp;</code><code class="js preprocessor">#&nbsp;启动3个进程</code>
									</div>
									<div class="line number3 index2 alt2">
										<code class="js plain">$&nbsp;pm2&nbsp;start&nbsp;app.js&nbsp;-x&nbsp;</code><code class="js preprocessor">#用fork模式启动&nbsp;app.js&nbsp;而不是使用&nbsp;cluster</code>
									</div>
									<div class="line number4 index3 alt1">
										<code class="js plain">$&nbsp;pm2&nbsp;start&nbsp;app.js&nbsp;-x&nbsp;--&nbsp;-a&nbsp;23&nbsp;</code><code class="js preprocessor">#&nbsp;用fork模式启动&nbsp;app.js&nbsp;并且传递参数&nbsp;(-a&nbsp;23)</code>
									</div>
									<div class="line number5 index4 alt2">
										<code class="js plain">$&nbsp;pm2&nbsp;start&nbsp;app.js&nbsp;--name&nbsp;serverone&nbsp;</code><code class="js preprocessor">#&nbsp;启动一个进程并把它命名为&nbsp;serverone</code>
									</div>
									<div class="line number6 index5 alt1">
										<code class="js plain">$&nbsp;pm2&nbsp;stop&nbsp;serverone&nbsp;</code><code class="js preprocessor">#&nbsp;停止&nbsp;serverone&nbsp;进程</code>
									</div>
									<div class="line number7 index6 alt2">
										<code class="js plain">$&nbsp;pm2&nbsp;start&nbsp;app.json&nbsp;</code><code class="js preprocessor">#&nbsp;启动进程,&nbsp;在&nbsp;app.json里设置选项</code>
									</div>
									<div class="line number8 index7 alt1">
										<code class="js plain">$&nbsp;pm2&nbsp;start&nbsp;app.js&nbsp;-i&nbsp;max&nbsp;--&nbsp;-a&nbsp;23&nbsp;</code><code class="js preprocessor">#在--之后给&nbsp;app.js&nbsp;传递参数</code>
									</div>
									<div class="line number9 index8 alt2">
										<code class="js plain">$&nbsp;pm2&nbsp;start&nbsp;app.js&nbsp;-i&nbsp;max&nbsp;-e&nbsp;err.log&nbsp;-o&nbsp;out.log&nbsp;</code><code class="js preprocessor">#&nbsp;启动&nbsp;并&nbsp;生成一个配置文件</code>
									</div>
								</div>
							</td>
						</tr>
					</tbody>
				</table>
			</div>
		</div>
		<p>
			你也可以执行用其他语言编写的app ( fork 模式):
		</p>
		<div>
			<div id="highlighter_925690" class="syntaxhighlighter js">
				<table cellspacing="0" cellpadding="0" border="0" class="ke-zeroborder">
					<tbody>
						<tr>
							<td class="gutter">
								<div class="line number1 index0 alt2">
									1
								</div>
								<div class="line number2 index1 alt1">
									2
								</div>
							</td>
							<td class="code">
								<div class="container">
									<div class="line number1 index0 alt2">
										<code class="js plain">$&nbsp;pm2&nbsp;start&nbsp;my-bash-script.sh&nbsp;-x&nbsp;--interpreter&nbsp;bash</code>
									</div>
									<div class="line number2 index1 alt1">
										<code class="js plain">$&nbsp;pm2&nbsp;start&nbsp;my-python-script.py&nbsp;-x&nbsp;--interpreter&nbsp;python</code>
									</div>
								</div>
							</td>
						</tr>
					</tbody>
				</table>
			</div>
		</div>
		<p>
			&nbsp;
		</p>
		<p>
			如何用pm2启动 DoraCMS:
		</p>
		<p>
			进入源码根目录下执行：
		</p>
		<div>
			<div id="highlighter_211821" class="syntaxhighlighter js">
				<table cellspacing="0" cellpadding="0" border="0" class="ke-zeroborder">
					<tbody>
						<tr>
							<td class="gutter">
								<div class="line number1 index0 alt2">
									1
								</div>
							</td>
							<td class="code">
								<div class="container">
									<div class="line number1 index0 alt2">
										<code class="js plain">pm2&nbsp;start&nbsp;bin/www</code>
									</div>
								</div>
							</td>
						</tr>
					</tbody>
				</table>
			</div>
		</div>
		<p>
			可以使用 pm2 list 查看当前所有的进程列表。更多关于pm2的api可以查看官方文档&nbsp;https://github.com/Unitech/pm2
		</p>
		<p>
			传送门：http://www.html-js.cn/details/NkZMo0GDl.html
		</p>
	</div>
</div>