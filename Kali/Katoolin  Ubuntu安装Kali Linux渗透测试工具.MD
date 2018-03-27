<p style="box-sizing:border-box;margin-top:0px;margin-bottom:1.1em;padding:0px;font-family:&quot;border:0px;outline:0px;font-size:15px;vertical-align:baseline;background-image:initial;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;color:#666666;line-height:26px;white-space:normal;">
	我想大多数Linux用户都听说过Kali Linux。它是一个非常好的用于渗透测试的Linux发行版。但通常我们需要在电脑上安装一个完整的Kali Linux才能使用它各种各样的工具。LionSec开发出了一个python工具，叫做Katoolin，它可以让你在其他Linux发行版上使用 Kali的全部工具。目前仅支持ubuntu，其他发行版会陆续支持。
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:1.1em;padding:0px;font-family:&quot;border:0px;outline:0px;font-size:15px;vertical-align:baseline;background-image:initial;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;color:#666666;line-height:26px;white-space:normal;">
	ubuntu如何安装Katoolin
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:1.1em;padding:0px;font-family:&quot;border:0px;outline:0px;font-size:15px;vertical-align:baseline;background-image:initial;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;color:#666666;line-height:26px;white-space:normal;">
	首先你的ubuntu需要安装有python2.7，ubuntu15.04以前的版本都是2.7。最近发布的ubuntu15.10默认python版本为3.5。使用下面的命令查看python版本。
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:1.1em;padding:0px;font-family:&quot;border:0px;outline:0px;font-size:15px;vertical-align:baseline;background-image:initial;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;color:#666666;line-height:26px;white-space:normal;">
	user@linuxhost:~$ python –version&nbsp;<br style="box-sizing:border-box;" />
Python 2.7.9
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:1.1em;padding:0px;font-family:&quot;border:0px;outline:0px;font-size:15px;vertical-align:baseline;background-image:initial;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;color:#666666;line-height:26px;white-space:normal;">
	然后在终端中输入下面命令克隆GitHub仓库
</p>
<pre style="box-sizing:border-box;font-family:&quot;font-size:14px;white-space:pre-wrap;padding:10px;margin-top:0px;margin-bottom:10.5px;line-height:1.45;color:#333333;word-break:break-all;word-wrap:break-word;background:rgba(128, 128, 128, 0.0470588);border:1px solid rgba(128, 128, 128, 0.0745098);border-radius:0px;outline:0px;vertical-align:baseline;">sudo apt-get install git
sudo git clone https://github.com/LionSec/katoolin.git</pre>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:1.1em;padding:0px;font-family:&quot;border:0px;outline:0px;font-size:15px;vertical-align:baseline;background-image:initial;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;color:#666666;line-height:26px;white-space:normal;">
	将katoolin目录下的python脚本复制到/usr/bin/目录下
</p>
<pre style="box-sizing:border-box;font-family:&quot;font-size:14px;white-space:pre-wrap;padding:10px;margin-top:0px;margin-bottom:10.5px;line-height:1.45;color:#333333;word-break:break-all;word-wrap:break-word;background:rgba(128, 128, 128, 0.0470588);border:1px solid rgba(128, 128, 128, 0.0745098);border-radius:0px;outline:0px;vertical-align:baseline;">sudo cp katoolin/katoolin.py /usr/bin/katoolin</pre>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:1.1em;padding:0px;font-family:&quot;border:0px;outline:0px;font-size:15px;vertical-align:baseline;background-image:initial;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;color:#666666;line-height:26px;white-space:normal;">
	为python脚本添加可执行权限
</p>
<pre style="box-sizing:border-box;font-family:&quot;font-size:14px;white-space:pre-wrap;padding:10px;margin-top:0px;margin-bottom:10.5px;line-height:1.45;color:#333333;word-break:break-all;word-wrap:break-word;background:rgba(128, 128, 128, 0.0470588);border:1px solid rgba(128, 128, 128, 0.0745098);border-radius:0px;outline:0px;vertical-align:baseline;">sudo chmod ugo+x /usr/bin/katoolin</pre>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:1.1em;padding:0px;font-family:&quot;border:0px;outline:0px;font-size:15px;vertical-align:baseline;background-image:initial;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;color:#666666;line-height:26px;white-space:normal;">
	输入下面的命令启动katoolin
</p>
<pre style="box-sizing:border-box;font-family:&quot;font-size:14px;white-space:pre-wrap;padding:10px;margin-top:0px;margin-bottom:10.5px;line-height:1.45;color:#333333;word-break:break-all;word-wrap:break-word;background:rgba(128, 128, 128, 0.0470588);border:1px solid rgba(128, 128, 128, 0.0745098);border-radius:0px;outline:0px;vertical-align:baseline;">sudo katoolin</pre>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:1.1em;padding:0px;font-family:&quot;border:0px;outline:0px;font-size:15px;vertical-align:baseline;background-image:initial;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;color:#666666;line-height:26px;white-space:normal;">
	会有一个菜单弹出，根据终端里的菜单启动你需要的渗透测试工具。我们可以看到一共有330个工具。你可以选择1来添加kali linux的软件库，选择2查看分类，选择3安装经典菜单通知，选择4安装kali菜单，选择5查看帮助信息。
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:1.1em;padding:0px;font-family:&quot;border:0px;outline:0px;font-size:15px;vertical-align:baseline;background-image:initial;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;color:#666666;line-height:26px;white-space:normal;">
	之后可以 apt-get install ×× 安装 kali工具
</p>