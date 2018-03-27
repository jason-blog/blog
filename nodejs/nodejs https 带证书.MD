var fs = require( 'fs' );<br />
var app = require('express')();<br />
var https &nbsp; &nbsp; &nbsp; &nbsp;= require('https');<br />
var server = https.createServer({<br />
&nbsp; &nbsp;key: fs.readFileSync('./test_key.key'),<br />
&nbsp; &nbsp;cert: fs.readFileSync('./test_cert.crt'),<br />
&nbsp; &nbsp;ca: fs.readFileSync('./test_ca.crt'),<br />
&nbsp; &nbsp;requestCert: false,<br />
&nbsp; &nbsp;rejectUnauthorized: false<br />
},app);<br />
server.listen(8080);<br />
<br />
var io = require('socket.io').listen(server);<br />
<br />
io.sockets.on('connection',function (socket) {<br />
&nbsp; &nbsp;...<br />
});<br />
<br />
app.get("/", function(request, response){<br />
&nbsp; &nbsp;...<br />
})<br />