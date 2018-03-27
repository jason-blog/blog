<pre class="prettyprint lang-js linenums">&lt;html&gt;
&lt;script type="text/javascript" src="http://www.phpstudy.net/e/jquery/jquery.js"&gt;&lt;/script&gt;
&lt;script&gt;



$(window).scroll(function () {

       console.log(Math.ceil($(window).scrollTop()));
	   
	    console.log( Math.ceil($(window).height()));
		
		console.log($(document).height());
		

	   
    if (Math.ceil($(window).scrollTop()) + Math.ceil($(window).height()) &gt;= $(document).height()) {
		
		
    }
});
var i=0;



&lt;/script&gt;

&lt;body style='height:1500px;'&gt;


&lt;/body&gt;

&lt;html&gt;</pre>