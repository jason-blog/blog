<pre class="prettyprint lang-js linenums">var fs = require('fs'),
    http = require('http'),
    sio = require('socket.io');
var qs = require('querystring');  

var server = http.createServer(function(req, res) {
   // res.writeHead(200, { 'Content-type': 'text/html' });
    res.end("sdfsf");
});
server.listen(8888, function() {
    console.log('Server listening at http://localhost:8888/');
});
// Attach the socket.io server
io = sio.listen(server);
// store messages
var messages = [];

var wocao='110';
     
////////////////////////////////////////////////////////////////////////////////////HTTP POST 
function httpPost(){


var qs = require('querystring');  
  
var post_data = {  
    password: "world",  
    node: '8207f1db190a5eb8dfb4943f251866dc'

};//这是需要提交的数据  
  
  
var content = qs.stringify(post_data);  
  console.log(content);
var options = {  
    hostname: 'logintest1.24k88.eu', 
    port: 80,  
    path: '/index.php?s=/Index_slotWin',  
    method: 'POST',  
    headers: {  
        'Content-Type': 'application/x-www-form-urlencoded; charset=UTF-8'  
    }  
};  
  
var req = http.request(options, function (res) {  
   // console.log('STATUS: ' + res.statusCode);  
  // console.log('HEADERS: ' + JSON.stringify(res.headers));  
    res.setEncoding('utf8');  
    res.on('data', function (chunk) {  
        console.log('BODY: ' + chunk);  
wocao=chunk;
return chunk;
    });  
});  
  
req.on('error', function (e) {  
    console.log('problem with request: ' + e.message);  
});  
  
// write data to request body  
req.write(content);  
  
req.end(); 

return req;
}
////////////////////////////////////////////////////////////////////////////////////HTTP POST +++++
// Define a message handler
io.sockets.on('connection', function(socket) {


httpPost();

           messages.push(wocao);

      messages.push('成功连上了，但是，，，，');

                  var oneSecond = 1000 * 1; // one second = 1000 x 1 ms
 
 var wcaojson=eval('(' + wocao + ')');
                  setInterval(function() {
      httpPost();
                       messages.push(wocao);
                       socket.send(wcaojson);             // document.write('&lt;p&gt;Hello there.&lt;/p&gt;');
                  }, oneSecond);


              var timeout_ms = 2000; // 2 seconds
                   var timeout = setTimeout(function() {
                            console.log("timed out!");
                   }, timeout_ms);





    socket.on('message', function(msg) {
        console.log('Received: ', msg);
        messages.push(msg);
        socket.broadcast.emit('message', msg);
    });

    // send messages to new clients
    messages.forEach(function(msg) {
        socket.send(msg);
    })


});






///客户端/////////////////////////////////////

&lt;html&gt;
&lt;head&gt;
  &lt;style type="text/css"&gt;
    #messages { padding: 0px; list-style-type: none;}
    #messages li { padding: 2px 0px; border-bottom: 1px solid #ccc; }
  &lt;/style&gt;
  &lt;script src="http://code.jquery.com/jquery-1.7.1.min.js"&gt;&lt;/script&gt;
  &lt;script src="https://cdn.socket.io/socket.io-1.3.4.js"&gt;&lt;/script&gt;
  &lt;script&gt;
      $(function() {
          var socket = io.connect("http://192.168.42.129:8888/");
          socket.on('connect', function() {
              socket.on('message', function(message) {
                  $('#messages').append($('&lt;li&gt;&lt;/li&gt;').text(message));
              });
              socket.on('disconnect', function() {
                  $('#messages').append('&lt;li&gt;Disconnected&lt;/li&gt;');
              });
          });

          var el = $('#chatmsg');
          $('#chatmsg').keypress(function(e) {
              if (e.which == 13) {
                 // e.preventDefault();
                  socket.send(el.val());
                  $('#messages').append($('&lt;li&gt;&lt;/li&gt;').text(el.val()));
                  el.val('');
              }
          });
      });
  &lt;/script&gt;
&lt;/head&gt;
&lt;body&gt;
 &lt;ul id="messages"&gt;&lt;/ul&gt;
 &lt;hr&gt;
 &lt;input type="text" id="chatmsg"&gt;
&lt;/body&gt;
&lt;/html&gt;


</pre>
<div style="white-space:nowrap;">
	<br />
</div>