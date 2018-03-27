<pre class="prettyprint lang-js linenums">
<pre class="prettyprint lang-js linenums">cd target/classes</pre>
<pre class="prettyprint lang-js linenums">java -classpath ",;/var/*" testApp.app</pre>
<br />
</pre>
<pre class="prettyprint lang-js linenums">以往基于构建工具和IDE工作,很少使用命令行执行程序,但偶尔使用命令行的时候关于类路径的设置都要查阅一下说明文档,这里找到一个详尽清晰的说明,以备自查.特别指明的是:classpath最好使用""(window系统下)或''(linux系统下)括起来,否则可能会因为包含的jar路径上含有空格一类的特殊字符导致出现奇怪的错误提示.,本文转自wikipedia,地址: http://en.wikipedia.org/wiki/Classpath_%28Java%29
Setting the path to execute Java programs
Basic usage
Suppose we have a package called org.mypackage containing the classes:
HelloWorld (main class)
SupportClass
UtilClass
and the files defining this package are stored physically under the directory D:\myprogram (on Windows) or /home/user/myprogram (on Linux).
The file structure will look like this:
Microsoft Windows	Linux
D:\myprogram\
      |
      ---&gt; org\  
            |
            ---&gt; mypackage\
                     |
                     ---&gt; HelloWorld.class       
                     ---&gt; SupportClass.class   
                     ---&gt; UtilClass.class     
/home/user/myprogram/
            |
            ---&gt; org/  
                  |
                  ---&gt; mypackage/
                           |
                           ---&gt; HelloWorld.class       
                           ---&gt; SupportClass.class   
                           ---&gt; UtilClass.class     
When we invoke Java, we specify the name of the application to run: org.mypackage.HelloWorld. However we must also tell Java where to look for the files and directories defining our package. So to launch the program, we use the following command:
Microsoft Windows	Linux
 java -classpath D:\myprogram org.mypackage.HelloWorld
 java -classpath /home/user/myprogram org.mypackage.HelloWorld 
where:
-classpath D:\myprogram sets the path to the packages used in the program (on Linux, -classpath /home/user/myprogram)
org.mypackage.HelloWorld is the name of the main class
Note that if we ran Java in D:\myprogram\ (on Linux, /home/user/myprogram/) then we would not need to specify the classpath since Java implicitly looks in the current working directory for files containing classes.
Adding all JAR files in a directory
In Java 6 and higher, one can add all jar-files in a specific directory to the classpath using wildcard notation.
Windows example:
java -classpath ".;c:\mylib\*" MyApp
Linux example:
java -classpath '.:/mylib/*' MyApp
Setting the path through an environment variable
The environment variable named CLASSPATH may be alternatively used to set the classpath. For the above example, we could also use on Windows:
Sometimes you have to check the JAVA_HOME also, if it is pointing towards the right JDK version
set CLASSPATH=D:\myprogram
java org.mypackage.HelloWorld
Setting the path of a Jar file
Now, suppose the program uses a supporting library enclosed in a Jar file called supportLib.jar, physically in the directory D:\myprogram\lib\.
The corresponding physical file structure is :
D:\myprogram\
      |
      ---&gt; lib\
            |
            ---&gt; supportLib.jar
      |
      ---&gt; org\
            |
            --&gt; mypackage\
                       |
                       ---&gt; HelloWorld.class
                       ---&gt; SupportClass.class
                       ---&gt; UtilClass.class
We should use the following command-line option:
java -classpath D:\myprogram;D:\myprogram\lib\supportLib.jar org.mypackage.HelloWorld
or alternatively:
set CLASSPATH=D:\myprogram;D:\myprogram\lib\supportLib.jar
java org.mypackage.HelloWorld
Setting the path in a Manifest file
Suppose that our program has been enclosed in a Jar file called helloWorld.jar, put directly in the D:\myprogram directory. We have the following file structure:
D:\myprogram\
      |
      ---&gt; helloWorld.jar 
      |
      ---&gt; lib\  
            |
            ---&gt; supportLib.jar
The manifest file defined in this Jar file has this definition:
Main-Class: org.mypackage.HelloWorld
Class-Path: lib/supportLib.jar

Note: It's important that the manifest file ends with either a new line or carriage return.
Also, note that the classpath string in this case describes the location of the supportLib.jar file relative to the location of the helloWorld.jar file, and not as an absolute file path (as it might be when setting the -classpath parameter on the command line, for example). Thus, the actual locations of the jar file and its support library are irrelevant so long as the relative directory structure between the two is preserved.
To launch the program, we can use the following command:
java -jar D:\myprogram\helloWorld.jar
It is not necessary to define the Classpath to the program classes, or the support library classes, because it is already defined in the manifest file.
Caution, it is useless to define the Main class at launch, the manifest of the JAR file must contain a line of the form
Main-Class: classname
in order for the -jar option to work JavaDoc.
The syntax for specifying multiple library JAR files in the manifest file is to separate the entries with a space:
Class-Path: lib/supportLib.jar lib/supportLib2.jar
OS specific notes
Being closely associated with the file system, the command-line Classpath syntax depends on the operating system. For example:
on all Unix-like operating systems (such as Linux and Mac OS X), the directory structure has a Unix syntax, with separate file paths separated by a colon (":").
on Windows, the directory structure has a Windows syntax, and each file path must be separated by a semicolon (";").
This does not apply when the Classpath is defined in manifest files, where each file path must be separated by a space (" "), regardless of the operating system.
Diagnose
Application programmers may want to find out/debug the current settings under which the application is running:
System.getProperty("java.class.path")</pre>