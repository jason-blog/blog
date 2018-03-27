<br style="white-space:normal;" />
<span style="white-space:normal;">=================================================================== &nbsp;</span><br style="white-space:normal;" />
<br style="white-space:normal;" />
<span style="white-space:normal;">一、安装PHP的MongoDB数据库扩展（在Web服务器192.168.21.127上操作）</span><br style="white-space:normal;" />
<br style="white-space:normal;" />
<span style="white-space:normal;">下载地址：http://pecl.php.net/get/mongo-1.5.1.tgz</span><br style="white-space:normal;" />
<br style="white-space:normal;" />
<span style="white-space:normal;">上传mongo-1.5.1.tgz到/usr/local/src目录</span><br style="white-space:normal;" />
<br style="white-space:normal;" />
<span style="white-space:normal;">tar &nbsp;zxvf mongo-1.5.1.tgz &nbsp;#解压</span><br style="white-space:normal;" />
<br style="white-space:normal;" />
<span style="white-space:normal;">cd mongo-1.5.1</span><br style="white-space:normal;" />
<br style="white-space:normal;" />
<span style="white-space:normal;">/usr/local/php/bin/phpize</span><br style="white-space:normal;" />
<br style="white-space:normal;" />
<span style="white-space:normal;">./configure --with-php-config=/usr/local/php/bin/php-config</span><br style="white-space:normal;" />
<br style="white-space:normal;" />
<span style="white-space:normal;">make &nbsp;#编译</span><br style="white-space:normal;" />
<br style="white-space:normal;" />
<span style="white-space:normal;">make install &nbsp;#安装，完成之后出现下面的界面</span><br style="white-space:normal;" />
<br style="white-space:normal;" />
<span style="white-space:normal;">/usr/local/php/lib/php/extensions/no-debug-non-zts-20090626/</span><br style="white-space:normal;" />
<br style="white-space:normal;" />
<span style="white-space:normal;">vi /usr/local/php/etc/php.ini &nbsp;#编辑，在最后一行添加下面的代码</span><br style="white-space:normal;" />
<br style="white-space:normal;" />
<span style="white-space:normal;">extension="mongo.so"</span><br style="white-space:normal;" />
<br style="white-space:normal;" />
<span style="white-space:normal;">:wq! #保存退出</span><br style="white-space:normal;" />
<br style="white-space:normal;" />
<span style="white-space:normal;">service php-fpm reload &nbsp;#重新加载php-fpm</span><br style="white-space:normal;" />
<br style="white-space:normal;" />
<span style="white-space:normal;">在站点根目录下添加php测试页面</span><br style="white-space:normal;" />
<br style="white-space:normal;" />
<span style="white-space:normal;">vi /usr/local/nginx/html/phpinfo.php &nbsp;#编辑</span><br style="white-space:normal;" />
<br style="white-space:normal;" />
<span style="white-space:normal;">&lt;?php</span><br style="white-space:normal;" />
<br style="white-space:normal;" />
<span style="white-space:normal;">phpinfo();</span><br style="white-space:normal;" />
<br style="white-space:normal;" />
<span style="white-space:normal;">?&gt;</span><br style="white-space:normal;" />
<br style="white-space:normal;" />
<span style="white-space:normal;">:wq! &nbsp;#保存退出</span><br style="white-space:normal;" />
<span style="white-space:normal;">=================================================================== &nbsp;</span><br style="white-space:normal;" />
<br style="white-space:normal;" />
<br style="white-space:normal;" />
<br style="white-space:normal;" />
<br style="white-space:normal;" />
<span style="white-space:normal;">php 链接</span><br style="white-space:normal;" />
<br style="white-space:normal;" />
<br style="white-space:normal;" />
<span style="white-space:normal;">六，php客户端连接</span><br style="white-space:normal;" />
<span style="white-space:normal;">1， 推荐方法一</span><br style="white-space:normal;" />
<br style="white-space:normal;" />
<span style="white-space:normal;">$mongo = new Mongo(); &nbsp;</span><br style="white-space:normal;" />
<span style="white-space:normal;">&nbsp;</span><br style="white-space:normal;" />
<span style="white-space:normal;">$db = $mongo-&gt;selectDB('tank'); &nbsp;//切换到tank数据库&nbsp;</span><br style="white-space:normal;" />
<span style="white-space:normal;">&nbsp;</span><br style="white-space:normal;" />
<span style="white-space:normal;">$db-&gt;authenticate("tank3", "test"); &nbsp;//认证</span><br style="white-space:normal;" />
<span style="white-space:normal;">&nbsp;</span><br style="white-space:normal;" />
<span style="white-space:normal;">$users= $db-&gt;selectCollection("users"); //选取users表</span><br style="white-space:normal;" />
<span style="white-space:normal;">&nbsp;</span><br style="white-space:normal;" />
<span style="white-space:normal;">$cursor = $users-&gt;find(); &nbsp;//读取数据</span><br style="white-space:normal;" />
<span style="white-space:normal;">&nbsp;</span><br style="white-space:normal;" />
<span style="white-space:normal;">foreach ($cursor as $id =&gt; $value) {</span><br style="white-space:normal;" />
<span style="white-space:normal;">&nbsp; echo "$id: "; print_r($value); echo "&lt;br&gt;";</span><br style="white-space:normal;" />
<span style="white-space:normal;">}</span><br style="white-space:normal;" />
<span style="white-space:normal;">这种方式比较好理解，根命令行下的操作过程差不多。</span><br style="white-space:normal;" />
<br style="white-space:normal;" />
<br style="white-space:normal;" />
<br style="white-space:normal;" />
<span style="white-space:normal;">2，推荐方法二</span><br style="white-space:normal;" />
<br style="white-space:normal;" />
<span style="white-space:normal;">$mongo = new Mongo("mongodb://tank3:test@127.0.0.1:27017/tank"); &nbsp;//认证用户，这里的数据库，只启认证作用</span><br style="white-space:normal;" />
<span style="white-space:normal;">&nbsp;</span><br style="white-space:normal;" />
<span style="white-space:normal;">$db = $mongo-&gt;selectDB('tank'); //选取数据库</span><br style="white-space:normal;" />
<span style="white-space:normal;">&nbsp;</span><br style="white-space:normal;" />
<span style="white-space:normal;">$users= $db-&gt;selectCollection("users");</span><br style="white-space:normal;" />
<span style="white-space:normal;">&nbsp;</span><br style="white-space:normal;" />
<span style="white-space:normal;">$cursor = $users-&gt;find();</span><br style="white-space:normal;" />
<span style="white-space:normal;">&nbsp;</span><br style="white-space:normal;" />
<span style="white-space:normal;">foreach ($cursor as $id =&gt; $value) {</span><br style="white-space:normal;" />
<span style="white-space:normal;">&nbsp; echo "$id: "; print_r($value); echo "&lt;br&gt;";</span><br style="white-space:normal;" />
<span style="white-space:normal;">}</span>