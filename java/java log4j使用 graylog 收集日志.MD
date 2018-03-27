<p>
	https://github.com/graylog-labs/log4j2-gelf
</p>
<p>
	<br />
</p>
<p>
	<br />
</p>
<p>
<pre style="box-sizing:border-box;font-family:SFMono-Regular, Consolas, &quot;font-size:13.6px;margin-top:0px;margin-bottom:16px;word-wrap:normal;padding:16px;overflow:auto;line-height:1.45;background-color:#F6F8FA;border-radius:3px;color:#24292E;"><code style="box-sizing:border-box;font-family:SFMono-Regular, Consolas, &quot;font-size:13.6px;padding:0px;margin:0px;background:transparent;border-radius:3px;word-break:normal;border:0px;display:inline;overflow:visible;line-height:inherit;word-wrap:normal;">&lt;?xml version="1.0" encoding="UTF-8"?&gt;
&lt;Configuration status="OFF" packages="org.graylog2.log4j2"&gt;
    &lt;Appenders&gt;
        &lt;GELF name="gelfAppender" server="graylog2.example.com" port="12201" hostName="appserver01.example.com"&gt;
            &lt;PatternLayout pattern="%logger{36} - %msg%n"/&gt;
            &lt;Filters&gt;
                &lt;Filter type="MarkerFilter" marker="FLOW" onMatch="DENY" onMismatch="NEUTRAL"/&gt;
                &lt;Filter type="MarkerFilter" marker="EXCEPTION" onMatch="DENY" onMismatch="ACCEPT"/&gt;
            &lt;/Filters&gt;
            &lt;!-- Additional fields --&gt;
            &lt;KeyValuePair key="foo" value="bar"/&gt;
            &lt;KeyValuePair key="jvm" value="${java:vm}"/&gt;                
        &lt;/GELF&gt;
    &lt;/Appenders&gt;
    &lt;Loggers&gt;
        &lt;Root level="info"&gt;
            &lt;AppenderRef ref="gelfAppender"/&gt;
        &lt;/Root&gt;
    &lt;/Loggers&gt; </code>
	<p>
		<code style="box-sizing:border-box;font-family:SFMono-Regular, Consolas, &quot;font-size:13.6px;padding:0px;margin:0px;background:transparent;border-radius:3px;word-break:normal;border:0px;display:inline;overflow:visible;line-height:inherit;word-wrap:normal;">&lt;/Configuration&gt;</code>
	</p>

	<p>
		<code style="box-sizing:border-box;font-family:SFMono-Regular, Consolas, &quot;font-size:13.6px;padding:0px;margin:0px;background:transparent;border-radius:3px;word-break:normal;border:0px;display:inline;overflow:visible;line-height:inherit;word-wrap:normal;"> </code>
	</p>

	<p>
		<code style="box-sizing:border-box;font-family:SFMono-Regular, Consolas, &quot;font-size:13.6px;padding:0px;margin:0px;background:transparent;border-radius:3px;word-break:normal;border:0px;display:inline;overflow:visible;line-height:inherit;word-wrap:normal;">pom.xml</code>
	</p>

	<p>
		<code style="box-sizing:border-box;font-family:SFMono-Regular, Consolas, &quot;font-size:13.6px;padding:0px;margin:0px;background:transparent;border-radius:3px;word-break:normal;border:0px;display:inline;overflow:visible;line-height:inherit;word-wrap:normal;"> </code>
	</p>

	<p>
		<code style="box-sizing:border-box;font-family:SFMono-Regular, Consolas, &quot;font-size:13.6px;padding:0px;margin:0px;background:transparent;border-radius:3px;word-break:normal;border:0px;display:inline;overflow:visible;line-height:inherit;word-wrap:normal;">
<pre style="box-sizing:border-box;font-family:SFMono-Regular, Consolas, &quot;font-size:13.6px;margin-top:0px;margin-bottom:16px;word-wrap:normal;padding:16px;overflow:auto;line-height:1.45;background-color:#F6F8FA;border-radius:3px;color:#24292E;"><code style="box-sizing:border-box;font-family:SFMono-Regular, Consolas, &quot;font-size:13.6px;padding:0px;margin:0px;background:transparent;border-radius:3px;word-break:normal;border:0px;display:inline;overflow:visible;line-height:inherit;word-wrap:normal;">&lt;dependencies&gt;
    &lt;dependency&gt;
        &lt;groupId&gt;org.graylog2.log4j2&lt;/groupId&gt;
        &lt;artifactId&gt;log4j2-gelf&lt;/artifactId&gt;
        &lt;version&gt;1.3.1&lt;/version&gt;
    &lt;/dependency&gt;
&lt;/dependencies&gt;</code></pre>
<br />
</code>
	</p>
	<p>
		<code style="box-sizing:border-box;font-family:SFMono-Regular, Consolas, &quot;font-size:13.6px;padding:0px;margin:0px;background:transparent;border-radius:3px;word-break:normal;border:0px;display:inline;overflow:visible;line-height:inherit;word-wrap:normal;"><br />
</code>
	</p>
	<p>
		<code style="box-sizing:border-box;font-family:SFMono-Regular, Consolas, &quot;font-size:13.6px;padding:0px;margin:0px;background:transparent;border-radius:3px;word-break:normal;border:0px;display:inline;overflow:visible;line-height:inherit;word-wrap:normal;"><br />
</code>
	</p>
	<p>
		<code style="box-sizing:border-box;font-family:SFMono-Regular, Consolas, &quot;font-size:13.6px;padding:0px;margin:0px;background:transparent;border-radius:3px;word-break:normal;border:0px;display:inline;overflow:visible;line-height:inherit;word-wrap:normal;"><br />
</code>
	</p>
</pre>
</p>