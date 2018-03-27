<p>
	到官网 http://www.xdebug.com/download.php 下载
</p>
<p>
	<br />
</p>
<p>
	相关文章&nbsp;
</p>
<p>
	http://blog.sina.com.cn/s/blog_6f2274fb0100zh6t.html
</p>
<p>
</p>
找到对应PHP版本的 Xdebug ，后面带 TS 的为线程安全，本机环境为 win7 64 + php-5.5.1-Win32-VC11-x64 ，下载的是 Xdebug 2.3.3 PHP 5.5 VC11 TS (64 bit)<br />
<br />
<br />
<br />
安装:<br />
Win ：将下载的dll文件(这里是php_xdebug-2.3.3-5.5-vc11-x86_64.dll)放到 php 安装目录的 ext 文件夹下。本机放在 D:\ApacheServer\php\ext\<br />
在ApacheServer下面新建xdebug文件夹，再在xdebug下面新建trace与profiler文件夹，用来存放xdebug生成的两种信息<br />
<br />
<br />
<br />
编辑php.ini，加入下面几行<br />
<br />
zend_extension &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;= "D:\ApacheServer\php\ext\php_xdebug-2.3.3-5.5-vc11-x86_64.dll"<br />
;允许远程IDE调试<br />
xdebug.remote_enable &nbsp; &nbsp; &nbsp; &nbsp;= true<br />
;远程主机<br />
xdebug.remote_host &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;= 127.0.0.1<br />
;xdebug.remote_port &nbsp; &nbsp; &nbsp; &nbsp; = 9000 ;默认端口 9000<br />
<br />
xdebug.profiler_enable &nbsp; &nbsp; &nbsp;= on<br />
;临时跟踪信息输出<br />
xdebug.trace_output_dir &nbsp; &nbsp; = "D:\ApacheServer\xdebug\trace"<br />
xdebug.profiler_output_dir &nbsp;= "D:\ApacheServer\xdebug\profiler"<br />
<br />
;其余参数<br />
;开启自动跟踪。自动打开"监测函数调用过程"的功模。该功能可以在你指定的目录中将函数调用的监测信息以文件的形式输出<br />
xdebug.auto_trace &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; = On<br />
;开启异常跟踪<br />
xdebug.show_exception_trace = On<br />
;开启远程调试自动启动<br />
xdebug.remote_autostart &nbsp; &nbsp; = On<br />
;收集变量<br />
xdebug.collect_vars &nbsp; &nbsp; &nbsp; &nbsp; = On<br />
;收集返回值<br />
xdebug.collect_return &nbsp; &nbsp; &nbsp; = On<br />
;收集参数<br />
xdebug.collect_params &nbsp; &nbsp; &nbsp; = On<br />
;显示局部变量<br />
xdebug.show_local_vars &nbsp; &nbsp; &nbsp;= On<br />
;显示默认的错误信息<br />
xdebug.default_enable &nbsp; &nbsp; &nbsp; = On<br />
;用于zend studio远程调试的应用层通信协议<br />
xdebug.remote_handler &nbsp; &nbsp; &nbsp; = dbgp<br />
;如果设得太小,函数中有递归调用自身次数太多时会报超过最大嵌套数错<br />
xdebug.max_nesting_level &nbsp; &nbsp;= 10000<br />
<br />
<br />
zend_extension = "D:\ApacheServer\php\ext\php_xdebug-2.3.3-5.5-vc11-x86_64.dll" 与 Zend Debugger 一样<br />
不同系统及 PHP 版本有不同写法<br />
Linux 和 Mac OS X &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; : zend_extension &nbsp; &nbsp;= "D:\ApacheServer\php\ext\php_xdebug-2.3.3-5.5-vc11-x86_64.dll"<br />
Windows Thread-Safe 版 PHP &nbsp; &nbsp; &nbsp;: zend_extension_ts = "D:\ApacheServer\php\ext\php_xdebug-2.3.3-5.5-vc11-x86_64.dll"<br />
Windows Non-Thread-Safe 版 PHP &nbsp;: zend_extension &nbsp; &nbsp;= "D:\ApacheServer\php\ext\php_xdebug-2.3.3-5.5-vc11-x86_64.dll"<br />
所以同一服务器只能加载一个调试工具，要么 Zend Debugger 要么 Xdebug<br />
但在 PHP5.5 环境下测试， Thread-Safe 版 PHP 后面不能加 _ts 只能写成 zend_extension =&nbsp;<br />
<br />
<br />
xdebug.profiler_enable = on 及后面的目录 "D:\ApacheServer\xdebug" 作用是开启把执行情况的分析文件写入到指定目录中的功能，可自由设置。也可不写<br />
生成的文件，例如 cachegrind.out.4408 这种格式命名的文件，用编辑器打开可以看到很多程序运行的相关细节信息<br />
<br />
重启Apache<br />
<br />
<br />
重启<br />
先写一个可以导致执行出错的程序，例如尝试包含一个不存在的文件。<br />
<br />
&lt;?php<br />
require 'abc.php';<br />
?&gt;<br />
<br />
然后通过浏览器访问，惊奇地发现，出错信息变成了彩色的了，并且Xdebug跟踪代码的执行<br />
<br />
<br />
<br />
Zend Studio设置<br />
Zend Studio 10.6.2<br />
Apache2.4.4<br />
修改 Zend Studio 设置<br />
Window-&gt;Preferences-&gt;PHP-&gt;PHP Executables-&gt;Add<br />
填写内容如下，Executable path选择文件后PHP ini file (optional)自动赋值<br />
Name &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;: PHP 5.5.1_CLI<br />
Executable path &nbsp; &nbsp; &nbsp; &nbsp; : D:\ApacheServer\php\php.exe<br />
PHP ini file (optional) : D:\ApacheServer\php\php.ini<br />
SAPI Type &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; : CLI<br />
PHP debugger &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;: XDebug<br />
点击Finish保存后自动就是默认<br />
<br />
<br />
(如果只需要CLI调试此步可忽略)点击PHP Server下拉框Default PHP Web Server右边的PHP Servers...<br />
选中Name|URL列表中的一条内容，点击右边的Edit<br />
在弹出框的Debugger下拉框中选择XDebug<br />
<br />
<br />
开始调试<br />
在代码中在左边行数栏上双击加断点<br />
Run-&gt;Debug Configurations...<br />
双击PHP CLI Application<br />
在Name处输入想要的名称，在PHP File处右边点击Browse，选择要debug的文件，点击下面的Apply即可<br />
<br />
或者打开要运行的页面<br />
Run-&gt;Debug As-&gt;PHP CLI Application<br />
即可以调试模式运行，也可选择CLI之外其他调试模式<br />
点击工具栏向下箭头(Step Into)或按 F5 逐行执行。点击左边的绿色向右箭头(Resume)或按F8一直执行，直到断点处停下<br />
点击红色按钮(Terminate)结束调试，再点击臭虫按钮重新开始调试<br />