<p>
	&nbsp; 当发现上网速度变慢时，人们通常会先首先测试自己的电脑到网络服务提供商（通常被称为“最后一公里”）的网络连接速度。在可用于测试宽带速度的网站中，Speedtest.net也许是使用最广泛的。
</p>
<p>
	Speedtest.net的工作原理并不复杂：它在你的浏览器中加载JavaScript代码并自动检测离你最近的Speedtest.net服务器，然后向服务器发送HTTP GET and POST请求来测试上行/下行网速。
</p>
<p>
	但在没有图形化桌面时（例如，当你通过命令行远程登陆服务器或使用没有图形界面的操作系统），基于flash、界面友好的Speedtest.net将无法工作。幸运的是，Speedtest.net提供了一个命令行版本——<a href="https://github.com/sivel/speedtest-cli">speedtest-cli</a>。下面我将向你演示如何在<span class="wp_keywordlink"><a href="http://www.linuxde.net/" title="Linux" target="_blank">Linux</a></span>的命令行中使用speedtest-cli来测试宽带连接速度。
</p>
<h2>
	安装speedtest-cli<br />
</h2>
<p>
	speedtest-cli是一个用Python编写的轻量级Linux命令行工具，在Python2.4至3.4版本下均可运行。它基于Speedtest.net的基础架构来测量网络的上/下行速率。安装speedtest-cli很简单——只需要下载其Python脚本文件。
</p>
<pre>$ <span class="wp_keywordlink"><a href="http://man.linuxde.net/wget" title="wget命令" target="_blank">wget</a></span> https://raw.github.com/sivel/speedtest-cli/master/speedtest_cli.py
$ <span class="wp_keywordlink"><a href="http://man.linuxde.net/chmod" title="chmod命令" target="_blank">chmod</a></span> a+rx speedtest_cli.py
$ <span class="wp_keywordlink"><a href="http://man.linuxde.net/sudo" title="sudo命令" target="_blank">sudo</a></span> <span class="wp_keywordlink"><a href="http://man.linuxde.net/mv" title="mv命令" target="_blank">mv</a></span> speedtest_cli.py /usr/local/bin/speedtest-cli
$ sudo <span class="wp_keywordlink"><a href="http://man.linuxde.net/chown" title="chown命令" target="_blank">chown</a></span> root:root /usr/local/bin/speedtest-cli</pre>
<h2>
	使用speedtest-cli测试网速<br />
</h2>
<p>
	使用speedtest-cli命令也很简单，它不需要任何参数即可工作。
</p>
<pre><span class="crayon-sy" style="outline:none;margin:0px;padding:0px;border:0px;font-variant-numeric:inherit;font-stretch:inherit;font-size:inherit;font-family:inherit;vertical-align:baseline;line-height:15px;white-space:pre-wrap;text-size-adjust:auto;background-color:#F8F8FF;height:inherit !important;color:#333333 !important;">$</span><span class="crayon-h" style="outline:none;margin:0px;padding:0px;border:0px;font-variant-numeric:inherit;font-stretch:inherit;font-size:inherit;font-family:inherit;vertical-align:baseline;line-height:15px;white-space:pre-wrap;text-size-adjust:auto;background-color:#F8F8FF;height:inherit !important;color:#006FE0 !important;"> </span><span class="crayon-i" style="outline:none;margin:0px;padding:0px;border:0px;font-variant-numeric:inherit;font-stretch:inherit;font-size:inherit;font-family:inherit;vertical-align:baseline;line-height:15px;white-space:pre-wrap;text-size-adjust:auto;background-color:#F8F8FF;height:inherit !important;">speedtest</span><span class="crayon-o" style="outline:none;margin:0px;padding:0px;border:0px;font-variant-numeric:inherit;font-stretch:inherit;font-size:inherit;font-family:inherit;vertical-align:baseline;line-height:15px;white-space:pre-wrap;text-size-adjust:auto;background-color:#F8F8FF;height:inherit !important;color:#006FE0 !important;">-</span><span class="crayon-i" style="outline:none;margin:0px;padding:0px;border:0px;font-variant-numeric:inherit;font-stretch:inherit;font-size:inherit;font-family:inherit;vertical-align:baseline;line-height:15px;white-space:pre-wrap;text-size-adjust:auto;background-color:#F8F8FF;height:inherit !important;">cli</span></pre>
<p>
	输入这个命令后，它会自动发现离你最近的Speedtest.net服务器（地理距离），然后打印出测试的网络上/下行速率。&nbsp;
</p>