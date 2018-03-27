<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	mysql数据库设计，其中，对于数据性能优化，字段类型考虑很重要，搜集了些资料，整理分享出来，这篇为有关mysql整型bigint、int、mediumint、smallint 和 tinyint的语法介绍，如下：<span style="color:#0000FF;"><strong><br />
1、bigint</strong></span>
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	从 -2^63 (-9223372036854775808) 到 2^63-1 (9223372036854775807) 的整型数据（所有数字），无符号的范围是0到
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	18446744073709551615。一位为 8 个字节。
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="color:#0000FF;"><strong>2、int</strong></span>
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	一个正常大小整数。有符号的范围是-2^31 (-2,147,483,648) 到 2^31 - 1 (2,147,483,647) 的整型数据（所有数字），无符号的范围是0到4294967295。一位大小为 4 个字节。<br />
<strong>int</strong>&nbsp;的 SQL-92 同义词为&nbsp;<strong>integer</strong>。<br />
<span style="color:#0000FF;"><strong>3、mediumint</strong></span><br />
一个中等大小整数，有符号的范围是-8388608到8388607，无符号的范围是0到16777215。 一位大小为3个字节。
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="color:#0000FF;"><strong>4、smallint</strong></span>
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	一个小整数。有符号的范围是-2^15 (-32,768) 到 2^15 - 1 (32,767) 的整型数据，无符号的范围是0到65535。一位大小为 2 个字节。MySQL提供的功能已经绰绰有余，而且由于MySQL是开放源码软件，因此可以大大降低总体拥有成本。
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="color:#0000FF;"><strong>5、tinyint</strong></span>
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	有符号的范围是<span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;font-size:12px;">-128 - 127，无符号的范围是</span><span style="font-size:12px;line-height:1.5;">&nbsp;从 0 到 255 的整型数据。一位大小为 1 字节。</span>
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<br />
注意，所有算术运算用有符号的BIGINT或DOUBLE值完成，因此你不应该使用大于9223372036854775807（63位)的有符号大整数，除了位函数！注意，当两个参数是INTEGER值时，-、+和*将使用BIGINT运算！这意味着如果你乘2个大整数(或来自于返回整数的函数)，如果结果大于9223372036854775807，你可以得到意外的结果。一个浮点数字，不能是无符号的，对一个单精度浮点数，其精度可以是&lt;=24，对一个双精度浮点数，是在25 和53之间，这些类型如FLOAT和DOUBLE类型马上在下面描述。FLOAT(X)有对应的FLOAT和DOUBLE相同的范围，但是显示尺寸和小数位数是未定义的。在MySQL3.23中，这是一个真正的浮点值。在更早的MySQL版本中，FLOAT(precision)总是有2位小数。该句法为了ODBC兼容性而提供。
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Helvetica, Tahoma, Arial, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;">MySQL中各数据类型的取值范围&nbsp;</span><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<strong><span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;color:#0000FF;">TINYINT&nbsp;</span></strong><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;">-128 - 127&nbsp;</span><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<strong><span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;color:#0000FF;">TINYINT UNSIGNED&nbsp;</span></strong><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;">0 - 255&nbsp;</span><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<strong><span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;color:#0000FF;">SMALLINT&nbsp;</span></strong><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;">-32768 - 32767&nbsp;</span><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<strong><span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;color:#0000FF;">SMALLINT UNSIGNED&nbsp;</span></strong><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;">0 - 65535&nbsp;</span><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<strong><span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;color:#0000FF;">MEDIUMINT&nbsp;</span></strong><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;">-8388608 - 8388607&nbsp;</span><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<strong><span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;color:#0000FF;">MEDIUMINT UNSIGNED&nbsp;</span></strong><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;">0 - 16777215&nbsp;</span><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<strong><span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;color:#0000FF;">INT 或 INTEGER&nbsp;</span></strong><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;">-2147483648 - 2147483647&nbsp;</span><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<strong><span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;color:#0000FF;">INT UNSIGNED 或 INTEGER UNSIGNED&nbsp;</span></strong><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;">0 - 4294967295&nbsp;</span><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<strong><span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;color:#0000FF;">BIGINT&nbsp;</span></strong><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;">-9223372036854775808 - 9223372036854775807&nbsp;</span><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<strong><span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;color:#0000FF;">BIGINT UNSIGNED&nbsp;</span></strong><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;">0 - 18446744073709551615&nbsp;</span><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<strong><span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;color:#0000FF;">FLOAT&nbsp;</span></strong><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;">-3.402823466E+38 - -1.175494351E-38,0,1.175494351E-38 - 3.402823466E+38&nbsp;</span><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<strong><span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;color:#0000FF;">DOUBLE 或 DOUBLE PRECISION 或 REAL&nbsp;</span></strong><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;">-1.7976931348623157E+308 - -2.2250738585072014E-308,0,2.2250738585072014E-308 - 1.7976931348623157E+308&nbsp;</span><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<strong><span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;color:#0000FF;">DECIMAL[(M,[D])] 或 NUMERIC(M,D)&nbsp;</span></strong><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;">由M(整个数字的长度,包括小数点,小数点左边的位数,小数点右边的位数,但不包括负号)和D(小数点右边的位数)来决定,M缺省为10,D缺省为0&nbsp;</span><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<strong><span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;color:#0000FF;">DATE&nbsp;</span></strong><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;">1000-01-01 - 9999-12-31&nbsp;</span><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<strong><span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;color:#0000FF;">DATETIME&nbsp;</span></strong><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;">1000-01-01 00:00:00 - 9999-12-31 23:59:59&nbsp;</span><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<strong><span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;color:#0000FF;">TIMESTAMP&nbsp;</span></strong><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;">1970-01-01 00:00:00 - 2037年的某天(具体是哪天我也不知道,呵呵)&nbsp;</span><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<strong><span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;color:#0000FF;">TIME</span></strong><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;">-838:59:59' to 838:59:59&nbsp;</span><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<strong><span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;color:#0000FF;">YEAR[(2|4)]&nbsp;</span></strong><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;">缺省为4位格式,4位格式取值范围为1901 - 2155,0000,2位格式取值范围为70-69(1970-2069)&nbsp;</span><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<strong><span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;color:#0000FF;">CHAR(M) [BINARY] 或 NCHAR(M) [BINARY]&nbsp;</span></strong><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;">M的范围为1 - 255,如果没有BINARY项,则不分大小写,NCHAR表示使用缺省的字符集.在数据库中以空格补足,但在取出来时末尾的空格将自动去掉.&nbsp;</span><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<strong><span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;color:#0000FF;">[NATIONAL] VARCHAR(M) [BINARY]&nbsp;</span></strong><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;">M的范围为1 - 255.在数据库中末尾的空格将自动去掉.&nbsp;</span><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<strong><span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;color:#0000FF;">TINYBLOB 或 TINYTEXT&nbsp;</span></strong><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;">255(2^8-1)个字符&nbsp;</span><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<strong><span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;color:#0000FF;">BLOB 或 TEXT&nbsp;</span></strong><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;">65535(2^16-1)个字符&nbsp;</span><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<strong><span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;color:#0000FF;">MEDIUMBLOB 或 MEDIUMTEXT&nbsp;</span></strong><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;">16777215 (2^24-1)个字符&nbsp;</span><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<strong><span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;color:#0000FF;">LONGBLOB 或 LONGTEXT&nbsp;</span></strong><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;">4294967295 (2^32-1)个字符&nbsp;</span><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<strong><span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;color:#0000FF;">ENUM('value1','value2',...)&nbsp;</span></strong><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;">可以总共有65535个不同的值&nbsp;</span><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<strong><span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;color:#0000FF;">SET('value1','value2',...)&nbsp;</span></strong><br style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;" />
<span style="font-family:Verdana, Arial, Helvetica, sans-serif;line-height:20px;">最多有64个成员&nbsp;</span>
</p>