<p>
	https://github.com/osiegmar/logback-gelf
</p>
<p>
	<br />
</p>
<p>
	<h1 style="box-sizing:border-box;margin-right:0px;margin-bottom:16px;margin-left:0px;line-height:1.25;padding-bottom:0.3em;border-bottom:1px solid #EAECEF;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;white-space:normal;margin-top:0px !important;">
		Logback GELF
	</h1>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:16px;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;font-size:16px;white-space:normal;">
		<a href="https://travis-ci.org/osiegmar/logback-gelf" style="box-sizing:border-box;color:#0366D6;text-decoration-line:none;"><img src="https://api.travis-ci.org/osiegmar/logback-gelf.svg" alt="Build Status" data-canonical-src="https://api.travis-ci.org/osiegmar/logback-gelf.svg" style="box-sizing:content-box;border-style:none;max-width:100%;background-color:#FFFFFF;" /></a>&nbsp;<a href="https://maven-badges.herokuapp.com/maven-central/de.siegmar/logback-gelf" style="box-sizing:border-box;color:#0366D6;text-decoration-line:none;"><img src="https://maven-badges.herokuapp.com/maven-central/de.siegmar/logback-gelf/badge.svg" alt="Maven Central" data-canonical-src="https://maven-badges.herokuapp.com/maven-central/de.siegmar/logback-gelf/badge.svg" style="box-sizing:content-box;border-style:none;max-width:100%;background-color:#FFFFFF;" /></a>
	</p>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:16px;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;font-size:16px;white-space:normal;">
		Logback appender for sending GELF (Graylog Extended Log Format) messages with zero additional dependencies.
	</p>
	<h2 style="box-sizing:border-box;margin-top:24px;margin-bottom:16px;line-height:1.25;padding-bottom:0.3em;border-bottom:1px solid #EAECEF;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;white-space:normal;">
		<a href="https://github.com/osiegmar/logback-gelf#latest-release" aria-hidden="true" class="anchor" id="user-content-latest-release" style="box-sizing:border-box;color:#0366D6;text-decoration-line:none;float:left;padding-right:4px;margin-left:-20px;line-height:1;"><svg aria-hidden="true" class="octicon octicon-link" height="16" version="1.1" viewbox="0 0 16 16" width="16"><path fill-rule="evenodd" d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"></path></svg></a>Latest release
	</h2>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:16px;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;font-size:16px;white-space:normal;">
		The most recent release is 1.0.4, released April 3, 2017.
	</p>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:16px;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;font-size:16px;white-space:normal;">
		To add a dependency using Maven, use the following:
	</p>
	<div class="highlight highlight-text-xml" style="box-sizing:border-box;margin-bottom:16px;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;font-size:16px;white-space:normal;">
<pre style="box-sizing:border-box;font-family:SFMono-Regular, Consolas, &quot;font-size:13.6px;margin-top:0px;margin-bottom:0px;word-wrap:normal;padding:16px;overflow:auto;line-height:1.45;background-color:#F6F8FA;border-radius:3px;word-break:normal;">&lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">dependency</span>&gt;
    &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">groupId</span>&gt;de.siegmar&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">groupId</span>&gt;
    &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">artifactId</span>&gt;logback-gelf&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">artifactId</span>&gt;
    &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">version</span>&gt;1.0.4&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">version</span>&gt;
&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">dependency</span>&gt;</pre>
	</div>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:16px;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;font-size:16px;white-space:normal;">
		To add a dependency using Gradle:
	</p>
	<div class="highlight highlight-source-groovy-gradle" style="box-sizing:border-box;margin-bottom:16px;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;font-size:16px;white-space:normal;">
<pre style="box-sizing:border-box;font-family:SFMono-Regular, Consolas, &quot;font-size:13.6px;margin-top:0px;margin-bottom:0px;word-wrap:normal;padding:16px;overflow:auto;line-height:1.45;background-color:#F6F8FA;border-radius:3px;word-break:normal;"><span class="pl-en" style="box-sizing:border-box;color:#6F42C1;">dependencies</span> {
    compile <span class="pl-s" style="box-sizing:border-box;color:#032F62;"><span class="pl-pds" style="box-sizing:border-box;">'</span>de.siegmar:logback-gelf:1.0.4<span class="pl-pds" style="box-sizing:border-box;">'</span></span> }</pre>
	</div>
	<h2 style="box-sizing:border-box;margin-top:24px;margin-bottom:16px;line-height:1.25;padding-bottom:0.3em;border-bottom:1px solid #EAECEF;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;white-space:normal;">
		<a href="https://github.com/osiegmar/logback-gelf#features" aria-hidden="true" class="anchor" id="user-content-features" style="box-sizing:border-box;color:#0366D6;text-decoration-line:none;float:left;padding-right:4px;margin-left:-20px;line-height:1;"><svg aria-hidden="true" class="octicon octicon-link" height="16" version="1.1" viewbox="0 0 16 16" width="16"><path fill-rule="evenodd" d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"></path></svg></a>Features
	</h2>
	<ul style="box-sizing:border-box;padding-left:2em;margin-top:0px;margin-bottom:16px;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;font-size:16px;white-space:normal;">
		<li style="box-sizing:border-box;">
			UDP (with chunking)
		</li>
		<li style="box-sizing:border-box;margin-top:0.25em;">
			TCP (with or without TLS encryption)
		</li>
		<li style="box-sizing:border-box;margin-top:0.25em;">
			Deflate compression in UDP mode
		</li>
		<li style="box-sizing:border-box;margin-top:0.25em;">
			Forwarding of MDC (Mapped Diagnostic Context)
		</li>
		<li style="box-sizing:border-box;margin-top:0.25em;">
			Forwarding of caller data
		</li>
		<li style="box-sizing:border-box;margin-top:0.25em;">
			Forwarding of static fields
		</li>
		<li style="box-sizing:border-box;margin-top:0.25em;">
			Forwarding of exception root cause
		</li>
		<li style="box-sizing:border-box;margin-top:0.25em;">
			No runtime dependencies beside Logback
		</li>
	</ul>
	<h2 style="box-sizing:border-box;margin-top:24px;margin-bottom:16px;line-height:1.25;padding-bottom:0.3em;border-bottom:1px solid #EAECEF;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;white-space:normal;">
		<a href="https://github.com/osiegmar/logback-gelf#requirements" aria-hidden="true" class="anchor" id="user-content-requirements" style="box-sizing:border-box;color:#0366D6;text-decoration-line:none;float:left;padding-right:4px;margin-left:-20px;line-height:1;"><svg aria-hidden="true" class="octicon octicon-link" height="16" version="1.1" viewbox="0 0 16 16" width="16"><path fill-rule="evenodd" d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"></path></svg></a>Requirements
	</h2>
	<ul style="box-sizing:border-box;padding-left:2em;margin-top:0px;margin-bottom:16px;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;font-size:16px;white-space:normal;">
		<li style="box-sizing:border-box;">
			Java 7
		</li>
		<li style="box-sizing:border-box;margin-top:0.25em;">
			Logback 1.1.3 (or later)
		</li>
	</ul>
	<h2 style="box-sizing:border-box;margin-top:24px;margin-bottom:16px;line-height:1.25;padding-bottom:0.3em;border-bottom:1px solid #EAECEF;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;white-space:normal;">
		<a href="https://github.com/osiegmar/logback-gelf#example" aria-hidden="true" class="anchor" id="user-content-example" style="box-sizing:border-box;color:#0366D6;text-decoration-line:none;float:left;padding-right:4px;margin-left:-20px;line-height:1;"><svg aria-hidden="true" class="octicon octicon-link" height="16" version="1.1" viewbox="0 0 16 16" width="16"><path fill-rule="evenodd" d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"></path></svg></a>Example
	</h2>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:16px;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;font-size:16px;white-space:normal;">
		Simple UDP configuration:
	</p>
	<div class="highlight highlight-text-xml" style="box-sizing:border-box;margin-bottom:16px;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;font-size:16px;white-space:normal;">
<pre style="box-sizing:border-box;font-family:SFMono-Regular, Consolas, &quot;font-size:13.6px;margin-top:0px;margin-bottom:0px;word-wrap:normal;padding:16px;overflow:auto;line-height:1.45;background-color:#F6F8FA;border-radius:3px;word-break:normal;">&lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">configuration</span>&gt;

    &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">appender</span> <span class="pl-e" style="box-sizing:border-box;color:#6F42C1;">name</span>=<span class="pl-s" style="box-sizing:border-box;color:#032F62;"><span class="pl-pds" style="box-sizing:border-box;">"</span>GELF<span class="pl-pds" style="box-sizing:border-box;">"</span></span> <span class="pl-e" style="box-sizing:border-box;color:#6F42C1;">class</span>=<span class="pl-s" style="box-sizing:border-box;color:#032F62;"><span class="pl-pds" style="box-sizing:border-box;">"</span>de.siegmar.logbackgelf.GelfUdpAppender<span class="pl-pds" style="box-sizing:border-box;">"</span></span>&gt;
        &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">graylogHost</span>&gt;localhost&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">graylogHost</span>&gt;
        &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">graylogPort</span>&gt;12201&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">graylogPort</span>&gt;
    &lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">appender</span>&gt;

    &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">root</span> <span class="pl-e" style="box-sizing:border-box;color:#6F42C1;">level</span>=<span class="pl-s" style="box-sizing:border-box;color:#032F62;"><span class="pl-pds" style="box-sizing:border-box;">"</span>debug<span class="pl-pds" style="box-sizing:border-box;">"</span></span>&gt;
        &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">appender-ref</span> <span class="pl-e" style="box-sizing:border-box;color:#6F42C1;">ref</span>=<span class="pl-s" style="box-sizing:border-box;color:#032F62;"><span class="pl-pds" style="box-sizing:border-box;">"</span>GELF<span class="pl-pds" style="box-sizing:border-box;">"</span></span> /&gt;
    &lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">root</span>&gt;

&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">configuration</span>&gt;</pre>
	</div>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:16px;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;font-size:16px;white-space:normal;">
		Simple TCP configuration:
	</p>
	<div class="highlight highlight-text-xml" style="box-sizing:border-box;margin-bottom:16px;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;font-size:16px;white-space:normal;">
<pre style="box-sizing:border-box;font-family:SFMono-Regular, Consolas, &quot;font-size:13.6px;margin-top:0px;margin-bottom:0px;word-wrap:normal;padding:16px;overflow:auto;line-height:1.45;background-color:#F6F8FA;border-radius:3px;word-break:normal;">&lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">configuration</span>&gt;

    &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">appender</span> <span class="pl-e" style="box-sizing:border-box;color:#6F42C1;">name</span>=<span class="pl-s" style="box-sizing:border-box;color:#032F62;"><span class="pl-pds" style="box-sizing:border-box;">"</span>GELF<span class="pl-pds" style="box-sizing:border-box;">"</span></span> <span class="pl-e" style="box-sizing:border-box;color:#6F42C1;">class</span>=<span class="pl-s" style="box-sizing:border-box;color:#032F62;"><span class="pl-pds" style="box-sizing:border-box;">"</span>de.siegmar.logbackgelf.GelfTcpAppender<span class="pl-pds" style="box-sizing:border-box;">"</span></span>&gt;
        &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">graylogHost</span>&gt;localhost&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">graylogHost</span>&gt;
        &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">graylogPort</span>&gt;12201&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">graylogPort</span>&gt;
    &lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">appender</span>&gt;

    &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">root</span> <span class="pl-e" style="box-sizing:border-box;color:#6F42C1;">level</span>=<span class="pl-s" style="box-sizing:border-box;color:#032F62;"><span class="pl-pds" style="box-sizing:border-box;">"</span>debug<span class="pl-pds" style="box-sizing:border-box;">"</span></span>&gt;
        &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">appender-ref</span> <span class="pl-e" style="box-sizing:border-box;color:#6F42C1;">ref</span>=<span class="pl-s" style="box-sizing:border-box;color:#032F62;"><span class="pl-pds" style="box-sizing:border-box;">"</span>GELF<span class="pl-pds" style="box-sizing:border-box;">"</span></span> /&gt;
    &lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">root</span>&gt;

&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">configuration</span>&gt;</pre>
	</div>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:16px;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;font-size:16px;white-space:normal;">
		Simple TCP with TLS configuration:
	</p>
	<div class="highlight highlight-text-xml" style="box-sizing:border-box;margin-bottom:16px;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;font-size:16px;white-space:normal;">
<pre style="box-sizing:border-box;font-family:SFMono-Regular, Consolas, &quot;font-size:13.6px;margin-top:0px;margin-bottom:0px;word-wrap:normal;padding:16px;overflow:auto;line-height:1.45;background-color:#F6F8FA;border-radius:3px;word-break:normal;">&lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">configuration</span>&gt;

    &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">appender</span> <span class="pl-e" style="box-sizing:border-box;color:#6F42C1;">name</span>=<span class="pl-s" style="box-sizing:border-box;color:#032F62;"><span class="pl-pds" style="box-sizing:border-box;">"</span>GELF<span class="pl-pds" style="box-sizing:border-box;">"</span></span> <span class="pl-e" style="box-sizing:border-box;color:#6F42C1;">class</span>=<span class="pl-s" style="box-sizing:border-box;color:#032F62;"><span class="pl-pds" style="box-sizing:border-box;">"</span>de.siegmar.logbackgelf.GelfTcpTlsAppender<span class="pl-pds" style="box-sizing:border-box;">"</span></span>&gt;
        &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">graylogHost</span>&gt;localhost&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">graylogHost</span>&gt;
        &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">graylogPort</span>&gt;12201&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">graylogPort</span>&gt;
    &lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">appender</span>&gt;

    &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">root</span> <span class="pl-e" style="box-sizing:border-box;color:#6F42C1;">level</span>=<span class="pl-s" style="box-sizing:border-box;color:#032F62;"><span class="pl-pds" style="box-sizing:border-box;">"</span>debug<span class="pl-pds" style="box-sizing:border-box;">"</span></span>&gt;
        &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">appender-ref</span> <span class="pl-e" style="box-sizing:border-box;color:#6F42C1;">ref</span>=<span class="pl-s" style="box-sizing:border-box;color:#032F62;"><span class="pl-pds" style="box-sizing:border-box;">"</span>GELF<span class="pl-pds" style="box-sizing:border-box;">"</span></span> /&gt;
    &lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">root</span>&gt;

&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">configuration</span>&gt;</pre>
	</div>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:16px;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;font-size:16px;white-space:normal;">
		<span style="box-sizing:border-box;font-weight:600;">Please note, that it is recommended to use Logback's AsyncAppender in conjunction with GelfTcpAppender or GelfTcpTlsAppender to send logs asynchronously. See the advanced configuration example below.</span>
	</p>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:16px;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;font-size:16px;white-space:normal;">
		Advanced UDP configuration:
	</p>
	<div class="highlight highlight-text-xml" style="box-sizing:border-box;margin-bottom:16px;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;font-size:16px;white-space:normal;">
<pre style="box-sizing:border-box;font-family:SFMono-Regular, Consolas, &quot;font-size:13.6px;margin-top:0px;margin-bottom:0px;word-wrap:normal;padding:16px;overflow:auto;line-height:1.45;background-color:#F6F8FA;border-radius:3px;word-break:normal;">&lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">configuration</span>&gt;

    &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">appender</span> <span class="pl-e" style="box-sizing:border-box;color:#6F42C1;">name</span>=<span class="pl-s" style="box-sizing:border-box;color:#032F62;"><span class="pl-pds" style="box-sizing:border-box;">"</span>GELF<span class="pl-pds" style="box-sizing:border-box;">"</span></span> <span class="pl-e" style="box-sizing:border-box;color:#6F42C1;">class</span>=<span class="pl-s" style="box-sizing:border-box;color:#032F62;"><span class="pl-pds" style="box-sizing:border-box;">"</span>de.siegmar.logbackgelf.GelfUdpAppender<span class="pl-pds" style="box-sizing:border-box;">"</span></span>&gt;
        &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">graylogHost</span>&gt;localhost&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">graylogHost</span>&gt;
        &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">graylogPort</span>&gt;12201&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">graylogPort</span>&gt;
        &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">maxChunkSize</span>&gt;508&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">maxChunkSize</span>&gt;
        &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">useCompression</span>&gt;true&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">useCompression</span>&gt;
        &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">layout</span> <span class="pl-e" style="box-sizing:border-box;color:#6F42C1;">class</span>=<span class="pl-s" style="box-sizing:border-box;color:#032F62;"><span class="pl-pds" style="box-sizing:border-box;">"</span>de.siegmar.logbackgelf.GelfLayout<span class="pl-pds" style="box-sizing:border-box;">"</span></span>&gt;
            &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">originHost</span>&gt;localhost&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">originHost</span>&gt;
            &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">includeRawMessage</span>&gt;false&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">includeRawMessage</span>&gt;
            &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">includeMarker</span>&gt;true&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">includeMarker</span>&gt;
            &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">includeMdcData</span>&gt;true&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">includeMdcData</span>&gt;
            &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">includeCallerData</span>&gt;false&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">includeCallerData</span>&gt;
            &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">includeRootCauseData</span>&gt;false&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">includeRootCauseData</span>&gt;
            &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">includeLevelName</span>&gt;false&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">includeLevelName</span>&gt;
            &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">shortPatternLayout</span> <span class="pl-e" style="box-sizing:border-box;color:#6F42C1;">class</span>=<span class="pl-s" style="box-sizing:border-box;color:#032F62;"><span class="pl-pds" style="box-sizing:border-box;">"</span>ch.qos.logback.classic.PatternLayout<span class="pl-pds" style="box-sizing:border-box;">"</span></span>&gt;
                &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">pattern</span>&gt;%m%nopex&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">pattern</span>&gt;
            &lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">shortPatternLayout</span>&gt;
            &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">fullPatternLayout</span> <span class="pl-e" style="box-sizing:border-box;color:#6F42C1;">class</span>=<span class="pl-s" style="box-sizing:border-box;color:#032F62;"><span class="pl-pds" style="box-sizing:border-box;">"</span>ch.qos.logback.classic.PatternLayout<span class="pl-pds" style="box-sizing:border-box;">"</span></span>&gt;
                &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">pattern</span>&gt;%m&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">pattern</span>&gt;
            &lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">fullPatternLayout</span>&gt;
            &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">staticField</span>&gt;app_name:backend&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">staticField</span>&gt;
            &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">staticField</span>&gt;os_arch:${os.arch}&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">staticField</span>&gt;
            &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">staticField</span>&gt;os_name:${os.name}&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">staticField</span>&gt;
            &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">staticField</span>&gt;os_version:${os.version}&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">staticField</span>&gt;
        &lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">layout</span>&gt;
    &lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">appender</span>&gt;

    &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">root</span> <span class="pl-e" style="box-sizing:border-box;color:#6F42C1;">level</span>=<span class="pl-s" style="box-sizing:border-box;color:#032F62;"><span class="pl-pds" style="box-sizing:border-box;">"</span>debug<span class="pl-pds" style="box-sizing:border-box;">"</span></span>&gt;
        &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">appender-ref</span> <span class="pl-e" style="box-sizing:border-box;color:#6F42C1;">ref</span>=<span class="pl-s" style="box-sizing:border-box;color:#032F62;"><span class="pl-pds" style="box-sizing:border-box;">"</span>GELF<span class="pl-pds" style="box-sizing:border-box;">"</span></span> /&gt;
    &lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">root</span>&gt;

&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">configuration</span>&gt;</pre>
	</div>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:16px;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;font-size:16px;white-space:normal;">
		Advanced TCP configuration:
	</p>
	<div class="highlight highlight-text-xml" style="box-sizing:border-box;margin-bottom:16px;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;font-size:16px;white-space:normal;">
<pre style="box-sizing:border-box;font-family:SFMono-Regular, Consolas, &quot;font-size:13.6px;margin-top:0px;margin-bottom:0px;word-wrap:normal;padding:16px;overflow:auto;line-height:1.45;background-color:#F6F8FA;border-radius:3px;word-break:normal;">&lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">configuration</span>&gt;

    &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">appender</span> <span class="pl-e" style="box-sizing:border-box;color:#6F42C1;">name</span>=<span class="pl-s" style="box-sizing:border-box;color:#032F62;"><span class="pl-pds" style="box-sizing:border-box;">"</span>GELF<span class="pl-pds" style="box-sizing:border-box;">"</span></span> <span class="pl-e" style="box-sizing:border-box;color:#6F42C1;">class</span>=<span class="pl-s" style="box-sizing:border-box;color:#032F62;"><span class="pl-pds" style="box-sizing:border-box;">"</span>de.siegmar.logbackgelf.GelfTcpAppender<span class="pl-pds" style="box-sizing:border-box;">"</span></span>&gt;
        &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">graylogHost</span>&gt;localhost&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">graylogHost</span>&gt;
        &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">graylogPort</span>&gt;12201&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">graylogPort</span>&gt;
        &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">connectTimeout</span>&gt;15000&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">connectTimeout</span>&gt;
        &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">reconnectInterval</span>&gt;300&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">reconnectInterval</span>&gt;
        &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">maxRetries</span>&gt;2&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">maxRetries</span>&gt;
        &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">retryDelay</span>&gt;3000&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">retryDelay</span>&gt;
        &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">layout</span> <span class="pl-e" style="box-sizing:border-box;color:#6F42C1;">class</span>=<span class="pl-s" style="box-sizing:border-box;color:#032F62;"><span class="pl-pds" style="box-sizing:border-box;">"</span>de.siegmar.logbackgelf.GelfLayout<span class="pl-pds" style="box-sizing:border-box;">"</span></span>&gt;
            &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">originHost</span>&gt;localhost&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">originHost</span>&gt;
            &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">includeRawMessage</span>&gt;false&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">includeRawMessage</span>&gt;
            &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">includeMarker</span>&gt;true&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">includeMarker</span>&gt;
            &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">includeMdcData</span>&gt;true&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">includeMdcData</span>&gt;
            &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">includeCallerData</span>&gt;false&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">includeCallerData</span>&gt;
            &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">includeRootCauseData</span>&gt;false&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">includeRootCauseData</span>&gt;
            &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">includeLevelName</span>&gt;false&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">includeLevelName</span>&gt;
            &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">shortPatternLayout</span> <span class="pl-e" style="box-sizing:border-box;color:#6F42C1;">class</span>=<span class="pl-s" style="box-sizing:border-box;color:#032F62;"><span class="pl-pds" style="box-sizing:border-box;">"</span>ch.qos.logback.classic.PatternLayout<span class="pl-pds" style="box-sizing:border-box;">"</span></span>&gt;
                &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">pattern</span>&gt;%m%nopex&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">pattern</span>&gt;
            &lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">shortPatternLayout</span>&gt;
            &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">fullPatternLayout</span> <span class="pl-e" style="box-sizing:border-box;color:#6F42C1;">class</span>=<span class="pl-s" style="box-sizing:border-box;color:#032F62;"><span class="pl-pds" style="box-sizing:border-box;">"</span>ch.qos.logback.classic.PatternLayout<span class="pl-pds" style="box-sizing:border-box;">"</span></span>&gt;
                &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">pattern</span>&gt;%m&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">pattern</span>&gt;
            &lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">fullPatternLayout</span>&gt;
            &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">staticField</span>&gt;app_name:backend&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">staticField</span>&gt;
            &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">staticField</span>&gt;os_arch:${os.arch}&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">staticField</span>&gt;
            &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">staticField</span>&gt;os_name:${os.name}&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">staticField</span>&gt;
            &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">staticField</span>&gt;os_version:${os.version}&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">staticField</span>&gt;
        &lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">layout</span>&gt;
    &lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">appender</span>&gt;

    &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">appender</span> <span class="pl-e" style="box-sizing:border-box;color:#6F42C1;">name</span>=<span class="pl-s" style="box-sizing:border-box;color:#032F62;"><span class="pl-pds" style="box-sizing:border-box;">"</span>ASYNC GELF<span class="pl-pds" style="box-sizing:border-box;">"</span></span> <span class="pl-e" style="box-sizing:border-box;color:#6F42C1;">class</span>=<span class="pl-s" style="box-sizing:border-box;color:#032F62;"><span class="pl-pds" style="box-sizing:border-box;">"</span>ch.qos.logback.classic.AsyncAppender<span class="pl-pds" style="box-sizing:border-box;">"</span></span>&gt;
        &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">appender-ref</span> <span class="pl-e" style="box-sizing:border-box;color:#6F42C1;">ref</span>=<span class="pl-s" style="box-sizing:border-box;color:#032F62;"><span class="pl-pds" style="box-sizing:border-box;">"</span>GELF<span class="pl-pds" style="box-sizing:border-box;">"</span></span> /&gt;
    &lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">appender</span>&gt;

    &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">root</span> <span class="pl-e" style="box-sizing:border-box;color:#6F42C1;">level</span>=<span class="pl-s" style="box-sizing:border-box;color:#032F62;"><span class="pl-pds" style="box-sizing:border-box;">"</span>debug<span class="pl-pds" style="box-sizing:border-box;">"</span></span>&gt;
        &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">appender-ref</span> <span class="pl-e" style="box-sizing:border-box;color:#6F42C1;">ref</span>=<span class="pl-s" style="box-sizing:border-box;color:#032F62;"><span class="pl-pds" style="box-sizing:border-box;">"</span>ASYNC GELF<span class="pl-pds" style="box-sizing:border-box;">"</span></span> /&gt;
    &lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">root</span>&gt;

&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">configuration</span>&gt;</pre>
	</div>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:16px;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;font-size:16px;white-space:normal;">
		Advanced TCP with TLS configuration:
	</p>
	<div class="highlight highlight-text-xml" style="box-sizing:border-box;margin-bottom:16px;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;font-size:16px;white-space:normal;">
<pre style="box-sizing:border-box;font-family:SFMono-Regular, Consolas, &quot;font-size:13.6px;margin-top:0px;margin-bottom:0px;word-wrap:normal;padding:16px;overflow:auto;line-height:1.45;background-color:#F6F8FA;border-radius:3px;word-break:normal;">&lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">configuration</span>&gt;

    &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">appender</span> <span class="pl-e" style="box-sizing:border-box;color:#6F42C1;">name</span>=<span class="pl-s" style="box-sizing:border-box;color:#032F62;"><span class="pl-pds" style="box-sizing:border-box;">"</span>GELF<span class="pl-pds" style="box-sizing:border-box;">"</span></span> <span class="pl-e" style="box-sizing:border-box;color:#6F42C1;">class</span>=<span class="pl-s" style="box-sizing:border-box;color:#032F62;"><span class="pl-pds" style="box-sizing:border-box;">"</span>de.siegmar.logbackgelf.GelfTcpTlsAppender<span class="pl-pds" style="box-sizing:border-box;">"</span></span>&gt;
        &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">graylogHost</span>&gt;localhost&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">graylogHost</span>&gt;
        &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">graylogPort</span>&gt;12201&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">graylogPort</span>&gt;
        &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">connectTimeout</span>&gt;15000&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">connectTimeout</span>&gt;
        &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">reconnectInterval</span>&gt;300&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">reconnectInterval</span>&gt;
        &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">maxRetries</span>&gt;2&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">maxRetries</span>&gt;
        &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">retryDelay</span>&gt;3000&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">retryDelay</span>&gt;
        &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">trustAllCertificates</span>&gt;false&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">trustAllCertificates</span>&gt;
        &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">layout</span> <span class="pl-e" style="box-sizing:border-box;color:#6F42C1;">class</span>=<span class="pl-s" style="box-sizing:border-box;color:#032F62;"><span class="pl-pds" style="box-sizing:border-box;">"</span>de.siegmar.logbackgelf.GelfLayout<span class="pl-pds" style="box-sizing:border-box;">"</span></span>&gt;
            &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">originHost</span>&gt;localhost&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">originHost</span>&gt;
            &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">includeRawMessage</span>&gt;false&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">includeRawMessage</span>&gt;
            &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">includeMarker</span>&gt;true&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">includeMarker</span>&gt;
            &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">includeMdcData</span>&gt;true&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">includeMdcData</span>&gt;
            &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">includeCallerData</span>&gt;false&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">includeCallerData</span>&gt;
            &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">includeRootCauseData</span>&gt;false&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">includeRootCauseData</span>&gt;
            &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">includeLevelName</span>&gt;false&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">includeLevelName</span>&gt;
            &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">shortPatternLayout</span> <span class="pl-e" style="box-sizing:border-box;color:#6F42C1;">class</span>=<span class="pl-s" style="box-sizing:border-box;color:#032F62;"><span class="pl-pds" style="box-sizing:border-box;">"</span>ch.qos.logback.classic.PatternLayout<span class="pl-pds" style="box-sizing:border-box;">"</span></span>&gt;
                &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">pattern</span>&gt;%m%nopex&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">pattern</span>&gt;
            &lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">shortPatternLayout</span>&gt;
            &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">fullPatternLayout</span> <span class="pl-e" style="box-sizing:border-box;color:#6F42C1;">class</span>=<span class="pl-s" style="box-sizing:border-box;color:#032F62;"><span class="pl-pds" style="box-sizing:border-box;">"</span>ch.qos.logback.classic.PatternLayout<span class="pl-pds" style="box-sizing:border-box;">"</span></span>&gt;
                &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">pattern</span>&gt;%m&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">pattern</span>&gt;
            &lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">fullPatternLayout</span>&gt;
            &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">staticField</span>&gt;app_name:backend&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">staticField</span>&gt;
            &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">staticField</span>&gt;os_arch:${os.arch}&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">staticField</span>&gt;
            &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">staticField</span>&gt;os_name:${os.name}&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">staticField</span>&gt;
            &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">staticField</span>&gt;os_version:${os.version}&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">staticField</span>&gt;
        &lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">layout</span>&gt;
    &lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">appender</span>&gt;

    &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">appender</span> <span class="pl-e" style="box-sizing:border-box;color:#6F42C1;">name</span>=<span class="pl-s" style="box-sizing:border-box;color:#032F62;"><span class="pl-pds" style="box-sizing:border-box;">"</span>ASYNC GELF<span class="pl-pds" style="box-sizing:border-box;">"</span></span> <span class="pl-e" style="box-sizing:border-box;color:#6F42C1;">class</span>=<span class="pl-s" style="box-sizing:border-box;color:#032F62;"><span class="pl-pds" style="box-sizing:border-box;">"</span>ch.qos.logback.classic.AsyncAppender<span class="pl-pds" style="box-sizing:border-box;">"</span></span>&gt;
        &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">appender-ref</span> <span class="pl-e" style="box-sizing:border-box;color:#6F42C1;">ref</span>=<span class="pl-s" style="box-sizing:border-box;color:#032F62;"><span class="pl-pds" style="box-sizing:border-box;">"</span>GELF<span class="pl-pds" style="box-sizing:border-box;">"</span></span> /&gt;
    &lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">appender</span>&gt;

    &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">root</span> <span class="pl-e" style="box-sizing:border-box;color:#6F42C1;">level</span>=<span class="pl-s" style="box-sizing:border-box;color:#032F62;"><span class="pl-pds" style="box-sizing:border-box;">"</span>debug<span class="pl-pds" style="box-sizing:border-box;">"</span></span>&gt;
        &lt;<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">appender-ref</span> <span class="pl-e" style="box-sizing:border-box;color:#6F42C1;">ref</span>=<span class="pl-s" style="box-sizing:border-box;color:#032F62;"><span class="pl-pds" style="box-sizing:border-box;">"</span>ASYNC GELF<span class="pl-pds" style="box-sizing:border-box;">"</span></span> /&gt;
    &lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">root</span>&gt;

&lt;/<span class="pl-ent" style="box-sizing:border-box;color:#22863A;">configuration</span>&gt;</pre>
	</div>
	<h2 style="box-sizing:border-box;margin-top:24px;margin-bottom:16px;line-height:1.25;padding-bottom:0.3em;border-bottom:1px solid #EAECEF;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;white-space:normal;">
		<a href="https://github.com/osiegmar/logback-gelf#configuration" aria-hidden="true" class="anchor" id="user-content-configuration" style="box-sizing:border-box;color:#0366D6;text-decoration-line:none;float:left;padding-right:4px;margin-left:-20px;line-height:1;"><svg aria-hidden="true" class="octicon octicon-link" height="16" version="1.1" viewbox="0 0 16 16" width="16"><path fill-rule="evenodd" d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"></path></svg></a>Configuration
	</h2>
	<h2 style="box-sizing:border-box;margin-top:24px;margin-bottom:16px;line-height:1.25;padding-bottom:0.3em;border-bottom:1px solid #EAECEF;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;white-space:normal;">
		<a href="https://github.com/osiegmar/logback-gelf#appender" aria-hidden="true" class="anchor" id="user-content-appender" style="box-sizing:border-box;color:#0366D6;text-decoration-line:none;float:left;padding-right:4px;margin-left:-20px;line-height:1;"><svg aria-hidden="true" class="octicon octicon-link" height="16" version="1.1" viewbox="0 0 16 16" width="16"><path fill-rule="evenodd" d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"></path></svg></a>Appender
	</h2>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:16px;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;font-size:16px;white-space:normal;">
		<code style="box-sizing:border-box;font-family:SFMono-Regular, Consolas, &quot;font-size:13.6px;padding:0.2em 0px;margin:0px;background-color:rgba(27, 31, 35, 0.05);border-radius:3px;">de.siegmar.logbackgelf.GelfUdpAppender</code>
	</p>
	<ul style="box-sizing:border-box;padding-left:2em;margin-top:0px;margin-bottom:16px;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;font-size:16px;white-space:normal;">
		<li style="box-sizing:border-box;">
			<span style="box-sizing:border-box;font-weight:600;">graylogHost</span>: IP or hostname of graylog server.
		</li>
		<li style="box-sizing:border-box;margin-top:0.25em;">
			<span style="box-sizing:border-box;font-weight:600;">graylogPort</span>: Port of graylog server. Default: 12201.
		</li>
		<li style="box-sizing:border-box;margin-top:0.25em;">
			<span style="box-sizing:border-box;font-weight:600;">layout</span>: See Layout configuration below.
		</li>
		<li style="box-sizing:border-box;margin-top:0.25em;">
			<span style="box-sizing:border-box;font-weight:600;">maxChunkSize</span>: Maximum size of GELF chunks in bytes. Default chunk size is 508 - this prevents IP packet fragmentation. This is also the recommended minimum. Maximum supported chunk size is 65,467 bytes.
		</li>
		<li style="box-sizing:border-box;margin-top:0.25em;">
			<span style="box-sizing:border-box;font-weight:600;">useCompression</span>: If true, compression of GELF messages is enabled. Default: true.
		</li>
	</ul>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:16px;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;font-size:16px;white-space:normal;">
		<code style="box-sizing:border-box;font-family:SFMono-Regular, Consolas, &quot;font-size:13.6px;padding:0.2em 0px;margin:0px;background-color:rgba(27, 31, 35, 0.05);border-radius:3px;">de.siegmar.logbackgelf.GelfTcpAppender</code>
	</p>
	<ul style="box-sizing:border-box;padding-left:2em;margin-top:0px;margin-bottom:16px;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;font-size:16px;white-space:normal;">
		<li style="box-sizing:border-box;">
			<span style="box-sizing:border-box;font-weight:600;">graylogHost</span>: IP or hostname of graylog server.
		</li>
		<li style="box-sizing:border-box;margin-top:0.25em;">
			<span style="box-sizing:border-box;font-weight:600;">graylogPort</span>: Port of graylog server. Default: 12201.
		</li>
		<li style="box-sizing:border-box;margin-top:0.25em;">
			<span style="box-sizing:border-box;font-weight:600;">layout</span>: See Layout configuration below.
		</li>
		<li style="box-sizing:border-box;margin-top:0.25em;">
			<span style="box-sizing:border-box;font-weight:600;">connectTimeout</span>: Maximum time (in milliseconds) to wait for establishing a connection. A value of 0 disables the connect timeout. Default: 15,000 milliseconds.
		</li>
		<li style="box-sizing:border-box;margin-top:0.25em;">
			<span style="box-sizing:border-box;font-weight:600;">reconnectInterval</span>: Time interval (in seconds) after an existing connection is closed and re-opened. A value of 0 disables automatic reconnects. Default: 300 seconds.
		</li>
		<li style="box-sizing:border-box;margin-top:0.25em;">
			<span style="box-sizing:border-box;font-weight:600;">maxRetries</span>: Number of retries. A value of 0 disables retry attempts. Default: 2.
		</li>
		<li style="box-sizing:border-box;margin-top:0.25em;">
			<span style="box-sizing:border-box;font-weight:600;">retryDelay</span>: Time (in milliseconds) between retry attempts. Ignored if maxRetries is 0. Default: 3,000 milliseconds.
		</li>
	</ul>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:16px;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;font-size:16px;white-space:normal;">
		<code style="box-sizing:border-box;font-family:SFMono-Regular, Consolas, &quot;font-size:13.6px;padding:0.2em 0px;margin:0px;background-color:rgba(27, 31, 35, 0.05);border-radius:3px;">de.siegmar.logbackgelf.GelfTcpTlsAppender</code>
	</p>
	<ul style="box-sizing:border-box;padding-left:2em;margin-top:0px;margin-bottom:16px;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;font-size:16px;white-space:normal;">
		<li style="box-sizing:border-box;">
			Everything from GelfTcpAppender
		</li>
		<li style="box-sizing:border-box;margin-top:0.25em;">
			<span style="box-sizing:border-box;font-weight:600;">trustAllCertificates</span>: If true, trust all TLS certificates (even self signed certificates). You should not use this in production! Default: false.
		</li>
	</ul>
	<h2 style="box-sizing:border-box;margin-top:24px;margin-bottom:16px;line-height:1.25;padding-bottom:0.3em;border-bottom:1px solid #EAECEF;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;white-space:normal;">
		<a href="https://github.com/osiegmar/logback-gelf#layout" aria-hidden="true" class="anchor" id="user-content-layout" style="box-sizing:border-box;color:#0366D6;text-decoration-line:none;float:left;padding-right:4px;margin-left:-20px;line-height:1;"><svg aria-hidden="true" class="octicon octicon-link" height="16" version="1.1" viewbox="0 0 16 16" width="16"><path fill-rule="evenodd" d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"></path></svg></a>Layout
	</h2>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:16px;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;font-size:16px;white-space:normal;">
		<code style="box-sizing:border-box;font-family:SFMono-Regular, Consolas, &quot;font-size:13.6px;padding:0.2em 0px;margin:0px;background-color:rgba(27, 31, 35, 0.05);border-radius:3px;">de.siegmar.logbackgelf.GelfLayout</code>
	</p>
	<ul style="box-sizing:border-box;padding-left:2em;margin-top:0px;margin-bottom:16px;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;font-size:16px;white-space:normal;">
		<li style="box-sizing:border-box;">
			<span style="box-sizing:border-box;font-weight:600;">originHost</span>: Origin hostname - will be auto detected if not specified.
		</li>
		<li style="box-sizing:border-box;margin-top:0.25em;">
			<span style="box-sizing:border-box;font-weight:600;">includeRawMessage</span>: If true, the raw message (with argument placeholders) will be sent, too. Default: false.
		</li>
		<li style="box-sizing:border-box;margin-top:0.25em;">
			<span style="box-sizing:border-box;font-weight:600;">includeMarker</span>: If true, logback markers will be sent, too. Default: true.
		</li>
		<li style="box-sizing:border-box;margin-top:0.25em;">
			<span style="box-sizing:border-box;font-weight:600;">includeMdcData</span>: If true, MDC keys/values will be sent, too. Default: true.
		</li>
		<li style="box-sizing:border-box;margin-top:0.25em;">
			<span style="box-sizing:border-box;font-weight:600;">includeCallerData</span>: If true, caller data (source file-, method-, class name and line) will be sent, too. Default: false.
		</li>
		<li style="box-sizing:border-box;margin-top:0.25em;">
			<span style="box-sizing:border-box;font-weight:600;">includeRootCauseData</span>: If true, root cause exception of the exception passed with the log message will be exposed in the root_cause_class_name and root_cause_message fields. Default: false.
		</li>
		<li style="box-sizing:border-box;margin-top:0.25em;">
			<span style="box-sizing:border-box;font-weight:600;">includeLevelName</span>: If true, the log level name (e.g. DEBUG) will be sent, too. Default: false.
		</li>
		<li style="box-sizing:border-box;margin-top:0.25em;">
			<span style="box-sizing:border-box;font-weight:600;">appendNewline</span>: If true, a system depended newline separator will be added at the end of each message. Don't use this in conjunction with TCP or UDP appenders, as this is only reasonable for console logging!
		</li>
		<li style="box-sizing:border-box;margin-top:0.25em;">
			<span style="box-sizing:border-box;font-weight:600;">shortPatternLayout</span>: Short message format. Default:&nbsp;<code style="box-sizing:border-box;font-family:SFMono-Regular, Consolas, &quot;font-size:13.6px;padding:0.2em 0px;margin:0px;background-color:rgba(27, 31, 35, 0.05);border-radius:3px;">"%m%nopex"</code>.
		</li>
		<li style="box-sizing:border-box;margin-top:0.25em;">
			<span style="box-sizing:border-box;font-weight:600;">fullPatternLayout</span>: Full message format (Stacktrace). Default:&nbsp;<code style="box-sizing:border-box;font-family:SFMono-Regular, Consolas, &quot;font-size:13.6px;padding:0.2em 0px;margin:0px;background-color:rgba(27, 31, 35, 0.05);border-radius:3px;">"%m"</code>.
		</li>
		<li style="box-sizing:border-box;margin-top:0.25em;">
			<span style="box-sizing:border-box;font-weight:600;">staticFields</span>: Additional, static fields to send to graylog. Defaults: none.
		</li>
	</ul>
	<h2 style="box-sizing:border-box;margin-top:24px;margin-bottom:16px;line-height:1.25;padding-bottom:0.3em;border-bottom:1px solid #EAECEF;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;white-space:normal;">
		<a href="https://github.com/osiegmar/logback-gelf#contribution" aria-hidden="true" class="anchor" id="user-content-contribution" style="box-sizing:border-box;color:#0366D6;text-decoration-line:none;float:left;padding-right:4px;margin-left:-20px;line-height:1;"><svg aria-hidden="true" class="octicon octicon-link" height="16" version="1.1" viewbox="0 0 16 16" width="16"><path fill-rule="evenodd" d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"></path></svg></a>Contribution
	</h2>
	<ul style="box-sizing:border-box;padding-left:2em;margin-top:0px;margin-bottom:16px;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;font-size:16px;white-space:normal;">
		<li style="box-sizing:border-box;">
			Fork
		</li>
		<li style="box-sizing:border-box;margin-top:0.25em;">
			Code
		</li>
		<li style="box-sizing:border-box;margin-top:0.25em;">
			Add test(s)
		</li>
		<li style="box-sizing:border-box;margin-top:0.25em;">
			Commit
		</li>
		<li style="box-sizing:border-box;margin-top:0.25em;">
			Send me a pull request
		</li>
	</ul>
	<h2 style="box-sizing:border-box;margin-top:24px;margin-bottom:16px;line-height:1.25;padding-bottom:0.3em;border-bottom:1px solid #EAECEF;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;white-space:normal;">
		<a href="https://github.com/osiegmar/logback-gelf#copyright" aria-hidden="true" class="anchor" id="user-content-copyright" style="box-sizing:border-box;color:#0366D6;text-decoration-line:none;float:left;padding-right:4px;margin-left:-20px;line-height:1;"><svg aria-hidden="true" class="octicon octicon-link" height="16" version="1.1" viewbox="0 0 16 16" width="16"><path fill-rule="evenodd" d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"></path></svg></a>Copyright
	</h2>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:16px;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;font-size:16px;white-space:normal;">
		Copyright (C) 2016 Oliver Siegmar
	</p>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:16px;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;font-size:16px;white-space:normal;">
		This library is free software; you can redistribute it and/or modify it under the terms of the GNU Lesser General Public License as published by the Free Software Foundation; either version 2.1 of the License, or (at your option) any later version.
	</p>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:16px;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;font-size:16px;white-space:normal;">
		This library is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU Lesser General Public License for more details.
	</p>
	<p style="box-sizing:border-box;margin-top:0px;color:#24292E;font-family:-apple-system, BlinkMacSystemFont, &quot;font-size:16px;white-space:normal;margin-bottom:0px !important;">
		You should have received a copy of the GNU Lesser General Public License along with this library; if not, write to the Free Software Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301 USA
	</p>
</p>