<p>
	<span style="color:#3F3F3F;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">http://blog.csdn.net/xinluke/article/details/52182858<br />
</span>
</p>
<p>
	<span style="color:#3F3F3F;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">其中，/etc/localtime是用来描述本机时间，而 /etc/timezone是用来描述本机所属的时区。</span>
</p>
<p>
	<span style="color:#3F3F3F;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;"><span style="color:#333333;font-family:&quot;font-size:12.6px;white-space:pre;background-color:rgba(128, 128, 128, 0.05);">cp /usr/share/zoneinfo/Asia/Shanghai /etc/</span><span class="hljs-keyword" style="box-sizing:border-box;margin:0px;padding:0px;color:#000088;font-family:&quot;font-size:12.6px;white-space:pre;background-color:rgba(128, 128, 128, 0.05);">localtime</span></span>
</p>
<p>
	<span style="color:#3F3F3F;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:1.7em;padding:0px;line-height:27.2px;word-break:normal;color:#3F3F3F;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		在/usr/share/zoneinfo下存放着不同时区格式的时间文件，执行以下命令，可以将本机时间调整至目标时区的时间格式。&nbsp;<br style="box-sizing:border-box;" />
<strong style="box-sizing:border-box;">但是！调整了时间格式，本机所属的时区是保持不变的！</strong>
	</p>
	<h2 id="修改本机时区" style="box-sizing:border-box;font-family:&quot;font-weight:100;line-height:1.1;color:#3F3F3F;margin:0.8em 0px;font-size:2.15em;padding:0px;white-space:normal;background-color:#FFFFFF;">
		<a name="t1"></a>修改本机时区
	</h2>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:1.7em;padding:0px;line-height:27.2px;word-break:normal;color:#3F3F3F;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		在linux中，有一些程序会自己计算时间，不会直接采用带有时区的本机时间格式，会根据UTC时间和本机所属的时区等计算出当前的时间。&nbsp;<br style="box-sizing:border-box;" />
比如jdk应用，时区为“Etc/UTC”，本机时间改为北京时间，通过java代码中new 出来的时间还是utc时间，所以必须得修正本机的时区。
	</p>
	<p>
		<span style="color:#3F3F3F;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;"><br />
</span>
	</p>
<span class="hljs-built_in" style="box-sizing:border-box;margin:0px;padding:0px;color:#660066;font-family:&quot;font-size:12.6px;white-space:pre;background-color:rgba(128, 128, 128, 0.05);">echo</span><span style="color:#333333;font-family:&quot;font-size:12.6px;white-space:pre;background-color:rgba(128, 128, 128, 0.05);"> </span><span class="hljs-string" style="box-sizing:border-box;margin:0px;padding:0px;color:#008800;font-family:&quot;font-size:12.6px;white-space:pre;background-color:rgba(128, 128, 128, 0.05);">'Asia/Shanghai'</span><span style="color:#333333;font-family:&quot;font-size:12.6px;white-space:pre;background-color:rgba(128, 128, 128, 0.05);"> &gt;/etc/timezone</span><br />
</span>
</p>