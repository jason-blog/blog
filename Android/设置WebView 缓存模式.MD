<span style="box-sizing:border-box;line-height:25.2px;color:#404040;font-family:&quot;white-space:normal;background-color:#FFFFFF;font-size:14px;">当我们加载Html时候，会在我们data/应用package下生成database与cache两个文件夹:<br style="box-sizing:border-box;line-height:10px;" />
我们请求的Url记录是保存在webviewCache.db里，而url的内容是保存在webviewCache文件夹下.<br style="box-sizing:border-box;line-height:10px;" />
WebView中存在着两种缓存：网页数据缓存（存储打开过的页面及资源）、H5缓存（即AppCache）。<br style="box-sizing:border-box;line-height:10px;" />
</span><span style="color:#404040;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;"></span>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:25px;line-height:28.8px;color:#404040;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;line-height:25.2px;font-size:14px;"><br style="box-sizing:border-box;line-height:10px;" />
</span>
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:25px;line-height:28.8px;color:#404040;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;line-height:25.2px;font-size:14px;">一、网页缓存</span>
</p>
<span style="box-sizing:border-box;line-height:25.2px;color:#404040;font-family:&quot;white-space:normal;background-color:#FFFFFF;font-size:14px;">1、缓存构成<br style="box-sizing:border-box;line-height:10px;" />
/data/data/package_name/cache/<br style="box-sizing:border-box;line-height:10px;" />
/data/data/package_name/database/webview.db<br style="box-sizing:border-box;line-height:10px;" />
</span><span style="color:#404040;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;"></span>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:25px;line-height:28.8px;color:#404040;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;line-height:25.2px;font-size:14px;">/data/data/package_name/database/webviewCache.db</span>
</p>
<br style="box-sizing:border-box;line-height:10px;color:#404040;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;" />
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:25px;line-height:28.8px;color:#404040;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:25px;line-height:28.8px;color:#404040;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;line-height:25.2px;font-size:14px;">综合可以得知 webview 会将我们浏览过的网页url已经网页文件(css、图片、js等)保存到数据库表中</span>
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:25px;line-height:28.8px;color:#404040;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;line-height:25.2px;font-size:14px;"><br style="box-sizing:border-box;line-height:10px;" />
</span>
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:25px;line-height:28.8px;color:#404040;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;line-height:25.2px;font-size:14px;"><span style="box-sizing:border-box;font-weight:700;"><span style="box-sizing:border-box;line-height:25.2px;color:#3333FF;">缓存模式(5种)</span></span><br style="box-sizing:border-box;line-height:10px;" />
LOAD_CACHE_ONLY: &nbsp;不使用网络，只读取本地缓存数据<br style="box-sizing:border-box;line-height:10px;" />
LOAD_DEFAULT: &nbsp;根据cache-control决定是否从网络上取数据。<br style="box-sizing:border-box;line-height:10px;" />
LOAD_CACHE_NORMAL: API level 17中已经废弃, 从API level 11开始作用同LOAD_DEFAULT模式<br style="box-sizing:border-box;line-height:10px;" />
LOAD_NO_CACHE: 不使用缓存，只从网络获取数据.<br style="box-sizing:border-box;line-height:10px;" />
LOAD_CACHE_ELSE_NETWORK，只要本地有，无论是否过期，或者no-cache，都使用缓存中的数据。<br style="box-sizing:border-box;line-height:10px;" />
如：www.taobao.com的cache-control为no-cache，在模式LOAD_DEFAULT下，无论如何都会从网络上取数据，如果没有网络，就会出现错误页面；在LOAD_CACHE_ELSE_NETWORK模式下，无论是否有网络，只要本地有缓存，都使用缓存。本地没有缓存时才从网络上获取。<br style="box-sizing:border-box;line-height:10px;" />
www.360.com.cn的cache-control为max-age=60，在两种模式下都使用本地缓存数据。<br style="box-sizing:border-box;line-height:10px;" />
<br style="box-sizing:border-box;line-height:10px;" />
<br style="box-sizing:border-box;line-height:10px;" />
总结：根据以上两种模式，建议缓存策略为，判断是否有网络，有的话，使用LOAD_DEFAULT，无网络时，使用LOAD_CACHE_ELSE_NETWORK。<br style="box-sizing:border-box;line-height:10px;" />
</span>
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:25px;line-height:28.8px;color:#404040;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;line-height:25.2px;font-size:14px;"><br style="box-sizing:border-box;line-height:10px;" />
</span>
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:25px;line-height:28.8px;color:#404040;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;line-height:25.2px;color:#3333FF;font-size:14px;"><span style="box-sizing:border-box;font-weight:700;color:#404040;">设置WebView 缓存模式</span></span>
</p>
<div class="dp-highlighter bg_java" style="box-sizing:border-box;line-height:28.8px;color:#404040;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<div class="bar" style="box-sizing:border-box;line-height:28.8px;">
		<div class="tools" style="box-sizing:border-box;line-height:28.8px;">
		</div>
	</div>
</div>
<pre class="brush:java; toolbar: true; auto-links: false;" style="box-sizing:border-box;overflow:auto;font-family:Menlo, Monaco, Consolas, &quot;font-size:13.6px;padding:6px;margin-top:0px;margin-bottom:10px;line-height:1.45;color:#333333;word-break:break-all;word-wrap:break-word;background-color:#F6F6F6;border:none;border-radius:3px;">    private void initWebView() {  
              
            mWebView.getSettings().setJavaScriptEnabled(true);  
            mWebView.getSettings().setRenderPriority(RenderPriority.HIGH);  
            mWebView.getSettings().setCacheMode(WebSettings.LOAD_DEFAULT);  //设置 缓存模式  
            // 开启 DOM storage API 功能  
            mWebView.getSettings().setDomStorageEnabled(true);  
            //开启 database storage API 功能  
            mWebView.getSettings().setDatabaseEnabled(true);   
            String cacheDirPath = getFilesDir().getAbsolutePath()+APP_CACAHE_DIRNAME;  
    //      String cacheDirPath = getCacheDir().getAbsolutePath()+Constant.APP_DB_DIRNAME;  
            Log.i(TAG, "cacheDirPath="+cacheDirPath);  
            //设置数据库缓存路径  
            mWebView.getSettings().setDatabasePath(cacheDirPath);  
            //设置  Application Caches 缓存目录  
            mWebView.getSettings().setAppCachePath(cacheDirPath);  
            //开启 Application Caches 功能  
            mWebView.getSettings().setAppCacheEnabled(true);  
        }  </pre>
<br style="box-sizing:border-box;line-height:10px;color:#404040;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;" />
<br style="box-sizing:border-box;line-height:10px;color:#404040;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;" />
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:25px;line-height:28.8px;color:#404040;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;line-height:25.2px;font-size:14px;"><br style="box-sizing:border-box;line-height:10px;" />
</span>
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:25px;line-height:28.8px;color:#404040;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;line-height:25.2px;color:#3333FF;font-size:14px;"><span style="box-sizing:border-box;font-weight:700;color:#404040;">清除缓存</span></span>
</p>
<div class="dp-highlighter bg_java" style="box-sizing:border-box;line-height:28.8px;color:#404040;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<div class="bar" style="box-sizing:border-box;line-height:28.8px;">
		<div class="tools" style="box-sizing:border-box;line-height:28.8px;">
<pre class="brush:java; toolbar: true; auto-links: false;" style="box-sizing:border-box;overflow:auto;font-family:Menlo, Monaco, Consolas, &quot;font-size:13.6px;padding:6px;margin-top:0px;margin-bottom:10px;line-height:1.45;color:#333333;word-break:break-all;word-wrap:break-word;background-color:#F6F6F6;border:none;border-radius:3px;">    /** 
         * 清除WebView缓存 
         */  
        public void clearWebViewCache(){  
              
            //清理Webview缓存数据库  
            try {  
                deleteDatabase("webview.db");   
                deleteDatabase("webviewCache.db");  
            } catch (Exception e) {  
                e.printStackTrace();  
            }  
              
            //WebView 缓存文件  
            File appCacheDir = new File(getFilesDir().getAbsolutePath()+APP_CACAHE_DIRNAME);  
            Log.e(TAG, "appCacheDir path="+appCacheDir.getAbsolutePath());  
              
            File webviewCacheDir = new File(getCacheDir().getAbsolutePath()+"/webviewCache");  
            Log.e(TAG, "webviewCacheDir path="+webviewCacheDir.getAbsolutePath());  
              
            //删除webview 缓存目录  
            if(webviewCacheDir.exists()){  
                deleteFile(webviewCacheDir);  
            }  
            //删除webview 缓存 缓存目录  
            if(appCacheDir.exists()){  
                deleteFile(appCacheDir);  
            }  
        }  </pre>
<a title="派生到我的代码片" href="https://code.csdn.net/snippets/88240/fork" target="_blank" style="box-sizing:border-box;background-color:transparent;color:#005FA9;text-decoration-line:none;"></a>
		</div>
	</div>
</div>
<br style="box-sizing:border-box;line-height:10px;color:#404040;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;" />
<br style="box-sizing:border-box;line-height:10px;color:#404040;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;" />
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:25px;line-height:28.8px;color:#404040;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;line-height:25.2px;font-size:14px;">完整代码</span>
</p>
<div class="dp-highlighter bg_java" style="box-sizing:border-box;line-height:28.8px;color:#404040;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<div class="bar" style="box-sizing:border-box;line-height:28.8px;">
		<div class="tools" style="box-sizing:border-box;line-height:28.8px;">
<pre class="brush:java; toolbar: true; auto-links: false;" style="box-sizing:border-box;overflow:auto;font-family:Menlo, Monaco, Consolas, &quot;font-size:13.6px;padding:6px;margin-top:0px;margin-bottom:10px;line-height:1.45;color:#333333;word-break:break-all;word-wrap:break-word;background-color:#F6F6F6;border:none;border-radius:3px;">package com.example.webviewtest;  
  
import java.io.File;  
  
import android.app.Activity;  
import android.graphics.Bitmap;  
import android.os.Bundle;  
import android.util.Log;  
import android.view.View;  
import android.webkit.JsPromptResult;  
import android.webkit.JsResult;  
import android.webkit.WebChromeClient;  
import android.webkit.WebSettings;  
import android.webkit.WebSettings.RenderPriority;  
import android.webkit.WebView;  
import android.webkit.WebViewClient;  
import android.widget.RelativeLayout;  
import android.widget.TextView;  
import android.widget.Toast;  
  
public class MainActivity extends Activity {  
  
    private static final String TAG = MainActivity.class.getSimpleName();  
    private static final String APP_CACAHE_DIRNAME = "/webcache";  
    private TextView tv_topbar_title;  
    private RelativeLayout rl_loading;  
    private WebView mWebView;  
    private String url;  
  
    @Override  
    protected void onCreate(Bundle savedInstanceState) {  
        super.onCreate(savedInstanceState);  
        setContentView(R.layout.activity_main);  
          
        //url:http://m.dianhua.cn/detail/31ccb426119d3c9eaa794df686c58636121d38bc?apikey=jFaWGVHdFVhekZYWTBWV1ZHSkZOVlJWY&amp;app=com.yulore.yellowsdk_ios&amp;uid=355136051337627  
        url = "http://m.dianhua.cn/detail/31ccb426119d3c9eaa794df686c58636121d38bc?apikey=jFaWGVHdFVhekZYWTBWV1ZHSkZOVlJWY&amp;app=com.yulore.yellowsdk_ios&amp;uid=355136051337627";  
        findView();  
    }  
  
    private void findView() {  
          
        tv_topbar_title = (TextView) findViewById(R.id.tv_topbar_title);  
          
        rl_loading = (RelativeLayout) findViewById(R.id.rl_loading);  
          
        mWebView = (WebView) findViewById(R.id.mWebView);  
          
        initWebView();  
          
        mWebView.setWebViewClient(new WebViewClient() {  
  
            @Override  
            public void onLoadResource(WebView view, String url) {  
                  
                Log.i(TAG, "onLoadResource url="+url);  
                  
                super.onLoadResource(view, url);  
            }  
  
            @Override  
            public boolean shouldOverrideUrlLoading(WebView webview, String url) {  
  
                Log.i(TAG, "intercept url="+url);  
                  
                webview.loadUrl(url);  
  
                return true;  
            }  
  
            @Override  
            public void onPageStarted(WebView view, String url, Bitmap favicon) {  
                  
                Log.e(TAG, "onPageStarted");  
                  
                rl_loading.setVisibility(View.VISIBLE); // 显示加载界面  
            }  
  
            @Override  
            public void onPageFinished(WebView view, String url) {  
  
                String title = view.getTitle();  
  
                Log.e(TAG, "onPageFinished WebView title=" + title);  
  
                tv_topbar_title.setText(title);  
                tv_topbar_title.setVisibility(View.VISIBLE);  
  
                rl_loading.setVisibility(View.GONE); // 隐藏加载界面  
            }  
  
            @Override  
            public void onReceivedError(WebView view, int errorCode, String description, String failingUrl) {  
  
                rl_loading.setVisibility(View.GONE); // 隐藏加载界面  
  
                Toast.makeText(getApplicationContext(), "",  
                        Toast.LENGTH_LONG).show();  
            }  
        });  
  
        mWebView.setWebChromeClient(new WebChromeClient() {  
  
            @Override  
            public boolean onJsAlert(WebView view, String url, String message, JsResult result) {  
  
                Log.e(TAG, "onJsAlert " + message);  
  
                Toast.makeText(getApplicationContext(), message, Toast.LENGTH_SHORT).show();  
  
                result.confirm();  
  
                return true;  
            }  
  
            @Override  
            public boolean onJsConfirm(WebView view, String url, String message, JsResult result) {  
  
                Log.e(TAG, "onJsConfirm " + message);  
  
                return super.onJsConfirm(view, url, message, result);  
            }  
  
            @Override  
            public boolean onJsPrompt(WebView view, String url, String message, String defaultValue, JsPromptResult result) {  
  
                Log.e(TAG, "onJsPrompt " + url);  
  
                return super.onJsPrompt(view, url, message, defaultValue, result);  
            }  
        });  
          
        mWebView.loadUrl(url);  
    }  
  
    private void initWebView() {  
          
        mWebView.getSettings().setJavaScriptEnabled(true);  
        mWebView.getSettings().setRenderPriority(RenderPriority.HIGH);  
        mWebView.getSettings().setCacheMode(WebSettings.LOAD_DEFAULT);  //设置 缓存模式  
        // 开启 DOM storage API 功能  
        mWebView.getSettings().setDomStorageEnabled(true);  
        //开启 database storage API 功能  
        mWebView.getSettings().setDatabaseEnabled(true);   
        String cacheDirPath = getFilesDir().getAbsolutePath()+APP_CACAHE_DIRNAME;  
//      String cacheDirPath = getCacheDir().getAbsolutePath()+Constant.APP_DB_DIRNAME;  
        Log.i(TAG, "cacheDirPath="+cacheDirPath);  
        //设置数据库缓存路径  
        mWebView.getSettings().setDatabasePath(cacheDirPath);  
        //设置  Application Caches 缓存目录  
        mWebView.getSettings().setAppCachePath(cacheDirPath);  
        //开启 Application Caches 功能  
        mWebView.getSettings().setAppCacheEnabled(true);  
    }  
      
    /** 
     * 清除WebView缓存 
     */  
    public void clearWebViewCache(){  
          
        //清理Webview缓存数据库  
        try {  
            deleteDatabase("webview.db");   
            deleteDatabase("webviewCache.db");  
        } catch (Exception e) {  
            e.printStackTrace();  
        }  
          
        //WebView 缓存文件  
        File appCacheDir = new File(getFilesDir().getAbsolutePath()+APP_CACAHE_DIRNAME);  
        Log.e(TAG, "appCacheDir path="+appCacheDir.getAbsolutePath());  
          
        File webviewCacheDir = new File(getCacheDir().getAbsolutePath()+"/webviewCache");  
        Log.e(TAG, "webviewCacheDir path="+webviewCacheDir.getAbsolutePath());  
          
        //删除webview 缓存目录  
        if(webviewCacheDir.exists()){  
            deleteFile(webviewCacheDir);  
        }  
        //删除webview 缓存 缓存目录  
        if(appCacheDir.exists()){  
            deleteFile(appCacheDir);  
        }  
    }  
      
    /** 
     * 递归删除 文件/文件夹 
     *  
     * @param file 
     */  
    public void deleteFile(File file) {  
  
        Log.i(TAG, "delete file path=" + file.getAbsolutePath());  
          
        if (file.exists()) {  
            if (file.isFile()) {  
                file.delete();  
            } else if (file.isDirectory()) {  
                File files[] = file.listFiles();  
                for (int i = 0; i &lt; files.length; i++) {  
                    deleteFile(files[i]);  
                }  
            }  
            file.delete();  
        } else {  
            Log.e(TAG, "delete file no exists " + file.getAbsolutePath());  
        }  
    }  
  
}  </pre>
		</div>
	</div>
</div>