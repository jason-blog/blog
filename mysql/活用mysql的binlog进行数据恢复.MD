<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	http://blog.csdn.net/a7442358/article/details/47355515&nbsp;&nbsp;
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	在日常操作mysql的过程中可能会遇到因为操作失误导致数据丢失，由于操作之前没有进行备份，而最近备份的文件时间又早，很可能导致备份之后到现在这段时间数据的丢失，那么如何应对这种突发状况？其实mysql已经给我们提供了应对这种情况的功能，只不过这项功能默认没有开启，平时又用不到，因此没有对它进行了解，下面我们就来认识一下它吧。
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	&nbsp; &nbsp;&nbsp;<strong style="box-sizing:border-box;">什么是binlog？</strong> 
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	&nbsp; &nbsp; binlog，也称为二进制日志，<span style="box-sizing:border-box;margin:0px;padding:0px;text-align:justify;">记录对数据发生或潜在发生更改的SQL语句，并以二进制的形式保存在磁盘中，<span style="box-sizing:border-box;margin:0px;padding:0px;">可以用来查看数据库的变更历史（具体的时间点所有的SQL操作）、数据库增量备份和恢复（增量备份和基于时间点的恢复）、Mysql的复制（主主数据库的复制、主从数据库的复制）。</span></span> 
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;text-align:justify;"><span style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp; &nbsp;&nbsp;<strong style="box-sizing:border-box;">如何开启binlog？</strong></span></span> 
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;text-align:justify;">&nbsp; &nbsp; 首先我们可以进入mysql输入命令</span> 
</p>
<div class="dp-highlighter bg_sql" style="box-sizing:border-box;padding:1px 0px 0px;font-family:Consolas, &quot;background-color:#E7E5DC;width:851.392px;overflow-x:auto;overflow-y:hidden;position:relative;color:#454545;white-space:normal;margin:18px 0px !important;">
	<div class="bar" style="box-sizing:border-box;margin:0px;padding:0px 0px 0px 45px;">
		<div class="tools" style="box-sizing:border-box;margin:0px;padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;border-right:1px solid #E7E5DC;">
			<b style="box-sizing:border-box;">[sql]</b>&nbsp;<a href="http://blog.csdn.net/a7442358/article/details/47355515#" class="ViewSource" title="view plain" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#CA0C16;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:none;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span class="tracking-ad" data-mod="popu_168" style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;<a href="http://blog.csdn.net/a7442358/article/details/47355515#" class="CopyToClipboard" title="copy" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#CA0C16;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:none;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a> 
			<div style="box-sizing:border-box;margin:0px;padding:0px;position:absolute;left:396px;top:503px;width:16px;height:16px;z-index:99;">
			</div>
</span><span class="tracking-ad" data-mod="popu_169" style="box-sizing:border-box;margin:0px;padding:0px;"></span> 
		</div>
	</div>
	<ol start="1" class="dp-sql" style="box-sizing:border-box;padding:0px;list-style-position:initial;list-style-image:initial;border-top:none;border-right:1px solid #E7E5DC;border-bottom:none;border-left:none;border-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span style="box-sizing:border-box;margin:0px;padding:0px;border:none;background-color:inherit;">show&nbsp;variables&nbsp;</span><span class="op" style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#808080;background-color:inherit;">like</span><span style="box-sizing:border-box;margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;</span><span class="string" style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">'%bin%'</span><span style="box-sizing:border-box;margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;&nbsp;</span></span> 
		</li>
	</ol>
</div>
<span style="color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">我们可以通过这个命令来查询关于binlog相关的设置，其中有一个log_bin选项，如果为off，那么证明我们的binlog没有开启，如果为on证明我们的binlog已经开启，开启binlog的方法很简单，只需要打开mysql的配置文件my.ini（也可能是my.cnf），找到log-bin，去掉前面的#号，如果没有该选项，则可以手动添加。</span> 
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;text-align:justify;"><span style="box-sizing:border-box;margin:0px;padding:0px;"></span></span> 
</p>
<div class="dp-highlighter bg_sql" style="box-sizing:border-box;padding:1px 0px 0px;font-family:Consolas, &quot;background-color:#E7E5DC;width:851.392px;overflow-x:auto;overflow-y:hidden;position:relative;color:#454545;white-space:normal;margin:18px 0px !important;">
	<div class="bar" style="box-sizing:border-box;margin:0px;padding:0px 0px 0px 45px;">
		<div class="tools" style="box-sizing:border-box;margin:0px;padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;border-right:1px solid #E7E5DC;">
			<b style="box-sizing:border-box;">[sql]</b>&nbsp;<a href="http://blog.csdn.net/a7442358/article/details/47355515#" class="ViewSource" title="view plain" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#CA0C16;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:none;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span class="tracking-ad" data-mod="popu_168" style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;<a href="http://blog.csdn.net/a7442358/article/details/47355515#" class="CopyToClipboard" title="copy" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#CA0C16;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:none;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a> 
			<div style="box-sizing:border-box;margin:0px;padding:0px;position:absolute;left:396px;top:659px;width:16px;height:16px;z-index:99;">
			</div>
</span><span class="tracking-ad" data-mod="popu_169" style="box-sizing:border-box;margin:0px;padding:0px;"></span> 
		</div>
	</div>
	<ol start="1" class="dp-sql" style="box-sizing:border-box;padding:0px;list-style-position:initial;list-style-image:initial;border-top:none;border-right:1px solid #E7E5DC;border-bottom:none;border-left:none;border-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span style="box-sizing:border-box;margin:0px;padding:0px;border:none;background-color:inherit;">log-bin=mysql-bin&nbsp;&nbsp;</span></span> 
		</li>
	</ol>
</div>
<span style="color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">其中mysql-bin就是日志文件的名称了，日志文件的名称和路径都可以自定义，如果不配置路径和名称，那么该文件会出现在mysql/data目录下，名称为mysql-bin.xxxxxx。</span><br style="box-sizing:border-box;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;" />
<br style="box-sizing:border-box;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;" />
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;text-align:center;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;text-align:justify;"><img src="http://img.blog.csdn.net/20150808103545175?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center" alt="" style="box-sizing:border-box;vertical-align:middle;outline:none;max-width:100%;" /></span> 
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;text-align:justify;">&nbsp; &nbsp; 添加完成后重启mysql，我们就会在mysql/data目录下找到binlog日志文件了，首次使用binlog的时候会出现两个文件，一个是mysql-bin.000001，一个是mysql-bin.index，其中，000001结尾的文件就是我们需要的日志文件，它包含了我们数据库的所有增，改，删操作（查询操作不做记录），以index结尾的文件是索引文件，包含了所有的以000xxx结尾的日志文件。</span> 
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;text-align:justify;">&nbsp; &nbsp; 开启binlog后mysql会自动为了记录以后增，改，删操作，关于备份操作无需我们手动操作，我们只要在需要恢复数据的时候查找对应的数据即可，由于binlog存储的格式为二进制，因此我们无法直接使用，需要借助mysql提供的工具mysqlbinlog（mysqlbinlog在mysql安装目录下的bin目录下）。初次接触一个命令不知道如何使用的时候，我们可以通过帮助命令查看它如何使用</span> 
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;text-align:justify;"><span style="box-sizing:border-box;margin:0px;padding:0px;"></span></span> 
</p>
<div class="dp-highlighter bg_sql" style="box-sizing:border-box;padding:1px 0px 0px;font-family:Consolas, &quot;background-color:#E7E5DC;width:851.392px;overflow-x:auto;overflow-y:hidden;position:relative;color:#454545;white-space:normal;margin:18px 0px !important;">
	<div class="bar" style="box-sizing:border-box;margin:0px;padding:0px 0px 0px 45px;">
		<div class="tools" style="box-sizing:border-box;margin:0px;padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;border-right:1px solid #E7E5DC;">
			<b style="box-sizing:border-box;">[sql]</b>&nbsp;<a href="http://blog.csdn.net/a7442358/article/details/47355515#" class="ViewSource" title="view plain" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#CA0C16;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:none;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span class="tracking-ad" data-mod="popu_168" style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;<a href="http://blog.csdn.net/a7442358/article/details/47355515#" class="CopyToClipboard" title="copy" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#CA0C16;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:none;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a> 
			<div style="box-sizing:border-box;margin:0px;padding:0px;position:absolute;left:396px;top:1394px;width:16px;height:16px;z-index:99;">
			</div>
</span><span class="tracking-ad" data-mod="popu_169" style="box-sizing:border-box;margin:0px;padding:0px;"></span> 
		</div>
	</div>
	<ol start="1" class="dp-sql" style="box-sizing:border-box;padding:0px;list-style-position:initial;list-style-image:initial;border-top:none;border-right:1px solid #E7E5DC;border-bottom:none;border-left:none;border-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span style="box-sizing:border-box;margin:0px;padding:0px;border:none;background-color:inherit;">mysqlbinlog&nbsp;</span><span class="comment" style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#008200;background-color:inherit;">--help</span><span style="box-sizing:border-box;margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;&nbsp;</span></span> 
		</li>
	</ol>
</div>
<span style="color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">通过该命令我们可以了解到mysqlbinlog可以附带哪些参数，不同的参数对应什么状况。</span> 
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;text-align:justify;"><span style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp; &nbsp;<strong style="box-sizing:border-box;">如何使用mysqlbinlog查询操作记录？</strong></span></span> 
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;text-align:justify;"><strong style="box-sizing:border-box;">&nbsp; &nbsp;</strong>1.读取所有数据库的操作</span> 
</p>
<div class="dp-highlighter bg_sql" style="box-sizing:border-box;padding:1px 0px 0px;font-family:Consolas, &quot;background-color:#E7E5DC;width:851.392px;overflow-x:auto;overflow-y:hidden;position:relative;color:#454545;white-space:normal;margin:18px 0px !important;">
	<div class="bar" style="box-sizing:border-box;margin:0px;padding:0px 0px 0px 45px;">
		<div class="tools" style="box-sizing:border-box;margin:0px;padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;border-right:1px solid #E7E5DC;">
			<b style="box-sizing:border-box;">[sql]</b>&nbsp;<a href="http://blog.csdn.net/a7442358/article/details/47355515#" class="ViewSource" title="view plain" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#CA0C16;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:none;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span class="tracking-ad" data-mod="popu_168" style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;<a href="http://blog.csdn.net/a7442358/article/details/47355515#" class="CopyToClipboard" title="copy" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#CA0C16;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:none;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a> 
			<div style="box-sizing:border-box;margin:0px;padding:0px;position:absolute;left:396px;top:1549px;width:16px;height:16px;z-index:99;">
			</div>
</span><span class="tracking-ad" data-mod="popu_169" style="box-sizing:border-box;margin:0px;padding:0px;"></span> 
		</div>
	</div>
	<ol start="1" class="dp-sql" style="box-sizing:border-box;padding:0px;list-style-position:initial;list-style-image:initial;border-top:none;border-right:1px solid #E7E5DC;border-bottom:none;border-left:none;border-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span style="box-sizing:border-box;margin:0px;padding:0px;border:none;background-color:inherit;">mysqlbinlog&nbsp;../data/mysql-bin.000001&nbsp;&nbsp;</span></span> 
		</li>
	</ol>
</div>
<span style="color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">通过该命令，我们可以看到该日志文件中记录的所有数据库的增，该，删操作。</span> 
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;text-align:justify;">&nbsp; &nbsp; 2.查询指定数据库的操作</span> 
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;text-align:justify;"><span style="box-sizing:border-box;margin:0px;padding:0px;"></span></span> 
</p>
<div class="dp-highlighter bg_sql" style="box-sizing:border-box;padding:1px 0px 0px;font-family:Consolas, &quot;background-color:#E7E5DC;width:851.392px;overflow-x:auto;overflow-y:hidden;position:relative;color:#454545;white-space:normal;margin:18px 0px !important;">
	<div class="bar" style="box-sizing:border-box;margin:0px;padding:0px 0px 0px 45px;">
		<div class="tools" style="box-sizing:border-box;margin:0px;padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;border-right:1px solid #E7E5DC;">
			<b style="box-sizing:border-box;">[sql]</b>&nbsp;<a href="http://blog.csdn.net/a7442358/article/details/47355515#" class="ViewSource" title="view plain" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#CA0C16;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:none;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span class="tracking-ad" data-mod="popu_168" style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;<a href="http://blog.csdn.net/a7442358/article/details/47355515#" class="CopyToClipboard" title="copy" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#CA0C16;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:none;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a> 
			<div style="box-sizing:border-box;margin:0px;padding:0px;position:absolute;left:396px;top:1681px;width:16px;height:16px;z-index:99;">
			</div>
</span><span class="tracking-ad" data-mod="popu_169" style="box-sizing:border-box;margin:0px;padding:0px;"></span> 
		</div>
	</div>
	<ol start="1" class="dp-sql" style="box-sizing:border-box;padding:0px;list-style-position:initial;list-style-image:initial;border-top:none;border-right:1px solid #E7E5DC;border-bottom:none;border-left:none;border-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span style="box-sizing:border-box;margin:0px;padding:0px;border:none;background-color:inherit;">mysqlbinlog&nbsp;</span><span class="comment" style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#008200;background-color:inherit;">--database=test&nbsp;../data/mysql-bin.000001</span><span style="box-sizing:border-box;margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;&nbsp;</span></span> 
		</li>
	</ol>
</div>
<span style="color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">通过该命令，我们可以查询数据库名称为test的增，该，删操作</span> 
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;text-align:justify;">&nbsp; &nbsp; 3.查询指定位置的操作</span> 
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;text-align:justify;">&nbsp; &nbsp; binlog每次进行记录的时候都会为其标注一个position，用于标识该操作所在的位置，与之相关的参数为--start-position（开始位置）和--stop-position（结束位置），我们可以通过position进行指定操作的查询。</span> 
</p>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;text-align:justify;">
	&nbsp; &nbsp; &nbsp;<strong style="box-sizing:border-box;">如何获取position的值？</strong> 
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;text-align:justify;">
	<strong style="box-sizing:border-box;"><img src="http://img.blog.csdn.net/20150808114602395?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center" alt="" style="box-sizing:border-box;vertical-align:middle;outline:none;max-width:100%;" /><br style="box-sizing:border-box;" />
</strong> 
</div>
<div style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;text-align:justify;">
	只需要在mysql中使用show binlog events即可，每一行都记录了一条操作，其中Pos就是该操作的start-position，End_log_pos就是stop-position。我们如果需要查询上述图片中的操作，可以使用以下语句：
</div>
<span style="box-sizing:border-box;margin:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;text-align:justify;"><span style="box-sizing:border-box;margin:0px;padding:0px;"></span></span> 
<div class="dp-highlighter bg_sql" style="box-sizing:border-box;padding:1px 0px 0px;font-family:Consolas, &quot;background-color:#E7E5DC;width:851.392px;overflow-x:auto;overflow-y:hidden;position:relative;color:#454545;white-space:normal;margin:18px 0px !important;">
	<div class="bar" style="box-sizing:border-box;margin:0px;padding:0px 0px 0px 45px;">
		<div class="tools" style="box-sizing:border-box;margin:0px;padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;border-right:1px solid #E7E5DC;">
			<b style="box-sizing:border-box;">[sql]</b>&nbsp;<a href="http://blog.csdn.net/a7442358/article/details/47355515#" class="ViewSource" title="view plain" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#CA0C16;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:none;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span class="tracking-ad" data-mod="popu_168" style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;<a href="http://blog.csdn.net/a7442358/article/details/47355515#" class="CopyToClipboard" title="copy" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#CA0C16;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:none;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a> 
			<div style="box-sizing:border-box;margin:0px;padding:0px;position:absolute;left:396px;top:2212px;width:16px;height:16px;z-index:99;">
			</div>
</span><span class="tracking-ad" data-mod="popu_169" style="box-sizing:border-box;margin:0px;padding:0px;"></span> 
		</div>
	</div>
	<ol start="1" class="dp-sql" style="box-sizing:border-box;padding:0px;list-style-position:initial;list-style-image:initial;border-top:none;border-right:1px solid #E7E5DC;border-bottom:none;border-left:none;border-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span style="box-sizing:border-box;margin:0px;padding:0px;border:none;background-color:inherit;">mysqlbinlog&nbsp;</span><span class="comment" style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#008200;background-color:inherit;">--start-position=4&nbsp;--stop-position=98&nbsp;../data/mysql-bin.000001</span><span style="box-sizing:border-box;margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;&nbsp;</span></span> 
		</li>
	</ol>
</div>
<pre style="box-sizing:border-box;font-family:Monaco, Menlo, Consolas, &quot;font-size:13px;white-space:pre-wrap;padding:0px;margin-top:0px;margin-bottom:0px;line-height:1.42857;color:#333333;word-break:break-all;word-wrap:break-word;background-color:#F5F5F5;border:1px solid #CCCCCC;border-radius:4px;"></pre>
<pre style="box-sizing:border-box;font-family:Monaco, Menlo, Consolas, &quot;font-size:13px;white-space:pre-wrap;padding:0px;margin-top:0px;margin-bottom:0px;line-height:1.42857;color:#333333;word-break:break-all;word-wrap:break-word;background-color:#F5F5F5;border:1px solid #CCCCCC;border-radius:4px;"></pre>
<span style="color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">&nbsp; &nbsp; 4.查询指定时间的操作</span> 
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;text-align:justify;">&nbsp; &nbsp; 除了有位置标识外，binlog还有时间标识，参数为--start-datetime（开始时间）和--stop-datetime（结束时间），如果想要查询某个时间段的操作，可以使用该参数。</span> 
</p>
<div class="dp-highlighter bg_sql" style="box-sizing:border-box;padding:1px 0px 0px;font-family:Consolas, &quot;background-color:#E7E5DC;width:851.392px;overflow-x:auto;overflow-y:hidden;position:relative;color:#454545;white-space:normal;margin:18px 0px !important;">
	<div class="bar" style="box-sizing:border-box;margin:0px;padding:0px 0px 0px 45px;">
		<div class="tools" style="box-sizing:border-box;margin:0px;padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;border-right:1px solid #E7E5DC;">
			<b style="box-sizing:border-box;">[sql]</b>&nbsp;<a href="http://blog.csdn.net/a7442358/article/details/47355515#" class="ViewSource" title="view plain" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#CA0C16;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:none;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span class="tracking-ad" data-mod="popu_168" style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;<a href="http://blog.csdn.net/a7442358/article/details/47355515#" class="CopyToClipboard" title="copy" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#CA0C16;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:none;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a> 
			<div style="box-sizing:border-box;margin:0px;padding:0px;position:absolute;left:396px;top:2372px;width:16px;height:16px;z-index:99;">
			</div>
</span><span class="tracking-ad" data-mod="popu_169" style="box-sizing:border-box;margin:0px;padding:0px;"></span> 
		</div>
	</div>
	<ol start="1" class="dp-sql" style="box-sizing:border-box;padding:0px;list-style-position:initial;list-style-image:initial;border-top:none;border-right:1px solid #E7E5DC;border-bottom:none;border-left:none;border-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span style="box-sizing:border-box;margin:0px;padding:0px;border:none;background-color:inherit;">mysqlbinlog&nbsp;</span><span class="comment" style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#008200;background-color:inherit;">--start-datetime="2015-08-08&nbsp;10:00:00"&nbsp;--stop-datetime="2015-08-08&nbsp;12:00:00"&nbsp;../data/mysql-bin.000001</span><span style="box-sizing:border-box;margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;&nbsp;</span></span> 
		</li>
	</ol>
</div>
<span style="color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">&nbsp; &nbsp; 常用的查询操作也就这么多了，查询操作不是我们的目的，恢复记录才是我们的目的，一切的查询都是为了恢复。</span> 
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;text-align:justify;"><span style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp; &nbsp; &nbsp;<strong style="box-sizing:border-box;">如何恢复删除记录？</strong></span></span> 
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;text-align:justify;">&nbsp; &nbsp; 如果你对于查询操作了如指掌了，那么恢复操作就简单的多了，因为恢复数据就是在查询的基础上，恢复的方法大致分为两种：</span> 
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;text-align:justify;">&nbsp; &nbsp; 1.直接使用mysqlbinlog进行查询带恢复</span> 
</p>
<div class="dp-highlighter bg_sql" style="box-sizing:border-box;padding:1px 0px 0px;font-family:Consolas, &quot;background-color:#E7E5DC;width:851.392px;overflow-x:auto;overflow-y:hidden;position:relative;color:#454545;white-space:normal;margin:18px 0px !important;">
	<div class="bar" style="box-sizing:border-box;margin:0px;padding:0px 0px 0px 45px;">
		<div class="tools" style="box-sizing:border-box;margin:0px;padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;border-right:1px solid #E7E5DC;">
			<b style="box-sizing:border-box;">[sql]</b>&nbsp;<a href="http://blog.csdn.net/a7442358/article/details/47355515#" class="ViewSource" title="view plain" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#CA0C16;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:none;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span class="tracking-ad" data-mod="popu_168" style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;<a href="http://blog.csdn.net/a7442358/article/details/47355515#" class="CopyToClipboard" title="copy" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#CA0C16;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:none;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a> 
			<div style="box-sizing:border-box;margin:0px;padding:0px;position:absolute;left:396px;top:2575px;width:16px;height:16px;z-index:99;">
			</div>
</span><span class="tracking-ad" data-mod="popu_169" style="box-sizing:border-box;margin:0px;padding:0px;"></span> 
		</div>
	</div>
	<ol start="1" class="dp-sql" style="box-sizing:border-box;padding:0px;list-style-position:initial;list-style-image:initial;border-top:none;border-right:1px solid #E7E5DC;border-bottom:none;border-left:none;border-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span style="box-sizing:border-box;margin:0px;padding:0px;border:none;background-color:inherit;">mysqlbinlog&nbsp;</span><span class="comment" style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#008200;background-color:inherit;">--start-position=4&nbsp;--stop-position=98&nbsp;../data/mysql-bin.000001&nbsp;|&nbsp;mysql&nbsp;-u&nbsp;root&nbsp;-p</span><span style="box-sizing:border-box;margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;&nbsp;</span></span> 
		</li>
	</ol>
</div>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;text-align:justify;">
	上述命令跟查询操作不同的地方在于尾部添加了“| mysql -u root -p”，该命令是用于连接数据库，整条命令连接起来就是恢复开始位置为4，结束位置为98的所有操作（不限于单行记录的恢复，如果想要用于连续的多行操作，只需要把最后的结束位置设置为最后一个需要进行恢复的行的End_log_pos即可）
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;text-align:justify;">
	&nbsp; &nbsp; 2.先导出查询记录，然后通过mysql source操作进行数据恢复
</p>
<div class="dp-highlighter bg_sql" style="box-sizing:border-box;padding:1px 0px 0px;font-family:Consolas, &quot;background-color:#E7E5DC;width:851.392px;overflow-x:auto;overflow-y:hidden;position:relative;color:#454545;white-space:normal;margin:18px 0px !important;">
	<div class="bar" style="box-sizing:border-box;margin:0px;padding:0px 0px 0px 45px;">
		<div class="tools" style="box-sizing:border-box;margin:0px;padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;border-right:1px solid #E7E5DC;">
			<b style="box-sizing:border-box;">[sql]</b>&nbsp;<a href="http://blog.csdn.net/a7442358/article/details/47355515#" class="ViewSource" title="view plain" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#CA0C16;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:none;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span class="tracking-ad" data-mod="popu_168" style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;<a href="http://blog.csdn.net/a7442358/article/details/47355515#" class="CopyToClipboard" title="copy" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#CA0C16;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:none;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a> 
			<div style="box-sizing:border-box;margin:0px;padding:0px;position:absolute;left:396px;top:2754px;width:16px;height:16px;z-index:99;">
			</div>
</span><span class="tracking-ad" data-mod="popu_169" style="box-sizing:border-box;margin:0px;padding:0px;"></span> 
		</div>
	</div>
	<ol start="1" class="dp-sql" style="box-sizing:border-box;padding:0px;list-style-position:initial;list-style-image:initial;border-top:none;border-right:1px solid #E7E5DC;border-bottom:none;border-left:none;border-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span style="box-sizing:border-box;margin:0px;padding:0px;border:none;background-color:inherit;">mysqlbinlog&nbsp;</span><span class="comment" style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#008200;background-color:inherit;">--start-position=4&nbsp;--stop-position=98&nbsp;../data/mysql-bin.000001&nbsp;&gt;&nbsp;test.sql</span><span style="box-sizing:border-box;margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;&nbsp;</span></span> 
		</li>
	</ol>
</div>
<div class="dp-highlighter bg_sql" style="box-sizing:border-box;padding:1px 0px 0px;font-family:Consolas, &quot;background-color:#E7E5DC;width:851.392px;overflow-x:auto;overflow-y:hidden;position:relative;color:#454545;white-space:normal;margin:18px 0px !important;">
	<div class="bar" style="box-sizing:border-box;margin:0px;padding:0px 0px 0px 45px;">
		<div class="tools" style="box-sizing:border-box;margin:0px;padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;border-right:1px solid #E7E5DC;">
			<b style="box-sizing:border-box;">[sql]</b>&nbsp;<a href="http://blog.csdn.net/a7442358/article/details/47355515#" class="ViewSource" title="view plain" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#CA0C16;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:none;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span class="tracking-ad" data-mod="popu_168" style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;<a href="http://blog.csdn.net/a7442358/article/details/47355515#" class="CopyToClipboard" title="copy" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#CA0C16;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:none;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a> 
			<div style="box-sizing:border-box;margin:0px;padding:0px;position:absolute;left:396px;top:2820px;width:16px;height:16px;z-index:99;">
			</div>
</span><span class="tracking-ad" data-mod="popu_169" style="box-sizing:border-box;margin:0px;padding:0px;"></span> 
		</div>
	</div>
	<ol start="1" class="dp-sql" style="box-sizing:border-box;padding:0px;list-style-position:initial;list-style-image:initial;border-top:none;border-right:1px solid #E7E5DC;border-bottom:none;border-left:none;border-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span style="box-sizing:border-box;margin:0px;padding:0px;border:none;background-color:inherit;">mysql&gt;source&nbsp;test.sql&nbsp;&nbsp;</span></span> 
		</li>
	</ol>
</div>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;text-align:justify;"><span style="box-sizing:border-box;margin:0px;padding:0px;"><strong style="box-sizing:border-box;">&nbsp; &nbsp; 恢复数据实例</strong></span></span> 
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;text-align:justify;"><strong style="box-sizing:border-box;">&nbsp; &nbsp;&nbsp;</strong>首先开启binlog，然后新建一个logtest数据库，然后新建一个test数据表，插入几条测试数据，然后删除，此时我们使用binlog来恢复数据</span> 
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;text-align:justify;"><span style="box-sizing:border-box;margin:0px;padding:0px;"></span></span> 
</p>
<div class="dp-highlighter bg_sql" style="box-sizing:border-box;padding:1px 0px 0px;font-family:Consolas, &quot;background-color:#E7E5DC;width:851.392px;overflow-x:auto;overflow-y:hidden;position:relative;color:#454545;white-space:normal;margin:18px 0px !important;">
	<div class="bar" style="box-sizing:border-box;margin:0px;padding:0px 0px 0px 45px;">
		<div class="tools" style="box-sizing:border-box;margin:0px;padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;border-right:1px solid #E7E5DC;">
			<b style="box-sizing:border-box;">[sql]</b>&nbsp;<a href="http://blog.csdn.net/a7442358/article/details/47355515#" class="ViewSource" title="view plain" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#CA0C16;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:none;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span class="tracking-ad" data-mod="popu_168" style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;<a href="http://blog.csdn.net/a7442358/article/details/47355515#" class="CopyToClipboard" title="copy" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#CA0C16;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:none;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a> 
			<div style="box-sizing:border-box;margin:0px;padding:0px;position:absolute;left:396px;top:2976px;width:16px;height:16px;z-index:99;">
			</div>
</span><span class="tracking-ad" data-mod="popu_169" style="box-sizing:border-box;margin:0px;padding:0px;"></span> 
		</div>
	</div>
	<ol start="1" class="dp-sql" style="box-sizing:border-box;padding:0px;list-style-position:initial;list-style-image:initial;border-top:none;border-right:1px solid #E7E5DC;border-bottom:none;border-left:none;border-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span style="box-sizing:border-box;margin:0px;padding:0px;border:none;background-color:inherit;">mysqlbinlog&nbsp;</span><span class="comment" style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#008200;background-color:inherit;">--database=logtest&nbsp;--start-position=98&nbsp;--stop-position=664&nbsp;../data/mysql-bin.000001&nbsp;|&nbsp;mysql&nbsp;-u&nbsp;root&nbsp;-p</span><span style="box-sizing:border-box;margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;&nbsp;</span></span> 
		</li>
	</ol>
</div>
<span style="color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">数值98是对数据库logtest的首次操作的Pos，数值664是对数据库logtest删除前的最后一次操作的End_log_pos，binlog的操作记录都在mysql-bin.000001中存储着，我们可以通过上述命令来恢复已经被删除的数据库logtest，从下图中我们可以看到1070-1636重复了98-664的动作，重新建立数据库，数据表和插入数据，我们再来打开数据库，发现被删除的数据库logtest，数据表test以及插入test的数据都已经被找回来了。</span> 
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;text-align:justify;"><img src="http://img.blog.csdn.net/20150808160319653?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center" alt="" style="box-sizing:border-box;vertical-align:middle;outline:none;max-width:100%;" /><br style="box-sizing:border-box;" />
</span> 
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;text-align:justify;">&nbsp; &nbsp; 当然使用binlog恢复的时候一定要注意几个问题：</span> 
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;text-align:justify;">&nbsp; &nbsp; 问题一：为什么使用mysqlbinlog --database=logtest ../data/mysql-bin.000001 | mysql -u root -p恢复数据不管用？</span> 
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;text-align:justify;">&nbsp; &nbsp; 其实并非该命令出错，而是日志中同时记录了最后一个drop操作，在没有选在position和datetime的情况下，binlog会读取有关该数据库的所有记录，从create到drop，使用该命令的情况下会重新把create到drop的语句再执行一遍，而在我们看来跟什么都没有做差不多，但是你再次使用mysqlbinlog查看该数据库的相关操作记录的时候就会发现，从create到drop的操作出现了两次，证明该命令的确被执行过，不过由于最后有drop语句，因此被恢复的数据库信息又被删除，回到没有恢复的状态。因此该命令不适用于数据的恢复，想要恢复数据，还要根据情况选择指定的时间或者位置。</span> 
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;text-align:justify;">&nbsp; &nbsp; 问题二：为什么使用position参数的时候数据恢复不完全？</span> 
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;text-align:justify;">&nbsp; &nbsp; &nbsp;选择position的时候也是非常有讲究的，就拿上图来说，如果执行命令语句的时候，只是执行到492</span> 
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;text-align:justify;"><span style="box-sizing:border-box;margin:0px;padding:0px;"></span></span> 
</p>
<div class="dp-highlighter bg_sql" style="box-sizing:border-box;padding:1px 0px 0px;font-family:Consolas, &quot;background-color:#E7E5DC;width:851.392px;overflow-x:auto;overflow-y:hidden;position:relative;color:#454545;white-space:normal;margin:18px 0px !important;">
	<div class="bar" style="box-sizing:border-box;margin:0px;padding:0px 0px 0px 45px;">
		<div class="tools" style="box-sizing:border-box;margin:0px;padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #6CE26C;border-right:1px solid #E7E5DC;">
			<b style="box-sizing:border-box;">[sql]</b>&nbsp;<a href="http://blog.csdn.net/a7442358/article/details/47355515#" class="ViewSource" title="view plain" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#CA0C16;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:none;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">view plain</a><span class="tracking-ad" data-mod="popu_168" style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;<a href="http://blog.csdn.net/a7442358/article/details/47355515#" class="CopyToClipboard" title="copy" style="box-sizing:border-box;background-image:url(&quot;background-position:left top;background-size:initial;background-repeat:no-repeat;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;color:#CA0C16;text-decoration-line:none;margin:0px 10px 0px 0px;padding:1px;outline:none;border:none;font-size:9px;display:inline-block;width:16px;height:16px;text-indent:-2000px;">copy</a> 
			<div style="box-sizing:border-box;margin:0px;padding:0px;position:absolute;left:396px;top:3862px;width:16px;height:16px;z-index:99;">
			</div>
</span><span class="tracking-ad" data-mod="popu_169" style="box-sizing:border-box;margin:0px;padding:0px;"></span> 
		</div>
	</div>
	<ol start="1" class="dp-sql" style="box-sizing:border-box;padding:0px;list-style-position:initial;list-style-image:initial;border-top:none;border-right:1px solid #E7E5DC;border-bottom:none;border-left:none;border-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
		<li class="alt" style="box-sizing:border-box;margin-left:40px;list-style:decimal;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #6CE26C;border-image:initial;color:inherit;line-height:18px;margin-top:0px !important;margin-right:0px !important;margin-bottom:0px !important;padding:0px 3px 0px 10px !important;">
			<span style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span style="box-sizing:border-box;margin:0px;padding:0px;border:none;background-color:inherit;">mysqlbinlog&nbsp;</span><span class="comment" style="box-sizing:border-box;margin:0px;padding:0px;border:none;color:#008200;background-color:inherit;">--database=logtest&nbsp;--start-position=98&nbsp;--stop-position=492&nbsp;../data/mysql-bin.000001&nbsp;|&nbsp;mysql&nbsp;-u&nbsp;root&nbsp;-p</span><span style="box-sizing:border-box;margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;&nbsp;</span></span> 
		</li>
	</ol>
</div>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;text-align:justify;">那么进行数据恢复的时候只能恢复logtest数据库和test数据表，而不能恢复数据表中的数据，Pos是一条记录的起始位置，End_log_pos是一条记录的结束 ，如果想要恢复某连续行的数据的时候，不要忘了把最后一行需要恢复的数据的End_log_pos作为stop-position，而不是把Pos作为stop-position。</span> 
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;text-align:justify;"><span style="box-sizing:border-box;margin:0px;padding:0px;"><strong style="box-sizing:border-box;">注意事项</strong></span></span> 
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;text-align:justify;">&nbsp; &nbsp; 1.每当重启mysql的时候，都会自动生成一个新的binlog文件，恢复数据的时候首先确定需要恢复的数据在哪个日志文件中，然后查找对应binlog文件进行数据恢复。</span> 
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;text-align:justify;">&nbsp; &nbsp; 2.binlog分别记录了一个操作的起始位置Pos和结束位置End_log_pos，当起始位置和终止位置都选择正确的时候，恢复的数据才会正确，尤其是当进行连续的多行记录进行恢复的时候，对于stop-position的选择一定要注意，最后一行的End_log_pos才是我们需要的。</span> 
</p>
<p style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;word-break:normal;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
	<span style="box-sizing:border-box;margin:0px;padding:0px;text-align:justify;">&nbsp; &nbsp; 3.使用show binlog events的时候默认指定的是第一个二进制文件，如果想要查看其它的二进制文件，可以使用show binlog events in 'logname'，其中logname是个字符串，不要忘记带上引号，否则会出错。</span> 
</p>