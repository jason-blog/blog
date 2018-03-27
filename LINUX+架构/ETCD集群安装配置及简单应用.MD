<h1 style="box-sizing:border-box;margin:0.8em 0px;font-size:2.6em;font-family:&quot;font-weight:100;line-height:1.1;color:#454545;padding:0px;white-space:normal;background-color:#FFFFFF;">
	<strong style="box-sizing:border-box;"><span style="box-sizing:border-box;margin:0px;padding:0px;font-weight:400;font-size:24px;">环境配置</span></strong> 
</h1>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<strong style="box-sizing:border-box;"><span style="box-sizing:border-box;margin:0px;padding:0px;font-weight:400;font-size:24px;"><br style="box-sizing:border-box;" />
</span></strong> 
</div>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	CentOS Linux release 7.3.1611 (Core)&nbsp;
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	etcd-v3.2.6
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<br />
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	192.168.108.128 节点1
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	192.168.108.129 节点2
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	192.168.108.130 节点3
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<br />
</p>
<h1 style="box-sizing:border-box;margin:0.8em 0px;font-size:2.6em;font-family:&quot;font-weight:100;line-height:1.1;color:#454545;padding:0px;white-space:normal;background-color:#FFFFFF;">
	<a name="t1"></a><strong style="box-sizing:border-box;"><span style="box-sizing:border-box;margin:0px;padding:0px;font-weight:400;font-size:24px;">ETCD下载</span></strong> 
</h1>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<strong style="box-sizing:border-box;"><span style="box-sizing:border-box;margin:0px;padding:0px;font-weight:400;font-size:24px;"><br style="box-sizing:border-box;" />
</span></strong> 
</div>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<a target="_blank" href="http://blog.csdn.net/god_wot/article/details/etcd-v3.2.6" style="box-sizing:border-box;background:transparent;color:#CA0C16;text-decoration-line:none;margin:0px;padding:0px;outline:0px;">https://github.com/coreos/etcd/releases/download/v3.2.6/etcd-v3.2.6-linux-amd64.tar.gz</a> 
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<br />
</p>
<h1 style="box-sizing:border-box;margin:0.8em 0px;font-size:2.6em;font-family:&quot;font-weight:100;line-height:1.1;color:#454545;padding:0px;white-space:normal;background-color:#FFFFFF;">
	<a name="t2"></a>ETCD安装配置
</h1>
<h3 style="box-sizing:border-box;font-family:&quot;font-weight:100;line-height:1.1;color:#454545;margin:0.8em 0px;font-size:1.7em;padding:0px;white-space:normal;background-color:#FFFFFF;">
	<a name="t3"></a> 
	<ul style="box-sizing:border-box;margin:0px;padding:0px;list-style-position:initial;list-style-image:initial;">
		<li style="box-sizing:border-box;margin:0px 0px 0px 40px;padding:0px;list-style:disc;">
			解压安装：
		</li>
	</ul>
</h3>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	$ tar -zxvf &nbsp;etcd-v3.2.6-linux-amd64.tar.gz -C /opt/
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	$ cd /opt
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	$ mv&nbsp;etcd-v3.2.6-linux-amd64 &nbsp;etcd-v3.2.6
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	$ mkdir /etc/etcd &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; # 创建etcd配置文件目录
</p>
<h3 style="box-sizing:border-box;font-family:&quot;font-weight:100;line-height:1.1;color:#454545;margin:0.8em 0px;font-size:1.7em;padding:0px;white-space:normal;background-color:#FFFFFF;">
	<a name="t4"></a> 
	<ul style="box-sizing:border-box;margin:0px;padding:0px;list-style-position:initial;list-style-image:initial;">
		<li style="box-sizing:border-box;margin:0px 0px 0px 40px;padding:0px;list-style:disc;">
			创建etcd配置文件：
		</li>
	</ul>
</h3>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	$ vi /etc/etcd/conf.yml
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	节点1，添加如下内容：
</p>
<div class="dp-highlighter bg_plain" style="box-sizing:border-box;padding:1px 0px 0px;position:relative;overflow-y:hidden;overflow-x:auto;font-family:Consolas, &quot;background-color:#E7E5DC;width:851.391px;color:#454545;white-space:normal;margin:18px 0px !important;">
	<div class="bar" style="box-sizing:border-box;margin:0px;padding:0px 0px 0px 45px;">
		<div class="tools" style="box-sizing:border-box;margin:0px;padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;border-right:1px solid #E7E5DC;">
			<b style="box-sizing:border-box;">[plain]</b>&nbsp;<a href="http://blog.csdn.net/god_wot/article/details/77854093#" class="ViewSource" title="view plain" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#A0A0A0;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:0px;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span class="tracking-ad" data-mod="popu_168" style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;<a href="http://blog.csdn.net/god_wot/article/details/77854093#" class="CopyToClipboard" title="copy" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#A0A0A0;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:0px;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a> 
			<div style="box-sizing:border-box;margin:0px;padding:0px;position:absolute;left:501px;top:1133px;width:16px;height:16px;z-index:99;">
			</div>
</span><span class="tracking-ad" data-mod="popu_169" style="box-sizing:border-box;margin:0px;padding:0px;"></span> 
		</div>
	</div>
	<ol start="1" style="box-sizing:border-box;padding:0px;list-style-position:initial;list-style-image:initial;border-top:none;border-right:1px solid #E7E5DC;border-bottom:none;border-left:none;border-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;"><span style="box-sizing:border-box;margin:0px;padding:0px;border:none;background-color:inherit;">name:&nbsp;etcd-1&nbsp;&nbsp;</span></span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">data-dir:&nbsp;/opt/etcd-v3.2.6/data&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">listen-client-urls:&nbsp;http://192.168.108.128:2379,http://127.0.0.1:2379&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">advertise-client-urls:&nbsp;http://192.168.108.128:2379,http://127.0.0.1:2379&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">listen-peer-urls:&nbsp;http://192.168.108.128:2380&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">initial-advertise-peer-urls:&nbsp;http://192.168.108.128:2380&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">initial-cluster:&nbsp;etcd-1=http://192.168.108.128:2380,etcd-2=http://192.168.108.129:2380,etcd-3=http://192.168.108.130:2380&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">initial-cluster-token:&nbsp;etcd-cluster-token&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">initial-cluster-state:&nbsp;new&nbsp;&nbsp;</span> 
		</li>
	</ol>
</div>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<br />
</p>
<span style="color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">节点2，添加如下内容：</span> 
<div class="dp-highlighter bg_plain" style="box-sizing:border-box;padding:1px 0px 0px;position:relative;overflow-y:hidden;overflow-x:auto;font-family:Consolas, &quot;background-color:#E7E5DC;width:851.391px;color:#454545;white-space:normal;margin:18px 0px !important;">
	<div class="bar" style="box-sizing:border-box;margin:0px;padding:0px 0px 0px 45px;">
		<div class="tools" style="box-sizing:border-box;margin:0px;padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;border-right:1px solid #E7E5DC;">
			<b style="box-sizing:border-box;">[plain]</b>&nbsp;<a href="http://blog.csdn.net/god_wot/article/details/77854093#" class="ViewSource" title="view plain" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#A0A0A0;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:0px;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span class="tracking-ad" data-mod="popu_168" style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;<a href="http://blog.csdn.net/god_wot/article/details/77854093#" class="CopyToClipboard" title="copy" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#A0A0A0;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:0px;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a> 
			<div style="box-sizing:border-box;margin:0px;padding:0px;position:absolute;left:501px;top:1428px;width:16px;height:16px;z-index:99;">
			</div>
</span><span class="tracking-ad" data-mod="popu_169" style="box-sizing:border-box;margin:0px;padding:0px;"></span> 
		</div>
	</div>
	<ol start="1" style="box-sizing:border-box;padding:0px;list-style-position:initial;list-style-image:initial;border-top:none;border-right:1px solid #E7E5DC;border-bottom:none;border-left:none;border-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;"><span style="box-sizing:border-box;margin:0px;padding:0px;border:none;background-color:inherit;">name:&nbsp;etcd-2&nbsp;&nbsp;</span></span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">data-dir:&nbsp;/opt/etcd-v3.2.6/data&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">listen-client-urls:&nbsp;http://192.168.108.129:2379,http://127.0.0.1:2379&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">advertise-client-urls:&nbsp;http://192.168.108.129:2379,http://127.0.0.1:2379&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">listen-peer-urls:&nbsp;http://192.168.108.129:2380&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">initial-advertise-peer-urls:&nbsp;http://192.168.108.129:2380&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">initial-cluster:&nbsp;etcd-1=http://192.168.108.128:2380,etcd-2=http://192.168.108.129:2380,etcd-3=http://192.168.108.130:2380&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">initial-cluster-token:&nbsp;etcd-cluster-token&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">initial-cluster-state:&nbsp;new&nbsp;&nbsp;</span> 
		</li>
	</ol>
</div>
<br style="box-sizing:border-box;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">节点3，添加如下内容：</span> 
<div class="dp-highlighter bg_plain" style="box-sizing:border-box;padding:1px 0px 0px;position:relative;overflow-y:hidden;overflow-x:auto;font-family:Consolas, &quot;background-color:#E7E5DC;width:851.391px;color:#454545;white-space:normal;margin:18px 0px !important;">
	<div class="bar" style="box-sizing:border-box;margin:0px;padding:0px 0px 0px 45px;">
		<div class="tools" style="box-sizing:border-box;margin:0px;padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;border-right:1px solid #E7E5DC;">
			<b style="box-sizing:border-box;">[plain]</b>&nbsp;<a href="http://blog.csdn.net/god_wot/article/details/77854093#" class="ViewSource" title="view plain" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#A0A0A0;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:0px;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span class="tracking-ad" data-mod="popu_168" style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;<a href="http://blog.csdn.net/god_wot/article/details/77854093#" class="CopyToClipboard" title="copy" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#A0A0A0;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:0px;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a> 
			<div style="box-sizing:border-box;margin:0px;padding:0px;position:absolute;left:501px;top:1723px;width:16px;height:16px;z-index:99;">
			</div>
</span><span class="tracking-ad" data-mod="popu_169" style="box-sizing:border-box;margin:0px;padding:0px;"></span> 
		</div>
	</div>
	<ol start="1" style="box-sizing:border-box;padding:0px;list-style-position:initial;list-style-image:initial;border-top:none;border-right:1px solid #E7E5DC;border-bottom:none;border-left:none;border-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;"><span style="box-sizing:border-box;margin:0px;padding:0px;border:none;background-color:inherit;">name:&nbsp;etcd-3&nbsp;&nbsp;</span></span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">data-dir:&nbsp;/opt/etcd-v3.2.6/data&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">listen-client-urls:&nbsp;http://192.168.108.130:2379,http://127.0.0.1:2379&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">advertise-client-urls:&nbsp;http://192.168.108.130:2379,http://127.0.0.1:2379&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">listen-peer-urls:&nbsp;http://192.168.108.130:2380&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">initial-advertise-peer-urls:&nbsp;http://192.168.108.130:2380&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">initial-cluster:&nbsp;etcd-1=http://192.168.108.128:2380,etcd-2=http://192.168.108.129:2380,etcd-3=http://192.168.108.130:2380&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">initial-cluster-token:&nbsp;etcd-cluster-token&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">initial-cluster-state:&nbsp;new&nbsp;&nbsp;</span> 
		</li>
	</ol>
</div>
<h3 style="box-sizing:border-box;font-family:&quot;font-weight:100;line-height:1.1;color:#454545;margin:0.8em 0px;font-size:1.7em;padding:0px;white-space:normal;background-color:#FFFFFF;">
	<a name="t5"></a> 
	<ul style="box-sizing:border-box;margin:0px;padding:0px;list-style-position:initial;list-style-image:initial;">
		<li style="box-sizing:border-box;margin:0px 0px 0px 40px;padding:0px;list-style:disc;">
			更新etcd系统默认配置：
		</li>
	</ul>
</h3>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	当前使用的是etcd v3版本，系统默认的是v2，通过下面命令修改配置。
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	$ vi /etc/profile
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	在末尾追加
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	export ETCDCTL_API=3
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	$ source /etc/profile
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<br />
</p>
<h1 style="box-sizing:border-box;margin:0.8em 0px;font-size:2.6em;font-family:&quot;font-weight:100;line-height:1.1;color:#454545;padding:0px;white-space:normal;background-color:#FFFFFF;">
	<a name="t6"></a>ETCD命令
</h1>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<br style="box-sizing:border-box;" />
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	$ cd &nbsp;/opt/etcd-v3.2.6
</div>
<h3 style="box-sizing:border-box;font-family:&quot;font-weight:100;line-height:1.1;color:#454545;margin:0.8em 0px;font-size:1.7em;padding:0px;white-space:normal;background-color:#FFFFFF;">
	<a name="t7"></a> 
	<ul style="box-sizing:border-box;margin:0px;padding:0px;list-style-position:initial;list-style-image:initial;">
		<li style="box-sizing:border-box;margin:0px 0px 0px 40px;padding:0px;list-style:disc;">
			创建etcd配置文件：
		</li>
	</ul>
</h3>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	$ ./etcdctl version
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	etcdctl version: 3.2.6<br style="box-sizing:border-box;" />
API version: 3.2
</p>
<h3 style="box-sizing:border-box;font-family:&quot;font-weight:100;line-height:1.1;color:#454545;margin:0.8em 0px;font-size:1.7em;padding:0px;white-space:normal;background-color:#FFFFFF;">
	<a name="t8"></a> 
	<ul style="box-sizing:border-box;margin:0px;padding:0px;list-style-position:initial;list-style-image:initial;">
		<li style="box-sizing:border-box;margin:0px 0px 0px 40px;padding:0px;list-style:disc;">
			启动命令：
		</li>
	</ul>
</h3>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	$ ./etcd --config-file=/etc/etcd/conf.yml
</p>
<h3 style="box-sizing:border-box;font-family:&quot;font-weight:100;line-height:1.1;color:#454545;margin:0.8em 0px;font-size:1.7em;padding:0px;white-space:normal;background-color:#FFFFFF;">
	<a name="t9"></a> 
	<ul style="box-sizing:border-box;margin:0px;padding:0px;list-style-position:initial;list-style-image:initial;">
		<li style="box-sizing:border-box;margin:0px 0px 0px 40px;padding:0px;list-style:disc;">
			查看集群成员信息：
		</li>
	</ul>
</h3>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	$&nbsp;./etcdctl member list
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	2618ce5cd761aa8e: name=etcd-3 peerURLs=http://192.168.108.130:2380 clientURLs=http://127.0.0.1:2379,http://192.168.108.130:2379 isLeader=false<br style="box-sizing:border-box;" />
9c359d48a2f34938: name=etcd-1 peerURLs=http://192.168.108.128:2380 clientURLs=http://127.0.0.1:2379,http://192.168.108.128:2379 isLeader=false<br style="box-sizing:border-box;" />
f3c45714407d68f3: name=etcd-2 peerURLs=http://192.168.108.129:2380 clientURLs=http://127.0.0.1:2379,http://192.168.108.129:2379 isLeader=true
</p>
<h3 style="box-sizing:border-box;font-family:&quot;font-weight:100;line-height:1.1;color:#454545;margin:0.8em 0px;font-size:1.7em;padding:0px;white-space:normal;background-color:#FFFFFF;">
	<a name="t10"></a> 
	<ul style="box-sizing:border-box;margin:0px;padding:0px;list-style-position:initial;list-style-image:initial;">
		<li style="box-sizing:border-box;margin:0px 0px 0px 40px;padding:0px;list-style:disc;">
			查看集群状态（Leader节点）：
		</li>
	</ul>
</h3>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	$&nbsp;./etcdctl cluster-health
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	member 2618ce5cd761aa8e is healthy: got healthy result from http://127.0.0.1:2379<br style="box-sizing:border-box;" />
member 9c359d48a2f34938 is healthy: got healthy result from http://127.0.0.1:2379<br style="box-sizing:border-box;" />
member f3c45714407d68f3 is healthy: got healthy result from http://127.0.0.1:2379<br style="box-sizing:border-box;" />
cluster is healthy
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<br />
</p>
<h1 style="box-sizing:border-box;margin:0.8em 0px;font-size:2.6em;font-family:&quot;font-weight:100;line-height:1.1;color:#454545;padding:0px;white-space:normal;background-color:#FFFFFF;">
	<a name="t11"></a>ECTD读写操作
</h1>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<br />
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	基于HTTP协议的API使用起来比较简单，这里主要通过etcdctl和curl两种方式来做简单介绍。
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	下面通过给message key设置Hello值示例：
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	$ ./etcdctl set /message Hello
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	Hello
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	$ curl -X PUT http://127.0.0.1:2379/v2/keys/message -d value="Hello"<br style="box-sizing:border-box;" />
{"action":"set","node":{"key":"/message","value":"Hello","modifiedIndex":4,"createdIndex":4}}
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<br />
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	读取message的值：
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	$ ./etcdctl &nbsp;get /message<br style="box-sizing:border-box;" />
Hello
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	$ curl http://127.0.0.1:2379/v2/keys/message<br style="box-sizing:border-box;" />
{"action":"get","node":{"key":"/message","value":"Hello","modifiedIndex":9,"createdIndex":9}}
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<br />
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	删除message key：
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	$ ./etcdctl &nbsp;rm &nbsp;/message
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	$ curl -X DELETE http://127.0.0.1:2379/v2/keys/message<br style="box-sizing:border-box;" />
{"action":"delete","node":{"key":"/message","modifiedIndex":10,"createdIndex":9},"prevNode":{"key":"/message","value":"Hello","modifiedIndex":9,"createdIndex":9}}
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<br />
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	说明：因为是集群，所以message在其中一个节点创建后，在集群中的任何节点都可以查询到。
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<br />
</p>
<h1 style="box-sizing:border-box;margin:0.8em 0px;font-size:2.6em;font-family:&quot;font-weight:100;line-height:1.1;color:#454545;padding:0px;white-space:normal;background-color:#FFFFFF;">
	<a name="t12"></a>配置ETCD为启动服务
</h1>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<br style="box-sizing:border-box;" />
</div>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	编辑/usr/lib/systemd/system/etcd.service，添加下面内容：
</p>
<div class="dp-highlighter bg_plain" style="box-sizing:border-box;padding:1px 0px 0px;position:relative;overflow-y:hidden;overflow-x:auto;font-family:Consolas, &quot;background-color:#E7E5DC;width:851.391px;color:#454545;white-space:normal;margin:18px 0px !important;">
	<div class="bar" style="box-sizing:border-box;margin:0px;padding:0px 0px 0px 45px;">
		<div class="tools" style="box-sizing:border-box;margin:0px;padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;border-right:1px solid #E7E5DC;">
			<b style="box-sizing:border-box;">[plain]</b>&nbsp;<a href="http://blog.csdn.net/god_wot/article/details/77854093#" class="ViewSource" title="view plain" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#A0A0A0;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:0px;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span class="tracking-ad" data-mod="popu_168" style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;<a href="http://blog.csdn.net/god_wot/article/details/77854093#" class="CopyToClipboard" title="copy" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#A0A0A0;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:0px;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a> 
			<div style="box-sizing:border-box;margin:0px;padding:0px;position:absolute;left:501px;top:3828px;width:16px;height:16px;z-index:99;">
			</div>
</span><span class="tracking-ad" data-mod="popu_169" style="box-sizing:border-box;margin:0px;padding:0px;"></span> 
		</div>
	</div>
	<ol start="1" style="box-sizing:border-box;padding:0px;list-style-position:initial;list-style-image:initial;border-top:none;border-right:1px solid #E7E5DC;border-bottom:none;border-left:none;border-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;"><span style="box-sizing:border-box;margin:0px;padding:0px;border:none;background-color:inherit;">[Unit]&nbsp;&nbsp;</span></span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">Description=Etcd&nbsp;Server&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">After=network.target&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">After=network-online.target&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">Wants=network-online.target&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">[Service]&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">Type=notify&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">WorkingDirectory=/opt/etcd-v3.2.6/&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">#&nbsp;User=etcd&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">ExecStart=/opt/etcd-v3.2.6/etcd&nbsp;--config-file=/etc/etcd/conf.yml&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">Restart=on-failure&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">LimitNOFILE=65536&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">[Install]&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">WantedBy=multi-user.target&nbsp;&nbsp;</span> 
		</li>
	</ol>
</div>
<br style="box-sizing:border-box;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">更新启动：</span> 
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	systemctl daemon-reload<br style="box-sizing:border-box;" />
systemctl enable etcd<br style="box-sizing:border-box;" />
systemctl start etcd<br style="box-sizing:border-box;" />
systemctl restart etcd
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	systemctl status etcd.service -l
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<br />
</p>
<h1 style="box-sizing:border-box;margin:0.8em 0px;font-size:2.6em;font-family:&quot;font-weight:100;line-height:1.1;color:#454545;padding:0px;white-space:normal;background-color:#FFFFFF;">
	<a name="t13"></a>参考文档
</h1>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<br />
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<a target="_blank" href="https://coreos.com/etcd/docs/latest/getting-started-with-etcd.html" style="box-sizing:border-box;background:transparent;color:#CA0C16;text-decoration-line:none;margin:0px;padding:0px;outline:0px;">https://coreos.com/etcd/docs/latest/getting-started-with-etcd.html</a> 
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<br />
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	http://blog.csdn.net/god_wot/article/details/77854093
</p>
<div>
	<br />
</div>