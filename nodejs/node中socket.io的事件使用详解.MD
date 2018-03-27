<p style="margin-top:0px;margin-bottom:0px;padding:5px 0px;white-space:normal;text-indent:2em;">
<pre class="prettyprint lang-js linenums">socket.io类库不但可以相互发送消息,而且还可以通过socket端口对象的emit方法互相发送事件.
emit在之前的事件上说过现在一句话带过:emit是用来手动触发事件的.
复制代码代码如下:

socket.emit(event,data,function(data1,data2......){
});
在使用emit方法发送事件时,可以再另一端使用socket端口对象的on方法会once方法监听.
复制代码代码如下:

socket.on(event,function(data,fn){
});
socket.once(event,function(data,fn){
})
上面的回调函数中的参数data:对方发送的事件中携带的数据,
fn:对方在发送事件时指定的callback回调函数.
案例1:当服务器和客户端连接后,向客户端发送一个news事件,事件中携带一个对象,该对象的hello属性值为"你好".在接收到客户端发送my other event事件时,在控制台中输出"服务器端就收到数据"+客户端发送事件中携带的数据.
服务器端代码,server.js
复制代码代码如下:

 var http=require("http");
 var sio=require("socket.io");
 var fs=require("fs");
 var server=http.createServer(function (req,res) {
     res.writeHead(200,{"Content-type":"text/html"});
     res.end(fs.readFileSync("./index.html"));
 });
 server.listen(1337);
 var socket=sio.listen(server);
 socket.on("connection", function (socket) {
     socket.emit("news",{hello:"你好"});
     socket.on("my other event", function (data) {
         console.log("服务器端接受到信息%j",data);
     });
 });
客户端index.html代码:
复制代码代码如下:

 &lt;!DOCTYPE html&gt;
 &lt;html&gt;
 &lt;head lang="en"&gt;
     &lt;meta charset="UTF-8"&gt;
     &lt;title&gt;&lt;/title&gt;
     &lt;script src="/socket.io/socket.io.js"&gt;&lt;/script&gt;
     &lt;script&gt;
         var socket=io.connect();
         socket.on("news", function (data) {
             console.log(data.hello);
             socket.emit("my other event",{my:"data"});
         });        
     &lt;/script&gt;
 &lt;/head&gt;
 &lt;body&gt;
 
 &lt;/body&gt;

运行结果:、
 


可以发现一点:执行总是在监听端,而不是手动执行端.
案例2:在手动触发对方事件时,指定回调函数.
当客户端和服务端连接后,向客户端发送setName事件,事件携带"张三",触发事件时,指定一个回调函数,该回调函数向控制台输出2个参数值.
复制代码代码如下:

 var http=require("http");
 var sio=require("socket.io");
 var fs=require("fs");
 var server=http.createServer(function (req,res) {
     res.writeHead(200,{"Content-type":"text/html"});
     res.end(fs.readFileSync("./index.html"));
 });
 server.listen(1337);
 var socket=sio.listen(server);
 socket.on("connection", function (socket) {
     socket.emit("setName","张三", function (data1,data2) {
         console.log(data1);
         console.log(data2);
     });
 });
复制代码代码如下:

 &lt;!DOCTYPE html&gt;
 &lt;html&gt;
 &lt;head lang="en"&gt;
     &lt;meta charset="UTF-8"&gt;
     &lt;title&gt;&lt;/title&gt;
     &lt;script src="/socket.io/socket.io.js"&gt;&lt;/script&gt;
     &lt;script&gt;
         var socket=io.connect();
         socket.on("setName", function (name,fn) {
            console.log(name);
             fn("李四","王五");
         });      
     &lt;/script&gt;
 &lt;/head&gt;
 &lt;body&gt;
 
 &lt;/body&gt;
 &lt;/html&gt;</pre>
</p>