<h2>
	引言：
</h2>
<p>
	前段时间项目中用到了RESTful模式来开发程序，但是当用POST、PUT模式提交数据时，发现服务器端接受不到提交的数据（服务器端参数绑定
没有加任何注解），查看了提交方式为application/json， 而且服务器端通过request.getReader() 
打出的数据里确实存在浏览器提交的数据。为了找出原因，便对参数绑定（@RequestParam、 @RequestBody、 
@RequestHeader 、 
@PathVariable）进行了研究，同时也看了一下HttpMessageConverter的相关内容，在此一并总结。
</p>
<p>
	&nbsp;
</p>
<h2>
	<a name="t1"></a>简介：
</h2>
<p>
	@RequestMapping
</p>
<p>
	RequestMapping是一个用来处理请求地址映射的注解，可用于类或方法上。用于类上，表示类中的所有响应请求的方法都是以该地址作为父路径。
</p>
<p>
	RequestMapping注解有六个属性，下面我们把她分成三类进行说明。
</p>
<h3>
	<a name="t2"></a>1、 value， method；
</h3>
<p>
	value：&nbsp;&nbsp;&nbsp;&nbsp; 指定请求的实际地址，指定的地址可以是URI Template 模式（后面将会说明）；
</p>
<p>
	method：&nbsp; 指定请求的method类型， GET、POST、PUT、DELETE等；
</p>
<p>
	&nbsp;
</p>
<h3>
	<a name="t3"></a>2、 consumes，produces；
</h3>
<p>
	consumes： 指定处理请求的提交内容类型（Content-Type），例如application/json, text/html;
</p>
<p>
	produces:&nbsp;&nbsp;&nbsp; 指定返回的内容类型，仅当request请求头中的(Accept)类型中包含该指定类型才返回；
</p>
<p>
	&nbsp;
</p>
<h3>
	<a name="t4"></a>3、 params，headers；
</h3>
<p>
	params： 指定request中必须包含某些参数值是，才让该方法处理。
</p>
<p>
	headers： 指定request中必须包含某些指定的header值，才能让该方法处理请求。
</p>
<p>
	&nbsp;
</p>
<h2>
	<a name="t5"></a>示例：
</h2>
<h3>
	<a name="t6"></a>1、value&nbsp; / method 示例
</h3>
<p>
	默认RequestMapping("....str...")即为value的值；
</p>
<div class="cnblogs_code">
	<div class="cnblogs_code_toolbar">
		<span class="cnblogs_code_copy"><img src="http://common.cnblogs.com/images/copycode.gif" alt="复制代码" /></span>
	</div>
<pre>@Controller
@RequestMapping("/appointments") <span style="color:#0000ff;">public</span> <span style="color:#0000ff;">class</span> AppointmentsController { <span style="color:#0000ff;">private</span> AppointmentBook appointmentBook;
    
    @Autowired <span style="color:#0000ff;">public</span> AppointmentsController(AppointmentBook appointmentBook) { <span style="color:#0000ff;">this</span>.appointmentBook = appointmentBook;
    }

    @RequestMapping(method = RequestMethod.GET) <span style="color:#0000ff;">public</span> Map&lt;String, Appointment&gt; get() { <span style="color:#0000ff;">return</span> appointmentBook.getAppointmentsForToday();
    }

    @RequestMapping(value="/{day}", method = RequestMethod.GET) <span style="color:#0000ff;">public</span> Map&lt;String, Appointment&gt; getForDay(@PathVariable @DateTimeFormat(iso=ISO.DATE) Date day, Model model) { <span style="color:#0000ff;">return</span> appointmentBook.getAppointmentsForDay(day);
    }

    @RequestMapping(value="/new", method = RequestMethod.GET) <span style="color:#0000ff;">public</span> AppointmentForm getNewForm() { <span style="color:#0000ff;">return</span> <span style="color:#0000ff;">new</span> AppointmentForm();
    }

    @RequestMapping(method = RequestMethod.POST) <span style="color:#0000ff;">public</span> String add(@Valid AppointmentForm appointment, BindingResult result) { <span style="color:#0000ff;">if</span> (result.hasErrors()) { <span style="color:#0000ff;">return</span> "appointments/new";
        }
        appointmentBook.addAppointment(appointment); <span style="color:#0000ff;">return</span> "redirect:/appointments";
    }
}</pre>
	<div class="cnblogs_code_toolbar">
		<span class="cnblogs_code_copy"><img src="http://common.cnblogs.com/images/copycode.gif" alt="复制代码" /></span>
	</div>
</div>
<p>
	value的uri值为以下三类：
</p>
<p>
	A） 可以指定为普通的具体值；
</p>
<p>
	B)&nbsp; 可以指定为含有某变量的一类值(URI Template Patterns with Path Variables)；
</p>
<p>
	C) 可以指定为含正则表达式的一类值( URI Template Patterns with Regular Expressions);
</p>
<p>
	&nbsp;
</p>
<p>
	example B)
</p>
<div class="cnblogs_code">
<pre>@RequestMapping(value="/owners/{ownerId}", method=RequestMethod.GET) <span style="color:#0000ff;">public</span> String findOwner(@PathVariable String ownerId, Model model) {
  Owner owner = ownerService.findOwner(ownerId);  
  model.addAttribute("owner", owner); <span style="color:#0000ff;">return</span> "displayOwner"; 
}</pre>
</div>
<p>
	example C)
</p>
<div class="cnblogs_code">
<pre>@RequestMapping("/spring-web/{symbolicName:[a-z-]+}-{version:\d\.\d\.\d}.{extension:\.[a-z]}") <span style="color:#0000ff;">public</span> <span style="color:#0000ff;">void</span> handle(@PathVariable String version, @PathVariable String extension) { <span style="color:#008000;">//</span><span style="color:#008000;"> ...</span> }
}</pre>
</div>
<h3>
	2 consumes、produces 示例
</h3>
<p>
	cousumes的样例：
</p>
<div class="cnblogs_code">
<pre>@Controller
@RequestMapping(value = "/pets", method = RequestMethod.POST, consumes="application/json") <span style="color:#0000ff;">public</span> <span style="color:#0000ff;">void</span> addPet(@RequestBody Pet pet, Model model) { <span style="color:#008000;">//</span><span style="color:#008000;"> implementation omitted</span> }</pre>
</div>
<p>
	方法仅处理request Content-Type为“application/json”类型的请求。
</p>
<p>
	produces的样例：
</p>
<div class="cnblogs_code">
<pre>@Controller
@RequestMapping(value = "/pets/{petId}", method = RequestMethod.GET, produces="application/json")
@ResponseBody <span style="color:#0000ff;">public</span> Pet getPet(@PathVariable String petId, Model model) { <span style="color:#008000;">//</span><span style="color:#008000;"> implementation omitted</span> }</pre>
</div>
<p>
	方法仅处理request请求中Accept头中包含了"application/json"的请求，同时暗示了返回的内容类型为application/json;
</p>
<p>
	&nbsp;
</p>
<p>
	&nbsp;
</p>
<h3>
	<a name="t8"></a>3 params、headers 示例
</h3>
<p>
	params的样例：
</p>
<div class="cnblogs_code">
	<div class="cnblogs_code_toolbar">
		<span class="cnblogs_code_copy"><img src="http://common.cnblogs.com/images/copycode.gif" alt="复制代码" /></span>
	</div>
<pre>@Controller
@RequestMapping("/owners/{ownerId}") <span style="color:#0000ff;">public</span> <span style="color:#0000ff;">class</span> RelativePathUriTemplateController {

  @RequestMapping(value = "/pets/{petId}", method = RequestMethod.GET, params="myParam=myValue") <span style="color:#0000ff;">public</span> <span style="color:#0000ff;">void</span> findPet(@PathVariable String ownerId, @PathVariable String petId, Model model) { <span style="color:#008000;">//</span><span style="color:#008000;"> implementation omitted</span> }
}</pre>
	<div class="cnblogs_code_toolbar">
		<span class="cnblogs_code_copy"><img src="http://common.cnblogs.com/images/copycode.gif" alt="复制代码" /></span>
	</div>
</div>
<p>
	仅处理请求中包含了名为“myParam”，值为“myValue”的请求；
</p>
<p>
	&nbsp;
</p>
<p>
	&nbsp;
</p>
<p>
	headers的样例：
</p>
<div class="cnblogs_code">
	<div class="cnblogs_code_toolbar">
		<span class="cnblogs_code_copy"><img src="http://common.cnblogs.com/images/copycode.gif" alt="复制代码" /></span>
	</div>
<pre>@Controller
@RequestMapping("/owners/{ownerId}") <span style="color:#0000ff;">public</span> <span style="color:#0000ff;">class</span> RelativePathUriTemplateController {

@RequestMapping(value = "/pets", method = RequestMethod.GET, headers="Referer=http://www.ifeng.com/") <span style="color:#0000ff;">public</span> <span style="color:#0000ff;">void</span> findPet(@PathVariable String ownerId, @PathVariable String petId, Model model) { <span style="color:#008000;">//</span><span style="color:#008000;"> implementation omitted</span> }
}</pre>
	<div class="cnblogs_code_toolbar">
		<span class="cnblogs_code_copy"><img src="http://common.cnblogs.com/images/copycode.gif" alt="复制代码" /></span>
	</div>
</div>
<p>
	仅处理request的header中包含了指定“Refer”请求头和对应值为“<code class="focusRow subFocusRow ">http://www.ifeng.com/</code>”的请求；
</p>
<p>
	&nbsp;
</p>
<p>
	&nbsp;
</p>
<p>
	&nbsp;
</p>
<p>
	上面仅仅介绍了，RequestMapping指定的方法处理哪些请求，下面一篇将讲解怎样处理request提交的数据（数据绑定）和返回的数据。
</p>