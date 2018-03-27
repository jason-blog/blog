<h2 style="margin:0px;padding:0px;font-family:simsun;white-space:normal;background-color:#F5F8FD;">
	安装GitLab出现ruby_block[supervise_redis_sleep] action run
</h2>
<br style="font-family:simsun;font-size:14px;white-space:normal;background-color:#F5F8FD;" />
<p style="margin-top:8px;margin-bottom:8px;padding:0px;color:#373737;font-stretch:normal;font-size:14px;font-family:&quot;line-height:2em;white-space:normal;background-color:#F5F8FD;">
	安装GitLab参照官网提供的步骤安装很简单。但在执行GitLab-ctl reconfigure时可能会出现<br />
ruby_block[supervise_redis_sleep] action run<br />
停止在哪，不动的情况。啥原因哪？<br />
我的GitLab是kvm的CentOS7虚拟机会不会是虚拟机的问题？排查半天都不是。<br />
最后参照官网提供的方法执行：<br />
手工执行exec /opt/GitLab/embedded/bin/runsvdir-start<br />
再执行GitLab-ctl start<br />
安装恢复正常，GitLab也能正常提供服务。
</p>
<p style="margin-top:8px;margin-bottom:8px;padding:0px;color:#373737;font-stretch:normal;font-size:14px;font-family:&quot;line-height:2em;white-space:normal;background-color:#F5F8FD;">
	<br />
但这样解决问题简直太恶心了。服务器重启后必须手工启动，这要是没人能连上服务器GitLab就不能提供服务了。<br />
再看看问题发现是和ruby有关系。<br />
死马当活马医，看看是不是gem安装源的问题哪。<br />
gem sources -r https://rubygems.org/<br />
gem sources -a http://ruby.taobao.org/<br />
再执行<br />
GitLab-ctl reconfigure
</p>
<p style="margin-top:8px;margin-bottom:8px;padding:0px;color:#373737;font-stretch:normal;font-size:14px;font-family:&quot;line-height:2em;white-space:normal;background-color:#F5F8FD;">
	不再卡在哪了。原来是这个原因换个安装源就解决问题了。
</p>