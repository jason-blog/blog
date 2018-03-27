<pre style="white-space:pre-wrap;word-wrap:break-word;color:#333333;font-size:14px;background-color:#FFFFFF;">
<p>
	这篇文章的<a href="http://lib.csdn.net/base/php" class="replace_word" title="PHP知识库" target="_blank" style="color:#DF3434;text-decoration-line:none;font-weight:bold;">PHP</a> Demo代码是网上找过来的,注释添加的比较全面，容易理解，在此基础上<a href="http://lib.csdn.net/base/softwaretest" class="replace_word" title="软件测试知识库" target="_blank" style="color:#DF3434;text-decoration-line:none;font-weight:bold;">测试</a>
</p>

<p>
	消费者：接收消息
</p>

<p>
	逻辑：

创建连接–&gt;创建channel–&gt;创建交换机–&gt;创建队列–&gt;绑定交换机/队列/路由键–&gt;接收消息
</p>

<p>
	文件名为 c.php
</p>

<pre style="white-space:pre-wrap;word-wrap:break-word;">&lt;?php    
/************************************* 
 * PHP amqp(RabbitMQ) Demo - consumer 
 * Author: Linvo 
 * Date: 2012/7/30 
 *************************************/  
//配置信息  
$conn_args = array(  
    'host' =&gt; '192.168.1.93',   
    'port' =&gt; '5672',   
    'login' =&gt; 'guest',   
    'password' =&gt; 'guest',  
    'vhost'=&gt;'/'  
);    
$e_name = 'e_linvo'; //交换机名  
$q_name = 'q_linvo'; //队列名  
$k_route = 'key_1'; //路由key  
  
//创建连接和channel  
$conn = new AMQPConnection($conn_args);    
if (!$conn-&gt;connect()) {    
    die("Cannot connect to the broker!\n");    
}    
$channel = new AMQPChannel($conn);    
  
//创建交换机     
$ex = new AMQPExchange($channel);    
$ex-&gt;setName($e_name);  
$ex-&gt;setType(AMQP_EX_TYPE_DIRECT); //direct类型   
$ex-&gt;setFlags(AMQP_DURABLE); //持久化  
echo "Exchange Status:".$ex-&gt;declare()."\n";    
    
//创建队列     
$q = new AMQPQueue($channel);  
$q-&gt;setName($q_name);    
$q-&gt;setFlags(AMQP_DURABLE); //持久化   
echo "Message Total:".$q-&gt;declare()."\n";    
  
//绑定交换机与队列，并指定路由键  
echo 'Queue Bind: '.$q-&gt;bind($e_name, $k_route)."\n";  
  
//阻塞模式接收消息  
echo "Message:\n";    
while(True){  
    $q-&gt;consume('processMessage');    
    //$q-&gt;consume('processMessage', AMQP_AUTOACK); //自动ACK应答   
}  
$conn-&gt;disconnect();    
  
/** 
 * 消费回调函数 
 * 处理消息 
 */  
function processMessage($envelope, $queue) {  
    $msg = $envelope-&gt;getBody();  
    echo $msg."\n"; //处理消息  
    $queue-&gt;ack($envelope-&gt;getDeliveryTag()); //手动发送ACK应答  
}</pre>
<p>
	生产者：发送消息
</p>
<p>
	逻辑：创建连接–&gt;创建channel–&gt;创建交换机对象–&gt;发送消息
</p>
<p>
	文件名为 p.php
</p>
<pre style="white-space:pre-wrap;word-wrap:break-word;">&lt;?php    
/************************************* 
 * PHP amqp(RabbitMQ) Demo - publisher 
 * Author: Linvo 
 * Date: 2012/7/30 
 *************************************/  
//配置信息  
$conn_args = array(  
    'host' =&gt; '192.168.1.93',   
    'port' =&gt; '5672',   
    'login' =&gt; 'guest',   
    'password' =&gt; 'guest',  
    'vhost'=&gt;'/'  
);    
$e_name = 'e_linvo'; //交换机名  
//$q_name = 'q_linvo'; //无需队列名  
$k_route = 'key_1'; //路由key  
  
//创建连接和channel  
$conn = new AMQPConnection($conn_args);    
if (!$conn-&gt;connect()) {    
    die("Cannot connect to the broker!\n");    
}    
$channel = new AMQPChannel($conn);    
  
//消息内容  
$message = "TEST MESSAGE! 测试消息！";    
  
//创建交换机对象     
$ex = new AMQPExchange($channel);    
$ex-&gt;setName($e_name);    
  
//发送消息  
//$channel-&gt;startTransaction(); //开始事务   
for($i=0; $i&lt;5; ++$i){  
    echo "Send Message:".$ex-&gt;publish($message, $k_route)."\n";   
}  
//$channel-&gt;commitTransaction(); //提交事务  
  
$conn-&gt;disconnect();</pre>
<p>
	需要注意的地方是：
</p>
<p>
	queue对象有两个方法可用于取消息：consume和get。<br />
前者是阻塞的，无消息时会被挂起，适合循环中使用；后者则是非阻塞的，取消息时有则取，无则返回false。
</p>
<p>
	<a target="_blank" href="http://img.phpsong.com/wp-content/uploads/2016/03/2016030302422324097.png" class="highslide-image" rel="attachment wp-att-2230" style="color:#336699;text-decoration-line:none;"><img class="alignnone wp-image-2230 size-full" src="http://img.phpsong.com/wp-content/uploads/2016/03/2016030302422324097.png" alt="rabbitmq php测试" width="590" height="186" style="border-width:initial;border-style:none;max-width:100%;" /></a> <a target="_blank" href="http://img.phpsong.com/wp-content/uploads/2016/03/2016030302422315022.png" class="highslide-image" rel="attachment wp-att-2231" style="color:#336699;text-decoration-line:none;"><img class="alignnone wp-image-2231 size-full" src="http://img.phpsong.com/wp-content/uploads/2016/03/2016030302422315022.png" alt="rabbitmq php测试" width="476" height="105" style="border-width:initial;border-style:none;max-width:100%;" /></a>
</p>
</pre>