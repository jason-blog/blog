<div id="cnblogs_post_body">
	<p>
		1、将war文件拷贝到tomcat目录webapps下（不要再建目录）。 <br />
<br />
2、将必要的jar文件拷贝到tomcat目录libxia下。 <br />
<br />
3、修改tomcat目录conf下的server.xml。
在&lt;Host&gt;&lt;/Host&gt;中加入：<br />
&nbsp;&nbsp;&nbsp;&nbsp; <br />
&nbsp;&nbsp;&nbsp;&nbsp; &lt;!-- Tomcat Manager Context --&gt; <br />
&nbsp;&nbsp;&nbsp;&nbsp; &lt;Context path="/manager" docBase="manager" debug="0"privileged="true"/&gt; <br />
path="" 为部署后运行的url路径，docBase为你的war的文件名。
第一次运行的时候，tomcat会自动解压war，生成path指定名称的网站。
	</p>
	<p>
		这里docBase中的"manager"就表示war文件名称为“manager.war"
	</p>
	<p>
		<br />
4、完毕，启动tomcat。。。。成功发布。。。^_^。。
	</p>
</div>