<div style="font-family:宋体;font-size:14px;">
	&nbsp;Quartz框架是一个全功能、开源的任务调度服务，可以集成几乎任何的java应用程序—从小的单片机系统到大型的电子商务系统。Quartz可以执行上千上万的任务调度。
</div>
<div style="font-family:宋体;font-size:14px;">
	<br />
</div>
<div style="font-family:宋体;font-size:14px;">
	&nbsp;核心概念
</div>
<div style="font-family:宋体;font-size:14px;">
	<div>
		&nbsp;Quartz核心的概念<span style="color:#333333;"><span style="line-height:26px;"><span style="font-family:Arial;">：</span>scheduler任务调度、Job任务、Trigger触发器、JobDetail任务细节</span></span>
	</div>
	<div>
		<span style="color:#333333;"><span style="line-height:26px;">&nbsp;</span></span>
	</div>
	<div>
		<span style="color:#333333;"><span style="line-height:26px;">&nbsp;Job任务：其实Job是接口，其中只有一个execute方法：</span></span>
	</div>
	<div>
		<span style="color:#333333;"><span style="line-height:26px;">&nbsp;</span></span>package org.quartz;
	</div>
public abstract interface Job<br />
{<br />
&nbsp; public abstract void execute(JobExecutionContext paramJobExecutionContext)<br />
&nbsp;&nbsp;&nbsp; throws JobExecutionException;<br />
}
</div>
<div style="font-family:宋体;font-size:14px;">
	&nbsp;我们开发者只要实现此接口，实现execute方法即可。把我们想做的事情，在execute中执行即可。
</div>
<div style="font-family:宋体;font-size:14px;">
	&nbsp;JobDetail：任务细节，Quartz执行Job时，需要新建个Job实例，但是不能直接操作Job类，所以通过JobDetail来获取Job的名称、描述信息。
</div>
<div style="font-family:宋体;font-size:14px;">
	&nbsp;Trigger触发器：执行任务的规则；比如每天，每小时等。
</div>
<div style="font-family:宋体;font-size:14px;">
	&nbsp;一般情况使用SimpleTrigger，和CronTrigger，这个触发器实现了Trigger接口。
</div>
<div style="font-family:宋体;font-size:14px;">
	&nbsp;对于复杂的时间表达式来说，比如每个月15日上午几点几分，使用CronTrigger
</div>
<div style="font-family:宋体;font-size:14px;">
	&nbsp;对于简单的时间来说，比如每天执行几次，使用SimpleTrigger
</div>
<div style="font-family:宋体;font-size:14px;">
	&nbsp;scheduler任务调度：是最核心的概念，需要把JobDetail和Trigger注册到scheduler中，才可以执行。
</div>
<div style="font-family:宋体;font-size:14px;">
	<br />
</div>
<div style="font-family:宋体;font-size:14px;">
	&nbsp;具体执行步骤：
</div>
<div style="font-family:宋体;font-size:14px;">
	&nbsp;下载相应的jar包：<a href="http://www.quartz-scheduler.org/" style="color:#FF9900;text-decoration-line:none;">http://www.quartz-scheduler.org/</a>
</div>
<div style="font-family:宋体;font-size:14px;">
	&nbsp;注意：
</div>
<div style="font-family:宋体;font-size:14px;">
	&nbsp;不同的版本的jar包，具体的操作不太相同，但是思路是相同的；比如1.8.6jar包中，JobDetail是个类，直接通过构造方法与Job类关联。SimpleTrigger和CornTrigger是类；在2.0.2jar包中，JobDetail是个接口，SimpleTrigger和CornTrigger是接口
</div>
<div style="font-family:宋体;font-size:14px;">
	&nbsp;不同版本测试：
</div>
<div style="font-family:宋体;font-size:14px;">
	&nbsp;1.8.6jar包：&nbsp;&nbsp;
</div>
	</div>
	<div style="font-family:宋体;font-size:14px;">
		<div class="dp-highlighter bg_html" style="font-family:Consolas, &quot;font-size:12px;background-color:#E7E5DC;width:936.531px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;margin:18px 0px !important;">
			<div class="bar" style="padding-left:45px;">
				<div class="tools" style="padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #999999;">
					<b>[html]</b>&nbsp;<a href="http://blog.csdn.net/yuebinghaoyuan/article/details/9045471#" class="ViewSource" title="view plain" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">view plain</a><span data-mod="popu_168">&nbsp;<a href="http://blog.csdn.net/yuebinghaoyuan/article/details/9045471#" class="CopyToClipboard" title="copy" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">copy</a>
					<div style="position:absolute;left:764px;top:1405px;width:27px;height:15px;z-index:99;">
					</div>
</span><span data-mod="popu_169">&nbsp;<a href="http://blog.csdn.net/yuebinghaoyuan/article/details/9045471#" class="PrintSource" title="print" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">print</a></span><a href="http://blog.csdn.net/yuebinghaoyuan/article/details/9045471#" class="About" title="?" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">?</a>
				</div>
			</div>
			<ol start="1" class="dp-xml" style="padding:0px;border:none;list-style-position:initial;list-style-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span style="margin:0px;padding:0px;border:none;background-color:inherit;">package&nbsp;com.test;&nbsp;&nbsp;</span></span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">import&nbsp;java.util.Date;&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">import&nbsp;org.quartz.Job;&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">import&nbsp;org.quartz.JobExecutionContext;&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">import&nbsp;org.quartz.JobExecutionException;&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">/**&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;*&nbsp;需要执行的任务&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;*&nbsp;@author&nbsp;lhy&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;*&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;*/&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">public&nbsp;class&nbsp;MyJob&nbsp;implements&nbsp;Job&nbsp;{&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;@Override&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;//把要执行的操作，写在execute方法中&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;public&nbsp;void&nbsp;execute(JobExecutionContext&nbsp;arg0)&nbsp;throws&nbsp;JobExecutionException&nbsp;{&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;System.out.println("测试Quartz"+new&nbsp;Date());&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;}&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">}&nbsp;&nbsp;</span>
				</li>
			</ol>
		</div>
&nbsp;使用SimpleTrigger触发器
	</div>
	<div style="font-family:宋体;font-size:14px;">
		<div class="dp-highlighter bg_html" style="font-family:Consolas, &quot;font-size:12px;background-color:#E7E5DC;width:936.531px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;margin:18px 0px !important;">
			<div class="bar" style="padding-left:45px;">
				<div class="tools" style="padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #999999;">
					<b>[html]</b>&nbsp;<a href="http://blog.csdn.net/yuebinghaoyuan/article/details/9045471#" class="ViewSource" title="view plain" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">view plain</a><span data-mod="popu_168">&nbsp;<a href="http://blog.csdn.net/yuebinghaoyuan/article/details/9045471#" class="CopyToClipboard" title="copy" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">copy</a>
					<div style="position:absolute;left:764px;top:1857px;width:27px;height:15px;z-index:99;">
					</div>
</span><span data-mod="popu_169">&nbsp;<a href="http://blog.csdn.net/yuebinghaoyuan/article/details/9045471#" class="PrintSource" title="print" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">print</a></span><a href="http://blog.csdn.net/yuebinghaoyuan/article/details/9045471#" class="About" title="?" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">?</a>
				</div>
			</div>
			<ol start="1" class="dp-xml" style="padding:0px;border:none;list-style-position:initial;list-style-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span style="margin:0px;padding:0px;border:none;background-color:inherit;">package&nbsp;com.test;&nbsp;&nbsp;</span></span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">import&nbsp;java.util.Date;&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">import&nbsp;org.quartz.JobDetail;&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">import&nbsp;org.quartz.Scheduler;&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">import&nbsp;org.quartz.SchedulerException;&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">import&nbsp;org.quartz.SchedulerFactory;&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">import&nbsp;org.quartz.SimpleTrigger;&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">import&nbsp;org.quartz.impl.StdSchedulerFactory;&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">/**&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;*&nbsp;调用任务的类&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;*&nbsp;@author&nbsp;lhy&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;*&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;*/&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">public&nbsp;class&nbsp;SchedulerTest&nbsp;{&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;public&nbsp;static&nbsp;void&nbsp;main(String[]&nbsp;args)&nbsp;{&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;//通过schedulerFactory获取一个调度器&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;SchedulerFactory&nbsp;<span class="attribute" style="margin:0px;padding:0px;border:none;color:red;background-color:inherit;">schedulerfactory</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">=</span><span class="attribute-value" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">new</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;StdSchedulerFactory();&nbsp;&nbsp;</span></span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Scheduler&nbsp;<span class="attribute" style="margin:0px;padding:0px;border:none;color:red;background-color:inherit;">scheduler</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">=</span><span class="attribute-value" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">null</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">;&nbsp;&nbsp;</span></span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;try{&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">//&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;通过schedulerFactory获取一个调度器&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="attribute" style="margin:0px;padding:0px;border:none;color:red;background-color:inherit;">scheduler</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">=</span><span class="attribute-value" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">schedulerfactory</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">.getScheduler();&nbsp;&nbsp;</span></span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">//&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;创建jobDetail实例，绑定Job实现类&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">//&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;指明job的名称，所在组的名称，以及绑定job类&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;JobDetail&nbsp;<span class="attribute" style="margin:0px;padding:0px;border:none;color:red;background-color:inherit;">jobDetail</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">=</span><span class="attribute-value" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">new</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;JobDetail("job1",&nbsp;"jgroup1",&nbsp;MyJob.class);&nbsp;&nbsp;</span></span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">//&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;定义调度触发规则，比如每1秒运行一次，共运行8次&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;SimpleTrigger&nbsp;<span class="attribute" style="margin:0px;padding:0px;border:none;color:red;background-color:inherit;">simpleTrigger</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">=</span><span class="attribute-value" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">new</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;SimpleTrigger("simpleTrigger","triggerGroup");&nbsp;&nbsp;</span></span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">//&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;马上启动&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;simpleTrigger.setStartTime(new&nbsp;Date());&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">//&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;间隔时间&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;simpleTrigger.setRepeatInterval(1000);&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">//&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;运行次数&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;simpleTrigger.setRepeatCount(8);&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">//&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;把作业和触发器注册到任务调度中&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;scheduler.scheduleJob(jobDetail,&nbsp;simpleTrigger);&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">//&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;启动调度&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;scheduler.start();&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}catch(SchedulerException&nbsp;e){&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;e.printStackTrace();&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">}&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">}&nbsp;&nbsp;</span>
				</li>
			</ol>
		</div>
&nbsp;若使用CornTrigger触发器：&nbsp;
	</div>
	<div style="font-family:宋体;font-size:14px;">
		<div class="dp-highlighter bg_html" style="font-family:Consolas, &quot;font-size:12px;background-color:#E7E5DC;width:936.531px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;margin:18px 0px !important;">
			<div class="bar" style="padding-left:45px;">
				<div class="tools" style="padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #999999;">
					<b>[html]</b>&nbsp;<a href="http://blog.csdn.net/yuebinghaoyuan/article/details/9045471#" class="ViewSource" title="view plain" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">view plain</a><span data-mod="popu_168">&nbsp;<a href="http://blog.csdn.net/yuebinghaoyuan/article/details/9045471#" class="CopyToClipboard" title="copy" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">copy</a>
					<div style="position:absolute;left:764px;top:2885px;width:27px;height:15px;z-index:99;">
					</div>
</span><span data-mod="popu_169">&nbsp;<a href="http://blog.csdn.net/yuebinghaoyuan/article/details/9045471#" class="PrintSource" title="print" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">print</a></span><a href="http://blog.csdn.net/yuebinghaoyuan/article/details/9045471#" class="About" title="?" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">?</a>
				</div>
			</div>
			<ol start="1" class="dp-xml" style="padding:0px;border:none;list-style-position:initial;list-style-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span style="margin:0px;padding:0px;border:none;background-color:inherit;">package&nbsp;com.test;&nbsp;&nbsp;</span></span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">import&nbsp;java.util.Date;&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">import&nbsp;org.quartz.CronTrigger;&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">import&nbsp;org.quartz.JobDetail;&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">import&nbsp;org.quartz.Scheduler;&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">import&nbsp;org.quartz.SchedulerException;&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">import&nbsp;org.quartz.SchedulerFactory;&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">import&nbsp;org.quartz.SimpleTrigger;&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">import&nbsp;org.quartz.impl.StdSchedulerFactory;&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">/**&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;*&nbsp;调用任务的类&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;*&nbsp;@author&nbsp;lhy&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;*&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;*/&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">public&nbsp;class&nbsp;CronTriggerTest&nbsp;{&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;public&nbsp;static&nbsp;void&nbsp;main(String[]&nbsp;args)&nbsp;{&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;//通过schedulerFactory获取一个调度器&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;SchedulerFactory&nbsp;<span class="attribute" style="margin:0px;padding:0px;border:none;color:red;background-color:inherit;">schedulerfactory</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">=</span><span class="attribute-value" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">new</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;StdSchedulerFactory();&nbsp;&nbsp;</span></span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Scheduler&nbsp;<span class="attribute" style="margin:0px;padding:0px;border:none;color:red;background-color:inherit;">scheduler</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">=</span><span class="attribute-value" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">null</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">;&nbsp;&nbsp;</span></span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;try{&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">//&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;通过schedulerFactory获取一个调度器&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="attribute" style="margin:0px;padding:0px;border:none;color:red;background-color:inherit;">scheduler</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">=</span><span class="attribute-value" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">schedulerfactory</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">.getScheduler();&nbsp;&nbsp;</span></span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">//&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;创建jobDetail实例，绑定Job实现类&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">//&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;指明job的名称，所在组的名称，以及绑定job类&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;JobDetail&nbsp;<span class="attribute" style="margin:0px;padding:0px;border:none;color:red;background-color:inherit;">jobDetail</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">=</span><span class="attribute-value" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">new</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;JobDetail("job1",&nbsp;"jgroup1",&nbsp;MyJob.class);&nbsp;&nbsp;</span></span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">//&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;定义调度触发规则，每天上午10：15执行&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;CronTrigger&nbsp;<span class="attribute" style="margin:0px;padding:0px;border:none;color:red;background-color:inherit;">cornTrigger</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">=</span><span class="attribute-value" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">new</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;CronTrigger("cronTrigger","triggerGroup");&nbsp;&nbsp;</span></span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">//&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;执行规则表达式&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;cornTrigger.setCronExpression("0&nbsp;15&nbsp;10&nbsp;*&nbsp;*&nbsp;?&nbsp;*");&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">//&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;把作业和触发器注册到任务调度中&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;scheduler.scheduleJob(jobDetail,&nbsp;cornTrigger);&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">//&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;启动调度&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;scheduler.start();&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}catch(Exception&nbsp;e){&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;e.printStackTrace();&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">}&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">}&nbsp;&nbsp;</span>
				</li>
			</ol>
		</div>
&nbsp; 对于2.0.2jar包如下：
	</div>
	<div style="font-family:宋体;font-size:14px;">
		&nbsp; 其中的job类不变，主要是调度类如下：
	</div>
	<div style="font-family:宋体;font-size:14px;">
		<div class="dp-highlighter bg_html" style="font-family:Consolas, &quot;font-size:12px;background-color:#E7E5DC;width:936.531px;overflow-x:auto;overflow-y:hidden;padding-top:1px;position:relative;margin:18px 0px !important;">
			<div class="bar" style="padding-left:45px;">
				<div class="tools" style="padding:3px 8px 10px 10px;font-stretch:normal;font-size:9px;line-height:normal;font-family:Verdana, Geneva, Arial, Helvetica, sans-serif;color:silver;background-color:#F8F8F8;border-left:3px solid #999999;">
					<b>[html]</b>&nbsp;<a href="http://blog.csdn.net/yuebinghaoyuan/article/details/9045471#" class="ViewSource" title="view plain" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">view plain</a><span data-mod="popu_168">&nbsp;<a href="http://blog.csdn.net/yuebinghaoyuan/article/details/9045471#" class="CopyToClipboard" title="copy" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">copy</a>
					<div style="position:absolute;left:764px;top:3867px;width:27px;height:15px;z-index:99;">
					</div>
</span><span data-mod="popu_169">&nbsp;<a href="http://blog.csdn.net/yuebinghaoyuan/article/details/9045471#" class="PrintSource" title="print" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">print</a></span><a href="http://blog.csdn.net/yuebinghaoyuan/article/details/9045471#" class="About" title="?" style="color:#A0A0A0;text-decoration-line:none;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;background-color:inherit;border:none;padding:0px;margin:0px 10px 0px 0px;font-size:9px;">?</a>
				</div>
			</div>
			<ol start="1" class="dp-xml" style="padding:0px;border:none;list-style-position:initial;list-style-image:initial;background-color:#FFFFFF;color:#5C5C5C;margin:0px 0px 1px 45px !important;">
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;"><span style="margin:0px;padding:0px;border:none;background-color:inherit;">package&nbsp;com.test;&nbsp;&nbsp;</span></span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">import&nbsp;java.util.Date;&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">import&nbsp;org.quartz.CronScheduleBuilder;&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">import&nbsp;org.quartz.JobBuilder;&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">import&nbsp;org.quartz.JobDetail;&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">import&nbsp;org.quartz.Scheduler;&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">import&nbsp;org.quartz.SchedulerException;&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">import&nbsp;org.quartz.SchedulerFactory;&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">import&nbsp;org.quartz.SimpleScheduleBuilder;&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">import&nbsp;org.quartz.Trigger;&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">import&nbsp;org.quartz.TriggerBuilder;&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">import&nbsp;org.quartz.impl.StdSchedulerFactory;&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">/**&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;*&nbsp;调用任务的类&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;*&nbsp;@author&nbsp;lhy&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;*&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;*/&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">public&nbsp;class&nbsp;SchedulerTest&nbsp;{&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;public&nbsp;static&nbsp;void&nbsp;main(String[]&nbsp;args)&nbsp;{&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;//通过schedulerFactory获取一个调度器&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;SchedulerFactory&nbsp;<span class="attribute" style="margin:0px;padding:0px;border:none;color:red;background-color:inherit;">schedulerfactory</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">=</span><span class="attribute-value" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">new</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">&nbsp;StdSchedulerFactory();&nbsp;&nbsp;</span></span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Scheduler&nbsp;<span class="attribute" style="margin:0px;padding:0px;border:none;color:red;background-color:inherit;">scheduler</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">=</span><span class="attribute-value" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">null</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">;&nbsp;&nbsp;</span></span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;try{&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">//&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;通过schedulerFactory获取一个调度器&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="attribute" style="margin:0px;padding:0px;border:none;color:red;background-color:inherit;">scheduler</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">=</span><span class="attribute-value" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">schedulerfactory</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">.getScheduler();&nbsp;&nbsp;</span></span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">//&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;创建jobDetail实例，绑定Job实现类&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">//&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;指明job的名称，所在组的名称，以及绑定job类&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;JobDetail&nbsp;<span class="attribute" style="margin:0px;padding:0px;border:none;color:red;background-color:inherit;">job</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">=</span><span class="attribute-value" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">JobBuilder</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">.newJob(MyJob.class).withIdentity("job1",&nbsp;"jgroup1").build();&nbsp;&nbsp;</span></span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">//&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;定义调度触发规则&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">//&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;使用simpleTrigger规则&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">//&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Trigger&nbsp;<span class="attribute" style="margin:0px;padding:0px;border:none;color:red;background-color:inherit;">trigger</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">=</span><span class="attribute-value" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">TriggerBuilder</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">.newTrigger().withIdentity("simpleTrigger",&nbsp;"triggerGroup")&nbsp;&nbsp;</span></span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">//&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;.withSchedule(SimpleScheduleBuilder.repeatSecondlyForever(1).withRepeatCount(8))&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">//&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;.startNow().build();&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">//&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;使用cornTrigger规则&nbsp;&nbsp;每天10点42分&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Trigger&nbsp;<span class="attribute" style="margin:0px;padding:0px;border:none;color:red;background-color:inherit;">trigger</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">=</span><span class="attribute-value" style="margin:0px;padding:0px;border:none;color:blue;background-color:inherit;">TriggerBuilder</span><span style="margin:0px;padding:0px;border:none;background-color:inherit;">.newTrigger().withIdentity("simpleTrigger",&nbsp;"triggerGroup")&nbsp;&nbsp;</span></span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;.withSchedule(CronScheduleBuilder.cronSchedule("0&nbsp;42&nbsp;10&nbsp;*&nbsp;*&nbsp;?&nbsp;*"))&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;.startNow().build();&nbsp;&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">//&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;把作业和触发器注册到任务调度中&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;scheduler.scheduleJob(job,&nbsp;trigger);&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">//&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;启动调度&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;scheduler.start();&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}catch(Exception&nbsp;e){&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;e.printStackTrace();&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>
				</li>
				<li class="" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:#555555;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">}&nbsp;&nbsp;</span>
				</li>
				<li class="alt" style="margin:0px !important;padding:0px 3px 0px 10px !important;border-top:none;border-right:none;border-bottom:none;border-left:3px solid #999999;border-image:initial;list-style-type:decimal-leading-zero;list-style-image:initial;background-color:#F5FAE2;color:inherit;line-height:18px;list-style-position:outside !important;">
					<span style="margin:0px;padding:0px;border:none;color:black;background-color:inherit;">}&nbsp;&nbsp;</span>
				</li>
			</ol>
		</div>
&nbsp; 上述demo下载：<a href="http://download.csdn.net/detail/llhhyy1989/5536893" style="color:#FF9900;text-decoration-line:none;">1.8版本demo下载</a>
	</div>
	<div style="font-family:宋体;font-size:14px;">
		&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<a href="http://download.csdn.net/detail/llhhyy1989/5536977" style="color:#FF9900;text-decoration-line:none;">2.0版本demo下载</a>
	</div>
	<div style="font-family:宋体;font-size:14px;">
		&nbsp;&nbsp;
	</div>
	<div style="font-family:宋体;font-size:14px;">
		&nbsp; 对于CornExpress讲解如下：&nbsp;
	</div>
	<div style="font-family:宋体;font-size:14px;">
		<div style="white-space:normal;background-color:#FFFFFF;font-family:Arial;">
			字段 &nbsp; 允许值 &nbsp; 允许的特殊字符 &nbsp; &nbsp;
		</div>
		<div style="white-space:normal;background-color:#FFFFFF;font-family:Arial;">
			秒 &nbsp; &nbsp;0-59 &nbsp; &nbsp;, - * / &nbsp; &nbsp;
		</div>
		<div style="white-space:normal;background-color:#FFFFFF;font-family:Arial;">
			分 &nbsp; &nbsp;0-59 &nbsp; &nbsp;, - * / &nbsp; &nbsp;
		</div>
		<div style="white-space:normal;background-color:#FFFFFF;font-family:Arial;">
			小时 &nbsp; &nbsp;0-23 &nbsp; &nbsp;, - * / &nbsp; &nbsp;
		</div>
		<div style="white-space:normal;background-color:#FFFFFF;font-family:Arial;">
			日期 &nbsp; &nbsp;1-31 &nbsp; &nbsp;, - * ? / L W C &nbsp; &nbsp;
		</div>
		<div style="white-space:normal;background-color:#FFFFFF;font-family:Arial;">
			月份 &nbsp; &nbsp;1-12 或者 JAN-DEC &nbsp; &nbsp;, - * / &nbsp; &nbsp;
		</div>
		<div style="white-space:normal;background-color:#FFFFFF;font-family:Arial;">
			星期 &nbsp; &nbsp;1-7 或者 SUN-SAT &nbsp; &nbsp;, - * ? / L C # &nbsp; &nbsp;
		</div>
		<div style="white-space:normal;background-color:#FFFFFF;font-family:Arial;">
			年（可选） &nbsp; &nbsp;留空, 1970-2099 &nbsp; &nbsp;, - * / &nbsp; &nbsp;
		</div>
		<div style="white-space:normal;background-color:#FFFFFF;font-family:Arial;">
			&nbsp;&nbsp;
		</div>
		<div style="white-space:normal;background-color:#FFFFFF;font-family:Arial;">
			表达式 &nbsp; 意义 &nbsp; &nbsp;
		</div>
		<div style="white-space:normal;background-color:#FFFFFF;font-family:Arial;">
			"0 0 12 * * ?" &nbsp; &nbsp;每天中午12点触发 &nbsp; &nbsp;
		</div>
		<div style="white-space:normal;background-color:#FFFFFF;font-family:Arial;">
			"0 15 10 ? * *" &nbsp; &nbsp;每天上午10:15触发 &nbsp; &nbsp;
		</div>
		<div style="white-space:normal;background-color:#FFFFFF;font-family:Arial;">
			"0 15 10 * * ?" &nbsp; &nbsp;每天上午10:15触发 &nbsp; &nbsp;
		</div>
		<div style="white-space:normal;background-color:#FFFFFF;font-family:Arial;">
			"0 15 10 * * ? *" &nbsp; &nbsp;每天上午10:15触发 &nbsp; &nbsp;
		</div>
		<div style="white-space:normal;background-color:#FFFFFF;font-family:Arial;">
			"0 15 10 * * ? 2005" &nbsp; &nbsp;2005年的每天上午10:15触发 &nbsp; &nbsp;
		</div>
		<div style="white-space:normal;background-color:#FFFFFF;font-family:Arial;">
			"0 * 14 * * ?" &nbsp; &nbsp;在每天下午2点到下午2:59期间的每1分钟触发 &nbsp; &nbsp;
		</div>
		<div style="white-space:normal;background-color:#FFFFFF;font-family:Arial;">
			"0 0/5 14 * * ?" &nbsp; &nbsp;在每天下午2点到下午2:55期间的每5分钟触发 &nbsp; &nbsp;&nbsp;
		</div>
		<div style="white-space:normal;background-color:#FFFFFF;font-family:Arial;">
			"0 0/5 14,18 * * ?" &nbsp; &nbsp;在每天下午2点到2:55期间和下午6点到6:55期间的每5分钟触发 &nbsp; &nbsp;&nbsp;
		</div>
		<div style="white-space:normal;background-color:#FFFFFF;font-family:Arial;">
			"0 0-5 14 * * ?" &nbsp; &nbsp;在每天下午2点到下午2:05期间的每1分钟触发 &nbsp; &nbsp;
		</div>
		<div style="white-space:normal;background-color:#FFFFFF;font-family:Arial;">
			"0 10,44 14 ? 3 WED" &nbsp; &nbsp;每年三月的星期三的下午2:10和2:44触发 &nbsp; &nbsp;
		</div>
		<div style="white-space:normal;background-color:#FFFFFF;font-family:Arial;">
			"0 15 10 ? * MON-FRI" &nbsp; &nbsp;周一至周五的上午10:15触发 &nbsp; &nbsp;
		</div>
		<div style="white-space:normal;background-color:#FFFFFF;font-family:Arial;">
			"0 15 10 15 * ?" &nbsp; &nbsp;每月15日上午10:15触发 &nbsp; &nbsp;
		</div>
		<div style="white-space:normal;background-color:#FFFFFF;font-family:Arial;">
			"0 15 10 L * ?" &nbsp; &nbsp;每月最后一日的上午10:15触发 &nbsp; &nbsp;
		</div>
		<div style="white-space:normal;background-color:#FFFFFF;font-family:Arial;">
			"0 15 10 ? * 6L" &nbsp; &nbsp;每月的最后一个星期五上午10:15触发 &nbsp; &nbsp; &nbsp;
		</div>
		<div style="white-space:normal;background-color:#FFFFFF;font-family:Arial;">
			"0 15 10 ? * 6L 2002-2005" &nbsp; &nbsp;2002年至2005年的每月的最后一个星期五上午10:15触发 &nbsp; &nbsp;
		</div>
		<div style="white-space:normal;background-color:#FFFFFF;font-family:Arial;">
			"0 15 10 ? * 6#3" &nbsp; &nbsp;每月的第三个星期五上午10:15触发 &nbsp; &nbsp;&nbsp;
		</div>
		<div style="white-space:normal;background-color:#FFFFFF;font-family:Arial;">
			&nbsp;&nbsp;
		</div>
		<div style="white-space:normal;background-color:#FFFFFF;font-family:Arial;">
			特殊字符 &nbsp; 意义 &nbsp; &nbsp;
		</div>
		<div style="white-space:normal;background-color:#FFFFFF;font-family:Arial;">
			* &nbsp; &nbsp;表示所有值； &nbsp; &nbsp;
		</div>
		<div style="white-space:normal;background-color:#FFFFFF;font-family:Arial;">
			? &nbsp; &nbsp;表示未说明的值，即不关心它为何值； &nbsp; &nbsp;
		</div>
		<div style="white-space:normal;background-color:#FFFFFF;font-family:Arial;">
			- &nbsp; &nbsp;表示一个指定的范围； &nbsp; &nbsp;
		</div>
		<div style="white-space:normal;background-color:#FFFFFF;font-family:Arial;">
			, &nbsp; &nbsp;表示附加一个可能值； &nbsp; &nbsp;
		</div>
		<div style="white-space:normal;background-color:#FFFFFF;font-family:Arial;">
			/ &nbsp; &nbsp;符号前表示开始时间，符号后表示每次递增的值； &nbsp; &nbsp;
		</div>
		<div style="white-space:normal;background-color:#FFFFFF;font-family:Arial;">
			L("last") &nbsp; &nbsp;("last") "L" 用在day-of-month字段意思是 "这个月最后一天"；用在 day-of-week字段, 它简单意思是 "7" or "SAT"。 如果在day-of-week字段里和数字联合使用，它的意思就是 "这个月的最后一个星期几" – 例如： "6L" means "这个月的最后一个星期五". 当我们用“L”时，不指明一个列表值或者范围是很重要的，不然的话，我们会得到一些意想不到的结果。 &nbsp; &nbsp;
		</div>
		<div style="white-space:normal;background-color:#FFFFFF;font-family:Arial;">
			W("weekday") &nbsp; &nbsp;只能用在day-of-month字段。用来描叙最接近指定天的工作日（周一到周五）。例如：在day-of-month字段用“15W”指“最接近这个月第15天的工作日”，即如果这个月第15天是周六，那么触发器将会在这个月第14天即周五触发；如果这个月第15天是周日，那么触发器将会在这个月第16天即周一触发；如果这个月第15天是周二，那么就在触发器这天触发。注意一点：这个用法只会在当前月计算值，不会越过当前月。“W”字符仅能在day-of-month指明一天，不能是一个范围或列表。也可以用“LW”来指定这个月的最后一个工作日。 &nbsp; &nbsp;&nbsp;
		</div>
		<div style="white-space:normal;background-color:#FFFFFF;font-family:Arial;">
			# &nbsp; &nbsp;只能用在day-of-week字段。用来指定这个月的第几个周几。例：在day-of-week字段用"6#3"指这个月第3个周五（6指周五，3指第3个）。如果指定的日期不存在，触发器就不会触发。 &nbsp; &nbsp;&nbsp;
		</div>
		<div style="white-space:normal;background-color:#FFFFFF;font-family:Arial;">
			C &nbsp; &nbsp;指和calendar联系后计算过的值。例：在day-of-month 字段用“5C”指在这个月第5天或之后包括calendar的第一天；在day-of-week字段用“1C”指在这周日或之后包括calendar的第一天 &nbsp;
		</div>
		<div>
			<br />
		</div>
	</div>
</div>