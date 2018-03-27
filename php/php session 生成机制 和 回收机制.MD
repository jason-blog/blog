<p style="margin-top:0px;margin-bottom:0px;padding:5px 0px;white-space:normal;">
	php.ini session.save_path 是存放session的路径
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:5px 0px;white-space:normal;">
	1、php中session的生成机制
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:5px 0px;white-space:normal;">
	我们先来分析一下PHP中是怎么生成一个session的。设计出session的目的是保持每一个用户的各种状态来弥补HTTP协议的不足(无状态)。我们现在有一个疑问，我们都知道session是保存在服务器的，既然它用于保持每一个用户的状态那它利用什么来区别用户的呢？这个时候就得借助cookie了。当我们在代码中调用session_start();时，PHP会同时往SESSION的存放目录(默认为/tmp/)和客户端的cookie目录各生成一个文件。session文件名称像这样：
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:5px 0px;white-space:normal;">
	<img src="http://files.jb51.net/file_images/article/201408/201481993313899.jpg?20147199340" alt="" style="border-width:1px;border-style:solid;border-color:#CCCCCC;vertical-align:bottom;padding:1px;overflow:hidden;max-width:650px;" /> 
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:5px 0px;white-space:normal;">
	格式为sess_{SESSIONID} ，这时session文件中没有任何内容，当我们在session_start();添加了这两行代码：
</p>
<div class="codetitle" style="margin:3px auto 0px;padding:0px 3px;background-image:initial;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;width:640px;clear:both;border-top:1px solid #0099CC;border-right:1px solid #0099CC;border-left:1px solid #0099CC;line-height:25.2px;white-space:normal;">
	<a data="69291" class="copybut" id="copybut69291" style="cursor:pointer;">复制代码</a>代码如下:
</div>
<div class="codebody" id="code69291" style="margin:0px auto 3px;padding:0px 3px 0px 5px;line-height:25.2px;background-image:initial;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;border:1px solid #0099CC;width:638px;clear:both;white-space:normal;">
	<br />
$_SESSION['name'] = 'wanchun0222';
	<p style="margin-top:0px;margin-bottom:0px;padding:5px 0px;">
		$_SESSION['blog'] = 'coderbolg.net';
	</p>
</div>
<p>
	<br style="white-space:normal;" />
这时文件就有内容了：
</p>
<div class="codetitle" style="margin:3px auto 0px;padding:0px 3px;background-image:initial;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;width:640px;clear:both;border-top:1px solid #0099CC;border-right:1px solid #0099CC;border-left:1px solid #0099CC;line-height:25.2px;white-space:normal;">
	<a data="61005" class="copybut" id="copybut61005" style="cursor:pointer;">复制代码</a>代码如下:
</div>
<div class="codebody" id="code61005" style="margin:0px auto 3px;padding:0px 3px 0px 5px;line-height:25.2px;background-image:initial;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;border:1px solid #0099CC;width:638px;clear:both;white-space:normal;">
	<br />
name|s:11:"wanchun0222";blog|s:13:"coderbolg.net";<br />
</div>
<p>
	<br style="white-space:normal;" />
这时再看看cookie：
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:5px 0px;white-space:normal;">
	<img src="http://files.jb51.net/file_images/article/201408/201481993635547.jpg?201471993648" alt="" style="border-width:1px;border-style:solid;border-color:#CCCCCC;vertical-align:bottom;padding:1px;overflow:hidden;max-width:650px;" /> 
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:5px 0px;white-space:normal;">
	可以看到服务器为我们自动生成了一个cookie,cookie名称为"PHPSESSID"，cookie内容是一串字符，其实这串字符就是{SESSIONID}。也许你已经明白了，当我们使用session时，PHP就先生成一个唯一的SESSIONID号(如2bd170b3f86523f1b1b60b55ffde0f66)，再在我们服务器的默认目录下生成一个文件，文件名为sess_{SESSIONID}，同时在当前用户的客户端生成一个cookie，内容已经说过了。这样PHP会为每一个用户生成一个SESSIONID，也就是说一个用户一个session文件。PHP第一次为某个用户使用session时就向客户端写入了cookie，当这个用户以后访问时，浏览器会带上这个cookie，PHP在拿到cookie后就读出里面的SESSIONID，拿着这个SESSIONID去session目录下找session文件。找到后在调用$_SESSION['blog']的时候显示出来。
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:5px 0px;white-space:normal;">
	2、php中session的过期回收机制
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:5px 0px;white-space:normal;">
	我们明白了session的生成及工作原理，发现在session目录下会有许多session文件。当然这些文件一定不是永远存在的，PHP一定提供了一种过期回收机制。在php.ini中session.gc_maxlifetime为session设置了生存时间(默认为1440s)。如果session文件的最后更新时间到现在超过了生存时间，这个session文件就被认为是过期的了。在下一次session回收的时候就会被删除。那下一次session回收是在什么时候呢？这和php请求次数有关的。在PHP内部机制中，当php被请求了N次后就会有一次触发回收机制。到底是请求多少次触发一次是通过以下两个参数控制的：
</p>
<div class="codetitle" style="margin:3px auto 0px;padding:0px 3px;background-image:initial;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;width:640px;clear:both;border-top:1px solid #0099CC;border-right:1px solid #0099CC;border-left:1px solid #0099CC;line-height:25.2px;white-space:normal;">
	<a data="38979" class="copybut" id="copybut38979" style="cursor:pointer;">复制代码</a>代码如下:
</div>
<div class="codebody" id="code38979" style="margin:0px auto 3px;padding:0px 3px 0px 5px;line-height:25.2px;background-image:initial;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;border:1px solid #0099CC;width:638px;clear:both;white-space:normal;">
	<br />
session.gc_probability = 1
	<p style="margin-top:0px;margin-bottom:0px;padding:5px 0px;">
		session.gc_divisor = 100
	</p>
</div>
<p>
	<br style="white-space:normal;" />
这是php.ini的默认设置，意思是每100次PHP请求就有一次回收发生。概率是 gc_probability/gc_divisor 。我们了解了服务器端的session过期机制，再来看看客户端的cookie的过期机制。
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:5px 0px;white-space:normal;">
	如果cookie失效了浏览器自然发送不了cookie到服务器，这时即使服务器的session文件存在也没用，因为PHP不知道要读取哪个session文件。我们知道PHP的cookie过期时间是在创建时设置的，那么PHP在创建session的同时为客户端创建的cookie的生命周期是多久呢？这个在php.ini中有设置：session.cookie_lifetime 。这个值默认是0，代表浏览器一关闭SESSIONID就失效。那就是说我们把session.gc_maxlifetime和session.cookie_lifetime设置成同一个值就可以控制session的失效时间了。
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:5px 0px;white-space:normal;">
	3、php中session的客户端存储机制
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:5px 0px;white-space:normal;">
	由上面的介绍我们可以知道，如果用户关闭了cookie，那我们的session就完全没法工作了。是的，确实是这样。php中session的客户端存储机制只有cookie吗？不是的。既然我们的SESSIONID 不能通过cookie传递到各个页面，那我们还有另一个法宝，就是通过页面GET传值的方式。
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:5px 0px;white-space:normal;">
	PHP可以在cookie被禁用时自动通过GET方式跨页传递SESSIONID，前提是设置php.ini的session.use_trans_sid为1。这时当我们在客户端禁用了cookie时使用了session，并在当前页面通过点击链接到另一页面时，PHP会自动在链接上添加SESSIONID参数，像这样：nextpage.php?SESSIONID=2bd170b3f86523f1b1b60b55ffde0f66。我想你应该看到了这种方式的缺点：好像不够安全啊。
</p>