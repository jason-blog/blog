<p style="text-indent:2em;">
<pre class="prettyprint lang-js linenums">github://git@github.com:myOrganizationProjectJson

1、创建wsdl 
说明： 
A、非标准的webservice，可能只能PHP才能访问 
B、标准的webservice，就必须要使用wsdl(webservice description language，就是用XML语法标准来描述你的服务内容，我是这么理解的) 
在这里我只介绍标准的webservice。 
那么如何创建wsdl呢？对于PHP来说这确实是件很不容易的事情，有人说用zend studio创建很方便，这是一种方法。但对于那些不喜欢用zend studio的人来说，会觉得创建一个webservice还要安装zend studio，太强人所难了，我就是，嘿嘿。 
在这里我介绍一个简单的方法，到网上下载SoapDiscovery.class.php类，里面有个公用方法：getWSDL，这个方法末尾是用的return，那么，你修改一下这个方法，我是这么做的： 
//return sprintf('%s%s%s%s%s%s', $headerWSDL, $portTypeWSDL, $bindingWSDL, $serviceWSDL, $messageWSDL, '&lt;/definitions&gt;'); 
//生成wsdl文件，将上面的return注释 
$fso = fopen($this-&gt;class_name . ".wsdl" , "w"); 
fwrite($fso, sprintf('%s%s%s%s%s%s', $headerWSDL, $portTypeWSDL, $bindingWSDL, $serviceWSDL, $messageWSDL, '&lt;/definitions&gt;')); 
现在生成wsdl的类有了，SoapDiscovery.class.php★。 

我只要再准备一个提供服务的类或者函数就可以创建wsdl了 
比如我有个类：person，文件名为：person.class.php★，里面有两个方法，一个是say，一个是run。很简单。 
复制代码代码如下:

&lt;?php 
class person 
{ 
public function say() 
{ 
return("i'm speaking."); 
} 
public function run() 
{ 
return("i'm running,don't disturb me please."); 
} 
} 
?&gt; 

到这里有两个类了：SoapDiscovery.class.php和person.class.php。 
开始正式生成wsdl： 
创建文件server.php。将以下内容拷贝进去，运行即可生成一个person.wsdl文件 
复制代码代码如下:

&lt;?php 
include("person.class.php"); 
include("SoapDiscovery.class.php"); 
$disco = new SoapDiscovery('person','Person');//第一个参数是类名（生成的wsdl文件就是以它来命名的），即person类，第二个参数是服务的名字（这个可以随便写）。 
$disco-&gt;getWSDL(); 
?&gt; 

2、创建webservice服务端程序 
将server.php文件的内容清空，复制以下代码进去： 
复制代码代码如下:

&lt;?php 
include("person.class.php"); 
$objSoapServer = new SoapServer("person.wsdl");//person.wsdl是刚创建的wsdl文件 
//$objSoapServer = new SoapServer("server.php?wsdl");//这样也行 
$objSoapServer-&gt;setClass("person");//注册person类的所有方法 
$objSoapServer-&gt;handle();//处理请求 
?&gt; 

3、创建webservice客户端程序，测试webservice是否有效，文件名是：client.php 
将以下内容拷贝进去 
复制代码代码如下:

&lt;?php 
$client = new SoapClient("person.wsdl"); 
//$client = new SoapClient("server.php?wsdl");//这样也行 
echo($client-&gt;say()); 
echo "&lt;br /&gt;"; 
echo($client-&gt;run()); 
echo "&lt;br /&gt;"; 
?&gt; 

OK，结束。很简单吧？ 
.NET如果要使用的话，你只要提供一个url给他就行了。 
获得url的方法：你可以先到person.wsdl文件里面查找&lt;soap:address location="http://xxxxxxxxxxxxxxxxxxxx/server.php" /&gt;，这里的url（具体url是根据你的目录确定的）就是你要提供给.NET开发人员使用的。不过别高兴太早，后面要加：“?wsdl”，http://xxxxxxxxxxxxxxxxxxxx/server.php?wsdl这样才是对的，不信你可以将url拷贝到浏览器的地址栏里看下就知道了。 
.NET开发人员获得你给他的url之后，就可以在自己的项目里面添加一个服务引用或者web引用了，然后就可以根据提示完成相关操作，对于使用.NET的开发人员来说很简单的。 

在这里我只介绍标准的webservice 
一、　创建WSDL 
1。网上下载SoapDiscovery.class.php类 
2。修改SoapDiscovery.class.php的公共方法getWsdl()，让其自动生成wsdl文件（注意存放路径），这里只是创建一个wsdl模型 
复制代码代码如下:

//return sprintf('%s%s%s%s%s%s', $headerWSDL, $portTypeWSDL, $bindingWSDL, $serviceWSDL, $messageWSDL, '&lt;/definitions&gt;'); 
//生成wsdl文件，将上面的return注释 
$fso = fopen($this-&gt;class_name . ".wsdl" , "w"); 
fwrite($fso, sprintf('%s%s%s%s%s%s', $headerWSDL, $portTypeWSDL, $bindingWSDL, $serviceWSDL, $messageWSDL, '&lt;/definitions&gt;')); 
exit; 

3。提供服务的类或者函数 
复制代码代码如下:

//比如我有个类：person，文件名为：person.class.php★，里面有两个方法，一个是say，一个是run。很简单。 
&lt;?php 
class person 
{ 
public function say() 
{ 
return("i'm speaking."); 
} 
public function run() 
{ 
return("i'm running,don't disturb me please."); 
} 
} 
?&gt; 

4。开始正式生成wsdl： 
创建文件server.php。将以下内容拷贝进去，运行即可生成一个person.wsdl文件 
复制代码代码如下:

&lt;?php 
include("person.class.php"); 
include("SoapDiscovery.class.php"); 
//第一个参数是类名（生成的wsdl文件就是以它来命名的），即person类，第二个参数是服务的名字（这个可以随便写）。 
$disco = new SoapDiscovery('person','Person'); 
$disco-&gt;getWSDL(); 
?&gt; 

5。创建webservice服务端程序 
将server.php文件的内容清空，复制以下代码进去： 
复制代码代码如下:

&lt;?php 
include("person.class.php"); 
$objSoapServer = new SoapServer("person.wsdl");//person.wsdl是刚创建的wsdl文件 
//$objSoapServer = new SoapServer("server.php?wsdl");//这样也行 
$objSoapServer-&gt;setClass("person");//注册person类的所有方法 
$objSoapServer-&gt;handle();//处理请求 
?&gt; 

6。创建webservice客户端程序，测试webservice是否有效，文件名是：client.php 
复制代码代码如下:

&lt;?php 
$client = new SoapClient("person.wsdl"); 
//$client = new SoapClient("server.php?wsdl");//这样也行 
echo($client-&gt;say()); 
echo "&lt;br /&gt;"; 
echo($client-&gt;run()); 
echo "&lt;br /&gt;"; 
?&gt; 

7。.NET如果要使用的话，你只要提供一个url给他就行了。 
获得url的方法：你可以先到person.wsdl文件里面查找&lt;soap:address location="http://xxxxxxxxxxxxxxxxxxxx/server.php" /&gt;，这里的url（具体url是根据你的目录确定的）就是你要提供给.NET开发人员使用的。不过别高兴太早，后面要加：“?wsdl”，http://xxxxxxxxxxxxxxxxxxxx/server.php?wsdl这样才是对的，不信你可以将url拷贝到浏览器的地址栏里看下就知道了。 
.NET开发人员获得你给他的url之后，就可以在自己的项目里面添加一个服务引用或者web引用了，然后就可以根据提示完成相关操作，对于使用.NET的开发人员来说很简单的。 

（1）创建一网站，创建一个web引用，输入url 

（2）实力调用 
复制代码代码如下:

protected void Page_Load(object sender, EventArgs e) 
{ 
if (!IsPostBack) { 
sdaf.Solsoft_HelloWorld ddd = new sdaf.Solsoft_HelloWorld(); 
Label1.Text = ddd.say(); 
} 
} 
</pre>
</p>