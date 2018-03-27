<h2>
	1. 安装Shadowsocks
</h2>
<p>
	终端下安装Shadowsocks只需要两步：
</p>
<p>
	Debian / Ubuntu:
</p>
<pre class="hljs sql"><code class="sql">apt-get <span class="hljs-operator"><span class="hljs-keyword">install</span> python-pip
pip <span class="hljs-keyword">install</span> shadowsocks</span></code></pre>
<p>
	编辑文件<code>vim /etc/shadowsocks.json</code>，填写代理信息：
</p>
<pre class="hljs json"><code class="json">{
    "<span class="hljs-attribute">server</span>":<span class="hljs-value"><span class="hljs-string">"my_server_ip"</span></span>,
    "<span class="hljs-attribute">server_port</span>":<span class="hljs-value"><span class="hljs-number">8388</span></span>,
    "<span class="hljs-attribute">local_address</span>": <span class="hljs-value"><span class="hljs-string">"127.0.0.1"</span></span>,
    "<span class="hljs-attribute">local_port</span>":<span class="hljs-value"><span class="hljs-number">1080</span></span>,
    "<span class="hljs-attribute">password</span>":<span class="hljs-value"><span class="hljs-string">"mypassword"</span></span>,
    "<span class="hljs-attribute">timeout</span>":<span class="hljs-value"><span class="hljs-number">300</span></span>,
    "<span class="hljs-attribute">method</span>":<span class="hljs-value"><span class="hljs-string">"aes-256-cfb"</span></span>,
    "<span class="hljs-attribute">fast_open</span>": <span class="hljs-value"><span class="hljs-literal">false</span> </span>}</code></pre>
<h4>
	1.1 后台运行Shadowsocks
</h4>
<p>
	启动：<code>sslocal -c /etc/shadowsocks.json -d start</code><br />
停止：<code>sslocal -c /etc/shadowsocks.json -d stop</code>
</p>
<h2>
	2. socks5转http
</h2>
<blockquote>
	<p>
		Shadowsocks使用socks5协议，而终端很多工具目前只支持http和https等协议，所以我们为终端设置Shadowsocks的思路就是将socks5协议转换成http协议，然后为终端设置即可。
	</p>
</blockquote>
<p>
	安装Polipo（Debian / Ubuntu）：
</p>
<pre class="hljs cs"><code class="cs">sudo apt-<span class="hljs-keyword">get</span> install polipo</code></pre>
<p>
	如下打开配置文件：
</p>
<pre class="hljs undefined"><code>sudo vim /etc/polipo/config</code></pre>
<p>
	设置ParentProxy为Shadowsocks，通常情况下本机Shadowsocks的地址如下：
</p>
<pre class="hljs bash"><code class="bash"><span class="hljs-comment"># Uncomment this if you want to use a parent SOCKS </span> proxy:socksParentProxy = <span class="hljs-string">"localhost:1080"</span> socksProxyType = socks5</code></pre>
<p>
	设置日志输出文件：
</p>
<pre class="hljs bash"><code class="bash"><span class="hljs-built_in">log</span>File=/var/<span class="hljs-built_in">log</span>/polipologLevel=<span class="hljs-number">4</span></code></pre>
<p>
	现在，你可以在某个命令前面加上<code>http_proxy=http://localhost:8123</code>设置代理。
</p>
<blockquote>
	<p>
		注：8123是Polipo的默认端口，如有需要，可以修改成其他有效端口。
	</p>
</blockquote>
<h4>
	2.1 当前会话设置全局代理
</h4>
<p>
	临时使用代理输入<code>export http_proxy=http://localhost:8123</code>回车即可。<br />
如果想撤销当前会话的http_proxy代理，使用<code>unset http_proxy</code>即可。
</p>
<blockquote>
	<p>
		设置更长久的代理可以把下面这句加到<code>～/.bashrc</code>文件。
	</p>
<pre class="hljs objectivec"><code class="objectivec"><span class="hljs-keyword">export</span> http_proxy=http:<span class="hljs-comment">//localhost:8123</span></code></pre>
</blockquote>
<h4>
	2.2 验证代理是否成功
</h4>
<p>
	没有挂代理的时候：
</p>
<pre class="hljs cpp"><code class="cpp">$ curl ip.gs
当前 IP：<span class="hljs-number">125.39</span><span class="hljs-number">.112</span><span class="hljs-number">.14</span> 来自：中国天津天津 联通</code></pre>
<p>
	挂代理后：
</p>
<pre class="hljs cpp"><code class="cpp">$ <span class="hljs-keyword">export</span> http_proxy=http:<span class="hljs-comment">//localhost:8123</span> $ curl ip.gs
当前 IP：<span class="hljs-number">210.140</span><span class="hljs-number">.193</span><span class="hljs-number">.128</span> 来自：日本日本</code></pre>
<p>
	取消代理后：
</p>
<pre class="hljs cpp"><code class="cpp">$ unset http_proxy
$ curl ip.gs
当前 IP：<span class="hljs-number">125.39</span><span class="hljs-number">.112</span><span class="hljs-number">.14</span> 来自：中国天津天津 联通</code></pre>
<h4>
	2.3 设置Git代理
</h4>
<pre class="hljs php"><code class="php">git <span class="hljs-keyword">clone</span> https:<span class="hljs-comment">//repo/path/ --config http.proxy=localhost:8123</span></code></pre>
<p>
	或者使用socks5：
</p>
<pre class="hljs scala"><code class="scala">git config --global http.proxy <span class="hljs-symbol">'socks5</span>:<span class="hljs-comment">//127.0.0.1:1080' </span> git config --global https.proxy <span class="hljs-symbol">'socks5</span>:<span class="hljs-comment">//127.0.0.1:1080'</span></code></pre>
<p>
	或者使用Polipo：
</p>
<pre class="hljs scala"><code class="scala">git config --global http.proxy <span class="hljs-symbol">'http</span>:<span class="hljs-comment">//127.0.0.1:8123' </span> git config --global https.proxy <span class="hljs-symbol">'https</span>:<span class="hljs-comment">//127.0.0.1:8123'</span></code></pre>
<h2>
	3. Proxychains
</h2>
<blockquote>
	<p>
		有了Polipo，为什么还要Proxychains呢？因为有时候全局代理反而会带来一些麻烦，使用Proxychains可以根据情况选择是否挂代理。
	</p>
</blockquote>
<h4>
	3.1 安装Proxychains
</h4>
<pre class="hljs bash"><code class="bash">git <span class="hljs-built_in">clone</span> https://github.com/rofl0r/proxychains-ng.git <span class="hljs-built_in">cd</span> proxychains-ng
./configure
make &amp;&amp; make install
cp ./src/proxychains.conf /etc/proxychains.conf <span class="hljs-built_in">cd</span> .. &amp;&amp; rm -rf proxychains-ng</code></pre>
<h4>
	3.2 编辑proxychains配置
</h4>
<pre class="hljs undefined"><code>vim /etc/proxychains.conf</code></pre>
<p>
	将<code>socks4 127.0.0.1 9095</code>改为
</p>
<pre class="hljs cpp"><code class="cpp">socks5 <span class="hljs-number">127.0</span><span class="hljs-number">.0</span><span class="hljs-number">.1</span> <span class="hljs-number">1080</span></code></pre>
<h4>
	3.3 使用方法
</h4>
<p>
	在需要代理的命令前加上 proxychains4 ，如：
</p>
<pre class="hljs objectivec"><code class="objectivec">proxychains4 wget http:<span class="hljs-comment">//xxx.com/xxx.zip</span></code></pre>
<br />
<div>
	文／左蓝（简书作者）<br />
原文链接：http://www.jianshu.com/p/8e7d7f57bf59<br />
著作权归作者所有，转载请联系作者获得授权，并标注“简书作者”。
</div>