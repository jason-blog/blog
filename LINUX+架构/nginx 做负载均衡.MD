upstream b.com {&nbsp;<br />
&nbsp; &nbsp; &nbsp; server &nbsp;192.168.5.150:80;&nbsp;<br />
&nbsp; &nbsp; &nbsp; server &nbsp;192.168.5.151:80;&nbsp;<br />
&nbsp;#server &nbsp;127.0.0.1:8080;&nbsp;<br />
}&nbsp;<br />
&nbsp;&nbsp;<br />
server{&nbsp;<br />
&nbsp; &nbsp; listen 80;&nbsp;<br />
&nbsp; &nbsp; server_name b.com;&nbsp;<br />
&nbsp; &nbsp; location / {&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; proxy_pass &nbsp; &nbsp; &nbsp; &nbsp; http://b.com;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; proxy_set_header &nbsp; Host &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; $host;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; proxy_set_header &nbsp; X-Real-IP &nbsp; &nbsp; &nbsp; &nbsp;$remote_addr;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; proxy_set_header &nbsp; X-Forwarded-For &nbsp;$proxy_add_x_forwarded_for;&nbsp;<br />
&nbsp; &nbsp; }&nbsp;<br />
}<br />
<br />
<br />
<br />
&nbsp;server {<br />
&nbsp; &nbsp; &nbsp; &nbsp; listen 8080 default_server;<br />
&nbsp; &nbsp; &nbsp; &nbsp; server_name localhost;<br />
&nbsp; &nbsp; &nbsp; &nbsp; root /www/html;<br />
&nbsp; &nbsp; &nbsp; &nbsp; index index.php index.html index.htm;<br />
<br />
&nbsp; &nbsp; &nbsp; &nbsp; location ~ \.php$ {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; fastcgi_pass &nbsp; 127.0.0.1:9000;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; fastcgi_index &nbsp;index.php;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; fastcgi_param &nbsp;SCRIPT_FILENAME &nbsp;$document_root$fastcgi_script_name;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; fastcgi_param &nbsp;PHP_VALUE &nbsp; &nbsp; &nbsp; &nbsp;open_basedir=$document_root:/tmp/:/proc/;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; include &nbsp; &nbsp; &nbsp; &nbsp;fastcgi_params;<br />
&nbsp; &nbsp; &nbsp; &nbsp; }<br />
<br />
&nbsp; &nbsp; }<br />