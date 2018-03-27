<div class="iteye-blog-content-contain" style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		对于开发来说需要有好的生态开发库来辅助我们快速开发，而Lua中也有大多数我们需要的第三方开发库如Redis、Memcached、Mysql、Http客户端、JSON、模板引擎等。
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		一些常见的Lua库可以在github上搜索，<a href="https://github.com/search?utf8=%E2%9C%93&amp;q=lua+resty" style="color:#108AC6;">https://github.com/search?utf8=%E2%9C%93&amp;q=lua+resty</a>。
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		&nbsp;
	</p>
	<h2 style="line-height:1.5em;margin:0px 0px 0.5em;padding:0px;">
		Redis客户端
	</h2>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		lua-resty-redis是为基于cosocket API的ngx_lua提供的Lua redis客户端，通过它可以完成Redis的操作。默认安装OpenResty时已经自带了该模块，使用文档可参考<a href="https://github.com/openresty/lua-resty-redis" style="color:#108AC6;">https://github.com/openresty/lua-resty-redis</a>。
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		&nbsp;
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		在测试之前请启动Redis实例：
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		nohup /usr/servers/redis-2.8.19/src/redis-server&nbsp; /usr/servers/redis-2.8.19/redis_6660.conf &amp;
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		&nbsp;
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		<strong>1、基本操作</strong>
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		&nbsp;
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		编辑test_redis_baisc.lua
	</p>
	<div class="dp-highlighter" id="" style="font-family:Monaco, &quot;font-size:12px;background-color:transparent;width:679px;overflow:auto;margin-left:9px;padding:1px;word-break:break-all;">
		<div class="bar">
			<div class="tools" style="padding:3px;margin:0px;font-weight:bold;">
				Java代码&nbsp;&nbsp;<a title="收藏这段代码" style="color:#108AC6;text-decoration-line:underline;"><img class="star" src="http://jinnianshilongnian.iteye.com/images/icon_star.png" alt="收藏代码" /></a>
			</div>
		</div>
		<ol start="1" class="dp-j" style="font-size:1em;line-height:1.4em;margin:0px 0px 1px;padding:2px 0px;border:1px solid #D1D7DC;list-style-position:initial;list-style-image:initial;color:#2B91AF;">
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">local&nbsp;function&nbsp;close_redis(red)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;<span class="keyword" style="color:#7F0055;font-weight:bold;">if</span>&nbsp;not&nbsp;red&nbsp;then&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="keyword" style="color:#7F0055;font-weight:bold;">return</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;end&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;local&nbsp;ok,&nbsp;err&nbsp;=&nbsp;red:close()&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;<span class="keyword" style="color:#7F0055;font-weight:bold;">if</span>&nbsp;not&nbsp;ok&nbsp;then&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ngx.say(<span class="string" style="color:blue;">"close&nbsp;redis&nbsp;error&nbsp;:&nbsp;"</span>,&nbsp;err)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;end&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">end&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">local&nbsp;redis&nbsp;=&nbsp;require(<span class="string" style="color:blue;">"resty.redis"</span>)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">--创建实例&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">local&nbsp;red&nbsp;=&nbsp;redis:<span class="keyword" style="color:#7F0055;font-weight:bold;">new</span>()&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">--设置超时（毫秒）&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">red:set_timeout(<span class="number" style="color:#C00000;">1000</span>)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">--建立连接&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">local&nbsp;ip&nbsp;=&nbsp;<span class="string" style="color:blue;">"127.0.0.1"</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">local&nbsp;port&nbsp;=&nbsp;<span class="number" style="color:#C00000;">6660</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">local&nbsp;ok,&nbsp;err&nbsp;=&nbsp;red:connect(ip,&nbsp;port)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;"><span class="keyword" style="color:#7F0055;font-weight:bold;">if</span>&nbsp;not&nbsp;ok&nbsp;then&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;ngx.say(<span class="string" style="color:blue;">"connect&nbsp;to&nbsp;redis&nbsp;error&nbsp;:&nbsp;"</span>,&nbsp;err)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;<span class="keyword" style="color:#7F0055;font-weight:bold;">return</span>&nbsp;close_redis(red)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">end&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">--调用API进行处理&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">ok,&nbsp;err&nbsp;=&nbsp;red:set(<span class="string" style="color:blue;">"msg"</span>,&nbsp;<span class="string" style="color:blue;">"hello&nbsp;world"</span>)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;"><span class="keyword" style="color:#7F0055;font-weight:bold;">if</span>&nbsp;not&nbsp;ok&nbsp;then&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;ngx.say(<span class="string" style="color:blue;">"set&nbsp;msg&nbsp;error&nbsp;:&nbsp;"</span>,&nbsp;err)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;<span class="keyword" style="color:#7F0055;font-weight:bold;">return</span>&nbsp;close_redis(red)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">end&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">--调用API获取数据&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">local&nbsp;resp,&nbsp;err&nbsp;=&nbsp;red:get(<span class="string" style="color:blue;">"msg"</span>)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;"><span class="keyword" style="color:#7F0055;font-weight:bold;">if</span>&nbsp;not&nbsp;resp&nbsp;then&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;ngx.say(<span class="string" style="color:blue;">"get&nbsp;msg&nbsp;error&nbsp;:&nbsp;"</span>,&nbsp;err)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;<span class="keyword" style="color:#7F0055;font-weight:bold;">return</span>&nbsp;close_redis(red)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">end&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">--得到的数据为空处理&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;"><span class="keyword" style="color:#7F0055;font-weight:bold;">if</span>&nbsp;resp&nbsp;==&nbsp;ngx.<span class="keyword" style="color:#7F0055;font-weight:bold;">null</span>&nbsp;then&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;resp&nbsp;=&nbsp;<span class="string" style="color:blue;">''</span>&nbsp;&nbsp;--比如默认值&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">end&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">ngx.say(<span class="string" style="color:blue;">"msg&nbsp;:&nbsp;"</span>,&nbsp;resp)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">close_redis(red)&nbsp;&nbsp;</span>
			</li>
		</ol>
	</div>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		<span style="line-height:1.5;">基本逻辑很简单，要注意此处判断是否为nil，需要跟ngx.null比较。</span>
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		&nbsp;
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		2、example.conf配置文件
	</p>
	<div class="dp-highlighter" id="" style="font-family:Monaco, &quot;font-size:12px;background-color:transparent;width:679px;overflow:auto;margin-left:9px;padding:1px;word-break:break-all;">
		<div class="bar">
			<div class="tools" style="padding:3px;margin:0px;font-weight:bold;">
				Java代码&nbsp;&nbsp;<a title="收藏这段代码" style="color:#108AC6;text-decoration-line:underline;"><img class="star" src="http://jinnianshilongnian.iteye.com/images/icon_star.png" alt="收藏代码" /></a>
			</div>
		</div>
		<ol start="1" class="dp-j" style="font-size:1em;line-height:1.4em;margin:0px 0px 1px;padding:2px 0px;border:1px solid #D1D7DC;list-style-position:initial;list-style-image:initial;color:#2B91AF;">
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;location&nbsp;/lua_redis_basic&nbsp;{&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;default_type&nbsp;<span class="string" style="color:blue;">'text/html'</span>;&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;lua_code_cache&nbsp;on;&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;content_by_lua_file&nbsp;/usr/example/lua/test_redis_basic.lua;&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">}&nbsp;&nbsp;</span>
			</li>
		</ol>
	</div>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		&nbsp;&nbsp;
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		3、访问如http://192.168.1.2/lua_redis_basic进行测试，正常情况得到如下信息
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		msg : hello world
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		&nbsp;
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		<strong>2、连接池</strong>
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		<span style="line-height:1.5;">建立TCP连接需要三次握手而释放TCP连接需要四次握手，而这些往返时延仅需要一次，以后应该复用TCP连接，此时就可以考虑使用连接池，即连接池可以复用连接。</span>
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		我们只需要将之前的close_redis函数改造为如下即可：<span style="line-height:1.5;">&nbsp;</span>
	</p>
	<div class="dp-highlighter" id="" style="font-family:Monaco, &quot;font-size:12px;background-color:transparent;width:679px;overflow:auto;margin-left:9px;padding:1px;word-break:break-all;">
		<div class="bar">
			<div class="tools" style="padding:3px;margin:0px;font-weight:bold;">
				Java代码&nbsp;&nbsp;<a title="收藏这段代码" style="color:#108AC6;text-decoration-line:underline;"><img class="star" src="http://jinnianshilongnian.iteye.com/images/icon_star.png" alt="收藏代码" /></a>
			</div>
		</div>
		<ol start="1" class="dp-j" style="font-size:1em;line-height:1.4em;margin:0px 0px 1px;padding:2px 0px;border:1px solid #D1D7DC;list-style-position:initial;list-style-image:initial;color:#2B91AF;">
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">local&nbsp;function&nbsp;close_redis(red)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;<span class="keyword" style="color:#7F0055;font-weight:bold;">if</span>&nbsp;not&nbsp;red&nbsp;then&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="keyword" style="color:#7F0055;font-weight:bold;">return</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;end&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;--释放连接(连接池实现)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;local&nbsp;pool_max_idle_time&nbsp;=&nbsp;<span class="number" style="color:#C00000;">10000</span>&nbsp;--毫秒&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;local&nbsp;pool_size&nbsp;=&nbsp;<span class="number" style="color:#C00000;">100</span>&nbsp;--连接池大小&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;local&nbsp;ok,&nbsp;err&nbsp;=&nbsp;red:set_keepalive(pool_max_idle_time,&nbsp;pool_size)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;<span class="keyword" style="color:#7F0055;font-weight:bold;">if</span>&nbsp;not&nbsp;ok&nbsp;then&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ngx.say(<span class="string" style="color:blue;">"set&nbsp;keepalive&nbsp;error&nbsp;:&nbsp;"</span>,&nbsp;err)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;end&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">end&nbsp;&nbsp;</span>
			</li>
		</ol>
	</div>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		即设置空闲连接超时时间防止连接一直占用不释放；设置连接池大小来复用连接。
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		&nbsp;
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		此处假设调用red:set_keepalive()，连接池大小通过nginx.conf中http部分的如下指令定义：
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		#默认连接池大小，默认30
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		lua_socket_pool_size 30;
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		#默认超时时间,默认60s
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		lua_socket_keepalive_timeout 60s;
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		&nbsp;
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		注意：
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		1、连接池是每Worker进程的，而不是每Server的；
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		2、当连接超过最大连接池大小时，会按照LRU算法回收空闲连接为新连接使用；
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		3、连接池中的空闲连接出现异常时会自动被移除；
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		4、连接池是通过ip和port标识的，即相同的ip和port会使用同一个连接池（即使是不同类型的客户端如Redis、Memcached）；
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		5、连接池第一次set_keepalive时连接池大小就确定下了，不会再变更；
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		5、cosocket的连接池<a target="_blank" href="http://wiki.nginx.org/HttpLuaModule#tcpsock:setkeepalive" style="color:#108AC6;">http://wiki.nginx.org/HttpLuaModule#tcpsock:setkeepalive</a>。
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		&nbsp;
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		<strong>3、pipeline</strong>
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		pipeline即管道，可以理解为把多个命令打包然后一起发送；MTU（Maxitum Transmission Unit 最大传输单元）为二层包大小，一般为1500字节；而MSS（Maximum Segment Size 最大报文分段大小）为四层包大小，其一般是1500-20（IP报头）-20（TCP报头）=1460字节；因此假设我们执行的多个Redis命令能在一个报文中传输的话，可以减少网络往返来提高速度。因此可以根据实际情况来选择走pipeline模式将多个命令打包到一个报文发送然后接受响应，而Redis协议也能很简单的识别和解决粘包。
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		&nbsp;
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		1、修改之前的代码片段
	</p>
	<div class="dp-highlighter" id="" style="font-family:Monaco, &quot;font-size:12px;background-color:transparent;width:679px;overflow:auto;margin-left:9px;padding:1px;word-break:break-all;">
		<div class="bar">
			<div class="tools" style="padding:3px;margin:0px;font-weight:bold;">
				Java代码&nbsp;&nbsp;<a title="收藏这段代码" style="color:#108AC6;text-decoration-line:underline;"><img class="star" src="http://jinnianshilongnian.iteye.com/images/icon_star.png" alt="收藏代码" /></a>
			</div>
		</div>
		<ol start="1" class="dp-j" style="font-size:1em;line-height:1.4em;margin:0px 0px 1px;padding:2px 0px;border:1px solid #D1D7DC;list-style-position:initial;list-style-image:initial;color:#2B91AF;">
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">red:init_pipeline()&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">red:set(<span class="string" style="color:blue;">"msg1"</span>,&nbsp;<span class="string" style="color:blue;">"hello1"</span>)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">red:set(<span class="string" style="color:blue;">"msg2"</span>,&nbsp;<span class="string" style="color:blue;">"hello2"</span>)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">red:get(<span class="string" style="color:blue;">"msg1"</span>)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">red:get(<span class="string" style="color:blue;">"msg2"</span>)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">local&nbsp;respTable,&nbsp;err&nbsp;=&nbsp;red:commit_pipeline()&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">--得到的数据为空处理&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;"><span class="keyword" style="color:#7F0055;font-weight:bold;">if</span>&nbsp;respTable&nbsp;==&nbsp;ngx.<span class="keyword" style="color:#7F0055;font-weight:bold;">null</span>&nbsp;then&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;respTable&nbsp;=&nbsp;{}&nbsp;&nbsp;--比如默认值&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">end&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">--结果是按照执行顺序返回的一个table&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;"><span class="keyword" style="color:#7F0055;font-weight:bold;">for</span>&nbsp;i,&nbsp;v&nbsp;in&nbsp;ipairs(respTable)&nbsp;<span class="keyword" style="color:#7F0055;font-weight:bold;">do</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;ngx.say(<span class="string" style="color:blue;">"msg&nbsp;:&nbsp;"</span>,&nbsp;v,&nbsp;<span class="string" style="color:blue;">"&lt;br/&gt;"</span>)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">end&nbsp;&nbsp;</span>
			</li>
		</ol>
	</div>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		通过init_pipeline()初始化，然后通过commit_pipieline()打包提交init_pipeline()之后的Redis命令；返回结果是一个lua table，可以通过ipairs循环获取结果；
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		&nbsp;
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		2、配置相应location，测试得到的结果
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		msg : OK<br style="font-family:Simsun;font-size:medium;line-height:normal;" />
msg : OK<br style="font-family:Simsun;font-size:medium;line-height:normal;" />
msg : hello1<br style="font-family:Simsun;font-size:medium;line-height:normal;" />
msg : hello2
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		&nbsp;
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		&nbsp;
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		3、Redis Lua脚本
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		利用Redis单线程特性，可以通过在Redis中执行Lua脚本实现一些原子操作。如之前的red:get("msg")可以通过如下两种方式实现：
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		1、直接eval：
	</p>
	<div class="dp-highlighter" id="" style="font-family:Monaco, &quot;font-size:12px;background-color:transparent;width:679px;overflow:auto;margin-left:9px;padding:1px;word-break:break-all;">
		<div class="bar">
			<div class="tools" style="padding:3px;margin:0px;font-weight:bold;">
				Java代码&nbsp;&nbsp;<a title="收藏这段代码" style="color:#108AC6;text-decoration-line:underline;"><img class="star" src="http://jinnianshilongnian.iteye.com/images/icon_star.png" alt="收藏代码" /></a>
			</div>
		</div>
		<ol start="1" class="dp-j" style="font-size:1em;line-height:1.4em;margin:0px 0px 1px;padding:2px 0px;border:1px solid #D1D7DC;list-style-position:initial;list-style-image:initial;color:#2B91AF;">
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">local&nbsp;resp,&nbsp;err&nbsp;=&nbsp;red:eval(<span class="string" style="color:blue;">"return&nbsp;redis.call('get',&nbsp;KEYS[1])"</span>,&nbsp;<span class="number" style="color:#C00000;">1</span>,&nbsp;<span class="string" style="color:blue;">"msg"</span>);&nbsp;&nbsp;&nbsp;</span>
			</li>
		</ol>
	</div>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		2、script load然后evalsha&nbsp;&nbsp;SHA1 校验和，这样可以节省脚本本身的服务器带宽：
	</p>
	<div class="dp-highlighter" id="" style="font-family:Monaco, &quot;font-size:12px;background-color:transparent;width:679px;overflow:auto;margin-left:9px;padding:1px;word-break:break-all;">
		<div class="bar">
			<div class="tools" style="padding:3px;margin:0px;font-weight:bold;">
				Java代码&nbsp;&nbsp;<a title="收藏这段代码" style="color:#108AC6;text-decoration-line:underline;"><img class="star" src="http://jinnianshilongnian.iteye.com/images/icon_star.png" alt="收藏代码" /></a>
			</div>
		</div>
		<ol start="1" class="dp-j" style="font-size:1em;line-height:1.4em;margin:0px 0px 1px;padding:2px 0px;border:1px solid #D1D7DC;list-style-position:initial;list-style-image:initial;color:#2B91AF;">
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">local&nbsp;sha1,&nbsp;err&nbsp;=&nbsp;red:script(<span class="string" style="color:blue;">"load"</span>,&nbsp;&nbsp;<span class="string" style="color:blue;">"return&nbsp;redis.call('get',&nbsp;KEYS[1])"</span>);&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;"><span class="keyword" style="color:#7F0055;font-weight:bold;">if</span>&nbsp;not&nbsp;sha1&nbsp;then&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;ngx.say(<span class="string" style="color:blue;">"load&nbsp;script&nbsp;error&nbsp;:&nbsp;"</span>,&nbsp;err)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;<span class="keyword" style="color:#7F0055;font-weight:bold;">return</span>&nbsp;close_redis(red)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">end&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">ngx.say(<span class="string" style="color:blue;">"sha1&nbsp;:&nbsp;"</span>,&nbsp;sha1,&nbsp;<span class="string" style="color:blue;">"&lt;br/&gt;"</span>)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">local&nbsp;resp,&nbsp;err&nbsp;=&nbsp;red:evalsha(sha1,&nbsp;<span class="number" style="color:#C00000;">1</span>,&nbsp;<span class="string" style="color:blue;">"msg"</span>);&nbsp;&nbsp;</span>
			</li>
		</ol>
	</div>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		首先通过script load导入脚本并得到一个sha1校验和（仅需第一次导入即可），然后通过evalsha执行sha1校验和即可，这样如果脚本很长通过这种方式可以减少带宽的消耗。&nbsp;
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		&nbsp;
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		此处仅介绍了最简单的redis lua脚本，更复杂的请参考官方文档学习使用。
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		&nbsp;
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		另外Redis集群分片算法该客户端没有提供需要自己实现，当然可以考虑直接使用类似于Twemproxy这种中间件实现。
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		Memcached客户端使用方式和本文类似，本文就不介绍了。
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		&nbsp;
	</p>
	<h2 style="line-height:21px;margin:0px 0px 0.5em;padding:0px;">
		Mysql客户端
	</h2>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		lua-resty-mysql是为基于cosocket API的ngx_lua提供的Lua Mysql客户端，通过它可以完成Mysql的操作。默认安装OpenResty时已经自带了该模块，使用文档可参考<a target="_blank" href="https://github.com/openresty/lua-resty-mysql" style="color:#108AC6;">https://github.com/openresty/lua-resty-mysql</a>。
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		&nbsp;
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		1、编辑test_mysql.lua
	</p>
	<div class="dp-highlighter" id="" style="font-family:Monaco, &quot;font-size:12px;background-color:transparent;width:679px;overflow:auto;margin-left:9px;padding:1px;word-break:break-all;">
		<div class="bar">
			<div class="tools" style="padding:3px;margin:0px;font-weight:bold;">
				Java代码&nbsp;&nbsp;<a title="收藏这段代码" style="color:#108AC6;text-decoration-line:underline;"><img class="star" src="http://jinnianshilongnian.iteye.com/images/icon_star.png" alt="收藏代码" /></a>
			</div>
		</div>
		<ol start="1" class="dp-j" style="font-size:1em;line-height:1.4em;margin:0px 0px 1px;padding:2px 0px;border:1px solid #D1D7DC;list-style-position:initial;list-style-image:initial;color:#2B91AF;">
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">local&nbsp;function&nbsp;close_db(db)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;<span class="keyword" style="color:#7F0055;font-weight:bold;">if</span>&nbsp;not&nbsp;db&nbsp;then&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="keyword" style="color:#7F0055;font-weight:bold;">return</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;end&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;db:close()&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">end&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">local&nbsp;mysql&nbsp;=&nbsp;require(<span class="string" style="color:blue;">"resty.mysql"</span>)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">--创建实例&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">local&nbsp;db,&nbsp;err&nbsp;=&nbsp;mysql:<span class="keyword" style="color:#7F0055;font-weight:bold;">new</span>()&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;"><span class="keyword" style="color:#7F0055;font-weight:bold;">if</span>&nbsp;not&nbsp;db&nbsp;then&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;ngx.say(<span class="string" style="color:blue;">"new&nbsp;mysql&nbsp;error&nbsp;:&nbsp;"</span>,&nbsp;err)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;<span class="keyword" style="color:#7F0055;font-weight:bold;">return</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">end&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">--设置超时时间(毫秒)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">db:set_timeout(<span class="number" style="color:#C00000;">1000</span>)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">local&nbsp;props&nbsp;=&nbsp;{&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;host&nbsp;=&nbsp;<span class="string" style="color:blue;">"127.0.0.1"</span>,&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;port&nbsp;=&nbsp;<span class="number" style="color:#C00000;">3306</span>,&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;database&nbsp;=&nbsp;<span class="string" style="color:blue;">"mysql"</span>,&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;user&nbsp;=&nbsp;<span class="string" style="color:blue;">"root"</span>,&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;password&nbsp;=&nbsp;<span class="string" style="color:blue;">"123456"</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">}&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">local&nbsp;res,&nbsp;err,&nbsp;errno,&nbsp;sqlstate&nbsp;=&nbsp;db:connect(props)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;"><span class="keyword" style="color:#7F0055;font-weight:bold;">if</span>&nbsp;not&nbsp;res&nbsp;then&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;ngx.say(<span class="string" style="color:blue;">"connect&nbsp;to&nbsp;mysql&nbsp;error&nbsp;:&nbsp;"</span>,&nbsp;err,&nbsp;<span class="string" style="color:blue;">"&nbsp;,&nbsp;errno&nbsp;:&nbsp;"</span>,&nbsp;errno,&nbsp;<span class="string" style="color:blue;">"&nbsp;,&nbsp;sqlstate&nbsp;:&nbsp;"</span>,&nbsp;sqlstate)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;<span class="keyword" style="color:#7F0055;font-weight:bold;">return</span>&nbsp;close_db(db)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">end&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">--删除表&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">local&nbsp;drop_table_sql&nbsp;=&nbsp;<span class="string" style="color:blue;">"drop&nbsp;table&nbsp;if&nbsp;exists&nbsp;test"</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">res,&nbsp;err,&nbsp;errno,&nbsp;sqlstate&nbsp;=&nbsp;db:query(drop_table_sql)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;"><span class="keyword" style="color:#7F0055;font-weight:bold;">if</span>&nbsp;not&nbsp;res&nbsp;then&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;ngx.say(<span class="string" style="color:blue;">"drop&nbsp;table&nbsp;error&nbsp;:&nbsp;"</span>,&nbsp;err,&nbsp;<span class="string" style="color:blue;">"&nbsp;,&nbsp;errno&nbsp;:&nbsp;"</span>,&nbsp;errno,&nbsp;<span class="string" style="color:blue;">"&nbsp;,&nbsp;sqlstate&nbsp;:&nbsp;"</span>,&nbsp;sqlstate)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;<span class="keyword" style="color:#7F0055;font-weight:bold;">return</span>&nbsp;close_db(db)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">end&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">--创建表&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">local&nbsp;create_table_sql&nbsp;=&nbsp;<span class="string" style="color:blue;">"create&nbsp;table&nbsp;test(id&nbsp;int&nbsp;primary&nbsp;key&nbsp;auto_increment,&nbsp;ch&nbsp;varchar(100))"</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">res,&nbsp;err,&nbsp;errno,&nbsp;sqlstate&nbsp;=&nbsp;db:query(create_table_sql)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;"><span class="keyword" style="color:#7F0055;font-weight:bold;">if</span>&nbsp;not&nbsp;res&nbsp;then&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;ngx.say(<span class="string" style="color:blue;">"create&nbsp;table&nbsp;error&nbsp;:&nbsp;"</span>,&nbsp;err,&nbsp;<span class="string" style="color:blue;">"&nbsp;,&nbsp;errno&nbsp;:&nbsp;"</span>,&nbsp;errno,&nbsp;<span class="string" style="color:blue;">"&nbsp;,&nbsp;sqlstate&nbsp;:&nbsp;"</span>,&nbsp;sqlstate)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;<span class="keyword" style="color:#7F0055;font-weight:bold;">return</span>&nbsp;close_db(db)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">end&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">--插入&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">local&nbsp;insert_sql&nbsp;=&nbsp;<span class="string" style="color:blue;">"insert&nbsp;into&nbsp;test&nbsp;(ch)&nbsp;values('hello')"</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">res,&nbsp;err,&nbsp;errno,&nbsp;sqlstate&nbsp;=&nbsp;db:query(insert_sql)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;"><span class="keyword" style="color:#7F0055;font-weight:bold;">if</span>&nbsp;not&nbsp;res&nbsp;then&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;ngx.say(<span class="string" style="color:blue;">"insert&nbsp;error&nbsp;:&nbsp;"</span>,&nbsp;err,&nbsp;<span class="string" style="color:blue;">"&nbsp;,&nbsp;errno&nbsp;:&nbsp;"</span>,&nbsp;errno,&nbsp;<span class="string" style="color:blue;">"&nbsp;,&nbsp;sqlstate&nbsp;:&nbsp;"</span>,&nbsp;sqlstate)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;<span class="keyword" style="color:#7F0055;font-weight:bold;">return</span>&nbsp;close_db(db)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">end&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">res,&nbsp;err,&nbsp;errno,&nbsp;sqlstate&nbsp;=&nbsp;db:query(insert_sql)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">ngx.say(<span class="string" style="color:blue;">"insert&nbsp;rows&nbsp;:&nbsp;"</span>,&nbsp;res.affected_rows,&nbsp;<span class="string" style="color:blue;">"&nbsp;,&nbsp;id&nbsp;:&nbsp;"</span>,&nbsp;res.insert_id,&nbsp;<span class="string" style="color:blue;">"&lt;br/&gt;"</span>)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">--更新&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">local&nbsp;update_sql&nbsp;=&nbsp;<span class="string" style="color:blue;">"update&nbsp;test&nbsp;set&nbsp;ch&nbsp;=&nbsp;'hello2'&nbsp;where&nbsp;id&nbsp;="</span>&nbsp;..&nbsp;res.insert_id&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">res,&nbsp;err,&nbsp;errno,&nbsp;sqlstate&nbsp;=&nbsp;db:query(update_sql)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;"><span class="keyword" style="color:#7F0055;font-weight:bold;">if</span>&nbsp;not&nbsp;res&nbsp;then&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;ngx.say(<span class="string" style="color:blue;">"update&nbsp;error&nbsp;:&nbsp;"</span>,&nbsp;err,&nbsp;<span class="string" style="color:blue;">"&nbsp;,&nbsp;errno&nbsp;:&nbsp;"</span>,&nbsp;errno,&nbsp;<span class="string" style="color:blue;">"&nbsp;,&nbsp;sqlstate&nbsp;:&nbsp;"</span>,&nbsp;sqlstate)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;<span class="keyword" style="color:#7F0055;font-weight:bold;">return</span>&nbsp;close_db(db)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">end&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">ngx.say(<span class="string" style="color:blue;">"update&nbsp;rows&nbsp;:&nbsp;"</span>,&nbsp;res.affected_rows,&nbsp;<span class="string" style="color:blue;">"&lt;br/&gt;"</span>)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">--查询&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">local&nbsp;select_sql&nbsp;=&nbsp;<span class="string" style="color:blue;">"select&nbsp;id,&nbsp;ch&nbsp;from&nbsp;test"</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">res,&nbsp;err,&nbsp;errno,&nbsp;sqlstate&nbsp;=&nbsp;db:query(select_sql)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;"><span class="keyword" style="color:#7F0055;font-weight:bold;">if</span>&nbsp;not&nbsp;res&nbsp;then&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;ngx.say(<span class="string" style="color:blue;">"select&nbsp;error&nbsp;:&nbsp;"</span>,&nbsp;err,&nbsp;<span class="string" style="color:blue;">"&nbsp;,&nbsp;errno&nbsp;:&nbsp;"</span>,&nbsp;errno,&nbsp;<span class="string" style="color:blue;">"&nbsp;,&nbsp;sqlstate&nbsp;:&nbsp;"</span>,&nbsp;sqlstate)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;<span class="keyword" style="color:#7F0055;font-weight:bold;">return</span>&nbsp;close_db(db)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">end&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;"><span class="keyword" style="color:#7F0055;font-weight:bold;">for</span>&nbsp;i,&nbsp;row&nbsp;in&nbsp;ipairs(res)&nbsp;<span class="keyword" style="color:#7F0055;font-weight:bold;">do</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;<span class="keyword" style="color:#7F0055;font-weight:bold;">for</span>&nbsp;name,&nbsp;value&nbsp;in&nbsp;pairs(row)&nbsp;<span class="keyword" style="color:#7F0055;font-weight:bold;">do</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ngx.say(<span class="string" style="color:blue;">"select&nbsp;row&nbsp;"</span>,&nbsp;i,&nbsp;<span class="string" style="color:blue;">"&nbsp;:&nbsp;"</span>,&nbsp;name,&nbsp;<span class="string" style="color:blue;">"&nbsp;=&nbsp;"</span>,&nbsp;value,&nbsp;<span class="string" style="color:blue;">"&lt;br/&gt;"</span>)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;end&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">end&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">ngx.say(<span class="string" style="color:blue;">"&lt;br/&gt;"</span>)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">--防止sql注入&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">local&nbsp;ch_param&nbsp;=&nbsp;ngx.req.get_uri_args()[<span class="string" style="color:blue;">"ch"</span>]&nbsp;or&nbsp;<span class="string" style="color:blue;">''</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">--使用ngx.quote_sql_str防止sql注入&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">local&nbsp;query_sql&nbsp;=&nbsp;<span class="string" style="color:blue;">"select&nbsp;id,&nbsp;ch&nbsp;from&nbsp;test&nbsp;where&nbsp;ch&nbsp;=&nbsp;"</span>&nbsp;..&nbsp;ngx.quote_sql_str(ch_param)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">res,&nbsp;err,&nbsp;errno,&nbsp;sqlstate&nbsp;=&nbsp;db:query(query_sql)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;"><span class="keyword" style="color:#7F0055;font-weight:bold;">if</span>&nbsp;not&nbsp;res&nbsp;then&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;ngx.say(<span class="string" style="color:blue;">"select&nbsp;error&nbsp;:&nbsp;"</span>,&nbsp;err,&nbsp;<span class="string" style="color:blue;">"&nbsp;,&nbsp;errno&nbsp;:&nbsp;"</span>,&nbsp;errno,&nbsp;<span class="string" style="color:blue;">"&nbsp;,&nbsp;sqlstate&nbsp;:&nbsp;"</span>,&nbsp;sqlstate)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;<span class="keyword" style="color:#7F0055;font-weight:bold;">return</span>&nbsp;close_db(db)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">end&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;"><span class="keyword" style="color:#7F0055;font-weight:bold;">for</span>&nbsp;i,&nbsp;row&nbsp;in&nbsp;ipairs(res)&nbsp;<span class="keyword" style="color:#7F0055;font-weight:bold;">do</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;<span class="keyword" style="color:#7F0055;font-weight:bold;">for</span>&nbsp;name,&nbsp;value&nbsp;in&nbsp;pairs(row)&nbsp;<span class="keyword" style="color:#7F0055;font-weight:bold;">do</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ngx.say(<span class="string" style="color:blue;">"select&nbsp;row&nbsp;"</span>,&nbsp;i,&nbsp;<span class="string" style="color:blue;">"&nbsp;:&nbsp;"</span>,&nbsp;name,&nbsp;<span class="string" style="color:blue;">"&nbsp;=&nbsp;"</span>,&nbsp;value,&nbsp;<span class="string" style="color:blue;">"&lt;br/&gt;"</span>)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;end&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">end&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">--删除&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">local&nbsp;delete_sql&nbsp;=&nbsp;<span class="string" style="color:blue;">"delete&nbsp;from&nbsp;test"</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">res,&nbsp;err,&nbsp;errno,&nbsp;sqlstate&nbsp;=&nbsp;db:query(delete_sql)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;"><span class="keyword" style="color:#7F0055;font-weight:bold;">if</span>&nbsp;not&nbsp;res&nbsp;then&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;ngx.say(<span class="string" style="color:blue;">"delete&nbsp;error&nbsp;:&nbsp;"</span>,&nbsp;err,&nbsp;<span class="string" style="color:blue;">"&nbsp;,&nbsp;errno&nbsp;:&nbsp;"</span>,&nbsp;errno,&nbsp;<span class="string" style="color:blue;">"&nbsp;,&nbsp;sqlstate&nbsp;:&nbsp;"</span>,&nbsp;sqlstate)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;<span class="keyword" style="color:#7F0055;font-weight:bold;">return</span>&nbsp;close_db(db)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">end&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">ngx.say(<span class="string" style="color:blue;">"delete&nbsp;rows&nbsp;:&nbsp;"</span>,&nbsp;res.affected_rows,&nbsp;<span class="string" style="color:blue;">"&lt;br/&gt;"</span>)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">close_db(db)&nbsp;&nbsp;</span>
			</li>
		</ol>
	</div>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		&nbsp;
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		对于新增/修改/删除会返回如下格式的响应：
	</p>
	<div class="dp-highlighter" id="" style="font-family:Monaco, &quot;font-size:12px;background-color:transparent;width:679px;overflow:auto;margin-left:9px;padding:1px;word-break:break-all;">
		<div class="bar">
			<div class="tools" style="padding:3px;margin:0px;font-weight:bold;">
				Java代码&nbsp;&nbsp;<a title="收藏这段代码" style="color:#108AC6;text-decoration-line:underline;"><img class="star" src="http://jinnianshilongnian.iteye.com/images/icon_star.png" alt="收藏代码" /></a>
			</div>
		</div>
		<ol start="1" class="dp-j" style="font-size:1em;line-height:1.4em;margin:0px 0px 1px;padding:2px 0px;border:1px solid #D1D7DC;list-style-position:initial;list-style-image:initial;color:#2B91AF;">
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">{&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;insert_id&nbsp;=&nbsp;<span class="number" style="color:#C00000;">0</span>,&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;server_status&nbsp;=&nbsp;<span class="number" style="color:#C00000;">2</span>,&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;warning_count&nbsp;=&nbsp;<span class="number" style="color:#C00000;">1</span>,&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;affected_rows&nbsp;=&nbsp;<span class="number" style="color:#C00000;">32</span>,&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;message&nbsp;=&nbsp;nil&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">}&nbsp;&nbsp;</span>
			</li>
		</ol>
	</div>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		affected_rows表示操作影响的行数，insert_id是在使用自增序列时产生的id。
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		&nbsp;
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		对于查询会返回如下格式的响应：
	</p>
	<div class="dp-highlighter" id="" style="font-family:Monaco, &quot;font-size:12px;background-color:transparent;width:679px;overflow:auto;margin-left:9px;padding:1px;word-break:break-all;">
		<div class="bar">
			<div class="tools" style="padding:3px;margin:0px;font-weight:bold;">
				Java代码&nbsp;&nbsp;<a title="收藏这段代码" style="color:#108AC6;text-decoration-line:underline;"><img class="star" src="http://jinnianshilongnian.iteye.com/images/icon_star.png" alt="收藏代码" /></a>
			</div>
		</div>
		<ol start="1" class="dp-j" style="font-size:1em;line-height:1.4em;margin:0px 0px 1px;padding:2px 0px;border:1px solid #D1D7DC;list-style-position:initial;list-style-image:initial;color:#2B91AF;">
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">{&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;{&nbsp;id=&nbsp;<span class="number" style="color:#C00000;">1</span>,&nbsp;ch=&nbsp;<span class="string" style="color:blue;">"hello"</span>},&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;{&nbsp;id=&nbsp;<span class="number" style="color:#C00000;">2</span>,&nbsp;ch=&nbsp;<span class="string" style="color:blue;">"hello2"</span>}&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">}&nbsp;&nbsp;</span>
			</li>
		</ol>
	</div>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		null将返回ngx.null。
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		&nbsp;
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		2、example.conf配置文件
	</p>
	<div class="dp-highlighter" id="" style="font-family:Monaco, &quot;font-size:12px;background-color:transparent;width:679px;overflow:auto;margin-left:9px;padding:1px;word-break:break-all;">
		<div class="bar">
			<div class="tools" style="padding:3px;margin:0px;font-weight:bold;">
				Java代码&nbsp;&nbsp;<a title="收藏这段代码" style="color:#108AC6;text-decoration-line:underline;"><img class="star" src="http://jinnianshilongnian.iteye.com/images/icon_star.png" alt="收藏代码" /></a>
			</div>
		</div>
		<ol start="1" class="dp-j" style="font-size:1em;line-height:1.4em;margin:0px 0px 1px;padding:2px 0px;border:1px solid #D1D7DC;list-style-position:initial;list-style-image:initial;color:#2B91AF;">
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">location&nbsp;/lua_mysql&nbsp;{&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;default_type&nbsp;<span class="string" style="color:blue;">'text/html'</span>;&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;lua_code_cache&nbsp;on;&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;content_by_lua_file&nbsp;/usr/example/lua/test_mysql.lua;&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">}&nbsp;&nbsp;</span>
			</li>
		</ol>
	</div>
&nbsp;
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		3、访问如http://192.168.1.2/lua_mysql?ch=hello进行测试，得到如下结果
	</p>
	<div class="dp-highlighter" id="" style="font-family:Monaco, &quot;font-size:12px;background-color:transparent;width:679px;overflow:auto;margin-left:9px;padding:1px;word-break:break-all;">
		<div class="bar">
			<div class="tools" style="padding:3px;margin:0px;font-weight:bold;">
				Java代码&nbsp;&nbsp;<a title="收藏这段代码" style="color:#108AC6;text-decoration-line:underline;"><img class="star" src="http://jinnianshilongnian.iteye.com/images/icon_star.png" alt="收藏代码" /></a>
			</div>
		</div>
		<ol start="1" class="dp-j" style="font-size:1em;line-height:1.4em;margin:0px 0px 1px;padding:2px 0px;border:1px solid #D1D7DC;list-style-position:initial;list-style-image:initial;color:#2B91AF;">
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">insert&nbsp;rows&nbsp;:&nbsp;<span class="number" style="color:#C00000;">1</span>&nbsp;,&nbsp;id&nbsp;:&nbsp;<span class="number" style="color:#C00000;">2</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">update&nbsp;rows&nbsp;:&nbsp;<span class="number" style="color:#C00000;">1</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">select&nbsp;row&nbsp;<span class="number" style="color:#C00000;">1</span>&nbsp;:&nbsp;ch&nbsp;=&nbsp;hello&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">select&nbsp;row&nbsp;<span class="number" style="color:#C00000;">1</span>&nbsp;:&nbsp;id&nbsp;=&nbsp;<span class="number" style="color:#C00000;">1</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">select&nbsp;row&nbsp;<span class="number" style="color:#C00000;">2</span>&nbsp;:&nbsp;ch&nbsp;=&nbsp;hello2&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">select&nbsp;row&nbsp;<span class="number" style="color:#C00000;">2</span>&nbsp;:&nbsp;id&nbsp;=&nbsp;<span class="number" style="color:#C00000;">2</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">select&nbsp;row&nbsp;<span class="number" style="color:#C00000;">1</span>&nbsp;:&nbsp;ch&nbsp;=&nbsp;hello&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">select&nbsp;row&nbsp;<span class="number" style="color:#C00000;">1</span>&nbsp;:&nbsp;id&nbsp;=&nbsp;<span class="number" style="color:#C00000;">1</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">delete&nbsp;rows&nbsp;:&nbsp;<span class="number" style="color:#C00000;">2</span>&nbsp;&nbsp;</span>
			</li>
		</ol>
	</div>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		客户端目前还没有提供预编译SQL支持（即占位符替换位置变量），这样在入参时记得使用ngx.quote_sql_str进行字符串转义，防止sql注入；连接池和之前Redis客户端完全一样就不介绍了。
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		&nbsp;
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		对于Mysql客户端的介绍基本够用了，更多请参考<a target="_blank" href="https://github.com/openresty/lua-resty-mysql" style="color:#108AC6;">https://github.com/openresty/lua-resty-mysql</a>。
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		&nbsp;
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		其他如MongoDB等数据库的客户端可以从github上查找使用。
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		&nbsp;
	</p>
	<h2 style="line-height:1.5em;margin:0px 0px 0.5em;padding:0px;">
		Http客户端
	</h2>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		OpenResty默认没有提供Http客户端，需要使用第三方提供；当然我们可以通过ngx.location.capture&nbsp;去方式实现，但是有一些限制，后边我们再做介绍。
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		&nbsp;
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		我们可以从github上搜索相应的客户端，比如<a href="https://github.com/pintsized/lua-resty-http" style="color:#108AC6;">https://github.com/pintsized/lua-resty-http</a>。
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		&nbsp;
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		<strong>lua-resty-http</strong>
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		&nbsp;
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		1、下载lua-resty-http客户端到lualib<span style="line-height:1.5;">&nbsp;</span>
	</p>
	<div class="dp-highlighter" id="" style="font-family:Monaco, &quot;font-size:12px;background-color:transparent;width:679px;overflow:auto;margin-left:9px;padding:1px;word-break:break-all;">
		<div class="bar">
			<div class="tools" style="padding:3px;margin:0px;font-weight:bold;">
				Java代码&nbsp;&nbsp;<a title="收藏这段代码" style="color:#108AC6;text-decoration-line:underline;"><img class="star" src="http://jinnianshilongnian.iteye.com/images/icon_star.png" alt="收藏代码" /></a>
			</div>
		</div>
		<ol start="1" class="dp-j" style="font-size:1em;line-height:1.4em;margin:0px 0px 1px;padding:2px 0px;border:1px solid #D1D7DC;list-style-position:initial;list-style-image:initial;color:#2B91AF;">
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">cd&nbsp;/usr/example/lualib/resty/&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">wget&nbsp;https:<span class="comment" style="color:#008200;padding:0px;margin:0px;width:auto;border:0px;">//raw.githubusercontent.com/pintsized/lua-resty-http/master/lib/resty/http_headers.lua</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">wget&nbsp;https:<span class="comment" style="color:#008200;padding:0px;margin:0px;width:auto;border:0px;">//raw.githubusercontent.com/pintsized/lua-resty-http/master/lib/resty/http.lua</span>&nbsp;&nbsp;</span>
			</li>
		</ol>
	</div>
&nbsp;
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		2、test_http_1.lua
	</p>
	<div class="dp-highlighter" id="" style="font-family:Monaco, &quot;font-size:12px;background-color:transparent;width:679px;overflow:auto;margin-left:9px;padding:1px;word-break:break-all;">
		<div class="bar">
			<div class="tools" style="padding:3px;margin:0px;font-weight:bold;">
				Java代码&nbsp;&nbsp;<a title="收藏这段代码" style="color:#108AC6;text-decoration-line:underline;"><img class="star" src="http://jinnianshilongnian.iteye.com/images/icon_star.png" alt="收藏代码" /></a>
			</div>
		</div>
		<ol start="1" class="dp-j" style="font-size:1em;line-height:1.4em;margin:0px 0px 1px;padding:2px 0px;border:1px solid #D1D7DC;list-style-position:initial;list-style-image:initial;color:#2B91AF;">
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">local&nbsp;http&nbsp;=&nbsp;require(<span class="string" style="color:blue;">"resty.http"</span>)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">--创建http客户端实例&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">local&nbsp;httpc&nbsp;=&nbsp;http.<span class="keyword" style="color:#7F0055;font-weight:bold;">new</span>()&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">local&nbsp;resp,&nbsp;err&nbsp;=&nbsp;httpc:request_uri(<span class="string" style="color:blue;">"http://s.taobao.com"</span>,&nbsp;{&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;method&nbsp;=&nbsp;<span class="string" style="color:blue;">"GET"</span>,&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;path&nbsp;=&nbsp;<span class="string" style="color:blue;">"/search?q=hello"</span>,&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;headers&nbsp;=&nbsp;{&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[<span class="string" style="color:blue;">"User-Agent"</span>]&nbsp;=&nbsp;<span class="string" style="color:blue;">"Mozilla/5.0&nbsp;(Windows&nbsp;NT&nbsp;6.1;&nbsp;WOW64)&nbsp;AppleWebKit/537.36&nbsp;(KHTML,&nbsp;like&nbsp;Gecko)&nbsp;Chrome/40.0.2214.111&nbsp;Safari/537.36"</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;}&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">})&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;"><span class="keyword" style="color:#7F0055;font-weight:bold;">if</span>&nbsp;not&nbsp;resp&nbsp;then&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;ngx.say(<span class="string" style="color:blue;">"request&nbsp;error&nbsp;:"</span>,&nbsp;err)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;<span class="keyword" style="color:#7F0055;font-weight:bold;">return</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">end&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">--获取状态码&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">ngx.status&nbsp;=&nbsp;resp.status&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">--获取响应头&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;"><span class="keyword" style="color:#7F0055;font-weight:bold;">for</span>&nbsp;k,&nbsp;v&nbsp;in&nbsp;pairs(resp.headers)&nbsp;<span class="keyword" style="color:#7F0055;font-weight:bold;">do</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;<span class="keyword" style="color:#7F0055;font-weight:bold;">if</span>&nbsp;k&nbsp;~=&nbsp;<span class="string" style="color:blue;">"Transfer-Encoding"</span>&nbsp;and&nbsp;k&nbsp;~=&nbsp;<span class="string" style="color:blue;">"Connection"</span>&nbsp;then&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ngx.header[k]&nbsp;=&nbsp;v&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;end&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">end&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">--响应体&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">ngx.say(resp.body)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">httpc:close()&nbsp;&nbsp;</span>
			</li>
		</ol>
	</div>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		&nbsp;
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		响应头中的Transfer-Encoding和Connection可以忽略，因为这个数据是当前server输出的。
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		&nbsp;
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		3、example.conf配置文件
	</p>
	<div class="dp-highlighter" id="" style="font-family:Monaco, &quot;font-size:12px;background-color:transparent;width:679px;overflow:auto;margin-left:9px;padding:1px;word-break:break-all;">
		<div class="bar">
			<div class="tools" style="padding:3px;margin:0px;font-weight:bold;">
				Java代码&nbsp;&nbsp;<a title="收藏这段代码" style="color:#108AC6;text-decoration-line:underline;"><img class="star" src="http://jinnianshilongnian.iteye.com/images/icon_star.png" alt="收藏代码" /></a>
			</div>
		</div>
		<ol start="1" class="dp-j" style="font-size:1em;line-height:1.4em;margin:0px 0px 1px;padding:2px 0px;border:1px solid #D1D7DC;list-style-position:initial;list-style-image:initial;color:#2B91AF;">
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">location&nbsp;/lua_http_1&nbsp;{&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;default_type&nbsp;<span class="string" style="color:blue;">'text/html'</span>;&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;lua_code_cache&nbsp;on;&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;content_by_lua_file&nbsp;/usr/example/lua/test_http_1.lua;&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">}&nbsp;&nbsp;</span>
			</li>
		</ol>
	</div>
</div>
<div class="iteye-blog-content-contain" style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	4、在nginx.conf中的http部分添加如下指令来做DNS解析
</div>
<div class="iteye-blog-content-contain" style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<div class="dp-highlighter" id="" style="font-family:Monaco, &quot;font-size:12px;background-color:transparent;width:679px;overflow:auto;margin-left:9px;padding:1px;word-break:break-all;">
		<div class="bar">
			<div class="tools" style="padding:3px;margin:0px;font-weight:bold;">
				Java代码&nbsp;&nbsp;<a title="收藏这段代码" style="color:#108AC6;text-decoration-line:underline;"><img class="star" src="http://jinnianshilongnian.iteye.com/images/icon_star.png" alt="收藏代码" /></a>
			</div>
		</div>
		<ol start="1" class="dp-j" style="font-size:1em;line-height:1.4em;margin:0px 0px 1px;padding:2px 0px;border:1px solid #D1D7DC;list-style-position:initial;list-style-image:initial;color:#2B91AF;">
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">resolver&nbsp;<span class="number" style="color:#C00000;">8.8</span>.<span class="number" style="color:#C00000;">8.8</span>;&nbsp;&nbsp;</span>
			</li>
		</ol>
	</div>
</div>
<div class="iteye-blog-content-contain" style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	记得要配置DNS解析器resolver 8.8.8.8，否则域名是无法解析的。
</div>
<div class="iteye-blog-content-contain" style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	5、访问如http://192.168.1.2/lua_http_1会看到淘宝的搜索界面。
</div>
<div class="iteye-blog-content-contain" style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		<span style="line-height:1.5;font-family:宋体;">使用方式比较简单，如超时和连接池设置和之前Redis客户端一样，不再阐述。更多客户端使用规则请参考<a target="_blank" href="https://github.com/pintsized/lua-resty-http" style="color:#108AC6;">https://github.com/pintsized/lua-resty-http</a>。</span>
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		&nbsp;
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		<strong><span style="line-height:1.5;font-family:宋体;">ngx.location.capture</span></strong>
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		ngx.location.capture也可以用来完成http请求，但是它只能请求到相对于当前nginx服务器的路径，不能使用之前的绝对路径进行访问，但是我们可以配合nginx upstream实现我们想要的功能。
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		&nbsp;
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		1、在nginx.cong中的http部分添加如下upstream配置
	</p>
	<div class="dp-highlighter" id="" style="font-family:Monaco, &quot;font-size:12px;background-color:transparent;width:679px;overflow:auto;margin-left:9px;padding:1px;word-break:break-all;">
		<div class="bar">
			<div class="tools" style="padding:3px;margin:0px;font-weight:bold;">
				Java代码&nbsp;&nbsp;<a title="收藏这段代码" style="color:#108AC6;text-decoration-line:underline;"><img class="star" src="http://jinnianshilongnian.iteye.com/images/icon_star.png" alt="收藏代码" /></a>
			</div>
		</div>
		<ol start="1" class="dp-j" style="font-size:1em;line-height:1.4em;margin:0px 0px 1px;padding:2px 0px;border:1px solid #D1D7DC;list-style-position:initial;list-style-image:initial;color:#2B91AF;">
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">upstream&nbsp;backend&nbsp;{&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;server&nbsp;s.taobao.com;&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;keepalive&nbsp;<span class="number" style="color:#C00000;">100</span>;&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">}&nbsp;&nbsp;</span>
			</li>
		</ol>
	</div>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		即我们将请求upstream到backend；另外记得一定要添加之前的DNS解析器。
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		&nbsp;
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		2、在example.conf配置如下location
	</p>
	<div class="dp-highlighter" id="" style="font-family:Monaco, &quot;font-size:12px;background-color:transparent;width:679px;overflow:auto;margin-left:9px;padding:1px;word-break:break-all;">
		<div class="bar">
			<div class="tools" style="padding:3px;margin:0px;font-weight:bold;">
				Java代码&nbsp;&nbsp;<a title="收藏这段代码" style="color:#108AC6;text-decoration-line:underline;"><img class="star" src="http://jinnianshilongnian.iteye.com/images/icon_star.png" alt="收藏代码" /></a>
			</div>
		</div>
		<ol start="1" class="dp-j" style="font-size:1em;line-height:1.4em;margin:0px 0px 1px;padding:2px 0px;border:1px solid #D1D7DC;list-style-position:initial;list-style-image:initial;color:#2B91AF;">
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">location&nbsp;~&nbsp;/proxy/(.*)&nbsp;{&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;internal;&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;proxy_pass&nbsp;http:<span class="comment" style="color:#008200;padding:0px;margin:0px;width:auto;border:0px;">//backend/$1$is_args$args;</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">}&nbsp;&nbsp;</span>
			</li>
		</ol>
	</div>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		internal表示只能内部访问，即外部无法通过url访问进来； 并通过proxy_pass将请求转发到upstream。
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		&nbsp;
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		3、test_http_2.lua
	</p>
	<div class="dp-highlighter" id="" style="font-family:Monaco, &quot;font-size:12px;background-color:transparent;width:679px;overflow:auto;margin-left:9px;padding:1px;word-break:break-all;">
		<div class="bar">
			<div class="tools" style="padding:3px;margin:0px;font-weight:bold;">
				Java代码&nbsp;&nbsp;<a title="收藏这段代码" style="color:#108AC6;text-decoration-line:underline;"><img class="star" src="http://jinnianshilongnian.iteye.com/images/icon_star.png" alt="收藏代码" /></a>
			</div>
		</div>
		<ol start="1" class="dp-j" style="font-size:1em;line-height:1.4em;margin:0px 0px 1px;padding:2px 0px;border:1px solid #D1D7DC;list-style-position:initial;list-style-image:initial;color:#2B91AF;">
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">local&nbsp;resp&nbsp;=&nbsp;ngx.location.capture(<span class="string" style="color:blue;">"/proxy/search"</span>,&nbsp;{&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;method&nbsp;=&nbsp;ngx.HTTP_GET,&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;args&nbsp;=&nbsp;{q&nbsp;=&nbsp;<span class="string" style="color:blue;">"hello"</span>}&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">})&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;"><span class="keyword" style="color:#7F0055;font-weight:bold;">if</span>&nbsp;not&nbsp;resp&nbsp;then&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;ngx.say(<span class="string" style="color:blue;">"request&nbsp;error&nbsp;:"</span>,&nbsp;err)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;<span class="keyword" style="color:#7F0055;font-weight:bold;">return</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">end&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">ngx.log(ngx.ERR,&nbsp;tostring(resp.status))&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">--获取状态码&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">ngx.status&nbsp;=&nbsp;resp.status&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">--获取响应头&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;"><span class="keyword" style="color:#7F0055;font-weight:bold;">for</span>&nbsp;k,&nbsp;v&nbsp;in&nbsp;pairs(resp.header)&nbsp;<span class="keyword" style="color:#7F0055;font-weight:bold;">do</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;<span class="keyword" style="color:#7F0055;font-weight:bold;">if</span>&nbsp;k&nbsp;~=&nbsp;<span class="string" style="color:blue;">"Transfer-Encoding"</span>&nbsp;and&nbsp;k&nbsp;~=&nbsp;<span class="string" style="color:blue;">"Connection"</span>&nbsp;then&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ngx.header[k]&nbsp;=&nbsp;v&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;end&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">end&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">--响应体&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;"><span class="keyword" style="color:#7F0055;font-weight:bold;">if</span>&nbsp;resp.body&nbsp;then&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;ngx.say(resp.body)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">end&nbsp;&nbsp;</span>
			</li>
		</ol>
	</div>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		通过<a target="_blank" href="http://wiki.nginx.org/HttpLuaModule#ngx.location.capture" style="color:#108AC6;">ngx.location.capture</a>发送一个子请求，此处因为是子请求，所有请求头继承自当前请求，还有如ngx.ctx和ngx.var是否继承可以参考官方文档<a target="_blank" href="http://wiki.nginx.org/HttpLuaModule#ngx.location.capture" style="color:#108AC6;">http://wiki.nginx.org/HttpLuaModule#ngx.location.capture</a>。&nbsp;另外还提供了ngx.location.capture_multi用于并发发出多个请求，这样总的响应时间是最慢的一个，批量调用时有用。
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		&nbsp;
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		4、example.conf配置文件
	</p>
	<div class="dp-highlighter" id="" style="font-family:Monaco, &quot;font-size:12px;background-color:transparent;width:679px;overflow:auto;margin-left:9px;padding:1px;word-break:break-all;">
		<div class="bar">
			<div class="tools" style="padding:3px;margin:0px;font-weight:bold;">
				Java代码&nbsp;&nbsp;<a title="收藏这段代码" style="color:#108AC6;text-decoration-line:underline;"><img class="star" src="http://jinnianshilongnian.iteye.com/images/icon_star.png" alt="收藏代码" /></a>
			</div>
		</div>
		<ol start="1" class="dp-j" style="font-size:1em;line-height:1.4em;margin:0px 0px 1px;padding:2px 0px;border:1px solid #D1D7DC;list-style-position:initial;list-style-image:initial;color:#2B91AF;">
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">location&nbsp;/lua_http_2&nbsp;{&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;default_type&nbsp;<span class="string" style="color:blue;">'text/html'</span>;&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;lua_code_cache&nbsp;on;&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;content_by_lua_file&nbsp;/usr/example/lua/test_http_2.lua;&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">}&nbsp;&nbsp;</span>
			</li>
		</ol>
	</div>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		&nbsp;
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		5、访问如http://192.168.1.2/lua_http_2进行测试可以看到淘宝搜索界面。
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		&nbsp;
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		我们通过upstream+<span style="line-height:1.5;font-family:宋体;">ngx.location.capture方式虽然麻烦点，但是得到更好的性能和upstream的连接池、负载均衡、故障转移、proxy cache等特性。</span>
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		&nbsp;
	</p>
	<p class="MsoNormal" style="margin-top:0px;margin-bottom:0px;padding:0px;">
		<span style="line-height:1.5;font-family:宋体;">不过因为继承在当前请求的请求头，所以可能会存在一些问题，比较常见的就是gzip压缩问题，</span><span style="line-height:1.5;font-family:宋体;">ngx.location.capture不会解压缩后端服务器的GZIP内容，解决办法可以参考<a target="_blank" href="https://github.com/openresty/lua-nginx-module/issues/12" style="color:#108AC6;">https://github.com/openresty/lua-nginx-module/issues/12</a>；因为我们大部分这种http调用的都是内部服务，因此完全可以在proxy location中添</span><span style="line-height:1.5;font-family:宋体;">加</span><span style="line-height:1.5;font-family:宋体;">proxy_pass_request_headers&nbsp;off;来不传递请求头。</span>
	</p>
</div>