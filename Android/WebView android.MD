<p style="margin:10px auto;padding:0px;color:#393939;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FAF7EF;">
	http://www.cnblogs.com/tinyphp/p/3858997.html
</p>
<p style="margin:10px auto;padding:0px;color:#393939;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FAF7EF;">
	http://blog.csdn.net/carson_ho/article/details/52693322
</p>
<p style="margin:10px auto;padding:0px;color:#393939;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FAF7EF;">
</p>
<p style="margin:10px auto;padding:0px;color:#393939;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FAF7EF;">
	WebView可以使得网页轻松的内嵌到app里，还可以直接跟js相互调用。
</p>
<p style="margin:10px auto;padding:0px;color:#393939;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FAF7EF;">
	webview有两个方法：setWebChromeClient 和 setWebClient
</p>
<p style="margin:10px auto;padding:0px;color:#393939;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FAF7EF;">
	setWebClient：主要处理解析，渲染网页等浏览器做的事情
</p>
<p style="margin:10px auto;padding:0px;color:#393939;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FAF7EF;">
	setWebChromeClient：辅助WebView处理Javascript的对话框，网站图标，网站title，加载进度等&nbsp;
</p>
<p style="margin:10px auto;padding:0px;color:#393939;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FAF7EF;">
	WebViewClient就是帮助WebView处理各种通知、请求事件的。
</p>
<p style="margin:10px auto;padding:0px;color:#393939;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FAF7EF;">
	&nbsp;
</p>
<p style="margin:10px auto;padding:0px;color:#393939;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FAF7EF;">
	在AndroidManifest.xml设置访问网络权限：
</p>
<div class="cnblogs_code" style="margin:5px 0px;padding:5px;background-color:#F5F5F5;border:1px solid #CCCCCC;overflow:auto;white-space:normal;font-family:&quot;">
<pre style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">&lt;uses-permission android:name="android.permission.INTERNET"/&gt;</pre>
</div>
<p style="margin:10px auto;padding:0px;color:#393939;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FAF7EF;">
	控件：
</p>
<div class="cnblogs_code" style="margin:5px 0px;padding:5px;background-color:#F5F5F5;border:1px solid #CCCCCC;overflow:auto;white-space:normal;font-family:&quot;">
<pre style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">&lt;WebView 
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:id="@+id/webView"
    /&gt;</pre>
</div>
<p style="margin:10px auto;padding:0px;color:#393939;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FAF7EF;">
	&nbsp;
</p>
<p style="margin:10px auto;padding:0px;color:#393939;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FAF7EF;">
	<strong style="margin:0px;padding:0px;">用途一：加载本地/Web资源</strong> 
</p>
<p style="margin:10px auto;padding:0px;color:#393939;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FAF7EF;">
	<img src="http://images.cnitblog.com/i/446475/201407/221119259002313.jpg" alt="" style="margin:0px;padding:0px;max-width:900px;" /> 
</p>
<p style="margin:10px auto;padding:0px;color:#393939;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FAF7EF;">
	example.html 存放在assets文件夹内
</p>
<p style="margin:10px auto;padding:0px;color:#393939;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FAF7EF;">
	调用WebView的loadUrl()方法，
</p>
<p style="margin:10px auto;padding:0px;color:#393939;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FAF7EF;">
	加载本地资源
</p>
<div class="cnblogs_code" style="margin:5px 0px;padding:5px;background-color:#F5F5F5;border:1px solid #CCCCCC;overflow:auto;white-space:normal;font-family:&quot;">
<pre style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">webView =<span style="margin:0px;padding:0px;line-height:1.5 !important;"> (WebView) findViewById(R.id.webView);
webView.loadUrl(</span>"file:///android_asset/example.html");</pre>
</div>
<p style="margin:10px auto;padding:0px;color:#393939;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FAF7EF;">
	加载web资源：
</p>
<div class="cnblogs_code" style="margin:5px 0px;padding:5px;background-color:#F5F5F5;border:1px solid #CCCCCC;overflow:auto;white-space:normal;font-family:&quot;">
<pre style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">webView =<span style="margin:0px;padding:0px;line-height:1.5 !important;"> (WebView) findViewById(R.id.webView);
webView.loadUrl(</span>"http://baidu.com");</pre>
</div>
<p style="margin:10px auto;padding:0px;color:#393939;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FAF7EF;">
	&nbsp;
</p>
<p style="margin:10px auto;padding:0px;color:#393939;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FAF7EF;">
	<strong style="margin:0px;padding:0px;">用途二：在程序内打开网页</strong> 
</p>
<p style="margin:10px auto;padding:0px;color:#393939;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FAF7EF;">
	<strong style="margin:0px;padding:0px;"><img src="http://images.cnitblog.com/i/446475/201407/221115297918446.jpg" alt="" style="margin:0px;padding:0px;max-width:900px;" /></strong> 
</p>
<p style="margin:10px auto;padding:0px;color:#393939;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FAF7EF;">
	&nbsp;
</p>
<p style="margin:10px auto;padding:0px;color:#393939;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FAF7EF;">
	<span style="margin:0px;padding:0px;line-height:1.5;">创建一个自己的WebViewClient，通过</span><span style="margin:0px;padding:0px;line-height:1.5;">setWebViewClient关联</span> 
</p>
<div class="cnblogs_code" style="margin:5px 0px;padding:5px;background-color:#F5F5F5;border:1px solid #CCCCCC;overflow:auto;white-space:normal;font-family:&quot;">
	<div class="cnblogs_code_toolbar" style="margin:5px 0px 0px;padding:0px;">
		<span class="cnblogs_code_copy" style="margin:0px;padding:0px 5px 0px 0px;line-height:1.5 !important;"><a title="复制代码" style="margin:0px;padding:0px;color:#6466B3;text-decoration-line:underline;border:none !important;"><img src="http://common.cnblogs.com/images/copycode.gif" alt="复制代码" style="margin:0px;padding:0px;max-width:900px;border-width:initial !important;border-style:none !important;" /></a></span> 
	</div>
<pre style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;"><span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">package</span><span style="margin:0px;padding:0px;line-height:1.5 !important;"> com.example.testopen; </span><span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">import</span><span style="margin:0px;padding:0px;line-height:1.5 !important;"> android.app.Activity; </span><span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">import</span><span style="margin:0px;padding:0px;line-height:1.5 !important;"> android.os.Bundle; </span><span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">import</span><span style="margin:0px;padding:0px;line-height:1.5 !important;"> android.webkit.WebView; </span><span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">import</span><span style="margin:0px;padding:0px;line-height:1.5 !important;"> android.webkit.WebViewClient; </span><span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">public</span> <span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">class</span> MainActivity <span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">extends</span><span style="margin:0px;padding:0px;line-height:1.5 !important;"> Activity { </span><span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">private</span><span style="margin:0px;padding:0px;line-height:1.5 !important;"> WebView webView;
    @Override </span><span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">protected</span> <span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">void</span><span style="margin:0px;padding:0px;line-height:1.5 !important;"> onCreate(Bundle savedInstanceState) { </span><span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">super</span><span style="margin:0px;padding:0px;line-height:1.5 !important;">.onCreate(savedInstanceState);
        setContentView(R.layout.test);             
        init();

    } </span><span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">private</span> <span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">void</span><span style="margin:0px;padding:0px;line-height:1.5 !important;"> init(){
        webView </span>=<span style="margin:0px;padding:0px;line-height:1.5 !important;"> (WebView) findViewById(R.id.webView); </span><span style="margin:0px;padding:0px;color:#008000;line-height:1.5 !important;">//</span><span style="margin:0px;padding:0px;color:#008000;line-height:1.5 !important;">WebView加载web资源</span> webView.loadUrl("http://baidu.com"<span style="margin:0px;padding:0px;line-height:1.5 !important;">); </span><span style="margin:0px;padding:0px;color:#008000;line-height:1.5 !important;">//</span><span style="margin:0px;padding:0px;color:#008000;line-height:1.5 !important;">覆盖WebView默认使用第三方或系统默认浏览器打开网页的行为，使网页用WebView打开</span> webView.setWebViewClient(<span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">new</span><span style="margin:0px;padding:0px;line-height:1.5 !important;"> WebViewClient(){
           @Override </span><span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">public</span> <span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">boolean</span><span style="margin:0px;padding:0px;line-height:1.5 !important;"> shouldOverrideUrlLoading(WebView view, String url) { </span><span style="margin:0px;padding:0px;color:#008000;line-height:1.5 !important;">//</span><span style="margin:0px;padding:0px;color:#008000;line-height:1.5 !important;"> TODO Auto-generated method stub </span><span style="margin:0px;padding:0px;color:#008000;line-height:1.5 !important;">//</span><span style="margin:0px;padding:0px;color:#008000;line-height:1.5 !important;">返回值是true的时候控制去WebView打开，为false调用系统浏览器或第三方浏览器</span> <span style="margin:0px;padding:0px;line-height:1.5 !important;"> view.loadUrl(url); </span><span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">return</span> <span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">true</span><span style="margin:0px;padding:0px;line-height:1.5 !important;">;
        }
       });
    }
    
}</span></pre>
	<div class="cnblogs_code_toolbar" style="margin:5px 0px 0px;padding:0px;">
		<span class="cnblogs_code_copy" style="margin:0px;padding:0px 5px 0px 0px;line-height:1.5 !important;"><a title="复制代码" style="margin:0px;padding:0px;color:#6466B3;text-decoration-line:underline;border:none !important;"><img src="http://common.cnblogs.com/images/copycode.gif" alt="复制代码" style="margin:0px;padding:0px;max-width:900px;border-width:initial !important;border-style:none !important;" /></a></span> 
	</div>
</div>
<p style="margin:10px auto;padding:0px;color:#393939;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FAF7EF;">
	&nbsp;
</p>
<p style="margin:10px auto;padding:0px;color:#393939;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FAF7EF;">
	<strong style="margin:0px;padding:0px;">用途三：</strong> 
</p>
<p style="margin:10px auto;padding:0px;color:#393939;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FAF7EF;">
	<strong style="margin:0px;padding:0px;">如果访问的页面中有Javascript，则webview必须设置支持Javascript</strong> 
</p>
<div class="cnblogs_code" style="margin:5px 0px;padding:5px;background-color:#F5F5F5;border:1px solid #CCCCCC;overflow:auto;white-space:normal;font-family:&quot;">
<pre style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;"><span style="margin:0px;padding:0px;color:#008000;line-height:1.5 !important;">//</span><span style="margin:0px;padding:0px;color:#008000;line-height:1.5 !important;">启用支持javascript</span> WebSettings settings =<span style="margin:0px;padding:0px;line-height:1.5 !important;"> webView.getSettings();
settings.setJavaScriptEnabled(</span><span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">true</span>);</pre>
</div>
<p style="margin:10px auto;padding:0px;color:#393939;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FAF7EF;">
	&nbsp;
</p>
<p style="margin:10px auto;padding:0px;color:#393939;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FAF7EF;">
	<strong style="margin:0px;padding:0px;">用途四：</strong> 
</p>
<p style="margin:10px auto;padding:0px;color:#393939;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FAF7EF;">
	<strong style="margin:0px;padding:0px;">如果希望浏览的网页后退而不是退出浏览器，需要WebView覆盖URL加载，让它自动生成历史访问记录，那样就可以通过前进或后退访问已访问过的站点。</strong> 
</p>
<div class="cnblogs_code" style="margin:5px 0px;padding:5px;background-color:#F5F5F5;border:1px solid #CCCCCC;overflow:auto;white-space:normal;font-family:&quot;">
	<div class="cnblogs_code_toolbar" style="margin:5px 0px 0px;padding:0px;">
		<span class="cnblogs_code_copy" style="margin:0px;padding:0px 5px 0px 0px;line-height:1.5 !important;"><a title="复制代码" style="margin:0px;padding:0px;color:#6466B3;text-decoration-line:underline;border:none !important;"><img src="http://common.cnblogs.com/images/copycode.gif" alt="复制代码" style="margin:0px;padding:0px;max-width:900px;border-width:initial !important;border-style:none !important;" /></a></span> 
	</div>
<pre style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;"><span style="margin:0px;padding:0px;color:#008000;line-height:1.5 !important;">//</span><span style="margin:0px;padding:0px;color:#008000;line-height:1.5 !important;">改写物理按键——返回的逻辑</span> <span style="margin:0px;padding:0px;line-height:1.5 !important;"> @Override </span><span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">public</span> <span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">boolean</span> onKeyDown(<span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">int</span><span style="margin:0px;padding:0px;line-height:1.5 !important;"> keyCode, KeyEvent event) { </span><span style="margin:0px;padding:0px;color:#008000;line-height:1.5 !important;">//</span><span style="margin:0px;padding:0px;color:#008000;line-height:1.5 !important;"> TODO Auto-generated method stub</span> <span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">if</span>(keyCode==<span style="margin:0px;padding:0px;line-height:1.5 !important;">KeyEvent.KEYCODE_BACK)
        {</span> <span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">if</span><span style="margin:0px;padding:0px;line-height:1.5 !important;">(webView.canGoBack())
            {
                webView.goBack();</span><span style="margin:0px;padding:0px;color:#008000;line-height:1.5 !important;">//</span><span style="margin:0px;padding:0px;color:#008000;line-height:1.5 !important;">返回上一页面</span> <span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">return</span> <span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">true</span><span style="margin:0px;padding:0px;line-height:1.5 !important;">;
            } </span><span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">else</span><span style="margin:0px;padding:0px;line-height:1.5 !important;"> {
                System.exit(</span>0);<span style="margin:0px;padding:0px;color:#008000;line-height:1.5 !important;">//</span><span style="margin:0px;padding:0px;color:#008000;line-height:1.5 !important;">退出程序</span> <span style="margin:0px;padding:0px;line-height:1.5 !important;"> }
        } </span><span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">return</span> <span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">super</span><span style="margin:0px;padding:0px;line-height:1.5 !important;">.onKeyDown(keyCode, event);
    }</span></pre>
	<div class="cnblogs_code_toolbar" style="margin:5px 0px 0px;padding:0px;">
		<span class="cnblogs_code_copy" style="margin:0px;padding:0px 5px 0px 0px;line-height:1.5 !important;"><a title="复制代码" style="margin:0px;padding:0px;color:#6466B3;text-decoration-line:underline;border:none !important;"><img src="http://common.cnblogs.com/images/copycode.gif" alt="复制代码" style="margin:0px;padding:0px;max-width:900px;border-width:initial !important;border-style:none !important;" /></a></span> 
	</div>
</div>
<p style="margin:10px auto;padding:0px;color:#393939;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FAF7EF;">
	<strong style="margin:0px;padding:0px;">用途五：判断页面加载过程</strong> 
</p>
<div class="cnblogs_code" style="margin:5px 0px;padding:5px;background-color:#F5F5F5;border:1px solid #CCCCCC;overflow:auto;white-space:normal;font-family:&quot;">
	<div class="cnblogs_code_toolbar" style="margin:5px 0px 0px;padding:0px;">
		<span class="cnblogs_code_copy" style="margin:0px;padding:0px 5px 0px 0px;line-height:1.5 !important;"><a title="复制代码" style="margin:0px;padding:0px;color:#6466B3;text-decoration-line:underline;border:none !important;"><img src="http://common.cnblogs.com/images/copycode.gif" alt="复制代码" style="margin:0px;padding:0px;max-width:900px;border-width:initial !important;border-style:none !important;" /></a></span> 
	</div>
<pre style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">    webView.setWebChromeClient(<span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">new</span><span style="margin:0px;padding:0px;line-height:1.5 !important;"> WebChromeClient() {
            @Override </span><span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">public</span> <span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">void</span> onProgressChanged(WebView view, <span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">int</span><span style="margin:0px;padding:0px;line-height:1.5 !important;"> newProgress) { </span><span style="margin:0px;padding:0px;color:#008000;line-height:1.5 !important;">//</span><span style="margin:0px;padding:0px;color:#008000;line-height:1.5 !important;"> TODO Auto-generated method stub</span> <span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">if</span> (newProgress == 100<span style="margin:0px;padding:0px;line-height:1.5 !important;">) { </span><span style="margin:0px;padding:0px;color:#008000;line-height:1.5 !important;">//</span><span style="margin:0px;padding:0px;color:#008000;line-height:1.5 !important;"> 网页加载完成</span> <span style="margin:0px;padding:0px;line-height:1.5 !important;"> } </span><span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">else</span><span style="margin:0px;padding:0px;line-height:1.5 !important;"> { </span><span style="margin:0px;padding:0px;color:#008000;line-height:1.5 !important;">//</span><span style="margin:0px;padding:0px;color:#008000;line-height:1.5 !important;"> 加载中</span> <span style="margin:0px;padding:0px;line-height:1.5 !important;"> }

            }
        });</span></pre>
	<div class="cnblogs_code_toolbar" style="margin:5px 0px 0px;padding:0px;">
		<span class="cnblogs_code_copy" style="margin:0px;padding:0px 5px 0px 0px;line-height:1.5 !important;"><a title="复制代码" style="margin:0px;padding:0px;color:#6466B3;text-decoration-line:underline;border:none !important;"><img src="http://common.cnblogs.com/images/copycode.gif" alt="复制代码" style="margin:0px;padding:0px;max-width:900px;border-width:initial !important;border-style:none !important;" /></a></span> 
	</div>
</div>
<p style="margin:10px auto;padding:0px;color:#393939;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FAF7EF;">
	<strong style="margin:0px;padding:0px;">用途六：缓存的使用</strong> 
</p>
<p style="margin:10px auto;padding:0px;color:#393939;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FAF7EF;">
	优先使用缓存
</p>
<div class="cnblogs_code" style="margin:5px 0px;padding:5px;background-color:#F5F5F5;border:1px solid #CCCCCC;overflow:auto;white-space:normal;font-family:&quot;">
<pre style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">webView.getSettings().setCacheMode(WebSettings.LOAD_CACHE_ELSE_NETWORK);</pre>
</div>
<p style="margin:10px auto;padding:0px;color:#393939;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FAF7EF;">
	不使用缓存：
</p>
<div class="cnblogs_code" style="margin:5px 0px;padding:5px;background-color:#F5F5F5;border:1px solid #CCCCCC;overflow:auto;white-space:normal;font-family:&quot;">
<pre style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">webView.getSettings().setCacheMode(WebSettings.LOAD_NO_CACHE);</pre>
</div>