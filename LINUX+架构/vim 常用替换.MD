<p class="p1" style="margin:10px auto;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	<strong style="margin:0px;padding:0px;">%s/\s//g</strong>
</p>
<p class="p1" style="margin:10px auto;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p class="p1" style="margin:10px auto;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	<strong style="margin:0px;padding:0px;">%s/\r//g</strong>
</p>
<p class="p1" style="margin:10px auto;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p class="p1" style="margin:10px auto;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	<strong style="margin:0px;padding:0px;">%s/\n//g</strong>
</p>
<div style="margin:0px;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	<strong style="margin:0px;padding:0px;">&nbsp;</strong>
</div>
<br style="margin:0px;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;" />
<p style="margin:10px auto;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin:10px auto;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	把一个很长的一行按空格分为多行
</p>
<span style="font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">:%s/ +/\r/g</span><br style="margin:0px;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">简单解释一下：</span><br style="margin:0px;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">%s ：在整个文件范围查找替换</span><br style="margin:0px;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">/ ：分隔符</span><br style="margin:0px;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">+ ：匹配空格，其中“ ”表示空格，+表示重复1次或多次，加在一起表示一个或多个空格。</span><br style="margin:0px;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">/r ：换行符</span><br style="margin:0px;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">/g ：全局替换</span><br style="margin:0px;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;" />
<br style="margin:0px;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;" />
<br style="margin:0px;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;" />
<br style="margin:0px;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;" />
<br style="margin:0px;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">删除文章中的空行</span><br style="margin:0px;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">:g/^s*$/d</span><br style="margin:0px;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">简单解释一下：</span><br style="margin:0px;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">g ：全区命令</span><br style="margin:0px;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">/ ：分隔符</span><br style="margin:0px;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">^s*$ ：匹配空行，其中^表示行首，s表示空字符，包括空格和制表符，*重复0到n个前面的字符，$表示行尾。连起来就是匹配只有空字符的行，也就是空行。</span><br style="margin:0px;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">/d ：删除该行</span><br style="margin:0px;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;" />
<br style="margin:0px;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;" />
<br style="margin:0px;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;" />
<br style="margin:0px;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;" />
<br style="margin:0px;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">删除行尾空格：</span><br style="margin:0px;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">:%s= *$==</span><br style="margin:0px;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">该命令全局查找文本文件的行尾空格并删除。</span><br style="margin:0px;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">解释：</span><br style="margin:0px;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">%s全局查找替换</span><br style="margin:0px;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">=为%s命令的分隔符，如果把=换为/，则该命令可以写为:%s/ *$//</span><br style="margin:0px;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">” *$”, $表示行尾，*匹配前面0个到n个字符，*前面是空格，因此此正则表达式匹配行尾的0个到n个字符。</span><br style="margin:0px;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;" />
<p style="margin:10px auto;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	==，分隔符没有中间没有内容，表示删除匹配空格, 在这里表示删除行尾空格。
</p>
<p style="margin:10px auto;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin:10px auto;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin:10px auto;padding:0px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	如何快速去掉^M呢，采取以下步骤就行了：<br style="margin:0px;padding:0px;" />
1. vi dosfilename<br style="margin:0px;padding:0px;" />
2. Press Esc&nbsp;<br style="margin:0px;padding:0px;" />
3. Enter this string: %s/^M//g&nbsp; (^M = Ctrl v + Ctrl m)<br style="margin:0px;padding:0px;" />
4. Press enter&nbsp; (the ^M cleared!)<br style="margin:0px;padding:0px;" />
5. :wq! (save the file)
</p>