<p style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	为了完成上述功能，在<a href="http://lib.csdn.net/base/mysql" class="replace_word" title="MySQL知识库" target="_blank" style="color:#DF3434;text-decoration-line:none;font-weight:bold;">MySQL</a>中提供了一些字符串操作的函数，其中SUBSTRING_INDEX(str, delim, count)
</p>
<p style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	str: 要处理的字符串
</p>
<p style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	delim: 分割符
</p>
<p style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	count: 计数 如果为正数，则从左开始数，如果为负数，则从右开始数
</p>
<p style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<br />
</p>
<p style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	例：
</p>
<p style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	str = 'www.baidu.com';
</p>
<div style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	SELECT substring_index('www.baidu.com','.', 1);&nbsp;&nbsp;&nbsp; #www
</div>
<div style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<br />
</div>
<div style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	SELECT substring_index('www.baidu.com','.', 2);&nbsp;&nbsp;&nbsp; #www.baidu
</div>
<div style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<br />
</div>
<div style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	SELECT substring_index('www.baidu.com','.', -1);&nbsp;&nbsp; #com
</div>
<div style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<br />
</div>
<div style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	SELECT substring_index('www.baidu.com','.', -2);&nbsp;&nbsp; #baidu.com
</div>
<div style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<br />
</div>
<div style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	SELECT substring_index(substring_index('www.baidu.com','.', -2), '.', 1);&nbsp; #baidu
</div>
<div style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<br />
</div>
<div style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	有了这个函数的帮助，我们还需要确定什么呢？需要知道&nbsp; 当前要分割的位置
</div>
<div style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	如何来获取当前要分割的位置呢？我们可以先获取总共能拆分成多少个字符串
</div>
<div style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	SELECT LENGTH('1,2,3,4,5,6,7') - LENGTH(REPLACE('1,2,3,4,5,6,7', ',', '')) + 1;
</div>
<div style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	结果为7，那么其实我们想要的就是遍历1到6，分别获取当前位置的字符串：SELECT substring_index(substring_index('1,2,3,4,5,6,7',',', index), ',', -1)
</div>