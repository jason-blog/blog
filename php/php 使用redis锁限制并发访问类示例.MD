<p>
	http://blog.csdn.net/fdipzone/article/details/51793837
</p>
<p>
<pre class="prettyprint lang-js linenums">1.并发访问限制问题

对于一些需要限制同一个用户并发访问的场景，如果用户并发请求多次，而服务器处理没有加锁限制，用户则可以多次请求成功。

例如换领优惠券，如果用户同一时间并发提交换领码，在没有加锁限制的情况下，用户则可以使用同一个换领码同时兑换到多张优惠券。

伪代码如下：

if A(可以换领)
    B(执行换领)
    C(更新为已换领)
D(结束)
1
2
3
4
1
2
3
4
如果用户并发提交换领码，都能通过可以换领(A)的判断，因为必须有一个执行换领(B)后，才会更新为已换领(C)。因此如果用户在有一个更新为已换领之前，有多少次请求，这些请求都可以执行成功。 


2.并发访问限制方法

使用文件锁可以实现并发访问限制，但对于分布式架构的环境，使用文件锁不能保证多台服务器的并发访问限制。

Redis是一个开源的使用ANSI C语言编写、支持网络、可基于内存亦可持久化的日志型、Key-Value数据库，并提供多种语言的API。 
本文将使用其setnx方法实现分布式锁功能。setnx即Set it Not eXists。 
当键值不存在时，插入成功（获取锁成功），如果键值已经存在，则插入失败（获取锁失败）

RedisLock.class.PHP

&lt;?php
/**
 *  Redis锁操作类
 *  Date:   2016-06-30
 *  Author: fdipzone
 *  Ver:    1.0
 *
 *  Func:
 *  public  lock    获取锁
 *  public  unlock  释放锁
 *  private connect 连接
 */
class RedisLock { // class start

    private $_config;
    private $_redis;

    /**
     * 初始化
     * @param Array $config redis连接设定
     */
    public function __construct($config=array()){
        $this-&gt;_config = $config;
        $this-&gt;_redis = $this-&gt;connect();
    }

    /**
     * 获取锁
     * @param  String  $key    锁标识
     * @param  Int     $expire 锁过期时间
     * @return Boolean
     */
    public function lock($key, $expire=5){
        $is_lock = $this-&gt;_redis-&gt;setnx($key, time()+$expire);

        // 不能获取锁
        if(!$is_lock){

            // 判断锁是否过期
            $lock_time = $this-&gt;_redis-&gt;get($key);

            // 锁已过期，删除锁，重新获取
            if(time()&gt;$lock_time){
                $this-&gt;unlock($key);
                $is_lock = $this-&gt;_redis-&gt;setnx($key, time()+$expire);
            }
        }

        return $is_lock? true : false;
    }

    /**
     * 释放锁
     * @param  String  $key 锁标识
     * @return Boolean
     */
    public function unlock($key){
        return $this-&gt;_redis-&gt;del($key);
    }

    /**
     * 创建redis连接
     * @return Link
     */
    private function connect(){
        try{
            $redis = new Redis();
            $redis-&gt;connect($this-&gt;_config['host'],$this-&gt;_config['port'],$this-&gt;_config['timeout'],$this-&gt;_config['reserved'],$this-&gt;_config['retry_interval']);
            if(empty($this-&gt;_config['auth'])){
                $redis-&gt;auth($this-&gt;_config['auth']);
            }
            $redis-&gt;select($this-&gt;_config['index']);
        }catch(RedisException $e){
            throw new Exception($e-&gt;getMessage());
            return false;
        }
        return $redis;
    }

} // class end

?&gt;

demo.php

&lt;?php
require 'RedisLock.class.php';

$config = array(
    'host' =&gt; 'localhost',
    'port' =&gt; 6379,
    'index' =&gt; 0,
    'auth' =&gt; '',
    'timeout' =&gt; 1,
    'reserved' =&gt; NULL,
    'retry_interval' =&gt; 100,
);

// 创建redislock对象
$oRedisLock = new RedisLock($config);

// 定义锁标识
$key = 'mylock';

// 获取锁
$is_lock = $oRedisLock-&gt;lock($key, 10);

if($is_lock){
    echo 'get lock success&lt;br&gt;';
    echo 'do sth..&lt;br&gt;';
    sleep(5);
    echo 'success&lt;br&gt;';
    $oRedisLock-&gt;unlock($key);

// 获取锁失败
}else{
    echo 'request too frequently&lt;br&gt;';
}

?&gt;</pre>
<pre class="prettyprint lang-js linenums">
</pre>
<pre class="prettyprint lang-js linenums">
	<p style="margin-top:0px;margin-bottom:1.1em;padding:0px;box-sizing:border-box;color:#3F3F3F;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		<strong style="box-sizing:border-box;"><a href="http://lib.csdn.net/base/softwaretest" class="replace_word" title="软件测试知识库" target="_blank" style="color:#DF3434;text-decoration-line:none;box-sizing:border-box;">测试</a>方法：</strong>&nbsp;
打开两个不同的浏览器,同时在A,B中访问demo.php&nbsp;
如果先访问的会获取到锁&nbsp;
输出<span style="box-sizing:border-box;color:#FF0000;">&nbsp;
get lock success&nbsp;
do sth..&nbsp;
success</span>
	</p>

	<p style="margin-top:0px;margin-bottom:1.1em;padding:0px;box-sizing:border-box;color:#3F3F3F;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		另一个获取锁失败则会输出<span style="box-sizing:border-box;color:#FF0000;">request too frequently</span>
	</p>

	<p style="margin-top:0px;margin-bottom:1.1em;padding:0px;box-sizing:border-box;color:#3F3F3F;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		保证同一时间只有一个访问有效，有效限制并发访问。&nbsp; <strong style="box-sizing:border-box;">为了避免系统突然出错导致死锁，所以在获取锁的时候增加一个过期时间，如果已超过过期时间，即使是锁定状态都会释放锁，避免死锁导致的问题。</strong>&nbsp;
	</p>

<pre class="prettyprint lang-js linenums">
</pre>
<strong style="box-sizing:border-box;color:#3F3F3F;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">源码下载地址：<a href="http://download.csdn.net/detail/fdipzone/9564385" target="_blank" style="color:#4FA1DB;text-decoration-line:none;box-sizing:border-box;">点击查看</a></strong><br />
</pre>
</p>