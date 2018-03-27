system = require('system') &nbsp; //传递一些需要的参数给js文件 &nbsp;<br />
&nbsp;&nbsp;<br />
address = system.args[1];//获得命令行第二个参数 ，也就是指定要加载的页面地址，接下来会用到 &nbsp; &nbsp;<br />
&nbsp;&nbsp;<br />
var page = require('webpage').create(); &nbsp;<br />
&nbsp;&nbsp;<br />
var url = address; &nbsp;<br />
&nbsp;&nbsp;<br />
&nbsp;&nbsp;<br />
page.open(url, function (status) { &nbsp;<br />
&nbsp;&nbsp;<br />
&nbsp; &nbsp; if (status !== 'success') { &nbsp;<br />
&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; console.log('Unable to post!'); &nbsp;<br />
&nbsp; &nbsp; } else { &nbsp;<br />
&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; var encodings = ["euc-jp", "sjis", "utf8", "System"];//这一步是用来测试输出的编码格式，选择合适的编码格式很重要，不然你抓取下来的页面会乱码o(╯□╰)o，给出的几个编码格式是官网上的例子，根据具体需要自己去调整。 &nbsp;<br />
&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; for (var i = 3; i &lt; encodings.length; i++) {//我这里只要一种编码就OK啦 &nbsp;<br />
&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; phantom.outputEncoding = encodings[i]; &nbsp;<br />
&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; console.log(phantom.outputEncoding+page.content);//最后返回webkit加载之后的页面内容 &nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; } &nbsp;<br />
&nbsp;&nbsp;<br />
&nbsp; &nbsp; } &nbsp;<br />
&nbsp; &nbsp; phantom.exit(); &nbsp;<br />
}); &nbsp; &nbsp;&nbsp;<br />