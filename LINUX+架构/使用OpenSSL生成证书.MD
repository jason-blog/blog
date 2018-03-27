使用OpenSSL生成证书<br />
<br />
1、生成RSA密钥的方法<br />
<br />
[c-sharp] view plaincopy<br />
openssl genrsa -des3 -out privkey.pem 2048 &nbsp;<br />
这个命令会生成一个2048位的密钥，同时有一个des3方法加密的密码，如果你不想要每次都输入密码，可以改成：<br />
<br />
[c-sharp] view plaincopy<br />
openssl genrsa -out privkey.pem 2048 &nbsp;<br />
&nbsp;<br />
<br />
建2、生成一个证书请求<br />
<br />
建议用2048位密钥，少于此可能会不安全或很快将不安全。<br />
<br />
[c-sharp] view plaincopy<br />
openssl req -new -key privkey.pem -out cert.csr &nbsp;<br />
这个命令将会生成一个证书请求，当然，用到了前面生成的密钥privkey.pem文件<br />
这里将生成一个新的文件cert.csr，即一个证书请求文件，你可以拿着这个文件去数字证书颁发机构（即CA）申请一个数字证书。CA会给你一个新的文件cacert.pem，那才是你的数字证书。<br />
<br />
如果是自己做测试，那么证书的申请机构和颁发机构都是自己。就可以用下面这个命令来生成证书：<br />
<br />
[c-sharp] view plaincopy<br />
openssl req -new -x509 -key privkey.pem -out cacert.pem -days 1095 &nbsp;<br />
这个命令将用上面生成的密钥privkey.pem生成一个数字证书cacert.pem<br />
<br />
配置nginx<br />
<br />
[c-sharp] view plaincopy<br />
01.server &nbsp;<br />
02.{ &nbsp;<br />
03. listen 443; &nbsp;<br />
04. ssl on; &nbsp;<br />
05. ssl_certificate /var/www/sslkey/cacert.pem; &nbsp;<br />
06. ssl_certificate_key /var/www/sslkey/privkey.pem; &nbsp;<br />
07. server_name 192.168.1.1; &nbsp;<br />
08. index index.html index.htm index.php; &nbsp;<br />
09. root /var/www/test; &nbsp;<br />
10. &nbsp;<br />
11. ….. &nbsp;<br />
12. … &nbsp;<br />
13.} &nbsp;<br />
&nbsp;<br />