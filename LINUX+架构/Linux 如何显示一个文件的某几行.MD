<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<strong style="margin:0px;padding:0px;">1. 从第1000行开始，显示2000行。即显示1000~2999行</strong>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	cat input_file | tail -n +1000 | head -n 2000
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<strong style="margin:0px;padding:0px;">2. 显示 1000行到3000行</strong>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	cat input_file | head -n&nbsp;3000&nbsp;| tail -n +1001
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	*注意两种方法的顺序
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;line-height:1.8;color:#FF0000;">分解：</span>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;&nbsp;&nbsp; tail -n 1000：显示最后1000行
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;&nbsp;&nbsp; tail -n +1000：从1000行开始显示，显示1000行以后的
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;&nbsp;&nbsp; head&nbsp;-n 1000：显示前面1000行
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<strong style="margin:0px;padding:0px;">3. 用sed命令</strong>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;sed -n '5,10p' input_file这样你就可以只查看文件的第5行到第10行。
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<strong style="margin:0px;padding:0px;">4. 用awk处理</strong>
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	awk 'NR==2, NR==11{print}'&nbsp;&nbsp;input_file
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	或者
</p>
<p style="margin:10px auto;padding:0px;color:#333333;font-family:verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	awk 'NR&gt;2 &amp;&amp; NR&lt;11 {print $0}' &nbsp;input_file
</p>