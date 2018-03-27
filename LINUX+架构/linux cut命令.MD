<div style="color:#666666;font-family:宋体, Arial;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	cut命令可以从一个文本文件或者文本流中提取文本列。
</div>
<div style="color:#666666;font-family:宋体, Arial;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;命令用法：
</div>
<div style="color:#666666;font-family:宋体, Arial;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; cut -b list [-n] [file ...]
</div>
<div style="color:#666666;font-family:宋体, Arial;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; cut -c list [file ...]
</div>
<div style="color:#666666;font-family:宋体, Arial;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; cut -f list [-d delim][-s][file ...]
</div>
<div style="color:#666666;font-family:宋体, Arial;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</div>
<div style="color:#666666;font-family:宋体, Arial;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</div>
<div style="color:#666666;font-family:宋体, Arial;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	l&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 上面的-b、-c、-f分别表示字节、字符、字段（即byte、character、field）；
</div>
<div style="color:#666666;font-family:宋体, Arial;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	l&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; list表示-b、-c、-f操作范围，-n常常表示具体数字；
</div>
<div style="color:#666666;font-family:宋体, Arial;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	l&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; file表示的自然是要操作的文本文件的名称；
</div>
<div style="color:#666666;font-family:宋体, Arial;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	l&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; delim（英文全写：delimiter）表示分隔符，默认情况下为TAB；
</div>
<div style="color:#666666;font-family:宋体, Arial;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	l&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; -s表示不包括那些不含分隔符的行（这样有利于去掉注释和标题）
</div>
<div style="color:#666666;font-family:宋体, Arial;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	上面三种方式中，表示从指定的范围中提取字节（-b）、或字符（-c）、或字段（-f）。
</div>
<div style="color:#666666;font-family:宋体, Arial;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	范围的表示方法：
</div>
<p>
	<br />
</p>
<p>
	<br />
</p>
<p>
	<strong>&nbsp;svn info | grep Revision | cut -f2 -d:</strong><strong></strong> 
</p>
<p>
	<strong><br />
</strong>
</p>
<p>
	<strong>http://blog.chinaunix.net/uid-20749043-id-1878322.html<br />
</strong>
</p>
<p>
	<br />
</p>