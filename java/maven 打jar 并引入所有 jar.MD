<p>
	http://www.thinksaas.cn/topics/0/396/396692.html
</p>
<p>
	<br />
</p>
<p>
	<br />
</p>
<p>
<pre style="box-sizing:border-box;overflow:auto;font-family:Menlo, Monaco, Consolas, &quot;font-size:13px;padding:9.5px;margin-top:0px;margin-bottom:10px;line-height:normal;color:#333333;word-break:break-all;word-wrap:break-word;background-color:#F5F5F5;border:1px solid #CCCCCC;border-radius:4px;"><code class="xml" style="box-sizing:border-box;font-family:Menlo, Monaco, Consolas, &quot;font-size:inherit;padding:0px;color:inherit;background-color:transparent;border-radius:0px;font-style:inherit;font-weight:inherit;white-space:pre-wrap;">&lt;plugin&gt;
&lt;artifactId&gt;maven-assembly-plugin&lt;/artifactId&gt;
&lt;configuration&gt;
&lt;archive&gt;
&lt;manifest&gt;
&lt;mainClass&gt;com.taobao.search.abc.Xyz&lt;/mainClass&gt;
&lt;/manifest&gt;
&lt;/archive&gt;
&lt;descriptorRefs&gt;
&lt;descriptorRef&gt;jar-with-dependencies&lt;/descriptorRef&gt;
&lt;/descriptorRefs&gt;
&lt;/configuration&gt;
&lt;/plugin&gt;</code></pre>
	<p>
		<br />
	</p>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:10px;color:#434343;font-family:微软雅黑, Helvetica, Arial, Verdana, sans-serif, 宋体;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		其中 mainClass 里面就是你的程序入口 main 方法。
	</p>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:10px;color:#434343;font-family:微软雅黑, Helvetica, Arial, Verdana, sans-serif, 宋体;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		然后进到项目目录运行：
	</p>
<pre style="box-sizing:border-box;overflow:auto;font-family:Menlo, Monaco, Consolas, &quot;font-size:13px;padding:9.5px;margin-top:0px;margin-bottom:10px;line-height:normal;color:#333333;word-break:break-all;word-wrap:break-word;background-color:#F5F5F5;border:1px solid #CCCCCC;border-radius:4px;"><code class="shell" style="box-sizing:border-box;font-family:Menlo, Monaco, Consolas, &quot;font-size:inherit;padding:0px;color:inherit;background-color:transparent;border-radius:0px;font-style:inherit;font-weight:inherit;white-space:pre-wrap;">mvn clean compile assembly:single </code></pre>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:10px;color:#434343;font-family:微软雅黑, Helvetica, Arial, Verdana, sans-serif, 宋体;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		如果没有错误，编译完成之后就有一个名为 xxxx-jar-with-dependencies.jar 的文件静静的躺在 target 文件夹下面。
	</p>
<pre style="box-sizing:border-box;overflow:auto;font-family:Menlo, Monaco, Consolas, &quot;font-size:13px;padding:9.5px;margin-top:0px;margin-bottom:10px;line-height:normal;color:#333333;word-break:break-all;word-wrap:break-word;background-color:#F5F5F5;border:1px solid #CCCCCC;border-radius:4px;"><code style="box-sizing:border-box;font-family:Menlo, Monaco, Consolas, &quot;font-size:inherit;padding:0px;color:inherit;background-color:transparent;border-radius:0px;font-style:inherit;font-weight:inherit;white-space:pre-wrap;">java -jar xxxx-jar-with-dependencies.jar</code></pre>
</p>