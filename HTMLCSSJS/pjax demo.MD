<p>
	<a target="_blank" href="https://github.com/defunkt/jquery-pjax">https://github.com/defunkt/jquery-pjax</a>！
</p>
<p>
	ajax缺点是破坏了浏览器的前进后退，因为ajax的请求不会留在历史记录中。pjax就不一样了，pjax被解释成ajax+pushState的封装，因为它把ajax的请求写入历史记录，并反映在地址栏，这样用户就能愉快地使用前进后退了。pjax有好几个实现方法，这里使用最常用的<a href="http://lib.csdn.net/base/jquery" class="replace_word" title="jQuery知识库" target="_blank" style="color:#df3434;font-weight:bold;">jQuery</a>库，使用jquery.pjax.js。演示代码的服务器端使用<a href="http://lib.csdn.net/base/php" class="replace_word" title="PHP知识库" target="_blank" style="color:#df3434;font-weight:bold;">PHP</a>脚本语言。
</p>
<p>
	Pjax用在那儿？就说百度云盘吧，这个大家肯定都用过。百度云盘PC端，在点击打开某个文件夹后会打开这个文件夹下的文件，其实显示文件的这个div就用到了pjax技术。地址栏变换，内容更换，但是却是一个ajax请求。等到后退的时候，不必重新请求上一层文件夹的内容，因为是存在在历史记录中的。而且，开发者还可以选择时候使用cache和storage缓存。
</p>
<p>
	DEMO1：
</p>
<p>
	客户端：
</p>
<p>
	<br />
</p>
<p>
	<br />
</p>
<p>
	<br />
</p>
<pre>

<pre class="prettyprint lang-html linenums">

<pre class="prettyprint lang-html linenums">&lt;!DOCTYPE html&gt; &lt;html&gt; &lt;head&gt; &lt;title&gt;pjax&lt;/title&gt; &lt;meta charset="utf-8"&gt; &lt;/head&gt; &lt;body&gt; &lt;h1&gt;My Site&lt;/h1&gt; &lt;div&gt; Go to &lt;a href="res1.php"&gt;第一页&lt;/a&gt;.&lt;a href="res2.php"&gt;第二页&lt;/a&gt; &lt;/div&gt; &lt;div id="container"&gt;&lt;/div&gt; &lt;/body&gt; &lt;script src="../jquery-2.1.4.min.js"&gt;&lt;/script&gt; &lt;script src="../jquery.pjax.js"&gt;&lt;/script&gt; &lt;script type="text/javascript"&gt; $(document).pjax('a', '#container') &lt;/script&gt; &lt;/html&gt;
 </pre>
<br />
</pre>
</pre>
<p>
	<br />
</p>
<p>
	<br />
</p>
<p>
	服务器端：
</p>
<p>
	res1.php
</p>
<div class="cnblogs_code">
<pre>&lt;?php <span style="color:#0000ff;">echo</span> "&lt;div style='background:red;'&gt;第一页&lt;/div&gt;";</pre>
</div>
<p>
	res2.php
</p>
<div class="cnblogs_code">
<pre>&lt;?php <span style="color:#0000ff;">echo</span> "&lt;div style='background:red;'&gt;第二页&lt;/div&gt;";</pre>
</div>
<p>
	解释：$(document).pjax('a', '#<a href="http://lib.csdn.net/base/docker" class="replace_word" title="Docker知识库" target="_blank" style="color:#df3434;font-weight:bold;">Container</a>')其中a是触发元素，#container是装载pjax返回内容的容器，下面也是这样。
</p>
<p>
	DEMO2：
</p>
<p>
	客户端：
</p>
<div class="cnblogs_code">
	<div class="cnblogs_code_toolbar">
		<br />
	</div>
<pre>
<pre class="prettyprint lang-html linenums">&lt;!DOCTYPE html&gt; &lt;html&gt; &lt;head&gt; &lt;title&gt;pjax&lt;/title&gt; &lt;meta charset="utf-8"&gt; &lt;/head&gt; &lt;body&gt; &lt;h1&gt;My Site&lt;/h1&gt; &lt;div&gt; &lt;input type="button" id="clickMe" value="GO"&gt; &lt;/div&gt; &lt;div id="container"&gt;&lt;/div&gt; &lt;/body&gt; &lt;script src="../jquery-2.1.4.min.js"&gt;&lt;/script&gt; &lt;script src="../jquery.pjax.js"&gt;&lt;/script&gt; &lt;script type="text/javascript"&gt; $(function(){
    $('#clickMe').click(function(){
        $.pjax({
            url: './res3.php',
            container: '#container' });
    });
}); &lt;/script&gt; &lt;/html&gt;</pre>
<br />
</pre>
	<div class="cnblogs_code_toolbar">
		<br />
	</div>
</div>
<p>
	服务器端代码：
</p>
<p>
	res3.php:
</p>
<div class="cnblogs_code">
<pre>&lt;?php <span style="color:#0000ff;">echo</span> "&lt;div style='background:red;'&gt;第三页&lt;/div&gt;";</pre>
</div>