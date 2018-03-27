<p style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-family:SimSun;font-size:18px;">session_set_save_handler&nbsp;<span style="white-space:pre;"> <span style="background-color:#F2F2F2;">设置用户自定义会话存储函数</span></span></span>
</p>
<p style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-family:SimSun;font-size:18px;"><span style="white-space:pre;background-color:#F2F2F2;">例如：</span></span>
</p>
<p style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-family:SimSun;font-size:18px;"><span style="white-space:pre;background-color:#F2F2F2;">如果想使用 <a href="http://lib.csdn.net/base/php" class="replace_word" title="PHP知识库" target="_blank" style="color:#DF3434;text-decoration-line:none;font-weight:bold;">PHP</a> 内置的会话存储机制之外的方式，
 可以使用本函数。 </span></span>
</p>
<p style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-family:SimSun;font-size:18px;"><span style="white-space:pre;background-color:#F2F2F2;">例如，可以自定义会话存储函数来将会话数据存储到<a href="http://lib.csdn.net/base/mysql" class="replace_word" title="MySQL知识库" target="_blank" style="color:#DF3434;text-decoration-line:none;font-weight:bold;">数据库</a>。两种使用方式：</span></span>
</p>
<p style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-family:SimSun;font-size:18px;"><span style="white-space:pre;background-color:#F2F2F2;">1.PHP5.4之前</span></span>
</p>
<p style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-family:SimSun;font-size:18px;"><span style="white-space:pre;background-color:#F2F2F2;"><span class="type" style="color:#669933;letter-spacing:-1px;word-spacing:-2px;">bool</span><span style="color:#737373;letter-spacing:-1px;word-spacing:-2px;">&nbsp;</span><span class="methodname" style="color:#737373;letter-spacing:-1px;word-spacing:-2px;"><span style="color:#336699;">session_set_save_handler</span></span><span style="color:#737373;letter-spacing:-1px;word-spacing:-2px;">&nbsp;(&nbsp;</span><span class="methodparam" style="color:#737373;letter-spacing:-1px;word-spacing:-2px;"><span class="type" style="color:#669933;"><a target="_blank" href="http://php.net/manual/zh/language.types.callable.php" class="type callable" style="color:#336699;text-decoration-line:none;border-bottom:1px solid;">callable</a></span>&nbsp;<code class="parameter" style="line-height:1.5rem;word-wrap:break-word;color:#336699;letter-spacing:-0.0625rem;word-spacing:-0.125rem;margin:0px;">$open</code></span><span style="color:#737373;letter-spacing:-1px;word-spacing:-2px;">&nbsp;,&nbsp;</span><span class="methodparam" style="color:#737373;letter-spacing:-1px;word-spacing:-2px;"><span class="type" style="color:#669933;"><a target="_blank" href="http://php.net/manual/zh/language.types.callable.php" class="type callable" style="color:#336699;text-decoration-line:none;border-bottom:1px solid;">callable</a></span>&nbsp;<code class="parameter" style="line-height:1.5rem;word-wrap:break-word;color:#336699;letter-spacing:-0.0625rem;word-spacing:-0.125rem;margin:0px;">$close</code></span><span style="color:#737373;letter-spacing:-1px;word-spacing:-2px;">&nbsp;,&nbsp;</span><span class="methodparam" style="color:#737373;letter-spacing:-1px;word-spacing:-2px;"><span class="type" style="color:#669933;"><a target="_blank" href="http://php.net/manual/zh/language.types.callable.php" class="type callable" style="color:#336699;text-decoration-line:none;border-bottom:1px solid;">callable</a></span>&nbsp;<code class="parameter" style="line-height:1.5rem;word-wrap:break-word;color:#336699;letter-spacing:-0.0625rem;word-spacing:-0.125rem;margin:0px;">$read</code></span><span style="color:#737373;letter-spacing:-1px;word-spacing:-2px;">&nbsp;,&nbsp;</span></span></span>
</p>
<p style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-family:SimSun;font-size:18px;"><span style="white-space:pre;background-color:#F2F2F2;"><span class="methodparam" style="color:#737373;letter-spacing:-1px;word-spacing:-2px;"><span class="type" style="color:#669933;"><a target="_blank" href="http://php.net/manual/zh/language.types.callable.php" class="type callable" style="color:#336699;text-decoration-line:none;border-bottom:1px solid;">callable</a></span>&nbsp;<code class="parameter" style="line-height:1.5rem;word-wrap:break-word;color:#336699;letter-spacing:-0.0625rem;word-spacing:-0.125rem;margin:0px;">$write</code></span><span style="color:#737373;letter-spacing:-1px;word-spacing:-2px;">&nbsp;,&nbsp;</span><span class="methodparam" style="color:#737373;letter-spacing:-1px;word-spacing:-2px;"><span class="type" style="color:#669933;"><a target="_blank" href="http://php.net/manual/zh/language.types.callable.php" class="type callable" style="color:#336699;text-decoration-line:none;border-bottom:1px solid;">callable</a></span>&nbsp;<code class="parameter" style="line-height:1.5rem;word-wrap:break-word;color:#336699;letter-spacing:-0.0625rem;word-spacing:-0.125rem;margin:0px;">$destroy</code></span><span style="color:#737373;letter-spacing:-1px;word-spacing:-2px;">,&nbsp;</span><span class="methodparam" style="color:#737373;letter-spacing:-1px;word-spacing:-2px;"><span class="type" style="color:#669933;"><a target="_blank" href="http://php.net/manual/zh/language.types.callable.php" class="type callable" style="color:#AE508D;text-decoration-line:none;border-bottom:1px solid #AE508D;outline:0px;border-top-color:#AE508D;border-right-color:#AE508D;border-left-color:#AE508D;">callable</a></span>&nbsp;<code class="parameter" style="line-height:1.5rem;word-wrap:break-word;color:#336699;letter-spacing:-0.0625rem;word-spacing:-0.125rem;margin:0px;">$gc</code></span><span style="color:#737373;letter-spacing:-1px;word-spacing:-2px;">&nbsp;[,&nbsp;</span><span class="methodparam" style="color:#737373;letter-spacing:-1px;word-spacing:-2px;"><span class="type" style="color:#669933;"><a target="_blank" href="http://php.net/manual/zh/language.types.callable.php" class="type callable" style="color:#336699;text-decoration-line:none;border-bottom:1px solid;">callable</a></span>&nbsp;<code class="parameter" style="line-height:1.5rem;word-wrap:break-word;color:#336699;letter-spacing:-0.0625rem;word-spacing:-0.125rem;margin:0px;">$create_sid</code></span><span style="color:#737373;letter-spacing:-1px;word-spacing:-2px;">&nbsp;]
 ) 2.PHP5.4之后</span></span></span>
</p>
<p style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-family:SimSun;font-size:18px;"><span style="white-space:pre;background-color:#F2F2F2;"><span style="color:#737373;letter-spacing:-1px;word-spacing:-2px;"><span class="type" style="color:#669933;">bool</span>&nbsp;<span class="methodname"><span style="color:#336699;">session_set_save_handler</span></span>&nbsp;(&nbsp;<span class="methodparam"><span class="type" style="color:#669933;"><a target="_blank" href="http://php.net/manual/zh/class.sessionhandlerinterface.php" class="type SessionHandlerInterface" style="color:#336699;text-decoration-line:none;border-bottom:1px solid;">SessionHandlerInterface</a></span>&nbsp;<code class="parameter" style="line-height:1.5rem;word-wrap:break-word;color:#336699;letter-spacing:-0.0625rem;word-spacing:-0.125rem;margin:0px;">$sessionhandler</code></span>&nbsp;[,&nbsp;<span class="methodparam"><span class="type" style="color:#669933;">bool</span>&nbsp;<code class="parameter" style="line-height:1.5rem;word-wrap:break-word;color:#336699;letter-spacing:-0.0625rem;word-spacing:-0.125rem;margin:0px;">$register_shutdown</code><span class="initializer" style="color:#993366;">&nbsp;=
 true</span></span>&nbsp;] )</span></span></span>
</p>
<p style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-family:SimSun;font-size:18px;color:#737373;"><span style="letter-spacing:-1px;white-space:pre;word-spacing:-2px;background-color:#F2F2F2;">详情，可查看<a href="http://lib.csdn.net/base/php" class="replace_word" title="PHP知识库" target="_blank" style="color:#DF3434;text-decoration-line:none;font-weight:bold;">php</a>手册：</span></span>
</p>
<p style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-family:SimSun;font-size:18px;color:#737373;"><span style="letter-spacing:-1px;white-space:pre;word-spacing:-2px;background-color:#F2F2F2;">http://php<a href="http://lib.csdn.net/base/dotnet" class="replace_word" title=".NET知识库" target="_blank" style="color:#DF3434;text-decoration-line:none;font-weight:bold;">.NET</a>/manual/zh/function.session-set-save-handler.php</span></span>
</p>
<p style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-family:SimSun;font-size:18px;color:#737373;">还是摘自手册中的内容：</span>
</p>
<p style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-family:SimSun;font-size:18px;color:#737373;"><span style="white-space:pre;"><span style="color:#0000BB;">$handler&nbsp;</span><span style="color:#007700;">=&nbsp;new&nbsp;</span><span style="color:#0000BB;">FileSessionHandler</span><span style="color:#007700;">();
// 我们自定义了一个session处理类，包含必须的几个方法<br />
</span></span></span><span style="font-family:SimSun;font-size:18px;color:#737373;"><span style="white-space:pre;"><span style="color:#0000BB;">session_set_save_handler</span><span style="color:#007700;">(<br />
&nbsp;&nbsp;&nbsp;&nbsp; array(</span><span style="color:#0000BB;">$handler</span><span style="color:#007700;">,&nbsp;</span><span style="color:#DD0000;">'open'</span><span style="color:#007700;">),<br />
&nbsp;&nbsp;&nbsp;&nbsp; array(</span><span style="color:#0000BB;">$handler</span><span style="color:#007700;">,&nbsp;</span><span style="color:#DD0000;">'close'</span><span style="color:#007700;">),<br />
&nbsp;&nbsp;&nbsp;&nbsp; array(</span><span style="color:#0000BB;">$handler</span><span style="color:#007700;">,&nbsp;</span><span style="color:#DD0000;">'read'</span><span style="color:#007700;">),<br />
&nbsp;&nbsp;&nbsp;&nbsp; array(</span><span style="color:#0000BB;">$handler</span><span style="color:#007700;">,&nbsp;</span><span style="color:#DD0000;">'write'</span><span style="color:#007700;">),<br />
&nbsp;&nbsp;&nbsp;&nbsp; array(</span><span style="color:#0000BB;">$handler</span><span style="color:#007700;">,&nbsp;</span><span style="color:#DD0000;">'destroy'</span><span style="color:#007700;">),<br />
&nbsp;&nbsp;&nbsp;&nbsp; array(</span><span style="color:#0000BB;">$handler</span><span style="color:#007700;">,&nbsp;</span><span style="color:#DD0000;">'gc'</span><span style="color:#007700;">)<br />
&nbsp;&nbsp;&nbsp;&nbsp;);<br />
<br />
</span><span style="color:#FF8000;">//&nbsp;下面这行代码可以防止使用对象作为会话保存管理器时可能引发的非预期行为<br />
</span><span style="color:#0000BB;">register_shutdown_function</span><span style="color:#007700;">(</span><span style="color:#DD0000;">'session_write_close'</span><span style="color:#007700;">);<br />
<br />
</span><span style="color:#0000BB;">session_start</span><span style="color:#007700;">();<br />
</span><span style="color:#FF8000;">//&nbsp;现在可以使用&nbsp;$_SESSION&nbsp;保存以及获取数据了</span></span></span>
</p>
<p style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-family:SimSun;font-size:18px;color:#737373;"><span style="white-space:pre;"><span style="color:#FF8000;">这里主要是想说：</span></span></span>
</p>
<p style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-family:SimSun;font-size:18px;color:#737373;"><span style="white-space:pre;"><span style="color:#FF8000;">使用session_set_save_handler()，得记得使用 '<span style="color:#0000BB;">register_shutdown_function<span style="color:#FF8000;">'，手册中是这样解释的：</span></span></span></span></span>
</p>
<p style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-family:SimSun;font-size:18px;color:#737373;"><span style="white-space:pre;"><span style="color:#FF8000;"><span style="color:#0000BB;"><span style="color:#FF8000;"><span style="color:#333333;font-family:&quot;font-size:16px;background-color:#F4DFDF;">在脚本执行完毕之后，PHP
 内部会清除对象， 所以有可能不调用&nbsp;</span><code class="parameter" style="font-weight:700;font-size:16px;line-height:1.375rem;font-family:&quot;word-wrap:break-word;color:#336699;background-color:#F4DFDF;">write</code><span style="color:#333333;font-family:&quot;font-size:16px;background-color:#F4DFDF;">&nbsp;和&nbsp;</span><code class="parameter" style="font-weight:700;font-size:16px;line-height:1.375rem;font-family:&quot;word-wrap:break-word;color:#336699;background-color:#F4DFDF;">close</code><span style="color:#333333;font-family:&quot;font-size:16px;background-color:#F4DFDF;">&nbsp;回调函数。
 这样可能会引发非预期</span></span></span></span></span></span>
</p>
<p style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-family:SimSun;font-size:18px;color:#737373;"><span style="white-space:pre;"><span style="color:#FF8000;"><span style="color:#0000BB;"><span style="color:#FF8000;"><span style="color:#333333;font-family:&quot;font-size:16px;background-color:#F4DFDF;">的行为，所以当使用对象作为会话保存管理器时，
 需要通过注册 shutdown 回调函数来规避风险。 通常，你可以通过</span></span></span></span></span></span>
</p>
<p style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-family:SimSun;font-size:18px;color:#737373;"><span style="white-space:pre;"><span style="color:#FF8000;"><span style="color:#0000BB;"><span style="color:#FF8000;"><span style="color:#333333;font-family:&quot;font-size:16px;background-color:#F4DFDF;">调用&nbsp;</span><span class="function" style="color:#333333;font-family:&quot;font-size:16px;background-color:#F4DFDF;"><a target="_blank" href="http://php.net/manual/zh/function.register-shutdown-function.php" class="function" style="color:#336699;text-decoration-line:none;border-bottom:1px solid;">register_shutdown_function()</a></span><span style="color:#333333;font-family:&quot;font-size:16px;background-color:#F4DFDF;">&nbsp;函数
 来注册&nbsp;</span><code class="parameter" style="font-weight:700;font-size:16px;line-height:1.375rem;font-family:&quot;word-wrap:break-word;color:#336699;background-color:#F4DFDF;">'session_write_close'</code><span style="color:#333333;font-family:&quot;font-size:16px;background-color:#F4DFDF;">&nbsp;回调函数。</span></span></span></span></span></span>
</p>
<p style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-family:SimSun;font-size:18px;color:#737373;"><span style="white-space:pre;"><span style="color:#FF8000;"><span style="color:#0000BB;"><span style="color:#FF8000;"><span style="color:#333333;font-family:&quot;font-size:16px;background-color:#F4DFDF;"><br />
</span></span></span></span></span></span>
</p>
<p style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-family:SimSun;font-size:18px;color:#FF0000;">接下来提到的非常关键的一点，是项目中真实出现的，而这个问题，我是真不知道，因为自定义的session机制，我没写过，都是进公司就是直接使用别人写好的，二次开发产品，肯定也是，所以，调试的过程中，很多应用问题，确实根本就没碰到过：</span>
</p>
<p style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-family:SimSun;font-size:18px;color:#FF0000;"><span style="white-space:pre;"></span>使用了自定义的session机制，php.ini 中的session.auto_start，必须设置为false。否则自定义的session机制失效，仍旧采用系统的！</span>
</p>
<div>
	<br />
</div>