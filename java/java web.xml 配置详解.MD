<p>
	&nbsp;<span style="white-space:pre;"> </span>在<a href="http://lib.csdn.net/base/javaee" class="replace_word" title="Java EE知识库" target="_blank" style="color:#df3434;font-weight:bold;">Java</a>工程中，web.xml用来初始化工程配置信息，比如说welcome页面，filter，listener，servlet，servlet-mapping，启动加载级别等等。
</p>
<p>
	&nbsp; &nbsp;每
一个xml文件都有定义他书写规范的schema文件，web.xml所对应的xml 
Schema文件中定义了多少种标签元素，web.xml中就可以出现它所定义的标签元素，也就具备哪些特定的功能。web.xml的模式文件是由Sun
 公司定义的，每个web.xml文件的根元素为&lt;web-app&gt;中，必须标明这个web.xml使用的是哪个模式文件。
</p>
<p>
	&nbsp; &nbsp;web.xml的根元素定义如下所示:
</p>
<div class="dp-highlighter bg_html">
	<div class="bar">
		<div class="tools">
			<b>[html]</b> <a href="http://blog.csdn.net/m751075306/article/details/9452893#" class="ViewSource" title="view plain">view plain</a><span data-mod="popu_168"> <a href="http://blog.csdn.net/m751075306/article/details/9452893#" class="CopyToClipboard" title="copy">copy</a>
			<div style="position:absolute;left:420px;top:721px;width:18px;height:18px;z-index:99;">
			</div>
</span><span data-mod="popu_169"> </span>
		</div>
	</div>
	<ol class="dp-xml" start="1">
		<li class="alt">
			<span class="tag">&lt;?</span><span class="tag-name">xml</span>&nbsp;<span class="attribute">version</span>=<span class="attribute-value">"1.0"</span>&nbsp;<span class="attribute">encoding</span>=<span class="attribute-value">"UTF-8"</span><span class="tag">?&gt;</span>&nbsp;&nbsp;
		</li>
		<li class="">
			<span class="tag">&lt;</span><span class="tag-name">web-app</span>&nbsp;<span class="attribute">version</span>=<span class="attribute-value">"2.5"</span>&nbsp;&nbsp;&nbsp;
		</li>
		<li class="alt">
			<span class="attribute">xmlns</span>=<span class="attribute-value">"http://java.sun.com/xml/ns/javaee"</span>&nbsp;&nbsp;
		</li>
		<li class="">
			<span class="attribute">xmlns:xsi</span>=<span class="attribute-value">"http://www.w3.org/2001/XMLSchema-instance"</span>&nbsp;&nbsp;&nbsp;
		</li>
		<li class="alt">
			<span class="attribute">xsi:schemaLocation</span>="http://java.sun.com/xml/ns/javaee&nbsp;&nbsp;&nbsp;
		</li>
		<li class="">
			http://java.sun.com/xml/ns/javaee/web-app_2_5.xsd"<span class="tag">&gt;</span>&nbsp;&nbsp;
		</li>
		<li class="alt">
			<span class="tag">&lt;/</span><span class="tag-name">web-app</span><span class="tag">&gt;</span>&nbsp;&nbsp;
		</li>
	</ol>
</div>
<br />
&nbsp; &nbsp; 下面就来介绍一下web.xml中常用的标签及其功能
<h2>
	<a name="t0"></a>1.&lt;description&gt;,&lt;display-name&gt;,&lt;icon&gt;
</h2>
<p>
	<span style="white-space:pre;"><span style="font-family:FangSong_GB2312;font-size:18px;">&lt;description&gt;项目描述&lt;/discription&gt; &nbsp;对项目做出描述.</span></span>
</p>
<p>
	<span style="white-space:pre;"><span style="font-family:FangSong_GB2312;font-size:18px;">&lt;display-name&gt;项目名称&lt;/display-name&gt; 定义项目的名称.</span></span>
</p>
<p>
	<span style="white-space:pre;"></span>&nbsp; &nbsp; &lt;icon&gt; icon元素包含small-icon和large-icon两个子元素.用来指定web站台中小图标和大图标的路径.
</p>
<p>
	<span style="white-space:pre;"></span>&nbsp;
 &nbsp; &nbsp; &nbsp; 
&lt;small-icon&gt;/路径/smallicon.gif&lt;/small-icon&gt;small-icon元素应指向web
站台中某个小图标的路径,大小为16 X 16 pixel,但是图象文件必须为GIF或JPEG格式,扩展名必须为:.gif或 .jpg.
</p>
<p>
	<span style="white-space:pre;"></span>&nbsp;
 &nbsp; &nbsp; &nbsp; &lt;large-icon&gt;/路径/largeicon-jpg&lt;/large-icon&gt; 
large-icon元素应指向web站台中某个大图表路径,大小为32 X 32 
pixel,但是图象文件必须为GIF或JPEG的格式,扩展名必须为; gif 或jpg.
</p>
<p>
	&nbsp; &nbsp; 例如：
</p>
<div>
	<div class="dp-highlighter bg_html">
		<div class="bar">
			<div class="tools">
				<b>[html]</b> <a href="http://blog.csdn.net/m751075306/article/details/9452893#" class="ViewSource" title="view plain">view plain</a><span data-mod="popu_168"> <a href="http://blog.csdn.net/m751075306/article/details/9452893#" class="CopyToClipboard" title="copy">copy</a>
				<div style="position:absolute;left:420px;top:1201px;width:18px;height:18px;z-index:99;">
				</div>
</span><span data-mod="popu_169"> </span>
			</div>
		</div>
		<ol class="dp-xml" start="1">
			<li class="alt">
				<span class="tag">&lt;</span><span class="tag-name">display-name</span><span class="tag">&gt;</span>Develop&nbsp;Example<span class="tag">&lt;/</span><span class="tag-name">display-name</span><span class="tag">&gt;</span>&nbsp;&nbsp;&nbsp;&nbsp;
			</li>
			<li class="">
				<span class="tag">&lt;</span><span class="tag-name">description</span><span class="tag">&gt;</span>JSP&nbsp;2.0&nbsp;Tech&nbsp;Book's&nbsp;Examples<span class="tag">&lt;/</span><span class="tag-name">description</span><span class="tag">&gt;</span>&nbsp;&nbsp;&nbsp;
			</li>
			<li class="alt">
				&nbsp;<span class="tag">&lt;</span><span class="tag-name">icon</span><span class="tag">&gt;</span>&nbsp;&nbsp;&nbsp;&nbsp;
			</li>
			<li class="">
				&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">small-icon</span><span class="tag">&gt;</span>/images/small.gif<span class="tag">&lt;/</span><span class="tag-name">small-icon</span><span class="tag">&gt;</span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
			</li>
			<li class="alt">
				&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">large-icon</span><span class="tag">&gt;</span>/images/large.gir<span class="tag">&lt;/</span><span class="tag-name">large-icon</span><span class="tag">&gt;</span>&nbsp;&nbsp;&nbsp;
			</li>
			<li class="">
				&nbsp;<span class="tag">&lt;/</span><span class="tag-name">icon</span><span class="tag">&gt;</span>&nbsp;&nbsp;
			</li>
		</ol>
	</div>
	<div style="font-family:simsun;font-size:14px;">
		<span style="white-space:pre;"><br />
</span>
	</div>
	<div>
		<h2 style="font-family:simsun;font-size:14px;">
			<a name="t1"></a><span style="white-space:pre;">2.&lt;context-param&gt;</span>
		</h2>
		<div>
			&nbsp; &nbsp; &lt;context-param&gt;元素含有一对参数名和参数值，用作应用的servlet上下文初始化参数。参数名在整个Web应用中必须是惟一的。<br />
&nbsp; &nbsp; context-param 元素用来设定web应用的环境参数(context),它包含两个子元素: param-name和param-value. <br />
&nbsp; &nbsp; &nbsp; &nbsp; &lt;param-name&gt;参数名称&lt;/param-name&gt; 设定Context名称 <br />
&nbsp; &nbsp; &nbsp; &nbsp; &lt;param-value&gt;值&lt;/param-value&gt; 设定Context名称的值 &lt;/context-param&gt; <br />
&nbsp; &nbsp; 例如：<br />
		</div>
		<div>
			<span style="white-space:pre;"><span style="font-family:FangSong_GB2312;font-size:18px;"></span></span>
			<div class="dp-highlighter bg_html">
				<div class="bar">
					<div class="tools">
						<b>[html]</b> <a href="http://blog.csdn.net/m751075306/article/details/9452893#" class="ViewSource" title="view plain">view plain</a><span data-mod="popu_168"> <a href="http://blog.csdn.net/m751075306/article/details/9452893#" class="CopyToClipboard" title="copy">copy</a>
						<div style="position:absolute;left:420px;top:1586px;width:18px;height:18px;z-index:99;">
						</div>
</span><span data-mod="popu_169"> </span>
					</div>
				</div>
				<ol class="dp-xml" start="1">
					<li class="alt">
						<span class="tag">&lt;</span><span class="tag-name">context-param</span><span class="tag">&gt;</span>&nbsp;&nbsp;
					</li>
					<li class="">
						&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">param-name</span><span class="tag">&gt;</span>param_name<span class="tag">&lt;/</span><span class="tag-name">param-name</span><span class="tag">&gt;</span>&nbsp;&nbsp;
					</li>
					<li class="alt">
						&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">param-value</span><span class="tag">&gt;</span>param_value<span class="tag">&lt;/</span><span class="tag-name">param-value</span><span class="tag">&gt;</span>&nbsp;&nbsp;
					</li>
					<li class="">
						<span class="tag">&lt;/</span><span class="tag-name">context-param</span><span class="tag">&gt;</span>&nbsp;&nbsp;
					</li>
				</ol>
			</div>
&nbsp; &nbsp; 此所设定的参数,在JSP网页中可以使用下列方法来取得:${initParam.param_name}<br />
&nbsp; &nbsp; 若在Servlet可以使用下列方法来获得:<br />
&nbsp; &nbsp; &nbsp; &nbsp; String param_name=getServletContext().getInitParamter("param_name");<br />
		</div>
		<h2>
			<a name="t2"></a><span style="white-space:pre;"><span style="font-size:14px;">3.</span></span><span style="font-size:14px;white-space:pre;font-family:SimSun;">&lt;filter&gt;</span>
		</h2>
	</div>
	<div>
		<p>
			<span style="white-space:pre;"><span style="font-family:FangSong_GB2312;font-size:18px;">filter元素用于指定Web容器中的过滤器。<br />
</span></span>
		</p>
		<p>
			<span style="white-space:pre;"><span style="font-family:FangSong_GB2312;font-size:18px;">在请求和响应对象被servlet处理之前或之后，可以使用过滤器对这两个对象进行操作。</span></span>
		</p>
		<p>
			<span style="white-space:pre;"><span style="font-family:FangSong_GB2312;font-size:18px;">利用下一节介绍 的filter-mapping元素，过滤器被映射到一个servlet或一个URL模式。</span></span>
		</p>
		<p>
			<span style="white-space:pre;"><span style="font-family:FangSong_GB2312;font-size:18px;">这个过滤器的filter元素和filter-mapping 元素必须具有相同的名称。</span></span>
		</p>
&nbsp; &nbsp; 
filter元素用来声明filter的相关设定.filter元素除了下面介绍的的子元素之外,还包括之前介绍过
的&lt;icon&gt;,&lt;display-name&gt;,&lt;description&gt;,&lt;init-
param&gt;,其用途一样.
	</div>
	<div>
		&nbsp; &nbsp; 下面介绍filter-name，filter-class和init-param元素<br />
&nbsp; &nbsp; &nbsp; &nbsp; init-param元素与context-param 元素具有相同的元素描述符。
	</div>
	<div>
		&nbsp; &nbsp; &nbsp; &nbsp; filter-name元素用来定义过滤器的名称，该名称在整个应用中都必须是惟一的。
	</div>
	<div>
		&nbsp; &nbsp; &nbsp; &nbsp; filter-class元素指定过滤 器类的完全限定的名称。<br />
	</div>
	<p>
		<br />
	</p>
&nbsp; &nbsp; &lt;filter-name&gt;Filter的名称&lt;/filter-name&gt; 定义Filter的名称.<br />
&nbsp; &nbsp; &lt;filter-class&gt;Filter的类名称&lt;/filter-class&gt;&nbsp;定义Filter的类名称.例如:com.foo.hello
</div>
<div>
	&nbsp; &nbsp; 例如：
</div>
<div>
	<div class="dp-highlighter bg_html">
		<div class="bar">
			<div class="tools">
				<b>[html]</b> <a href="http://blog.csdn.net/m751075306/article/details/9452893#" class="ViewSource" title="view plain">view plain</a><span data-mod="popu_168"> <a href="http://blog.csdn.net/m751075306/article/details/9452893#" class="CopyToClipboard" title="copy">copy</a>
				<div style="position:absolute;left:420px;top:2195px;width:18px;height:18px;z-index:99;">
				</div>
</span><span data-mod="popu_169"> </span>
			</div>
		</div>
		<ol class="dp-xml" start="1">
			<li class="alt">
				<span class="tag">&lt;</span><span class="tag-name">filter</span><span class="tag">&gt;</span>&nbsp;&nbsp;
			</li>
			<li class="">
				&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">filter-name</span><span class="tag">&gt;</span>setCharacterEncoding<span class="tag">&lt;/</span><span class="tag-name">filter-name</span><span class="tag">&gt;</span>&nbsp;&nbsp;
			</li>
			<li class="alt">
				&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">filter-class</span><span class="tag">&gt;</span>coreservlet.javaworld.CH11.SetCharacterEncodingFilter<span class="tag">&lt;/</span><span class="tag-name">filter-class</span><span class="tag">&gt;</span>&nbsp;&nbsp;
			</li>
			<li class="">
				&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">init-param</span><span class="tag">&gt;</span>&nbsp;&nbsp;
			</li>
			<li class="alt">
				&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">param-name</span><span class="tag">&gt;</span>encoding<span class="tag">&lt;/</span><span class="tag-name">param-name</span><span class="tag">&gt;</span>&nbsp;&nbsp;
			</li>
			<li class="">
				&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">param-value</span><span class="tag">&gt;</span>GB2312<span class="tag">&lt;/</span><span class="tag-name">param-value</span><span class="tag">&gt;</span>&nbsp;&nbsp;
			</li>
			<li class="alt">
				&nbsp;&nbsp;<span class="tag">&lt;/</span><span class="tag-name">init-param</span><span class="tag">&gt;</span>&nbsp;&nbsp;
			</li>
			<li class="">
				<span class="tag">&lt;/</span><span class="tag-name">filter</span><span class="tag">&gt;</span>&nbsp;&nbsp;
			</li>
		</ol>
	</div>
	<h2>
		<a name="t3"></a>
	</h2>
	<h2>
		<a name="t4"></a>
	</h2>
	<h2>
		<a name="t5"></a><span style="white-space:pre;"><span style="font-size:14px;">4.</span></span><span style="white-space:pre;"><span style="font-family:SimSun;font-size:14px;">&lt;filter-mapping&gt;</span></span>
	</h2>
	<p>
		&nbsp;
 &nbsp; filter-mapping元素用来声明Web应用中的过滤器映射。过滤器可被映射到一个servlet或一个URL模式。将过滤器映射到一个 
servlet中会造成过滤器作用于servlet上。将过滤器映射到一个URL模式中则可以将过滤器应用于任何资源，只要该资源的URL与URL模式匹
配。过滤是按照部署描述符的filter-mapping元素出现的顺序执行的。
	</p>
	<p>
		&nbsp; &nbsp; filter-mapping 元素的两个主要子元素filter-name和url-pattern.用来定义Filter所对应的URL。还有<span style="white-space:pre;">servlet-name和dispatcher子元素，不是很常用。</span>
	</p>
	<p>
		&nbsp; &nbsp; &nbsp; &nbsp; &lt;filter-name&gt;Filter的名称&lt;/filter-name&gt; &nbsp;定义Filter的名称.
	</p>
	<p>
		&nbsp; &nbsp; &nbsp; &nbsp; &lt;url-pattern&gt;URL&lt;/url-pattern&gt; Filter所对应的RUL.例如:&lt;url-pattern&gt;/Filter/Hello&lt;/url-pattern&gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &lt;servlet-name&gt;Servlet的名称&lt;servlet-name&gt; 定义servlet的名称.<br />
&nbsp; &nbsp; &nbsp; &nbsp; 
&lt;dispatcher&gt;REQUEST|INCLUDE|FORWARD|ERROR&lt;/disaptcher&gt; 
设定Filter对应的请求方式,有RQUEST,INCLUDE,FORWAR,ERROR四种,默认为REQUEST.
	</p>
	<p>
		例如：
	</p>
	<div class="dp-highlighter bg_html">
		<div class="bar">
			<div class="tools">
				<b>[html]</b> <a href="http://blog.csdn.net/m751075306/article/details/9452893#" class="ViewSource" title="view plain">view plain</a><span data-mod="popu_168"> <a href="http://blog.csdn.net/m751075306/article/details/9452893#" class="CopyToClipboard" title="copy">copy</a>
				<div style="position:absolute;left:420px;top:2720px;width:18px;height:18px;z-index:99;">
				</div>
</span><span data-mod="popu_169"> </span>
			</div>
		</div>
		<ol class="dp-xml" start="1">
			<li class="alt">
				<span class="tag">&lt;</span><span class="tag-name">filter-mapping</span><span class="tag">&gt;</span>&nbsp;&nbsp;
			</li>
			<li class="">
				&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">filter-name</span><span class="tag">&gt;</span>GZIPEncoding<span class="tag">&lt;/</span><span class="tag-name">filter-name</span><span class="tag">&gt;</span>&nbsp;&nbsp;
			</li>
			<li class="alt">
				&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">url-pattern</span><span class="tag">&gt;</span>/*<span class="tag">&lt;/</span><span class="tag-name">url-pattern</span><span class="tag">&gt;</span>&nbsp;&nbsp;
			</li>
			<li class="">
				<span class="tag">&lt;/</span><span class="tag-name">filter-mapping</span><span class="tag">&gt;</span>&nbsp;&nbsp;
			</li>
		</ol>
	</div>
	<p>
		完整的filter配置例子如下：
	</p>
	<div class="dp-highlighter bg_html">
		<div class="bar">
			<div class="tools">
				<b>[html]</b> <a href="http://blog.csdn.net/m751075306/article/details/9452893#" class="ViewSource" title="view plain">view plain</a><span data-mod="popu_168"> <a href="http://blog.csdn.net/m751075306/article/details/9452893#" class="CopyToClipboard" title="copy">copy</a>
				<div style="position:absolute;left:420px;top:2887px;width:18px;height:18px;z-index:99;">
				</div>
</span><span data-mod="popu_169"> </span>
			</div>
		</div>
		<ol class="dp-xml" start="1">
			<li class="alt">
				<span class="tag">&lt;</span><span class="tag-name">filter</span><span class="tag">&gt;</span>&nbsp;&nbsp;
			</li>
			<li class="">
				&nbsp;&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">filter-name</span><span class="tag">&gt;</span>struts2<span class="tag">&lt;/</span><span class="tag-name">filter-name</span><span class="tag">&gt;</span>&nbsp;&nbsp;
			</li>
			<li class="alt">
				&nbsp;&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">filter-class</span><span class="tag">&gt;</span>org.apache.struts2.dispatcher.ng.filter.StrutsPrepareAndExecuteFilter<span class="tag">&lt;/</span><span class="tag-name">filter-class</span><span class="tag">&gt;</span>&nbsp;&nbsp;
			</li>
			<li class="">
				<span class="tag">&lt;/</span><span class="tag-name">filter</span><span class="tag">&gt;</span>&nbsp;&nbsp;
			</li>
			<li class="alt">
				<span class="tag">&lt;</span><span class="tag-name">filter-mapping</span><span class="tag">&gt;</span>&nbsp;&nbsp;
			</li>
			<li class="">
				&nbsp;&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">filter-name</span><span class="tag">&gt;</span>struts2<span class="tag">&lt;/</span><span class="tag-name">filter-name</span><span class="tag">&gt;</span>&nbsp;&nbsp;
			</li>
			<li class="alt">
				&nbsp;&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">url-pattern</span><span class="tag">&gt;</span>/*<span class="tag">&lt;/</span><span class="tag-name">url-pattern</span><span class="tag">&gt;</span>&nbsp;&nbsp;
			</li>
			<li class="">
				<span class="tag">&lt;/</span><span class="tag-name">filter-mapping</span><span class="tag">&gt;</span>&nbsp;&nbsp;
			</li>
		</ol>
	</div>
<br />
	<h2>
		<a name="t6"></a><span style="white-space:pre;"><span style="font-size:14px;">5.</span></span><span style="white-space:pre;"><span style="font-family:SimSun;font-size:14px;">&lt;servlet&gt;</span></span>
	</h2>
	<p>
		&nbsp; &nbsp;在web.xml中完成的一个最常见的任务是对servlet或JSP页面给出名称和定制的URL。用servlet元素分配名称，使用servlet-mapping元素将定制的URL与刚分配的名称相关联。
	</p>
	<div>
		例如：
	</div>
	<div>
		<div class="dp-highlighter bg_html">
			<div class="bar">
				<div class="tools">
					<b>[html]</b> <a href="http://blog.csdn.net/m751075306/article/details/9452893#" class="ViewSource" title="view plain">view plain</a><span data-mod="popu_168"> <a href="http://blog.csdn.net/m751075306/article/details/9452893#" class="CopyToClipboard" title="copy">copy</a>
					<div style="position:absolute;left:420px;top:3230px;width:18px;height:18px;z-index:99;">
					</div>
</span><span data-mod="popu_169"> </span>
				</div>
			</div>
			<ol class="dp-xml" start="1">
				<li class="alt">
					<span class="tag">&lt;</span><span class="tag-name">servlet</span><span class="tag">&gt;</span>&nbsp;&nbsp;&nbsp;
				</li>
				<li class="">
					&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">servlet-name</span><span class="tag">&gt;</span>Test<span class="tag">&lt;/</span><span class="tag-name">servlet-name</span><span class="tag">&gt;</span>&nbsp;&nbsp;&nbsp;
				</li>
				<li class="alt">
					&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">servlet-class</span><span class="tag">&gt;</span>com.moreservlets.TestServlet<span class="tag">&lt;/</span><span class="tag-name">servlet-class</span><span class="tag">&gt;</span>&nbsp;&nbsp;&nbsp;
				</li>
				<li class="">
					<span class="tag">&lt;/</span><span class="tag-name">servlet</span><span class="tag">&gt;</span>&nbsp;&nbsp;&nbsp;
				</li>
			</ol>
		</div>
&nbsp; &nbsp; 这表示位于WEB-INF/classes/com/moreservlets/TestServlet的servlet已经得到了注册名Test。
	</div>
	<div>
		<h2 style="font-family:FangSong_GB2312;white-space:pre;">
			<a name="t7"></a><span style="font-family:SimSun;"><span style="font-size:14px;">6.</span></span><span style="font-family:SimSun;font-size:14px;">&lt;servlet-mapping&gt;</span>
		</h2>
		<div>
			&nbsp; &nbsp; servlet-mapping元素包含两个子元素servlet-name和url-pattern.用来定义servlet所对应URL.<br />
		</div>
&nbsp; &nbsp; &nbsp; &nbsp; &lt;servlet-name&gt;Servlet的名称&lt;/servlet-name&gt; 定义Servlet的名称.<br />
&nbsp; &nbsp; &nbsp; &nbsp; &lt;url-pattern&gt;Servlet URL&lt;/url-pattern&gt; 
定义Servlet所对应的RUL.例如:&lt;url-pattern&gt;/Servlet/Hello&lt;/url-
pattern&gt;
	</div>
	<div>
		例如：
	</div>
	<div>
		<div class="dp-highlighter bg_html">
			<div class="bar">
				<div class="tools">
					<b>[html]</b> <a href="http://blog.csdn.net/m751075306/article/details/9452893#" class="ViewSource" title="view plain">view plain</a><span data-mod="popu_168"> <a href="http://blog.csdn.net/m751075306/article/details/9452893#" class="CopyToClipboard" title="copy">copy</a>
					<div style="position:absolute;left:420px;top:3553px;width:18px;height:18px;z-index:99;">
					</div>
</span><span data-mod="popu_169"> </span>
				</div>
			</div>
			<ol class="dp-xml" start="1">
				<li class="alt">
					<span class="tag">&lt;</span><span class="tag-name">servlet-mapping</span><span class="tag">&gt;</span>&nbsp;&nbsp;
				</li>
				<li class="">
					&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">servlet-name</span><span class="tag">&gt;</span>LoginChecker<span class="tag">&lt;/</span><span class="tag-name">servlet-name</span><span class="tag">&gt;</span>&nbsp;&nbsp;
				</li>
				<li class="alt">
					&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">url-pattern</span><span class="tag">&gt;</span>/LoginChecker<span class="tag">&lt;/</span><span class="tag-name">url-pattern</span><span class="tag">&gt;</span>&nbsp;&nbsp;
				</li>
				<li class="">
					<span class="tag">&lt;/</span><span class="tag-name">servlet-mapping</span><span class="tag">&gt;</span>&nbsp;&nbsp;
				</li>
			</ol>
		</div>
完整的servlet配置如下所示：
	</div>
	<div>
		<div class="dp-highlighter bg_html">
			<div class="bar">
				<div class="tools">
					<b>[html]</b> <a href="http://blog.csdn.net/m751075306/article/details/9452893#" class="ViewSource" title="view plain">view plain</a><span data-mod="popu_168"> <a href="http://blog.csdn.net/m751075306/article/details/9452893#" class="CopyToClipboard" title="copy">copy</a>
					<div style="position:absolute;left:420px;top:3720px;width:18px;height:18px;z-index:99;">
					</div>
</span><span data-mod="popu_169"> </span>
				</div>
			</div>
			<ol class="dp-xml" start="1">
				<li class="alt">
					<span class="tag">&lt;</span><span class="tag-name">servlet</span><span class="tag">&gt;</span>&nbsp;&nbsp;
				</li>
				<li class="">
					&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">servlet-name</span><span class="tag">&gt;</span>ServletName<span class="tag">&lt;/</span><span class="tag-name">servlet-name</span><span class="tag">&gt;</span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
				</li>
				<li class="alt">
					&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">servlet-class</span><span class="tag">&gt;</span>xxxpackage.xxxServlet<span class="tag">&lt;/</span><span class="tag-name">servlet-class</span><span class="tag">&gt;</span>&nbsp;&nbsp;&nbsp;<span class="comments">&lt;!--Servlet的类--&gt;</span>&nbsp;&nbsp;
				</li>
				<li class="">
					&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">init-param</span><span class="tag">&gt;</span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="comments">&lt;!--初始化一个变量，可看成全局变量，可省略--&gt;</span>&nbsp;&nbsp;
				</li>
				<li class="alt">
					&nbsp;&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">param-name</span><span class="tag">&gt;</span>参数名称<span class="tag">&lt;/</span><span class="tag-name">param-name</span><span class="tag">&gt;</span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="comments">&lt;!--变量名称--&gt;</span>&nbsp;&nbsp;
				</li>
				<li class="">
					&nbsp;&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">param-value</span><span class="tag">&gt;</span>参数值<span class="tag">&lt;/</span><span class="tag-name">param-value</span><span class="tag">&gt;</span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="comments">&lt;!--变量值--&gt;</span>&nbsp;&nbsp;
				</li>
				<li class="alt">
					&nbsp;&nbsp;<span class="tag">&lt;/</span><span class="tag-name">init-param</span><span class="tag">&gt;</span>&nbsp;&nbsp;
				</li>
				<li class="">
					<span class="tag">&lt;/</span><span class="tag-name">servlet</span><span class="tag">&gt;</span>&nbsp;&nbsp;
				</li>
				<li class="alt">
					<span class="tag">&lt;</span><span class="tag-name">servlet-mapping</span><span class="tag">&gt;</span>&nbsp;&nbsp;
				</li>
				<li class="">
					&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">servlet-name</span><span class="tag">&gt;</span>ServletName<span class="tag">&lt;/</span><span class="tag-name">servlet-name</span><span class="tag">&gt;</span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
				</li>
				<li class="alt">
					&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">url-pattern</span><span class="tag">&gt;</span>/aaa/xxx<span class="tag">&lt;/</span><span class="tag-name">url-pattern</span><span class="tag">&gt;</span>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="comments">&lt;!--映射的url路径&nbsp;--&gt;</span>&nbsp;&nbsp;
				</li>
				<li class="">
					<span class="tag">&lt;/</span><span class="tag-name">servlet-mapping</span><span class="tag">&gt;</span>&nbsp;&nbsp;
				</li>
			</ol>
		</div>
&nbsp; &nbsp; 在地址栏中输入http://localhost:8080/web-App/aaa/xxx就可以访问了。
	</div>
	<div>
		<h2 style="font-family:FangSong_GB2312;white-space:pre;">
			<a name="t8"></a><span style="font-family:SimSun;"><span style="font-size:14px;">7.</span></span><span style="font-family:SimSun;font-size:14px;">&lt;<strong>listener</strong>&gt;</span>
		</h2>
		<div>
			&nbsp; &nbsp; listener元素用来注册一个监听器类，可以在Web应用中包含该类。使用listener元素，可以收到事件什么时候发生以及用什么作为响应的通知。<br />
		</div>
		<div>
			&nbsp; &nbsp; listener元素用来定义Listener接口,它的主要子元素为&lt;listener-class&gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &lt;listen-class&gt;Listener的类名称&lt;/listener-class&gt; 定义Listener的类名称.例如: com.foo.hello<br />
&nbsp; &nbsp; 例如：
		</div>
		<div>
			<div class="dp-highlighter bg_html">
				<div class="bar">
					<div class="tools">
						<b>[html]</b> <a href="http://blog.csdn.net/m751075306/article/details/9452893#" class="ViewSource" title="view plain">view plain</a><span data-mod="popu_168"> <a href="http://blog.csdn.net/m751075306/article/details/9452893#" class="CopyToClipboard" title="copy">copy</a>
						<div style="position:absolute;left:420px;top:4187px;width:18px;height:18px;z-index:99;">
						</div>
</span><span data-mod="popu_169"> </span>
					</div>
				</div>
				<ol class="dp-xml" start="1">
					<li class="alt">
						<span class="tag">&lt;</span><span class="tag-name">listener</span><span class="tag">&gt;</span>&nbsp;&nbsp;
					</li>
					<li class="">
						&nbsp;&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">listener-class</span><span class="tag">&gt;</span><span class="tag">&lt;</span><span class="tag-name">span</span>&nbsp;<span class="attribute">style</span>=<span class="attribute-value">"font-family:&nbsp;FangSong_GB2312;font-size:18px;&nbsp;white-space:&nbsp;pre;"</span><span class="tag">&gt;</span>com.foo.hello<span class="tag">&lt;/</span><span class="tag-name">span</span><span class="tag">&gt;</span><span class="tag">&lt;/</span><span class="tag-name">listener-class</span><span class="tag">&gt;</span>&nbsp;&nbsp;
					</li>
					<li class="alt">
						<span class="tag">&lt;/</span><span class="tag-name">listener</span><span class="tag">&gt;</span>&nbsp;&nbsp;
					</li>
				</ol>
			</div>
			<h2 style="font-family:FangSong_GB2312;white-space:pre;">
				<a name="t9"></a><span style="font-family:SimSun;"><span style="font-size:14px;">8.</span></span><span style="font-family:SimSun;font-size:14px;">&lt;<strong>session-cofing</strong>&gt;</span>
			</h2>
			<div>
				&nbsp; &nbsp; session-config包含一个子元素session-timeout.定义web应用中的session参数.<br />
&nbsp; &nbsp; &nbsp; &nbsp; &lt;session-timeout&gt;分钟&lt;/session-timeout&gt; 定义这个web应用所有session的有效期限.单位为分钟.<br />
			</div>
			<div>
				&nbsp; &nbsp; 例如：
			</div>
			<div>
				<div class="dp-highlighter bg_html">
					<div class="bar">
						<div class="tools">
							<b>[html]</b> <a href="http://blog.csdn.net/m751075306/article/details/9452893#" class="ViewSource" title="view plain">view plain</a><span data-mod="popu_168"> <a href="http://blog.csdn.net/m751075306/article/details/9452893#" class="CopyToClipboard" title="copy">copy</a>
							<div style="position:absolute;left:420px;top:4432px;width:18px;height:18px;z-index:99;">
							</div>
</span><span data-mod="popu_169"> </span>
						</div>
					</div>
					<ol class="dp-xml" start="1">
						<li class="alt">
							<span class="tag">&lt;</span><span class="tag-name">session-config</span><span class="tag">&gt;</span>&nbsp;&nbsp;
						</li>
						<li class="">
							&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">session-timeout</span><span class="tag">&gt;</span>20<span class="tag">&lt;/</span><span class="tag-name">session-timeout</span><span class="tag">&gt;</span>&nbsp;&nbsp;
						</li>
						<li class="alt">
							<span class="tag">&lt;/</span><span class="tag-name">session-config</span><span class="tag">&gt;</span>&nbsp;&nbsp;
						</li>
					</ol>
				</div>
				<h2 style="font-family:FangSong_GB2312;white-space:pre;">
					<a name="t10"></a><span style="font-family:SimSun;"><span style="font-size:14px;">9.</span></span><span style="font-family:SimSun;font-size:14px;">&lt;<strong>mime-mapping</strong>&gt;</span>
				</h2>
				<div>
					&nbsp; &nbsp; mime-mapping包含两个子元素extension和mime-type.定义某一个扩展名和某一MIME Type做对映.<br />
				</div>
				<div>
					&nbsp; &nbsp; &nbsp; &nbsp; &lt;extension&gt;扩展名名称&lt;/extension&gt;&nbsp;扩展名称<br />
&nbsp; &nbsp; &nbsp; &nbsp; &lt;mime-type&gt;MIME格式&lt;/mime-type&gt;&nbsp;MIME格式.<br />
				</div>
				<div>
					&nbsp; &nbsp; 例如：
				</div>
				<div>
					<div class="dp-highlighter bg_html">
						<div class="bar">
							<div class="tools">
								<b>[html]</b> <a href="http://blog.csdn.net/m751075306/article/details/9452893#" class="ViewSource" title="view plain">view plain</a><span data-mod="popu_168"> <a href="http://blog.csdn.net/m751075306/article/details/9452893#" class="CopyToClipboard" title="copy">copy</a>
								<div style="position:absolute;left:420px;top:4685px;width:18px;height:18px;z-index:99;">
								</div>
</span><span data-mod="popu_169"> </span>
							</div>
						</div>
						<ol class="dp-xml" start="1">
							<li class="alt">
								<span class="tag">&lt;</span><span class="tag-name">mime-mapping</span><span class="tag">&gt;</span>&nbsp;&nbsp;
							</li>
							<li class="">
								&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">extension</span><span class="tag">&gt;</span>doc<span class="tag">&lt;/</span><span class="tag-name">extension</span><span class="tag">&gt;</span>&nbsp;&nbsp;
							</li>
							<li class="alt">
								&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">mime-type</span><span class="tag">&gt;</span>application/vnd.ms-word<span class="tag">&lt;/</span><span class="tag-name">mime-type</span><span class="tag">&gt;</span>&nbsp;&nbsp;
							</li>
							<li class="">
								<span class="tag">&lt;/</span><span class="tag-name">mime-mapping</span><span class="tag">&gt;</span>&nbsp;&nbsp;
							</li>
							<li class="alt">
								<span class="tag">&lt;</span><span class="tag-name">mime-mapping</span><span class="tag">&gt;</span>&nbsp;&nbsp;
							</li>
							<li class="">
								&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">extension</span><span class="tag">&gt;</span>xls<span class="tag">&lt;/</span><span class="tag-name">extension</span><span class="tag">&gt;</span>&nbsp;&nbsp;
							</li>
							<li class="alt">
								&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">mime-type</span><span class="tag">&gt;</span>application/vnd.ms-excel<span class="tag">&lt;/</span><span class="tag-name">mime-type</span><span class="tag">&gt;</span>&nbsp;&nbsp;
							</li>
							<li class="">
								<span class="tag">&lt;/</span><span class="tag-name">mime-mapping</span><span class="tag">&gt;</span>&nbsp;&nbsp;
							</li>
							<li class="alt">
								<span class="tag">&lt;</span><span class="tag-name">mime-mapping</span><span class="tag">&gt;</span>&nbsp;&nbsp;
							</li>
							<li class="">
								&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">extension</span><span class="tag">&gt;</span>ppt<span class="tag">&lt;/</span><span class="tag-name">extesnion</span><span class="tag">&gt;</span>&nbsp;&nbsp;
							</li>
							<li class="alt">
								&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">mime-type</span><span class="tag">&gt;</span>application/vnd.ms-powerpoint<span class="tag">&lt;/</span><span class="tag-name">mime-type</span><span class="tag">&gt;</span>&nbsp;&nbsp;
							</li>
							<li class="">
								<span class="tag">&lt;/</span><span class="tag-name">mime-mapping</span><span class="tag">&gt;</span>&nbsp;&nbsp;
							</li>
						</ol>
					</div>
					<h2 style="font-family:FangSong_GB2312;white-space:pre;">
						<a name="t11"></a><span style="font-family:SimSun;"><span style="font-size:14px;">10.</span></span><span style="font-family:SimSun;font-size:14px;">&lt;<strong>welcome-file-list</strong>&gt;</span>
					</h2>
					<div>
						&nbsp; &nbsp; welcome-file-list包含一个子元素welcome-file.用来定义首页列单.<br />
&nbsp; &nbsp; &nbsp; &nbsp; &lt;welcome-file&gt;用来指定首页文件名称&lt;/welcome-flie&gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; welcome-file用来指定首页文件名称.我们可以用&lt;welcome-file&gt;指定几个首页,而服务器会依照设定的顺序来找首页.<br />
					</div>
					<div>
						&nbsp; &nbsp; 例如：
					</div>
					<div>
						<div class="dp-highlighter bg_html">
							<div class="bar">
								<div class="tools">
									<b>[html]</b> <a href="http://blog.csdn.net/m751075306/article/details/9452893#" class="ViewSource" title="view plain">view plain</a><span data-mod="popu_168"> <a href="http://blog.csdn.net/m751075306/article/details/9452893#" class="CopyToClipboard" title="copy">copy</a>
									<div style="position:absolute;left:420px;top:5100px;width:18px;height:18px;z-index:99;">
									</div>
</span><span data-mod="popu_169"> </span>
								</div>
							</div>
							<ol class="dp-xml" start="1">
								<li class="alt">
									<span class="tag">&lt;</span><span class="tag-name">welcome-file-list</span><span class="tag">&gt;</span>&nbsp;&nbsp;
								</li>
								<li class="">
									&nbsp;&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">welcome-file</span><span class="tag">&gt;</span>index.jsp<span class="tag">&lt;/</span><span class="tag-name">welcome-file</span><span class="tag">&gt;</span>&nbsp;&nbsp;
								</li>
								<li class="alt">
									&nbsp;&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">welcome-file</span><span class="tag">&gt;</span>index.htm<span class="tag">&lt;/</span><span class="tag-name">welcome-file</span><span class="tag">&gt;</span>&nbsp;&nbsp;
								</li>
								<li class="">
									<span class="tag">&lt;/</span><span class="tag-name">welcome-file-list</span><span class="tag">&gt;</span>&nbsp;&nbsp;
								</li>
							</ol>
						</div>
						<h2 style="font-family:FangSong_GB2312;white-space:pre;">
							<a name="t12"></a><span style="font-family:SimSun;"><span style="font-size:14px;">11.</span></span><span style="font-family:SimSun;font-size:14px;">&lt;error-page&gt;</span>
						</h2>
						<div>
							&nbsp; &nbsp; error-page元素包含三个子元素error-code,exception-type和location.
						</div>
						<div>
							&nbsp; &nbsp; 将错误代码(Error Code)或异常(Exception)的种类对应到web应用资源路径.<br />
						</div>
						<div>
							&nbsp; &nbsp; &nbsp; &nbsp; &lt;error-code&gt;错误代码&lt;/error-code&gt;&nbsp;HTTP Error code,例如: 404<br />
&nbsp; &nbsp; &nbsp; &nbsp; &lt;exception-type&gt;Exception&lt;/exception-type&gt;&nbsp;一个完整名称的Java异常类型<br />
&nbsp; &nbsp; &nbsp; &nbsp; &lt;location&gt;/路径&lt;/location&gt; &nbsp;在web应用内的相关资源路径<br />
						</div>
						<div>
							&nbsp; &nbsp; 例如：
						</div>
						<div>
							<div class="dp-highlighter bg_html">
								<div class="bar">
									<div class="tools">
										<b>[html]</b> <a href="http://blog.csdn.net/m751075306/article/details/9452893#" class="ViewSource" title="view plain">view plain</a><span data-mod="popu_168"> <a href="http://blog.csdn.net/m751075306/article/details/9452893#" class="CopyToClipboard" title="copy">copy</a>
										<div style="position:absolute;left:420px;top:5423px;width:18px;height:18px;z-index:99;">
										</div>
</span><span data-mod="popu_169"> </span>
									</div>
								</div>
								<ol class="dp-xml" start="1">
									<li class="alt">
										<span class="tag">&lt;</span><span class="tag-name">error-page</span><span class="tag">&gt;</span>&nbsp;&nbsp;
									</li>
									<li class="">
										&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">error-code</span><span class="tag">&gt;</span>404<span class="tag">&lt;/</span><span class="tag-name">error-code</span><span class="tag">&gt;</span>&nbsp;&nbsp;
									</li>
									<li class="alt">
										&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">location</span><span class="tag">&gt;</span>/error404.jsp<span class="tag">&lt;/</span><span class="tag-name">location</span><span class="tag">&gt;</span>&nbsp;&nbsp;
									</li>
									<li class="">
										<span class="tag">&lt;/</span><span class="tag-name">error-page</span><span class="tag">&gt;</span>&nbsp;&nbsp;
									</li>
									<li class="alt">
										<span class="tag">&lt;</span><span class="tag-name">error-page</span><span class="tag">&gt;</span>&nbsp;&nbsp;
									</li>
									<li class="">
										&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">exception-type</span><span class="tag">&gt;</span>java.lang.Exception<span class="tag">&lt;/</span><span class="tag-name">exception-type</span><span class="tag">&gt;</span>&nbsp;&nbsp;
									</li>
									<li class="alt">
										&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">location</span><span class="tag">&gt;</span>/except.jsp<span class="tag">&lt;/</span><span class="tag-name">location</span><span class="tag">&gt;</span>&nbsp;&nbsp;
									</li>
									<li class="">
										<span class="tag">&lt;/</span><span class="tag-name">error-page</span><span class="tag">&gt;</span>&nbsp;&nbsp;
									</li>
								</ol>
							</div>
							<h2 style="font-family:FangSong_GB2312;white-space:pre;">
								<a name="t13"></a><span style="font-family:SimSun;"><span style="font-size:14px;">12.</span></span><span style="font-family:SimSun;font-size:14px;">&lt;jsp-config&gt;</span>
							</h2>
							<div>
								&nbsp; &nbsp; 
jsp-config元素主要用来设定JSP的相关配置,&lt;jsp:config&gt;包括&lt;taglib&gt;和&lt;jsp-
property-group&gt;两个子元素.其中&lt;taglib&gt;元素在JSP 
1.2时就已经存在了;而&lt;jsp-property-group&gt;是JSP 2.0新增的元素.<br />
							</div>
							<div>
								<br />
							</div>
							<div>
								&nbsp; &nbsp; &lt;taglib&gt;<br />
&nbsp; &nbsp; taglib元素包含两个子元素taglib-uri和taglib-location.用来设定JSP网页用到的Tag Library路径.<br />
&nbsp; &nbsp; &nbsp; &nbsp; &lt;taglib-uri&gt;URI&lt;/taglib-uri&gt;&nbsp;taglib-uri定义TLD文件的URI,JSP网页的taglib指令可以经由这个URI存取到TLD文件.<br />
&nbsp; &nbsp; &nbsp; &nbsp; &lt;taglib-location&gt;/WEB-INF/lib/xxx.tld&lt;/taglib-laction&gt;&nbsp;TLD文件对应Web应用的存放位置.<br />
<br />
							</div>
							<div>
								&nbsp; &nbsp; &lt;jsp-property-group&gt;<br />
&nbsp; &nbsp; jsp-property-group元素包含8个元素,分别为:<br />
&nbsp; &nbsp; &nbsp; &nbsp; &lt;description&gt;Description&lt;/descrition&gt; &nbsp; &nbsp;此设定的说明<br />
&nbsp; &nbsp; &nbsp; &nbsp; &lt;display-name&gt;Name&lt;/display-name&gt; &nbsp; &nbsp; &nbsp; &nbsp;此设定的名称<br />
&nbsp; &nbsp; &nbsp; &nbsp; &lt;url-pattern&gt;URL&lt;/url-pattern&gt; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;设定值所影响的范围,如:/CH2 或者/*.jsp<br />
&nbsp; &nbsp; &nbsp; &nbsp; &lt;el-ignored&gt;true|false&lt;/el-ignored&gt; &nbsp; &nbsp; &nbsp;若为true,表示不支持EL语法.<br />
&nbsp; &nbsp; &nbsp; &nbsp; &lt;scripting-invalid&gt;true|false&lt;/scripting-invalid&gt; &nbsp; &nbsp;若为true表示不支持&lt;%scription%&gt;语法.<br />
&nbsp; &nbsp; &nbsp; &nbsp; &lt;page-encoding&gt;encoding&lt;/page-encoding&gt; &nbsp;设定JSP网页的编码<br />
&nbsp; &nbsp; &nbsp; &nbsp; &lt;include-prelude&gt;.jspf&lt;/include-prelude&gt; 设置JSP网页的抬头,扩展名为.jspf<br />
&nbsp; &nbsp; &nbsp; &nbsp; &lt;include-coda&gt;.jspf&lt;/include-coda&gt; &nbsp; &nbsp; &nbsp;&nbsp;设置JSP网页的结尾,扩展名为.jspf
							</div>
							<div>
								<br />
							</div>
							<div>
								&nbsp; &nbsp; 例如：
							</div>
							<div>
								<div class="dp-highlighter bg_html">
									<div class="bar">
										<div class="tools">
											<b>[html]</b> <a href="http://blog.csdn.net/m751075306/article/details/9452893#" class="ViewSource" title="view plain">view plain</a><span data-mod="popu_168"> <a href="http://blog.csdn.net/m751075306/article/details/9452893#" class="CopyToClipboard" title="copy">copy</a>
											<div style="position:absolute;left:420px;top:6182px;width:18px;height:18px;z-index:99;">
											</div>
</span><span data-mod="popu_169"> </span>
										</div>
									</div>
									<ol class="dp-xml" start="1">
										<li class="alt">
											<span class="tag">&lt;</span><span class="tag-name">jsp-config</span><span class="tag">&gt;</span>&nbsp;&nbsp;
										</li>
										<li class="">
											&nbsp;&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">taglib</span><span class="tag">&gt;</span>&nbsp;&nbsp;
										</li>
										<li class="alt">
											&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">taglib-uri</span><span class="tag">&gt;</span>Taglib<span class="tag">&lt;/</span><span class="tag-name">taglib-uri</span><span class="tag">&gt;</span>&nbsp;&nbsp;
										</li>
										<li class="">
											&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">taglib-location</span><span class="tag">&gt;</span>/WEB-INF/tlds/MyTaglib.tld<span class="tag">&lt;/</span><span class="tag-name">taglib-location</span><span class="tag">&gt;</span>&nbsp;&nbsp;
										</li>
										<li class="alt">
											&nbsp;&nbsp;&nbsp;&nbsp;<span class="tag">&lt;/</span><span class="tag-name">taglib</span><span class="tag">&gt;</span>&nbsp;&nbsp;
										</li>
										<li class="">
											&nbsp;&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">jsp-property-group</span><span class="tag">&gt;</span>&nbsp;&nbsp;
										</li>
										<li class="alt">
											&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">description</span><span class="tag">&gt;</span>&nbsp;&nbsp;
										</li>
										<li class="">
											&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Special&nbsp;property&nbsp;group&nbsp;for&nbsp;JSP&nbsp;Configuration&nbsp;JSP&nbsp;example.&nbsp;&nbsp;
										</li>
										<li class="alt">
											&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="tag">&lt;/</span><span class="tag-name">description</span><span class="tag">&gt;</span>&nbsp;&nbsp;
										</li>
										<li class="">
											&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">display-name</span><span class="tag">&gt;</span>JSPConfiguration<span class="tag">&lt;/</span><span class="tag-name">display-name</span><span class="tag">&gt;</span>&nbsp;&nbsp;
										</li>
										<li class="alt">
											&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">uri-pattern</span><span class="tag">&gt;</span>/*<span class="tag">&lt;/</span><span class="tag-name">uri-pattern</span><span class="tag">&gt;</span>&nbsp;&nbsp;
										</li>
										<li class="">
											&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">el-ignored</span><span class="tag">&gt;</span>true<span class="tag">&lt;/</span><span class="tag-name">el-ignored</span><span class="tag">&gt;</span>&nbsp;&nbsp;
										</li>
										<li class="alt">
											&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">page-encoding</span><span class="tag">&gt;</span>GB2312<span class="tag">&lt;/</span><span class="tag-name">page-encoding</span><span class="tag">&gt;</span>&nbsp;&nbsp;
										</li>
										<li class="">
											&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">scripting-inivalid</span><span class="tag">&gt;</span>true<span class="tag">&lt;/</span><span class="tag-name">scripting-inivalid</span><span class="tag">&gt;</span>&nbsp;&nbsp;
										</li>
										<li class="alt">
											&nbsp;&nbsp;&nbsp;............&nbsp;&nbsp;
										</li>
										<li class="">
											&nbsp;&nbsp;&nbsp;&nbsp;<span class="tag">&lt;/</span><span class="tag-name">jsp-property-group</span><span class="tag">&gt;</span>&nbsp;&nbsp;
										</li>
										<li class="alt">
											<span class="tag">&lt;/</span><span class="tag-name">jsp-config</span><span class="tag">&gt;</span>&nbsp;&nbsp;
										</li>
									</ol>
								</div>
								<h2 style="white-space:pre;">
									<a name="t14"></a><span style="font-family:SimSun;"><span style="font-size:14px;"></span></span>
								</h2>
								<h2 style="font-family:FangSong_GB2312;white-space:pre;">
									<a name="t15"></a><span style="font-family:SimSun;"><span style="font-size:14px;">12.</span></span><span style="font-family:SimSun;font-size:14px;">&lt;<strong>resource-ref</strong>&gt;</span>
								</h2>
								<div>
									resource-ref元素包括五个子元素description,res-ref-name,res-type,res-auth,res-sharing-scope.利用JNDI取得应用可利用资源.
								</div>
								<div>
									&nbsp; &nbsp; &lt;description&gt;说明&lt;/description&gt; 资源说明<br />
&nbsp; &nbsp; &lt;rec-ref-name&gt;资源名称&lt;/rec-ref-name&gt; 资源名称<br />
&nbsp; &nbsp; &lt;res-type&gt;资源种类&lt;/res-type&gt; 资源种类<br />
&nbsp; &nbsp; &lt;res-auth&gt;Application|Container&lt;/res-auth&gt; 资源由Application或Container来许可<br />
&nbsp; &nbsp; &lt;res-sharing-scope&gt;Shareable|Unshareable&lt;/res-sharing-scope&gt; 资源是否可以共享.默认值为 Shareable
								</div>
								<div>
									例如：
								</div>
								<div>
									<div class="dp-highlighter bg_html">
										<div class="bar">
											<div class="tools">
												<b>[html]</b> <a href="http://blog.csdn.net/m751075306/article/details/9452893#" class="ViewSource" title="view plain">view plain</a><span data-mod="popu_168"> <a href="http://blog.csdn.net/m751075306/article/details/9452893#" class="CopyToClipboard" title="copy">copy</a>
												<div style="position:absolute;left:420px;top:6791px;width:18px;height:18px;z-index:99;">
												</div>
</span><span data-mod="popu_169"> </span>
											</div>
										</div>
										<ol class="dp-xml" start="1">
											<li class="alt">
												<span class="tag">&lt;</span><span class="tag-name">resource-ref</span><span class="tag">&gt;</span>&nbsp;&nbsp;
											</li>
											<li class="">
												&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">description</span><span class="tag">&gt;</span>JNDI&nbsp;JDBC&nbsp;DataSource&nbsp;of&nbsp;JSPBook<span class="tag">&lt;/</span><span class="tag-name">description</span><span class="tag">&gt;</span>&nbsp;&nbsp;
											</li>
											<li class="alt">
												&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">res-ref-name</span><span class="tag">&gt;</span>jdbc/sample_db<span class="tag">&lt;/</span><span class="tag-name">res-ref-name</span><span class="tag">&gt;</span>&nbsp;&nbsp;
											</li>
											<li class="">
												&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">res-type</span><span class="tag">&gt;</span>javax.sql.DataSoruce<span class="tag">&lt;/</span><span class="tag-name">res-type</span><span class="tag">&gt;</span>&nbsp;&nbsp;
											</li>
											<li class="alt">
												&nbsp;&nbsp;&nbsp;<span class="tag">&lt;</span><span class="tag-name">res-auth</span><span class="tag">&gt;</span>Container<span class="tag">&lt;/</span><span class="tag-name">res-auth</span><span class="tag">&gt;</span>&nbsp;&nbsp;
											</li>
											<li class="">
												<span class="tag">&lt;/</span><span class="tag-name">resource-ref</span><span class="tag">&gt;</span>&nbsp;&nbsp;
											</li>
										</ol>
									</div>
								</div>
							</div>
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</div>