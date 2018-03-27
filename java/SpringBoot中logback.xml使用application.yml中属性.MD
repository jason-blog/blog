<blockquote style="margin:0px;padding:0px 15px;color:#666666;border-left:4px solid #DDDDDD;font-family:Lato, &quot;font-size:16px;text-align:justify;white-space:normal;background-color:#FFFFFF;">
	<p style="margin-top:0px;margin-bottom:20px;">
		转自 http://blog.battcn.com/2017/07/25/springboot/springboot-logbak-config/
	</p>
	<p style="margin-top:0px;margin-bottom:20px;">
		教你如何使用&nbsp;<code style="font-family:consolas, Menlo, &quot;font-size:13px;padding:2px 4px;word-wrap:break-word;color:#FC6423;background:#FBF7F8;border-radius:3px;margin:2px;border:1px solid #D6D6D6;">springProfile</code>&nbsp;与&nbsp;<code style="font-family:consolas, Menlo, &quot;font-size:13px;padding:2px 4px;word-wrap:break-word;color:#FC6423;background:#FBF7F8;border-radius:3px;margin:2px;border:1px solid #D6D6D6;">springProperty</code>&nbsp;让你的logback.xml 配置显得更有逼格，当别人还在苦苦挣扎弄logback-{profile}.xml的时候 你一个文件就搞定了…
	</p>
</blockquote>
<a id="more" style="background-color:#FFFFFF;color:#555555;border-bottom:1px solid #999999;word-wrap:break-word;font-family:Lato, &quot;font-size:16px;text-align:justify;white-space:normal;"></a><span style="color:#555555;font-family:Lato, &quot;font-size:16px;text-align:justify;white-space:normal;background-color:#FFFFFF;"></span>
<h2 id="springProfile" style="margin:20px 0px 15px;padding:10px 0px 0px;line-height:1.5;font-family:Lato, &quot;font-size:20px;color:#555555;text-align:justify;white-space:normal;background-color:#FFFFFF;">
	<a href="http://blog.battcn.com/2017/07/25/springboot/springboot-logbak-config/#springProfile" class="headerlink" title="- springProfile" style="background-color:transparent;color:#555555;text-decoration-line:none;border-bottom:1px solid #999999;word-wrap:break-word;"></a>- springProfile
</h2>
<p style="margin-top:0px;margin-bottom:20px;color:#555555;font-family:Lato, &quot;font-size:16px;text-align:justify;white-space:normal;background-color:#FFFFFF;">
	该&nbsp;<code style="font-family:consolas, Menlo, &quot;font-size:13px;padding:2px 4px;word-wrap:break-word;color:#FC6423;background:#FBF7F8;border-radius:3px;margin:2px;border:1px solid #D6D6D6;">&lt;springProfile&gt;</code>&nbsp;标签允许我们更加灵活配置文件，可选地包含或排除配置部分。<configuration>元素中的任何位置均支持轮廓部分。使用该name属性指定哪个配置文件接受配置。可以使用逗号分隔列表指定多个配置文件。</configuration>
</p>
<figure class="highlight xml" style="margin:5px 0px;overflow:auto;padding:5px;font-size:13px;color:#4D4D4C;background:#F7F7F7;line-height:1.6;border-radius:3px;border:1px solid #D6D6D6;font-family:Lato, &quot;text-align:justify;white-space:normal;">
<table style="border-spacing:0px;margin:0px;width:auto;border:none;font-size:14px;table-layout:fixed;">
	<tbody>
		<tr style="background-color:#F9F9F9;">
			<td class="gutter" style="padding:0px;vertical-align:middle;border:none;user-select:none;">
<pre style="overflow:auto;font-family:consolas, Menlo, &quot;font-size:13px;margin-top:0px;margin-bottom:0px;padding:10px;color:#869194;background:#EFF2F3;line-height:1.6;border-radius:3px;border:none;text-align:right;">
				<div class="line" style="height:20px;">
					1
				</div>

				<div class="line" style="height:20px;">
					2
				</div>

				<div class="line" style="height:20px;">
					3
				</div>

				<div class="line" style="height:20px;">
					4
				</div>

				<div class="line" style="height:20px;">
					5
				</div>

				<div class="line" style="height:20px;">
					6
				</div>

				<div class="line" style="height:20px;">
					7
				</div>

				<div class="line" style="height:20px;">
					8
				</div>

				<div class="line" style="height:20px;">
					9
				</div>

				<div class="line" style="height:20px;">
					10
				</div>

				<div class="line" style="height:20px;">
					11
				</div>
</pre>
			</td>
			<td class="code" style="padding:0px;vertical-align:middle;border:none;">
<pre style="overflow:auto;font-family:consolas, Menlo, &quot;font-size:13px;margin-top:0px;margin-bottom:0px;padding:10px;color:#4D4D4C;background:#F7F7F7;line-height:1.6;border-radius:3px;border:none;width:304px;">
				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">springProfile</span> <span class="attr">name</span>=<span class="string" style="color:#718C00;">"dev"</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="comment" style="color:#8E908C;">&lt;!-- 开发环境时激活 --&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;/<span class="name">springProfile</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">springProfile</span> <span class="attr">name</span>=<span class="string" style="color:#718C00;">"dev,test"</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="comment" style="color:#8E908C;">&lt;!-- 开发，测试的时候激活--&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;/<span class="name">springProfile</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">springProfile</span> <span class="attr">name</span>=<span class="string" style="color:#718C00;">"!prod"</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="comment" style="color:#8E908C;">&lt;!-- 当 "生产" 环境时，该配置不激活--&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;/<span class="name">springProfile</span>&gt;</span>
				</div>
</pre>
			</td>
		</tr>
	</tbody>
</table>
</figure>
<h3 id="案例" style="margin:20px 0px 15px;padding:10px 0px 0px;line-height:1.5;font-family:Lato, &quot;font-size:18px;color:#555555;text-align:justify;white-space:normal;background-color:#FFFFFF;">
	<a href="http://blog.battcn.com/2017/07/25/springboot/springboot-logbak-config/#案例" class="headerlink" title="- 案例" style="background-color:transparent;color:#555555;text-decoration-line:none;border-bottom:1px solid #999999;word-wrap:break-word;"></a>- 案例
</h3>
<figure class="highlight xml" style="margin:5px 0px;overflow:auto;padding:5px;font-size:13px;color:#4D4D4C;background:#F7F7F7;line-height:1.6;border-radius:3px;border:1px solid #D6D6D6;font-family:Lato, &quot;text-align:justify;white-space:normal;">
<table style="border-spacing:0px;margin:0px;width:auto;border:none;font-size:14px;table-layout:fixed;">
	<tbody>
		<tr style="background-color:#F9F9F9;">
			<td class="gutter" style="padding:0px;vertical-align:middle;border:none;user-select:none;">
<pre style="overflow:auto;font-family:consolas, Menlo, &quot;font-size:13px;margin-top:0px;margin-bottom:0px;padding:10px;color:#869194;background:#EFF2F3;line-height:1.6;border-radius:3px;border:none;text-align:right;">
				<div class="line" style="height:20px;">
					1
				</div>

				<div class="line" style="height:20px;">
					2
				</div>

				<div class="line" style="height:20px;">
					3
				</div>

				<div class="line" style="height:20px;">
					4
				</div>

				<div class="line" style="height:20px;">
					5
				</div>

				<div class="line" style="height:20px;">
					6
				</div>

				<div class="line" style="height:20px;">
					7
				</div>

				<div class="line" style="height:20px;">
					8
				</div>

				<div class="line" style="height:20px;">
					9
				</div>

				<div class="line" style="height:20px;">
					10
				</div>

				<div class="line" style="height:20px;">
					11
				</div>

				<div class="line" style="height:20px;">
					12
				</div>

				<div class="line" style="height:20px;">
					13
				</div>

				<div class="line" style="height:20px;">
					14
				</div>

				<div class="line" style="height:20px;">
					15
				</div>
</pre>
			</td>
			<td class="code" style="padding:0px;vertical-align:middle;border:none;">
<pre style="overflow:auto;font-family:consolas, Menlo, &quot;font-size:13px;margin-top:0px;margin-bottom:0px;padding:10px;color:#4D4D4C;background:#F7F7F7;line-height:1.6;border-radius:3px;border:none;width:278px;">
				<div class="line" style="height:20px;">
					<span class="comment" style="color:#8E908C;">&lt;!-- 开发环境日志级别为DEBUG --&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">springProfile</span> <span class="attr">name</span>=<span class="string" style="color:#718C00;">"dev"</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">root</span> <span class="attr">level</span>=<span class="string" style="color:#718C00;">"DEBUG"</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">appender-ref</span> <span class="attr">ref</span>=<span class="string" style="color:#718C00;">"FILE"</span>/&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">appender-ref</span> <span class="attr">ref</span>=<span class="string" style="color:#718C00;">"STDOUT"</span>/&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;/<span class="name">root</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;/<span class="name">springProfile</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					
				</div>

				<div class="line" style="height:20px;">
					<span class="comment" style="color:#8E908C;">&lt;!-- 测试环境日志级别为INFO --&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">springProfile</span> <span class="attr">name</span>=<span class="string" style="color:#718C00;">"test"</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">root</span> <span class="attr">level</span>=<span class="string" style="color:#718C00;">"INFO"</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">appender-ref</span> <span class="attr">ref</span>=<span class="string" style="color:#718C00;">"FILE"</span>/&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">appender-ref</span> <span class="attr">ref</span>=<span class="string" style="color:#718C00;">"STDOUT"</span>/&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;/<span class="name">root</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;/<span class="name">springProfile</span>&gt;</span>
				</div>
</pre>
			</td>
		</tr>
	</tbody>
</table>
</figure>
<h2 id="springProperty" style="margin:20px 0px 15px;padding:10px 0px 0px;line-height:1.5;font-family:Lato, &quot;font-size:20px;color:#555555;text-align:justify;white-space:normal;background-color:#FFFFFF;">
	<a href="http://blog.battcn.com/2017/07/25/springboot/springboot-logbak-config/#springProperty" class="headerlink" title="- springProperty" style="background-color:transparent;color:#555555;text-decoration-line:none;border-bottom:1px solid #999999;word-wrap:break-word;"></a>- springProperty
</h2>
<p style="margin-top:0px;margin-bottom:20px;color:#555555;font-family:Lato, &quot;font-size:16px;text-align:justify;white-space:normal;background-color:#FFFFFF;">
	1.该&nbsp;<code style="font-family:consolas, Menlo, &quot;font-size:13px;padding:2px 4px;word-wrap:break-word;color:#FC6423;background:#FBF7F8;border-radius:3px;margin:2px;border:1px solid #D6D6D6;">&lt;springProperty&gt;</code>&nbsp;标签允许我们从Spring中显示属性，Environment 以便在Logback中使用。如果你想将 application.properties在回读配置中访问文件中的值，这将非常有用
</p>
<p style="margin-top:0px;margin-bottom:20px;color:#555555;font-family:Lato, &quot;font-size:16px;text-align:justify;white-space:normal;background-color:#FFFFFF;">
	2.标签的工作方式与Logback的标准&nbsp;<code style="font-family:consolas, Menlo, &quot;font-size:13px;padding:2px 4px;word-wrap:break-word;color:#FC6423;background:#FBF7F8;border-radius:3px;margin:2px;border:1px solid #D6D6D6;">&lt;property&gt;</code>&nbsp;标签类似，但不是直接value 指定source属性（从Environment）指定。scope 如果需要将属性存储在local范围之外的其他位置，则可以使用该属性。如果您需要一个后备值，以防该属性未设置，则Environment可以使用该defaultValue属性。
</p>
<figure class="highlight xml" style="margin:5px 0px;overflow:auto;padding:5px;font-size:13px;color:#4D4D4C;background:#F7F7F7;line-height:1.6;border-radius:3px;border:1px solid #D6D6D6;font-family:Lato, &quot;text-align:justify;white-space:normal;">
<table style="border-spacing:0px;margin:0px;width:auto;border:none;font-size:14px;table-layout:fixed;">
	<tbody>
		<tr style="background-color:#F9F9F9;">
			<td class="gutter" style="padding:0px;vertical-align:middle;border:none;user-select:none;">
<pre style="overflow:auto;font-family:consolas, Menlo, &quot;font-size:13px;margin-top:0px;margin-bottom:0px;padding:10px;color:#869194;background:#EFF2F3;line-height:1.6;border-radius:3px;border:none;text-align:right;">
				<div class="line" style="height:20px;">
					1
				</div>

				<div class="line" style="height:20px;">
					2
				</div>

				<div class="line" style="height:20px;">
					3
				</div>

				<div class="line" style="height:20px;">
					4
				</div>

				<div class="line" style="height:20px;">
					5
				</div>
</pre>
			</td>
			<td class="code" style="padding:0px;vertical-align:middle;border:none;">
<pre style="overflow:auto;font-family:consolas, Menlo, &quot;font-size:13px;margin-top:0px;margin-bottom:0px;padding:10px;color:#4D4D4C;background:#F7F7F7;line-height:1.6;border-radius:3px;border:none;width:764px;">
				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">springProperty</span> <span class="attr">scope</span>=<span class="string" style="color:#718C00;">"context"</span> <span class="attr">name</span>=<span class="string" style="color:#718C00;">"fluentHost"</span> <span class="attr">source</span>=<span class="string" style="color:#718C00;">"myapp.fluentd.host"</span> <span class="attr">defaultValue</span>=<span class="string" style="color:#718C00;">"localhost"</span>/&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">appender</span> <span class="attr">name</span>=<span class="string" style="color:#718C00;">"FLUENT"</span> <span class="attr">class</span>=<span class="string" style="color:#718C00;">"ch.qos.logback.more.appenders.DataFluentAppender"</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">remoteHost</span>&gt;</span>${fluentHost}<span class="tag" style="color:#C82829;">&lt;/<span class="name">remoteHost</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;/<span class="name">appender</span>&gt;</span>
				</div>
</pre>
			</td>
		</tr>
	</tbody>
</table>
</figure>
<h3 id="案例-1" style="margin:20px 0px 15px;padding:10px 0px 0px;line-height:1.5;font-family:Lato, &quot;font-size:18px;color:#555555;text-align:justify;white-space:normal;background-color:#FFFFFF;">
	<a href="http://blog.battcn.com/2017/07/25/springboot/springboot-logbak-config/#案例-1" class="headerlink" title="- 案例" style="background-color:transparent;color:#555555;text-decoration-line:none;border-bottom:1px solid #999999;word-wrap:break-word;"></a>- 案例
</h3>
<figure class="highlight xml" style="margin:5px 0px;overflow:auto;padding:5px;font-size:13px;color:#4D4D4C;background:#F7F7F7;line-height:1.6;border-radius:3px;border:1px solid #D6D6D6;font-family:Lato, &quot;text-align:justify;white-space:normal;">
<table style="border-spacing:0px;margin:0px;width:auto;border:none;font-size:14px;table-layout:fixed;">
	<tbody>
		<tr style="background-color:#F9F9F9;">
			<td class="gutter" style="padding:0px;vertical-align:middle;border:none;user-select:none;">
<pre style="overflow:auto;font-family:consolas, Menlo, &quot;font-size:13px;margin-top:0px;margin-bottom:0px;padding:10px;color:#869194;background:#EFF2F3;line-height:1.6;border-radius:3px;border:none;text-align:right;">
				<div class="line" style="height:20px;">
					1
				</div>

				<div class="line" style="height:20px;">
					2
				</div>

				<div class="line" style="height:20px;">
					3
				</div>

				<div class="line" style="height:20px;">
					4
				</div>

				<div class="line" style="height:20px;">
					5
				</div>

				<div class="line" style="height:20px;">
					6
				</div>

				<div class="line" style="height:20px;">
					7
				</div>

				<div class="line" style="height:20px;">
					8
				</div>

				<div class="line" style="height:20px;">
					9
				</div>

				<div class="line" style="height:20px;">
					10
				</div>

				<div class="line" style="height:20px;">
					11
				</div>

				<div class="line" style="height:20px;">
					12
				</div>

				<div class="line" style="height:20px;">
					13
				</div>

				<div class="line" style="height:20px;">
					14
				</div>

				<div class="line" style="height:20px;">
					15
				</div>

				<div class="line" style="height:20px;">
					16
				</div>

				<div class="line" style="height:20px;">
					17
				</div>

				<div class="line" style="height:20px;">
					18
				</div>

				<div class="line" style="height:20px;">
					19
				</div>
</pre>
			</td>
			<td class="code" style="padding:0px;vertical-align:middle;border:none;">
<pre style="overflow:auto;font-family:consolas, Menlo, &quot;font-size:13px;margin-top:0px;margin-bottom:0px;padding:10px;color:#4D4D4C;background:#F7F7F7;line-height:1.6;border-radius:3px;border:none;width:821px;">
				<div class="line" style="height:20px;">
					<span class="comment" style="color:#8E908C;">&lt;!-- 读取spring.application.name中的属性来生成日志文件名 --&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">springProperty</span> <span class="attr">scope</span>=<span class="string" style="color:#718C00;">"context"</span> <span class="attr">name</span>=<span class="string" style="color:#718C00;">"logName"</span> <span class="attr">source</span>=<span class="string" style="color:#718C00;">"spring.application.name"</span> <span class="attr">defaultValue</span>=<span class="string" style="color:#718C00;">"localhost.log"</span>/&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">appender</span> <span class="attr">name</span>=<span class="string" style="color:#718C00;">"FILE"</span> <span class="attr">class</span>=<span class="string" style="color:#718C00;">"ch.qos.logback.core.rolling.RollingFileAppender"</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">file</span>&gt;</span>logs/${logName}.log<span class="tag" style="color:#C82829;">&lt;/<span class="name">file</span>&gt;</span> <span class="comment" style="color:#8E908C;">&lt;!-- 使用方法 --&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">append</span>&gt;</span>true<span class="tag" style="color:#C82829;">&lt;/<span class="name">append</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">rollingPolicy</span> <span class="attr">class</span>=<span class="string" style="color:#718C00;">"ch.qos.logback.core.rolling.SizeAndTimeBasedRollingPolicy"</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">fileNamePattern</span>&gt;</span>logs/${logName}-%d{yyyy-MM-dd}.%i.log.zip<span class="tag" style="color:#C82829;">&lt;/<span class="name">fileNamePattern</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">maxFileSize</span>&gt;</span>100MB<span class="tag" style="color:#C82829;">&lt;/<span class="name">maxFileSize</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">maxHistory</span>&gt;</span>7<span class="tag" style="color:#C82829;">&lt;/<span class="name">maxHistory</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">totalSizeCap</span>&gt;</span>3GB<span class="tag" style="color:#C82829;">&lt;/<span class="name">totalSizeCap</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;/<span class="name">rollingPolicy</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">encoder</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">pattern</span>&gt;</span>[%date{yyyy-MM-dd HH:mm:ss}] [%-5level] [%logger:%line] &amp;#45;&amp;#45;%mdc{client} %msg%n<span class="tag" style="color:#C82829;">&lt;/<span class="name">pattern</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;/<span class="name">encoder</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">filter</span> <span class="attr">class</span>=<span class="string" style="color:#718C00;">"ch.qos.logback.classic.filter.LevelFilter"</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">level</span>&gt;</span>DEBUG<span class="tag" style="color:#C82829;">&lt;/<span class="name">level</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;/<span class="name">filter</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;/<span class="name">appender</span>&gt;</span>
				</div>
</pre>
			</td>
		</tr>
	</tbody>
</table>
</figure>
<p style="margin-top:0px;margin-bottom:20px;color:#555555;font-family:Lato, &quot;font-size:16px;text-align:justify;white-space:normal;background-color:#FFFFFF;">
	将RelaxedPropertyResolver用于访问环境属性。如果使用虚线符号指定source（my-property-name）所有的变化都会被尝试（myPropertyName，MY_PROPERTY_NAME等）。
</p>
<h2 id="logback-spring-xml" style="margin:20px 0px 15px;padding:10px 0px 0px;line-height:1.5;font-family:Lato, &quot;font-size:20px;color:#555555;text-align:justify;white-space:normal;background-color:#FFFFFF;">
	<a href="http://blog.battcn.com/2017/07/25/springboot/springboot-logbak-config/#logback-spring-xml" class="headerlink" title="- logback-spring.xml" style="background-color:transparent;color:#555555;text-decoration-line:none;border-bottom:1px solid #999999;word-wrap:break-word;"></a>- logback-spring.xml
</h2>
<figure class="highlight xml" style="margin:5px 0px;overflow:auto;padding:5px;font-size:13px;color:#4D4D4C;background:#F7F7F7;line-height:1.6;border-radius:3px;border:1px solid #D6D6D6;font-family:Lato, &quot;text-align:justify;white-space:normal;">
<table style="border-spacing:0px;margin:0px;width:auto;border:none;font-size:14px;table-layout:fixed;">
	<tbody>
		<tr style="background-color:#F5F5F5;">
			<td class="gutter" style="padding:0px;vertical-align:middle;border:none;user-select:none;">
<pre style="overflow:auto;font-family:consolas, Menlo, &quot;font-size:13px;margin-top:0px;margin-bottom:0px;padding:10px;color:#869194;background:#EFF2F3;line-height:1.6;border-radius:3px;border:none;text-align:right;">
				<div class="line" style="height:20px;">
					1
				</div>

				<div class="line" style="height:20px;">
					2
				</div>

				<div class="line" style="height:20px;">
					3
				</div>

				<div class="line" style="height:20px;">
					4
				</div>

				<div class="line" style="height:20px;">
					5
				</div>

				<div class="line" style="height:20px;">
					6
				</div>

				<div class="line" style="height:20px;">
					7
				</div>

				<div class="line" style="height:20px;">
					8
				</div>

				<div class="line" style="height:20px;">
					9
				</div>

				<div class="line" style="height:20px;">
					10
				</div>

				<div class="line" style="height:20px;">
					11
				</div>

				<div class="line" style="height:20px;">
					12
				</div>

				<div class="line" style="height:20px;">
					13
				</div>

				<div class="line" style="height:20px;">
					14
				</div>

				<div class="line" style="height:20px;">
					15
				</div>

				<div class="line" style="height:20px;">
					16
				</div>

				<div class="line" style="height:20px;">
					17
				</div>

				<div class="line" style="height:20px;">
					18
				</div>

				<div class="line" style="height:20px;">
					19
				</div>

				<div class="line" style="height:20px;">
					20
				</div>

				<div class="line" style="height:20px;">
					21
				</div>

				<div class="line" style="height:20px;">
					22
				</div>

				<div class="line" style="height:20px;">
					23
				</div>

				<div class="line" style="height:20px;">
					24
				</div>

				<div class="line" style="height:20px;">
					25
				</div>

				<div class="line" style="height:20px;">
					26
				</div>

				<div class="line" style="height:20px;">
					27
				</div>

				<div class="line" style="height:20px;">
					28
				</div>

				<div class="line" style="height:20px;">
					29
				</div>

				<div class="line" style="height:20px;">
					30
				</div>

				<div class="line" style="height:20px;">
					31
				</div>

				<div class="line" style="height:20px;">
					32
				</div>

				<div class="line" style="height:20px;">
					33
				</div>

				<div class="line" style="height:20px;">
					34
				</div>

				<div class="line" style="height:20px;">
					35
				</div>

				<div class="line" style="height:20px;">
					36
				</div>

				<div class="line" style="height:20px;">
					37
				</div>

				<div class="line" style="height:20px;">
					38
				</div>

				<div class="line" style="height:20px;">
					39
				</div>

				<div class="line" style="height:20px;">
					40
				</div>

				<div class="line" style="height:20px;">
					41
				</div>

				<div class="line" style="height:20px;">
					42
				</div>

				<div class="line" style="height:20px;">
					43
				</div>

				<div class="line" style="height:20px;">
					44
				</div>

				<div class="line" style="height:20px;">
					45
				</div>

				<div class="line" style="height:20px;">
					46
				</div>

				<div class="line" style="height:20px;">
					47
				</div>

				<div class="line" style="height:20px;">
					48
				</div>

				<div class="line" style="height:20px;">
					49
				</div>

				<div class="line" style="height:20px;">
					50
				</div>

				<div class="line" style="height:20px;">
					51
				</div>

				<div class="line" style="height:20px;">
					52
				</div>

				<div class="line" style="height:20px;">
					53
				</div>
</pre>
			</td>
			<td class="code" style="padding:0px;vertical-align:middle;border:none;">
<pre style="overflow:auto;font-family:consolas, Menlo, &quot;font-size:13px;margin-top:0px;margin-bottom:0px;padding:10px;color:#4D4D4C;background:#F7F7F7;line-height:1.6;border-radius:3px;border:none;width:850px;">
				<div class="line" style="height:20px;">
					&lt;?xml version="1.0" encoding="UTF-8"?&gt;
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">configuration</span> <span class="attr">scan</span>=<span class="string" style="color:#718C00;">"true"</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">springProperty</span> <span class="attr">scope</span>=<span class="string" style="color:#718C00;">"context"</span> <span class="attr">name</span>=<span class="string" style="color:#718C00;">"logName"</span> <span class="attr">source</span>=<span class="string" style="color:#718C00;">"spring.application.name"</span> <span class="attr">defaultValue</span>=<span class="string" style="color:#718C00;">"localhost.log"</span>/&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">appender</span> <span class="attr">name</span>=<span class="string" style="color:#718C00;">"FILE"</span> <span class="attr">class</span>=<span class="string" style="color:#718C00;">"ch.qos.logback.core.rolling.RollingFileAppender"</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">file</span>&gt;</span>logs/${logName}.log<span class="tag" style="color:#C82829;">&lt;/<span class="name">file</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">append</span>&gt;</span>true<span class="tag" style="color:#C82829;">&lt;/<span class="name">append</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">rollingPolicy</span> <span class="attr">class</span>=<span class="string" style="color:#718C00;">"ch.qos.logback.core.rolling.SizeAndTimeBasedRollingPolicy"</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">fileNamePattern</span>&gt;</span>logs/${logName}-%d{yyyy-MM-dd}.%i.log.zip<span class="tag" style="color:#C82829;">&lt;/<span class="name">fileNamePattern</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">maxFileSize</span>&gt;</span>100MB<span class="tag" style="color:#C82829;">&lt;/<span class="name">maxFileSize</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">maxHistory</span>&gt;</span>7<span class="tag" style="color:#C82829;">&lt;/<span class="name">maxHistory</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">totalSizeCap</span>&gt;</span>3GB<span class="tag" style="color:#C82829;">&lt;/<span class="name">totalSizeCap</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;/<span class="name">rollingPolicy</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">encoder</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">pattern</span>&gt;</span>[%date{yyyy-MM-dd HH:mm:ss}] [%-5level] [%logger:%line] &amp;#45;&amp;#45;%mdc{client} %msg%n<span class="tag" style="color:#C82829;">&lt;/<span class="name">pattern</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;/<span class="name">encoder</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">filter</span> <span class="attr">class</span>=<span class="string" style="color:#718C00;">"ch.qos.logback.classic.filter.LevelFilter"</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">level</span>&gt;</span>DEBUG<span class="tag" style="color:#C82829;">&lt;/<span class="name">level</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;/<span class="name">filter</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;/<span class="name">appender</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="comment" style="color:#8E908C;">&lt;!-- Console output --&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">appender</span> <span class="attr">name</span>=<span class="string" style="color:#718C00;">"STDOUT"</span> <span class="attr">class</span>=<span class="string" style="color:#718C00;">"ch.qos.logback.core.ConsoleAppender"</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">encoder</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">pattern</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					[ %-5level] [%date{yyyy-MM-dd HH:mm:ss}] %logger{96} [%line] - %msg%n
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;/<span class="name">pattern</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">charset</span>&gt;</span>UTF-8<span class="tag" style="color:#C82829;">&lt;/<span class="name">charset</span>&gt;</span> <span class="comment" style="color:#8E908C;">&lt;!-- 此处设置字符集 --&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;/<span class="name">encoder</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">filter</span> <span class="attr">class</span>=<span class="string" style="color:#718C00;">"ch.qos.logback.classic.filter.ThresholdFilter"</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">level</span>&gt;</span>DEBUG<span class="tag" style="color:#C82829;">&lt;/<span class="name">level</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;/<span class="name">filter</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;/<span class="name">appender</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">springProfile</span> <span class="attr">name</span>=<span class="string" style="color:#718C00;">"dev,test"</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">root</span> <span class="attr">level</span>=<span class="string" style="color:#718C00;">"DEBUG"</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">appender-ref</span> <span class="attr">ref</span>=<span class="string" style="color:#718C00;">"FILE"</span>/&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">appender-ref</span> <span class="attr">ref</span>=<span class="string" style="color:#718C00;">"STDOUT"</span>/&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;/<span class="name">root</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;/<span class="name">springProfile</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">springProfile</span> <span class="attr">name</span>=<span class="string" style="color:#718C00;">"prod"</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">root</span> <span class="attr">level</span>=<span class="string" style="color:#718C00;">"INFO"</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">appender-ref</span> <span class="attr">ref</span>=<span class="string" style="color:#718C00;">"FILE"</span>/&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">appender-ref</span> <span class="attr">ref</span>=<span class="string" style="color:#718C00;">"STDOUT"</span>/&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;/<span class="name">root</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;/<span class="name">springProfile</span>&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">logger</span> <span class="attr">name</span>=<span class="string" style="color:#718C00;">"org.springframework"</span> <span class="attr">level</span>=<span class="string" style="color:#718C00;">"INFO"</span>/&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">logger</span> <span class="attr">name</span>=<span class="string" style="color:#718C00;">"com.netflix"</span> <span class="attr">level</span>=<span class="string" style="color:#718C00;">"WARN"</span>/&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">logger</span> <span class="attr">name</span>=<span class="string" style="color:#718C00;">"org"</span> <span class="attr">level</span>=<span class="string" style="color:#718C00;">"INFO"</span>/&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;<span class="name">logger</span> <span class="attr">name</span>=<span class="string" style="color:#718C00;">"springfox.documentation"</span> <span class="attr">level</span>=<span class="string" style="color:#718C00;">"INFO"</span>/&gt;</span>
				</div>

				<div class="line" style="height:20px;">
					
				</div>

				<div class="line" style="height:20px;">
					<span class="tag" style="color:#C82829;">&lt;/<span class="name">configuration</span>&gt;</span>
				</div>
</pre>
			</td>
		</tr>
	</tbody>
</table>
</figure>