<p style="margin-top:0px;margin-bottom:1.1em;padding:0px;font-size:14px;white-space:normal;background-color:#FFFFFF;color:#333333;font-family:&quot;">
	最近在开发一个web app，发现横屏后，URL会重新加载，体验很不好。
</p>
<p style="margin-top:0px;margin-bottom:1.1em;padding:0px;font-size:14px;white-space:normal;background-color:#FFFFFF;color:#333333;font-family:&quot;">
	<span style="white-space:pre;"></span>需要更改AndroidManifest.xml文件，在需要禁止重新加载的Activity中增加<a href="http://lib.csdn.net/base/android" class="replace_word" title="Android知识库" target="_blank" style="color:#DF3434;text-decoration-line:none;font-weight:bold;">Android</a>:configChanges="orientation|keyboardHidden|navigation<span style="white-space:pre-wrap;">"。但在手机上<a href="http://lib.csdn.net/base/softwaretest" class="replace_word" title="软件测试知识库" target="_blank" style="color:#DF3434;text-decoration-line:none;font-weight:bold;">测试</a>发现，并没有效果，原来，该设置在android4.0及以上的版本中无效，需要另外一个属性："screenSize"，改成android:configChanges="orientation|keyboardHidden|screenSize"。</span>
</p>
<p style="margin-top:0px;margin-bottom:1.1em;padding:0px;font-size:14px;white-space:normal;background-color:#FFFFFF;color:#333333;font-family:&quot;">
	<span style="white-space:pre-wrap;"><span style="white-space:pre;"></span>configChanges属性的含义及横竖屏切换Activity的生命周期变化请见：</span><a target="_blank" href="http://my.oschina.net/u/242041/blog/203006" style="color:#FF9900;text-decoration-line:none;white-space:pre-wrap;">http://my.oschina.net/u/242041/blog/203006</a>。
</p>
<p style="margin-top:0px;margin-bottom:1.1em;padding:0px;font-size:14px;white-space:normal;background-color:#FFFFFF;color:#333333;font-family:&quot;">
	<span style="white-space:pre;"></span><span style="white-space:pre;"></span>但考虑html页面在手机上横屏后，会出现显示不全的情况，所以就想要禁止手机上横屏，pad上支持横屏。首先想到的是，如何获取屏幕尺寸，参考：<a target="_blank" href="http://blog.csdn.net/lincyang/article/details/42679589" style="color:#FF9900;text-decoration-line:none;">http://blog.csdn.net/lincyang/article/details/42679589</a>，该篇文章介绍的很详细。但实际上，5.5英寸的魅蓝note(分辨率为1920*1080)，读出来的值只有4.5英寸，所以该方法理论上是对的，但实际上，会存在出入。查中关村魅蓝note的参数（官网并没有），实际ppi为401，根据该ppi，计算出来的值就是5.5英寸。但并没有办法获取到该ppi，根据<a target="_blank" href="http://www.zhihu.com/question/23795304" style="color:#FF9900;text-decoration-line:none;">http://www.zhihu.com/question/23795304</a>的介绍，实际厂商设置dpi时会尽量设置成80的倍数，所以401换算成80的倍数就是实际Android接口获取到的值：480。
</p>
<p style="margin-top:0px;margin-bottom:1.1em;padding:0px;font-size:14px;white-space:normal;background-color:#FFFFFF;color:#333333;font-family:&quot;">
	<span style="white-space:pre;"></span>现在已经无法通过计算屏幕尺寸来判断是手机或者平板，那么就要换种思路。
</p>
<p style="margin-top:0px;margin-bottom:1.1em;padding:0px;font-size:14px;white-space:normal;background-color:#FFFFFF;color:#333333;font-family:&quot;">
	<span style="white-space:pre;"></span>根据<a target="_blank" href="http://www.jb51.net/article/49410.htm" style="color:#FF9900;text-decoration-line:none;">http://www.jb51.net/article/49410.htm</a>的介绍，有如下几种方法
</p>
<p style="margin-top:0px;margin-bottom:1.1em;padding:0px;font-size:14px;white-space:normal;background-color:#FFFFFF;color:#333333;font-family:&quot;">
	1、设备尺寸、DPI：根据上文介绍，会出现问题，所以不推荐；
</p>
<p style="margin-top:0px;margin-bottom:1.1em;padding:0px;font-size:14px;white-space:normal;background-color:#FFFFFF;color:#333333;font-family:&quot;">
	2、版本号：原本3.x的版本是属于平板的，但到了4.x、5.x的时代，这已经无法作为判断的依据了，所以也不推荐；
</p>
<p style="margin-top:0px;margin-bottom:1.1em;padding:0px;font-size:14px;white-space:normal;background-color:#FFFFFF;color:#333333;font-family:&quot;">
	3、是否具备电话功能：现在能够通话的平板多着呢，所以也不推荐；
</p>
<p style="margin-top:0px;margin-bottom:1.1em;padding:0px;font-size:14px;white-space:normal;background-color:#FFFFFF;color:#333333;font-family:&quot;">
	4、Configuration的screenLayout：经测试发现，这个可以作为判断的依据。
</p>