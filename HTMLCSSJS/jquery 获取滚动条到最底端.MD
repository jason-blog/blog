&lt;html&gt;<br />
&lt;script type="text/javascript" src="http://www.phpstudy.net/e/jquery/jquery.js"&gt;&lt;/script&gt;<br />
&lt;script&gt;<br />
<br />
<br />
<br />
$(window).scroll(function () {<br />
<br />
&nbsp; &nbsp; &nbsp; &nbsp;console.log(Math.ceil($(window).scrollTop()));<br />
&nbsp;&nbsp;<br />
&nbsp; &nbsp;console.log( Math.ceil($(window).height()));<br />
<br />
console.log($(document).height());<br />
<br />
<br />
&nbsp;&nbsp;<br />
&nbsp; &nbsp; if (Math.ceil($(window).scrollTop()) + Math.ceil($(window).height()) &gt;= $(document).height()) {<br />
<br />
<br />
&nbsp; &nbsp; }<br />
});<br />
var i=0;<br />
<br />
<br />
<br />
&lt;/script&gt;<br />
<br />
&lt;body style='height:1500px;'&gt;<br />
<br />
<br />
&lt;/body&gt;<br />
<br />
&lt;html&gt;<br />