<pre style="line-height:20px;white-space:pre-wrap;box-sizing:border-box;overflow:auto;font-family:&quot;padding:10px 20px;margin-top:20px;margin-bottom:20px;color:#F8F8D4;word-wrap:break-word;border:none;border-radius:4px;font-stretch:normal;background:#4A4A4A;">server {
listen 80;
server_name $host;
location / {
proxy_pass http://www.31.gd/;
proxy_set_header Host $host;
proxy_redirect off;
proxy_set_header X-Real-IP $remote_addr;
proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
proxy_connect_timeout 60;
proxy_read_timeout 600;
proxy_send_timeout 600;
}
}</pre>