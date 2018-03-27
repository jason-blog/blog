<p>
	http://blog.csdn.net/qq496013218/article/details/74910155
</p>
<p>
	fuck 浪费了我好长时间才找到
</p>
<p>
	<br />
</p>
<p>
	<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;font-size:16px;color:#4F4F4F;line-height:26px;min-height:26px;text-align:justify;word-break:normal;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		<span style="box-sizing:border-box;font-size:14px;">一、从eclipse切换IntelliJ IDEA 也有一段时间了，基本上功能和快捷键都用的顺手了，感受到了IntelliJ IDEA 的强大。刚开始因为不熟悉这个强大的开发工具，所以分刚开始还是多走了一些弯路。我们的项目是划分了很多分布式的项目，多个服务，每次把几十个项目的pom.xml文件选中才能在右侧栏的Maven Projects展示。今天我们演示如何一次性把多个的Maven导入到Maven Projects中，首先如下图：</span>
	</p>
	<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;font-size:16px;color:#4F4F4F;line-height:26px;min-height:26px;text-align:justify;word-break:normal;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		<span style="box-sizing:border-box;font-size:14px;"><img src="http://img.blog.csdn.net/20170710105504556?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcXE0OTYwMTMyMTg=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" alt="" style="border-width:initial;border-style:none;box-sizing:border-box;margin:0px;max-width:100%;max-height:100%;" /><br style="box-sizing:border-box;" />
</span>
	</p>
	<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;font-size:16px;color:#4F4F4F;line-height:26px;min-height:26px;text-align:justify;word-break:normal;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		<span style="box-sizing:border-box;font-size:14px;">选中Module from Existing Sources...，然后如下图所示，操作如下：</span>
	</p>
	<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;font-size:16px;color:#4F4F4F;line-height:26px;min-height:26px;text-align:justify;word-break:normal;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		<span style="box-sizing:border-box;font-size:14px;"><img src="http://img.blog.csdn.net/20170710110018747?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcXE0OTYwMTMyMTg=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" alt="" style="border-width:initial;border-style:none;box-sizing:border-box;margin:0px;max-width:100%;max-height:100%;" /><br style="box-sizing:border-box;" />
</span>
	</p>
	<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;font-size:16px;color:#4F4F4F;line-height:26px;min-height:26px;text-align:justify;word-break:normal;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		<span style="box-sizing:border-box;font-size:14px;">选中项目的根目录，然后会出现下面的这个界面操作如下：</span>
	</p>
	<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;font-size:16px;color:#4F4F4F;line-height:26px;min-height:26px;text-align:justify;word-break:normal;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		<span style="box-sizing:border-box;font-size:14px;"><img src="http://img.blog.csdn.net/20170710110049544?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcXE0OTYwMTMyMTg=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" alt="" style="border-width:initial;border-style:none;box-sizing:border-box;margin:0px;max-width:100%;max-height:100%;" /><br style="box-sizing:border-box;" />
</span>
	</p>
	<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;font-size:16px;color:#4F4F4F;line-height:26px;min-height:26px;text-align:justify;word-break:normal;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		<span style="box-sizing:border-box;font-size:14px;">默认情况下是选中的Create modules from existing sources,我们选中下面一个import module from external model,然后next。继续下面的操作，如图所示：&nbsp;</span>
	</p>
	<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;font-size:16px;color:#4F4F4F;line-height:26px;min-height:26px;text-align:justify;word-break:normal;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		<span style="box-sizing:border-box;font-size:14px;"><img src="http://img.blog.csdn.net/20170710110315949?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcXE0OTYwMTMyMTg=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" alt="" style="border-width:initial;border-style:none;box-sizing:border-box;margin:0px;max-width:100%;max-height:100%;" /><br style="box-sizing:border-box;" />
</span>
	</p>
	<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;font-size:16px;color:#4F4F4F;line-height:26px;min-height:26px;text-align:justify;word-break:normal;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		<span style="box-sizing:border-box;font-size:14px;">选中红色框标记的Search from project recursively，然后next，出现下图界面：<img src="http://img.blog.csdn.net/20170710110442715?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcXE0OTYwMTMyMTg=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" alt="" style="border-width:initial;border-style:none;box-sizing:border-box;margin:0px;max-width:100%;max-height:100%;" /></span>
	</p>
	<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;font-size:16px;color:#4F4F4F;line-height:26px;min-height:26px;text-align:justify;word-break:normal;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		<span style="box-sizing:border-box;font-size:14px;">点击next,默认即可，操作如下：</span>
	</p>
	<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;font-size:16px;color:#4F4F4F;line-height:26px;min-height:26px;text-align:justify;word-break:normal;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		<span style="box-sizing:border-box;font-size:14px;"><img src="http://img.blog.csdn.net/20170710110515618?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcXE0OTYwMTMyMTg=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" alt="" style="border-width:initial;border-style:none;box-sizing:border-box;margin:0px;max-width:100%;max-height:100%;" /><br style="box-sizing:border-box;" />
</span>
	</p>
	<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;font-size:16px;color:#4F4F4F;line-height:26px;min-height:26px;text-align:justify;word-break:normal;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		<span style="box-sizing:border-box;font-size:14px;">最后是展示的导入maven project，点击next:</span>
	</p>
	<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;font-size:16px;color:#4F4F4F;line-height:26px;min-height:26px;text-align:justify;word-break:normal;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		<span style="box-sizing:border-box;font-size:14px;"><img src="http://img.blog.csdn.net/20170710110623786?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvcXE0OTYwMTMyMTg=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast" alt="" style="border-width:initial;border-style:none;box-sizing:border-box;margin:0px;max-width:100%;max-height:100%;" /><br style="box-sizing:border-box;" />
</span>
	</p>
	<p style="margin-top:0px;margin-bottom:16px;padding:0px;box-sizing:border-box;font-size:16px;color:#4F4F4F;line-height:26px;min-height:26px;text-align:justify;word-break:normal;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		<span style="box-sizing:border-box;font-size:14px;">最后一步next即可，完成之后，项目自动在右侧的maven projects展示，如果没有展示请使用快捷键 ctrl+shift +a。注意：快捷键可能存在冲突，导致无法使用。</span>
	</p>
</p>