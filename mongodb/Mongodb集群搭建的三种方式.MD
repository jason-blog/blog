<p>
	http://blog.csdn.net/luonanqin/article/details/8497860
</p>
<p>
	<br />
</p>
<p>
	<br />
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	&nbsp; &nbsp; &nbsp; &nbsp;Mongodb是时下流行的NoSql数据库，它的存储方式是文档式存储，并不是Key-Value形式。关于Mongodb的特点，这里就不多介绍了，大家可以去看看官方说明：<a href="http://docs.mongodb.org/manual/" target="_blank" style="box-sizing:border-box;background:transparent;color:#CA0C16;text-decoration-line:none;margin:0px;padding:0px;outline:0px;">http://docs.mongodb.org/manual/</a> 
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<a href="http://docs.mongodb.org/manual/" target="_blank" style="box-sizing:border-box;background:transparent;color:#CA0C16;text-decoration-line:none;margin:0px;padding:0px;outline:0px;"><br style="box-sizing:border-box;" />
</a> 
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 今天主要来说说Mongodb的三种集群方式的搭建：Replica Set / Sharding / Master-Slaver。这里只说明最简单的集群搭建方式（生产环境），如果有多个节点可以此类推或者查看官方文档。OS是Ubuntu_x64系统，客户端用的是Java客户端。Mongodb版本是mongodb-linux-x86_64-2.2.2.tgz
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<br />
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;font-size:18px;"><strong style="box-sizing:border-box;">Replica Set</strong></span> 
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 中文翻译叫做副本集，不过我并不喜欢把英文翻译成中文，总是感觉怪怪的。其实简单来说就是集群当中包含了多份数据，保证主节点挂掉了，备节点能继续提供数据服务，提供的前提就是数据需要和主节点一致。如下图：
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<img src="http://img.my.csdn.net/uploads/201301/13/1358056331_2790.png" alt="" height="172" width="364" style="box-sizing:border-box;vertical-align:middle;outline:0px;max-width:100%;" /> 
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Mongodb(M)表示主节点，Mongodb(S)表示备节点，Mongodb(A)表示仲裁节点。主备节点存储数据，仲裁节点不存储数据。客户端同时连接主节点与备节点，不连接仲裁节点。
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 默认设置下，主节点提供所有增删查改服务，备节点不提供任何服务。但是可以通过设置使备节点提供查询服务，这样就可以减少主节点的压力，当客户端进行数据查询时，请求自动转到备节点上。这个设置叫做<a href="http://docs.mongodb.org/manual/applications/replication/#read-preference-modes" target="_blank" style="box-sizing:border-box;background:transparent;color:#CA0C16;text-decoration-line:none;margin:0px;padding:0px;outline:0px;">Read Preference Modes</a>，同时Java客户端提供了简单的配置方式，可以不必直接对数据库进行操作。
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 仲裁节点是一种特殊的节点，它本身并不存储数据，主要的作用是决定哪一个备节点在主节点挂掉之后提升为主节点，所以客户端不需要连接此节点。这里虽然只有一个备节点，但是仍然需要一个仲裁节点来提升备节点级别。我开始也不相信必须要有仲裁节点，但是自己也试过没仲裁节点的话，主节点挂了备节点还是备节点，所以咱们还是需要它的。
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	介绍完了集群方案，那么现在就开始搭建了。
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<br />
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	1.建立数据文件夹
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	一般情况下不会把数据目录建立在mongodb的解压目录下，不过这里方便起见，就建在mongodb解压目录下吧。
</p>
<div class="dp-highlighter bg_plain" style="box-sizing:border-box;padding:1px 0px 0px;position:relative;overflow-y:hidden;overflow-x:auto;font-family:Consolas, &quot;background-color:#E7E5DC;width:851.392px;color:#454545;white-space:normal;margin:18px 0px !important;">
	<div class="bar" style="box-sizing:border-box;margin:0px;padding:0px 0px 0px 45px;">
		<div class="tools" style="box-sizing:border-box;margin:0px;padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;border-right:1px solid #E7E5DC;">
			<b style="box-sizing:border-box;">[plain]</b>&nbsp;<a href="http://blog.csdn.net/luonanqin/article/details/8497860#" class="ViewSource" title="view plain" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#A0A0A0;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:0px;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span class="tracking-ad" data-mod="popu_168" style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;<a href="http://blog.csdn.net/luonanqin/article/details/8497860#" class="CopyToClipboard" title="copy" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#A0A0A0;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:0px;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a> 
			<div style="box-sizing:border-box;margin:0px;padding:0px;position:absolute;left:409px;top:949px;width:15px;height:16px;z-index:99;">
			</div>
</span><span class="tracking-ad" data-mod="popu_169" style="box-sizing:border-box;margin:0px;padding:0px;"></span> 
		</div>
	</div>
	<ol start="1" style="box-sizing:border-box;padding:0px;list-style-position:initial;list-style-image:initial;border-top:none;border-right:1px solid #E7E5DC;border-bottom:none;border-left:none;border-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;"><span style="box-sizing:border-box;margin:0px;padding:0px;border:none;background-color:inherit;">mkdir&nbsp;-p&nbsp;/mongodb/data/master&nbsp;&nbsp;&nbsp;</span></span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">mkdir&nbsp;-p&nbsp;/mongodb/data/slaver&nbsp;&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">mkdir&nbsp;-p&nbsp;/mongodb/data/arbiter&nbsp;&nbsp;&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">#三个目录分别对应主，备，仲裁节点&nbsp;&nbsp;</span> 
		</li>
	</ol>
</div>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	2.建立配置文件
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	由于配置比较多，所以我们将配置写到文件里。
</p>
<div class="dp-highlighter bg_plain" style="box-sizing:border-box;padding:1px 0px 0px;position:relative;overflow-y:hidden;overflow-x:auto;font-family:Consolas, &quot;background-color:#E7E5DC;width:851.392px;color:#454545;white-space:normal;margin:18px 0px !important;">
	<div class="bar" style="box-sizing:border-box;margin:0px;padding:0px 0px 0px 45px;">
		<div class="tools" style="box-sizing:border-box;margin:0px;padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;border-right:1px solid #E7E5DC;">
			<b style="box-sizing:border-box;">[plain]</b>&nbsp;<a href="http://blog.csdn.net/luonanqin/article/details/8497860#" class="ViewSource" title="view plain" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#A0A0A0;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:0px;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span class="tracking-ad" data-mod="popu_168" style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;<a href="http://blog.csdn.net/luonanqin/article/details/8497860#" class="CopyToClipboard" title="copy" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#A0A0A0;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:0px;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a> 
			<div style="box-sizing:border-box;margin:0px;padding:0px;position:absolute;left:409px;top:1133px;width:15px;height:16px;z-index:99;">
			</div>
</span><span class="tracking-ad" data-mod="popu_169" style="box-sizing:border-box;margin:0px;padding:0px;"></span> 
		</div>
	</div>
	<ol start="1" style="box-sizing:border-box;padding:0px;list-style-position:initial;list-style-image:initial;border-top:none;border-right:1px solid #E7E5DC;border-bottom:none;border-left:none;border-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;"><span style="box-sizing:border-box;margin:0px;padding:0px;border:none;background-color:inherit;">#master.conf&nbsp;&nbsp;</span></span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">dbpath=/mongodb/data/master&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">logpath=/mongodb/log/master.log&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">pidfilepath=/mongodb/master.pid&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">directoryperdb=true&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">logappend=true&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">replSet=testrs&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">bind_ip=10.10.148.130&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">port=27017&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">oplogSize=10000&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">fork=true&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">noprealloc=true&nbsp;&nbsp;</span> 
		</li>
	</ol>
</div>
<div class="dp-highlighter bg_plain" style="box-sizing:border-box;padding:1px 0px 0px;position:relative;overflow-y:hidden;overflow-x:auto;font-family:Consolas, &quot;background-color:#E7E5DC;width:851.392px;color:#454545;white-space:normal;margin:18px 0px !important;">
	<div class="bar" style="box-sizing:border-box;margin:0px;padding:0px 0px 0px 45px;">
		<div class="tools" style="box-sizing:border-box;margin:0px;padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;border-right:1px solid #E7E5DC;">
			<b style="box-sizing:border-box;">[plain]</b>&nbsp;<a href="http://blog.csdn.net/luonanqin/article/details/8497860#" class="ViewSource" title="view plain" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#A0A0A0;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:0px;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span class="tracking-ad" data-mod="popu_168" style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;<a href="http://blog.csdn.net/luonanqin/article/details/8497860#" class="CopyToClipboard" title="copy" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#A0A0A0;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:0px;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a> 
			<div style="box-sizing:border-box;margin:0px;padding:0px;position:absolute;left:409px;top:1389px;width:15px;height:16px;z-index:99;">
			</div>
</span><span class="tracking-ad" data-mod="popu_169" style="box-sizing:border-box;margin:0px;padding:0px;"></span> 
		</div>
	</div>
	<ol start="1" style="box-sizing:border-box;padding:0px;list-style-position:initial;list-style-image:initial;border-top:none;border-right:1px solid #E7E5DC;border-bottom:none;border-left:none;border-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;"><span style="box-sizing:border-box;margin:0px;padding:0px;border:none;background-color:inherit;">#slaver.conf&nbsp;&nbsp;</span></span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">dbpath=/mongodb/data/slaver&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">logpath=/mongodb/log/slaver.log&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">pidfilepath=/mongodb/slaver.pid&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">directoryperdb=true&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">logappend=true&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">replSet=testrs&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">bind_ip=10.10.148.131&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">port=27017&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">oplogSize=10000&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">fork=true&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">noprealloc=true&nbsp;&nbsp;</span> 
		</li>
	</ol>
</div>
<div class="dp-highlighter bg_plain" style="box-sizing:border-box;padding:1px 0px 0px;position:relative;overflow-y:hidden;overflow-x:auto;font-family:Consolas, &quot;background-color:#E7E5DC;width:851.392px;color:#454545;white-space:normal;margin:18px 0px !important;">
	<div class="bar" style="box-sizing:border-box;margin:0px;padding:0px 0px 0px 45px;">
		<div class="tools" style="box-sizing:border-box;margin:0px;padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;border-right:1px solid #E7E5DC;">
			<b style="box-sizing:border-box;">[plain]</b>&nbsp;<a href="http://blog.csdn.net/luonanqin/article/details/8497860#" class="ViewSource" title="view plain" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#A0A0A0;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:0px;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span class="tracking-ad" data-mod="popu_168" style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;<a href="http://blog.csdn.net/luonanqin/article/details/8497860#" class="CopyToClipboard" title="copy" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#A0A0A0;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:0px;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a> 
			<div style="box-sizing:border-box;margin:0px;padding:0px;position:absolute;left:409px;top:1646px;width:15px;height:16px;z-index:99;">
			</div>
</span><span class="tracking-ad" data-mod="popu_169" style="box-sizing:border-box;margin:0px;padding:0px;"></span> 
		</div>
	</div>
	<ol start="1" style="box-sizing:border-box;padding:0px;list-style-position:initial;list-style-image:initial;border-top:none;border-right:1px solid #E7E5DC;border-bottom:none;border-left:none;border-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;"><span style="box-sizing:border-box;margin:0px;padding:0px;border:none;background-color:inherit;">#arbiter.conf&nbsp;&nbsp;</span></span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">dbpath=/mongodb/data/arbiter&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">logpath=/mongodb/log/arbiter.log&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">pidfilepath=/mongodb/arbiter.pid&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">directoryperdb=true&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">logappend=true&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">replSet=testrs&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">bind_ip=10.10.148.132&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">port=27017&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">oplogSize=10000&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">fork=true&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">noprealloc=true&nbsp;&nbsp;</span> 
		</li>
	</ol>
</div>
<span style="color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">参数解释：</span> 
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	dbpath：数据存放目录
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	logpath：日志存放路径
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	pidfilepath：进程文件，方便停止mongodb
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	directoryperdb：为每一个数据库按照数据库名建立文件夹存放
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	logappend：以追加的方式记录日志
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	replSet：replica set的名字
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	bind_ip：mongodb所绑定的ip地址
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	port：mongodb进程所使用的端口号，默认为27017
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	oplogSize：mongodb操作日志文件的最大大小。单位为Mb，默认为硬盘剩余空间的5%
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	fork：以后台方式运行进程
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	noprealloc：不预先分配存储
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<br />
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	3.启动mongodb
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	进入每个mongodb节点的bin目录下
</p>
<div class="dp-highlighter bg_java" style="box-sizing:border-box;padding:1px 0px 0px;position:relative;overflow-y:hidden;overflow-x:auto;font-family:Consolas, &quot;background-color:#E7E5DC;width:851.392px;color:#454545;white-space:normal;margin:18px 0px !important;">
	<div class="bar" style="box-sizing:border-box;margin:0px;padding:0px 0px 0px 45px;">
		<div class="tools" style="box-sizing:border-box;margin:0px;padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;border-right:1px solid #E7E5DC;">
			<b style="box-sizing:border-box;">[java]</b>&nbsp;<a href="http://blog.csdn.net/luonanqin/article/details/8497860#" class="ViewSource" title="view plain" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#A0A0A0;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:0px;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span class="tracking-ad" data-mod="popu_168" style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;<a href="http://blog.csdn.net/luonanqin/article/details/8497860#" class="CopyToClipboard" title="copy" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#A0A0A0;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:0px;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a> 
			<div style="box-sizing:border-box;margin:0px;padding:0px;position:absolute;left:405px;top:2276px;width:16px;height:16px;z-index:99;">
			</div>
</span><span class="tracking-ad" data-mod="popu_169" style="box-sizing:border-box;margin:0px;padding:0px;"></span> 
		</div>
	</div>
	<ol start="1" class="dp-j" style="box-sizing:border-box;padding:0px;list-style-position:initial;list-style-image:initial;border-top:none;border-right:1px solid #E7E5DC;border-bottom:none;border-left:none;border-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;"><span style="box-sizing:border-box;margin:0px;padding:0px;border:none;background-color:inherit;">./monood&nbsp;-f&nbsp;master.conf&nbsp;&nbsp;</span></span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">./mongod&nbsp;-f&nbsp;slaver.conf&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">./mongod&nbsp;-f&nbsp;arbiter.conf&nbsp;&nbsp;</span> 
		</li>
	</ol>
</div>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	注意配置文件的路径一定要保证正确，可以是相对路径也可以是绝对路径。
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<br />
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	4.配置主，备，仲裁节点
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	可以通过客户端连接mongodb，也可以直接在三个节点中选择一个连接mongodb。
</p>
<div class="dp-highlighter bg_plain" style="box-sizing:border-box;padding:1px 0px 0px;position:relative;overflow-y:hidden;overflow-x:auto;font-family:Consolas, &quot;background-color:#E7E5DC;width:851.392px;color:#454545;white-space:normal;margin:18px 0px !important;">
	<div class="bar" style="box-sizing:border-box;margin:0px;padding:0px 0px 0px 45px;">
		<div class="tools" style="box-sizing:border-box;margin:0px;padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;border-right:1px solid #E7E5DC;">
			<b style="box-sizing:border-box;">[plain]</b>&nbsp;<a href="http://blog.csdn.net/luonanqin/article/details/8497860#" class="ViewSource" title="view plain" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#A0A0A0;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:0px;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span class="tracking-ad" data-mod="popu_168" style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;<a href="http://blog.csdn.net/luonanqin/article/details/8497860#" class="CopyToClipboard" title="copy" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#A0A0A0;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:0px;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a> 
			<div style="box-sizing:border-box;margin:0px;padding:0px;position:absolute;left:409px;top:2489px;width:15px;height:16px;z-index:99;">
			</div>
</span><span class="tracking-ad" data-mod="popu_169" style="box-sizing:border-box;margin:0px;padding:0px;"></span> 
		</div>
	</div>
	<ol start="1" style="box-sizing:border-box;padding:0px;list-style-position:initial;list-style-image:initial;border-top:none;border-right:1px solid #E7E5DC;border-bottom:none;border-left:none;border-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;"><span style="box-sizing:border-box;margin:0px;padding:0px;border:none;background-color:inherit;">./mongo&nbsp;10.10.148.130:27017&nbsp;&nbsp;&nbsp;#ip和port是某个节点的地址&nbsp;&nbsp;</span></span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&gt;use&nbsp;admin&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&gt;cfg={&nbsp;_id:"testrs",&nbsp;members:[&nbsp;{_id:0,host:'10.10.148.130:27017',priority:2},&nbsp;{_id:1,host:'10.10.148.131:27017',priority:1},&nbsp;&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">{_id:2,host:'10.10.148.132:27017',arbiterOnly:true}]&nbsp;};&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&gt;rs.initiate(cfg)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;#使配置生效&nbsp;&nbsp;</span> 
		</li>
	</ol>
</div>
<span style="color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; cfg是可以任意的名字，当然最好不要是mongodb的关键字，conf，config都可以。最外层的_id表示replica set的名字，members里包含的是所有节点的地址以及优先级。优先级最高的即成为主节点，即这里的10.10.148.130:27017。特别注意的是，对于仲裁节点，需要有个特别的配置——arbiterOnly:true。这个千万不能少了，不然主备模式就不能生效。</span> 
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 配置的生效时间根据不同的机器配置会有长有短，配置不错的话基本上十几秒内就能生效，有的配置需要一两分钟。如果生效了，执行rs.status()命令会看到如下信息：
</p>
<div class="dp-highlighter bg_plain" style="box-sizing:border-box;padding:1px 0px 0px;position:relative;overflow-y:hidden;overflow-x:auto;font-family:Consolas, &quot;background-color:#E7E5DC;width:851.392px;color:#454545;white-space:normal;margin:18px 0px !important;">
	<div class="bar" style="box-sizing:border-box;margin:0px;padding:0px 0px 0px 45px;">
		<div class="tools" style="box-sizing:border-box;margin:0px;padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;border-right:1px solid #E7E5DC;">
			<b style="box-sizing:border-box;">[plain]</b>&nbsp;<a href="http://blog.csdn.net/luonanqin/article/details/8497860#" class="ViewSource" title="view plain" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#A0A0A0;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:0px;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span class="tracking-ad" data-mod="popu_168" style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;<a href="http://blog.csdn.net/luonanqin/article/details/8497860#" class="CopyToClipboard" title="copy" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#A0A0A0;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:0px;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a> 
			<div style="box-sizing:border-box;margin:0px;padding:0px;position:absolute;left:409px;top:2779px;width:15px;height:16px;z-index:99;">
			</div>
</span><span class="tracking-ad" data-mod="popu_169" style="box-sizing:border-box;margin:0px;padding:0px;"></span> 
		</div>
	</div>
	<ol start="1" style="box-sizing:border-box;padding:0px;list-style-position:initial;list-style-image:initial;border-top:none;border-right:1px solid #E7E5DC;border-bottom:none;border-left:none;border-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;"><span style="box-sizing:border-box;margin:0px;padding:0px;border:none;background-color:inherit;">{&nbsp;&nbsp;</span></span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"set"&nbsp;:&nbsp;"testrs",&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"date"&nbsp;:&nbsp;ISODate("2013-01-05T02:44:43Z"),&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"myState"&nbsp;:&nbsp;1,&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"members"&nbsp;:&nbsp;[&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"_id"&nbsp;:&nbsp;0,&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"name"&nbsp;:&nbsp;"10.10.148.130:27017",&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"health"&nbsp;:&nbsp;1,&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"state"&nbsp;:&nbsp;1,&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"stateStr"&nbsp;:&nbsp;"PRIMARY",&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"uptime"&nbsp;:&nbsp;200,&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"optime"&nbsp;:&nbsp;Timestamp(1357285565000,&nbsp;1),&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"optimeDate"&nbsp;:&nbsp;ISODate("2013-01-04T07:46:05Z"),&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"self"&nbsp;:&nbsp;true&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;},&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"_id"&nbsp;:&nbsp;1,&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"name"&nbsp;:&nbsp;"10.10.148.131:27017",&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"health"&nbsp;:&nbsp;1,&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"state"&nbsp;:&nbsp;2,&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"stateStr"&nbsp;:&nbsp;"SECONDARY",&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"uptime"&nbsp;:&nbsp;200,&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"optime"&nbsp;:&nbsp;Timestamp(1357285565000,&nbsp;1),&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"optimeDate"&nbsp;:&nbsp;ISODate("2013-01-04T07:46:05Z"),&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"lastHeartbeat"&nbsp;:&nbsp;ISODate("2013-01-05T02:44:42Z"),&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"pingMs"&nbsp;:&nbsp;0&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;},&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;{&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"_id"&nbsp;:&nbsp;2,&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"name"&nbsp;:&nbsp;"10.10.148.132:27017",&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"health"&nbsp;:&nbsp;1,&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"state"&nbsp;:&nbsp;7,&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"stateStr"&nbsp;:&nbsp;"ARBITER",&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"uptime"&nbsp;:&nbsp;200,&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"lastHeartbeat"&nbsp;:&nbsp;ISODate("2013-01-05T02:44:42Z"),&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"pingMs"&nbsp;:&nbsp;0&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;],&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"ok"&nbsp;:&nbsp;1&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">}&nbsp;&nbsp;</span> 
		</li>
	</ol>
</div>
<span style="color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">如果配置正在生效，其中会包含如下信息：</span> 
<div class="dp-highlighter bg_plain" style="box-sizing:border-box;padding:1px 0px 0px;position:relative;overflow-y:hidden;overflow-x:auto;font-family:Consolas, &quot;background-color:#E7E5DC;width:851.392px;color:#454545;white-space:normal;margin:18px 0px !important;">
	<div class="bar" style="box-sizing:border-box;margin:0px;padding:0px 0px 0px 45px;">
		<div class="tools" style="box-sizing:border-box;margin:0px;padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;border-right:1px solid #E7E5DC;">
			<b style="box-sizing:border-box;">[plain]</b>&nbsp;<a href="http://blog.csdn.net/luonanqin/article/details/8497860#" class="ViewSource" title="view plain" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#A0A0A0;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:0px;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span class="tracking-ad" data-mod="popu_168" style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;<a href="http://blog.csdn.net/luonanqin/article/details/8497860#" class="CopyToClipboard" title="copy" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#A0A0A0;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:0px;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a> 
			<div style="box-sizing:border-box;margin:0px;padding:0px;position:absolute;left:409px;top:3578px;width:15px;height:16px;z-index:99;">
			</div>
</span><span class="tracking-ad" data-mod="popu_169" style="box-sizing:border-box;margin:0px;padding:0px;"></span> 
		</div>
	</div>
	<ol start="1" style="box-sizing:border-box;padding:0px;list-style-position:initial;list-style-image:initial;border-top:none;border-right:1px solid #E7E5DC;border-bottom:none;border-left:none;border-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;"><span style="box-sizing:border-box;margin:0px;padding:0px;border:none;background-color:inherit;">"stateStr"&nbsp;:&nbsp;"RECOVERING"&nbsp;&nbsp;</span></span> 
		</li>
	</ol>
</div>
<br style="box-sizing:border-box;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">同时可以查看对应节点的日志，发现正在等待别的节点生效或者正在分配数据文件。</span> 
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 现在基本上已经完成了集群的所有搭建工作。至于测试工作，可以留给大家自己试试。一个是往主节点插入数据，能从备节点查到之前插入的数据（查询备节点可能会遇到某个问题，可以自己去网上查查看）。二是停掉主节点，备节点能变成主节点提供服务。三是恢复主节点，备节点也能恢复其备的角色，而不是继续充当主的角色。二和三都可以通过rs.status()命令实时查看集群的变化。
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<br />
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	Sharding
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	和Replica Set类似，都需要一个仲裁节点，但是Sharding还需要配置节点和路由节点。就三种集群搭建方式来说，这种是最复杂的。部署图如下：
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<img src="http://img.my.csdn.net/uploads/201301/13/1358091861_1772.png" alt="" height="369" width="401" style="box-sizing:border-box;vertical-align:middle;outline:0px;max-width:100%;" /> 
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	1.启动数据节点
</p>
<div class="dp-highlighter bg_plain" style="box-sizing:border-box;padding:1px 0px 0px;position:relative;overflow-y:hidden;overflow-x:auto;font-family:Consolas, &quot;background-color:#E7E5DC;width:851.392px;color:#454545;white-space:normal;margin:18px 0px !important;">
	<div class="bar" style="box-sizing:border-box;margin:0px;padding:0px 0px 0px 45px;">
		<div class="tools" style="box-sizing:border-box;margin:0px;padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;border-right:1px solid #E7E5DC;">
			<b style="box-sizing:border-box;">[plain]</b>&nbsp;<a href="http://blog.csdn.net/luonanqin/article/details/8497860#" class="ViewSource" title="view plain" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#A0A0A0;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:0px;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span class="tracking-ad" data-mod="popu_168" style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;<a href="http://blog.csdn.net/luonanqin/article/details/8497860#" class="CopyToClipboard" title="copy" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#A0A0A0;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:0px;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a> 
			<div style="box-sizing:border-box;margin:0px;padding:0px;position:absolute;left:409px;top:4291px;width:15px;height:16px;z-index:99;">
			</div>
</span><span class="tracking-ad" data-mod="popu_169" style="box-sizing:border-box;margin:0px;padding:0px;"></span> 
		</div>
	</div>
	<ol start="1" style="box-sizing:border-box;padding:0px;list-style-position:initial;list-style-image:initial;border-top:none;border-right:1px solid #E7E5DC;border-bottom:none;border-left:none;border-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;"><span style="box-sizing:border-box;margin:0px;padding:0px;border:none;background-color:inherit;">./mongod&nbsp;--fork&nbsp;--dbpath&nbsp;../data/set1/&nbsp;--logpath&nbsp;../log/set1.log&nbsp;--replSet&nbsp;test&nbsp;#192.168.4.43&nbsp;&nbsp;</span></span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">./mongod&nbsp;--fork&nbsp;--dbpath&nbsp;../data/set2/&nbsp;--logpath&nbsp;../log/set2.log&nbsp;--replSet&nbsp;test&nbsp;#192.168.4.44&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">./mongod&nbsp;--fork&nbsp;--dbpath&nbsp;../data/set3/&nbsp;--logpath&nbsp;../log/set3.log&nbsp;--replSet&nbsp;test&nbsp;#192.168.4.45&nbsp;决策&nbsp;不存储数据&nbsp;&nbsp;</span> 
		</li>
	</ol>
</div>
<br style="box-sizing:border-box;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">2.启动配置节点</span> 
<div class="dp-highlighter bg_plain" style="box-sizing:border-box;padding:1px 0px 0px;position:relative;overflow-y:hidden;overflow-x:auto;font-family:Consolas, &quot;background-color:#E7E5DC;width:851.392px;color:#454545;white-space:normal;margin:18px 0px !important;">
	<div class="bar" style="box-sizing:border-box;margin:0px;padding:0px 0px 0px 45px;">
		<div class="tools" style="box-sizing:border-box;margin:0px;padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;border-right:1px solid #E7E5DC;">
			<b style="box-sizing:border-box;">[plain]</b>&nbsp;<a href="http://blog.csdn.net/luonanqin/article/details/8497860#" class="ViewSource" title="view plain" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#A0A0A0;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:0px;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span class="tracking-ad" data-mod="popu_168" style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;<a href="http://blog.csdn.net/luonanqin/article/details/8497860#" class="CopyToClipboard" title="copy" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#A0A0A0;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:0px;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a> 
			<div style="box-sizing:border-box;margin:0px;padding:0px;position:absolute;left:409px;top:4458px;width:15px;height:16px;z-index:99;">
			</div>
</span><span class="tracking-ad" data-mod="popu_169" style="box-sizing:border-box;margin:0px;padding:0px;"></span> 
		</div>
	</div>
	<ol start="1" style="box-sizing:border-box;padding:0px;list-style-position:initial;list-style-image:initial;border-top:none;border-right:1px solid #E7E5DC;border-bottom:none;border-left:none;border-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;"><span style="box-sizing:border-box;margin:0px;padding:0px;border:none;background-color:inherit;">./mongod&nbsp;--configsvr&nbsp;--dbpath&nbsp;../config/set1/&nbsp;--port&nbsp;20001&nbsp;--fork&nbsp;--logpath&nbsp;../log/conf1.log&nbsp;#192.168.4.30&nbsp;&nbsp;</span></span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">./mongod&nbsp;--configsvr&nbsp;--dbpath&nbsp;../config/set2/&nbsp;--port&nbsp;20002&nbsp;--fork&nbsp;--logpath&nbsp;../log/conf2.log&nbsp;#192.168.4.31&nbsp;&nbsp;</span> 
		</li>
	</ol>
</div>
<br style="box-sizing:border-box;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">3.启动路由节点</span> 
<div class="dp-highlighter bg_plain" style="box-sizing:border-box;padding:1px 0px 0px;position:relative;overflow-y:hidden;overflow-x:auto;font-family:Consolas, &quot;background-color:#E7E5DC;width:851.392px;color:#454545;white-space:normal;margin:18px 0px !important;">
	<div class="bar" style="box-sizing:border-box;margin:0px;padding:0px 0px 0px 45px;">
		<div class="tools" style="box-sizing:border-box;margin:0px;padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;border-right:1px solid #E7E5DC;">
			<b style="box-sizing:border-box;">[plain]</b>&nbsp;<a href="http://blog.csdn.net/luonanqin/article/details/8497860#" class="ViewSource" title="view plain" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#A0A0A0;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:0px;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span class="tracking-ad" data-mod="popu_168" style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;<a href="http://blog.csdn.net/luonanqin/article/details/8497860#" class="CopyToClipboard" title="copy" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#A0A0A0;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:0px;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a> 
			<div style="box-sizing:border-box;margin:0px;padding:0px;position:absolute;left:409px;top:4607px;width:15px;height:16px;z-index:99;">
			</div>
</span><span class="tracking-ad" data-mod="popu_169" style="box-sizing:border-box;margin:0px;padding:0px;"></span> 
		</div>
	</div>
	<ol start="1" style="box-sizing:border-box;padding:0px;list-style-position:initial;list-style-image:initial;border-top:none;border-right:1px solid #E7E5DC;border-bottom:none;border-left:none;border-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;"><span style="box-sizing:border-box;margin:0px;padding:0px;border:none;background-color:inherit;">./mongos&nbsp;--configdb&nbsp;192.168.4.30:20001,192.168.4.31:20002&nbsp;--port&nbsp;27017&nbsp;--fork&nbsp;--logpath&nbsp;../log/root.log&nbsp;#192.168.4.29&nbsp;&nbsp;</span></span> 
		</li>
	</ol>
</div>
<br style="box-sizing:border-box;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 这里我们没有用配置文件的方式启动，其中的参数意义大家应该都明白。一般来说一个数据节点对应一个配置节点，仲裁节点则不需要对应的配置节点。注意在启动路由节点时，要将配置节点地址写入到启动命令里。</span> 
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<br />
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	4.配置Replica Set
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 这里可能会有点奇怪为什么Sharding会需要配置Replica Set。其实想想也能明白，多个节点的数据肯定是相关联的，如果不配一个Replica Set，怎么标识是同一个集群的呢。这也是人家mongodb的规定，咱们还是遵守吧。配置方式和之前所说的一样，定一个cfg，然后初始化配置。
</p>
<div class="dp-highlighter bg_plain" style="box-sizing:border-box;padding:1px 0px 0px;position:relative;overflow-y:hidden;overflow-x:auto;font-family:Consolas, &quot;background-color:#E7E5DC;width:851.392px;color:#454545;white-space:normal;margin:18px 0px !important;">
	<div class="bar" style="box-sizing:border-box;margin:0px;padding:0px 0px 0px 45px;">
		<div class="tools" style="box-sizing:border-box;margin:0px;padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;border-right:1px solid #E7E5DC;">
			<b style="box-sizing:border-box;">[plain]</b>&nbsp;<a href="http://blog.csdn.net/luonanqin/article/details/8497860#" class="ViewSource" title="view plain" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#A0A0A0;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:0px;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span class="tracking-ad" data-mod="popu_168" style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;<a href="http://blog.csdn.net/luonanqin/article/details/8497860#" class="CopyToClipboard" title="copy" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#A0A0A0;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:0px;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a> 
			<div style="box-sizing:border-box;margin:0px;padding:0px;position:absolute;left:409px;top:4880px;width:15px;height:16px;z-index:99;">
			</div>
</span><span class="tracking-ad" data-mod="popu_169" style="box-sizing:border-box;margin:0px;padding:0px;"></span> 
		</div>
	</div>
	<ol start="1" style="box-sizing:border-box;padding:0px;list-style-position:initial;list-style-image:initial;border-top:none;border-right:1px solid #E7E5DC;border-bottom:none;border-left:none;border-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;"><span style="box-sizing:border-box;margin:0px;padding:0px;border:none;background-color:inherit;">./mongo&nbsp;192.168.4.43:27017&nbsp;&nbsp;&nbsp;#ip和port是某个节点的地址&nbsp;&nbsp;</span></span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&gt;use&nbsp;admin&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&gt;cfg={&nbsp;_id:"testrs",&nbsp;members:[&nbsp;{_id:0,host:'192.168.4.43:27017',priority:2},&nbsp;{_id:1,host:'192.168.4.44:27017',priority:1},&nbsp;&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">{_id:2,host:'192.168.4.45:27017',arbiterOnly:true}]&nbsp;};&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&gt;rs.initiate(cfg)&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;#使配置生效&nbsp;&nbsp;</span> 
		</li>
	</ol>
</div>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<br />
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	5.配置Sharding
</p>
<div class="dp-highlighter bg_plain" style="box-sizing:border-box;padding:1px 0px 0px;position:relative;overflow-y:hidden;overflow-x:auto;font-family:Consolas, &quot;background-color:#E7E5DC;width:851.392px;color:#454545;white-space:normal;margin:18px 0px !important;">
	<div class="bar" style="box-sizing:border-box;margin:0px;padding:0px 0px 0px 45px;">
		<div class="tools" style="box-sizing:border-box;margin:0px;padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;border-right:1px solid #E7E5DC;">
			<b style="box-sizing:border-box;">[plain]</b>&nbsp;<a href="http://blog.csdn.net/luonanqin/article/details/8497860#" class="ViewSource" title="view plain" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#A0A0A0;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:0px;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span class="tracking-ad" data-mod="popu_168" style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;<a href="http://blog.csdn.net/luonanqin/article/details/8497860#" class="CopyToClipboard" title="copy" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#A0A0A0;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:0px;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a> 
			<div style="box-sizing:border-box;margin:0px;padding:0px;position:absolute;left:409px;top:5099px;width:15px;height:16px;z-index:99;">
			</div>
</span><span class="tracking-ad" data-mod="popu_169" style="box-sizing:border-box;margin:0px;padding:0px;"></span> 
		</div>
	</div>
	<ol start="1" style="box-sizing:border-box;padding:0px;list-style-position:initial;list-style-image:initial;border-top:none;border-right:1px solid #E7E5DC;border-bottom:none;border-left:none;border-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;"><span style="box-sizing:border-box;margin:0px;padding:0px;border:none;background-color:inherit;">./mongo&nbsp;192.168.4.29:27017&nbsp;&nbsp;&nbsp;#这里必须连接路由节点&nbsp;&nbsp;</span></span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&gt;sh.addShard("test/192.168.4.43:27017")&nbsp;#test表示replica&nbsp;set的名字&nbsp;当把主节点添加到shard以后，会自动找到set里的主，备，决策节点&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&gt;db.runCommand({enableSharding:"diameter_test"})&nbsp;&nbsp;&nbsp;&nbsp;#diameter_test&nbsp;is&nbsp;database&nbsp;name&nbsp;&nbsp;</span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&gt;db.runCommand(&nbsp;{&nbsp;shardCollection:&nbsp;"diameter_test.dcca_dccr_test",key:{"__avpSessionId":1}})&nbsp;&nbsp;&nbsp;</span> 
		</li>
	</ol>
</div>
<span style="color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 第一个命令很容易理解，第二个命令是对需要进行Sharding的数据库进行配置，第三个命令是对需要进行Sharding的Collection进行配置，这里的dcca_dccr_test即为Collection的名字。另外还有个key，这个是比较关键的东西，对于查询效率会有很大的影响，具体可以查看</span><a href="http://docs.mongodb.org/manual/core/sharding/#sharding-shard-key" target="_blank" style="box-sizing:border-box;background:#FFFFFF;color:#CA0C16;text-decoration-line:none;margin:0px;padding:0px;outline:0px;font-family:&quot;font-size:16px;white-space:normal;">Shard Key Overview</a><span style="color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;"></span> 
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 到这里Sharding也已经搭建完成了，以上只是最简单的搭建方式，其中某些配置仍然使用的是默认配置。如果设置不当，会导致效率异常低下，所以建议大家多看看官方文档再进行默认配置的修改。
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<br />
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	Master-Slaver
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	这个是最简答的集群搭建，不过准确说也不能算是集群，只能说是主备。并且官方已经不推荐这种方式，所以在这里只是简单的介绍下吧，搭建方式也相对简单。
</p>
<div class="dp-highlighter bg_plain" style="box-sizing:border-box;padding:1px 0px 0px;position:relative;overflow-y:hidden;overflow-x:auto;font-family:Consolas, &quot;background-color:#E7E5DC;width:851.392px;color:#454545;white-space:normal;margin:18px 0px !important;">
	<div class="bar" style="box-sizing:border-box;margin:0px;padding:0px 0px 0px 45px;">
		<div class="tools" style="box-sizing:border-box;margin:0px;padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;border-right:1px solid #E7E5DC;">
			<b style="box-sizing:border-box;">[plain]</b>&nbsp;<a href="http://blog.csdn.net/luonanqin/article/details/8497860#" class="ViewSource" title="view plain" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#A0A0A0;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:0px;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span class="tracking-ad" data-mod="popu_168" style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;<a href="http://blog.csdn.net/luonanqin/article/details/8497860#" class="CopyToClipboard" title="copy" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#A0A0A0;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:0px;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a> 
			<div style="box-sizing:border-box;margin:0px;padding:0px;position:absolute;left:409px;top:5465px;width:15px;height:16px;z-index:99;">
			</div>
</span><span class="tracking-ad" data-mod="popu_169" style="box-sizing:border-box;margin:0px;padding:0px;"></span> 
		</div>
	</div>
	<ol start="1" style="box-sizing:border-box;padding:0px;list-style-position:initial;list-style-image:initial;border-top:none;border-right:1px solid #E7E5DC;border-bottom:none;border-left:none;border-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;"><span style="box-sizing:border-box;margin:0px;padding:0px;border:none;background-color:inherit;">./mongod&nbsp;--master&nbsp;--dbpath&nbsp;/data/masterdb/&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;#主节点&nbsp;&nbsp;</span></span> 
		</li>
		<li class="" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;background-color:#F8F8F8;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">&nbsp;&nbsp;</span> 
		</li>
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#000000;background-color:inherit;">./mongod&nbsp;--slave&nbsp;--source&nbsp;&lt;masterip:masterport&gt;&nbsp;--dbpath&nbsp;/data/slavedb/&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;备节点&nbsp;&nbsp;</span> 
		</li>
	</ol>
</div>
<span style="color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 基本上只要在主节点和备节点上分别执行这两条命令，Master-Slaver就算搭建完成了。我没有试过主节点挂掉后备节点是否能变成主节点，不过既然已经不推荐了，大家就没必要去使用了。</span> 
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<br />
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 以上三种集群搭建方式首选Replica Set，只有真的是大数据，Sharding才能显现威力，毕竟备节点同步数据是需要时间的。Sharding可以将多片数据集中到路由节点上进行一些对比，然后将数据返回给客户端，但是效率还是比较低的说。
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 我自己有测试过，不过具体的机器配置已经不记得了。Replica Set的ips在数据达到1400w条时基本能达到1000左右，而Sharding在300w时已经下降到500ips了，两者的单位数据大小大概是10kb。大家在应用的时候还是多多做下性能测试，毕竟不像Redis有benchmark。
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Mongodb现在用的还是比较多的，但是个人觉得配置太多了。。。。我看官网都看了好多天，才把集群搭建的配置和注意要点弄明白。而且用过的人应该知道mongodb吃内存的问题，解决办法只能通过ulimit来控制内存使用量，但是如果控制不好的话，mongodb会挂掉。。。
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<br />
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	过段时间我会写一篇关于项目里使用mongodb所涉及到的具体业务，各位有兴趣可以关注下。
</p>
<p>
	<br />
</p>