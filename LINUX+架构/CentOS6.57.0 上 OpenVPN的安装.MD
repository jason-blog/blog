<p>
	http://blog.csdn.net/rdcxuly/article/details/54909325
</p>
<p>
	<br />
</p>
<p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		CentOS&nbsp;<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">上</span>&nbsp;OpenVPN<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">的安装：</span>
	</p>
	<p class="p2" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<br />
	</p>
	<p class="p3" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		一、安装准备
	</p>
	<p class="p4" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<a href="http://www.oschina.net/question/54100_26864#" target="_blank" style="box-sizing:border-box;background:transparent;color:#CA0C16;text-decoration-line:none;margin:0px;padding:0px;outline:0px;">?</a>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		1<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">、安装</span>openssl<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">、</span>gcc<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">、</span>libpam
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#yum -y install openssl-devel openssl
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#yum -y install gcc gcc-c++
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#yum -y install pam-devel.x86_64
	</p>
	<p class="p2" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<br />
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">如遇</span>Segmentation Fault<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">，在</span>/usr/local/lib<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">下，删除链接</span>libz.so<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">和</span>libz.so.1
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#rm -f libz.so
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#rm -f libz.so.1
	</p>
	<p class="p5" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		安装完之后恢复这两个链接即可
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#ln -s libz.so.1.2.7 libz.so.1
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#ln -s libz.so.1 libz.so
	</p>
	<p class="p2" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<br />
	</p>
	<p class="p3" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		二、<span class="s2" style="box-sizing:border-box;margin:0px;padding:0px;">OpenVPN</span>服务端安装过程<span class="s2" style="box-sizing:border-box;margin:0px;padding:0px;"><br style="box-sizing:border-box;" />
</span>
	</p>
	<p class="p6" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<span class="s3" style="box-sizing:border-box;margin:0px;padding:0px;">下载</span><span class="s4" style="box-sizing:border-box;margin:0px;padding:0px;">lzo</span><span class="s3" style="box-sizing:border-box;margin:0px;padding:0px;">，下载链接为<a href="http://www.oberhumer.com/opensource/lzo/#download" target="_blank" style="box-sizing:border-box;background:transparent;color:#CA0C16;text-decoration-line:none;margin:0px;padding:0px;outline:0px;"><span class="s5" style="box-sizing:border-box;margin:0px;padding:0px;">http://www.oberhumer.com/opensource/lzo/#download</span></a></span><span class="s6" style="box-sizing:border-box;margin:0px;padding:0px;">，下载完之后复制到</span><span class="s7" style="box-sizing:border-box;margin:0px;padding:0px;">/var/tmp</span><span class="s6" style="box-sizing:border-box;margin:0px;padding:0px;">目录下</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		1<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">、</span>lzo<span class="s8" style="box-sizing:border-box;margin:0px;padding:0px;">的安装</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#cd /var/tmp&nbsp;&nbsp;&nbsp; //<span class="s8" style="box-sizing:border-box;margin:0px;padding:0px;">安装目录</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#gunzip zxvf lzo-2.04.tar.gz&nbsp;&nbsp;&nbsp; //<span class="s8" style="box-sizing:border-box;margin:0px;padding:0px;">解压</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#tar zxvf lzo-2.04.tar&nbsp;&nbsp;&nbsp; //<span class="s8" style="box-sizing:border-box;margin:0px;padding:0px;">解压</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#cd lzo-2.04
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#./configure&nbsp;&nbsp; &nbsp;
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#make
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#make install&nbsp;&nbsp; #<span class="s8" style="box-sizing:border-box;margin:0px;padding:0px;">编译与安装</span>
	</p>
	<p class="p2" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<br />
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		2<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">、</span>openvpn<span class="s8" style="box-sizing:border-box;margin:0px;padding:0px;">下载与安装</span>
	</p>
	<p class="p2" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<br />
	</p>
	<p class="p6" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<span class="s3" style="box-sizing:border-box;margin:0px;padding:0px;">下载</span><span class="s4" style="box-sizing:border-box;margin:0px;padding:0px;">openvpn</span><span class="s3" style="box-sizing:border-box;margin:0px;padding:0px;">，下载链接为<a href="https://openvpn.net/index.php/open-source/downloads.html" target="_blank" style="box-sizing:border-box;background:transparent;color:#CA0C16;text-decoration-line:none;margin:0px;padding:0px;outline:0px;"><span class="s5" style="box-sizing:border-box;margin:0px;padding:0px;">https://openvpn.net/index.php/open-source/downloads.html</span></a></span><span class="s6" style="box-sizing:border-box;margin:0px;padding:0px;">，下载完之后复制到</span><span class="s7" style="box-sizing:border-box;margin:0px;padding:0px;">/var/tmp</span><span class="s6" style="box-sizing:border-box;margin:0px;padding:0px;">目录下</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#cd /var/tmp
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#gunzip xvf openvpn-2.3.10.tar.gz
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#tar xvf openvpn-2.3.10.tar
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#./configure
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#make
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#make install
	</p>
	<p class="p2" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<br />
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">“</span>lzo enabled but missing<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">”</span>&nbsp;-&gt; lzo configure&nbsp;<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">改为</span>&nbsp;<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">“</span>./configure --prefix=/usr/local/<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">”</span><span style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;</span><span style="box-sizing:border-box;margin:0px;padding:0px;"></span>##CentOS 7&nbsp;<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">会遇到这个问题</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">“</span>libpam required but missting<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">”</span>&nbsp;-&gt;<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">安装</span>libpam&nbsp;<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">“</span>yum -y install pam-devel.x86_64<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">”</span><span style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;</span><span style="box-sizing:border-box;margin:0px;padding:0px;"></span>##CentOS 7&nbsp;<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">会遇到这个问题</span>
	</p>
	<p class="p2" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<br />
	</p>
	<p class="p5" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		安装好了检查一下<span class="s2" style="box-sizing:border-box;margin:0px;padding:0px;">openvpn</span>版本
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#openvpn --version
	</p>
	<p class="p2" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<br />
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		3<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">、</span>easy-sea<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">安装</span>
	</p>
	<p class="p6" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<span class="s3" style="box-sizing:border-box;margin:0px;padding:0px;">下载</span><span class="s4" style="box-sizing:border-box;margin:0px;padding:0px;">openvpn</span><span class="s3" style="box-sizing:border-box;margin:0px;padding:0px;">，下载链接为<a href="https://community.openvpn.net/openvpn/wiki/GettingEasyRsa" target="_blank" style="box-sizing:border-box;background:transparent;color:#CA0C16;text-decoration-line:none;margin:0px;padding:0px;outline:0px;"><span class="s5" style="box-sizing:border-box;margin:0px;padding:0px;">https://community.openvpn.net/openvpn/wiki/GettingEasyRsa</span></a></span><span class="s6" style="box-sizing:border-box;margin:0px;padding:0px;">，下载完之后复制到</span><span class="s7" style="box-sizing:border-box;margin:0px;padding:0px;">/var/tmp</span><span class="s6" style="box-sizing:border-box;margin:0px;padding:0px;">目录下</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#cd /var/tmp
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#gunzip xvf easy-rsa-2.2.0_master.tar.gz
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#tar xvf easy-rsa-2.2.0_master.tar
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#./configure
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#make
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#make install
	</p>
	<p class="p2" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<br />
	</p>
	<p class="p5" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		安装路径
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		/usr/local/share/easy-esa/
	</p>
	<p class="p2" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<br />
	</p>
	<p class="p3" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		三、制作证书
	</p>
	<p class="p3" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		复制源文件至目标路径
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#mkdir /etc/openvpn
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#cp -rf /usr/local/share/easy-rsa /etc/openvpn/
	</p>
	<p class="p7" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<br />
	</p>
	<p class="p3" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		0、配置vars
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#vi /etc/openvpn/easy-rsa/vars
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<strong style="box-sizing:border-box;">export KEY_SIZE=2048&nbsp; &nbsp; &nbsp; //DH</strong><span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">证书的长度设为</span><strong style="box-sizing:border-box;">2048</strong><span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">，缺省为</span><strong style="box-sizing:border-box;">1024</strong>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		…
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		export KEY_COUNTRY="CN"
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		export KEY_PROVINCE=<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">“</span>SH<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">”</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		export KEY_CITY=<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">“</span>Shanghai<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">”</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		export KEY_ORG=<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">“</span>jhrdc<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">”</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		export KEY_EMAIL=<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">“</span>admin@jh.cn<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">”</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		export KEY_OU=<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">“</span>jhrdc<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">“</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<strong style="box-sizing:border-box;">export KEY_NAME=</strong><span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">“</span><strong style="box-sizing:border-box;">jhrdc</strong><span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">”</span><strong style="box-sizing:border-box;">&nbsp;&nbsp; &nbsp; &nbsp; //</strong><span class="s8" style="box-sizing:border-box;margin:0px;padding:0px;"><strong style="box-sizing:border-box;">特别重要，“jhrdc”根据情况自己设定</strong></span>
	</p>
	<p class="p7" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<br />
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#cd /etc/openvpn/easy-rsa
	</p>
	<p class="p5" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<span class="s2" style="box-sizing:border-box;margin:0px;padding:0px;">#source vars&nbsp; //</span>执行脚本生成证书时，需要设置一些环境变量
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#./clean-all&nbsp; &nbsp; //<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">制作客户端证书时，不需要执行该脚本</span>
	</p>
	<p class="p7" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<br />
	</p>
	<p class="p3" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		1、生成根证书-CA证书，CA证书同时需要部署在服务器和客户端上
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#./build-ca
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#cp keys/ca.crt /etc/openvpn/
	</p>
	<p class="p7" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<br />
	</p>
	<p class="p5" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<span class="s2" style="box-sizing:border-box;margin:0px;padding:0px;">2</span>、<span class="s8" style="box-sizing:border-box;margin:0px;padding:0px;">生成</span>服务器端证书
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#./build-key-server jhrdc
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#./build-dh
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#cp keys/jhrdc.crt keys/jhrdc.key keys/dh2048.pem /etc/openvpn/
	</p>
	<p class="p2" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<br />
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		3<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">、</span>Client<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">端证书</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#./build-key jhrdc&nbsp; &nbsp;<strong style="box-sizing:border-box;">&nbsp;//</strong><span class="s8" style="box-sizing:border-box;margin:0px;padding:0px;"><strong style="box-sizing:border-box;">使用服务器端的CN设定</strong></span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<span style="box-sizing:border-box;">Generating a 2048 bit RSA private key</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<span style="box-sizing:border-box;">................................................................................................+++</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<span style="box-sizing:border-box;">....+++</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<span style="box-sizing:border-box;">writing new private key to&nbsp;</span><span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">‘</span><span style="box-sizing:border-box;">jhrdc.key'</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<span style="box-sizing:border-box;">-----</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<span style="box-sizing:border-box;">You are about to be asked to enter information that will be incorporated</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<span style="box-sizing:border-box;">into your certificate request.</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<span style="box-sizing:border-box;">What you are about to enter is what is called a Distinguished Name or a DN.</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<span style="box-sizing:border-box;">There are quite a few fields but you can leave some blank</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<span style="box-sizing:border-box;">For some fields there will be a default value</span><span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">,</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<span style="box-sizing:border-box;">If you enter '.'</span><span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">,</span><span style="box-sizing:border-box;">&nbsp;the field will be left blank.</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<span style="box-sizing:border-box;">-----</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<span style="box-sizing:border-box;">Country Name&nbsp;</span><span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">(</span><span style="box-sizing:border-box;">2 letter code</span><span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">)</span><span style="box-sizing:border-box;">&nbsp;</span><span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">[</span><span style="box-sizing:border-box;">CN</span><span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">]</span><span style="box-sizing:border-box;">:</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<span style="box-sizing:border-box;">State or Province Name&nbsp;</span><span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">(</span><span style="box-sizing:border-box;">full name</span><span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">)</span><span style="box-sizing:border-box;">&nbsp;</span><span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">[</span><span style="box-sizing:border-box;">SH</span><span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">]</span><span style="box-sizing:border-box;">:</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<span style="box-sizing:border-box;">Locality Name&nbsp;</span><span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">(</span><span style="box-sizing:border-box;">eg</span><span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">,</span><span style="box-sizing:border-box;">&nbsp;city</span><span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">)</span><span style="box-sizing:border-box;">&nbsp;</span><span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">[</span><span style="box-sizing:border-box;">Shanghai</span><span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">]</span><span style="box-sizing:border-box;">:</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<span style="box-sizing:border-box;">Organization Name&nbsp;</span><span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">(</span><span style="box-sizing:border-box;">eg</span><span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">,</span><span style="box-sizing:border-box;">&nbsp;company</span><span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">)</span><span style="box-sizing:border-box;">&nbsp;</span><span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">[</span><span style="box-sizing:border-box;">JH</span><span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">]</span><span style="box-sizing:border-box;">:</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<span style="box-sizing:border-box;">Organizational Unit Name&nbsp;</span><span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">(</span><span style="box-sizing:border-box;">eg</span><span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">,</span><span style="box-sizing:border-box;">&nbsp;section</span><span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">)</span><span style="box-sizing:border-box;">&nbsp;</span><span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">[</span><span style="box-sizing:border-box;">jhrdc</span><span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">]</span><span style="box-sizing:border-box;">:</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<span style="box-sizing:border-box;">Common Name&nbsp;</span><span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">(</span><span style="box-sizing:border-box;">eg</span><span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">,</span><span style="box-sizing:border-box;">&nbsp;your name or your server's hostname</span><span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">)</span><span style="box-sizing:border-box;">&nbsp;</span><span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">[</span><span style="box-sizing:border-box;">jhrdc</span><span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">]</span><span style="box-sizing:border-box;">:testchannel1&nbsp; &nbsp;&nbsp;</span><span class="s8" style="box-sizing:border-box;margin:0px;padding:0px;"><strong style="box-sizing:border-box;">//给不同的客户端创建证书和私钥时，可以使用不同名字</strong></span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<span style="box-sizing:border-box;">Name&nbsp;</span><span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">[</span><span style="box-sizing:border-box;">jhrdc</span><span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">]</span><span style="box-sizing:border-box;">:testchannel1</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<span style="box-sizing:border-box;">Email Address&nbsp;</span><span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">[</span><span style="box-sizing:border-box;">admin@jh.cn</span><span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">]</span><span style="box-sizing:border-box;">:</span>
	</p>
	<p class="p2" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<span style="box-sizing:border-box;"></span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<span style="box-sizing:border-box;">Please enter the following 'extra' attributes</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<span style="box-sizing:border-box;">to be sent with your certificate request</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<span style="box-sizing:border-box;">A challenge password&nbsp;</span><span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">[]</span><span style="box-sizing:border-box;">:</span>
	</p>
	<p class="p2" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<br />
	</p>
	<p class="p2" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<br />
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">如遇“</span>TXT_DB error number 2<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">”错误，重新</span>touch<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">一个</span>keys/index.txt
	</p>
	<p class="p2" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<br />
	</p>
	<p class="p5" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		生成的客户端证书位于<span class="s2" style="box-sizing:border-box;margin:0px;padding:0px;">/etc/openvpn/easy-rsa/keys</span>，分别是<span class="s2" style="box-sizing:border-box;margin:0px;padding:0px;">jhrdc.crt</span>、<span class="s2" style="box-sizing:border-box;margin:0px;padding:0px;">jhrdc.csr</span>、<span class="s2" style="box-sizing:border-box;margin:0px;padding:0px;">jhrdc.key</span>。这几个证书和前面所生成的服务器端的证书有所不同，仅可为客户端所使用，请将这几个证书文件和<span class="s2" style="box-sizing:border-box;margin:0px;padding:0px;">ca.crt</span>打包，拷贝到客户端电脑备用。
	</p>
	<p class="p2" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<br />
	</p>
	<p class="p5" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		注意，同一个证书，缺省配置情况下同时只能从一个客户端登陆
	</p>
	<p class="p2" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<br />
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">四、配置</span>openvpn<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">服务器</span>
	</p>
	<p class="p5" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		修改服务器配置文件
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#cp /var/tmp/openvpn-2.3.10/sample/sample-config-files/server.conf /etc/openvpn/
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#vi /etc/openvpn/server.conf
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		port 1194<span style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;</span><span style="box-sizing:border-box;margin:0px;padding:0px;"></span><span style="box-sizing:border-box;margin:0px;padding:0px;"></span>//<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">端口设为</span>1194
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		proto tcp<span style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;</span><span style="box-sizing:border-box;margin:0px;padding:0px;"></span><span style="box-sizing:border-box;margin:0px;padding:0px;"></span>//<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">协议设为</span>tcp
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		ca ca.crt<span style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;</span><span style="box-sizing:border-box;margin:0px;padding:0px;"></span><span style="box-sizing:border-box;margin:0px;padding:0px;"></span>//ca.crt<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">的路径，建议和</span>server.conf<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">在一个目录下</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		cert jhrdc.crt<span style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;</span><span style="box-sizing:border-box;margin:0px;padding:0px;"></span>//jhrdc.crt<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">的路径，建议和</span>server.conf<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">在一个目录下</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		key jhrdc.key<span style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;</span><span style="box-sizing:border-box;margin:0px;padding:0px;"></span>//jhrdc.key<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">的路径，建议和</span>server.conf<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">在一个目录下</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		server 10.8.0.0 255.255.255.0<span style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;</span><span style="box-sizing:border-box;margin:0px;padding:0px;"></span>//DHCP<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">服务器的</span>IP<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">段，缺省是</span>10.8.0.0
	</p>
	<p class="p5" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<span class="s2" style="box-sizing:border-box;margin:0px;padding:0px;">client-to-client<span style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;</span><span style="box-sizing:border-box;margin:0px;padding:0px;"></span><span style="box-sizing:border-box;margin:0px;padding:0px;"></span><span style="box-sizing:border-box;margin:0px;padding:0px;"></span><span style="box-sizing:border-box;margin:0px;padding:0px;"></span>//VPN</span>客户端之间允许互相访问，如不需要客户端之间互相访问，则可注释该配置
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		max-clients 10<span style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;</span><span style="box-sizing:border-box;margin:0px;padding:0px;"></span><span style="box-sizing:border-box;margin:0px;padding:0px;"></span><span style="box-sizing:border-box;margin:0px;padding:0px;"></span><span style="box-sizing:border-box;margin:0px;padding:0px;"></span>//<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">并发的客户端链接，可设为</span>10<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">个</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		user nobody<span style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;</span><span style="box-sizing:border-box;margin:0px;padding:0px;"></span><span style="box-sizing:border-box;margin:0px;padding:0px;"></span><span style="box-sizing:border-box;margin:0px;padding:0px;"></span><span style="box-sizing:border-box;margin:0px;padding:0px;"></span>//<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">服务启动时使用的系统用户，建议使用</span>nobody
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		group nobody<span style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;</span><span style="box-sizing:border-box;margin:0px;padding:0px;"></span><span style="box-sizing:border-box;margin:0px;padding:0px;"></span><span style="box-sizing:border-box;margin:0px;padding:0px;"></span><span style="box-sizing:border-box;margin:0px;padding:0px;"></span>//<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">服务启动时使用的系统用户组，建议使用</span>nobody
	</p>
	<p class="p2" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<br />
	</p>
	<p class="p5" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		五、启动<span class="s2" style="box-sizing:border-box;margin:0px;padding:0px;">openvpn</span>的服务器端
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#cd /etc/openvpn
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#openvpn —config /etc/openvpn/server.conf —daemon
	</p>
	<p class="p2" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<br />
	</p>
	<p class="p5" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		六、配置客户端
	</p>
	<p class="p6" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<span class="s3" style="box-sizing:border-box;margin:0px;padding:0px;">下载</span><span class="s4" style="box-sizing:border-box;margin:0px;padding:0px;">Windows</span><span class="s3" style="box-sizing:border-box;margin:0px;padding:0px;">客户端，下载链接为<a href="http://www.oberhumer.com/opensource/lzo/#download" target="_blank" style="box-sizing:border-box;background:transparent;color:#CA0C16;text-decoration-line:none;margin:0px;padding:0px;outline:0px;"><span class="s5" style="box-sizing:border-box;margin:0px;padding:0px;">https://openvpn.net/index.php/download/community-downloads.html</span></a></span><span class="s6" style="box-sizing:border-box;margin:0px;padding:0px;">，</span>
	</p>
	<p class="p8" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<br />
	</p>
	<p class="p9" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		安装后，将第三步所生成的证书文件和配置文件放在一个目录里，并修改客户端配置文件，然后启动该配置文件即大功告成。配置文件简要说明
	</p>
	<p class="p9" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		client
	</p>
	<p class="p9" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		proto tcp
	</p>
	<p class="p9" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		remote 111.111.111.111 1194&nbsp;&nbsp;<span style="box-sizing:border-box;margin:0px;padding:0px;"></span><span class="s9" style="box-sizing:border-box;margin:0px;padding:0px;">//VPN</span><span class="s3" style="box-sizing:border-box;margin:0px;padding:0px;">服务器的</span><span class="s9" style="box-sizing:border-box;margin:0px;padding:0px;">IP</span><span class="s3" style="box-sizing:border-box;margin:0px;padding:0px;">地址和端口号</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		ca /etc/openvpn/ca.crt<span style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;</span><span style="box-sizing:border-box;margin:0px;padding:0px;"></span><span style="box-sizing:border-box;margin:0px;padding:0px;"></span><span style="box-sizing:border-box;margin:0px;padding:0px;"></span><span style="box-sizing:border-box;margin:0px;padding:0px;"></span>//ca.crt<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">的路径，建议和</span>server.conf<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">在一个目录下</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		cert /etc/openvpn/testchannel1.crt<span style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;</span><span style="box-sizing:border-box;margin:0px;padding:0px;"></span>//testchannel1.crt<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">的路径，建议和</span>server.conf<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">在一个目录下</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		key /etc/openvpn/testchannel1.key<span style="box-sizing:border-box;margin:0px;padding:0px;">&nbsp;</span><span style="box-sizing:border-box;margin:0px;padding:0px;"></span>//testchannel1.key<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">的路径，建议和</span>server.conf<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">在一个目录下</span>
	</p>
	<p class="p2" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<br />
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		Please enter the following 'extra' attributes
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		to be sent with your certificate request
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		A challenge password&nbsp;<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">[]</span>:Jing7VPN
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		An optional company name&nbsp;<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">[]</span>:JingHang
	</p>
	<p class="p2" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<br />
	</p>
	<p class="p2" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<br />
	</p>
	<p class="p2" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<br />
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">七、将</span>openvpn<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">添加到启动脚本</span>/etc/rc.d/rc.local<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">里</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		CentOS 7<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">里面需要给</span>rc.local<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">加上可执行权限，</span>
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<span class="s1" style="box-sizing:border-box;margin:0px;padding:0px;">需要</span>ln -s /etc/rc.d/rc.local /etc/rc.local
	</p>
	<p class="p2" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<br />
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		=======
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#!/bin/sh
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		#
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		# This script will be executed *after* all the other init scripts.
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		# You can put your own initialization stuff in here if you don't
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		# want to do the full Sys V style init stuff.
	</p>
	<p class="p2" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<br />
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		touch /var/lock/subsys/local
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		/usr/local/sbin/openvpn --config /etc/openvpn/client.conf --daemon
	</p>
	<p class="p1" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		service iptables start
	</p>
	<p class="p2" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		<br />
	</p>
	<p class="p5" style="box-sizing:border-box;margin-top:0px;margin-bottom:0px;padding:0px;color:#454545;font-family:&quot;font-size:16px;white-space:normal;background-color:#FFFFFF;">
		自启动时，<span class="s2" style="box-sizing:border-box;margin:0px;padding:0px;">server.conf</span>里，证书的路径需要是绝对路径
	</p>
</p>