<p>
	https://www.centos.bz/2012/06/make-rpm-package-methods/
</p>
<p>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:16px;color:#444444;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		RPM是<a href="https://www.centos.bz/tag/redhat/" style="box-sizing:border-box;background:transparent;color:#428BCA;">RedHat</a>&nbsp;Package Manager（RedHat软件包管理工具）的缩写,是一种用于互联网下载包的打包及安装工具，它包含在某些<a href="https://www.centos.bz/tag/linux/" style="box-sizing:border-box;background:transparent;color:#428BCA;">Linux</a>分发版中。它生成具有.RPM扩展名的文件。使用rpm安装软件和管理软件非常的方便。而这节我们不是介绍如何使用rpm安装或管理软件，而是如何把源码制作成rpm包。<br style="box-sizing:border-box;" />
下面我们以制作<a href="https://www.centos.bz/category/web-server/nginx/" style="box-sizing:border-box;background:transparent;color:#428BCA;">nginx</a>的rpm开始介绍其制作方法。以下操作在<a href="https://www.centos.bz/tag/centos/" style="box-sizing:border-box;background:transparent;color:#428BCA;">centos</a>-5 32系统进行。
	</p>
	<h3 id="制作nginx的rpm例子" style="box-sizing:border-box;font-family:&quot;line-height:1.1;color:green;margin-top:20px;margin-bottom:16px;font-size:16px;border-bottom:1px solid #EEEEEE;padding-bottom:0px;white-space:normal;background-color:#FFFFFF;">
		制作nginx的rpm例子
	</h3>
	<h4 id="1、建立目录结构" style="box-sizing:border-box;font-family:&quot;font-weight:500;line-height:1.1;color:#444444;margin-top:10px;margin-bottom:10px;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		1、建立目录结构
	</h4>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:16px;color:#444444;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		/usr/src/redhat/SOURCES — 存放源代码，补丁，图标等文件。<br style="box-sizing:border-box;" />
/usr/src/redhat/SPECS — 存放用于管理rpm制作进程的spec文件。<br style="box-sizing:border-box;" />
/usr/src/redhat/BUILD — 解压后的文件存放在这里。<br style="box-sizing:border-box;" />
/usr/src/redhat/RPMS — 存放由rpmbuild制作好的二进制包。<br style="box-sizing:border-box;" />
/usr/src/redhat/SRPMS —存放由rpmbuild制作好的源码包。
	</p>
	<div class="hl-surround" style="box-sizing:border-box;background-color:#F9FBFC;border:1px solid #C3CED9;margin:0px 0px 5px;width:auto;height:auto;overflow:auto;font-family:Fixedsys, &quot;color:#444444;font-size:15px;white-space:normal;">
		<ol class="hl-main ln-hide" title="Double click to show line number." style="box-sizing:border-box;margin:0px;padding:0px 12px 0px 56px;background-image:url(&quot;list-style-type:none !important;background-color:transparent;background-repeat:no-repeat;background-position:5px 5px;">
			<li class="hl-firstline" style="box-sizing:border-box;border-top-width:1px;border-top-style:solid;border-left:1px solid #C3CED9;list-style-type:none !important;border-top-color:#E3EEF9 !important;font-size:12px !important;margin:0px !important;line-height:20px !important;padding:0px 0px 0px 12px !important;">
				mkdir -p /usr/src/redhat
			</li>
			<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style-type:none !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
				cd /usr/src/redhat
			</li>
			<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style-type:none !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
				mkdir SOURCES SPECS BUILD RPMS SRPMS
			</li>
		</ol>
	</div>
	<h4 id="2、下载源码包" style="box-sizing:border-box;font-family:&quot;font-weight:500;line-height:1.1;color:#444444;margin-top:10px;margin-bottom:10px;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		2、下载源码包
	</h4>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:16px;color:#444444;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		下载源码包到SOURCES目录，不需要解压。
	</p>
	<div class="hl-surround" style="box-sizing:border-box;background-color:#F9FBFC;border:1px solid #C3CED9;margin:0px 0px 5px;width:auto;height:auto;overflow:auto;font-family:Fixedsys, &quot;color:#444444;font-size:15px;white-space:normal;">
		<ol class="hl-main ln-hide" title="Double click to show line number." style="box-sizing:border-box;margin:0px;padding:0px 12px 0px 56px;background-image:url(&quot;list-style-type:none !important;background-color:transparent;background-repeat:no-repeat;background-position:5px 5px;">
			<li class="hl-firstline" style="box-sizing:border-box;border-top-width:1px;border-top-style:solid;border-left:1px solid #C3CED9;list-style-type:none !important;border-top-color:#E3EEF9 !important;font-size:12px !important;margin:0px !important;line-height:20px !important;padding:0px 0px 0px 12px !important;">
				cd /usr/src/redhat/SOURCES
			</li>
			<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style-type:none !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
				wget http://nginx.org/download/nginx-1.2.1.tar.gz
			</li>
		</ol>
	</div>
	<h4 id="3、创建Spec文件" style="box-sizing:border-box;font-family:&quot;font-weight:500;line-height:1.1;color:#444444;margin-top:10px;margin-bottom:10px;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		3、创建Spec文件
	</h4>
	<div class="hl-surround" style="box-sizing:border-box;background-color:#F9FBFC;border:1px solid #C3CED9;margin:0px 0px 5px;width:auto;height:auto;overflow:auto;font-family:Fixedsys, &quot;color:#444444;font-size:15px;white-space:normal;">
		<ol class="hl-main ln-hide" title="Double click to show line number." style="box-sizing:border-box;margin:0px;padding:0px 12px 0px 56px;background-image:url(&quot;list-style-type:none !important;background-color:transparent;background-repeat:no-repeat;background-position:5px 5px;">
			<li class="hl-firstline" style="box-sizing:border-box;border-top-width:1px;border-top-style:solid;border-left:1px solid #C3CED9;list-style-type:none !important;border-top-color:#E3EEF9 !important;font-size:12px !important;margin:0px !important;line-height:20px !important;padding:0px 0px 0px 12px !important;">
				cd /usr/src/redhat/SPECS
			</li>
			<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style-type:none !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
				vi nginx.spec
			</li>
		</ol>
	</div>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:16px;color:#444444;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		内容如下：
	</p>
	<div class="hl-surround" style="box-sizing:border-box;background-color:#F9FBFC;border:1px solid #C3CED9;margin:0px 0px 5px;width:auto;height:auto;overflow:auto;font-family:Fixedsys, &quot;color:#444444;font-size:15px;white-space:normal;">
		<ol class="hl-main ln-show" title="Double click to hide line number." style="box-sizing:border-box;margin:0px;padding:0px 12px 0px 56px;background-image:url(&quot;background-color:transparent;background-repeat:no-repeat;background-position:5px 5px;list-style-position:outside !important;list-style-image:initial !important;">
			<li class="hl-firstline" style="box-sizing:border-box;border-top-width:1px;border-top-style:solid;border-left:1px solid #C3CED9;list-style:decimal outside !important;border-top-color:#E3EEF9 !important;font-size:12px !important;margin:0px !important;line-height:20px !important;padding:0px 0px 0px 12px !important;">
				#
			</li>
			<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
				# Example spec file for nginx
			</li>
			<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
				#
			</li>
			<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
				Summary: high performance web server
			</li>
			<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
				Name: nginx
			</li>
			<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
				Version: 1.2.1
			</li>
			<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
				Release: 1.el5.ngx
			</li>
			<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
				License: 2-clause BSD-like license
			</li>
			<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
				Group: Applications/Server
			</li>
			<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
				Source: http://nginx.org/download/nginx-1.2.1.tar.gz
			</li>
			<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
				URL: http://nginx.org/
			</li>
			<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
				Distribution: Linux
			</li>
			<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
				Packager: zhumaohai &lt;admin@www.centos.bz&gt;
			</li>
			<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
				&nbsp;
			</li>
			<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
				%description
			</li>
			<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
				nginx [engine x] is a HTTP and reverse proxy server, as well as
			</li>
			<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
				a mail proxy server
			</li>
			<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
				%prep
			</li>
			<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
				rm -rf $RPM_BUILD_DIR/nginx-1.2.1
			</li>
			<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
				zcat $RPM_SOURCE_DIR/nginx-1.2.1.tar.gz | tar -xvf -
			</li>
			<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
				%build
			</li>
			<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
				cd nginx-1.2.1
			</li>
			<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
				./configure --prefix=/usr/local/nginx
			</li>
			<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
				make
			</li>
			<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
				%install
			</li>
			<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
				cd nginx-1.2.1
			</li>
			<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
				make install
			</li>
			<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
				%preun
			</li>
			<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
				if [ -z "`ps aux | grep nginx | grep -v grep`" ];then
			</li>
			<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
				killall nginx &gt;/dev/null
			</li>
			<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
				exit 0
			</li>
			<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
				fi
			</li>
			<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
				%files
			</li>
			<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style:decimal outside !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
				/usr/local/nginx
			</li>
		</ol>
	</div>
	<h4 id="4、开始RPM制作" style="box-sizing:border-box;font-family:&quot;font-weight:500;line-height:1.1;color:#444444;margin-top:10px;margin-bottom:10px;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		4、开始RPM制作
	</h4>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:16px;color:#444444;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		在制作RPM包之前需要安装必要的工具，如rpmbuild,gcc等。
	</p>
	<div class="hl-surround" style="box-sizing:border-box;background-color:#F9FBFC;border:1px solid #C3CED9;margin:0px 0px 5px;width:auto;height:auto;overflow:auto;font-family:Fixedsys, &quot;color:#444444;font-size:15px;white-space:normal;">
		<ol class="hl-main ln-hide" title="Double click to show line number." style="box-sizing:border-box;margin:0px;padding:0px 12px 0px 56px;background-image:url(&quot;list-style-type:none !important;background-color:transparent;background-repeat:no-repeat;background-position:5px 5px;">
			<li class="hl-firstline" style="box-sizing:border-box;border-top-width:1px;border-top-style:solid;border-left:1px solid #C3CED9;list-style-type:none !important;border-top-color:#E3EEF9 !important;font-size:12px !important;margin:0px !important;line-height:20px !important;padding:0px 0px 0px 12px !important;">
				yum install gcc rpm-build pcre-devel
			</li>
		</ol>
	</div>
	<div class="hl-surround" style="box-sizing:border-box;background-color:#F9FBFC;border:1px solid #C3CED9;margin:0px 0px 5px;width:auto;height:auto;overflow:auto;font-family:Fixedsys, &quot;color:#444444;font-size:15px;white-space:normal;">
		<ol class="hl-main ln-hide" title="Double click to show line number." style="box-sizing:border-box;margin:0px;padding:0px 12px 0px 56px;background-image:url(&quot;list-style-type:none !important;background-color:transparent;background-repeat:no-repeat;background-position:5px 5px;">
			<li class="hl-firstline" style="box-sizing:border-box;border-top-width:1px;border-top-style:solid;border-left:1px solid #C3CED9;list-style-type:none !important;border-top-color:#E3EEF9 !important;font-size:12px !important;margin:0px !important;line-height:20px !important;padding:0px 0px 0px 12px !important;">
				cd /usr/src/redhat/SPECS/
			</li>
			<li style="box-sizing:border-box;border-left:1px solid #C3CED9;border-top-width:1px;border-top-style:solid;list-style-type:none !important;font-size:12px !important;margin:0px !important;line-height:20px !important;border-top-color:#E3EEF9 !important;padding:0px 0px 0px 12px !important;">
				rpmbuild -bb nginx.spec
			</li>
		</ol>
	</div>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:16px;color:#444444;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		一切顺利的话，会生成<a href="https://www.centos.bz/tag/nginx-2/" style="box-sizing:border-box;background:transparent;color:#428BCA;">nginx</a>的rpm包，/usr/src/redhat/RPMS/i386/nginx-1.2.1-1.el5.ngx.i386.rpm。
	</p>
	<h4 id="5、测试rpm包" style="box-sizing:border-box;font-family:&quot;font-weight:500;line-height:1.1;color:#444444;margin-top:10px;margin-bottom:10px;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		5、测试rpm包
	</h4>
	<div class="hl-surround" style="box-sizing:border-box;background-color:#F9FBFC;border:1px solid #C3CED9;margin:0px 0px 5px;width:auto;height:auto;overflow:auto;font-family:Fixedsys, &quot;color:#444444;font-size:15px;white-space:normal;">
		<ol class="hl-main ln-show" title="Double click to hide line number." style="box-sizing:border-box;margin:0px;padding:0px 12px 0px 56px;background-image:url(&quot;background-color:transparent;background-repeat:no-repeat;background-position:5px 5px;list-style-position:outside !important;list-style-image:initial !important;">
			<li class="hl-firstline" style="box-sizing:border-box;border-top-width:1px;border-top-style:solid;border-left:1px solid #C3CED9;list-style:decimal outside !important;border-top-color:#E3EEF9 !important;font-size:12px !important;margin:0px !important;line-height:20px !important;padding:0px 0px 0px 12px !important;">
				rpm -ivh /usr/src/redhat/RPMS/i386/nginx-1.2.1-1.el5.ngx.i386.rpm
			</li>
		</ol>
	</div>
	<h3 id="spec文件解释" style="box-sizing:border-box;font-family:&quot;line-height:1.1;color:green;margin-top:20px;margin-bottom:16px;font-size:16px;border-bottom:1px solid #EEEEEE;padding-bottom:0px;white-space:normal;background-color:#FFFFFF;">
		spec文件解释
	</h3>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:16px;color:#444444;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		从以上的简单例子可以看出，制作rpm包最重要的还是spec文件，下面解释一下例子所用到的指令。<br style="box-sizing:border-box;" />
#:以#开头是注释，rpm会忽略它。<br style="box-sizing:border-box;" />
Summary：简单描述软件。<br style="box-sizing:border-box;" />
Name ：定义rpm的名称。<br style="box-sizing:border-box;" />
Version: 定义软件版本<br style="box-sizing:border-box;" />
Release: 发行版本<br style="box-sizing:border-box;" />
License: 定义许可证<br style="box-sizing:border-box;" />
Group: 软件分类<br style="box-sizing:border-box;" />
<a href="https://www.centos.bz/tag/source/" style="box-sizing:border-box;background:transparent;color:#428BCA;">Source</a>: 源码下载地址<br style="box-sizing:border-box;" />
URL: 源码相关网站<br style="box-sizing:border-box;" />
Distribution: 发行版系列<br style="box-sizing:border-box;" />
Packager: 打包人的信息
	</p>
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:16px;color:#444444;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		%description:软件详细描述，可多行<br style="box-sizing:border-box;" />
%prep ：软件编译之前的处理，如解压。<br style="box-sizing:border-box;" />
%build ：开始编译软件，如make<br style="box-sizing:border-box;" />
%install :开始安装软件，如make install<br style="box-sizing:border-box;" />
%files :指定哪些文件需要被打包，如/usr/local/nginx<br style="box-sizing:border-box;" />
%preun :定义卸载之前的动作，如杀掉进程。<br style="box-sizing:border-box;" />
这里只介绍了几个常用的tag，更详细的请参考：<a href="http://www.rpm.org/max-rpm/ch-rpm-inside.html" target="_blank" style="box-sizing:border-box;background:transparent;color:#428BCA;">http://www.rpm.org/max-rpm/ch-rpm-inside.html</a>
	</p>
</p>