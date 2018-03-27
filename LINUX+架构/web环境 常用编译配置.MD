nginx<br />
./configure --user=nginx --group=nginx --prefix=/usr/local/nginx --with-http_stub_status_module --with-http_ssl_module<br />
<br />
<br />
<br />
mysql<br />
./configure --prefix=/usr/local/mysql --without-debug --enable-thread-safe-client --with-pthread --enable-assembler --enable-profiling --with-mysqld-ldflags=-all-static --with-client-ldflags=-all-static --with-extra-charsets=all --with-plugins=all --with-mysqld-user=mysql --without-embedded-server --with-server-suffix=-community --with-unix-socket-path=/tmp/mysql.sock<br />
<br />
<br />
<br />
php<br />
<br />
'./configure' '--prefix=/usr/local/php' '--with-config-file-path=/usr/local/php' '--with-mysql=/usr/local/mysql' '--with-iconv=/usr' '--with-mysqli=/www/local/mysql/bin/mysql_config' '--with-pdo-mysql=/www/local/mysql' '--with-freetype-dir' '--with-jpeg-dir' '--with-png-dir' '--with-zlib' '--with-libxml-dir=/usr' '--enable-xml' '--disable-rpath' '--enable-discard-path' '--enable-inline-optimization' '--with-curl' '--enable-mbregex' '--enable-mbstring' '--with-mcrypt=/usr' '--with-gd' '--enable-gd-native-ttf' '--with-openssl' '--with-mhash' '--enable-ftp' '--enable-fpm' '--enable-bcmath' '--enable-exif' '--enable-sockets' '--enable-zip' '--with-apxs2=/www/wdlinux/apache/bin/apxs'<br />
<br />
<br />
apache<br />
./configure --prefix=/usr/local/apache2 --with-apr=/usr/local/apr --with-apr-util=/usr/local/apr-util/ --with-pcre=/usr/local/pcre<br />