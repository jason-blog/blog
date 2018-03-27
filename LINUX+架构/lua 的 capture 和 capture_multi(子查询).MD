location /capture {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; content_by_lua_file lua/capture.lua;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; #access_by_lua_file lua/capture.lua;<br />
&nbsp; &nbsp; &nbsp; &nbsp; }<br />
<br />
&nbsp; &nbsp; &nbsp; &nbsp; location ~ \.php$ {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; root &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; html;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; fastcgi_pass &nbsp; 127.0.0.1:9000;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; fastcgi_index &nbsp;index.php;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; fastcgi_param &nbsp;SCRIPT_FILENAME &nbsp;$document_root$fastcgi_script_name;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; include &nbsp; &nbsp; &nbsp; &nbsp;fastcgi_params;<br />
<p>
	&nbsp; &nbsp; &nbsp; &nbsp; }
</p>
<p>
	<br />
</p>
<p>
	[root@localhost lua]# pwd<br />
/opt/openresty/nginx/lua<br />
[root@localhost lua]# cat capture.lua<br />
local res1,res2,res3,res4 = ngx.location.capture_multi{<br />
&nbsp; &nbsp; &nbsp; &nbsp; {"/mysql_test", {args="t=1&amp;id=1"}},<br />
&nbsp; &nbsp; &nbsp; &nbsp; {"/redis_test", {args="t=2&amp;id=2"}},<br />
&nbsp; &nbsp; &nbsp; &nbsp; {"/lua", {args="t=3&amp;id=3"}},<br />
&nbsp; &nbsp; &nbsp; &nbsp; {"/index.php", {args="t=3&amp;id=3"}},<br />
}<br />
<br />
ngx.header.content_type="text/plain"<br />
ngx.say(res1.body)<br />
ngx.say(res2.body)<br />
ngx.say(res3.body)<br />
ngx.say(res4.truncated)<br />
ngx.say(res4.status)<br />
ngx.say(res4.header["Set-Cookie"])<br />
<br />
--ngx.say(res4.body)
</p>