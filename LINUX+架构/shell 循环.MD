<p>
	<br />
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
	<strong>http://blog.csdn.net/babyfish13/article/details/52981110</strong>
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
	<strong><span style="font-size:18px;">第一类：数字性循环</span></strong><br />
-----------------------------<br />
<strong>for1-1.sh</strong>
</p>
<div class="dp-highlighter bg_html" style="font-family:Consolas, &quot;font-size:12px;width:936.563px;overflow-x:auto;overflow-y:hidden;padding-top:1px;background-image:url(&quot;background-position:right top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;opacity:0.6;position:relative;margin:18px 0px !important;">
	<div class="bar" style="padding-left:45px;">
		<div class="tools" style="padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;border-left:3px solid #6CE26C;">
			<b>[html]</b>&nbsp;<a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="ViewSource" title="view plain" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">view plain</a><span data-mod="popu_168">&nbsp;<a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="CopyToClipboard" title="copy" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">copy</a>
			<div style="position:absolute;left:668px;top:509px;width:25px;height:14px;z-index:99;">
			</div>
</span><span data-mod="popu_169">&nbsp;<a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="PrintSource" title="print" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">print</a></span><a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="About" title="?" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">?</a>
		</div>
	</div>
	<ol start="1" class="dp-xml" style="padding:0px;border:none;position:relative;list-style-position:initial;list-style-image:initial;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">#!/bin/bash&nbsp;&nbsp;</span>
		</li>
		<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;</span>
		</li>
		<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">for((<span class="attribute" style="margin:0px;padding:0px;border:none;color:red;background-color:inherit;">i</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">=</span><span class="attribute-value" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">1</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">;i</span><span class="tag" style="color:#993300;margin:0px;padding:0px;border:none;background-color:inherit;font-weight:bold;">&lt;</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">=10;i++));&nbsp;&nbsp;</span></span>
		</li>
		<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">do&nbsp;&nbsp;&nbsp;</span>
		</li>
		<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">echo&nbsp;$(expr&nbsp;$i&nbsp;\*&nbsp;3&nbsp;+&nbsp;1);&nbsp;&nbsp;</span>
		</li>
		<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">done&nbsp;&nbsp;</span>
		</li>
	</ol>
</div>
<br />
<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
	-----------------------------<br />
<strong>for1-2.sh</strong>
</p>
<div class="dp-highlighter bg_html" style="font-family:Consolas, &quot;font-size:12px;width:936.563px;overflow-x:auto;overflow-y:hidden;padding-top:1px;background-image:url(&quot;background-position:right top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;opacity:0.6;position:relative;margin:18px 0px !important;">
	<div class="bar" style="padding-left:45px;">
		<div class="tools" style="padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;border-left:3px solid #6CE26C;">
			<b>[html]</b>&nbsp;<a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="ViewSource" title="view plain" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">view plain</a><span data-mod="popu_168">&nbsp;<a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="CopyToClipboard" title="copy" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">copy</a>
			<div style="position:absolute;left:668px;top:753px;width:25px;height:14px;z-index:99;">
			</div>
</span><span data-mod="popu_169">&nbsp;<a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="PrintSource" title="print" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">print</a></span><a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="About" title="?" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">?</a>
		</div>
	</div>
	<ol start="1" class="dp-xml" style="padding:0px;border:none;position:relative;list-style-position:initial;list-style-image:initial;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">#!/bin/bash&nbsp;&nbsp;</span>
		</li>
		<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;</span>
		</li>
		<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">for&nbsp;i&nbsp;in&nbsp;$(seq&nbsp;1&nbsp;10)&nbsp;&nbsp;</span>
		</li>
		<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">do&nbsp;&nbsp;&nbsp;</span>
		</li>
		<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">echo&nbsp;$(expr&nbsp;$i&nbsp;\*&nbsp;3&nbsp;+&nbsp;1);&nbsp;&nbsp;</span>
		</li>
		<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">done&nbsp;&nbsp;</span>
		</li>
	</ol>
</div>
<br />
<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
	-----------------------------<br />
<strong>for1-3.sh</strong>
</p>
<div class="dp-highlighter bg_html" style="font-family:Consolas, &quot;font-size:12px;width:936.563px;overflow-x:auto;overflow-y:hidden;padding-top:1px;background-image:url(&quot;background-position:right top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;opacity:0.6;position:relative;margin:18px 0px !important;">
	<div class="bar" style="padding-left:45px;">
		<div class="tools" style="padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;border-left:3px solid #6CE26C;">
			<b>[html]</b>&nbsp;<a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="ViewSource" title="view plain" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">view plain</a><span data-mod="popu_168">&nbsp;<a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="CopyToClipboard" title="copy" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">copy</a>
			<div style="position:absolute;left:668px;top:998px;width:25px;height:14px;z-index:99;">
			</div>
</span><span data-mod="popu_169">&nbsp;<a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="PrintSource" title="print" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">print</a></span><a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="About" title="?" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">?</a>
		</div>
	</div>
	<ol start="1" class="dp-xml" style="padding:0px;border:none;position:relative;list-style-position:initial;list-style-image:initial;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">#!/bin/bash&nbsp;&nbsp;</span>
		</li>
		<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;</span>
		</li>
		<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">for&nbsp;i&nbsp;in&nbsp;{1..10}&nbsp;&nbsp;</span>
		</li>
		<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">do&nbsp;&nbsp;</span>
		</li>
		<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">echo&nbsp;$(expr&nbsp;$i&nbsp;\*&nbsp;3&nbsp;+&nbsp;1);&nbsp;&nbsp;</span>
		</li>
		<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">done&nbsp;&nbsp;</span>
		</li>
	</ol>
</div>
<br />
<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
	-----------------------------<br />
<strong>for1-4.sh</strong>
</p>
<div class="dp-highlighter bg_html" style="font-family:Consolas, &quot;font-size:12px;width:936.563px;overflow-x:auto;overflow-y:hidden;padding-top:1px;background-image:url(&quot;background-position:right top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;opacity:0.6;position:relative;margin:18px 0px !important;">
	<div class="bar" style="padding-left:45px;">
		<div class="tools" style="padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;border-left:3px solid #6CE26C;">
			<b>[html]</b>&nbsp;<a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="ViewSource" title="view plain" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">view plain</a><span data-mod="popu_168">&nbsp;<a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="CopyToClipboard" title="copy" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">copy</a>
			<div style="position:absolute;left:668px;top:1242px;width:25px;height:14px;z-index:99;">
			</div>
</span><span data-mod="popu_169">&nbsp;<a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="PrintSource" title="print" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">print</a></span><a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="About" title="?" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">?</a>
		</div>
	</div>
	<ol start="1" class="dp-xml" style="padding:0px;border:none;position:relative;list-style-position:initial;list-style-image:initial;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">#!/bin/bash&nbsp;&nbsp;</span>
		</li>
		<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;</span>
		</li>
		<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">awk&nbsp;'BEGIN{for(<span class="attribute" style="margin:0px;padding:0px;border:none;color:red;background-color:inherit;">i</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">=</span><span class="attribute-value" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">1</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">;&nbsp;i</span><span class="tag" style="color:#993300;margin:0px;padding:0px;border:none;background-color:inherit;font-weight:bold;">&lt;</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">=10;&nbsp;i++)&nbsp;print&nbsp;i}'&nbsp;&nbsp;</span></span>
		</li>
	</ol>
</div>
<br />
<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
	<span style="font-size:18px;"><strong>第二类：字符性循环</strong></span><br />
-----------------------------<br />
<strong>for2-1.sh</strong>
</p>
<div class="dp-highlighter bg_html" style="font-family:Consolas, &quot;font-size:12px;width:936.563px;overflow-x:auto;overflow-y:hidden;padding-top:1px;background-image:url(&quot;background-position:right top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;opacity:0.6;position:relative;margin:18px 0px !important;">
	<div class="bar" style="padding-left:45px;">
		<div class="tools" style="padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;border-left:3px solid #6CE26C;">
			<b>[html]</b>&nbsp;<a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="ViewSource" title="view plain" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">view plain</a><span data-mod="popu_168">&nbsp;<a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="CopyToClipboard" title="copy" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">copy</a>
			<div style="position:absolute;left:668px;top:1460px;width:25px;height:14px;z-index:99;">
			</div>
</span><span data-mod="popu_169">&nbsp;<a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="PrintSource" title="print" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">print</a></span><a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="About" title="?" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">?</a>
		</div>
	</div>
	<ol start="1" class="dp-xml" style="padding:0px;border:none;position:relative;list-style-position:initial;list-style-image:initial;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">#!/bin/bash&nbsp;&nbsp;</span>
		</li>
		<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;</span>
		</li>
		<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">for&nbsp;i&nbsp;in&nbsp;`ls`;&nbsp;&nbsp;</span>
		</li>
		<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">do&nbsp;&nbsp;&nbsp;</span>
		</li>
		<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">echo&nbsp;$i&nbsp;is&nbsp;file&nbsp;name\!&nbsp;;&nbsp;&nbsp;</span>
		</li>
		<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">done&nbsp;&nbsp;</span>
		</li>
	</ol>
</div>
<br />
<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
	-----------------------------<br />
<strong>for2-2.sh</strong>
</p>
<div class="dp-highlighter bg_html" style="font-family:Consolas, &quot;font-size:12px;width:936.563px;overflow-x:auto;overflow-y:hidden;padding-top:1px;background-image:url(&quot;background-position:right top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;opacity:0.6;position:relative;margin:18px 0px !important;">
	<div class="bar" style="padding-left:45px;">
		<div class="tools" style="padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;border-left:3px solid #6CE26C;">
			<b>[html]</b>&nbsp;<a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="ViewSource" title="view plain" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">view plain</a><span data-mod="popu_168">&nbsp;<a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="CopyToClipboard" title="copy" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">copy</a>
			<div style="position:absolute;left:668px;top:1705px;width:25px;height:14px;z-index:99;">
			</div>
</span><span data-mod="popu_169">&nbsp;<a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="PrintSource" title="print" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">print</a></span><a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="About" title="?" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">?</a>
		</div>
	</div>
	<ol start="1" class="dp-xml" style="padding:0px;border:none;position:relative;list-style-position:initial;list-style-image:initial;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">#!/bin/bash&nbsp;&nbsp;</span>
		</li>
		<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;</span>
		</li>
		<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">for&nbsp;i&nbsp;in&nbsp;$*&nbsp;;&nbsp;&nbsp;</span>
		</li>
		<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">do&nbsp;&nbsp;</span>
		</li>
		<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">echo&nbsp;$i&nbsp;is&nbsp;input&nbsp;chart\!&nbsp;;&nbsp;&nbsp;</span>
		</li>
		<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">done&nbsp;&nbsp;</span>
		</li>
	</ol>
</div>
<br />
<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
	-----------------------------<br />
<strong>for2-3.sh</strong>
</p>
<div class="dp-highlighter bg_html" style="font-family:Consolas, &quot;font-size:12px;width:936.563px;overflow-x:auto;overflow-y:hidden;padding-top:1px;background-image:url(&quot;background-position:right top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;opacity:0.6;position:relative;margin:18px 0px !important;">
	<div class="bar" style="padding-left:45px;">
		<div class="tools" style="padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;border-left:3px solid #6CE26C;">
			<b>[html]</b>&nbsp;<a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="ViewSource" title="view plain" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">view plain</a><span data-mod="popu_168">&nbsp;<a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="CopyToClipboard" title="copy" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">copy</a>
			<div style="position:absolute;left:668px;top:1949px;width:25px;height:14px;z-index:99;">
			</div>
</span><span data-mod="popu_169">&nbsp;<a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="PrintSource" title="print" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">print</a></span><a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="About" title="?" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">?</a>
		</div>
	</div>
	<ol start="1" class="dp-xml" style="padding:0px;border:none;position:relative;list-style-position:initial;list-style-image:initial;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">#!/bin/bash&nbsp;&nbsp;</span>
		</li>
		<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;</span>
		</li>
		<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">for&nbsp;i&nbsp;in&nbsp;f1&nbsp;f2&nbsp;f3&nbsp;;&nbsp;&nbsp;</span>
		</li>
		<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">do&nbsp;&nbsp;</span>
		</li>
		<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">echo&nbsp;$i&nbsp;is&nbsp;appoint&nbsp;;&nbsp;&nbsp;</span>
		</li>
		<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">done&nbsp;&nbsp;</span>
		</li>
	</ol>
</div>
<br />
<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
	-----------------------------<br />
<strong>for2-4.sh</strong>
</p>
<div class="dp-highlighter bg_html" style="font-family:Consolas, &quot;font-size:12px;width:936.563px;overflow-x:auto;overflow-y:hidden;padding-top:1px;background-image:url(&quot;background-position:right top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;opacity:0.6;position:relative;margin:18px 0px !important;">
	<div class="bar" style="padding-left:45px;">
		<div class="tools" style="padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;border-left:3px solid #6CE26C;">
			<b>[html]</b>&nbsp;<a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="ViewSource" title="view plain" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">view plain</a><span data-mod="popu_168">&nbsp;<a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="CopyToClipboard" title="copy" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">copy</a>
			<div style="position:absolute;left:668px;top:2194px;width:25px;height:14px;z-index:99;">
			</div>
</span><span data-mod="popu_169">&nbsp;<a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="PrintSource" title="print" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">print</a></span><a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="About" title="?" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">?</a>
		</div>
	</div>
	<ol start="1" class="dp-xml" style="padding:0px;border:none;position:relative;list-style-position:initial;list-style-image:initial;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">#!/bin/bash&nbsp;&nbsp;</span>
		</li>
		<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;</span>
		</li>
		<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span class="attribute" style="margin:0px;padding:0px;border:none;color:red;background-color:inherit;">list</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">=</span><span class="attribute-value" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">"rootfs&nbsp;usr&nbsp;data&nbsp;data2"</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;&nbsp;</span></span>
		</li>
		<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">for&nbsp;i&nbsp;in&nbsp;$list;&nbsp;&nbsp;</span>
		</li>
		<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">do&nbsp;&nbsp;</span>
		</li>
		<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">echo&nbsp;$i&nbsp;is&nbsp;appoint&nbsp;;&nbsp;&nbsp;</span>
		</li>
		<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">done&nbsp;&nbsp;</span>
		</li>
	</ol>
</div>
<br />
<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
	<span style="font-size:18px;"><strong>第三类：路径查找</strong></span><br />
-----------------------------<br />
<strong>for3-1.sh</strong>
</p>
<div class="dp-highlighter bg_html" style="font-family:Consolas, &quot;font-size:12px;width:936.563px;overflow-x:auto;overflow-y:hidden;padding-top:1px;background-image:url(&quot;background-position:right top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;opacity:0.6;position:relative;margin:18px 0px !important;">
	<div class="bar" style="padding-left:45px;">
		<div class="tools" style="padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;border-left:3px solid #6CE26C;">
			<b>[html]</b>&nbsp;<a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="ViewSource" title="view plain" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">view plain</a><span data-mod="popu_168">&nbsp;<a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="CopyToClipboard" title="copy" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">copy</a>
			<div style="position:absolute;left:668px;top:2481px;width:25px;height:14px;z-index:99;">
			</div>
</span><span data-mod="popu_169">&nbsp;<a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="PrintSource" title="print" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">print</a></span><a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="About" title="?" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">?</a>
		</div>
	</div>
	<ol start="1" class="dp-xml" style="padding:0px;border:none;position:relative;list-style-position:initial;list-style-image:initial;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">#!/bin/bash&nbsp;&nbsp;</span>
		</li>
		<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;</span>
		</li>
		<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">for&nbsp;file&nbsp;in&nbsp;/proc/*;&nbsp;&nbsp;</span>
		</li>
		<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">do&nbsp;&nbsp;</span>
		</li>
		<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">echo&nbsp;$file&nbsp;is&nbsp;file&nbsp;path&nbsp;\!&nbsp;;&nbsp;&nbsp;</span>
		</li>
		<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">done&nbsp;&nbsp;</span>
		</li>
	</ol>
</div>
<br />
<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
	-----------------------------<br />
<strong>for3-2.sh</strong>
</p>
<div class="dp-highlighter bg_html" style="font-family:Consolas, &quot;font-size:12px;width:936.563px;overflow-x:auto;overflow-y:hidden;padding-top:1px;background-image:url(&quot;background-position:right top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;opacity:0.6;position:relative;margin:18px 0px !important;">
	<div class="bar" style="padding-left:45px;">
		<div class="tools" style="padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;border-left:3px solid #6CE26C;">
			<b>[html]</b>&nbsp;<a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="ViewSource" title="view plain" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">view plain</a><span data-mod="popu_168">&nbsp;<a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="CopyToClipboard" title="copy" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">copy</a>
			<div style="position:absolute;left:668px;top:2726px;width:25px;height:14px;z-index:99;">
			</div>
</span><span data-mod="popu_169">&nbsp;<a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="PrintSource" title="print" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">print</a></span><a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="About" title="?" target="_blank" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">?</a>
		</div>
	</div>
	<ol start="1" class="dp-xml" style="padding:0px;border:none;position:relative;list-style-position:initial;list-style-image:initial;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">#!/bin/bash&nbsp;&nbsp;</span>
		</li>
		<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;</span>
		</li>
		<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">for&nbsp;file&nbsp;in&nbsp;$(ls&nbsp;*.sh)&nbsp;&nbsp;</span>
		</li>
		<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">do&nbsp;&nbsp;</span>
		</li>
		<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;color:inherit;line-height:18px;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">echo&nbsp;$file&nbsp;is&nbsp;file&nbsp;path&nbsp;\!&nbsp;;&nbsp;&nbsp;</span>
		</li>
		<li class="" style="border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;line-height:18px;margin:0px !important;padding:0px 3px 0px 10px !important;list-style-position:outside !important;">
			<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">done&nbsp;&nbsp;</span>
		</li>
	</ol>
</div>
<p>
	<br />
</p>
<div class="bdsharebuttonbox tracking-ad bdshare-button-style0-16" data-mod="popu_172" data-bd-bind="1509529058794" style="zoom:1;font-family:Arial, Console, Verdana, &quot;white-space:normal;background-color:#FFFFFF;float:right;">
	<a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="bds_more" data-cmd="more" target="_blank" style="color:#333333;text-decoration-line:none;float:left;padding-left:17px;line-height:16px;height:16px;background-repeat:no-repeat;cursor:pointer;margin:6px 6px 6px 0px;background-image:url(&quot;http://bdimg.share.baidu.com/static/api/img/share/icons_0_16.png?v=d754dcc0.png&quot;background-position:0px 0px !important;"></a><a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="bds_qzone" data-cmd="qzone" title="分享到QQ空间" target="_blank" style="color:#FF9900;text-decoration-line:none;float:left;padding-left:17px;line-height:16px;height:16px;background-image:url(&quot;background-repeat:no-repeat;cursor:pointer;margin:6px 6px 6px 0px;background-position:0px -52px !important;"></a><a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="bds_tsina" data-cmd="tsina" title="分享到新浪微博" target="_blank" style="color:#FF9900;text-decoration-line:none;float:left;padding-left:17px;line-height:16px;height:16px;background-image:url(&quot;background-repeat:no-repeat;cursor:pointer;margin:6px 6px 6px 0px;background-position:0px -104px !important;"></a><a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="bds_tqq" data-cmd="tqq" title="分享到腾讯微博" target="_blank" style="color:#FF9900;text-decoration-line:none;float:left;padding-left:17px;line-height:16px;height:16px;background-image:url(&quot;background-repeat:no-repeat;cursor:pointer;margin:6px 6px 6px 0px;background-position:0px -260px !important;"></a><a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="bds_renren" data-cmd="renren" title="分享到人人网" target="_blank" style="color:#FF9900;text-decoration-line:none;float:left;padding-left:17px;line-height:16px;height:16px;background-image:url(&quot;background-repeat:no-repeat;cursor:pointer;margin:6px 6px 6px 0px;background-position:0px -208px !important;"></a><a href="http://blog.csdn.net/babyfish13/article/details/52981110#" class="bds_weixin" data-cmd="weixin" title="分享到微信" target="_blank" style="color:#FF9900;text-decoration-line:none;float:left;padding-left:17px;line-height:16px;height:16px;background-image:url(&quot;background-repeat:no-repeat;cursor:pointer;margin:6px 6px 6px 0px;background-position:0px -1612px !important;"></a>
</div>
<div id="digg" articleid="52981110" style="clear:both;width:182px;margin:0px auto;padding:30px 0px 15px;text-align:center;font-family:Arial, Console, Verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	<dl id="btnDigg" class="digg digg_disable" style="display:inline-block;float:left;width:72px;height:72px;overflow:hidden;margin:0px 2px;background:#FF7900;color:#FFFFFF;cursor:pointer;">
	</dl>
</div>