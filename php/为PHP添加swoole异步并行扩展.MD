<h1>
	1. 确认安装环境
</h1>
<div class="article_body" id="nei">
	<div class="code-pre">
		<ul>
			<li>
				仅支持Linux操作系统，核心代码兼容FreeBSD，需要调整某些编译的参数和细节才能通过
			</li>
			<li>
				Linux内核版本2.3.32以上
			</li>
			<li>
				PHP5.3.10以上版本
			</li>
			<li>
				gcc4.4以上版本。核心代码兼容clang，需要关闭CPU亲和设置特性
			</li>
			<li>
				cmake2.4+,编译为libswoole.so作为C/C++库时，需要使用cmake
			</li>
		</ul>
	</div>
	<p>
		2. 安装与配置
	</p>
	<p>
		2. 1安装swoole：可pecl直接在线安装，或下载  releases版本的swoole编译安装
	</p>
	<p>
		2.11 pecl安装swoole扩展
	</p>
	<p>
		pecl不可用的请确认php安装目录的bin目录已加入系统变量
	</p>
<pre class="bash"><span class="comment"># pecl install swoole</span></pre>
	<p>
		2.12编译安装swoole扩展
	</p>
	<p>
		从此处下载： <a href="http://pecl.php.net/package/swoole" rel="nofollow,noindex" target="_blank">http://pecl.php.net/package/swoole</a> 
	</p>
<pre class="bash"><span class="comment"># cd swoole</span> <span class="comment"># phpize</span> <span class="comment"># ./configure</span> --WITH-PHP-CONFIG=php-config <span class="comment"># make &amp;&amp; make install </span></pre>
	<p>
		2.2配置php.ini
	</p>
	<p>
		phpinfo()确认Configuration File (php.ini) Path
	</p>
	<p>
		添加：
	</p>
<pre class="ini"><span class="setting">extension=<span class="value">swoole.so</span></span></pre>
	<p>
		重启Apache查看php扩展库
	</p>
<pre class="bash"><span class="comment"># service httpd restart</span> <span class="comment"># php -m</span></pre>
	<p>
		确认swoole已添加
	</p>
	<p>
		官方文档： <a href="http://wiki.swoole.com/wiki/index/prid-1" rel="nofollow,noindex" target="_blank">http://wiki.swoole.com/wiki/index/prid-1</a> 
	</p>
	<p>
		3.测试
	</p>
	<p>
		server.php:
	</p>
<pre class="prettyprint php"><span class="preprocessor">&lt;?php</span> <span class="indent"> </span><span class="variable">$serv</span> = <span class="keyword">new</span> swoole_server(<span class="string">"0.0.0.0"</span>, <span class="number">9501</span>); <span class="indent"> </span><span class="variable">$serv</span>-&gt;on(<span class="string">'connect'</span>, <span class="function"><span class="keyword">function</span> <span class="params">(<span class="variable">$serv</span>, <span class="variable">$fd</span>)</span>{</span> <span class="indent"> </span><span class="indent"> </span><span class="keyword">echo</span> <span class="string">"Client:Connect.\n"</span>; <span class="indent"> </span>}); <span class="indent"> </span><span class="variable">$serv</span>-&gt;on(<span class="string">'receive'</span>, <span class="function"><span class="keyword">function</span> <span class="params">(<span class="variable">$serv</span>, <span class="variable">$fd</span>, <span class="variable">$from_id</span>, <span class="variable">$data</span>)</span> {</span> <span class="indent"> </span><span class="indent"> </span><span class="variable">$serv</span>-&gt;send(<span class="variable">$fd</span>, <span class="string">'Swoole: '</span>.<span class="variable">$data</span>); <span class="indent"> </span>}); <span class="indent"> </span><span class="variable">$serv</span>-&gt;on(<span class="string">'close'</span>, <span class="function"><span class="keyword">function</span> <span class="params">(<span class="variable">$serv</span>, <span class="variable">$fd</span>)</span> {</span> <span class="indent"> </span><span class="indent"> </span><span class="keyword">echo</span> <span class="string">"Client: Close.\n"</span>; <span class="indent"> </span>}); <span class="indent"> </span><span class="variable">$serv</span>-&gt;start(); <span class="preprocessor">?&gt;</span></pre>
	<p>
		client.php:
	</p>
<pre class="prettyprint php"><span class="preprocessor">&lt;?php</span> <span class="indent"> </span><span class="variable">$client</span> = <span class="keyword">new</span> swoole_client(SWOOLE_SOCK_TCP, SWOOLE_SOCK_ASYNC); <span class="indent"> </span><span class="variable">$client</span>-&gt;on(<span class="string">"connect"</span>, function(<span class="variable">$cli</span>) { <span class="indent"> </span><span class="indent"> </span><span class="variable">$cli</span>-&gt;send(<span class="string">"hello world\n"</span>); <span class="indent"> </span>}); <span class="indent"> </span><span class="variable">$client</span>-&gt;on(<span class="string">"receive"</span>, function(<span class="variable">$cli</span>, <span class="variable">$data</span>){ <span class="indent"> </span><span class="indent"> </span><span class="keyword">echo</span> <span class="string">"Receive: $data\n"</span>; <span class="indent"> </span>}); <span class="indent"> </span><span class="variable">$client</span>-&gt;on(<span class="string">"error"</span>, function(<span class="variable">$cli</span>){ <span class="indent"> </span><span class="indent"> </span><span class="keyword">echo</span> <span class="string">"connect fail\n"</span>; <span class="indent"> </span>}); <span class="indent"> </span><span class="variable">$client</span>-&gt;on(<span class="string">"close"</span>, function(<span class="variable">$cli</span>){ <span class="indent"> </span><span class="indent"> </span><span class="keyword">echo</span> <span class="string">"close\n"</span>; <span class="indent"> </span>}); <span class="indent"> </span><span class="variable">$client</span>-&gt;connect(<span class="string">'127.0.0.1'</span>, <span class="number">9501</span>, <span class="number">0.5</span>); <span class="preprocessor">?&gt;</span></pre>
	<p>
		Test：
	</p>
	<p>
		<em> &nbsp; </em> 测试Server： <em> <br />
</em> 
	</p>
	<p>
		&nbsp;&nbsp;&nbsp; <img src="http://img0.tuicool.com/IvQFFb2.png%21web" class="alignCenter" /> 
	</p>
	<p>
		&nbsp;&nbsp;&nbsp;&nbsp;测试Client：
	</p>
	<p>
		&nbsp;&nbsp;&nbsp; <img src="http://img1.tuicool.com/uQbQNjB.png%21web" class="alignCenter" /> 
	</p>
	<p>
		End.
	</p>
</div>