<p>
	http://leitelyaya.iteye.com/blog/808266
</p>
<p>
	<br />
</p>
<p>
	<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">搜索Linux DNS，映入眼帘的是鸟哥的文章：</span><a href="http://linux.vbird.org/linux_server/0350dns.php" target="_blank" style="color:#108AC6;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">http://linux.vbird.org/linux_server/0350dns.php</a><span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">这篇长达11节的文章，看到Zone文件时就开始晕菜了。&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">继续寻找下一篇文章，来自于安全中国的：</span><a href="http://www.anqn.com/os/linux/2010-03-30/a09125458.shtml" target="_blank" style="color:#108AC6;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">http://www.anqn.com/os/linux/2010-03-30/a09125458.shtml</a><span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">在战胜了瞌睡虫的同时，DNS服务器终于跑上来了。&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">以前教授给我的理念就是将域名作为一棵倒挂的树，从根节点开始解析，直至叶子节点。通过下图更明确一下：&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<img src="http://dl.iteye.com/upload/attachment/345921/d519d373-ef14-38f6-977b-db03034c0948.png" style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" /><span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">从图的描述可以得知，&nbsp;</span><strong style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">根域</strong><span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">是以“</span><span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;color:red;">点(.)</span><span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">”表示。明了这一点非常重要，因为它的意义会在Zone文件中得到体现。&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">再加上客户端的请求解析流程图，会让整个流程更加清晰明了：&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<img src="http://dl.iteye.com/upload/attachment/345934/6466bf54-5b59-324e-8178-28bb85cbb674.png" style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" /><span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">详细的请求的顺序为：&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
	<ol style="font-size:14px;line-height:1.4em;margin:0px 0px 1.5em;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;white-space:normal;background-color:#FFFFFF;">
		<li style="font-size:1em;margin:0px 0px 0.25em 30px;padding:0px;">
			客户端Host文件标识
		</li>
		<li style="font-size:1em;margin:0px 0px 0.25em 30px;padding:0px;">
			客户缓存
		</li>
		<li style="font-size:1em;margin:0px 0px 0.25em 30px;padding:0px;">
			服务器区域设定
		</li>
		<li style="font-size:1em;margin:0px 0px 0.25em 30px;padding:0px;">
			服务器缓存
		</li>
		<li style="font-size:1em;margin:0px 0px 0.25em 30px;padding:0px;">
			其它服务器
		</li>
	</ol>
<br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">理念明白后，就开始服务器的配置历程了。&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">首先，看看已经安装好的bind程序。&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
	<div class="dp-highlighter" id="" style="font-family:Monaco, &quot;background-color:#FFFFFF;width:679px;overflow:auto;margin-left:9px;padding:1px;word-break:break-all;white-space:normal;">
		<div class="bar">
			<div class="tools" style="padding:3px;margin:0px;font-weight:bold;">
				Sh代码&nbsp;&nbsp;<a title="收藏这段代码" style="color:#108AC6;text-decoration:underline;"><img class="star" src="http://leitelyaya.iteye.com/images/icon_star.png" alt="收藏代码" /></a>
			</div>
		</div>
		<ol start="1" class="dp-default" style="font-size:1em;line-height:1.4em;margin:0px 0px 1px;padding:2px 0px;border:1px solid #D1D7DC;list-style-position:initial;list-style-image:initial;color:#2B91AF;">
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">$&nbsp;rpm&nbsp;-q&nbsp;bind&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">bind-<span class="number" style="color:#C00000;">9.7</span>.<span class="number" style="color:#C00000;">1</span>-<span class="number" style="color:#C00000;">2</span>.P2.fc13.i686&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">$&nbsp;rpm&nbsp;-q&nbsp;bind-chroot&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">bind-chroot-<span class="number" style="color:#C00000;">9.7</span>.<span class="number" style="color:#C00000;">1</span>-<span class="number" style="color:#C00000;">2</span>.P2.fc13.i686&nbsp;&nbsp;</span>
			</li>
		</ol>
	</div>
<br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">熟悉默认配置</span><strong style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">/etc/named.conf</strong><span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">：&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
	<div class="dp-highlighter" id="" style="font-family:Monaco, &quot;background-color:#FFFFFF;width:679px;overflow:auto;margin-left:9px;padding:1px;word-break:break-all;white-space:normal;">
		<div class="bar">
			<div class="tools" style="padding:3px;margin:0px;font-weight:bold;">
				Conf代码&nbsp;&nbsp;<a title="收藏这段代码" style="color:#108AC6;text-decoration:underline;"><img class="star" src="http://leitelyaya.iteye.com/images/icon_star.png" alt="收藏代码" /></a>
			</div>
		</div>
		<ol start="1" class="dp-default" style="font-size:1em;line-height:1.4em;margin:0px 0px 1px;padding:2px 0px;border:1px solid #D1D7DC;list-style-position:initial;list-style-image:initial;color:#2B91AF;">
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">//&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">//&nbsp;named.conf&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">//&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">//&nbsp;Provided&nbsp;by&nbsp;Red&nbsp;Hat&nbsp;bind&nbsp;package&nbsp;to&nbsp;configure&nbsp;the&nbsp;ISC&nbsp;BIND&nbsp;named(<span class="number" style="color:#C00000;">8</span>)&nbsp;DNS&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">//&nbsp;server&nbsp;as&nbsp;a&nbsp;caching&nbsp;only&nbsp;nameserver&nbsp;(as&nbsp;a&nbsp;localhost&nbsp;DNS&nbsp;resolver&nbsp;only).&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">//&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">//&nbsp;See&nbsp;/usr/share/doc/bind*/sample/&nbsp;for&nbsp;example&nbsp;named&nbsp;configuration&nbsp;files.&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">//&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">options&nbsp;{&nbsp;&nbsp;//&nbsp;定义全局变量&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;listen-on&nbsp;port&nbsp;<span class="number" style="color:#C00000;">53</span>&nbsp;{&nbsp;<span class="number" style="color:#C00000;">127.0</span>.<span class="number" style="color:#C00000;">0.1</span>;&nbsp;};&nbsp;//&nbsp;ipv4&nbsp;监听端口&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;listen-on-v6&nbsp;port&nbsp;<span class="number" style="color:#C00000;">53</span>&nbsp;{&nbsp;::<span class="number" style="color:#C00000;">1</span>;&nbsp;};&nbsp;&nbsp;&nbsp;&nbsp;//&nbsp;ipv6&nbsp;监听端口&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;directory&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="string" style="color:blue;">"/var/named"</span>;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;//&nbsp;制定装载zone区域文件的目录&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dump-file&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="string" style="color:blue;">"/var/named/data/cache_dump.db"</span>;&nbsp;&nbsp;&nbsp;&nbsp;//&nbsp;cache&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;statistics-file&nbsp;<span class="string" style="color:blue;">"/var/named/data/named_stats.txt"</span>;&nbsp;&nbsp;//&nbsp;statistics&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;memstatistics-file&nbsp;<span class="string" style="color:blue;">"/var/named/data/named_mem_stats.txt"</span>;&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;allow-query&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{&nbsp;localhost;&nbsp;};&nbsp;&nbsp;&nbsp;//&nbsp;允许访问列表&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;recursion&nbsp;yes;&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dnssec-enable&nbsp;yes;&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dnssec-validation&nbsp;yes;&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;dnssec-lookaside&nbsp;auto;&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;/*&nbsp;Path&nbsp;to&nbsp;ISC&nbsp;DLV&nbsp;key&nbsp;*/&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;bindkeys-file&nbsp;<span class="string" style="color:blue;">"/etc/named.iscdlv.key"</span>;&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">};&nbsp;//&nbsp;<span class="string" style="color:blue;">"}"</span>后也得分号结束&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">logging&nbsp;{&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;channel&nbsp;default_debug&nbsp;{&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;file&nbsp;<span class="string" style="color:blue;">"data/named.run"</span>;&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;severity&nbsp;dynamic;&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;};&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">};&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">zone&nbsp;<span class="string" style="color:blue;">"."</span>&nbsp;IN&nbsp;{&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;//&nbsp;<span class="string" style="color:blue;">"."</span>代表根区域&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;type&nbsp;hint;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;//&nbsp;根区域的类型就为hint&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;file&nbsp;<span class="string" style="color:blue;">"named.ca"</span>;&nbsp;//&nbsp;指定zone文件，默认已经生成&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">};&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">include&nbsp;<span class="string" style="color:blue;">"/etc/named.rfc1912.zones"</span>;&nbsp;&nbsp;</span>
			</li>
		</ol>
	</div>
<br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">注意，在最后一行还include一个conf文件，将本地地址都进行了映射。&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">我们需要修改option的内容，并且添加新的zone：&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
	<div class="dp-highlighter" id="" style="font-family:Monaco, &quot;background-color:#FFFFFF;width:679px;overflow:auto;margin-left:9px;padding:1px;word-break:break-all;white-space:normal;">
		<div class="bar">
			<div class="tools" style="padding:3px;margin:0px;font-weight:bold;">
				Zone代码&nbsp;&nbsp;<a title="收藏这段代码" style="color:#108AC6;text-decoration:underline;"><img class="star" src="http://leitelyaya.iteye.com/images/icon_star.png" alt="收藏代码" /></a>
			</div>
		</div>
		<ol start="1" class="dp-default" style="font-size:1em;line-height:1.4em;margin:0px 0px 1px;padding:2px 0px;border:1px solid #D1D7DC;list-style-position:initial;list-style-image:initial;color:#2B91AF;">
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">option&nbsp;{&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;listen-on&nbsp;port&nbsp;<span class="number" style="color:#C00000;">53</span>&nbsp;{&nbsp;&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="number" style="color:#C00000;">127.0</span>.<span class="number" style="color:#C00000;">0.1</span>;&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="number" style="color:#C00000;">192.168</span>.<span class="number" style="color:#C00000;">60.14</span>;&nbsp;//&nbsp;为局域网其它机器提供Named服务，必须监听向本机IP发出的请求&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;};&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;forwarders&nbsp;{&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;//&nbsp;添加forwarders，指向其它DNS服务器&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="number" style="color:#C00000;">202.106</span>.<span class="number" style="color:#C00000;">196.115</span>;&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;};&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;allow-query{&nbsp;any;&nbsp;};&nbsp;&nbsp;//&nbsp;开放访问权限&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">};&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">zone&nbsp;<span class="string" style="color:blue;">"groupon.cn"</span>&nbsp;IN&nbsp;{&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;//&nbsp;解析groupon.cn&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;type&nbsp;master;&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;file&nbsp;<span class="string" style="color:blue;">"named.groupon.cn"</span>;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;//&nbsp;自定义的域名到IP的正向解析配置&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">};&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">zone&nbsp;<span class="string" style="color:blue;">"60.168.192.in-addr.arpa"</span>&nbsp;IN&nbsp;{&nbsp;&nbsp;//&nbsp;本地内网为<span class="number" style="color:#C00000;">192.168</span>.<span class="number" style="color:#C00000;">60</span>.x&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;type&nbsp;master;&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;file&nbsp;<span class="string" style="color:blue;">"named.192.168.60"</span>;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;//&nbsp;自定义的IP到域名的反向解析配置&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">};&nbsp;&nbsp;</span>
			</li>
		</ol>
	</div>
<br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">至此看来，named.conf的配置并不复杂，不过接下来的zone文件的配置就会改变你的看法。&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">熟悉默认配置</span><strong style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">/var/named/named.localhost</strong><span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
	<div class="dp-highlighter" id="" style="font-family:Monaco, &quot;background-color:#FFFFFF;width:679px;overflow:auto;margin-left:9px;padding:1px;word-break:break-all;white-space:normal;">
		<div class="bar">
			<div class="tools" style="padding:3px;margin:0px;font-weight:bold;">
				Zone代码&nbsp;&nbsp;<a title="收藏这段代码" style="color:#108AC6;text-decoration:underline;"><img class="star" src="http://leitelyaya.iteye.com/images/icon_star.png" alt="收藏代码" /></a>
			</div>
		</div>
		<ol start="1" class="dp-default" style="font-size:1em;line-height:1.4em;margin:0px 0px 1px;padding:2px 0px;border:1px solid #D1D7DC;list-style-position:initial;list-style-image:initial;color:#2B91AF;">
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">;&nbsp;注意，zone文件的注释是以分号<span class="string" style="color:blue;">";"</span>开始的。&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">$TTL&nbsp;1D&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;;&nbsp;生存期,&nbsp;默认单位为秒，另可设定为[W|D|H|M]&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">;&nbsp;[zone]&nbsp;IN&nbsp;SOA&nbsp;[主机名]&nbsp;[管理员email]&nbsp;([五组更新时间参数])&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">;&nbsp;@=&gt;zone&nbsp;IN&nbsp;SOA&nbsp;@=&gt;主机名&nbsp;rname.invalid.=&gt;email&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">;&nbsp;@代表根域&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">;&nbsp;rname.invalid.解析为rname@invalid，第一个<span class="string" style="color:blue;">"."</span>为<span class="string" style="color:blue;">"@"</span>的替代，尾部的<span class="string" style="color:blue;">"."</span>为根域，表明其为绝对URL。&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">@&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;IN&nbsp;SOA&nbsp;&nbsp;@&nbsp;rname.invalid.&nbsp;(&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="number" style="color:#C00000;">0</span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;;&nbsp;serial&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1D&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;;&nbsp;refresh&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1H&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;;&nbsp;retry&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1W&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;;&nbsp;expire&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3H&nbsp;)&nbsp;&nbsp;&nbsp;&nbsp;;&nbsp;minimum&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;NS&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;@&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;;&nbsp;直接输入域名，访问@&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;A&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="number" style="color:#C00000;">127.0</span>.<span class="number" style="color:#C00000;">0.1</span>&nbsp;&nbsp;;&nbsp;直接输入域名，解析到的IPV4的IP&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;AAAA&nbsp;&nbsp;&nbsp;&nbsp;::<span class="number" style="color:#C00000;">1</span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;;&nbsp;直接输入域名，解析到的IPV6的IP&nbsp;&nbsp;</span>
			</li>
		</ol>
	</div>
<br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">现在开始建立正向解析文件:&nbsp;</span><strong style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">/var/named/named.groupon.cn</strong><span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
	<div class="dp-highlighter" id="" style="font-family:Monaco, &quot;background-color:#FFFFFF;width:679px;overflow:auto;margin-left:9px;padding:1px;word-break:break-all;white-space:normal;">
		<div class="bar">
			<div class="tools" style="padding:3px;margin:0px;font-weight:bold;">
				Zone代码&nbsp;&nbsp;<a title="收藏这段代码" style="color:#108AC6;text-decoration:underline;"><img class="star" src="http://leitelyaya.iteye.com/images/icon_star.png" alt="收藏代码" /></a>
			</div>
		</div>
		<ol start="1" class="dp-default" style="font-size:1em;line-height:1.4em;margin:0px 0px 1px;padding:2px 0px;border:1px solid #D1D7DC;list-style-position:initial;list-style-image:initial;color:#2B91AF;">
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">$TTL&nbsp;1D&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">@&nbsp;IN&nbsp;SOA&nbsp;@&nbsp;root.groupon.cn.&nbsp;(&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="number" style="color:#C00000;">2010110901</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="number" style="color:#C00000;">28800</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="number" style="color:#C00000;">14400</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="number" style="color:#C00000;">3600000</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="number" style="color:#C00000;">86400</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;IN&nbsp;NS&nbsp;@&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;;&nbsp;直接输入域名，访问@&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;IN&nbsp;A&nbsp;<span class="number" style="color:#C00000;">221.123</span>.<span class="number" style="color:#C00000;">177.226</span>&nbsp;&nbsp;;&nbsp;直接输入域名(www)，解析到的外网IP&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">store&nbsp;&nbsp;&nbsp;IN&nbsp;A&nbsp;<span class="number" style="color:#C00000;">192.168</span>.<span class="number" style="color:#C00000;">60.42</span>&nbsp;&nbsp;&nbsp;&nbsp;;&nbsp;输入子域名，解析到的内网IP&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">img&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;IN&nbsp;A&nbsp;<span class="number" style="color:#C00000;">192.168</span>.<span class="number" style="color:#C00000;">60.43</span>&nbsp;&nbsp;</span>
			</li>
		</ol>
	</div>
<br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">建立反向解析文件:</span><strong style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">/var/named/named.192.168.60</strong><span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
	<div class="dp-highlighter" id="" style="font-family:Monaco, &quot;background-color:#FFFFFF;width:679px;overflow:auto;margin-left:9px;padding:1px;word-break:break-all;white-space:normal;">
		<div class="bar">
			<div class="tools" style="padding:3px;margin:0px;font-weight:bold;">
				Zone代码&nbsp;&nbsp;<a title="收藏这段代码" style="color:#108AC6;text-decoration:underline;"><img class="star" src="http://leitelyaya.iteye.com/images/icon_star.png" alt="收藏代码" /></a>
			</div>
		</div>
		<ol start="1" class="dp-default" style="font-size:1em;line-height:1.4em;margin:0px 0px 1px;padding:2px 0px;border:1px solid #D1D7DC;list-style-position:initial;list-style-image:initial;color:#2B91AF;">
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">$TTL&nbsp;1D&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">@&nbsp;IN&nbsp;SOA&nbsp;<span class="number" style="color:#C00000;">60.168</span>.<span class="number" style="color:#C00000;">192</span>.in-addr.arpa.&nbsp;root.groupon.cn.&nbsp;(&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="number" style="color:#C00000;">2010110901</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="number" style="color:#C00000;">28800</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="number" style="color:#C00000;">14400</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="number" style="color:#C00000;">3600000</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="number" style="color:#C00000;">86400</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">)&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">@&nbsp;IN&nbsp;NS&nbsp;www.groupon.cn.&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;"><span class="number" style="color:#C00000;">42</span>&nbsp;IN&nbsp;PTR&nbsp;store.groupon.cn.&nbsp;&nbsp;;&nbsp;<span class="number" style="color:#C00000;">192.168</span>.<span class="number" style="color:#C00000;">60.42</span>&nbsp;-&gt;&nbsp;store&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;"><span class="number" style="color:#C00000;">43</span>&nbsp;IN&nbsp;PTR&nbsp;img.groupon.cn.&nbsp;&nbsp;&nbsp;&nbsp;;&nbsp;<span class="number" style="color:#C00000;">192.168</span>.<span class="number" style="color:#C00000;">60.43</span>&nbsp;-&gt;&nbsp;img&nbsp;&nbsp;</span>
			</li>
		</ol>
	</div>
<br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">配置完毕，检查配置文件的正确性：&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
	<div class="dp-highlighter" id="" style="font-family:Monaco, &quot;background-color:#FFFFFF;width:679px;overflow:auto;margin-left:9px;padding:1px;word-break:break-all;white-space:normal;">
		<div class="bar">
			<div class="tools" style="padding:3px;margin:0px;font-weight:bold;">
				Sh代码&nbsp;&nbsp;<a title="收藏这段代码" style="color:#108AC6;text-decoration:underline;"><img class="star" src="http://leitelyaya.iteye.com/images/icon_star.png" alt="收藏代码" /></a>
			</div>
		</div>
		<ol start="1" class="dp-default" style="font-size:1em;line-height:1.4em;margin:0px 0px 1px;padding:2px 0px;border:1px solid #D1D7DC;list-style-position:initial;list-style-image:initial;color:#2B91AF;">
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">#&nbsp;/usr/sbin/named-checkconf&nbsp;-z&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">zone&nbsp;localhost/IN:&nbsp;loaded&nbsp;serial&nbsp;<span class="number" style="color:#C00000;">0</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">zone&nbsp;<span class="number" style="color:#C00000;">60.168</span>.<span class="number" style="color:#C00000;">192</span>.in-addr.arpa/IN:&nbsp;loaded&nbsp;serial&nbsp;<span class="number" style="color:#C00000;">2010110901</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">zone&nbsp;groupon.cn/IN:&nbsp;loaded&nbsp;serial&nbsp;<span class="number" style="color:#C00000;">2010110901</span>&nbsp;&nbsp;</span>
			</li>
		</ol>
	</div>
<br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">看来一切正常， 这时就可以启动named服务器了。&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
	<div class="dp-highlighter" id="" style="font-family:Monaco, &quot;background-color:#FFFFFF;width:679px;overflow:auto;margin-left:9px;padding:1px;word-break:break-all;white-space:normal;">
		<div class="bar">
			<div class="tools" style="padding:3px;margin:0px;font-weight:bold;">
				Sh代码&nbsp;&nbsp;<a title="收藏这段代码" style="color:#108AC6;text-decoration:underline;"><img class="star" src="http://leitelyaya.iteye.com/images/icon_star.png" alt="收藏代码" /></a>
			</div>
		</div>
		<ol start="1" class="dp-default" style="font-size:1em;line-height:1.4em;margin:0px 0px 1px;padding:2px 0px;border:1px solid #D1D7DC;list-style-position:initial;list-style-image:initial;color:#2B91AF;">
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">#&nbsp;/sbin/service&nbsp;named&nbsp;start&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">Starting&nbsp;named:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[&nbsp;&nbsp;OK&nbsp;&nbsp;]&nbsp;&nbsp;</span>
			</li>
		</ol>
	</div>
<br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">还要做的就是开通端口，并在客户端设定DNS地址为该服务器地址，强制刷新dns和测试：&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
	<div class="dp-highlighter" id="" style="font-family:Monaco, &quot;background-color:#FFFFFF;width:679px;overflow:auto;margin-left:9px;padding:1px;word-break:break-all;white-space:normal;">
		<div class="bar">
			<div class="tools" style="padding:3px;margin:0px;font-weight:bold;">
				Cmd代码&nbsp;&nbsp;<a title="收藏这段代码" style="color:#108AC6;text-decoration:underline;"><img class="star" src="http://leitelyaya.iteye.com/images/icon_star.png" alt="收藏代码" /></a>
			</div>
		</div>
		<ol start="1" class="dp-default" style="font-size:1em;line-height:1.4em;margin:0px 0px 1px;padding:2px 0px;border:1px solid #D1D7DC;list-style-position:initial;list-style-image:initial;color:#2B91AF;">
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&gt;&nbsp;ipconfig&nbsp;/flushdns&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">Windows&nbsp;IP&nbsp;Configuration&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">Successfully&nbsp;flushed&nbsp;the&nbsp;DNS&nbsp;Resolver&nbsp;Cache.&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&gt;&nbsp;nslookup&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">***&nbsp;Can't&nbsp;find&nbsp;server&nbsp;name&nbsp;for&nbsp;address&nbsp;<span class="number" style="color:#C00000;">192.168</span>.<span class="number" style="color:#C00000;">60.36</span>:&nbsp;Non-existent&nbsp;domain&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">***&nbsp;Default&nbsp;servers&nbsp;are&nbsp;not&nbsp;available&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">Default&nbsp;Server:&nbsp;&nbsp;UnKnown&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">Address:&nbsp;&nbsp;<span class="number" style="color:#C00000;">192.168</span>.<span class="number" style="color:#C00000;">60.36</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&gt;&nbsp;groupon.cn&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">Server:&nbsp;&nbsp;UnKnown&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">Address:&nbsp;&nbsp;<span class="number" style="color:#C00000;">192.168</span>.<span class="number" style="color:#C00000;">60.36</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">Name:&nbsp;&nbsp;&nbsp;&nbsp;groupon.cn&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">Address:&nbsp;&nbsp;<span class="number" style="color:#C00000;">221.123</span>.<span class="number" style="color:#C00000;">177.226</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&gt;&nbsp;store.groupon.cn&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">Server:&nbsp;&nbsp;UnKnown&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">Address:&nbsp;&nbsp;<span class="number" style="color:#C00000;">192.168</span>.<span class="number" style="color:#C00000;">60.36</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">Name:&nbsp;&nbsp;&nbsp;&nbsp;store.groupon.cn&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">Address:&nbsp;&nbsp;<span class="number" style="color:#C00000;">192.168</span>.<span class="number" style="color:#C00000;">60.42</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&gt;&nbsp;<span class="number" style="color:#C00000;">192.168</span>.<span class="number" style="color:#C00000;">60.42</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">Server:&nbsp;&nbsp;UnKnown&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">Address:&nbsp;&nbsp;<span class="number" style="color:#C00000;">192.168</span>.<span class="number" style="color:#C00000;">60.36</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">Name:&nbsp;&nbsp;&nbsp;&nbsp;store.groupon.cn&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">Address:&nbsp;&nbsp;<span class="number" style="color:#C00000;">192.168</span>.<span class="number" style="color:#C00000;">60.42</span>&nbsp;&nbsp;</span>
			</li>
		</ol>
	</div>
<br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">大功告成！&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">参考：&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">文件:</span><strong style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">/etc/named.rfc1912.zones</strong><span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
	<div class="dp-highlighter" id="" style="font-family:Monaco, &quot;background-color:#FFFFFF;width:679px;overflow:auto;margin-left:9px;padding:1px;word-break:break-all;white-space:normal;">
		<div class="bar">
			<div class="tools" style="padding:3px;margin:0px;font-weight:bold;">
				Conf代码&nbsp;&nbsp;<a title="收藏这段代码" style="color:#108AC6;text-decoration:underline;"><img class="star" src="http://leitelyaya.iteye.com/images/icon_star.png" alt="收藏代码" /></a>
			</div>
		</div>
		<ol start="1" class="dp-default" style="font-size:1em;line-height:1.4em;margin:0px 0px 1px;padding:2px 0px;border:1px solid #D1D7DC;list-style-position:initial;list-style-image:initial;color:#2B91AF;">
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">//&nbsp;named.rfc1912.zones:&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">//&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">//&nbsp;Provided&nbsp;by&nbsp;Red&nbsp;Hat&nbsp;caching-nameserver&nbsp;package&nbsp;&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">//&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">//&nbsp;ISC&nbsp;BIND&nbsp;named&nbsp;zone&nbsp;configuration&nbsp;for&nbsp;zones&nbsp;recommended&nbsp;by&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">//&nbsp;RFC&nbsp;<span class="number" style="color:#C00000;">1912</span>&nbsp;section&nbsp;<span class="number" style="color:#C00000;">4.1</span>&nbsp;:&nbsp;localhost&nbsp;TLDs&nbsp;and&nbsp;address&nbsp;zones&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">//&nbsp;and&nbsp;http://www.ietf.org/internet-drafts/draft-ietf-dnsop-default-local-zones-<span class="number" style="color:#C00000;">02</span>.txt&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">//&nbsp;(c)<span class="number" style="color:#C00000;">2007</span>&nbsp;R&nbsp;W&nbsp;Franks&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">//&nbsp;&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">//&nbsp;See&nbsp;/usr/share/doc/bind*/sample/&nbsp;for&nbsp;example&nbsp;named&nbsp;configuration&nbsp;files.&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">//&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">zone&nbsp;<span class="string" style="color:blue;">"localhost.localdomain"</span>&nbsp;IN&nbsp;{&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;type&nbsp;master;&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;file&nbsp;<span class="string" style="color:blue;">"named.localhost"</span>;&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;allow-update&nbsp;{&nbsp;none;&nbsp;};&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">};&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">zone&nbsp;<span class="string" style="color:blue;">"localhost"</span>&nbsp;IN&nbsp;{&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;type&nbsp;master;&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;file&nbsp;<span class="string" style="color:blue;">"named.localhost"</span>;&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;allow-update&nbsp;{&nbsp;none;&nbsp;};&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">};&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">zone&nbsp;<span class="string" style="color:blue;">"1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.ip6.arpa"</span>&nbsp;IN&nbsp;{&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;type&nbsp;master;&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;file&nbsp;<span class="string" style="color:blue;">"named.loopback"</span>;&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;allow-update&nbsp;{&nbsp;none;&nbsp;};&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">};&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">zone&nbsp;<span class="string" style="color:blue;">"1.0.0.127.in-addr.arpa"</span>&nbsp;IN&nbsp;{&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;type&nbsp;master;&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;file&nbsp;<span class="string" style="color:blue;">"named.loopback"</span>;&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;allow-update&nbsp;{&nbsp;none;&nbsp;};&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">};&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">zone&nbsp;<span class="string" style="color:blue;">"0.in-addr.arpa"</span>&nbsp;IN&nbsp;{&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;type&nbsp;master;&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;file&nbsp;<span class="string" style="color:blue;">"named.empty"</span>;&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;allow-update&nbsp;{&nbsp;none;&nbsp;};&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">};&nbsp;&nbsp;</span>
			</li>
		</ol>
	</div>
<br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">文件:</span><strong style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">/var/named/named.loopback</strong><span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
	<div class="dp-highlighter" id="" style="font-family:Monaco, &quot;background-color:#FFFFFF;width:679px;overflow:auto;margin-left:9px;padding:1px;word-break:break-all;white-space:normal;">
		<div class="bar">
			<div class="tools" style="padding:3px;margin:0px;font-weight:bold;">
				Zone代码&nbsp;&nbsp;<a title="收藏这段代码" style="color:#108AC6;text-decoration:underline;"><img class="star" src="http://leitelyaya.iteye.com/images/icon_star.png" alt="收藏代码" /></a>
			</div>
		</div>
		<ol start="1" class="dp-default" style="font-size:1em;line-height:1.4em;margin:0px 0px 1px;padding:2px 0px;border:1px solid #D1D7DC;list-style-position:initial;list-style-image:initial;color:#2B91AF;">
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">$TTL&nbsp;1D&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">@&nbsp;&nbsp;&nbsp;IN&nbsp;SOA&nbsp;&nbsp;@&nbsp;rname.invalid.&nbsp;(&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="number" style="color:#C00000;">0</span>&nbsp;&nbsp;&nbsp;;&nbsp;serial&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1D&nbsp;&nbsp;;&nbsp;refresh&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1H&nbsp;&nbsp;;&nbsp;retry&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1W&nbsp;&nbsp;;&nbsp;expire&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3H&nbsp;)&nbsp;&nbsp;&nbsp;&nbsp;;&nbsp;minimum&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;NS&nbsp;&nbsp;@&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;A&nbsp;&nbsp;&nbsp;<span class="number" style="color:#C00000;">127.0</span>.<span class="number" style="color:#C00000;">0.1</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;AAAA&nbsp;&nbsp;&nbsp;&nbsp;::<span class="number" style="color:#C00000;">1</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;PTR&nbsp;localhost.&nbsp;&nbsp;</span>
			</li>
		</ol>
	</div>
<br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">文件:</span><strong style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">/var/named/named.empty</strong><span style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">&nbsp;</span><br style="font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
	<div class="dp-highlighter" id="" style="font-family:Monaco, &quot;background-color:#FFFFFF;width:679px;overflow:auto;margin-left:9px;padding:1px;word-break:break-all;white-space:normal;">
		<div class="bar">
			<div class="tools" style="padding:3px;margin:0px;font-weight:bold;">
				Zone代码&nbsp;&nbsp;<a title="收藏这段代码" style="color:#108AC6;text-decoration:underline;"><img class="star" src="http://leitelyaya.iteye.com/images/icon_star.png" alt="收藏代码" /></a>
			</div>
		</div>
		<ol start="1" class="dp-default" style="font-size:1em;line-height:1.4em;margin:0px 0px 1px;padding:2px 0px;border:1px solid #D1D7DC;list-style-position:initial;list-style-image:initial;color:#2B91AF;">
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">$TTL&nbsp;3H&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">@&nbsp;&nbsp;&nbsp;IN&nbsp;SOA&nbsp;&nbsp;@&nbsp;rname.invalid.&nbsp;(&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="number" style="color:#C00000;">0</span>&nbsp;&nbsp;&nbsp;;&nbsp;serial&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1D&nbsp;&nbsp;;&nbsp;refresh&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1H&nbsp;&nbsp;;&nbsp;retry&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1W&nbsp;&nbsp;;&nbsp;expire&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3H&nbsp;)&nbsp;&nbsp;&nbsp;&nbsp;;&nbsp;minimum&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;NS&nbsp;&nbsp;@&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;A&nbsp;&nbsp;&nbsp;<span class="number" style="color:#C00000;">127.0</span>.<span class="number" style="color:#C00000;">0.1</span>&nbsp;&nbsp;</span>
			</li>
			<li style="font-size:1em;margin:0px 0px 0px 38px;padding:0px 0px 0px 10px;border-left:1px solid #D1D7DC;background-color:#FAFAFA;line-height:18px;">
				<span style="color:black;">&nbsp;&nbsp;&nbsp;&nbsp;AAAA&nbsp;&nbsp;&nbsp;&nbsp;::<span class="number" style="color:#C00000;">1</span>&nbsp;&nbsp;</span>
			</li>
		</ol>
	</div>
</p>