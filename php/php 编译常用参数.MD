<p style="margin:10px auto;padding:0px;font-family:&quot;font-weight:700;white-space:normal;background-color:#FFFFFF;">
	常用的配置参数<br style="margin:0px;padding:0px;" />
<span style="margin:0px;padding:0px;font-family:&quot;font-size:18px;color:#FF0000;"><strong style="margin:0px;padding:0px;">1.&nbsp;<span style="margin:0px;padding:0px;">--prefix</span></strong>=/usr/local/php</span><br style="margin:0px;padding:0px;" />
指定 php 安装目录<br style="margin:0px;padding:0px;" />
install architecture-independent files in PREFIX 默认/usr/local<br style="margin:0px;padding:0px;" />
<span style="margin:0px;padding:0px;font-size:18px;"><strong style="margin:0px;padding:0px;"><span style="margin:0px;padding:0px;color:#FF0000;font-family:&quot;">2.--with-config-file-path=PATH</span></strong></span><br style="margin:0px;padding:0px;" />
php.ini的存放位置<br style="margin:0px;padding:0px;" />
Set the path in which to look for php.ini [PREFIX/lib]<br style="margin:0px;padding:0px;" />
<strong style="margin:0px;padding:0px;"><span style="margin:0px;padding:0px;color:#FF0000;font-family:&quot;">--with-config-file-scan-dir=PATH</span></strong><br style="margin:0px;padding:0px;" />
php.ini的扩展目录<br style="margin:0px;padding:0px;" />
Set the path where to scan for configuration files<br style="margin:0px;padding:0px;" />
<span style="margin:0px;padding:0px;font-size:18px;font-family:&quot;"><span style="margin:0px;padding:0px;color:#FF0000;">3.--with-apxs2=FILE</span>&nbsp;</span><br style="margin:0px;padding:0px;" />
生成libphp5.so ,httpd处理php的模块,需要用到apache的apxs支持 (需安装了httpd-devel)<br style="margin:0px;padding:0px;" />
Build shared Apache 2.0 Handler module. FILE is the optional<br style="margin:0px;padding:0px;" />
pathname to the Apache apxs tool apxs<br style="margin:0px;padding:0px;" />
<span style="margin:0px;padding:0px;font-size:18px;font-family:&quot;"><span style="margin:0px;padding:0px;color:#FF0000;">4.--with-mysql=DIR</span>&nbsp;</span><br style="margin:0px;padding:0px;" />
加入mysql支持, mysql官方的Mysql驱动目录,如果没设置DIR就使用php自带的mysql驱动mysqlnd<br style="margin:0px;padding:0px;" />
Include MySQL support. DIR is the MySQL base directory, if no DIR is passed or the value is<br style="margin:0px;padding:0px;" />
mysqlnd the MySQL native driver will be used<br style="margin:0px;padding:0px;" />
<span style="margin:0px;padding:0px;color:#FF0000;font-size:18px;font-family:&quot;">5.--with-mysqli=FILE&nbsp;</span><br style="margin:0px;padding:0px;" />
加入mysqli支持,没有设置默认是mysqlnd<br style="margin:0px;padding:0px;" />
Include MySQLi support. FILE is the path to mysql_config. If no value or mysqlnd is passed&nbsp;<br style="margin:0px;padding:0px;" />
as FILE, the MySQL native driver will be used<br style="margin:0px;padding:0px;" />
<span style="margin:0px;padding:0px;color:#FF0000;font-size:18px;font-family:&quot;">6.--with-pdo-mysql=DIR&nbsp;</span><br style="margin:0px;padding:0px;" />
加入pdo支持,默认为自带驱动mysqlnd&nbsp;<br style="margin:0px;padding:0px;" />
PDO: MySQL support. DIR is the MySQL base directory If no value or mysqlnd is passed as DIR, the<br style="margin:0px;padding:0px;" />
MySQL native driver will be used<br style="margin:0px;padding:0px;" />
<span style="margin:0px;padding:0px;color:#FF0000;font-family:&quot;font-size:18px;">7.--with-mysql-sock=SOCKPATH</span><br style="margin:0px;padding:0px;" />
指定mysql套接字文件位置,如果没指定则搜索默认位置<br style="margin:0px;padding:0px;" />
MySQL/MySQLi/PDO_MYSQL: Location of the MySQL unix socket pointer.<br style="margin:0px;padding:0px;" />
If unspecified, the default locations are searched<br style="margin:0px;padding:0px;" />
<span style="margin:0px;padding:0px;color:#FF0000;font-size:18px;font-family:&quot;">8.--enable-sockets&nbsp;</span><br style="margin:0px;padding:0px;" />
开启sockets支持<br style="margin:0px;padding:0px;" />
Enable sockets support<br style="margin:0px;padding:0px;" />
<span style="margin:0px;padding:0px;color:#FF0000;font-family:&quot;font-size:18px;">9.--with-libxml-dir=DIR&nbsp;</span><br style="margin:0px;padding:0px;" />
libxml2 安装位置<br style="margin:0px;padding:0px;" />
SimpleXML: libxml2 install prefix<br style="margin:0px;padding:0px;" />
<span style="margin:0px;padding:0px;color:#FF0000;font-size:18px;font-family:&quot;">10.--enable-mbstring&nbsp;</span><br style="margin:0px;padding:0px;" />
使php支持对多字节字符串的处理<br style="margin:0px;padding:0px;" />
Enable multibyte string support<br style="margin:0px;padding:0px;" />
<span style="margin:0px;padding:0px;color:#FF0000;font-family:&quot;font-size:18px;">11.--with-gd=DIR&nbsp;</span><br style="margin:0px;padding:0px;" />
Include GD support. DIR is the GD library base install directory BUNDLED<br style="margin:0px;padding:0px;" />
<span style="margin:0px;padding:0px;color:#FF0000;font-size:18px;font-family:&quot;">12.--with-curl=DIR&nbsp;</span><br style="margin:0px;padding:0px;" />
加入curl支持<br style="margin:0px;padding:0px;" />
Include cURL support<br style="margin:0px;padding:0px;" />
<span style="margin:0px;padding:0px;color:#FF0000;font-family:&quot;font-size:18px;">13.--with-mcrypt=DIR Include mcrypt support</span><br style="margin:0px;padding:0px;" />
<span style="margin:0px;padding:0px;color:#FF0000;font-family:&quot;font-size:18px;">14.--enable-zip Include Zip read/write support</span><br style="margin:0px;padding:0px;" />
<span style="margin:0px;padding:0px;color:#FF0000;font-family:&quot;font-size:18px;">15.--enable-calendar</span>&nbsp;<br style="margin:0px;padding:0px;" />
支持日历转换<br style="margin:0px;padding:0px;" />
Enable support for calendar conversion<br style="margin:0px;padding:0px;" />
<span style="margin:0px;padding:0px;color:#FF0000;font-family:&quot;font-size:18px;">16.--with-zlib=DIR&nbsp;</span><br style="margin:0px;padding:0px;" />
打开zlib库支持<br style="margin:0px;padding:0px;" />
Include ZLIB support (requires zlib &gt;= 1.0.9)<br style="margin:0px;padding:0px;" />
<span style="margin:0px;padding:0px;color:#FF0000;font-size:18px;font-family:&quot;">17.--enable-bcmath&nbsp;</span><br style="margin:0px;padding:0px;" />
打开图片大小调整,用到zabbix监控的时候用到了这个模块<br style="margin:0px;padding:0px;" />
Enable bc style precision math functions<br style="margin:0px;padding:0px;" />
<span style="margin:0px;padding:0px;color:#FF0000;font-family:&quot;font-size:18px;">18. --enable-soap Enable SOAP support</span><br style="margin:0px;padding:0px;" />
<span style="margin:0px;padding:0px;color:#FF0000;font-family:&quot;font-size:18px;">19.--with-iconv-dir=DIR XMLRPC-EPI: iconv dir for XMLRPC-EPI</span><br style="margin:0px;padding:0px;" />
<span style="margin:0px;padding:0px;color:#FF0000;font-family:&quot;font-size:18px;">20.--with-freetype-dir=DIR&nbsp;</span><br style="margin:0px;padding:0px;" />
打开对freetype字体库的支持&nbsp;<br style="margin:0px;padding:0px;" />
GD: Set the path to FreeType 2 install prefix<br style="margin:0px;padding:0px;" />
<span style="margin:0px;padding:0px;font-size:18px;font-family:&quot;color:#FF0000;">21.--with-jpeg-dir=DIR&nbsp;</span><br style="margin:0px;padding:0px;" />
打开对jpeg图片的支持<br style="margin:0px;padding:0px;" />
GD: Set the path to libjpeg install prefix<br style="margin:0px;padding:0px;" />
<span style="margin:0px;padding:0px;font-size:18px;font-family:&quot;color:#FF0000;">22.--with-png-dir=DIR&nbsp;</span><br style="margin:0px;padding:0px;" />
打开对png图片的支持<br style="margin:0px;padding:0px;" />
GD: Set the path to libpng install prefix<br style="margin:0px;padding:0px;" />
<span style="margin:0px;padding:0px;color:#FF0000;font-size:18px;font-family:&quot;">23.--without-sqlite3=DIR&nbsp;</span><br style="margin:0px;padding:0px;" />
自PHP5.3起默认启用SQLite3 扩展,可以在编译时使用--without-sqlite3禁用SQLite3 扩展<br style="margin:0px;padding:0px;" />
Do not include SQLite3 support. DIR is the prefix to SQLite3 installation directory.<br style="margin:0px;padding:0px;" />
<span style="margin:0px;padding:0px;color:#FF0000;font-size:18px;font-family:&quot;">24.--enable-exif&nbsp;</span><br style="margin:0px;padding:0px;" />
开启图片的元数据支持<br style="margin:0px;padding:0px;" />
Enable EXIF (metadata from images) support<br style="margin:0px;padding:0px;" />
<span style="margin:0px;padding:0px;font-size:18px;color:#FF0000;font-family:&quot;">25.--enable-ftp Enable FTP support</span><br style="margin:0px;padding:0px;" />
<span style="margin:0px;padding:0px;font-size:18px;color:#FF0000;font-family:&quot;">26.--with-pcre-dir&nbsp;</span><br style="margin:0px;padding:0px;" />
FILTER: pcre install prefix<br style="margin:0px;padding:0px;" />
<span style="margin:0px;padding:0px;color:#FF0000;font-family:&quot;font-size:18px;">27.--disable-fileinfo&nbsp;</span><br style="margin:0px;padding:0px;" />
fileinfo在5.3以后就被默认安装的,小内存VPS上编译PHP会out of memory<br style="margin:0px;padding:0px;" />
Disable fileinfo support
</p>
<p style="margin:10px auto;padding:0px;font-family:&quot;font-weight:700;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;font-size:18px;font-family:&quot;color:#FF0000;">28.--enable-shared</span>=PKGS Build shared libraries default=yes<br style="margin:0px;padding:0px;" />
生成动态链接库<br style="margin:0px;padding:0px;" />
--enable-static=PKGS Build static libraries default=yes<br style="margin:0px;padding:0px;" />
生成静态链接库<br style="margin:0px;padding:0px;" />
<span style="margin:0px;padding:0px;color:#FF0000;font-family:&quot;font-size:18px;">29.--disable-ipv6 Disable IPv6 support</span><br style="margin:0px;padding:0px;" />
<span style="margin:0px;padding:0px;color:#FF0000;font-family:&quot;font-size:18px;">30.--enable-phpdbg</span>&nbsp;<br style="margin:0px;padding:0px;" />
轻量级、强大、易用的PHP调试平台,可以在PHP5.4和之上版本中使用,在php5.6和之上版本内部集成<br style="margin:0px;padding:0px;" />
Build phpdbg<br style="margin:0px;padding:0px;" />
<span style="margin:0px;padding:0px;color:#FF0000;font-size:18px;font-family:&quot;">31.--enable-fpm</span>&nbsp;Enable building of the fpm SAPI executable<br style="margin:0px;padding:0px;" />
--with-fpm-user=USER Set the user for php-fpm to run as. (default: nobody)<br style="margin:0px;padding:0px;" />
--with-fpm-group=GRP Set the group for php-fpm to run as. For a system user, this<br style="margin:0px;padding:0px;" />
should usually be set to match the fpm username (default: nobody)<br style="margin:0px;padding:0px;" />
<span style="margin:0px;padding:0px;color:#FF0000;font-size:18px;font-family:&quot;">32.--enable-posix</span><br style="margin:0px;padding:0px;" />
开启posix扩展支持<br style="margin:0px;padding:0px;" />
<span style="margin:0px;padding:0px;font-family:&quot;font-size:18px;color:#FF0000;">33.--enable-pcntl</span><br style="margin:0px;padding:0px;" />
开启pcntl扩展<br style="margin:0px;padding:0px;" />
<span style="margin:0px;padding:0px;font-family:&quot;font-size:18px;color:#FF0000;">34.--with-pear</span>=DIR Install PEAR in DIR [PREFIX/lib/php]<br style="margin:0px;padding:0px;" />
--without-pear Do not install PEAR
</p>