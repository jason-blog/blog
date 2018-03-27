<br />
FIND_IN_SET() //是精确匹配，字段值以英文”,”分隔<br />
<br />
UNIX_TIMESTAMP(datetime) //处理日期转换为unix时间戳<br />
<br />
FROM_UNIXTIME(unixtime) &nbsp;//处理unix时间戳转换为日期<br />
<br />
<br />
//////////////////指定时间////////////////<br />
select date_sub(now(),interval 1 day);<br />
year<br />
week<br />
month<br />
//////////////////指定时间///////////////<br />
<br />
<br />
<br />
//////////////////////////////////////////////////////////////////<br />
一、数学函数<br />
ABS(x) &nbsp; 返回x的绝对值<br />
BIN(x) &nbsp; 返回x的二进制（OCT返回八进制，HEX返回十六进制）<br />
CEILING(x) &nbsp; 返回大于x的最小整数值<br />
EXP(x) &nbsp; 返回值e（自然对数的底）的x次方<br />
FLOOR(x) &nbsp; 返回小于x的最大整数值<br />
GREATEST(x1,x2,...,xn)返回集合中最大的值<br />
LEAST(x1,x2,...,xn) &nbsp; &nbsp; &nbsp;返回集合中最小的值<br />
LN(x) &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;返回x的自然对数<br />
LOG(x,y)返回x的以y为底的对数<br />
MOD(x,y) &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 返回x/y的模（余数）<br />
PI()返回pi的值（圆周率）<br />
RAND()返回０到１内的随机值,可以通过提供一个参数(种子)使RAND()随机数生成器生成一个指定的值。<br />
ROUND(x,y)返回参数x的四舍五入的有y位小数的值<br />
SIGN(x) 返回代表数字x的符号的值<br />
SQRT(x) 返回一个数的平方根<br />
TRUNCATE(x,y) &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;返回数字x截短为y位小数的结果<br />
<br />
二、聚合函数(常用于GROUP BY从句的SELECT查询中)<br />
AVG(col)返回指定列的平均值<br />
COUNT(col)返回指定列中非NULL值的个数<br />
MIN(col)返回指定列的最小值<br />
MAX(col)返回指定列的最大值<br />
SUM(col)返回指定列的所有值之和<br />
GROUP_CONCAT(col) 返回由属于一组的列值连接组合而成的结果<br />
<br />
三、字符串函数<br />
ASCII(char)返回字符的ASCII码值<br />
BIT_LENGTH(str)返回字符串的比特长度<br />
CONCAT(s1,s2...,sn)将s1,s2...,sn连接成字符串<br />
CONCAT_WS(sep,s1,s2...,sn)将s1,s2...,sn连接成字符串，并用sep字符间隔<br />
INSERT(str,x,y,instr) 将字符串str从第x位置开始，y个字符长的子串替换为字符串instr，返回结果<br />
FIND_IN_SET(str,list)分析逗号分隔的list列表，如果发现str，返回str在list中的位置<br />
LCASE(str)或LOWER(str) 返回将字符串str中所有字符改变为小写后的结果<br />
LEFT(str,x)返回字符串str中最左边的x个字符<br />
LENGTH(s)返回字符串str中的字符数<br />
LTRIM(str) 从字符串str中切掉开头的空格<br />
POSITION(substr,str) 返回子串substr在字符串str中第一次出现的位置<br />
QUOTE(str) 用反斜杠转义str中的单引号<br />
REPEAT(str,srchstr,rplcstr)返回字符串str重复x次的结果<br />
REVERSE(str) 返回颠倒字符串str的结果<br />
RIGHT(str,x) 返回字符串str中最右边的x个字符<br />
RTRIM(str) 返回字符串str尾部的空格<br />
STRCMP(s1,s2)比较字符串s1和s2<br />
TRIM(str)去除字符串首部和尾部的所有空格<br />
UCASE(str)或UPPER(str) 返回将字符串str中所有字符转变为大写后的结果<br />
<br />
四、日期和时间函数<br />
CURDATE()或CURRENT_DATE() 返回当前的日期<br />
CURTIME()或CURRENT_TIME() 返回当前的时间<br />
DATE_ADD(date,INTERVAL int keyword)返回日期date加上间隔时间int的结果(int必须按照关键字进行格式化),如：SELECTDATE_ADD(CURRENT_DATE,INTERVAL 6 MONTH);<br />
DATE_FORMAT(date,fmt) &nbsp;依照指定的fmt格式格式化日期date值<br />
DATE_SUB(date,INTERVAL int keyword)返回日期date加上间隔时间int的结果(int必须按照关键字进行格式化),如：SELECTDATE_SUB(CURRENT_DATE,INTERVAL 6 MONTH);<br />
DAYOFWEEK(date) &nbsp; 返回date所代表的一星期中的第几天(1~7)<br />
DAYOFMONTH(date) &nbsp;返回date是一个月的第几天(1~31)<br />
DAYOFYEAR(date) &nbsp; 返回date是一年的第几天(1~366)<br />
DAYNAME(date) &nbsp; 返回date的星期名，如：SELECT DAYNAME(CURRENT_DATE);<br />
FROM_UNIXTIME(ts,fmt) &nbsp;根据指定的fmt格式，格式化UNIX时间戳ts<br />
HOUR(time) &nbsp; 返回time的小时值(0~23)<br />
MINUTE(time) &nbsp; 返回time的分钟值(0~59)<br />
MONTH(date) &nbsp; 返回date的月份值(1~12)<br />
MONTHNAME(date) &nbsp; 返回date的月份名，如：SELECT MONTHNAME(CURRENT_DATE);<br />
NOW() &nbsp; &nbsp;返回当前的日期和时间<br />
QUARTER(date) &nbsp; 返回date在一年中的季度(1~4)，如SELECT QUARTER(CURRENT_DATE);<br />
WEEK(date) &nbsp; 返回日期date为一年中第几周(0~53)<br />
YEAR(date) &nbsp; 返回日期date的年份(1000~9999)<br />
一些示例：<br />
获取当前系统时间：SELECT FROM_UNIXTIME(UNIX_TIMESTAMP());<br />
SELECT EXTRACT(YEAR_MONTH FROM CURRENT_DATE);<br />
SELECT EXTRACT(DAY_SECOND FROM CURRENT_DATE);<br />
SELECT EXTRACT(HOUR_MINUTE FROM CURRENT_DATE);<br />
返回两个日期值之间的差值(月数)：SELECT PERIOD_DIFF(200302,199802);<br />
在Mysql中计算年龄：<br />
SELECT DATE_FORMAT(FROM_DAYS(TO_DAYS(NOW())-TO_DAYS(birthday)),'%Y')+0 AS age FROM employee;<br />
这样，如果Brithday是未来的年月日的话，计算结果为0。<br />
下面的SQL语句计算员工的绝对年龄，即当Birthday是未来的日期时，将得到负值。<br />
SELECT DATE_FORMAT(NOW(), '%Y') - DATE_FORMAT(birthday, '%Y') -(DATE_FORMAT(NOW(), '00-%m-%d') &lt;DATE_FORMAT(birthday, '00-%m-%d')) AS age from employee<br />
<br />
五、加密函数<br />
AES_ENCRYPT(str,key) &nbsp;返回用密钥key对字符串str利用高级加密标准算法加密后的结果，调用AES_ENCRYPT的结果是一个二进制字符串，以BLOB类型存储<br />
AES_DECRYPT(str,key) &nbsp;返回用密钥key对字符串str利用高级加密标准算法解密后的结果<br />
DECODE(str,key) &nbsp; 使用key作为密钥解密加密字符串str<br />
ENCRYPT(str,salt) &nbsp; 使用UNIXcrypt()函数，用关键词salt(一个可以惟一确定口令的字符串，就像钥匙一样)加密字符串str<br />
ENCODE(str,key) &nbsp; 使用key作为密钥加密字符串str，调用ENCODE()的结果是一个二进制字符串，它以BLOB类型存储<br />
MD5() &nbsp; &nbsp;计算字符串str的MD5校验和<br />
PASSWORD(str) &nbsp; 返回字符串str的加密版本，这个加密过程是不可逆转的，和UNIX密码加密过程使用不同的算法。<br />
SHA() &nbsp; &nbsp;计算字符串str的安全散列算法(SHA)校验和<br />
示例：<br />
SELECT ENCRYPT('root','salt');<br />
SELECT ENCODE('xufeng','key');<br />
SELECT DECODE(ENCODE('xufeng','key'),'key');#加解密放在一起<br />
SELECT AES_ENCRYPT('root','key');<br />
SELECT AES_DECRYPT(AES_ENCRYPT('root','key'),'key');<br />
SELECT MD5('123456');<br />
SELECT SHA('123456');<br />
<br />
六、控制流函数<br />
MySQL有4个函数是用来进行条件操作的，这些函数可以实现SQL的条件逻辑，允许开发者将一些应用程序业务逻辑转换到数据库后台。<br />
MySQL控制流函数：<br />
CASE WHEN[test1] THEN [result1]...ELSE [default] END如果testN是真，则返回resultN，否则返回default<br />
CASE [test] WHEN[val1] THEN [result]...ELSE [default]END &nbsp;如果test和valN相等，则返回resultN，否则返回default<br />
IF(test,t,f) &nbsp; 如果test是真，返回t；否则返回f<br />
IFNULL(arg1,arg2) 如果arg1不是空，返回arg1，否则返回arg2<br />
NULLIF(arg1,arg2) 如果arg1=arg2返回NULL；否则返回arg1<br />
这些函数的第一个是IFNULL()，它有两个参数，并且对第一个参数进行判断。如果第一个参数不是NULL，函数就会向调用者返回第一个参数；如果是NULL,将返回第二个参数。<br />
如：SELECT IFNULL(1,2), IFNULL(NULL,10),IFNULL(4*NULL,'false');<br />
NULLIF()函数将会检验提供的两个参数是否相等，如果相等，则返回NULL，如果不相等，就返回第一个参数。<br />
如：SELECT NULLIF(1,1),NULLIF('A','B'),NULLIF(2+3,4+1);<br />
和许多脚本语言提供的IF()函数一样，MySQL的IF()函数也可以建立一个简单的条件测试，这个函数有三个参数，第一个是要被判断的表达式，如果表达式为真，IF()将会返回第二个参数，如果为假，IF()将会返回第三个参数。<br />
如：SELECTIF(1&lt;10,2,3),IF(56&gt;100,'true','false');<br />
IF()函数在只有两种可能结果时才适合使用。然而，在现实世界中，我们可能发现在条件测试中会需要多个分支。在这种情况下，MySQL提供了CASE函数，它和PHP及Perl语言的switch-case条件例程一样。<br />
CASE函数的格式有些复杂，通常如下所示：<br />
CASE [expression to be evaluated]<br />
WHEN [val 1] THEN [result 1]<br />
WHEN [val 2] THEN [result 2]<br />
WHEN [val 3] THEN [result 3]<br />
......<br />
WHEN [val n] THEN [result n]<br />
ELSE [default result]<br />
END<br />
这里，第一个参数是要被判断的值或表达式，接下来的是一系列的WHEN-THEN块，每一块的第一个参数指定要比较的值，如果为真，就返回结果。所有的WHEN-THEN块将以ELSE块结束，当END结束了所有外部的CASE块时，如果前面的每一个块都不匹配就会返回ELSE块指定的默认结果。如果没有指定ELSE块，而且所有的WHEN-THEN比较都不是真，MySQL将会返回NULL。<br />
CASE函数还有另外一种句法，有时使用起来非常方便，如下：<br />
CASE<br />
WHEN [conditional test 1] THEN [result 1]<br />
WHEN [conditional test 2] THEN [result 2]<br />
ELSE [default result]<br />
END<br />
这种条件下，返回的结果取决于相应的条件测试是否为真。<br />
示例：<br />
mysql&gt;SELECT CASE 'green'<br />
&nbsp; &nbsp; &nbsp;WHEN 'red' THEN 'stop'<br />
&nbsp; &nbsp; &nbsp;WHEN 'green' THEN 'go' END;<br />
SELECT CASE 9 WHEN 1 THEN 'a' WHEN 2 THEN 'b' ELSE 'N/A' END;<br />
SELECT CASE WHEN (2+2)=4 THEN 'OK' WHEN(2+2)&lt;&gt;4 THEN 'not OK' END ASSTATUS;<br />
SELECT Name,IF((IsActive = 1),'已激活','未激活') AS RESULT FROMUserLoginInfo;<br />
SELECT fname,lname,(math+sci+lit) AS total,<br />
CASE WHEN (math+sci+lit) &lt; 50 THEN 'D'<br />
WHEN (math+sci+lit) BETWEEN 50 AND 150 THEN 'C'<br />
WHEN (math+sci+lit) BETWEEN 151 AND 250 THEN 'B'<br />
ELSE 'A' END<br />
AS grade FROM marks;<br />
SELECT IF(ENCRYPT('sue','ts')=upass,'allow','deny') AS LoginResultFROM users WHERE uname = 'sue';#一个登陆验证<br />
<br />
七、格式化函数<br />
DATE_FORMAT(date,fmt) &nbsp;依照字符串fmt格式化日期date值<br />
FORMAT(x,y) &nbsp; 把x格式化为以逗号隔开的数字序列，y是结果的小数位数<br />
INET_ATON(ip) &nbsp; 返回IP地址的数字表示<br />
INET_NTOA(num) &nbsp; 返回数字所代表的IP地址<br />
TIME_FORMAT(time,fmt) &nbsp;依照字符串fmt格式化时间time值<br />
其中最简单的是FORMAT()函数，它可以把大的数值格式化为以逗号间隔的易读的序列。<br />
示例：<br />
SELECT FORMAT(34234.34323432,3);<br />
SELECT DATE_FORMAT(NOW(),'%W,%D %M %Y %r');<br />
SELECT DATE_FORMAT(NOW(),'%Y-%m-%d');<br />
SELECT DATE_FORMAT(19990330,'%Y-%m-%d');<br />
SELECT DATE_FORMAT(NOW(),'%h:%i %p');<br />
SELECT INET_ATON('10.122.89.47');<br />
SELECT INET_NTOA(175790383);<br />
<br />
八、类型转化函数<br />
为了进行数据类型转化，MySQL提供了CAST()函数，它可以把一个值转化为指定的数据类型。类型有：BINARY,CHAR,DATE,TIME,DATETIME,SIGNED,UNSIGNED<br />
示例：<br />
SELECT CAST(NOW() AS SIGNED INTEGER),CURDATE()+0;<br />
SELECT 'f'=BINARY 'F','f'=CAST('F' AS BINARY);<br />
<br />
九、系统信息函数<br />
DATABASE() &nbsp; 返回当前数据库名<br />
BENCHMARK(count,expr) &nbsp;将表达式expr重复运行count次<br />
CONNECTION_ID() &nbsp; 返回当前客户的连接ID<br />
FOUND_ROWS() &nbsp; 返回最后一个SELECT查询进行检索的总行数<br />
USER()或SYSTEM_USER() &nbsp;返回当前登陆用户名<br />
VERSION() &nbsp; 返回MySQL服务器的版本<br />
示例：<br />
SELECT DATABASE(),VERSION(),USER();<br />
SELECTBENCHMARK(9999999,LOG(RAND()*PI()));#该例中,MySQL计算LOG(RAND()*PI())表达式9999999次。<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />