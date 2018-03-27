server {<br />
&nbsp; &nbsp; listen&nbsp; &nbsp; &nbsp; &nbsp;80;<br />
&nbsp; &nbsp; #listen&nbsp; &nbsp; &nbsp; &nbsp;somename:8080;<br />
&nbsp; &nbsp; server_name&nbsp; test.com&nbsp;test1.com;<br />
<br />
&nbsp; &nbsp; root&nbsp; /var/www/test;<br />
&nbsp; &nbsp; #alias&nbsp; another.alias;<br />
&nbsp; &nbsp; #oot /usr/share/nginx/html;<br />
&nbsp; &nbsp; include ./rewirte.conf&nbsp;<br />
&nbsp; &nbsp; location ~ \.php$ {<br />
&nbsp; &nbsp; &nbsp; fastcgi_pass 127.0.0.1:9000;<br />
&nbsp; &nbsp; &nbsp; fastcgi_index index.php;<br />
&nbsp; &nbsp; &nbsp; fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;<br />
&nbsp; &nbsp; &nbsp; include fastcgi_params;<br />
&nbsp; &nbsp; }<br />
<br />
&nbsp; &nbsp; location / {<br />
&nbsp; &nbsp; &nbsp; &nbsp; index&nbsp; index.php index.html index.htm;<br />
&nbsp; &nbsp; }<br />
<br />
&nbsp; &nbsp;access_log /var/log/nginx/test_access.log;<br />
&nbsp; &nbsp;error_log /var/log/nginx/test_error.log;<br />
}<br />