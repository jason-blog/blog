<h1 class="postTitle">
	<a id="cb_post_title_url" class="postTitle2" href="http://www.cnblogs.com/xuxn/archive/2011/02/14/build-simple-web-server-with-python.html">用Python建立最简单的web服务器</a> 
</h1>
<div id="cnblogs_post_body">
	<p>
		利用Python自带的包可以建立简单的web服务器。在DOS里cd到准备做服务器根目录的路径下，输入命令：
	</p>
	<ul>
		<li>
			python -m <span style="color:#0000ff;">Web服务器模块</span> [端口号，默认8000]
		</li>
	</ul>
例如：<br />
	<ul>
		<li>
			<span style="color:#ff0000;">python -m SimpleHTTPServer 8080</span>
		</li>
	</ul>
	<p>
		然后就可以在浏览器中输入
	</p>
	<ul>
		<li>
			http://localhost:端口号/路径
		</li>
	</ul>
来访问服务器资源。&nbsp;<br />
例如：<br />
	<ul>
		<li>
			<span style="color:#ff0000;">http://localhost:8080/index.htm<span style="color:#000000;">（当然index.htm文件得自己创建）</span></span>
		</li>
	</ul>
其他机器也可以通过<span style="color:#ff0000;">服务器的IP地址</span>来访问。<br />
<br />
	<p>
		这里的“<span style="color:#0000ff;">Web服务器模块</span>”有如下三种：
	</p>
	<ul>
		<li>
			BaseHTTPServer: 提供基本的Web服务和处理器类，分别是HTTPServer和BaseHTTPRequestHandler。
		</li>
		<li>
			SimpleHTTPServer: 包含执行GET和HEAD请求的SimpleHTTPRequestHandler类。
		</li>
		<li>
			CGIHTTPServer: 包含处理POST请求和执行CGIHTTPRequestHandler类。
		</li>
	</ul>
</div>