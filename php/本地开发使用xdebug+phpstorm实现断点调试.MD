<blockquote>
	<p>
		一直以来，我调试PHP脚本都是直接在脚本中 die 或 exit 实现断点调试，很不方便，今天phpstorm+xdebug的组合给了我一个惊喜。
	</p>
</blockquote>
<p>
	我们一般是通过浏览器访问web项目，脚本的执行不受ide控制，所以一般情况下无法在ide中实现断点，但是有了xdebug，一切变得不一样了。
</p>
<p>
	当然，我们首先给php安装xdebug扩展，xdebug 
有个远程调试的功能，可以指定一个远程ip地址和端口，当我们在浏览器中访问某个脚本的时候，可以通过某种方法告诉xdebug我们需要调试，然后xdebug会将调试信息发送给远程地址，这个远程地址呢，就是我们phpstorm来实现的，它将接收xdebug吐出来的信息，并在ide中反馈给我们，我们就可以实现断点调试了。
</p>
<p>
	那么，实现这个功能分三步走：
</p>
<p>
	1.安装&amp;配置xdebug
</p>
<p>
	安装扩展过程就略了，简单贴一下我的xdebug配置参数，在php.ini中：
</p>
<pre class="hljs bash"><code>[xdebug]
zend_extension=<span class="hljs-string">"/usr/local/Cellar/php54-xdebug/2.2.5/xdebug.so"</span> xdebug.remote_<span class="hljs-built_in">enable</span> =<span class="hljs-number">1</span> xdebug.remote_handler = <span class="hljs-string">"dbgp"</span> xdebug.remote_host = <span class="hljs-string">"localhost"</span> xdebug.remote_mode = <span class="hljs-string">"req"</span> xdebug.remote_port = <span class="hljs-number">9001</span> xdebug.idekey=<span class="hljs-string">"PHPSTORM"</span> </code></pre>
<p>
	注意 <code class="hljs">xdebug.remote_host</code> 和 <code class="hljs">xdebug.remote_port</code> 两个参数，这与phpstorm有关，先留个心。
</p>
<p>
	之后重启下webserver以使php.ini生效。
</p>
<p>
	2.phpstorm配置
</p>
<p>
	在 <code class="hljs nginx"><span class="hljs-title">project</span> settings - PHP - Debug</code> 中，有一个 <code class="hljs">xdebug</code> 的栏，其中有一个 <code class="hljs nginx"><span class="hljs-title">debug</span> port</code> ，我们设置为 <code class="hljs">9001</code> 和上面 <code class="hljs">xdebug.remote_port</code> 保持一致，其他不变，保存配置。
</p>
<p>
	然后点击phpstorm菜单栏 <code class="hljs nginx"><span class="hljs-title">run</span> - start listening for php <span class="hljs-built_in">debug</span> connections</code> ，这时候php会后台创建一个服务来监听 <code class="hljs css"><span class="hljs-tag">localhost</span><span class="hljs-pseudo">:9001</span></code> 这个地址，对应 xdebug 配置的。
</p>
<p>
	3.浏览器触发调试
</p>
<p>
	万事俱备只欠东风，现在打开一个php脚本是不会产生调试信息的，xdebug不会调试所有的请求，必须指定一个标识，xdebug才能识别。
</p>
<p>
	现在，打开 https://www.jetbrains.com/phpstorm/marklets/ 这个地址，点击左侧的 
generate 按钮，然后页面下方会出现一系列链接，比如 "start debugger" 
，查看它的href属性会发现是一个js代码，复制它，然后到你要调试的页面，在f12控制台中执行它，它会在当前域下生成一个cookie，当请求url时，xdebug就能根据这个cookie知道你要debug，随即向 <code class="hljs css"><span class="hljs-tag">localhost</span><span class="hljs-pseudo">:9001</span></code> 吐数据，phpstorm接收到以后再结合自身的断点调试工具...
</p>
<p>
	但是这样太麻烦，如果你用的是chrome那可以下载一个插件，名字叫 "Xdebug helper" 你可以在插件市场搜索到并安装它，安装好以后在扩展管理中心找到它，并点击 "选项" 链接，进入插件的配置页面，其中 <code class="hljs nginx"><span class="hljs-title">IDE</span> Key</code> 选择 "phpstorm" ,然后在 <code class="hljs nginx"><span class="hljs-title">Domain</span> filter</code> 中将你的项目域名添加进去。这样，当你访问你的项目url时，会在地址栏右侧出现一个小虫子，你可以点击小虫子开启debug，很方便吧。
</p>
<p>
	这样，你在phpstorm中对应url的脚本设置一个断点，然后浏览器中开启debug,刷新页面，phpstorm会自动弹出一个确认框，让你确认是否调试指定的脚本。接着你就可以快乐的使用断点调试功能了。
</p>