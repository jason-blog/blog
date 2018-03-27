<span style="font-family:Tahoma;font-size:14px;white-space:normal;">LINUX如何用ls -l显示出文件的详细的年-月-日 时-分-秒？</span><br style="margin:0px;padding:0px;font-family:Tahoma;font-size:14px;white-space:normal;" />
<div class="iteye-blog-content-contain" style="margin:0px;padding:0px;font-family:Tahoma;font-size:14px;white-space:normal;">
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;">
		1.&nbsp;&nbsp; 给出命令：&nbsp; ls -l&nbsp; --time-style=full-iso (取值可以是： full-iso|long-iso|iso|locale等)<br style="margin:0px;padding:0px;" />
<br style="margin:0px;padding:0px;" />
2.&nbsp;&nbsp; 给出命令：&nbsp; ls -l&nbsp; --full-time<br style="margin:0px;padding:0px;" />
<br style="margin:0px;padding:0px;" />
3.&nbsp;&nbsp; 给出命令：&nbsp; ls -l --time-style="+%Y-%m-%d&nbsp; %H:%I:%S"&nbsp; (自己定制， 这个是我们一般想要的人性化格式)
	</p>
</div>