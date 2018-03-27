<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	http://hi.baidu.com/sunyaming/blog/item/fec4450e6b0191c77acbe182.html
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	在开发中我们经常需要把我们的应用设置为全屏，这里我所知道的有俩中方法，一中是在代码中设置，另一种方法是在配置文件里改！
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	一、在代码中设置:
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	view plaincopy to clipboardprint?<br />
package com.<a href="http://lib.csdn.net/base/android" class="replace_word" title="Android知识库" target="_blank" style="color:#DF3434;text-decoration-line:none;font-weight:bold;">Android</a>.tutor;&nbsp;&nbsp;&nbsp;<br />
import android.app.Activity;&nbsp;&nbsp;&nbsp;<br />
import android.os.Bundle;&nbsp;&nbsp;&nbsp;<br />
import android.view.Window;&nbsp;&nbsp;&nbsp;<br />
import android.view.WindowManager;&nbsp;&nbsp;&nbsp;<br />
public class OpenGl_Lesson1 extends Activity {&nbsp;&nbsp;&nbsp;<br />
&nbsp;&nbsp;&nbsp; public void onCreate(Bundle savedInstanceState) {&nbsp;&nbsp;&nbsp;<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; super.onCreate(savedInstanceState);&nbsp;&nbsp;&nbsp;<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; //无title&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; requestWindowFeature(Window.FEATURE_NO_TITLE);&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; //全屏&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; getWindow().setFlags(WindowManager.LayoutParams. FLAG_FULLSCREEN ,&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; WindowManager.LayoutParams. FLAG_FULLSCREEN);&nbsp;&nbsp;&nbsp;&nbsp;<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; setContentView(R.layout.main);&nbsp;&nbsp;&nbsp;<br />
&nbsp;&nbsp;&nbsp; }&nbsp;&nbsp;&nbsp;<br />
}&nbsp;<br />
package com.android.tutor;<br />
import android.app.Activity;<br />
import android.os.Bundle;<br />
import android.view.Window;<br />
import android.view.WindowManager;<br />
public class OpenGl_Lesson1 extends Activity {<br />
&nbsp;&nbsp;&nbsp; public void onCreate(Bundle savedInstanceState) {<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; super.onCreate(savedInstanceState);<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; //无title&nbsp;<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; requestWindowFeature(Window.FEATURE_NO_TITLE);&nbsp;<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; //全屏&nbsp;<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; getWindow().setFlags(WindowManager.LayoutParams. FLAG_FULLSCREEN ,&nbsp;&nbsp;&nbsp;&nbsp;<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; WindowManager.LayoutParams. FLAG_FULLSCREEN);&nbsp;<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; setContentView(R.layout.main);<br />
&nbsp;&nbsp;&nbsp; }<br />
}
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	在这里要强调一点，设置全屏的俩段代码必须在setContentView(R.layout.main) 之前，不然会报错。
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	二、在配置文件里修改(android:theme="@android:style/Theme.NoTitleBar.Fullscreen"):
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	view plaincopy to clipboardprint?<br />
&lt;?xml version="1.0" encoding="utf-8"?&gt;&nbsp;&nbsp;&nbsp;<br />
&lt;manifest xmlns:android="<a href="http://schemas.android.com/apk/res/android" style="color:#FF9900;text-decoration-line:none;">http://schemas.android.com/apk/res/android</a>&nbsp;"&nbsp;<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; package="com.android.tutor"&nbsp;<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; android:versionCode="1"&nbsp;<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; android:versionName="1.0"&gt;&nbsp;&nbsp;&nbsp;<br />
&nbsp;&nbsp;&nbsp; &lt;application android:icon="@drawable/icon" android:label="@string/app_name"&gt;&nbsp;&nbsp;&nbsp;<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;activity android:name=".OpenGl_Lesson1"&nbsp;<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; android:theme="@android:style/Theme.NoTitleBar.Fullscreen"&nbsp;<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; android:label="@string/app_name"&gt;&nbsp;&nbsp;&nbsp;<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;intent-filter&gt;&nbsp;&nbsp;&nbsp;<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;action android:name="android.intent.action.MAIN" /&gt;&nbsp;&nbsp;&nbsp;<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;category android:name="android.intent.category.LAUNCHER" /&gt;&nbsp;&nbsp;&nbsp;<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;/intent-filter&gt;&nbsp;&nbsp;&nbsp;<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;/activity&gt;&nbsp;&nbsp;&nbsp;<br />
&nbsp;&nbsp;&nbsp; &lt;/application&gt;&nbsp;&nbsp;&nbsp;<br />
&nbsp;&nbsp;&nbsp; &lt;uses-sdk android:minSdkVersion="7" /&gt;&nbsp;&nbsp;&nbsp;<br />
&lt;/manifest&gt;&nbsp;&nbsp;&nbsp;<br />
&lt;?xml version="1.0" encoding="utf-8"?&gt;<br />
&lt;manifest xmlns:android="<a href="http://schemas.android.com/apk/res/android" style="color:#FF9900;text-decoration-line:none;">http://schemas.android.com/apk/res/android</a>&nbsp;"<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; package="com.android.tutor"<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; android:versionCode="1"<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; android:versionName="1.0"&gt;<br />
&nbsp;&nbsp;&nbsp; &lt;application android:icon="@drawable/icon" android:label="@string/app_name"&gt;<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;activity android:name=".OpenGl_Lesson1"<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; android:theme="@android:style/Theme.NoTitleBar.Fullscreen"<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; android:label="@string/app_name"&gt;<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;intent-filter&gt;<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;action android:name="android.intent.action.MAIN" /&gt;<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;category android:name="android.intent.category.LAUNCHER" /&gt;<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;/intent-filter&gt;<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;/activity&gt;<br />
&nbsp;&nbsp;&nbsp; &lt;/application&gt;<br />
&nbsp;&nbsp;&nbsp; &lt;uses-sdk android:minSdkVersion="7" /&gt;<br />
&lt;/manifest&gt;
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	在这里我还想说明一下，用前者在我们应用运行后，会看到短暂的状态栏，然后才全屏，而第二种方法是不会有这种情况的，所以我建议
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	大家使用后者！ 谢谢~
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	让程序全屏的方法，大家都知道，那是静态的，程序运行之初就申明了。但是如果有这样的需求：要在程序运行的过程中，执行了某个操作而使之全屏，然后还需要退出全屏，怎么做？<br />
&nbsp;&nbsp;&nbsp; 如下：<a href="http://lib.csdn.net/base/javase" class="replace_word" title="Java SE知识库" target="_blank" style="color:#DF3434;text-decoration-line:none;font-weight:bold;">Java</a>代码&nbsp;<br />
&nbsp;&nbsp;&nbsp; WindowManager.LayoutParams attrs = getWindow().getAttributes();&nbsp;&nbsp;<br />
&nbsp;&nbsp;&nbsp; attrs.flags |= WindowManager.LayoutParams.FLAG_FULLSCREEN;&nbsp;&nbsp;<br />
&nbsp;&nbsp;&nbsp; getWindow().setAttributes(attrs);&nbsp;&nbsp;<br />
&nbsp;&nbsp;&nbsp; getWindow().addFlags(WindowManager.LayoutParams.FLAG_LAYOUT_NO_LIMITS);&nbsp;&nbsp;<br />
&nbsp;&nbsp;&nbsp; 修改window的LayoutParams参数，然后加上FLAG_LAYOUT_NO_LIMITS标志，就OK了。window会自动重新布局，呈现全屏的状态。<br />
&nbsp;&nbsp;&nbsp; 要退出全屏，只需要清除刚才加上的FLAG_FULLSCREEN参数，然后去掉FLAG_LAYOUT_NO_LIMITS标志。<br />
&nbsp;&nbsp;&nbsp; 如下：Java代码<br />
&nbsp;&nbsp;&nbsp; WindowManager.LayoutParams attrs = getWindow().getAttributes();&nbsp;&nbsp;<br />
&nbsp;&nbsp;&nbsp; attrs.flags &amp;= (~WindowManager.LayoutParams.FLAG_FULLSCREEN);&nbsp;&nbsp;<br />
&nbsp;&nbsp;&nbsp; getWindow().setAttributes(attrs);&nbsp;&nbsp;<br />
&nbsp;&nbsp;&nbsp; getWindow().clearFlags(WindowManager.LayoutParams.FLAG_LAYOUT_NO_LIMITS);
</p>