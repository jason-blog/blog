<table width="100%" style="padding:0px;margin:0px;color:#333333;font-family:Verdana, Arial, Tahoma;font-size:14px;background-color:#FFFFFF;">
	<tbody style="padding:0px;margin:0px;">
		<tr style="padding:0px;margin:0px;">
			<td style="padding:0px;margin:0px;">
				<div id="contentMidPicAD" style="padding:0px;margin:0px;float:right;clear:both;top:0px;vertical-align:top;">
				</div>
				<p style="padding:0px;margin-top:10px;margin-bottom:10px;clear:both;line-height:24px;color:#000000;font-family:Arial, 宋体;font-size:14px;">
					<span style="font-family:'sans serif, tahoma, verdana, helvetica';"><span style="font-size:12px;white-space:nowrap;">原文 ：http://linux.it.net.cn/e/server/nginx/2015/0208/12996.html</span></span>
				</p>
				<p style="padding:0px;margin-top:10px;margin-bottom:10px;clear:both;line-height:24px;color:#000000;font-family:Arial, 宋体;font-size:14px;">
					<span style="font-family:'sans serif, tahoma, verdana, helvetica';"><span style="font-size:12px;white-space:nowrap;">在nginx中限制客户端访问频次与访问次数，需要用到二个模块NginxHttpLimitConnModule与NginxHttpLimitReqModule。</span></span>
				</p>
				<p style="padding:0px;margin-top:10px;margin-bottom:10px;clear:both;line-height:24px;color:#000000;font-family:Arial, 宋体;font-size:14px;">
					<span style="font-family:'sans serif, tahoma, verdana, helvetica';"><span style="font-size:12px;white-space:nowrap;">nginx的两个模块：<br style="padding:0px;margin:0px;" />
NginxHttpLimitConnModule，可以根据设定的条件来限定客户端（单一ip）的并发访问，但是并不是所有的访问都会被计数，只有那些正在被处理的的请求（这些请求的头信息已<br style="padding:0px;margin:0px;" />
被完全读入），所在的访问才会被计数。</span></span>
				</p>
				<p style="padding:0px;margin-top:10px;margin-bottom:10px;clear:both;line-height:24px;color:#000000;font-family:Arial, 宋体;font-size:14px;">
					<span style="font-family:'sans serif, tahoma, verdana, helvetica';"><span style="font-size:12px;white-space:nowrap;">NginxHttpLimitReqModule，可以根据设定的条件来限定客户端（单一ip）的访问频率。</span></span>
				</p>
				<p style="padding:0px;margin-top:10px;margin-bottom:10px;clear:both;line-height:24px;color:#000000;font-family:Arial, 宋体;font-size:14px;">
					<span style="font-family:'sans serif, tahoma, verdana, helvetica';"><span style="font-size:12px;white-space:nowrap;">下面重点介绍下这两个模块的用法。</span></span>
				</p>
				<p style="padding:0px;margin-top:10px;margin-bottom:10px;clear:both;line-height:24px;color:#000000;font-family:Arial, 宋体;font-size:14px;">
					<span style="font-family:'sans serif, tahoma, verdana, helvetica';"><span style="font-size:12px;white-space:nowrap;">1.NginxHttpLimitConnModule<br style="padding:0px;margin:0px;" />
&nbsp;&nbsp;<span style="padding:0px;margin:0px;">IT网，http://www.it.net.cn</span></span></span>
				</p>
				<div class="codetext" style="padding:5px;margin:0px;width:620px;font-size:14px;line-height:22px;border-width:1px 1px 1px 2px;border-style:solid;border-color:#C9D6F1 #C9D6F1 #C9D6F1 #C7C7EB;background-color:#F3F5FC;color:#000000;font-family:Arial, 宋体;">
					<span style="font-family:'sans serif, tahoma, verdana, helvetica';"><span style="font-size:12px;white-space:nowrap;">http{<br style="padding:0px;margin:0px;" />
limit_conn_zone $binary_remote_addr&nbsp; zone=one:10m;<br style="padding:0px;margin:0px;" />
server {<br style="padding:0px;margin:0px;" />
limit_conn test 1;<br style="padding:0px;margin:0px;" />
location =/1.html{<br style="padding:0px;margin:0px;" />
root html;<br style="padding:0px;margin:0px;" />
}<br style="padding:0px;margin:0px;" />
}<br style="padding:0px;margin:0px;" />
}</span></span>
				</div>
				<p style="padding:0px;margin-top:10px;margin-bottom:10px;clear:both;line-height:24px;color:#000000;font-family:Arial, 宋体;font-size:14px;">
					<span style="font-family:'sans serif, tahoma, verdana, helvetica';"><span style="font-size:12px;white-space:nowrap;">1）limit_conn_zone $binary_remote_addr&nbsp; zone=one:10m;<br style="padding:0px;margin:0px;" />
第一个参数$binary_remote_addr ：表示以客户端ip作为键值来进行限制</span></span>
				</p>
<span style="color:#000000;"><span style="white-space:nowrap;"><br style="padding:0px;margin:0px;" />
第二个参数zone=one:10m：表示生成一个大小为10M，名字为one的存储区域，用来存储访问次数</span></span>
				<p style="padding:0px;margin-top:10px;margin-bottom:10px;clear:both;line-height:24px;color:#000000;font-family:Arial, 宋体;font-size:14px;">
					<span style="font-family:'sans serif, tahoma, verdana, helvetica';"><span style="font-size:12px;white-space:nowrap;">2）limit_conn test 1;<br style="padding:0px;margin:0px;" />
表示在test存储区内，限制客户端ip只能访问一次，若超过访问限制，则返回503错误。</span></span>
				</p>
				<p style="padding:0px;margin-top:10px;margin-bottom:10px;clear:both;line-height:24px;color:#000000;font-family:Arial, 宋体;font-size:14px;">
					<span style="font-family:'sans serif, tahoma, verdana, helvetica';"><span style="font-size:12px;white-space:nowrap;">用ab进行测试<br style="padding:0px;margin:0px;" />
&nbsp;ab -c 2 -n 10 http://www.test.cn/1.html<br style="padding:0px;margin:0px;" />
我们每次发起2个请求，一共有10次请求<br style="padding:0px;margin:0px;" />
&nbsp;&nbsp;<span style="padding:0px;margin:0px;">Linux学习，http:// linux.it.net.cn</span></span></span>
				</p>
				<div class="codetext" style="padding:5px;margin:0px;width:620px;font-size:14px;line-height:22px;border-width:1px 1px 1px 2px;border-style:solid;border-color:#C9D6F1 #C9D6F1 #C9D6F1 #C7C7EB;background-color:#F3F5FC;color:#000000;font-family:Arial, 宋体;">
					<span style="font-family:'sans serif, tahoma, verdana, helvetica';"><span style="font-size:12px;white-space:nowrap;">[root@usvr-124 logs]# vim access.log<br style="padding:0px;margin:0px;" />
&nbsp; 1 27/Nov/2014:11:25:30 +0800 - - 192.168.3.124:80 GET /1.html - - 192.168.3.126 HTTP/1.0 [ApacheBench/2.3] [-] - www.test.cn 200 0 0 235 90 0"-"<br style="padding:0px;margin:0px;" />
&nbsp; 2 27/Nov/2014:11:25:30 +0800 - - 192.168.3.124:80 GET /1.html - - 192.168.3.126 HTTP/1.0 [ApacheBench/2.3] [-] - www.test.cn 503 0 0 371 90 0"-"<br style="padding:0px;margin:0px;" />
&nbsp; 3 27/Nov/2014:11:25:30 +0800 - - 192.168.3.124:80 GET /1.html - - 192.168.3.126 HTTP/1.0 [ApacheBench/2.3] [-] - www.test.cn 200 0 0 235 90 0"-"<br style="padding:0px;margin:0px;" />
&nbsp; 4 27/Nov/2014:11:25:30 +0800 - - 192.168.3.124:80 GET /1.html - - 192.168.3.126 HTTP/1.0 [ApacheBench/2.3] [-] - www.test.cn 503 0 0 371 90 0"-"&nbsp;<span style="padding:0px;margin:0px;">IT网，http://www.it.net.cn</span>&nbsp;<br style="padding:0px;margin:0px;" />
&nbsp; 5 27/Nov/2014:11:25:30 +0800 - - 192.168.3.124:80 GET /1.html - - 192.168.3.126 HTTP/1.0 [ApacheBench/2.3] [-] - www.test.cn 200 0 0 235 90 0"-"<br style="padding:0px;margin:0px;" />
&nbsp; 6 27/Nov/2014:11:25:30 +0800 - - 192.168.3.124:80 GET /1.html - - 192.168.3.126 HTTP/1.0 [ApacheBench/2.3] [-] - www.test.cn 503 0 0 371 90 0"-"<br style="padding:0px;margin:0px;" />
&nbsp; 7 27/Nov/2014:11:25:30 +0800 - - 192.168.3.124:80 GET /1.html - - 192.168.3.126 HTTP/1.0 [ApacheBench/2.3] [-] - www.test.cn 503 0 0 371 90 0"-"<br style="padding:0px;margin:0px;" />
&nbsp; 8 27/Nov/2014:11:25:30 +0800 - - 192.168.3.124:80 GET /1.html - - 192.168.3.126 HTTP/1.0 [ApacheBench/2.3] [-] - www.test.cn 200 0 0 235 90 0"-"<br style="padding:0px;margin:0px;" />
&nbsp; 9 27/Nov/2014:11:25:30 +0800 - - 192.168.3.124:80 GET /1.html - - 192.168.3.126 HTTP/1.0 [ApacheBench/2.3] [-] - www.test.cn 503 0 0 371 90 0"-"&nbsp;<span style="padding:0px;margin:0px;">Linux学习，http:// linux.it.net.cn</span>&nbsp;<br style="padding:0px;margin:0px;" />
&nbsp;10 27/Nov/2014:11:25:30 +0800 - - 192.168.3.124:80 GET /1.html - - 192.168.3.126 HTTP/1.0 [ApacheBench/2.3] [-] - www.test.cn 200 0 0 235 90 0"-"</span></span>
				</div>
				<p style="padding:0px;margin-top:10px;margin-bottom:10px;clear:both;line-height:24px;color:#000000;font-family:Arial, 宋体;font-size:14px;">
					<span style="font-family:'sans serif, tahoma, verdana, helvetica';"><span style="font-size:12px;white-space:nowrap;">每次访问是两个并发，每两个并发请求中有一个是被拒绝的，返回的是503错误。</span></span>
				</p>
				<p style="padding:0px;margin-top:10px;margin-bottom:10px;clear:both;line-height:24px;color:#000000;font-family:Arial, 宋体;font-size:14px;">
					<span style="font-family:'sans serif, tahoma, verdana, helvetica';"><span style="font-size:12px;white-space:nowrap;">看下错误日志：<br style="padding:0px;margin:0px;" />
&nbsp;</span></span>
				</p>
				<div class="codetext" style="padding:5px;margin:0px;width:620px;font-size:14px;line-height:22px;border-width:1px 1px 1px 2px;border-style:solid;border-color:#C9D6F1 #C9D6F1 #C9D6F1 #C7C7EB;background-color:#F3F5FC;color:#000000;font-family:Arial, 宋体;">
					<span style="font-family:'sans serif, tahoma, verdana, helvetica';"><span style="font-size:12px;white-space:nowrap;">[root@usvr-124 logs]# cat error/error.log&nbsp;<br style="padding:0px;margin:0px;" />
2014/11/27 11:29:50 [error] 8445#0: *22317249 limiting connections by zone "one", client: 192.168.3.126, server: www.test.cn, request: "GET /1.html HTTP/1.0", host: "www.test.cn"<br style="padding:0px;margin:0px;" />
2014/11/27 11:29:50 [error] 8445#0: *22317251 limiting connections by zone "one", client: 192.168.3.126, server: www.test.cn, request: "GET /1.html HTTP/1.0", host: "www.test.cn"<br style="padding:0px;margin:0px;" />
2014/11/27 11:29:50 [error] 8445#0: *22317255 limiting connections by zone "one", client: 192.168.3.126, server: www.test.cn, request: "GET /1.html HTTP/1.0", host: "www.test.cn"&nbsp;<br style="padding:0px;margin:0px;" />
2014/11/27 11:29:50 [error] 8445#0: *22317257 limiting connections by zone "one", client: 192.168.3.126, server: www.test.cn, request: "GET /1.html HTTP/1.0", host: "www.test.cn"<br style="padding:0px;margin:0px;" />
&nbsp;</span></span>
				</div>
				<p style="padding:0px;margin-top:10px;margin-bottom:10px;clear:both;line-height:24px;color:#000000;font-family:Arial, 宋体;font-size:14px;">
					<span style="font-family:'sans serif, tahoma, verdana, helvetica';"><span style="font-size:12px;white-space:nowrap;">从上面看出返回503错误的由于被设定的存储区域one所限制，设定的规则生效了。</span></span>
				</p>
				<p style="padding:0px;margin-top:10px;margin-bottom:10px;clear:both;line-height:24px;color:#000000;font-family:Arial, 宋体;font-size:14px;">
					<span style="font-family:'sans serif, tahoma, verdana, helvetica';"><span style="font-size:12px;white-space:nowrap;">2.NginxHttpLimitReqModule<br style="padding:0px;margin:0px;" />
&nbsp;</span></span>
				</p>
				<div class="codetext" style="padding:5px;margin:0px;width:620px;font-size:14px;line-height:22px;border-width:1px 1px 1px 2px;border-style:solid;border-color:#C9D6F1 #C9D6F1 #C9D6F1 #C7C7EB;background-color:#F3F5FC;color:#000000;font-family:Arial, 宋体;">
					<span style="font-family:'sans serif, tahoma, verdana, helvetica';"><span style="font-size:12px;white-space:nowrap;">http{<br style="padding:0px;margin:0px;" />
limit_req_zone&nbsp; $binary_remote_addr&nbsp; zone=two:10m&nbsp;&nbsp; rate=5r/s;<br style="padding:0px;margin:0px;" />
server {<br style="padding:0px;margin:0px;" />
limit_req zone=two burst=5 nodelay;<br style="padding:0px;margin:0px;" />
location =/1.html{<br style="padding:0px;margin:0px;" />
root html;<br style="padding:0px;margin:0px;" />
}<br style="padding:0px;margin:0px;" />
}<br style="padding:0px;margin:0px;" />
}</span></span>
				</div>
				<p style="padding:0px;margin-top:10px;margin-bottom:10px;clear:both;line-height:24px;color:#000000;font-family:Arial, 宋体;font-size:14px;">
					<span style="font-family:'sans serif, tahoma, verdana, helvetica';"><span style="font-size:12px;white-space:nowrap;">1）limit_req_zone&nbsp; $binary_remote_addr&nbsp; zone=two:10m&nbsp;&nbsp; rate=5r/s;</span></span>
				</p>
<span style="color:#000000;"><span style="white-space:nowrap;"><br style="padding:0px;margin:0px;" />
第一个参数$binary_remote_addr：表示以客户端ip作为键值来进行限制<br style="padding:0px;margin:0px;" />
第二个参数zone=two:10m ：表示生成一个大小为10M，名字为two的存储区域，用来存储访问频率<br style="padding:0px;margin:0px;" />
第三个参数 rate=5r/s：表示限定客户端的访问频率为每秒10次</span></span>
				<p style="padding:0px;margin-top:10px;margin-bottom:10px;clear:both;line-height:24px;color:#000000;font-family:Arial, 宋体;font-size:14px;">
					<span style="font-family:'sans serif, tahoma, verdana, helvetica';"><span style="font-size:12px;white-space:nowrap;">2）limit_req zone=two burst=5 nodelay;<br style="padding:0px;margin:0px;" />
第一个参数zone=two：表示使用存储区域two来限制<br style="padding:0px;margin:0px;" />
第二个参数burst=5：表示设定一个缓存区域，当有大量请求时，超过了访问频次限制的请求会放在这个缓冲区域内<br style="padding:0px;margin:0px;" />
第三个参数nodelay：表示当超过访问次数并缓冲也满的情况下，直接放回503错误，若不设置，这些多余的请求会延迟处理</span></span>
				</p>
				<p style="padding:0px;margin-top:10px;margin-bottom:10px;clear:both;line-height:24px;color:#000000;font-family:Arial, 宋体;font-size:14px;">
					<span style="font-family:'sans serif, tahoma, verdana, helvetica';"><span style="font-size:12px;white-space:nowrap;">用ab进行测试 ab -c 1 -n 5 -t 2 http://www.leduz.com/1.html，由于在2秒内会请求上前次，因此在这就不把访问日志和错误日志贴出来了，大体描述下：<br style="padding:0px;margin:0px;" />
在第一秒内成功访问，也就是返回200的有6条记录<br style="padding:0px;margin:0px;" />
在第二秒内成功访问，也就是返回200的有5条记录<br style="padding:0px;margin:0px;" />
在第三秒内成功访问，也就是返回200的有4条记录<br style="padding:0px;margin:0px;" />
从上面看出，访问频次平均现在在5条左右，其实也没有精确的达到我们设置的限制，但是对外来说，这种效果还是起到作用了。</span></span>
				</p>
				<p style="padding:0px;margin-top:10px;margin-bottom:10px;clear:both;line-height:24px;color:#000000;font-family:Arial, 宋体;font-size:14px;">
					<span style="font-family:'sans serif, tahoma, verdana, helvetica';"><span style="font-size:12px;white-space:nowrap;">说明：<br style="padding:0px;margin:0px;" />
1，虽然在看访问日志是限制没有精确达到要求的次数，但是不可否定的是这可以帮助nginx节省部分流量，提高了可用的并发。<br style="padding:0px;margin:0px;" />
2，经过多次实验，limit_conn和limit_req都不是每次很准，有时差距和实际参数很大。</span></span>
				</p>
			</td>
		</tr>
	</tbody>
</table>