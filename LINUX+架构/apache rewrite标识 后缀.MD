R[=code](force redirect) 强制外部重定向<br />
G(force URL to be gone) 强制URL为GONE，返回410HTTP状态码。<br />
P(force proxy) 强制使用代理转发。<br />
L(last rule) 表明当前规则是最后一条规则，停止分析以后规则的重写。<br />
N(next round) 重新从第一条规则开始运行重写过程。<br />
C(chained with next rule) 与下一条规则关联<br />
如果规则匹配则正常处理，该标志无效，如果不匹配，那么下面所有关联的规则都跳过<br />
T=MIME-type(force MIME type) 强制MIME类型<br />
NS (used only if no internal sub-request) 只用于不是内部子请求<br />
NC(no case) 不区分大小写<br />
QSA(query string append) 追加请求字符串<br />
NE(no URI escaping of output) 不在输出转义特殊字符<br />
例如：<br />
RewriteRule /foo/(.*) /bar?arg=P1\%3d$1 [R,NE] 将能正确的将/foo/zoo转换成/bar?arg=P1=zed<br />
PT(pass through to next handler) 传递给下一个处理<br />
例如：<br />
RewriteRule ^/abc(.*) /def$1 [PT] # 将会交给/def规则处理<br />
Alias /def /ghi<br />
S=num(skip next rule(s)) 跳过num条规则<br />
E=VAR:VAL(set environment variable) 设置环境变量<br />
<br />
<br />
#排除拓展名<br />
<p>
	RewriteRule !\.(js|ico|gif|jpg|JPG|png|PNG|css|pdf|swf)$ index.php
</p>
<p>
	#域名重定向
</p>
<p>
	RewriteCond %{HTTP_HOST} ^www.fd.com$<br />
RewriteRule ^(.*)$ https://blog.verytalk.cn$1<br />
</p>