&lt;plugin&gt; &nbsp;<br />
&nbsp; &nbsp; &lt;groupId&gt;org.apache.maven.plugins&lt;/groupId&gt; &nbsp;<br />
&nbsp; &nbsp; &lt;artifactId&gt;maven-jar-plugin&lt;/artifactId&gt; &nbsp;<br />
&nbsp; &nbsp; &lt;version&gt;2.4&lt;/version&gt; &nbsp;<br />
&nbsp; &nbsp; &lt;configuration&gt; &nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &lt;archive&gt; &nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &lt;manifest&gt; &nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &lt;addClasspath&gt;true&lt;/addClasspath&gt; &nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &lt;classpathPrefix&gt;lib/&lt;/classpathPrefix&gt; &nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &lt;mainClass&gt;com.sysware.HelloWorld&lt;/mainClass&gt; &nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &lt;/manifest&gt; &nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &lt;/archive&gt; &nbsp;<br />
&nbsp; &nbsp; &lt;/configuration&gt; &nbsp;<br />
<p>
	&lt;/plugin&gt;&nbsp;
</p>
<p>
	<br />
</p>
<p>
	<span style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">运行mvn clean package即可</span> 
</p>
<p>
	<span style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;"><br />
</span>
</p>
<p>
	<span style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;"><br />
</span>
</p>
<p>
	<span style="color:#333333;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">&lt;build&gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &lt;resources&gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &lt;resource&gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &lt;directory&gt;src/main/resources&lt;/directory&gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &lt;filtering&gt;true&lt;/filtering&gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &lt;/resource&gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &lt;/resources&gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &lt;plugins&gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &lt;plugin&gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &lt;groupId&gt;org.springframework.boot&lt;/groupId&gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &lt;artifactId&gt;spring-boot-maven-plugin&lt;/artifactId&gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &lt;configuration&gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &lt;finalName&gt;${project.artifactId}&lt;/finalName&gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &lt;/configuration&gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &lt;/plugin&gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &lt;plugin&gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &lt;groupId&gt;org.apache.maven.plugins&lt;/groupId&gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &lt;artifactId&gt;maven-resources-plugin&lt;/artifactId&gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &lt;version&gt;${plugin.maven-resources-plugin.version}&lt;/version&gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &lt;configuration&gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &lt;delimiters&gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &lt;delimiter&gt;@&lt;/delimiter&gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &lt;/delimiters&gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &lt;useDefaultDelimiters&gt;false&lt;/useDefaultDelimiters&gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &lt;/configuration&gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &lt;/plugin&gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &lt;/plugins&gt;<br />
&nbsp; &nbsp; &lt;/build&gt;<br />
<br />
</span>
</p>