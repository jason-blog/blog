<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<strong><span style="font-size:small;">python发送GET或POST请求以便干一些趣事</span></strong>
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<strong>适合级别：</strong>入门，中级
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<strong>关键字 &nbsp; ：</strong>python, http, GET, POST, 安全, 模拟, 浏览器, 验证码,图片识别, google&nbsp;
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<strong>1 此</strong>文不是关于黑客或安全话题的！
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<strong>2 使</strong>用脚本程序发送GET或POST，这是最简单也是最常见最频繁的事情之一；那为什么我还要YY一遍呢？ 因为不只是熟能生巧，熟还能生出好多东西来呢，就看是和谁生！
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<strong>3 我</strong>想有必要再次温习一遍HTTP协议及GET/POST请求相应内容与格式等基础知识的；不过我不会在此简述，希望你去看看那些诸如“当你使用浏览器打开一个URL，究竟发生了哪些事”这样的文章吧！
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<strong>4 py</strong>thon发送GET/POST可能涉及的lib: &nbsp;urllib, urllib2, cookielib ;至于其他的诸如处理HTML等不在本话题范围内:)
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<strong>5 请</strong>求google.com的首页：
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<div class="dp-highlighter" id="" style="font-family:Monaco, &quot;background-color:#FFFFFF;width:679px;overflow:auto;margin-left:9px;padding:1px;word-break:break-all;white-space:normal;">
	<div class="bar">
		<div class="tools" style="padding:3px;margin:0px;font-weight:bold;">
			Python代码&nbsp;&nbsp;<a title="收藏这段代码" style="color:#006600;text-decoration-line:underline;"><img class="star" src="http://nodex.iteye.com/images/icon_star.png" alt="收藏代码" /></a>
		</div>
	</div>
	<ol start="1" class="dp-py" style="font-size:1em;line-height:1.4em;margin:0px 0px 1px;padding:2px 0px;border:1px solid #D1D7DC;list-style-position:initial;list-style-image:initial;color:#2B91AF;">
		<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
			<span style="color:black;">&gt;&gt;&gt;&nbsp;<span class="keyword" style="color:#7F0055;font-weight:bold;">import</span>&nbsp;urllib2&nbsp;&nbsp;</span>
		</li>
		<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
			<span style="color:black;">&gt;&gt;&gt;&nbsp;<span class="keyword" style="color:#7F0055;font-weight:bold;">print</span>&nbsp;urllib2.urlopen(<span class="string" style="color:blue;">'http://google.com'</span>).read()&nbsp;&nbsp;</span>
		</li>
	</ol>
</div>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;以上是hello world级别了；但geek程序员往往会通过此发现，打印出的东西，因URL而异 --- 废话，当然不是说内容，是指风格！！！ &nbsp;优秀的站点，其源码往往也在各个方面高一个水准，包括unicode编码、安全、性能等等方面。
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<strong>下载GOOGLE的LOGO文件</strong>
</p>
<div class="dp-highlighter" id="" style="font-family:Monaco, &quot;background-color:#FFFFFF;width:679px;overflow:auto;margin-left:9px;padding:1px;word-break:break-all;white-space:normal;">
	<div class="bar">
		<div class="tools" style="padding:3px;margin:0px;font-weight:bold;">
			Python代码&nbsp;&nbsp;<a title="收藏这段代码" style="color:#006600;text-decoration-line:underline;"><img class="star" src="http://nodex.iteye.com/images/icon_star.png" alt="收藏代码" /></a>
		</div>
	</div>
	<ol start="1" class="dp-py" style="font-size:1em;line-height:1.4em;margin:0px 0px 1px;padding:2px 0px;border:1px solid #D1D7DC;list-style-position:initial;list-style-image:initial;color:#2B91AF;">
		<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
			<span style="color:black;">open(<span class="string" style="color:blue;">'d:\\temp\\google-logo.gif'</span>,<span class="string" style="color:blue;">'wb'</span>).write(urllib2.urlopen(<span class="string" style="color:blue;">'http://www.google.com/images/logo_sm.gif'</span>).read())&nbsp;&nbsp;</span>
		</li>
	</ol>
</div>
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">&nbsp;</span>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<strong>6 模</strong>拟浏览器打开某个登录URL，并通过POST成功登录：
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	（1 这个问题的情况比较特殊，所以我打算写一个稍微全面点的，以尽可能涵盖常见情况，包括但不限于：cookies ,密码加密发送,https,简单验证码,ip限制,充分假装浏览器等等。
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	（2 POST请求发送的最小形式：
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<div class="dp-highlighter" id="" style="font-family:Monaco, &quot;background-color:#FFFFFF;width:679px;overflow:auto;margin-left:9px;padding:1px;word-break:break-all;white-space:normal;">
	<div class="bar">
		<div class="tools" style="padding:3px;margin:0px;font-weight:bold;">
			Python代码&nbsp;&nbsp;<a title="收藏这段代码" style="color:#006600;text-decoration-line:underline;"><img class="star" src="http://nodex.iteye.com/images/icon_star.png" alt="收藏代码" /></a>
		</div>
	</div>
	<ol start="1" class="dp-py" style="font-size:1em;line-height:1.4em;margin:0px 0px 1px;padding:2px 0px;border:1px solid #D1D7DC;list-style-position:initial;list-style-image:initial;color:#2B91AF;">
		<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
			<span style="color:black;">&gt;&gt;&gt;&nbsp;<span class="keyword" style="color:#7F0055;font-weight:bold;">import</span>&nbsp;urllib&nbsp;&nbsp;</span>
		</li>
		<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
			<span style="color:black;">&gt;&gt;&gt;&nbsp;<span class="keyword" style="color:#7F0055;font-weight:bold;">import</span>&nbsp;urllib2&nbsp;&nbsp;</span>
		</li>
		<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
			<span style="color:black;">&gt;&gt;&gt;&nbsp;<span class="keyword" style="color:#7F0055;font-weight:bold;">import</span>&nbsp;cookielib&nbsp;&nbsp;</span>
		</li>
		<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
			<span style="color:black;">&nbsp;&nbsp;</span>
		</li>
		<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
			<span style="color:black;">&gt;&gt;&gt;&nbsp;cj&nbsp;=&nbsp;cookielib.CookieJar()&nbsp;&nbsp;</span>
		</li>
		<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
			<span style="color:black;">&gt;&gt;&gt;&nbsp;opener&nbsp;=&nbsp;urllib2.build_opener(urllib2.HTTPCookieProcessor(cj))&nbsp;&nbsp;</span>
		</li>
		<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
			<span style="color:black;">&gt;&gt;&gt;&nbsp;opener.addheaders&nbsp;=&nbsp;[(<span class="string" style="color:blue;">'User-agent'</span>,<span class="string" style="color:blue;">'Mozilla/4.0&nbsp;(compatible;&nbsp;MSIE&nbsp;7.0;&nbsp;Windows&nbsp;NT&nbsp;5.1)'</span>)]&nbsp;&nbsp;</span>
		</li>
		<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
			<span style="color:black;">&gt;&gt;&gt;&nbsp;urllib2.install_opener(opener)&nbsp;&nbsp;</span>
		</li>
		<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
			<span style="color:black;">&gt;&gt;&gt;&nbsp;req&nbsp;=&nbsp;urllib2.Request(<span class="string" style="color:blue;">"http://xxoo.com"</span>,urllib.urlencode({<span class="string" style="color:blue;">"username"</span>:<span class="string" style="color:blue;">"root"</span>,<span class="string" style="color:blue;">"password"</span>:<span class="string" style="color:blue;">"ROOTXXOO"</span>}))&nbsp;&nbsp;</span>
		</li>
		<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
			<span style="color:black;">&gt;&gt;&gt;&nbsp;req.add_header(<span class="string" style="color:blue;">"Referer"</span>,<span class="string" style="color:blue;">"http://xxoo.com"</span>)&nbsp;&nbsp;</span>
		</li>
		<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
			<span style="color:black;">&gt;&gt;&gt;&nbsp;resp&nbsp;=&nbsp;urllib2.urlopen(req)&nbsp;&nbsp;</span>
		</li>
		<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
			<span style="color:black;">&gt;&gt;&gt;&nbsp;<span class="keyword" style="color:#7F0055;font-weight:bold;">print</span>&nbsp;resp.read()&nbsp;&nbsp;</span>
		</li>
	</ol>
</div>
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">&nbsp;</span>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	（3 一些注意事项或最佳实践：
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<strong>A</strong>&nbsp;是否因为cookie的问题而POST失败，最好使用真的浏览器登录，然后使用firebug这样的调试工具来查看实际的请求与响应头信息，以及cookie数据！
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<strong>B</strong>&nbsp;除了cookie之外，还有很多其他方法来达到一些安全或其他目的；cookie能保存的数据就4k，而且对客户端完全开放。
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<strong>C</strong>&nbsp;其实第一件重要的事情是阅读源码，肉眼解析出form及其action和参数等；搞清楚逻辑，再去模拟；但这一步往往是最开始的斗智斗勇阶段；有些程序员总是使用小把戏来调戏你，比如追加无意义参数，追加随机数并命名为看上去像业务数据的变量等，还有人喜欢玩数学，比如搞质数运算等。
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<strong>D</strong>&nbsp;验证码问题：分很多种，有的程序员比较嫩，所以你可以分析下绕过；而一般的安全验证码，则需要你自己多请求一些验证码回来建库，做特征识别；至于很变态的验证码，建议你放弃这个思路，不要非去识别不可！
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<strong>E</strong>&nbsp;网上流传的discuz!模拟登录，其实都大多是理论；真正的程序都在那些专业发帖公司那里。<img src="http://nodex.iteye.com/images/smiles/icon_biggrin.gif" alt="" />
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<strong>F</strong>&nbsp;我本来想贴一个真实的代码出来，但是担心和谐问题，所以还是作罢！
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<strong>7 熟</strong>练地掌握这些东西可以做什么？
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	答：这只是一种方式和途径，或者说一种小伎俩；做什么是你自己的事哦，能做什么就是方法本身的事了！！！低调地说，我用这个干过：刷票(投票的，刷人气的，耍点击率的，抽奖的...)；突破限制完全下载整站数据(区别于爬虫哦)；专业数据库的数据COPY；其他不和谐的勾当。。。
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<strong>8 其</strong>实只要你够geek,几乎能用curl搞定大多数问题。不过往往，我们更应该将精力放在解决问题上，而不是解决问题的工具上！<img src="http://nodex.iteye.com/images/smiles/icon_biggrin.gif" alt="" />
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<strong>2011-6-7 更新</strong>
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	关于验证码的问题：
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	1 有很多很多的人都想搞这个验证码，比如想破解，比如想写机器人，等等
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	2 验证码的问题我觉得就两张思路： 绕过，识别； 其中绕过的条件是机制本身有漏洞，识别又分自动识别和人工识别
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	3 不是所有场合都一定需要破解验证码才能继续，比如有的时候只需要人工识别即可： 一个半自动化的机器人，在需要填写验证码时，把验证码图片给出(甚至可以发送到email或者手机上)，人工识别并返回，机器人提交并继续工作 - 这是很理想也很底代价的方式之一 。
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	当然，如果你非要破解验证码不可，那就搞特征库并比对识别喽。具体思路也很简单，而且个人建议不要重头来写，用开源的即可：
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	1 大量读取验证码图片，建立原始数据库；
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	2 分析并提取特征，比如有的验证码图片很简单，就几个数字而已，你抓2W个图片拿下来分析一下，基本八九不离十了，都可以识别出；
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	3 程序里遇到验证码的时候，拿图片去特征数据库比对，得到结果。
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	4 主意事项：比如图片中字符的分隔，比如容错，比如干扰因素的排除，比如对于类似google验证码的那种扭曲等变换，就要麻烦了。。。
</p>