<p style="margin:10px auto;padding:0px;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	参考文档：<br style="margin:0px;padding:0px;" />
<a href="http://www.cnblogs.com/phpinfo/p/4104551.html" target="_blank" style="margin:0px;padding:0px;color:black;">http://www.cnblogs.com/phpinfo/p/4104551...</a><br style="margin:0px;padding:0px;" />
<a href="http://blog.csdn.net/historyasamirror/article/details/6827870" target="_blank" style="margin:0px;padding:0px;color:black;">http://blog.csdn.net/historyasamirror/ar...</a>
</p>
<h2 id="articleHeader0" style="margin:10px 0px;padding:0px;font-size:21px;line-height:1.5;font-family:Verdana, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
	依赖包安装
</h2>
<pre class="hljs sql" style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-size:14px;background-color:#FFFFFF;"><code style="margin:0px;padding:0px;">yum&nbsp;<span class="hljs-operator" style="margin:0px;padding:0px;"><span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">install&nbsp;ncurses-devel unixODBC unixODBC-devel</span></span></code></pre>
<h2 id="articleHeader1" style="margin:10px 0px;padding:0px;font-size:21px;line-height:1.5;font-family:Verdana, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
	erlang环境
</h2>
<pre class="hljs nginx" style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-size:14px;background-color:#FFFFFF;"><code style="margin:0px;padding:0px;"><span class="hljs-title" style="margin:0px;padding:0px;color:#A31515;">wget <span class="hljs-url" style="margin:0px;padding:0px;">http://erlang.org/download/otp_src_18.1.tar.gz
tar -zxvf otp_src_18.<span class="hljs-number" style="margin:0px;padding:0px;">1.tar.gz
cd otp_src_18.<span class="hljs-number" style="margin:0px;padding:0px;">1
./configure --prefix=/usr/local/erlang
make
make install <span class="hljs-comment" style="margin:0px;padding:0px;color:green;"># 配置erlang环境变量
vim /etc/profile <span class="hljs-comment" style="margin:0px;padding:0px;"># 增加内容：
export PATH=<span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">"<span class="hljs-variable" style="margin:0px;padding:0px;color:green;">$PATH:/usr/local/erlang/bin" <span class="hljs-comment" style="margin:0px;padding:0px;"># 保存退出，并刷新变量
source /etc/profile <span class="hljs-comment" style="margin:0px;padding:0px;"># 测试erlang是否安装成功 <span class="hljs-comment" style="margin:0px;padding:0px;"># 安装完成以后，执行erl看是否能打开eshell，用’halt().’退出，注意后面的点号，那是erlang的结束符。
[root<span class="hljs-variable" style="margin:0px;padding:0px;">@localhost src]<span class="hljs-comment" style="margin:0px;padding:0px;"># erl 
Erlang/OTP <span class="hljs-number" style="margin:0px;padding:0px;">17 [erts-<span class="hljs-number" style="margin:0px;padding:0px;">6.<span class="hljs-number" style="margin:0px;padding:0px;">1] [source] [<span class="hljs-number" style="margin:0px;padding:0px;">64-bit] [async-threads:<span class="hljs-number" style="margin:0px;padding:0px;">10] [hipe] [kernel-<span class="hljs-built_in" style="margin:0px;padding:0px;color:#0000FF;">poll:<span class="hljs-built_in" style="margin:0px;padding:0px;">false]

Eshell V6.<span class="hljs-number" style="margin:0px;padding:0px;">1  (abort with<span class="hljs-regexp" style="margin:0px;padding:0px;"> ^G) <span class="hljs-number" style="margin:0px;padding:0px;">2&gt; <span class="hljs-number" style="margin:0px;padding:0px;">9+<span class="hljs-number" style="margin:0px;padding:0px;">3. <span class="hljs-number" style="margin:0px;padding:0px;">12 <span class="hljs-number" style="margin:0px;padding:0px;">3&gt; halt(). </span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></code></pre>
<h2 id="articleHeader2" style="margin:10px 0px;padding:0px;font-size:21px;line-height:1.5;font-family:Verdana, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
	安装rabbitmq依赖文件,安装rabbitmq
</h2>
<pre class="hljs sql" style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-size:14px;background-color:#FFFFFF;"><code style="margin:0px;padding:0px;"># 安装rabbitmq依赖包
yum <span class="hljs-operator" style="margin:0px;padding:0px;"><span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">install xmlto

# 安装rabbitmq服务端
wget http://www.rabbitmq.com/releases/rabbitmq-<span class="hljs-keyword" style="margin:0px;padding:0px;">server/v3<span class="hljs-number" style="margin:0px;padding:0px;">.5<span class="hljs-number" style="margin:0px;padding:0px;">.7/rabbitmq-<span class="hljs-keyword" style="margin:0px;padding:0px;">server-<span class="hljs-number" style="margin:0px;padding:0px;">3.5<span class="hljs-number" style="margin:0px;padding:0px;">.7.tar.gz
tar zxvf rabbitmq-<span class="hljs-keyword" style="margin:0px;padding:0px;">server-<span class="hljs-number" style="margin:0px;padding:0px;">3.5<span class="hljs-number" style="margin:0px;padding:0px;">.7.tar.gz
cd rabbitmq-<span class="hljs-keyword" style="margin:0px;padding:0px;">server-<span class="hljs-number" style="margin:0px;padding:0px;">3.5<span class="hljs-number" style="margin:0px;padding:0px;">.7/
make
make <span class="hljs-keyword" style="margin:0px;padding:0px;">install TARGET_DIR=/usr/<span class="hljs-keyword" style="margin:0px;padding:0px;">local/rabbitmq SBIN_DIR=/usr/<span class="hljs-keyword" style="margin:0px;padding:0px;">local/rabbitmq/sbin MAN_DIR=/usr/<span class="hljs-keyword" style="margin:0px;padding:0px;">local/rabbitmq/man DOC_INSTALL_DIR=/usr/<span class="hljs-keyword" style="margin:0px;padding:0px;">local/rabbitmq/doc

# 配置<span class="hljs-keyword" style="margin:0px;padding:0px;">hosts
vim /etc/<span class="hljs-keyword" style="margin:0px;padding:0px;">hosts
# 增加一行内容
# 当前IP地址   绑定HOSTNAME名称(vim /etc/sysconfig/network) <span class="hljs-number" style="margin:0px;padding:0px;">192.168<span class="hljs-number" style="margin:0px;padding:0px;">.2<span class="hljs-number" style="margin:0px;padding:0px;">.208 localhost.localdomain

# 这种会提示错误(Warning: PID file <span class="hljs-keyword" style="margin:0px;padding:0px;">not written; -detached was passed.)
/usr/local/rabbitmq/sbin/rabbitmq-server -detached 启动rabbitmq
/usr/local/rabbitmq/sbin/rabbitmqctl status 查看状态
/usr/local/rabbitmq/sbin/rabbitmqctl <span class="hljs-operator" style="margin:0px;padding:0px;"><span class="hljs-keyword" style="margin:0px;padding:0px;">stop 关闭rabbitmq

# 目前我自己使用
/usr/<span class="hljs-keyword" style="margin:0px;padding:0px;">local/rabbitmq/sbin/rabbitmq-<span class="hljs-keyword" style="margin:0px;padding:0px;">server <span class="hljs-keyword" style="margin:0px;padding:0px;">start &amp; 启动rabbitmq
/usr/<span class="hljs-keyword" style="margin:0px;padding:0px;">local/rabbitmq/sbin/rabbitmqctl <span class="hljs-keyword" style="margin:0px;padding:0px;">status 查看状态
/usr/<span class="hljs-keyword" style="margin:0px;padding:0px;">local/rabbitmq/sbin/rabbitmqctl <span class="hljs-keyword" style="margin:0px;padding:0px;">stop 关闭rabbitmq</span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></code></pre>
<h2 id="articleHeader3" style="margin:10px 0px;padding:0px;font-size:21px;line-height:1.5;font-family:Verdana, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
	启用管理插件
</h2>
<pre class="hljs perl" style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-size:14px;background-color:#FFFFFF;"><code style="margin:0px;padding:0px;"><span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">mkdir /etc/rabbitmq
/usr/<span class="hljs-keyword" style="margin:0px;padding:0px;">local/rabbitmq/sbin/rabbitmq-plugins list 查看插件列表
/usr/<span class="hljs-keyword" style="margin:0px;padding:0px;">local/rabbitmq/sbin/rabbitmq-plugins enable rabbitmq_management  (启用插件)
/usr/<span class="hljs-keyword" style="margin:0px;padding:0px;">local/rabbitmq/sbin/rabbitmq-plugins disable rabbitmq_management (禁用插件) <span class="hljs-comment" style="margin:0px;padding:0px;color:green;"># 重启rabbitmq <span class="hljs-comment" style="margin:0px;padding:0px;"># 访问 http://127.0.0.1:15672/ <span class="hljs-comment" style="margin:0px;padding:0px;"># 如果有iptables
vim /etc/sysconfig/iptables <span class="hljs-comment" style="margin:0px;padding:0px;"># 增加一下内容
-A INPUT -<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">m <span class="hljs-keyword" style="margin:0px;padding:0px;">state --<span class="hljs-keyword" style="margin:0px;padding:0px;">state NEW -<span class="hljs-keyword" style="margin:0px;padding:0px;">m tcp -p tcp --dport <span class="hljs-number" style="margin:0px;padding:0px;">15672 -j ACCEPT <span class="hljs-comment" style="margin:0px;padding:0px;color:green;"># 重启动iptable
service iptables restart</span></span></span></span></span></span></span></span></span></span></span></span></span></span></code></pre>
<h3 id="articleHeader4" style="margin:10px 0px;padding:0px;font-size:16px;line-height:1.5;font-family:Verdana, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
	开机自启动配置
</h3>
<pre class="hljs bash" style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-size:14px;background-color:#FFFFFF;"><code style="margin:0px;padding:0px;"><span class="hljs-shebang" style="margin:0px;padding:0px;">#!/bin/sh <span class="hljs-comment" style="margin:0px;padding:0px;color:green;">#start rabbitMq
sudo /usr/<span class="hljs-built_in" style="margin:0px;padding:0px;color:#0000FF;">local/rabbitmq/sbin/rabbitmq-server &amp; &gt; /usr/<span class="hljs-built_in" style="margin:0px;padding:0px;">local/rabbitmq/logs/rabbitmq.log <span class="hljs-number" style="margin:0px;padding:0px;">2&gt;&amp;<span class="hljs-number" style="margin:0px;padding:0px;">1 </span></span></span></span></span></span></code></pre>
<h2 id="articleHeader5" style="margin:10px 0px;padding:0px;font-size:21px;line-height:1.5;font-family:Verdana, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
	RabbitMQ PHP扩展安装
</h2>
<pre class="hljs bash" style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-size:14px;background-color:#FFFFFF;"><code style="margin:0px;padding:0px;"><span class="hljs-comment" style="margin:0px;padding:0px;color:green;"># 安装rabbitmq-c依赖包
yum install libtool autoconf <span class="hljs-comment" style="margin:0px;padding:0px;"># 安装rabbitmq-c ( 最好下载 0.5的，0.6安装可能会报错) <span class="hljs-comment" style="margin:0px;padding:0px;"># 版本下载：https://github.com/alanxz/rabbitmq-c/releases/tag/v0.5.0
wget https://github.com/alanxz/rabbitmq-c/releases/download/v0.<span class="hljs-number" style="margin:0px;padding:0px;">5.0/rabbitmq-c-<span class="hljs-number" style="margin:0px;padding:0px;">0.5.<span class="hljs-number" style="margin:0px;padding:0px;">0.tar.gz
tar -zxvf v0.<span class="hljs-number" style="margin:0px;padding:0px;">5.0 <span class="hljs-built_in" style="margin:0px;padding:0px;color:#0000FF;">cd rabbitmq-c-<span class="hljs-number" style="margin:0px;padding:0px;">0.5.<span class="hljs-number" style="margin:0px;padding:0px;">0/
autoreconf -i
./configure --prefix=/usr/<span class="hljs-built_in" style="margin:0px;padding:0px;">local/rabbitmq-c
make
make install <span class="hljs-comment" style="margin:0px;padding:0px;color:green;"># 安装PHP扩展 amqp
wget http://pecl.php.net/get/amqp-<span class="hljs-number" style="margin:0px;padding:0px;">1.6.<span class="hljs-number" style="margin:0px;padding:0px;">1.tgz
tar zxvf amqp-<span class="hljs-number" style="margin:0px;padding:0px;">1.6.<span class="hljs-number" style="margin:0px;padding:0px;">1.tgz <span class="hljs-built_in" style="margin:0px;padding:0px;color:#0000FF;">cd amqp-<span class="hljs-number" style="margin:0px;padding:0px;">1.6.<span class="hljs-number" style="margin:0px;padding:0px;">1
/usr/<span class="hljs-built_in" style="margin:0px;padding:0px;">local/php/bin/phpize
./configure --with-php-config=/usr/<span class="hljs-built_in" style="margin:0px;padding:0px;">local/php/bin/php-config --with-amqp --with-librabbitmq-dir=/usr/<span class="hljs-built_in" style="margin:0px;padding:0px;">local/rabbitmq-c
make
make install <span class="hljs-comment" style="margin:0px;padding:0px;color:green;"># 编辑php.ini文件，增加amqp扩展支持
vim /usr/<span class="hljs-built_in" style="margin:0px;padding:0px;color:#0000FF;">local/php/etc/php.ini <span class="hljs-comment" style="margin:0px;padding:0px;color:green;"># 增加下面内容
; rabbitmq扩展支持
extension=amqp.so <span class="hljs-comment" style="margin:0px;padding:0px;"># 重启php-fpm
/etc/init.d/php-fpm restart</span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></code></pre>
<p style="margin:10px auto;padding:0px;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	验证是否成功 phpinfo()查看下是否支持amqp扩展<br style="margin:0px;padding:0px;" />
	<iframe id="iframe_0.13345288226682217" src="data:text/html;charset=utf8,%3Cstyle%3Ebody%7Bmargin:0;padding:0%7D%3C/style%3E%3Cimg%20id=%22img%22%20src=%22https://segmentfault.com/img/bVtNcE?_=5634342%22%20style=%22border:none;max-width:1576px%22%3E%3Cscript%3Ewindow.onload%20=%20function%20()%20%7Bvar%20img%20=%20document.getElementById('img');%20window.parent.postMessage(%7BiframeId:'iframe_0.13345288226682217',width:img.width,height:img.height%7D,%20'http://www.cnblogs.com');%7D%3C/script%3E" frameborder="0" scrolling="no" style="margin:0px;padding:0px;border-width:initial;border-style:none;width:800px;height:221px;">
	</iframe>
</p>
<hr style="margin:0px;padding:0px;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<h2 id="articleHeader6" style="margin:10px 0px;padding:0px;font-size:21px;line-height:1.5;font-family:Verdana, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
	相关配置
</h2>
<pre class="hljs cs" style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-size:14px;background-color:#FFFFFF;"><code style="margin:0px;padding:0px;">hostname mq <span class="hljs-comment" style="margin:0px;padding:0px;color:green;">// 设置hostname名称
vim /etc/sysconfig/network <span class="hljs-comment" style="margin:0px;padding:0px;">// 设置hostname
vim /etc/hosts <span class="hljs-comment" style="margin:0px;padding:0px;">// 编辑hosts
./rabbitmqctl add_user admin admin <span class="hljs-comment" style="margin:0px;padding:0px;">// 添加用户
./rabbitmqctl set_user_tags admin administrator <span class="hljs-comment" style="margin:0px;padding:0px;">// 添加admin 到 administrator分组
./rabbitmqctl set_permissions -p / admin <span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">"*." <span class="hljs-string" style="margin:0px;padding:0px;">"*." <span class="hljs-string" style="margin:0px;padding:0px;">"*." <span class="hljs-comment" style="margin:0px;padding:0px;color:green;">// 添加权限</span></span></span></span></span></span></span></span></span></code></pre>
<h2 id="articleHeader7" style="margin:10px 0px;padding:0px;font-size:21px;line-height:1.5;font-family:Verdana, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
	创建配置文件
</h2>
<pre class="hljs coffeescript" style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-size:14px;background-color:#FFFFFF;"><code style="margin:0px;padding:0px;"><span class="hljs-comment" style="margin:0px;padding:0px;color:green;">#在/usr/rabbitmq/sbin/rabbitmq-defaults 查看config文件路径 <span class="hljs-comment" style="margin:0px;padding:0px;"># 创建配置文件 
touch/usr/rabbitmq/sbin <span class="hljs-comment" style="margin:0px;padding:0px;">#vm_memory_high_watermark 内存低水位线，若低于该水位线，则开启流控机制,阻止所有请求，默认值是0.4，即内存总量的40%, <span class="hljs-comment" style="margin:0px;padding:0px;">#vm_memory_high_watermark_paging_ratio 内存低水位线的多少百分比开始通过写入磁盘文件来释放内存
vi /usr/rabbitmq/sbin/rabbitmq.config 输入
[
{rabbit, [{vm_memory_high_watermark_paging_ratio, <span class="hljs-number" style="margin:0px;padding:0px;">0.75},
         {vm_memory_high_watermark, <span class="hljs-number" style="margin:0px;padding:0px;">0.7}]}
].</span></span></span></span></span></span></code></pre>
<h2 id="articleHeader8" style="margin:10px 0px;padding:0px;font-size:21px;line-height:1.5;font-family:Verdana, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
	创建环境文件
</h2>
<pre class="hljs nginx" style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-size:14px;background-color:#FFFFFF;"><code style="margin:0px;padding:0px;"><span class="hljs-title" style="margin:0px;padding:0px;color:#A31515;">touch /etc/rabbitmq/rabbitmq-env.conf <span class="hljs-comment" style="margin:0px;padding:0px;color:green;">#输入
    RABBITMQ_NODENAME=FZTEC-<span class="hljs-number" style="margin:0px;padding:0px;">240088 节点名称
    RABBITMQ_NODE_IP_ADDRESS=<span class="hljs-number" style="margin:0px;padding:0px;">127.0.0.1 监听IP
    RABBITMQ_NODE_PORT=<span class="hljs-number" style="margin:0px;padding:0px;">5672 监听端口
    RABBITMQ_LOG_BASE=/data/rabbitmq/log 日志目录
    RABBITMQ_PLUGINS_DIR=/data/rabbitmq/plugins 插件目录
    RABBITMQ_MNESIA_BASE=/data/rabbitmq/mnesia 后端存储目录</span></span></span></span></span></code></pre>
<h2 id="articleHeader9" style="margin:10px 0px;padding:0px;font-size:21px;line-height:1.5;font-family:Verdana, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
	操作命令
</h2>
<pre class="hljs javascript" style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-size:14px;background-color:#FFFFFF;"><code style="margin:0px;padding:0px;"> 查看exchange信息
          /usr/rabbitmq/sbin/rabbitmqctl list_exchanges name type durable auto_delete <span class="hljs-built_in" style="margin:0px;padding:0px;color:#0000FF;">arguments

 查看队列信息
          /usr/rabbitmq/sbin/rabbitmqctl list_queues name durable auto_delete messages consumers me
  查看绑定信息
          /usr/rabbitmq/sbin/rabbitmqctl list_bindings
 查看连接信息
          /usr/rabbitmq/sbin/rabbitmqctl list_connections</span></code></pre>
<h2 id="articleHeader10" style="margin:10px 0px;padding:0px;font-size:21px;line-height:1.5;font-family:Verdana, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
	php的server端脚本
</h2>
<pre class="hljs bash" style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-size:14px;background-color:#FFFFFF;"><code style="margin:0px;padding:0px;">&lt;?php <span class="hljs-variable" style="margin:0px;padding:0px;color:green;">$routingkey=<span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">'key';
//设置你的连接 <span class="hljs-variable" style="margin:0px;padding:0px;color:green;">$conn_args = array(<span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">'host' =&gt; <span class="hljs-string" style="margin:0px;padding:0px;">'localhost', <span class="hljs-string" style="margin:0px;padding:0px;">'port' =&gt; <span class="hljs-string" style="margin:0px;padding:0px;">'5672', <span class="hljs-string" style="margin:0px;padding:0px;">'login' =&gt; <span class="hljs-string" style="margin:0px;padding:0px;">'guest', <span class="hljs-string" style="margin:0px;padding:0px;">'password' =&gt; <span class="hljs-string" style="margin:0px;padding:0px;">'guest'); <span class="hljs-variable" style="margin:0px;padding:0px;color:green;">$conn = new AMQPConnection(<span class="hljs-variable" style="margin:0px;padding:0px;">$conn_args); <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">if (<span class="hljs-variable" style="margin:0px;padding:0px;color:green;">$conn-&gt;connect()) { <span class="hljs-built_in" style="margin:0px;padding:0px;color:#0000FF;">echo <span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">"Established a connection to the broker \n";
} <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">else { <span class="hljs-built_in" style="margin:0px;padding:0px;">echo <span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">"Cannot connect to the broker \n ";
}
//你的消息 <span class="hljs-variable" style="margin:0px;padding:0px;color:green;">$message = json_encode(array(<span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">'Hello World3!',<span class="hljs-string" style="margin:0px;padding:0px;">'php3',<span class="hljs-string" style="margin:0px;padding:0px;">'c++3:'));
//创建channel <span class="hljs-variable" style="margin:0px;padding:0px;color:green;">$channel = new AMQPChannel(<span class="hljs-variable" style="margin:0px;padding:0px;">$conn);
//创建exchange <span class="hljs-variable" style="margin:0px;padding:0px;">$ex = new AMQPExchange(<span class="hljs-variable" style="margin:0px;padding:0px;">$channel); <span class="hljs-variable" style="margin:0px;padding:0px;">$ex-&gt;<span class="hljs-built_in" style="margin:0px;padding:0px;color:#0000FF;">setName(<span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">'exchange');//创建名字 <span class="hljs-variable" style="margin:0px;padding:0px;color:green;">$ex-&gt;<span class="hljs-built_in" style="margin:0px;padding:0px;color:#0000FF;">setType(AMQP_EX_TYPE_DIRECT); <span class="hljs-variable" style="margin:0px;padding:0px;color:green;">$ex-&gt;<span class="hljs-built_in" style="margin:0px;padding:0px;color:#0000FF;">setFlags(AMQP_DURABLE);
//<span class="hljs-variable" style="margin:0px;padding:0px;color:green;">$ex-&gt;<span class="hljs-built_in" style="margin:0px;padding:0px;color:#0000FF;">setFlags(AMQP_AUTODELETE);
//<span class="hljs-built_in" style="margin:0px;padding:0px;">echo <span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">"exchange status:".<span class="hljs-variable" style="margin:0px;padding:0px;color:green;">$ex-&gt;<span class="hljs-built_in" style="margin:0px;padding:0px;color:#0000FF;">declare(); <span class="hljs-built_in" style="margin:0px;padding:0px;">echo <span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">"exchange status:".<span class="hljs-variable" style="margin:0px;padding:0px;color:green;">$ex-&gt;<span class="hljs-built_in" style="margin:0px;padding:0px;color:#0000FF;">declareExchange(); <span class="hljs-built_in" style="margin:0px;padding:0px;">echo <span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">"\n"; <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">for(<span class="hljs-variable" style="margin:0px;padding:0px;color:green;">$i=<span class="hljs-number" style="margin:0px;padding:0px;">0;<span class="hljs-variable" style="margin:0px;padding:0px;">$i&lt;<span class="hljs-number" style="margin:0px;padding:0px;">100;<span class="hljs-variable" style="margin:0px;padding:0px;">$i++){ <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">if(<span class="hljs-variable" style="margin:0px;padding:0px;color:green;">$routingkey==<span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">'key2'){ <span class="hljs-variable" style="margin:0px;padding:0px;color:green;">$routingkey=<span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">'key';
        }<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">else{ <span class="hljs-variable" style="margin:0px;padding:0px;color:green;">$routingkey=<span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">'key2';
        } <span class="hljs-variable" style="margin:0px;padding:0px;color:green;">$ex-&gt;publish(<span class="hljs-variable" style="margin:0px;padding:0px;">$message,<span class="hljs-variable" style="margin:0px;padding:0px;">$routingkey);
}
/* <span class="hljs-variable" style="margin:0px;padding:0px;">$ex-&gt;publish(<span class="hljs-variable" style="margin:0px;padding:0px;">$message,<span class="hljs-variable" style="margin:0px;padding:0px;">$routingkey);
创建队列 <span class="hljs-variable" style="margin:0px;padding:0px;">$q = new AMQPQueue(<span class="hljs-variable" style="margin:0px;padding:0px;">$channel);
设置队列名字 如果不存在则添加 <span class="hljs-variable" style="margin:0px;padding:0px;">$q-&gt;<span class="hljs-built_in" style="margin:0px;padding:0px;color:#0000FF;">setName(<span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">'queue'); <span class="hljs-variable" style="margin:0px;padding:0px;color:green;">$q-&gt;<span class="hljs-built_in" style="margin:0px;padding:0px;color:#0000FF;">setFlags(AMQP_DURABLE | AMQP_AUTODELETE); <span class="hljs-built_in" style="margin:0px;padding:0px;">echo <span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">"queue status: ".<span class="hljs-variable" style="margin:0px;padding:0px;color:green;">$q-&gt;<span class="hljs-built_in" style="margin:0px;padding:0px;color:#0000FF;">declare(); <span class="hljs-built_in" style="margin:0px;padding:0px;">echo <span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">"\n"; <span class="hljs-built_in" style="margin:0px;padding:0px;color:#0000FF;">echo <span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">'queue bind: '.<span class="hljs-variable" style="margin:0px;padding:0px;color:green;">$q-&gt;<span class="hljs-built_in" style="margin:0px;padding:0px;color:#0000FF;">bind(<span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">'exchange',<span class="hljs-string" style="margin:0px;padding:0px;">'route.key');
将你的队列绑定到routingKey <span class="hljs-built_in" style="margin:0px;padding:0px;color:#0000FF;">echo <span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">"\n"; <span class="hljs-variable" style="margin:0px;padding:0px;color:green;">$channel-&gt;startTransaction(); <span class="hljs-built_in" style="margin:0px;padding:0px;color:#0000FF;">echo <span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">"send: ".<span class="hljs-variable" style="margin:0px;padding:0px;color:green;">$ex-&gt;publish(<span class="hljs-variable" style="margin:0px;padding:0px;">$message, <span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">'route.key'); //将你的消息通过制定routingKey发送 <span class="hljs-variable" style="margin:0px;padding:0px;color:green;">$channel-&gt;commitTransaction(); <span class="hljs-variable" style="margin:0px;padding:0px;">$conn-&gt;disconnect();
*/</span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></code></pre>
<h2 id="articleHeader11" style="margin:10px 0px;padding:0px;font-size:21px;line-height:1.5;font-family:Verdana, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
	php客户端脚本
</h2>
<pre class="hljs xml" style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-size:14px;background-color:#FFFFFF;"><code style="margin:0px;padding:0px;"><span class="php" style="margin:0px;padding:0px;"><span class="hljs-preprocessor" style="margin:0px;padding:0px;">&lt;?php <span class="hljs-variable" style="margin:0px;padding:0px;color:green;">$bindingkey=<span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">'key2'; <span class="hljs-comment" style="margin:0px;padding:0px;color:green;">//连接RabbitMQ <span class="hljs-variable" style="margin:0px;padding:0px;">$conn_args = <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">array( <span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">'host'=&gt;<span class="hljs-string" style="margin:0px;padding:0px;">'127.0.0.1' , <span class="hljs-string" style="margin:0px;padding:0px;">'port'=&gt; <span class="hljs-string" style="margin:0px;padding:0px;">'5672', <span class="hljs-string" style="margin:0px;padding:0px;">'login'=&gt;<span class="hljs-string" style="margin:0px;padding:0px;">'guest' , <span class="hljs-string" style="margin:0px;padding:0px;">'password'=&gt; <span class="hljs-string" style="margin:0px;padding:0px;">'guest',<span class="hljs-string" style="margin:0px;padding:0px;">'vhost' =&gt;<span class="hljs-string" style="margin:0px;padding:0px;">'/'); <span class="hljs-variable" style="margin:0px;padding:0px;color:green;">$conn = <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">new AMQPConnection(<span class="hljs-variable" style="margin:0px;padding:0px;color:green;">$conn_args); <span class="hljs-variable" style="margin:0px;padding:0px;">$conn-&gt;connect(); <span class="hljs-comment" style="margin:0px;padding:0px;">//设置queue名称，使用exchange，绑定routingkey <span class="hljs-variable" style="margin:0px;padding:0px;">$channel = <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">new AMQPChannel(<span class="hljs-variable" style="margin:0px;padding:0px;color:green;">$conn); <span class="hljs-variable" style="margin:0px;padding:0px;">$q = <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">new AMQPQueue(<span class="hljs-variable" style="margin:0px;padding:0px;color:green;">$channel); <span class="hljs-variable" style="margin:0px;padding:0px;">$q-&gt;setName(<span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">'queue2'); <span class="hljs-variable" style="margin:0px;padding:0px;color:green;">$q-&gt;setFlags(AMQP_DURABLE); <span class="hljs-variable" style="margin:0px;padding:0px;">$q-&gt;declare(); <span class="hljs-variable" style="margin:0px;padding:0px;">$q-&gt;bind(<span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">'exchange',<span class="hljs-variable" style="margin:0px;padding:0px;color:green;">$bindingkey); <span class="hljs-comment" style="margin:0px;padding:0px;">//消息获取 <span class="hljs-variable" style="margin:0px;padding:0px;">$messages = <span class="hljs-variable" style="margin:0px;padding:0px;">$q-&gt;get(AMQP_AUTOACK) ; <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">if (<span class="hljs-variable" style="margin:0px;padding:0px;color:green;">$messages){
var_dump(json_decode(<span class="hljs-variable" style="margin:0px;padding:0px;">$messages-&gt;getBody(), <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">true ));
} <span class="hljs-variable" style="margin:0px;padding:0px;color:green;">$conn-&gt;disconnect(); <span class="hljs-preprocessor" style="margin:0px;padding:0px;">?&gt;</span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></code></pre>
<h2 id="articleHeader12" style="margin:10px 0px;padding:0px;font-size:21px;line-height:1.5;font-family:Verdana, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
	翻译了部分mq常量设置,不正确的地方,大家以试验为准
</h2>
<div class="widget-codetool" style="margin:0px;padding:0px;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<button class="selectCode btn btn-xs" style="margin:0px;padding:0px;">全选</button><button class="copyCode btn btn-xs" title="" data-clipboard-text="/** * Passing in this constant as a flag will forcefully disable all other flags. * Use this if you want to temporarily disable the amqp.auto_ack ini setting. * 传递这个参数作为标志将完全禁用其他标志,如果你想临时禁用amqp.auto_ack设置起效 */ define('AMQP_NOPARAM', 0); /** * Durable exchanges and queues will survive a broker restart, complete with all of their data. * 持久化交换机和队列,当代理重启动后依然存在,并包括它们中的完整数据 */ define('AMQP_DURABLE', 2); /** * Passive exchanges and queues will not be redeclared, but the broker will throw an error if the exchange or queue does not exist. * 被动模式的交换机和队列不能被重新定义,但是如果交换机和队列不存在,代理将扔出一个错误提示 */ define('AMQP_PASSIVE', 4); /** * Valid for queues only, this flag indicates that only one client can be listening to and consuming from this queue. * 仅对队列有效,这个人标志定义队列仅允许一个客户端连接并且从其消费消息 */ define('AMQP_EXCLUSIVE', 8); /** * For exchanges, the auto delete flag indicates that the exchange will be deleted as soon as no more queues are bound * to it. If no queues were ever bound the exchange, the exchange will never be deleted. For queues, the auto delete * flag indicates that the queue will be deleted as soon as there are no more listeners subscribed to it. If no * subscription has ever been active, the queue will never be deleted. Note: Exclusive queues will always be * automatically deleted with the client disconnects. * 对交换机而言,自动删除标志表示交换机将在没有队列绑定的情况下被自动删除,如果从没有队列和其绑定过,这个交换机将不会被删除. * 对队列而言,自动删除标志表示如果没有消费者和你绑定的话将被自动删除,如果从没有消费者和其绑定,将不被删除,独占队列在客户断 * 开连接的时候将总是会被删除 */ define('AMQP_AUTODELETE', 16); /** * Clients are not allowed to make specific queue bindings to exchanges defined with this flag. * 这个标志标识不允许自定义队列绑定到交换机上 */ define('AMQP_INTERNAL', 32); /** * When passed to the consume method for a clustered environment, do not consume from the local node. * 在集群环境消费方法中传递这个参数,表示将不会从本地站点消费消息 */ define('AMQP_NOLOCAL', 64); /** * When passed to the {@link AMQPQueue::get()} and {@link AMQPQueue::get()} methods as a flag, * the messages will be immediately marked as acknowledged by the server upon delivery. * 当在队列get方法中作为标志传递这个参数的时候,消息将在被服务器输出之前标志为acknowledged (已收到) */ define('AMQP_AUTOACK', 128); /** * Passed on queue creation, this flag indicates that the queue should be deleted if it becomes empty. * 在队列建立时候传递这个参数,这个标志表示队列将在为空的时候被删除 */ define('AMQP_IFEMPTY', 256); /** * Passed on queue or exchange creation, this flag indicates that the queue or exchange should be * deleted when no clients are connected to the given queue or exchange. * 在交换机或者队列建立的时候传递这个参数,这个标志表示没有客户端连接的时候,交换机或者队列将被删除 */ define('AMQP_IFUNUSED', 512); /** * When publishing a message, the message must be routed to a valid queue. If it is not, an error will be returned. * 当发布消息的时候,消息必须被正确路由到一个有效的队列,否则将返回一个错误 */ define('AMQP_MANDATORY', 1024); /** * When publishing a message, mark this message for immediate processing by the broker. (High priority message.) * 当发布消息时候,这个消息将被立即处理. */ define('AMQP_IMMEDIATE', 2048); /** * If set during a call to {@link AMQPQueue::ack()}, the delivery tag is treated as &quot;up to and including&quot;, so that multiple * messages can be acknowledged with a single method. If set to zero, the delivery tag refers to a single message. * If the AMQP_MULTIPLE flag is set, and the delivery tag is zero, this indicates acknowledgement of all outstanding * messages. * 当在调用AMQPQueue::ack时候设置这个标志,传递标签将被视为最大包含数量,以便通过单个方法标示多个消息为已收到,如果设置为0 * 传递标签指向单个消息,如果设置了AMQP_MULTIPLE,并且传递标签是0,将所有未完成消息标示为已收到 */ define('AMQP_MULTIPLE', 4096); /** * If set during a call to {@link AMQPExchange::bind()}, the server will not respond to the method.The client should not wait * for a reply method. If the server could not complete the method it will raise a channel or connection exception. * 当在调用AMQPExchange::bind()方法的时候,服务器将不响应请求,客户端将不应该等待响应,如果服务器无法完成该方法,将会抛出一个异常 */ define('AMQP_NOWAIT', 8192); /** * If set during a call to {@link AMQPQueue::nack()}, the message will be placed back to the queue. * 如果在调用AMQPQueue::nack方法时候设置,消息将会被传递回队列 */ define('AMQP_REQUEUE', 16384); /** * A direct exchange type. * direct类型交换机 */ define('AMQP_EX_TYPE_DIRECT', 'direct'); /** * A fanout exchange type. * fanout类型交换机 */ define('AMQP_EX_TYPE_FANOUT', 'fanout'); /** * A topic exchange type. * topic类型交换机 */ define('AMQP_EX_TYPE_TOPIC', 'topic'); /** * A header exchange type. * header类型交换机 */ define('AMQP_EX_TYPE_HEADERS', 'headers'); /** * socket连接超时设置 */ define('AMQP_OS_SOCKET_TIMEOUT_ERRNO', 536870947);" data-toggle="tooltip" data-placement="bottom" style="margin:0px;padding:0px;">复制</button><button class="saveToNote btn btn-xs" style="margin:0px;padding:0px;">放进笔记</button>
</div>
<pre class="hljs cs" style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-size:14px;background-color:#FFFFFF;"><code style="margin:0px;padding:0px;"><span class="hljs-comment" style="margin:0px;padding:0px;color:green;">/**
 * Passing in this constant as a flag will forcefully disable all other flags.
 * Use this if you want to temporarily disable the amqp.auto_ack ini setting.
 * 传递这个参数作为标志将完全禁用其他标志,如果你想临时禁用amqp.auto_ack设置起效
 */
define(<span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">'AMQP_NOPARAM', <span class="hljs-number" style="margin:0px;padding:0px;">0); <span class="hljs-comment" style="margin:0px;padding:0px;color:green;">/**
 * Durable exchanges and queues will survive a broker restart, complete with all of their data.
 * 持久化交换机和队列,当代理重启动后依然存在,并包括它们中的完整数据
 */
define(<span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">'AMQP_DURABLE', <span class="hljs-number" style="margin:0px;padding:0px;">2); <span class="hljs-comment" style="margin:0px;padding:0px;color:green;">/**
 * Passive exchanges and queues will not be redeclared, but the broker will throw an error if the exchange or queue does not exist.
 * 被动模式的交换机和队列不能被重新定义,但是如果交换机和队列不存在,代理将扔出一个错误提示
 */
define(<span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">'AMQP_PASSIVE', <span class="hljs-number" style="margin:0px;padding:0px;">4); <span class="hljs-comment" style="margin:0px;padding:0px;color:green;">/**
 * Valid for queues only, this flag indicates that only one client can be listening to and consuming from this queue.
 * 仅对队列有效,这个人标志定义队列仅允许一个客户端连接并且从其消费消息
 */
define(<span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">'AMQP_EXCLUSIVE', <span class="hljs-number" style="margin:0px;padding:0px;">8); <span class="hljs-comment" style="margin:0px;padding:0px;color:green;">/**
 * For exchanges, the auto delete flag indicates that the exchange will be deleted as soon as no more queues are bound
 * to it. If no queues were ever bound the exchange, the exchange will never be deleted. For queues, the auto delete
 * flag indicates that the queue will be deleted as soon as there are no more listeners subscribed to it. If no
 * subscription has ever been active, the queue will never be deleted. Note: Exclusive queues will always be
 * automatically deleted with the client disconnects.
 * 对交换机而言,自动删除标志表示交换机将在没有队列绑定的情况下被自动删除,如果从没有队列和其绑定过,这个交换机将不会被删除.
 * 对队列而言,自动删除标志表示如果没有消费者和你绑定的话将被自动删除,如果从没有消费者和其绑定,将不被删除,独占队列在客户断
 * 开连接的时候将总是会被删除
 */
define(<span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">'AMQP_AUTODELETE', <span class="hljs-number" style="margin:0px;padding:0px;">16); <span class="hljs-comment" style="margin:0px;padding:0px;color:green;">/**
 * Clients are not allowed to make specific queue bindings to exchanges defined with this flag.
 * 这个标志标识不允许自定义队列绑定到交换机上
 */
define(<span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">'AMQP_INTERNAL', <span class="hljs-number" style="margin:0px;padding:0px;">32); <span class="hljs-comment" style="margin:0px;padding:0px;color:green;">/**
 * When passed to the consume method for a clustered environment, do not consume from the local node.
 * 在集群环境消费方法中传递这个参数,表示将不会从本地站点消费消息
 */
define(<span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">'AMQP_NOLOCAL', <span class="hljs-number" style="margin:0px;padding:0px;">64); <span class="hljs-comment" style="margin:0px;padding:0px;color:green;">/**
 * When passed to the {@link AMQPQueue::get()} and {@link AMQPQueue::get()} methods as a flag,
 * the messages will be immediately marked as acknowledged by the server upon delivery.
 * 当在队列get方法中作为标志传递这个参数的时候,消息将在被服务器输出之前标志为acknowledged (已收到)
 */
define(<span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">'AMQP_AUTOACK', <span class="hljs-number" style="margin:0px;padding:0px;">128); <span class="hljs-comment" style="margin:0px;padding:0px;color:green;">/**
 * Passed on queue creation, this flag indicates that the queue should be deleted if it becomes empty.
 * 在队列建立时候传递这个参数,这个标志表示队列将在为空的时候被删除
 */
define(<span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">'AMQP_IFEMPTY', <span class="hljs-number" style="margin:0px;padding:0px;">256); <span class="hljs-comment" style="margin:0px;padding:0px;color:green;">/**
 * Passed on queue or exchange creation, this flag indicates that the queue or exchange should be
 * deleted when no clients are connected to the given queue or exchange.
 * 在交换机或者队列建立的时候传递这个参数,这个标志表示没有客户端连接的时候,交换机或者队列将被删除
 */
define(<span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">'AMQP_IFUNUSED', <span class="hljs-number" style="margin:0px;padding:0px;">512); <span class="hljs-comment" style="margin:0px;padding:0px;color:green;">/**
 * When publishing a message, the message must be routed to a valid queue. If it is not, an error will be returned.
 * 当发布消息的时候,消息必须被正确路由到一个有效的队列,否则将返回一个错误
 */
define(<span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">'AMQP_MANDATORY', <span class="hljs-number" style="margin:0px;padding:0px;">1024); <span class="hljs-comment" style="margin:0px;padding:0px;color:green;">/**
 * When publishing a message, mark this message for immediate processing by the broker. (High priority message.)
 * 当发布消息时候,这个消息将被立即处理.
 */
define(<span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">'AMQP_IMMEDIATE', <span class="hljs-number" style="margin:0px;padding:0px;">2048); <span class="hljs-comment" style="margin:0px;padding:0px;color:green;">/**
 * If set during a call to {@link AMQPQueue::ack()}, the delivery tag is treated as "up to and including", so that multiple
 * messages can be acknowledged with a single method. If set to zero, the delivery tag refers to a single message.
 * If the AMQP_MULTIPLE flag is set, and the delivery tag is zero, this indicates acknowledgement of all outstanding
 * messages.
 * 当在调用AMQPQueue::ack时候设置这个标志,传递标签将被视为最大包含数量,以便通过单个方法标示多个消息为已收到,如果设置为0
 * 传递标签指向单个消息,如果设置了AMQP_MULTIPLE,并且传递标签是0,将所有未完成消息标示为已收到
 */
define(<span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">'AMQP_MULTIPLE', <span class="hljs-number" style="margin:0px;padding:0px;">4096); <span class="hljs-comment" style="margin:0px;padding:0px;color:green;">/**
 * If set during a call to {@link AMQPExchange::bind()}, the server will not respond to the method.The client should not wait
 * for a reply method. If the server could not complete the method it will raise a channel or connection exception.
 * 当在调用AMQPExchange::bind()方法的时候,服务器将不响应请求,客户端将不应该等待响应,如果服务器无法完成该方法,将会抛出一个异常
 */
define(<span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">'AMQP_NOWAIT', <span class="hljs-number" style="margin:0px;padding:0px;">8192); <span class="hljs-comment" style="margin:0px;padding:0px;color:green;">/**
 * If set during a call to {@link AMQPQueue::nack()}, the message will be placed back to the queue.
 * 如果在调用AMQPQueue::nack方法时候设置,消息将会被传递回队列
 */
define(<span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">'AMQP_REQUEUE', <span class="hljs-number" style="margin:0px;padding:0px;">16384); <span class="hljs-comment" style="margin:0px;padding:0px;color:green;">/**
 * A direct exchange type.
 * direct类型交换机
 */
define(<span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">'AMQP_EX_TYPE_DIRECT', <span class="hljs-string" style="margin:0px;padding:0px;">'direct'); <span class="hljs-comment" style="margin:0px;padding:0px;color:green;">/**
 * A fanout exchange type.
 * fanout类型交换机
 */
define(<span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">'AMQP_EX_TYPE_FANOUT', <span class="hljs-string" style="margin:0px;padding:0px;">'fanout'); <span class="hljs-comment" style="margin:0px;padding:0px;color:green;">/**
 * A topic exchange type.
 * topic类型交换机
 */
define(<span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">'AMQP_EX_TYPE_TOPIC', <span class="hljs-string" style="margin:0px;padding:0px;">'topic'); <span class="hljs-comment" style="margin:0px;padding:0px;color:green;">/**
 * A header exchange type.
 * header类型交换机
 */
define(<span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">'AMQP_EX_TYPE_HEADERS', <span class="hljs-string" style="margin:0px;padding:0px;">'headers'); <span class="hljs-comment" style="margin:0px;padding:0px;color:green;">/**
 * socket连接超时设置
 */
define(<span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">'AMQP_OS_SOCKET_TIMEOUT_ERRNO', <span class="hljs-number" style="margin:0px;padding:0px;">536870947);</span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></code></pre>
<span style="display:none;" id="__kindeditor_bookmark_start_5__"></span>