<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-size:18px;">http://blog.csdn.net/qwlzxx/article/details/77163268<br />
</span>
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-size:18px;"><br />
</span>
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-size:18px;">地址：<a target="_blank" href="https://github.com/spring-cloud/spring-cloud-netflix/issues/768" style="color:#CA0000;text-decoration-line:none;">https://github.com/spring-cloud/spring-cloud-netflix/issues/768</a></span>
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-size:18px;">默认的请求时间为1秒，超过这个时间便超时异常。那么顺着这个思路我们有如下解决方式：</span>
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-size:18px;">1、把时间设长</span>
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-size:18px;">这里设置5秒</span>
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-size:18px;"></span>
</p>
<div class="dp-highlighter bg_html" style="font-family:Consolas, &quot;background-color:#E7E5DC;width:936.531px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;white-space:normal;margin:18px 0px !important;">
	<div class="bar" style="padding-left:45px;">
		<div class="tools" style="padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;border-right:1px solid #E7E5DC;">
			<b>[html]</b>&nbsp;<a href="http://blog.csdn.net/qwlzxx/article/details/77163268#" class="ViewSource" title="view plain" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span data-mod="popu_168">&nbsp;<a href="http://blog.csdn.net/qwlzxx/article/details/77163268#" class="CopyToClipboard" title="copy" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a>
			<div style="position:absolute;left:723px;top:726px;width:18px;height:18px;z-index:99;">
			</div>
</span><span data-mod="popu_169"></span>
		</div>
	</div>
	<ol start="1" class="dp-xml" style="padding:0px;border-top:none;border-right:1px solid #E7E5DC;border-bottom:none;border-left:none;border-image:initial;list-style-position:initial;list-style-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span style="margin:0px;padding:0px;border:none;background-color:inherit;">hystrix:&nbsp;&nbsp;</span></span>
		</li>
		<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;command:&nbsp;&nbsp;</span>
		</li>
		<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;default:&nbsp;&nbsp;</span>
		</li>
		<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;execution:&nbsp;&nbsp;</span>
		</li>
		<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;isolation:&nbsp;&nbsp;</span>
		</li>
		<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;thread:&nbsp;&nbsp;</span>
		</li>
		<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;timeoutInMilliseconds:&nbsp;5000&nbsp;&nbsp;</span>
		</li>
	</ol>
</div>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-size:18px;">2、把超时发生异常属性关闭</span>
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-size:18px;"></span>
</p>
<div class="dp-highlighter bg_html" style="font-family:Consolas, &quot;background-color:#E7E5DC;width:936.531px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;white-space:normal;margin:18px 0px !important;">
	<div class="bar" style="padding-left:45px;">
		<div class="tools" style="padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;border-right:1px solid #E7E5DC;">
			<b>[html]</b>&nbsp;<a href="http://blog.csdn.net/qwlzxx/article/details/77163268#" class="ViewSource" title="view plain" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span data-mod="popu_168">&nbsp;<a href="http://blog.csdn.net/qwlzxx/article/details/77163268#" class="CopyToClipboard" title="copy" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a>
			<div style="position:absolute;left:723px;top:947px;width:18px;height:18px;z-index:99;">
			</div>
</span><span data-mod="popu_169"></span>
		</div>
	</div>
	<ol start="1" class="dp-xml" style="padding:0px;border-top:none;border-right:1px solid #E7E5DC;border-bottom:none;border-left:none;border-image:initial;list-style-position:initial;list-style-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span style="margin:0px;padding:0px;border:none;background-color:inherit;">hystrix:&nbsp;&nbsp;</span></span>
		</li>
		<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;command:&nbsp;&nbsp;</span>
		</li>
		<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;default:&nbsp;&nbsp;</span>
		</li>
		<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;execution:&nbsp;&nbsp;</span>
		</li>
		<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;timeout:&nbsp;&nbsp;</span>
		</li>
		<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;enabled:&nbsp;false&nbsp;&nbsp;</span>
		</li>
	</ol>
</div>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-size:18px;">3、禁用feign的hystrix</span>
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-size:18px;"></span>
</p>
<div class="dp-highlighter bg_html" style="font-family:Consolas, &quot;background-color:#E7E5DC;width:936.531px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;white-space:normal;margin:18px 0px !important;">
	<div class="bar" style="padding-left:45px;">
		<div class="tools" style="padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;border-right:1px solid #E7E5DC;">
			<b>[html]</b>&nbsp;<a href="http://blog.csdn.net/qwlzxx/article/details/77163268#" class="ViewSource" title="view plain" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span data-mod="popu_168">&nbsp;<a href="http://blog.csdn.net/qwlzxx/article/details/77163268#" class="CopyToClipboard" title="copy" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:1px;margin:0px 10px 0px 0px;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a>
			<div style="position:absolute;left:723px;top:1150px;width:18px;height:18px;z-index:99;">
			</div>
</span><span data-mod="popu_169"></span>
		</div>
	</div>
	<ol start="1" class="dp-xml" style="padding:0px;border-top:none;border-right:1px solid #E7E5DC;border-bottom:none;border-left:none;border-image:initial;list-style-position:initial;list-style-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span style="margin:0px;padding:0px;border:none;background-color:inherit;">feign:&nbsp;&nbsp;</span></span>
		</li>
		<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F8F8F8;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;hystrix:&nbsp;&nbsp;</span>
		</li>
		<li class="alt" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;enabled:&nbsp;false&nbsp;&nbsp;</span>
		</li>
	</ol>
</div>
<br style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">这三种任意一种都能解决问题，已经实践过，只需要修改application.yml中添加这些配置即可。</span>