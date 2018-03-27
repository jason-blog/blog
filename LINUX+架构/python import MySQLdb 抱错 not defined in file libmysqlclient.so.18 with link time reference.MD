<h2 class="blog-title" style="box-sizing:border-box;margin:0px;padding:0px;font-weight:500;font-size:28px;font-family:&quot;line-height:38px;white-space:normal;background-color:#FFFFFF;">
	<span style="font-size:14px;">not defined in file libmysqlclient.so.18 with link time reference&nbsp;</span>
</h2>
<div class="blog-o-info" style="box-sizing:border-box;margin:0px;padding:12px 0px;color:#999999;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
	<div class="other-opt" style="box-sizing:border-box;margin:0px;padding:0px;float:right;">
	</div>
<span style="font-size:14px;">字面意思是对应版本不一样 ，那么请留意&nbsp;</span><br />
	<h2 class="blog-title" style="white-space:normal;box-sizing:border-box;margin:0px;padding:0px;font-weight:500;font-size:28px;font-family:&quot;line-height:38px;background-color:#FFFFFF;">
		<span style="color:#555555;font-family:&quot;font-size:14px;white-space:normal;">etc/ld.so.conf.d里面的路径下的&nbsp;libmysqlclient.so.18&nbsp;</span> 
	</h2>
</div>
<p class="blog-summary" style="box-sizing:border-box;margin-top:30px;margin-bottom:10px;padding:16px 30px;font-size:16px;line-height:32px;color:#333333;background:#F9F9F9;table-layout:fixed;word-break:break-all;overflow:hidden;font-family:&quot;white-space:normal;">
	<span style="box-sizing:border-box;font-weight:700;font-size:14px;">摘要：</span><span style="font-size:14px;">&nbsp;[root@master conf]# /opt/php/sbin/php-fpm/opt/php/sbin/php-fpm: relocation error: /opt/php/sbin/php-fpm: symbol mysql_server_init, version libmysqlclient_</span>
</p>
<div class="content-detail" style="box-sizing:border-box;margin:0px;padding:40px 0px;font-size:16px;line-height:32px;position:relative;overflow:hidden;color:#333333;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
	<span style="font-size:14px;">[root@master conf]</span><span style="box-sizing:border-box;color:#3333FF;font-size:14px;"># /opt/php/sbin/php-fpm</span><br style="box-sizing:border-box;" />
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:10px;padding:0px;">
		<span style="font-size:14px;">/opt/php/sbin/php-fpm: relocation error: /opt/php/sbin/php-fpm: symbol mysql_server_init, version libmysqlclient_18</span>
	</p>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:10px;padding:0px;">
		<span style="box-sizing:border-box;color:#3333FF;font-size:14px;">&nbsp;not defined in file libmysqlclient.so.18 with link time reference</span> 
	</p>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:10px;padding:0px;">
		<br />
	</p>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:10px;padding:0px;">
		<span style="font-size:14px;">记录一下，没有找到解决办法。</span>
	</p>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:10px;padding:0px;">
		<span style="font-size:14px;">欢迎留言。</span>
	</p>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:10px;padding:0px;">
		<span style="font-size:14px;">1、如下不行：</span>
	</p>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:10px;padding:0px;">
		<span style="font-size:14px;">自己一定要删除干净。</span>
	</p>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:10px;padding:0px;">
		<br />
	</p>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:20px;padding:0px;line-height:1.6em;color:#555555;font-family:&quot;font-size:15px;">
		<span style="font-size:14px;">最近编译php的时候在加入mysql编译参数的时候报错，然后我就仔细的研究了下</span>
	</p>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:20px;padding:0px;line-height:1.6em;color:#555555;font-family:&quot;font-size:15px;">
		<span style="box-sizing:border-box;margin:0px;padding:0px;color:#FF0000;font-size:14px;">基本情况</span><span style="font-size:14px;">：</span><br style="box-sizing:border-box;margin:0px;padding:0px;" />
<span style="font-size:14px;"> 系统：CentOS－6.5</span><br style="box-sizing:border-box;margin:0px;padding:0px;" />
<span style="font-size:14px;"> 数据库：之前yum安装了mysql后来卸载掉，编译安装了mysql</span><br style="box-sizing:border-box;margin:0px;padding:0px;" />
<span style="font-size:14px;"> php：我电脑里装了两个版本的php</span><br style="box-sizing:border-box;margin:0px;padding:0px;" />
<span style="font-size:14px;"> 一个是yum安装的 php-5.4.28</span><br style="box-sizing:border-box;margin:0px;padding:0px;" />
<span style="font-size:14px;"> 另一个是编译安装的 php-5.3.28</span>
	</p>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:20px;padding:0px;line-height:1.6em;color:#555555;font-family:&quot;font-size:15px;">
		<span style="box-sizing:border-box;margin:0px;padding:0px;color:#FF0000;font-size:14px;">以下是各种报错</span> 
	</p>
	<div style="box-sizing:border-box;margin:0px;padding:0px;color:#555555;font-family:&quot;font-size:15px;">
		<div class="syntaxhighlighter php" style="box-sizing:border-box;margin:1em 0px;padding:0px;width:788.5px;font-size:1em;overflow-x:auto;border:0px !important;outline:0px !important;background:0px 0px !important;float:none !important;vertical-align:baseline !important;position:relative !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;height:auto !important;line-height:1.1em !important;font-family:Consolas, &quot;min-height:auto !important;">
			<table border="0" style="box-sizing:border-box;border-spacing:0px;background:none;max-width:100%;margin:0px;padding:0px;border:0px;float:none;vertical-align:baseline;height:auto;width:788px;line-height:1.1em;font-size:1em;display:block;overflow:visible;table-layout:auto;outline:0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;" class="ke-zeroborder">
				<tbody style="box-sizing:border-box;margin:0px;padding:0px;border:0px;background:none;float:none;vertical-align:baseline;height:auto;width:auto;line-height:1.1em;font-size:1em;overflow:visible;outline:0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;">
					<tr style="box-sizing:border-box;margin:0px;padding:0px;border:0px;background:none;float:none;vertical-align:baseline;height:auto;width:auto;line-height:1.1em;font-size:1em;overflow:visible;outline:0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;">
						<td class="gutter" style="box-sizing:border-box;margin:0px;padding:0px;border:0px;background:none;float:none;vertical-align:baseline;height:auto;width:auto;line-height:1.1em;font-family:Consolas, &quot;font-size:1em;overflow:visible;color:#AFAFAF;outline:0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;">
							<div class="line number1 index0 alt2" style="box-sizing:border-box;margin:0px;padding:0px 0.5em 0px 1em;border-width:0px 3px 0px 0px;border-right-style:solid;border-right-color:#6CE26C;text-align:right;float:none;vertical-align:baseline;height:auto;width:auto;line-height:1.1em;font-size:1em;overflow:visible;white-space:pre;border-top-style:initial !important;border-bottom-style:initial !important;border-left-style:initial !important;border-top-color:initial !important;border-bottom-color:initial !important;border-left-color:initial !important;border-image:initial !important;outline:0px !important;background:0px 0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;">
								<span style="font-size:14px;">1</span>
							</div>
							<div class="line number2 index1 alt1" style="box-sizing:border-box;margin:0px;padding:0px 0.5em 0px 1em;border-width:0px 3px 0px 0px;border-right-style:solid;border-right-color:#6CE26C;text-align:right;float:none;vertical-align:baseline;height:auto;width:auto;line-height:1.1em;font-size:1em;overflow:visible;white-space:pre;border-top-style:initial !important;border-bottom-style:initial !important;border-left-style:initial !important;border-top-color:initial !important;border-bottom-color:initial !important;border-left-color:initial !important;border-image:initial !important;outline:0px !important;background:0px 0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;">
								<span style="font-size:14px;">2</span>
							</div>
							<div class="line number3 index2 alt2" style="box-sizing:border-box;margin:0px;padding:0px 0.5em 0px 1em;border-width:0px 3px 0px 0px;border-right-style:solid;border-right-color:#6CE26C;text-align:right;float:none;vertical-align:baseline;height:auto;width:auto;line-height:1.1em;font-size:1em;overflow:visible;white-space:pre;border-top-style:initial !important;border-bottom-style:initial !important;border-left-style:initial !important;border-top-color:initial !important;border-bottom-color:initial !important;border-left-color:initial !important;border-image:initial !important;outline:0px !important;background:0px 0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;">
								<span style="font-size:14px;">3</span>
							</div>
							<div class="line number4 index3 alt1" style="box-sizing:border-box;margin:0px;padding:0px 0.5em 0px 1em;border-width:0px 3px 0px 0px;border-right-style:solid;border-right-color:#6CE26C;text-align:right;float:none;vertical-align:baseline;height:auto;width:auto;line-height:1.1em;font-size:1em;overflow:visible;white-space:pre;border-top-style:initial !important;border-bottom-style:initial !important;border-left-style:initial !important;border-top-color:initial !important;border-bottom-color:initial !important;border-left-color:initial !important;border-image:initial !important;outline:0px !important;background:0px 0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;">
								<span style="font-size:14px;">4</span>
							</div>
							<div class="line number5 index4 alt2" style="box-sizing:border-box;margin:0px;padding:0px 0.5em 0px 1em;border-width:0px 3px 0px 0px;border-right-style:solid;border-right-color:#6CE26C;text-align:right;float:none;vertical-align:baseline;height:auto;width:auto;line-height:1.1em;font-size:1em;overflow:visible;white-space:pre;border-top-style:initial !important;border-bottom-style:initial !important;border-left-style:initial !important;border-top-color:initial !important;border-bottom-color:initial !important;border-left-color:initial !important;border-image:initial !important;outline:0px !important;background:0px 0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;">
								<span style="font-size:14px;">5</span>
							</div>
						</td>
						<td class="code" style="box-sizing:border-box;margin:0px;padding:0px;border:0px;background:none;float:none;vertical-align:baseline;height:auto;width:754px;line-height:1.1em;font-family:Consolas, &quot;font-size:1em;overflow:visible;outline:0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;">
							<div class="container" style="box-sizing:border-box;margin:0px;padding:0px;width:auto;border:0px;background:none;float:none;vertical-align:baseline;height:auto;line-height:1.1em;font-size:1em;overflow:visible;outline:0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;">
								<div class="line number1 index0 alt2" style="box-sizing:border-box;margin:0px;padding:0px 1em;border:0px;float:none;vertical-align:baseline;height:auto;width:auto;line-height:1.1em;font-size:1em;overflow:visible;white-space:pre;outline:0px !important;background:0px 0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;">
									<code class="php plain" style="box-sizing:border-box;margin:0px;padding:0px;font-size:1em;border-radius:2px;font-family:Consolas, &quot;color:#C7254E;background:none;white-space:pre-wrap;border:0px;float:none;vertical-align:baseline;height:auto;width:auto;line-height:1.1em;clear:both;overflow:visible;display:inline;outline:0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;"><span style="font-size:14px;">[root@localhost
 php-5.3]# php-fpm</span></code> 
								</div>
								<div class="line number2 index1 alt1" style="box-sizing:border-box;margin:0px;padding:0px 1em;border:0px;float:none;vertical-align:baseline;height:auto;width:auto;line-height:1.1em;font-size:1em;overflow:visible;white-space:pre;outline:0px !important;background:0px 0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;">
									<code class="php plain" style="box-sizing:border-box;margin:0px;padding:0px;font-size:1em;border-radius:2px;font-family:Consolas, &quot;color:#C7254E;background:none;white-space:pre-wrap;border:0px;float:none;vertical-align:baseline;height:auto;width:auto;line-height:1.1em;clear:both;overflow:visible;display:inline;outline:0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;"><span style="font-size:14px;">[09-Jun-2014
 15:37:41] NOTICE: PHP message: PHP Warning:&nbsp; PHP Startup: Unable to load dynamic library</span></code><code class="php string" style="box-sizing:border-box;margin:0px;padding:0px;font-size:1em;border-radius:2px;font-family:Consolas, &quot;color:#0000FF;background:none;white-space:pre-wrap;border:0px;float:none;vertical-align:baseline;height:auto;width:auto;line-height:1.1em;clear:both;overflow:visible;display:inline;outline:0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;"><span style="font-size:14px;">'/usr/lib64/php/modules/mysql.so'</span></code><code class="php plain" style="box-sizing:border-box;margin:0px;padding:0px;font-size:1em;border-radius:2px;font-family:Consolas, &quot;color:#C7254E;background:none;white-space:pre-wrap;border:0px;float:none;vertical-align:baseline;height:auto;width:auto;line-height:1.1em;clear:both;overflow:visible;display:inline;outline:0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;"><span style="font-size:14px;">-
 /usr/lib64/mysql/libmysqlclient.so.18: version `libmysqlclient_16' not found (required by /usr/lib64/php/modules/mysql.so) in Unknown on line 0</span></code> 
								</div>
								<div class="line number3 index2 alt2" style="box-sizing:border-box;margin:0px;padding:0px 1em;border:0px;float:none;vertical-align:baseline;height:auto;width:auto;line-height:1.1em;font-size:1em;overflow:visible;white-space:pre;outline:0px !important;background:0px 0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;">
									<code class="php plain" style="box-sizing:border-box;margin:0px;padding:0px;font-size:1em;border-radius:2px;font-family:Consolas, &quot;color:#C7254E;background:none;white-space:pre-wrap;border:0px;float:none;vertical-align:baseline;height:auto;width:auto;line-height:1.1em;clear:both;overflow:visible;display:inline;outline:0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;"><span style="font-size:14px;">[09-Jun-2014
 15:37:41] NOTICE: PHP message: PHP Warning:&nbsp; PHP Startup: Unable to load dynamic library</span></code><code class="php string" style="box-sizing:border-box;margin:0px;padding:0px;font-size:1em;border-radius:2px;font-family:Consolas, &quot;color:#0000FF;background:none;white-space:pre-wrap;border:0px;float:none;vertical-align:baseline;height:auto;width:auto;line-height:1.1em;clear:both;overflow:visible;display:inline;outline:0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;"><span style="font-size:14px;">'/usr/lib64/php/modules/mysqli.so'</span></code><code class="php plain" style="box-sizing:border-box;margin:0px;padding:0px;font-size:1em;border-radius:2px;font-family:Consolas, &quot;color:#C7254E;background:none;white-space:pre-wrap;border:0px;float:none;vertical-align:baseline;height:auto;width:auto;line-height:1.1em;clear:both;overflow:visible;display:inline;outline:0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;"><span style="font-size:14px;">-
 /usr/lib64/mysql/libmysqlclient.so.18: version `libmysqlclient_16' not found (required by /usr/lib64/php/modules/mysqli.so) in Unknown on line 0</span></code> 
								</div>
								<div class="line number4 index3 alt1" style="box-sizing:border-box;margin:0px;padding:0px 1em;border:0px;float:none;vertical-align:baseline;height:auto;width:auto;line-height:1.1em;font-size:1em;overflow:visible;white-space:pre;outline:0px !important;background:0px 0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;">
									<code class="php plain" style="box-sizing:border-box;margin:0px;padding:0px;font-size:1em;border-radius:2px;font-family:Consolas, &quot;color:#C7254E;background:none;white-space:pre-wrap;border:0px;float:none;vertical-align:baseline;height:auto;width:auto;line-height:1.1em;clear:both;overflow:visible;display:inline;outline:0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;"><span style="font-size:14px;">[09-Jun-2014
 15:37:41] NOTICE: PHP message: PHP Warning:&nbsp; PHP Startup: Unable to load dynamic library</span></code><code class="php string" style="box-sizing:border-box;margin:0px;padding:0px;font-size:1em;border-radius:2px;font-family:Consolas, &quot;color:#0000FF;background:none;white-space:pre-wrap;border:0px;float:none;vertical-align:baseline;height:auto;width:auto;line-height:1.1em;clear:both;overflow:visible;display:inline;outline:0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;"><span style="font-size:14px;">'/usr/lib64/php/modules/pdo_mysql.so'</span></code><code class="php plain" style="box-sizing:border-box;margin:0px;padding:0px;font-size:1em;border-radius:2px;font-family:Consolas, &quot;color:#C7254E;background:none;white-space:pre-wrap;border:0px;float:none;vertical-align:baseline;height:auto;width:auto;line-height:1.1em;clear:both;overflow:visible;display:inline;outline:0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;"><span style="font-size:14px;">-
 /usr/lib64/mysql/libmysqlclient.so.18: version `libmysqlclient_16' not found (required by /usr/lib64/php/modules/pdo_mysql.so) in Unknown on line 0</span></code> 
								</div>
								<div class="line number5 index4 alt2" style="box-sizing:border-box;margin:0px;padding:0px 1em;border:0px;float:none;vertical-align:baseline;height:auto;width:auto;line-height:1.1em;font-size:1em;overflow:visible;white-space:pre;outline:0px !important;background:0px 0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;">
									<code class="php plain" style="box-sizing:border-box;margin:0px;padding:0px;font-size:1em;border-radius:2px;font-family:Consolas, &quot;color:#C7254E;background:none;white-space:pre-wrap;border:0px;float:none;vertical-align:baseline;height:auto;width:auto;line-height:1.1em;clear:both;overflow:visible;display:inline;outline:0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;"><span style="font-size:14px;">[root@localhost
 php-5.3]#</span></code> 
								</div>
							</div>
						</td>
					</tr>
				</tbody>
			</table>
		</div>
	</div>
	<div style="box-sizing:border-box;margin:0px;padding:0px;color:#555555;font-family:&quot;font-size:15px;">
		<div class="syntaxhighlighter php" style="box-sizing:border-box;margin:1em 0px;padding:0px;width:788.5px;font-size:1em;overflow-x:auto;border:0px !important;outline:0px !important;background:0px 0px !important;float:none !important;vertical-align:baseline !important;position:relative !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;height:auto !important;line-height:1.1em !important;font-family:Consolas, &quot;min-height:auto !important;">
			<table border="0" style="box-sizing:border-box;border-spacing:0px;background:none;max-width:100%;margin:0px;padding:0px;border:0px;float:none;vertical-align:baseline;height:auto;width:788px;line-height:1.1em;font-size:1em;display:block;overflow:visible;table-layout:auto;outline:0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;" class="ke-zeroborder">
				<tbody style="box-sizing:border-box;margin:0px;padding:0px;border:0px;background:none;float:none;vertical-align:baseline;height:auto;width:auto;line-height:1.1em;font-size:1em;overflow:visible;outline:0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;">
					<tr style="box-sizing:border-box;margin:0px;padding:0px;border:0px;background:none;float:none;vertical-align:baseline;height:auto;width:auto;line-height:1.1em;font-size:1em;overflow:visible;outline:0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;">
						<td class="gutter" style="box-sizing:border-box;margin:0px;padding:0px;border:0px;background:none;float:none;vertical-align:baseline;height:auto;width:auto;line-height:1.1em;font-family:Consolas, &quot;font-size:1em;overflow:visible;color:#AFAFAF;outline:0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;">
							<div class="line number1 index0 alt2" style="box-sizing:border-box;margin:0px;padding:0px 0.5em 0px 1em;border-width:0px 3px 0px 0px;border-right-style:solid;border-right-color:#6CE26C;text-align:right;float:none;vertical-align:baseline;height:auto;width:auto;line-height:1.1em;font-size:1em;overflow:visible;white-space:pre;border-top-style:initial !important;border-bottom-style:initial !important;border-left-style:initial !important;border-top-color:initial !important;border-bottom-color:initial !important;border-left-color:initial !important;border-image:initial !important;outline:0px !important;background:0px 0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;">
								<span style="font-size:14px;">1</span>
							</div>
						</td>
						<td class="code" style="box-sizing:border-box;margin:0px;padding:0px;border:0px;background:none;float:none;vertical-align:baseline;height:auto;width:754px;line-height:1.1em;font-family:Consolas, &quot;font-size:1em;overflow:visible;outline:0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;">
							<div class="container" style="box-sizing:border-box;margin:0px;padding:0px;width:auto;border:0px;background:none;float:none;vertical-align:baseline;height:auto;line-height:1.1em;font-size:1em;overflow:visible;outline:0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;">
								<div class="line number1 index0 alt2" style="box-sizing:border-box;margin:0px;padding:0px 1em;border:0px;float:none;vertical-align:baseline;height:auto;width:auto;line-height:1.1em;font-size:1em;overflow:visible;white-space:pre;outline:0px !important;background:0px 0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;">
									<code class="php plain" style="box-sizing:border-box;margin:0px;padding:0px;font-size:1em;border-radius:2px;font-family:Consolas, &quot;color:#C7254E;background:none;white-space:pre-wrap;border:0px;float:none;vertical-align:baseline;height:auto;width:auto;line-height:1.1em;clear:both;overflow:visible;display:inline;outline:0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;"><span style="font-size:14px;">version
 libmysqlclient_18 not defined in file libmysqlclient.so.18 with link time reference</span></code> 
								</div>
							</div>
						</td>
					</tr>
				</tbody>
			</table>
		</div>
	</div>
	<div style="box-sizing:border-box;margin:0px;padding:0px;color:#555555;font-family:&quot;font-size:15px;">
		<div class="syntaxhighlighter php" style="box-sizing:border-box;margin:1em 0px;padding:0px;width:788.5px;font-size:1em;overflow-x:auto;border:0px !important;outline:0px !important;background:0px 0px !important;float:none !important;vertical-align:baseline !important;position:relative !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;height:auto !important;line-height:1.1em !important;font-family:Consolas, &quot;min-height:auto !important;">
			<table border="0" style="box-sizing:border-box;border-spacing:0px;background:none;max-width:100%;margin:0px;padding:0px;border:0px;float:none;vertical-align:baseline;height:auto;width:788px;line-height:1.1em;font-size:1em;display:block;overflow:visible;table-layout:auto;outline:0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;" class="ke-zeroborder">
				<tbody style="box-sizing:border-box;margin:0px;padding:0px;border:0px;background:none;float:none;vertical-align:baseline;height:auto;width:auto;line-height:1.1em;font-size:1em;overflow:visible;outline:0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;">
					<tr style="box-sizing:border-box;margin:0px;padding:0px;border:0px;background:none;float:none;vertical-align:baseline;height:auto;width:auto;line-height:1.1em;font-size:1em;overflow:visible;outline:0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;">
						<td class="gutter" style="box-sizing:border-box;margin:0px;padding:0px;border:0px;background:none;float:none;vertical-align:baseline;height:auto;width:auto;line-height:1.1em;font-family:Consolas, &quot;font-size:1em;overflow:visible;color:#AFAFAF;outline:0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;">
							<div class="line number1 index0 alt2" style="box-sizing:border-box;margin:0px;padding:0px 0.5em 0px 1em;border-width:0px 3px 0px 0px;border-right-style:solid;border-right-color:#6CE26C;text-align:right;float:none;vertical-align:baseline;height:auto;width:auto;line-height:1.1em;font-size:1em;overflow:visible;white-space:pre;border-top-style:initial !important;border-bottom-style:initial !important;border-left-style:initial !important;border-top-color:initial !important;border-bottom-color:initial !important;border-left-color:initial !important;border-image:initial !important;outline:0px !important;background:0px 0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;">
								<span style="font-size:14px;">1</span>
							</div>
						</td>
						<td class="code" style="box-sizing:border-box;margin:0px;padding:0px;border:0px;background:none;float:none;vertical-align:baseline;height:auto;width:754px;line-height:1.1em;font-family:Consolas, &quot;font-size:1em;overflow:visible;outline:0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;">
							<div class="container" style="box-sizing:border-box;margin:0px;padding:0px;width:auto;border:0px;background:none;float:none;vertical-align:baseline;height:auto;line-height:1.1em;font-size:1em;overflow:visible;outline:0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;">
								<div class="line number1 index0 alt2" style="box-sizing:border-box;margin:0px;padding:0px 1em;border:0px;float:none;vertical-align:baseline;height:auto;width:auto;line-height:1.1em;font-size:1em;overflow:visible;white-space:pre;outline:0px !important;background:0px 0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;">
									<code class="php plain" style="box-sizing:border-box;margin:0px;padding:0px;font-size:1em;border-radius:2px;font-family:Consolas, &quot;color:#C7254E;background:none;white-space:pre-wrap;border:0px;float:none;vertical-align:baseline;height:auto;width:auto;line-height:1.1em;clear:both;overflow:visible;display:inline;outline:0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;"><span style="font-size:14px;">/usr/lib64/mysql/libmysqlclient.so.18:
 version `libmysqlclient_16' not found (required by /usr/lib64/php/modules/mysql.so) in Unknown on line 0</span></code> 
								</div>
							</div>
						</td>
					</tr>
				</tbody>
			</table>
		</div>
	</div>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:20px;padding:0px;line-height:1.6em;color:#555555;font-family:&quot;font-size:15px;">
		<span style="box-sizing:border-box;margin:0px;padding:0px;color:#FF0000;font-size:14px;">错误分析</span><span style="font-size:14px;">：</span><br style="box-sizing:border-box;margin:0px;padding:0px;" />
<span style="font-size:14px;"> 是64位系统中 libmysqlclient 默认安装到了 /usr/lib64/mysql/ 目录下</span><br style="box-sizing:border-box;margin:0px;padding:0px;" />
<span style="font-size:14px;"> 如果此目录没有加入到 /etc/ld.so.conf里面，Linux就无法自动加载 /usr/lib64/mysql/ 里面的库文件</span><br style="box-sizing:border-box;margin:0px;padding:0px;" />
<span style="font-size:14px;"> php编译时要去 /usr/lib64 和 /etc/ld.so.conf 所指定的目录下查找，却找不到 libmysqlclient 文件</span>
	</p>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:20px;padding:0px;line-height:1.6em;color:#555555;font-family:&quot;font-size:15px;">
		<span style="box-sizing:border-box;margin:0px;padding:0px;color:#FF0000;font-size:14px;">解决方法一</span><span style="font-size:14px;">：</span>
	</p>
	<div style="box-sizing:border-box;margin:0px;padding:0px;color:#555555;font-family:&quot;font-size:15px;">
		<div class="syntaxhighlighter php" style="box-sizing:border-box;margin:1em 0px;padding:0px;width:788.5px;font-size:1em;overflow-x:auto;border:0px !important;outline:0px !important;background:0px 0px !important;float:none !important;vertical-align:baseline !important;position:relative !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;height:auto !important;line-height:1.1em !important;font-family:Consolas, &quot;min-height:auto !important;">
			<table border="0" style="box-sizing:border-box;border-spacing:0px;background:none;max-width:100%;margin:0px;padding:0px;border:0px;float:none;vertical-align:baseline;height:auto;width:788px;line-height:1.1em;font-size:1em;display:block;overflow:visible;table-layout:auto;outline:0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;" class="ke-zeroborder">
				<tbody style="box-sizing:border-box;margin:0px;padding:0px;border:0px;background:none;float:none;vertical-align:baseline;height:auto;width:auto;line-height:1.1em;font-size:1em;overflow:visible;outline:0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;">
					<tr style="box-sizing:border-box;margin:0px;padding:0px;border:0px;background:none;float:none;vertical-align:baseline;height:auto;width:auto;line-height:1.1em;font-size:1em;overflow:visible;outline:0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;">
						<td class="gutter" style="box-sizing:border-box;margin:0px;padding:0px;border:0px;background:none;float:none;vertical-align:baseline;height:auto;width:auto;line-height:1.1em;font-family:Consolas, &quot;font-size:1em;overflow:visible;color:#AFAFAF;outline:0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;">
							<div class="line number1 index0 alt2" style="box-sizing:border-box;margin:0px;padding:0px 0.5em 0px 1em;border-width:0px 3px 0px 0px;border-right-style:solid;border-right-color:#6CE26C;text-align:right;float:none;vertical-align:baseline;height:auto;width:auto;line-height:1.1em;font-size:1em;overflow:visible;white-space:pre;border-top-style:initial !important;border-bottom-style:initial !important;border-left-style:initial !important;border-top-color:initial !important;border-bottom-color:initial !important;border-left-color:initial !important;border-image:initial !important;outline:0px !important;background:0px 0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;">
								<span style="font-size:14px;">1</span>
							</div>
						</td>
						<td class="code" style="box-sizing:border-box;margin:0px;padding:0px;border:0px;background:none;float:none;vertical-align:baseline;height:auto;width:754px;line-height:1.1em;font-family:Consolas, &quot;font-size:1em;overflow:visible;outline:0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;">
							<div class="container" style="box-sizing:border-box;margin:0px;padding:0px;width:auto;border:0px;background:none;float:none;vertical-align:baseline;height:auto;line-height:1.1em;font-size:1em;overflow:visible;outline:0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;">
								<div class="line number1 index0 alt2" style="box-sizing:border-box;margin:0px;padding:0px 1em;border:0px;float:none;vertical-align:baseline;height:auto;width:auto;line-height:1.1em;font-size:1em;overflow:visible;white-space:pre;outline:0px !important;background:0px 0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;">
									<code class="php plain" style="box-sizing:border-box;margin:0px;padding:0px;font-size:1em;border-radius:2px;font-family:Consolas, &quot;color:#C7254E;background:none;white-space:pre-wrap;border:0px;float:none;vertical-align:baseline;height:auto;width:auto;line-height:1.1em;clear:both;overflow:visible;display:inline;outline:0px !important;position:static !important;left:auto !important;top:auto !important;right:auto !important;bottom:auto !important;min-height:auto !important;"><span style="font-size:14px;">ln
 -s /usr/local/mysql/lib/libmysqlclient.so.18 /usr/lib64/libmysqlclient.so.18（mysql是编译安装的使用此行） ln -s /usr/lib64/mysql/libmysqlclient.so.18 /usr/lib64/libmysqlclient.so.18 （myslq非编译安装的使用此行）</span></code> 
								</div>
							</div>
						</td>
					</tr>
				</tbody>
			</table>
		</div>
	</div>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:20px;padding:0px;line-height:1.6em;color:#555555;font-family:&quot;font-size:15px;">
		<span style="box-sizing:border-box;margin:0px;padding:0px;color:#FF0000;font-size:14px;">解决方法二</span><span style="font-size:14px;">： 也可以把mysql库加入/etc/ld.so.conf.d里面</span>
	</p>
</div>