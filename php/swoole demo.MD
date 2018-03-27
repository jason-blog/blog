<div class="col-md-9 col-sm-8 col-xs-12" style="text-indent:2em;">
	<div class="post-topheader__info" data-username="sunwenzheng" data-userslug="sunwenzheng" data-useravatar="https://sfault-avatar.b0.upaiyun.com/150/107/1501078571-1030000000487103_big64">
		<h1 class="h3 post-topheader__info--title" id="articleTitle" data-id="1190000003057118">
			<a href="https://segmentfault.com/a/1190000003057118">swoole聊天室</a> 
		</h1>
	</div>
</div>
<div class="container mt30" style="text-indent:2em;">
	<div class="row">
		<div class="col-xs-12 col-md-9 main ">
			<div class="article fmt article__content" data-id="1190000003057118" data-license="cc">
				<p>
					原本我是准备接着写我那个多进程教程的，今天心血来潮想看看swoole的websocket,<br />
我就点开了这个<br />
<a rel="nofollow" href="http://wiki.swoole.com/wiki/page/397.html" target="_blank">WebSocket</a><br />
我看了看官网的demo,觉得看起来很简单嘛，
				</p>
<pre class="hljs xml"><code><span class="hljs-preprocessor">&lt;?php</span> <span class="hljs-comment">//官网demo</span> <span class="hljs-variable">$server</span> = <span class="hljs-keyword">new</span> swoole_websocket_server(<span class="hljs-string">"0.0.0.0"</span>, <span class="hljs-number">9501</span>); <span class="hljs-variable">$server</span>-&gt;on(<span class="hljs-string">'open'</span>, <span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-params">(swoole_websocket_server <span class="hljs-variable">$server</span>, <span class="hljs-variable">$request</span>)</span> </span>{ <span class="hljs-keyword">echo</span> <span class="hljs-string">"server: handshake success with fd{$request-&gt;fd}\n"</span>;<span class="hljs-comment">//$request-&gt;fd 是客户端id</span> }); <span class="hljs-variable">$server</span>-&gt;on(<span class="hljs-string">'message'</span>, <span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-params">(swoole_websocket_server <span class="hljs-variable">$server</span>, <span class="hljs-variable">$frame</span>)</span> </span>{ <span class="hljs-keyword">echo</span> <span class="hljs-string">"receive from {$frame-&gt;fd}:{$frame-&gt;data},opcode:{$frame-&gt;opcode},fin:{$frame-&gt;finish}\n"</span>; <span class="hljs-variable">$server</span>-&gt;push(<span class="hljs-variable">$frame</span>-&gt;fd, <span class="hljs-string">"this is server"</span>);<span class="hljs-comment">//$frame-&gt;fd 是客户端id，$frame-&gt;data是客户端发送的数据</span> <span class="hljs-comment">//服务端向客户端发送数据是用 $server-&gt;push( '客户端id' ,  '内容')</span> }); <span class="hljs-variable">$server</span>-&gt;on(<span class="hljs-string">'close'</span>, <span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-params">(<span class="hljs-variable">$ser</span>, <span class="hljs-variable">$fd</span>)</span> </span>{ <span class="hljs-keyword">echo</span> <span class="hljs-string">"client {$fd} closed\n"</span>;
}); <span class="hljs-variable">$server</span>-&gt;start(); </code></pre>
				<p>
					我就是喜欢这种简单易懂的demo ，每行代码意思一看就明白
				</p>
				<p>
					服务端有了，我找点客户端的js代码<br />
<a rel="nofollow" href="https://developer.mozilla.org/zh-CN/docs/WebSockets/Writing_WebSocket_client_applications" target="_blank">火狐的MDN</a> 
				</p>
<pre class="hljs xml"><code><span class="hljs-doctype">&lt;!DOCTYPE html&gt;</span> <span class="hljs-tag">&lt;<span class="hljs-title">html</span>&gt;</span> <span class="hljs-tag">&lt;<span class="hljs-title">head</span>&gt;</span> <span class="hljs-tag">&lt;<span class="hljs-title">title</span>&gt;</span><span class="hljs-tag">&lt;/<span class="hljs-title">title</span>&gt;</span> <span class="hljs-tag">&lt;<span class="hljs-title">meta</span> <span class="hljs-attribute">charset</span>=<span class="hljs-value">"UTF-8"</span>&gt;</span> <span class="hljs-tag">&lt;<span class="hljs-title">script</span> <span class="hljs-attribute">type</span>=<span class="hljs-value">"text/javascript"</span>&gt;</span><span class="javascript"> <span class="hljs-keyword">var</span> exampleSocket = <span class="hljs-keyword">new</span> WebSocket(<span class="hljs-string">"ws://0.0.0.0:9501"</span>);
  exampleSocket.onopen = <span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-params">(event)</span> </span>{
    exampleSocket.send(<span class="hljs-string">"亲爱的服务器！我连上你啦！"</span>); 
  };
  exampleSocket.onmessage = <span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-params">(event)</span> </span>{ <span class="hljs-built_in">console</span>.log(event.data);
  } </span><span class="hljs-tag">&lt;/<span class="hljs-title">script</span>&gt;</span> <span class="hljs-tag">&lt;/<span class="hljs-title">head</span>&gt;</span> <span class="hljs-tag">&lt;<span class="hljs-title">body</span>&gt;</span> <span class="hljs-tag">&lt;<span class="hljs-title">input</span> <span class="hljs-attribute">type</span>=<span class="hljs-value">"text"</span> <span class="hljs-attribute">id</span>=<span class="hljs-value">"content"</span>&gt;</span> <span class="hljs-tag">&lt;<span class="hljs-title">button</span> <span class="hljs-attribute">onclick</span>=<span class="hljs-value">"exampleSocket.send( document.getElementById('content').value )"</span>&gt;</span>发送<span class="hljs-tag">&lt;/<span class="hljs-title">button</span>&gt;</span> <span class="hljs-tag">&lt;/<span class="hljs-title">body</span>&gt;</span> <span class="hljs-tag">&lt;/<span class="hljs-title">html</span>&gt;</span> </code></pre>
				<p>
					最后命令行运行php文件，之后浏览器打开html文件，
F12打开调试界面看console，ok ， 没有问题
				</p>
				<p>
					这个时候我突然想到一个事情，因为我做多进程的那个教程里，在主进程中会将所有的子进程的句柄存起来，以后进行进程间通讯用。<br />
那么 我将所有的客户端的链接存起来存成数组，每当一个客户端发送消息时，我就遍历这个客户端数组，将消息群发一遍，不久实现了聊天室了吗？<br />
然后就，服务端代码成了这个样子
				</p>
<pre class="hljs xml"><code><span class="hljs-preprocessor">&lt;?php</span> <span class="hljs-variable">$map</span> = <span class="hljs-keyword">array</span>();<span class="hljs-comment">//客户端集合</span> <span class="hljs-variable">$server</span> = <span class="hljs-keyword">new</span> swoole_websocket_server(<span class="hljs-string">"0.0.0.0"</span>, <span class="hljs-number">9501</span>); <span class="hljs-variable">$server</span>-&gt;on(<span class="hljs-string">'open'</span>, <span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-params">(swoole_websocket_server <span class="hljs-variable">$server</span>, <span class="hljs-variable">$request</span>)</span> </span>{ <span class="hljs-keyword">global</span> <span class="hljs-variable">$map</span>;<span class="hljs-comment">//客户端集合</span> <span class="hljs-variable">$map</span>[<span class="hljs-variable">$request</span>-&gt;fd] = <span class="hljs-variable">$request</span>-&gt;fd;<span class="hljs-comment">//首次连上时存起来</span> }); <span class="hljs-variable">$server</span>-&gt;on(<span class="hljs-string">'message'</span>, <span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-params">(swoole_websocket_server <span class="hljs-variable">$server</span>, <span class="hljs-variable">$frame</span>)</span> </span>{ <span class="hljs-keyword">global</span> <span class="hljs-variable">$map</span>;<span class="hljs-comment">//客户端集合</span> <span class="hljs-variable">$data</span> = <span class="hljs-variable">$frame</span>-&gt;data; <span class="hljs-keyword">foreach</span>(<span class="hljs-variable">$map</span> <span class="hljs-keyword">as</span> <span class="hljs-variable">$fd</span>){ <span class="hljs-variable">$server</span>-&gt;push(<span class="hljs-variable">$fd</span> , <span class="hljs-variable">$data</span>);<span class="hljs-comment">//循环广播</span> }
}); <span class="hljs-variable">$server</span>-&gt;on(<span class="hljs-string">'close'</span>, <span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-params">(<span class="hljs-variable">$ser</span>, <span class="hljs-variable">$fd</span>)</span> </span>{ <span class="hljs-keyword">echo</span> <span class="hljs-string">"client {$fd} closed\n"</span>;
}); <span class="hljs-variable">$server</span>-&gt;start(); </code></pre>
				<p>
					哈哈 ， 我觉得这样就大功告成了，结果发现自己是 图样图森破
大家可以自己试试，运行php后  ，  浏览器打开两个页面，看看console.log的内容是什么
				</p>
				<p>
					运行良好，可是并没有实现我们说的那种聊天效果。<br />
找找原因吧。<br />
我第一反映看看$map里面是什么，就输出看看，结果发现这个map里面只有一个元素。<br />
唉，不对啊，我这是全局变量，难道不应该是有几个客户端链接，就有几个元素吗？<br />
这是怎么回事啊，竟然没有保存到所有客户端id？
				</p>
				<p>
					到了这一步，我解决不了map变量的这个问题了，然后我就想看看那个fd是什么东西，<br />
老规矩 var_dump输出 ， 发现fd就是 int类型的数字，并且是自增的<br />
这好办了，不就是数字嘛
				</p>
				<p>
					于是呼，我就这样做<br />
变量存不了，我搞不定，我存文本里嘛。<br />
最终版 websocket.php
				</p>
<pre class="hljs xml"><code><span class="hljs-preprocessor">&lt;?php</span> <span class="hljs-variable">$server</span> = <span class="hljs-keyword">new</span> swoole_websocket_server(<span class="hljs-string">"0.0.0.0"</span>, <span class="hljs-number">9501</span>); <span class="hljs-variable">$server</span>-&gt;on(<span class="hljs-string">'open'</span>, <span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-params">(swoole_websocket_server <span class="hljs-variable">$server</span>, <span class="hljs-variable">$request</span>)</span> </span>{
    file_put_contents( <span class="hljs-keyword">__DIR__</span> .<span class="hljs-string">'/log.txt'</span> , <span class="hljs-variable">$request</span>-&gt;fd);
}); <span class="hljs-variable">$server</span>-&gt;on(<span class="hljs-string">'message'</span>, <span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-params">(swoole_websocket_server <span class="hljs-variable">$server</span>, <span class="hljs-variable">$frame</span>)</span> </span>{ <span class="hljs-keyword">global</span> <span class="hljs-variable">$client</span>; <span class="hljs-variable">$data</span> = <span class="hljs-variable">$frame</span>-&gt;data; <span class="hljs-variable">$m</span> = file_get_contents( <span class="hljs-keyword">__DIR__</span> .<span class="hljs-string">'/log.txt'</span>); <span class="hljs-keyword">for</span> (<span class="hljs-variable">$i</span>=<span class="hljs-number">1</span> ; <span class="hljs-variable">$i</span>&lt;= <span class="hljs-variable">$m</span> ; <span class="hljs-variable">$i</span>++) { <span class="hljs-keyword">echo</span> PHP_EOL . <span class="hljs-string">'  i is  '</span> . <span class="hljs-variable">$i</span> . <span class="hljs-string">'  data  is '</span>.<span class="hljs-variable">$data</span> . <span class="hljs-string">'  m = '</span> . <span class="hljs-variable">$m</span>; <span class="hljs-variable">$server</span>-&gt;push(<span class="hljs-variable">$i</span>, <span class="hljs-variable">$data</span> );
    }

}); <span class="hljs-variable">$server</span>-&gt;on(<span class="hljs-string">'close'</span>, <span class="hljs-function"><span class="hljs-keyword">function</span> <span class="hljs-params">(<span class="hljs-variable">$ser</span>, <span class="hljs-variable">$fd</span>)</span> </span>{ <span class="hljs-keyword">echo</span> <span class="hljs-string">"client {$fd} closed\n"</span>;
}); <span class="hljs-variable">$server</span>-&gt;start(); </code></pre>
				<p>
					再次打开html文件，多个页面进行输入观察，ok，可以了。
				</p>
				<p>
					当然，作为聊天室，我这写的也过于简陋了，界面大家自己可以写的好看一些(因为我懒的写界面)
还有，每次的发送聊天的记录，应该存起来，这样，如果有新的连接连过来的时候，先把以前的聊天记录发过去，这样，我想体验更好一些
				</p>
				<p>
					然后，大家可以愉快的聊天了。哈哈
				</p>
			</div>
		</div>
	</div>
</div>