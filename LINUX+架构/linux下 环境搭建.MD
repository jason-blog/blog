======================================NGINX=====================================<br />
1.需要编译C库<br />
yum install gcc gcc-c++ ncurses-devel perl<br />
2.需要 PCRE<br />
&nbsp;./configure &nbsp;--prefix=/usr/local/pcre<br />
&nbsp;make&nbsp;<br />
&nbsp;make install<br />
&nbsp;<br />
3.需要 OpenSSL<br />
yum -y install openssl openssl-devel<br />
<br />
4.安装<br />
<br />
nginx<br />
./configure --user=nginx --group=nginx --prefix=/usr/local/nginx &nbsp;--with-pcre=/home/jsonSpade/pcre-8.12 --with-pcre --with-http_stub_status_module --with-http_ssl_module<br />
<br />
/////注意这里的--with-pcre= 是源码目录<br />
make<br />
make install<br />
<br />
nginx: [emerg] getpwnam("nginx") failed //是用户和用户组不存在<br />
<br />
groupadd nginx<br />
useradd -s /home/nginx -g nginx nginx<br />
<br />
=====================================MYSQL======================================<br />
<br />
<br />
新版mysql用cmake编译需要 yum install cmake<br />
<br />
<br />
cmake -DCMAKE_INSTALL_PREFIX=/usr/local/mysql/mysql -DMYSQL_DATADIR=/usr/local/mysql/data -DSYSCONFDIR=/etc -DWITH_MYISAM_STORAGE_ENGINE=1 -DWITH_INNOBASE_STORAGE_ENGINE=1 -DWITH_MEMORY_STORAGE_ENGINE=1 -DWITH_READLINE=1 -DMYSQL_UNIX_ADDR=/tmp/mysqld.sock -DMYSQL_TCP_PORT=3306 -DENABLED_LOCAL_INFILE=1 &nbsp;-DWITH_PARTITION_STORAGE_ENGINE=1 -DEXTRA_CHARSETS=all -DDEFAULT_CHARSET=utf8 -DDEFAULT_COLLATION=utf8_general_ci<br />
<br />
make &amp;&amp; make install<br />
<br />
//mysql_install_db 需要perl<br />
yum install -y perl-Module-Install.noarch<br />
<br />
<br />
<br />
cd /usr/local/mysql/mysql<br />
chown -R mysql:mysql .<br />
cd /opt/mysql-5.6.19<br />
cp support-files/my-default.cnf /etc/my.cnf<br />
cp support-files/mysql.server /etc/init.d/mysqld<br />
chmod 755 /etc/init.d/mysqld<br />
mkdir -p /mysql/data<br />
chown -R mysql:mysql /mysql/data<br />
/usr/local/mysql/mysql/mysql_install_db --user=mysql --basedir=/usr/local/mysql/mysql/ --datadir=/usr/local/mysql/data/<br />
<br />
<br />
service mysqld start<br />
<br />
/mysql/3306/bin/mysql -u root -p<br />
<br />
/*****<br />
my.cnf **<br />
******<br />
*<br />
*[mysqld]<br />
<br />
datadir=/usr/local/mysql/data<br />
socket=/tmp/mysql.sock<br />
<br />
[mysql.server]<br />
user=mysql<br />
basedir=/usr/local/mysql/mysql<br />
<br />
<br />
[client]<br />
socket=/tmp/mysql.sock<br />
<br />
#symbolic-links=0<br />
<br />
[mysqld_safe]<br />
log-error=/var/log/mysqld.log<br />
pid-file=/tmp/mysqld.pid<br />
*<br />
*<br />
*<br />
*<br />
*/<br />
<br />
<br />
//安全模式<br />
/mysql/3306/bin/mysqld_safe --skip-grant-tables &amp;&nbsp;<br />
<br />
<br />
//创建测试用户<br />
GRANT ALL PRIVILEGES ON *.* TO 'jason'@'%' IDENTIFIED BY '' WITH GRANT OPTION;<br />
flush privileges;<br />
<br />
<br />
===================================PHP=======================================<br />
<br />
<br />
//编译时可能提示curl不存在&nbsp;<br />
yum -y install curl-devel<br />
&nbsp;<br />
/////////////////////////////////////////////////需要安装的库///////////////////////////&nbsp;<br />
&nbsp;1.安装libxml2<br />
cd /usr/local/src/<br />
tar zxvf libxml2-2.6.30.tar.gz<br />
cd libxml2-2.6.30<br />
./configure --prefix=/usr/local/libxml2<br />
make &amp;&amp; make install<br />
&nbsp;<br />
2.安装libmcrypt、zlib、libpng、freetype<br />
安装方法同libxml2，分别安装到如下路径<br />
/usr/local/libmcrypt<br />
/usr/local/zlib<br />
/usr/local/libpng<br />
/usr/local/freetype<br />
&nbsp;<br />
注意，安装freetype时有可能提示如下错误：<br />
&nbsp;either set the LIBPNG_CFLAGS and LIBPNG_LDFLAGS environment variables<br />
&nbsp;<br />
这是提示找不到libpng的安装位置，所以需要将libpng的bin目录配置到环境变量中：<br />
解决方法：<br />
编辑：vi /etc/profile<br />
LIB_PNG=/usr/local/libpng/bin<br />
PATH=$LIB_PNG:$PATH &nbsp;<br />
export PATH&nbsp;<br />
<br />
<br />
生效：. &nbsp;/etc/profile 或 source /etc/profile<br />
&nbsp;<br />
重新安装freetype即可。<br />
&nbsp;<br />
3.安装jpeg9<br />
mkdir /usr/local/jpeg9<br />
mkdir /usr/local/jpeg9/bin<br />
mkdir /usr/local/jpeg9/lib<br />
mkdir /usr/local/jpeg9/include<br />
mkdir -p /usr/local/jpeg9/man/man1<br />
cd /usr/local/src/<br />
tar zxvf jpegsrc.v9.tar.gz<br />
cd jpeg-9<br />
./configure \<br />
&gt; --prefix=/usr/local/jpeg9/ \&nbsp;<br />
&gt; --enable-shared \ //建立共享库使用的GNU 的libtool<br />
&gt; --enable-static //建立静态库使用的GNU 的libtool<br />
make &amp;&amp; make install<br />
<br />
4.安装autoconf<br />
&nbsp;yum install autoconf<br />
&nbsp;<br />
&nbsp;<br />
&nbsp;<br />
&nbsp;5.安装GD<br />
cd /usr/local/src/<br />
tar zxvf libgd-2.1.0.tar.gz<br />
cd libgd-2.1.0<br />
./configure \ //配置命令<br />
&gt; --prefix=/usr/local/gd2/ \ //指定软件安装的位置<br />
&gt; --with-zlib=/usr/local/zlib/ \ //指定到哪去找zlib 库文件的位置<br />
&gt; --with-jpeg=/usr/local/jpeg9/ \ //指定到哪去找jpeg 库文件的位置<br />
&gt; --with-png=/usr/local/libpng/ \ //指定到哪去找png 库文件的位置<br />
&gt; --with-freetype=/usr/local/freetype/ //指定到哪去找freetype 2.x 字体库的位置<br />
make &amp;&amp; make install<br />
<br />
<br />
<br />
//////这一步没有做<br />
接下来就都是重点了<br />
问题1：<br />
按照以上配置，make时可能报如下错误：<br />
/usr/local/src/php-5.5.6/ext/gd/gd.c:57:22: error: X11/xpm.h: No such file or directory<br />
make: *** [ext/gd/gd.lo] Error 1<br />
问题说明：这是提示gd库不支持xpm<br />
解决方法：<br />
1.安装libxpm<br />
yum install libXpm-devel.x86_64<br />
&nbsp;<br />
2.按照上面的方法重新安装gd库<br />
安装成功后会看到如下信息，说明gd已经支持xpm了：<br />
** Configuration summary for libgd 2.1.0:<br />
&nbsp;<br />
&nbsp; &nbsp;Support for Zlib: &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; yes<br />
&nbsp; &nbsp;Support for PNG library: &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;yes<br />
&nbsp; &nbsp;Support for JPEG library: &nbsp; &nbsp; &nbsp; &nbsp; yes<br />
&nbsp; &nbsp;Support for VPX library: &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;no<br />
&nbsp; &nbsp;Support for TIFF library: &nbsp; &nbsp; &nbsp; &nbsp; no<br />
&nbsp; &nbsp;Support for Freetype 2.x library: yes<br />
&nbsp; &nbsp;Support for Fontconfig library: &nbsp; no<br />
&nbsp; &nbsp;Support for Xpm library: &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;yes<br />
&nbsp; &nbsp;Support for pthreads: &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; yes<br />
&nbsp;<br />
3.再次按照上面的方法安装php：<br />
问题2：<br />
报错：<br />
ext/gd/gd.c:1330: undefined reference to `XpmLibraryVersion'<br />
问题说明：没有找到xpm库的安装位置<br />
解决方法：<br />
1.rpm -ql libXpm ：查询出libXpm的安装位置，发现在/usr/lib64/ 下<br />
2.重新编译php，./configure中增加 --with-xpm-dir=/usr/lib64/&nbsp;<br />
3.make &amp;&amp; make install 成功！<br />
<br />
//////////////////<br />
/////////////////////////////////////////////////需要安装的库 END///////////////////////////&nbsp;<br />
<br />
<br />
#./configure --prefix=/usr/local/php -with-vpx-dir=/ --with-config-file-path=/usr/local/php --with-mysql=/mysql/3306 --with-iconv=/usr --with-mysqli=/mysql/3306/bin/mysql_config --with-pdo-mysql=/mysql/3306 --with-freetype-dir --with-jpeg-dir --with-png-dir --with-zlib --with-libxml-dir=/usr/local/libxml2.2 --enable-xml --disable-rpath --enable-discard-path --enable-inline-optimization --with-curl --enable-mbregex --enable-mbstring --with-mcrypt=/usr/local/libmcrypt --with-gd --enable-gd-native-ttf --with-openssl --with-mhash --enable-ftp --enable-fpm --enable-bcmath --enable-exif --enable-sockets --enable-zip&nbsp;<br />
<br />
//最终编译配置<br />
./configure --prefix=/usr/local/php --with-config-file-path=/usr/local/php/etc --with-libxml-dir=/usr/local/libxml2/ --with-png-dir=/usr/local/libpng/ --with-jpeg-dir=/usr/local/jpeg9/ --with-freetype-dir=/usr/local/freetype/ --with-gd &nbsp;--with-zlib-dir=/usr/local/zlib/ --with-mcrypt=/usr/local/libmcrypt/ --with-mysql --with-mysqli --enable-soap &nbsp;--enable-mbstring=all --enable-sockets --enable-pdo --with-pdo-mysql --with-curl --with-openssl --with-mhash --enable-ftp --enable-fpm --enable-bcmath --enable-exif --enable-sockets --enable-zip&nbsp;<br />
<br />
#./configure --prefix=/usr/local/php7 --with-config-file-path=/usr/local/php7/etc --with-libxml-dir=/usr/local/libxml2/ --with-png-dir=/usr/local/libpng/ --with-jpeg-dir=/usr/local/jpeg9/ --with-freetype-dir=/usr/local/freetype/ --with-gd &nbsp;--with-zlib-dir=/usr/local/zlib/ --with-mcrypt=/usr/local/libmcrypt/ --with-mysql --with-mysqli --enable-soap &nbsp;--enable-mbstring=all --enable-sockets --enable-pdo --with-pdo-mysql --with-curl --with-openssl --with-mhash --enable-ftp --enable-fpm --enable-bcmath --enable-exif --enable-sockets --enable-zip&nbsp;<br />
<br />
//apache需要<br />
#--with-apxs2=/www/wdlinux/apache/bin/apxs<br />
<br />
<br />
################<br />
设置时区<br />
<br />
<br />
时区的配置文件是/etc/sysconfig/clock。用tzselect命令就可以修改这个配置文件，根据命令的提示进行修改就好了。<br />
&nbsp;<br />
但是在实际工作中，发现这种方式是不能够使得服务器上的时间设置马上生效的，而且使用ntpdate去同步时间服务器也不能够更改时间。即使你使用了 date命令手工设置了时间的话，如果使用ntpdate去进行时间同步的话，时间又会被改动到原来的错误时区的时间。而生产的机器往往是非常重要的，不能够进行重启等操作。<br />
&nbsp;<br />
如果要修改时区并且马上生效，可以更换/etc/localtime 文件来实现。比如修改时区为中国上海，那么就可以使用如下的命令来使得时区的更改生效。<br />
&nbsp;<br />
cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime<br />
&nbsp;<br />
然后最好使用下面的命令将更改写入bios。<br />
&nbsp;<br />
hwclock<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
/////////////////apache安装未测试///////////////<br />
<br />
./configure --prefix=/usr/local/apache2 --with-apr=/usr/local/apr --with-apr-util=/usr/local/apr-util/ --with-pcre=/usr/local/pcre （除了指定Apache的安装目录外，还要安装apr、apr-util、pcre，并指定参数）<br />
make<br />
make install<br />
<br />
<br />
1.解决apr not found问题<br />
<br />
&nbsp; [root@localhost bin]# tar -zxf apr-1.4.5.tar.gz<br />
&nbsp; [root@localhost apr-1.4.5]# ./configure --prefix=/usr/local/apr<br />
&nbsp; [root@localhost apr-1.4.5]# make<br />
&nbsp; [root@localhost apr-1.4.5]# make install<br />
&nbsp;&nbsp;<br />
&nbsp; 2.解决APR-util not found问题<br />
<br />
&nbsp; [root@localhost bin]# tar -zxf apr-util-1.3.12.tar.gz<br />
&nbsp; [root@localhost apr-util-1.3.12]# ./configure --prefix=/usr/local/apr-util -with-apr=/usr/local/apr/bin/apr-1-config<br />
&nbsp; [root@localhost apr-util-1.3.12]# make<br />
&nbsp; [root@localhost apr-util-1.3.12]# make install<br />
3、解决pcre-config for libpcre not found问题<br />
<br />
&nbsp; [root@localhost ~]# unzip pcre-8.31.zip<br />
&nbsp; [root@localhost ~]# cd pcre-8.31<br />
&nbsp; [root@localhost pcre-8.31]# ./configure --prefix=/usr/local/pcre<br />
&nbsp; [root@localhost pcre-8.31]# make[root@localhost pcre-8.31]# make install<br />
&nbsp;&nbsp;<br />
httpd.conf 添加&nbsp;<br />
<br />
<br />
LoadModule php5_module modues/libphp5.so<br />
<br />
<br />
AddType application/x-httpd-php .php<br />
AddType application/x-httpd-php-source .phps<br />
<br />
<br />