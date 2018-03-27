<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	转自&nbsp;http://blog.csdn.net/ctf521love/article/details/44152765
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	最近有需求是将java项目部署到linux服务器上作为服务端程序，最后经过测试成功。本着分享精神将总结出来的路子分享给大家，如果不明白的地方可以在下边留言，谢谢。
</p>
<h1 align="center" style="margin:0px;padding:0px;font-family:Arial;white-space:normal;background-color:#FFFFFF;">
	将java项目部署到linux服务器
</h1>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	1、&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;首先从官网下载<a target="_blank" href="http://wrapper.tanukisoftware.com/doc/english/download.jsp" style="color:#CA0000;text-decoration-line:none;">http://wrapper.tanukisoftware.com/doc/english/download.jsp</a>，注意下载的文件为<strong>Community列中的（PS:其他版本需要序列号）</strong>
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	2、&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;将写好的java项目打成jar包，待用
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	3、&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;将下载好的文件解压到本地目录%wrapper_home%.
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	4、&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;连接到linux服务器，在linux服务器上创建文件夹为%linux_wrapper_home%。
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	5、&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;在%linux_wrapper_home%下依次创建空文件夹：bin、lib、conf、logs。
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	6、&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;将%wrapper_home%/bin下的wrapper文件上传到%linux_wrapper_home%/bin下。
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	7、&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;将%wrapper_home%/conf下的wrapper.conf文件上传到%linux_wrapper_home%/conf下。
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	8、&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;将%wrapper_home%/lib下的wrapper.jar、libwrapper.so文件上传到%linux_wrapper_home%/lib下，将事先打包好的项目jar包也放在这里。
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	9、&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;将将%wrapper_home%/src/bin/ sh.script.in文件上传到%linux_wrapper_home%/bin目录下并重命名为（建议：java项目中main方法的类名）。打开文件，修改两处地方：
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	APP_NAME="输入您的项目名称 "
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	APP_LONG_NAME="输入您的项目名称"。
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	10、 打开%linux_wrapper_home%/conf/wrapper.conf文件，需要修改以下地方：
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	wrapper.java.command=/usr/java/jdk1.7.0_45/bin/java
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	wrapper.java.mainclass=org.tanukisoftware.wrapper.WrapperStartStopApp
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	wrapper.java.classpath.1=../lib/serverdemo.jar（ps:此处就是项目打包之后的jar包）
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	wrapper.java.classpath.2=../lib/wrapper.jar
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	wrapper.java.classpath.3=/usr/java/jdk1.7.0_45/lib/dt.jar
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	wrapper.java.classpath.4=/usr/java/jdk1.7.0_45/lib/tools.jar
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	wrapper.app.parameter.1=HelloWorldServer（ps:此处就是项目main方法所在的类目）
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	wrapper.app.parameter.2=1
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	wrapper.app.parameter.3=true
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	wrapper.app.parameter.4=HelloWorldServer（ps:此处就是项目main方法所在的类目）
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	wrapper.app.parameter.5=true
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	wrapper.app.parameter.6=1
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	wrapper.app.parameter.7=stop&nbsp;
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	11、 以上任务完成之后即可在linux服务器上运行测试了。首先连接到linux服务器，找到
</p>
<p style="margin-top:0px;margin-bottom:0px;padding:0px;font-family:Arial;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	%linux_wrapper_home%/bin目录，先赋予文件可运行权限，赋予完毕之后输入./文件名 start 出现如下情况则表示运行成功。
</p>