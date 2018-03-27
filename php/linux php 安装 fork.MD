pcntl扩展可以支持php的多线程操作（仅限linux）<br />
原本需要重新编译PHP的后面configrue提示加上--enable-pcnt<br />
<br />
由于我的php是采用yum安装的，所以不能采用上面的方式<br />
下面介绍一个php动态添加扩展的方式 phpize<br />
<br />
1、首先看下 phpize命令 所在的目录 &nbsp;（ps：我的目录/usr/bin/phpize）<br />
如果没有找到的话 执行安装<br />
yum install php53_devel &nbsp; （ps：请注意自己的版本)<br />
安装完毕后。会生成phpize命令 &nbsp;&nbsp;<br />
<br />
2、去php.net下载相应版本的php源文件<br />
咱们以php-5.3.17 为例吧，解压后，进入相应的模块下<br />
cd ext/pcntl<br />
#先执行phpize<br />
/usr/bin/phpize<br />
./configure --with-php-config=/usr/bin/php-config &nbsp; （ps:请正确的指定php-config的目录）<br />
#编译、安装<br />
make &amp;&amp; make install<br />
<br />
这时候出了一个错误<br />
<br />
./configure编译正常，但make出错<br />
error: ‘PHP_FE_END’ undeclared here (not in a function)<br />
<br />
解决方法：<br />
<br />
源代码有错误，进入php-5.3.17目录<br />
sed -i 's|PHP_FE_END|{NULL,NULL,NULL}|' ./ext/**/*.c<br />
sed -i 's|ZEND_MOD_END|{NULL,NULL,NULL}|' ./ext/**/*.c<br />
再重新make &amp;&amp; make install<br />
<br />
3、编译完毕后会生成了一个 &nbsp;pcntl.so的文件。在php的model目录里<br />
<br />
编辑/etc/php.ini，加入<br />
extension=pcntl.so<br />
<br />
4、重启apache<br />
<br />
service httpd restart<br />
<br />
5、测试是否安装成功<br />
<br />
&lt;?php<br />
&nbsp; &nbsp; echo pcntl_fork();<br />
?&gt;<br />
<br />
输出：23165<br />