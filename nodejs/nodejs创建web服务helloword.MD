<h2>
	<a id="cb_post_title_url" href="http://www.cnblogs.com/macroxu-1982/archive/2013/04/02/2995174.html">nodejs创建web服务helloword</a> 
</h2>
<div id="cnblogs_post_body">
	<p>
		第一步创建js并包含启动服务的功能<br />
<pre class="prettyprint lang-js linenums">var http = require('http');  
var url = require('url');  
  
http.createServer(function(request, response){  
    response.writeHead(200,{'Content-Type':'text/plain'});  
      
    var params = url.parse(request.url, true).query;  
    var input = params.number;  
      
    var numInput = new Number(input);  
    var numOutput = new Number(Math.random() * numInput).toFixed(0);  
      
    response.write(numOutput);  
    response.end();  
}).listen(8124);  
  
console.log('Random Number Generator');
</pre>
<br />
第二步： dos 命令启动nodejs，并执行初始化js<br />
&nbsp;<br />
&nbsp; dos命令 node 'js路径'<br />
<br />
现在直接在浏览器中输入 http://l27.0.0.1/?number=11 ,查看效果
	</p>
</div>