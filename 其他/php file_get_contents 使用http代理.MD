function send_post($url, $post_data) {<br />
&nbsp; &nbsp; $postdata = http_build_query($post_data);<br />
&nbsp; &nbsp; $options = array(<br />
&nbsp; &nbsp; &nbsp; &nbsp; 'http' =&gt; array(<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'method' =&gt; 'GET',//or GET<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'header' =&gt; 'Content-type:application/x-www-form-urlencoded',<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'content' =&gt; $postdata,<br />
'proxy' =&gt; 'tcp://127.0.0.1:8888',&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 'timeout' =&gt; 15 * 60 // 超时时间（单位:s）<br />
&nbsp; &nbsp; &nbsp; &nbsp; )<br />
&nbsp; &nbsp; );<br />
&nbsp; &nbsp; $context = stream_context_create($options);<br />
&nbsp; &nbsp; $result = file_get_contents($url, false, $context);<br />
&nbsp; &nbsp; return $result;<br />
}<br />