<p style="padding:5px;background-color:#F6F6F6;border:1px dotted #AAAAAA;white-space:pre-wrap;word-wrap:break-word;color:#3F3F3F;max-width:680px !important;">
	<br />
</p>
<pre class="prettyprint lang-js linenums" style="font-family:Arial, Helvetica, sans-serif;">systemctl list-unit-files --type=service #查看所有服务列表</pre>
<pre class="prettyprint lang-js linenums" style="font-family:Arial, Helvetica, sans-serif;"></pre>
<pre class="prettyprint lang-js linenums" style="font-family:Arial, Helvetica, sans-serif;">
<span style="font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">systemctl list-units --type=service #查看已经启动的服务</span> 
<pre class="prettyprint lang-js linenums">systemctl cat sshd.service #<span style="color:#3F3F3F;font-family:‘微软雅黑‘, &quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">看看一个服务包含哪些内容</span></pre>
自定义服务文件路径</pre>
<pre class="prettyprint lang-js linenums"><span style="font-family:'‘微软雅黑‘, font-size:14px;white-space:normal;background-color:#FFFFFF;">cd <span style="font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">/usr/lib/systemd/system/</span></span><span style="font-family:'Arial, Helvetica, sans-serif';"> </span></pre>
<pre class="prettyprint lang-js linenums"><span style="font-family:'Arial, Helvetica, sans-serif';"> </span></pre>
<pre class="prettyprint lang-js linenums"><span style="font-family:'Arial, Helvetica, sans-serif';"><span style="font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">systemctl enable nginx.service&nbsp;#设置服务开机启动</span></span></pre>
<pre class="prettyprint lang-js linenums"><span style="font-family:'Arial, Helvetica, sans-serif';"><span style="font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">systemctl <span style="color:#CC0000;font-family:arial;font-size:13px;white-space:normal;background-color:#FFFFFF;">disable</span> nginx.service&nbsp;</span>#设置不开机启动 </span></pre>
<pre class="prettyprint lang-js linenums">

<pre class="prettyprint lang-js linenums">systemctl is-enabled mysqld.service #查看是否开机启动</pre>
<br />
</pre>
<span style="font-family:'Arial, Helvetica, sans-serif';"> <br />
</span> 
<p>
	<br />
</p>