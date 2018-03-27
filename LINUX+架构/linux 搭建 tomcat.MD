<p>
	1.下载apache及jdk安装文件<br />
jdk-6u10-linux-i586-rpm.bin<br />
apache-tomcat-5.5.12.tar.gz
</p>
<p>
	JDK和TOMCAT都是免费的，可以在其主页上下载需要的版本以及API文档。<br />
JDK&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 下载地址：http://java.sun.com/<br />
&nbsp;TOMCAT下载地址：http://tomcat.apache.org/&nbsp;&nbsp;&nbsp;
</p>
<p>
	2.安装JDK及apache<br />
jdk-6u10-linux-i586-rpm.bin 放在 /usr目录下
</p>
<p>
	chmod 777 jdk-6u10-linux-i586-rpm.bin 将其转换为可执行文件
</p>
<p>
	sh jdk-6u10-linux-i586-rpm.bin 执行此文件，先会出来一段协议，按空格看完
</p>
<p>
	后选择yes会自动释放出JDK的RPM包，并进行安装
</p>
<p>
	安装完成后/usr/java/jdk1.6.0_10这个即为JDK的安装目录
</p>
<p>
	测试java安装成功 java -version
</p>
<p>
	apache-tomcat-5.5.12.tar.gz 放在/usr/local下面
</p>
<p>
	tar -zxvf apache-tomcat-5.5.12.tar.gz 解包apache
</p>
<p>
	/usr/local下面将解出的目录重命名<br />
mv apache-tomcat-5.5.12 tomcat5.5
</p>
<p>
	3.配置 /etc/profile (环境变量)
</p>
<p>
	vi /etc/profile<br />
文件最后面把下面一段加上去
</p>
<p>
	JDK_HOME=/usr/java/jdk1.6.0_10<br />
JAVA_HOME=/usr/java/jdk1.6.0_10<br />
CATALINA_HOME=/usr/local/tomcat5.5<br />
JRE_HOME=/usr/java/jdk1.6.0_10
</p>
<p>
	<br />
source /etc/profile&nbsp; 载入配置
</p>
<p>
	4.启动tomcat
</p>
<p>
	sh /usr/local/tomcat5.5/bin/startup.sh
</p>
<p>
	Using CATALINA_BASE:&nbsp;&nbsp; /usr/local/tomcat5.5<br />
Using CATALINA_HOME:&nbsp;&nbsp; /usr/local/tomcat5.5<br />
Using CATALINA_TMPDIR: /usr/local/tomcat5.5/temp<br />
Using JRE_HOME:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; /usr/java/jdk1.6.0_10
</p>
<p>
	ps -elf | grep tomcat 有类似下面的提示出现证明tomcat 启动成功<br />
0 S root&nbsp;&nbsp;&nbsp;&nbsp; 25099&nbsp;&nbsp;&nbsp;&nbsp; 1&nbsp; 1&nbsp; 81&nbsp;&nbsp; 0 - 57074 322562 14:54 pts/0&nbsp;&nbsp;&nbsp;
</p>
<p>
	00:00:02 /usr/java/jdk1.6.0_10/bin/java -
</p>
<p>
	Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager -
</p>
<p>
	Djava.util.logging.config.file=/usr/local/tomcat5.5/conf/logging.propert
</p>
<p>
	ies -Djava.endorsed.dirs=/usr/local/tomcat5.5/common/endorsed -classpath
</p>
<p>
	:/usr/local/tomcat5.5/bin/bootstrap.jar:/usr/local/tomcat5.5/bin/commons
</p>
<p>
	-logging-api.jar -Dcatalina.base=/usr/local/tomcat5.5 -
</p>
<p>
	Dcatalina.home=/usr/local/tomcat5.5 -
</p>
<p>
	Djava.io.tmpdir=/usr/local/tomcat5.5/temp
</p>
<p>
	org.apache.catalina.startup.Bootstrap start<br />
0 S root&nbsp;&nbsp;&nbsp;&nbsp; 25149&nbsp; 2807&nbsp; 0&nbsp; 77&nbsp;&nbsp; 0 -&nbsp;&nbsp; 971 pipe_w 14:57 pts/0&nbsp;&nbsp;&nbsp;
</p>
<p>
	00:00:00 grep tomcat
</p>
<p>
	5.测试tomcat<br />
http://192.168.3.30:8080&nbsp; 192.168.3.30(tomcat服务器地址） 8080 默认端口号，也可以在配置文件中改掉<br />
会出现tomcat的示例页面<br />
安装完成
</p>