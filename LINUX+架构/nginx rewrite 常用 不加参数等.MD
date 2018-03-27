<p>
	<span style="color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;"><span style="color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">&nbsp;rewrite ^/article\.php /affiche/$id.html? permanent;</span><br />
</span> 
</p>
<p>
	<span style="color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;"><br />
</span> 
</p>
<p>
	<span style="color:#454545;">加&nbsp;permanent&nbsp;会做 301跳转</span> 
</p>
<p>
	<span style="color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">关键点就在于“?”这个尾缀。重定向的目标地址结尾处如果加了?号，则不会再转发传递过来原地址的问号?后面的参数那部分。</span> 
</p>
<span style="color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">&nbsp;</span><wbr style="box-sizing:border-box;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;"><span style="color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">&nbsp;&nbsp;</span><wbr style="box-sizing:border-box;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;"><span style="color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">假如又想保留某个特定的参数，那又该如何呢？可以利用Nginx本身就带有的$arg_PARAMETER参数自行补充来实现。</span><br style="box-sizing:border-box;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">例如：</span><br style="box-sizing:border-box;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">把http://example.com/test.php?para=xxx&amp;p=xx 重写向到http://example.com/new.php?p=xx</span><br style="box-sizing:border-box;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;" />
<p>
	<span style="color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">可以写成：rewrite&nbsp;</span><wbr style="box-sizing:border-box;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;"><span style="color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">&nbsp;^/test.php&nbsp;</span><wbr style="box-sizing:border-box;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;"><span style="color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">/new.php?p=$arg_p?&nbsp;</span><wbr style="box-sizing:border-box;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;"><span style="color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">&nbsp;permanent;</span>
</p>
<p>
	<span style="color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;"><br />
</span>
</p>
<p>
	<span style="color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;"><br />
if ($host ~ '^(.*)\.(.*)'){<br />
&nbsp;set $w $1;<br />
&nbsp;set $t $2;<br />
}<br />
<br />
if ($w !~ "(.*)\.(.*)" ){<br />
&nbsp;rewrite .*&nbsp; $scheme://www.$host permanent;<br />
}<br />
<br />
<br />
<br />
#if ($scheme != "https" ){<br />
# rewrite .*&nbsp; https://$host permanent;<br />
#}<br />
<br />
</span>
</p>