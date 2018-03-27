linux中查看nginx、apache、php、mysql配置文件路径的方法<br />
作者:phper163 / 时间: 2014-06-17 / 分类: Linux学习 / 浏览次数: 25597 / 0个评论发表评论<br />
如何在linux中查看nginx、apache、php、mysql配置文件路径了，如果你接收一个别人配置过的环境，但没留下相关文档。这时该怎么判断找到正确的加载文件路径了。可以通过以下来判断<br />
1、判断apache<br />
首先执行命令找到httpd路径<br />
ps aux | grep httpd<br />
如httpd路径为 /usr/local/apache/bin/httpd<br />
然后执行以下命令<br />
/usr/local/apache/bin/httpd -V | grep “SERVER_CONFIG_FILE”<br />
即可找到编译时加载的配置文件路径 httpd.conf<br />
-V 参数可以看到编译时配置的参数<br />
2、判断nginx<br />
首先执行命令找到nginx路径<br />
ps aux | grep nginx<br />
如nginx路径为<br />
/usr/local/nginx/sbin/nginx<br />
然后执行以下命令<br />
/usr/local/nginx/sbin/nginx -V<br />
默认放在 安装目录下 conf/nginx.conf<br />
3、判断mysql<br />
首先执行命令找到mysql路径<br />
ps aux | grep mysqld<br />
如mysqld路径为<br />
/usr/bin/mysql<br />
然后执行以下命令<br />
/usr/bin/mysql –verbose –help | grep -A 1 ‘Default options’<br />
或<br />
/usr/bin/mysql –print-defaults<br />
4、判断php加载的配置文件路径<br />
（1）、可通过php函数phpinfo来查看，写个文件，然后用网址访问一下，查找“Loaded Configuration File”对应的值即为php加载的配置文件<br />
（2）、如果是nginx+php配置，也可以通过查找php执行路径<br />
ps aux | grep php<br />
如，路径为 /usr/local/nginx/sbin/php-fpm<br />
然后执行以下命令<br />
/usr/local/nginx/sbin/php-fpm -i | grep “Loaded Configuration File”<br />
即可看到php加载的配置文件<br />
(3)、如果是apache+mod_php配置，也可以在apache配置文件中查看加载的php.ini路径。如 PHPIniDir “/usr/local/apache/conf/php.ini”<br />
当然也有简单的方法，就是通过find来搜索<br />
如<br />
find / -name nginx.conf<br />
find / -name php.ini<br />
find / -name my.cnf<br />
find / -name httpd.conf<br />