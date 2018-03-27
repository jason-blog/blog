<p>
	1. linux curl抓取网页：
</p>
<p>
	<br />
</p>
<p>
	抓取百度：
</p>
<p>
	curl http://www.baidu.com
</p>
<p>
	<br />
</p>
<p>
	如发现乱码，可以使用iconv转码：
</p>
<p>
	curl http://iframe.ip138.com/ic.asp|iconv -fgb2312
</p>
<p>
	iconv的用法请参阅：在Linux/Unix系统下用iconv命令处理文本文件中文乱码问题
</p>
<p>
	<br />
</p>
<p>
	2. Linux curl使用代理：
</p>
<p>
	<br />
</p>
<p>
	linux curl使用http代理抓取页面：
</p>
<p>
	curl -x 111.95.243.36:80 http://iframe.ip138.com/ic.asp|iconv -fgb2312
</p>
<p>
	curl -x 111.95.243.36:80 -U aiezu:password http://www.baidu.com
</p>
<p>
	<br />
</p>
<p>
	使用socks代理抓取页面：
</p>
<p>
	curl --socks4 202.113.65.229:443 http://iframe.ip138.com/ic.asp|iconv -fgb2312
</p>
<p>
	curl --socks5 202.113.65.229:443 http://iframe.ip138.com/ic.asp|iconv -fgb2312
</p>
<p>
	<br />
</p>
<p>
	代理服务器地址可以从爬虫代理上获取。
</p>
<p>
	<br />
</p>
<p>
	3. linux curl处理cookies
</p>
<p>
	<br />
</p>
<p>
	接收cookies:
</p>
<p>
	curl -c /tmp/cookies http://www.baidu.com #cookies保存到/tmp/cookies文件
</p>
<p>
	<br />
</p>
<p>
	发送cookies:
</p>
<p>
	curl -b "key1=val1;key2=val2;" http://www.baidu.com #发送cookies文本
</p>
<p>
	curl -b /tmp/cookies http://www.baidu.com #从文件中读取cookies
</p>
<p>
	<br />
</p>
<p>
	4. linux curl发送数据：
</p>
<p>
	<br />
</p>
<p>
	linux curl get方式提交数据：
</p>
<p>
	curl -G -d "name=value&amp;name2=value2" http://www.baidu.com
</p>
<p>
	<br />
</p>
<p>
	linux curl post方式提交数据：
</p>
<p>
	curl -d "name=value&amp;name2=value2" http://www.baidu.com #post数据
</p>
<p>
	curl -d a=b&amp;c=d&amp;txt@/tmp/txt http://www.baidu.com #post文件
</p>
<p>
	<br />
</p>
<p>
	以表单的方式上传文件：
</p>
<p>
	curl -F file=@/tmp/me.txt http://www.aiezu.com
</p>
<p>
	<br />
</p>
<p>
	相当于设置form表单的method="POST"和enctype='multipart/form-data'两个属性。
</p>
<p>
	<br />
</p>
<p>
	5. linux curl http header处理：
</p>
<p>
	<br />
</p>
<p>
	设置http请求头信息：
</p>
<p>
	curl -A "Mozilla/5.0 Firefox/21.0" http://www.baidu.com #设置http请求头User-Agent
</p>
<p>
	curl -e "http://pachong.org/" http://www.baidu.com #设置http请求头Referer
</p>
<p>
	curl -H "Connection:keep-alive \n User-Agent: Mozilla/5.0" http://www.aiezu.com
</p>
<p>
	<br />
</p>
<p>
	设置http响应头处理：
</p>
<p>
	curl -I http://www.aiezu.com #仅仅返回header
</p>
<p>
	curl -D /tmp/header http://www.aiezu.com #将http header保存到/tmp/header文件
</p>
<p>
	<br />
</p>
<p>
	6. linux curl认证：
</p>
<p>
	<br />
</p>
<p>
	curl -u aiezu:password http://www.aiezu.com #用户名密码认证
</p>
<p>
	curl -E mycert.pem https://www.baidu.com #采用证书认证
</p>
<p>
	<br />
</p>
<p>
	7. 其他：
</p>
<p>
	<br />
</p>
<p>
	curl -# http://www.baidu.com #以“#”号输出进度条
</p>
<p>
	curl -o /tmp/aiezu http://www.baidu.com #保存http响应到/tmp/aiezu
</p>
<p>
	<br />
</p>
<p>
	8. 经验
</p>
<p>
	linux 使用curl小经验教训：
</p>
<p>
	http请求地址的url要使用""括起来。当有存在多个参数使用&amp;连接时可能会出错。
</p>