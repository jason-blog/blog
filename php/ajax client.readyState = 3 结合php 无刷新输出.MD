<pre class="prettyprint lang-js linenums">&lt;!DOCTYPE html&gt;
&lt;html&gt;
&lt;head&gt;
&lt;meta charset="UTF-8"&gt;
&lt;title&gt;Insert title here&lt;/title&gt;
&lt;/head&gt;
&lt;body&gt;
&lt;div id="test"&gt;waiting&lt;/div&gt;
&lt;script&gt;
scan();
function scan()
{

	var params="ignore_warning=1";
	var prevDataLength;
	client = new XMLHttpRequest();
	client.onreadystatechange = function () 
	{ 
	console.log(client);
       if(client.readyState)
			
	while (prevDataLength != client.responseText.length) {
		if (client.readyState == 4  &amp;&amp; prevDataLength == client.responseText.length)
			break;		
		 prevDataLength = client.responseText.length;
		 console.log(client.responseText);
	     document.getElementById("test").innerHTML = client.responseText;
	  }
	}
	client.open("POST", "index.php", true);
	client.setRequestHeader("Content-type", "application/x-www-form-urlencoded");
	//client.setRequestHeader("Content-length", params.length);
	//client.setRequestHeader("Connection", "close");
	client.send(params);
}
&lt;/script&gt;
&lt;?php 

        $i=0;
	    for(;;){
	       echo $i++;
	       sleep(2);
	       flush();
	       ob_flush();
	    }
?&gt;
&lt;/body&gt;
&lt;/html&gt;</pre>