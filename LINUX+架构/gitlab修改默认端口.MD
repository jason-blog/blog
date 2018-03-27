<p>
	http://blog.csdn.net/arybd/article/details/54635295
</p>
<p>
	<br />
</p>
<p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		部署gitlab的时候，一启动，发现80和8080端口已经被占用，无奈，只得先将监听80端口的nginx和监听8080端口的jenkins停止。这会儿有空，琢磨一下如何修改gitlab的默认端口。
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		修改主要分为两部分，一部分是gitlab总的控制文件，一部分是子模块真实监听端口的修改。
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		当前我使用的是官方rpm 813版本。
	</p>
	<h2 id="gitlabrb修改" style="margin:0px;padding:0px;color:#555555;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		<a name="t0"></a><a name="t0"></a>gitlab.rb修改
	</h2>
	<ul style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		<li>
			配置文件在/opt/gitlab/etc/gitlab.rb。这个文件用于gitlab如何调用80和8080的服务等。
		</li>
	</ul>
<pre code_snippet_id="2142887" snippet_file_name="blog_20170120_1_5453288" class="prettyprint" name="code" style="white-space:nowrap;word-wrap:break-word;position:relative;overflow-y:hidden;overflow-x:auto;padding:5px 5px 5px 60px;border:1px solid rgba(128, 128, 128, 0.075);box-sizing:border-box;margin-top:0px;margin-bottom:1.1em;font-family:&quot;font-size:14px;line-height:1.45;word-break:break-all;color:#333333;border-radius:0px;widows:1;background-color:rgba(128, 128, 128, 0.047);"><code class="hljs vala has-numbering" style="display:block;padding:0px;background:transparent;color:inherit;box-sizing:border-box;font-family:&quot;white-space:pre;border-radius:0px;word-wrap:normal;"><span class="hljs-preprocessor" style="color:#444444;box-sizing:border-box;">## Advanced settings</span> unicorn[<span class="hljs-string" style="color:#008800;box-sizing:border-box;">'listen'</span>] = <span class="hljs-string" style="color:#008800;box-sizing:border-box;">'127.0.0.1'</span> unicorn[<span class="hljs-string" style="color:#008800;box-sizing:border-box;">'port'</span>] = <span class="hljs-number" style="color:#006666;box-sizing:border-box;">8082</span></code>
	<ul class="pre-numbering" style="box-sizing:border-box;position:absolute;width:50px;top:0px;left:0px;margin:0px;padding:6px 0px 40px;border-right:1px solid #DDDDDD;list-style:none;text-align:right;background-color:#EEEEEE;">
		
		<li style="box-sizing:border-box;padding:0px 5px;">
			1
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			2
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			3
		</li>

	</ul>

	<ul class="pre-numbering" style="box-sizing:border-box;position:absolute;width:50px;top:0px;left:0px;margin:0px;padding:6px 0px 40px;border-right:1px solid #DDDDDD;list-style:none;text-align:right;background-color:#EEEEEE;">
		
		<li style="box-sizing:border-box;padding:0px 5px;">
			1
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			2
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			3
		</li>

	</ul>
</pre>
<pre code_snippet_id="2142887" snippet_file_name="blog_20170120_2_6521893" class="prettyprint" name="code" style="white-space:nowrap;word-wrap:break-word;position:relative;overflow-y:hidden;overflow-x:auto;padding:5px 5px 5px 60px;border:1px solid rgba(128, 128, 128, 0.075);box-sizing:border-box;margin-top:0px;margin-bottom:1.1em;font-family:&quot;font-size:14px;line-height:1.45;word-break:break-all;color:#333333;border-radius:0px;widows:1;background-color:rgba(128, 128, 128, 0.047);"><code class="hljs actionscript has-numbering" style="display:block;padding:0px;background:transparent;color:inherit;box-sizing:border-box;font-family:&quot;white-space:pre;border-radius:0px;word-wrap:normal;">nginx[<span class="hljs-string" style="color:#008800;box-sizing:border-box;">'listen_addresses'</span>] = [<span class="hljs-string" style="color:#008800;box-sizing:border-box;">'*'</span>]
nginx[<span class="hljs-string" style="color:#008800;box-sizing:border-box;">'listen_port'</span>] = <span class="hljs-number" style="color:#006666;box-sizing:border-box;">82</span> # <span class="hljs-keyword" style="color:#000088;box-sizing:border-box;">override</span> only <span class="hljs-keyword" style="color:#000088;box-sizing:border-box;">if</span> you <span class="hljs-keyword" style="color:#000088;box-sizing:border-box;">use</span> a reverse proxy: https:<span class="hljs-comment" style="color:#880000;box-sizing:border-box;">//gitlab.com/gitlab-org/omnibus-gitlab/blob/master/doc/settings/nginx.md#setting-the-nginx-listen-port</span></code>
	<ul class="pre-numbering" style="box-sizing:border-box;position:absolute;width:50px;top:0px;left:0px;margin:0px;padding:6px 0px 40px;border-right:1px solid #DDDDDD;list-style:none;text-align:right;background-color:#EEEEEE;">
		
		<li style="box-sizing:border-box;padding:0px 5px;">
			1
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			2
		</li>

	</ul>

	<ul class="pre-numbering" style="box-sizing:border-box;position:absolute;width:50px;top:0px;left:0px;margin:0px;padding:6px 0px 40px;border-right:1px solid #DDDDDD;list-style:none;text-align:right;background-color:#EEEEEE;">
		
		<li style="box-sizing:border-box;padding:0px 5px;">
			1
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			2
		</li>

	</ul>
</pre>
	<h2 id="gitlab-rails修改" style="margin:0px;padding:0px;color:#555555;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		<a name="t1"></a><a name="t1"></a>gitlab-rails修改
	</h2>
	<ul style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		<li>
			配置文件/var/opt/gitlab/gitlab-rails/etc/unicorn.rb
		</li>
	</ul>
<pre code_snippet_id="2142887" snippet_file_name="blog_20170120_3_523082" class="prettyprint" name="code" style="white-space:nowrap;word-wrap:break-word;position:relative;overflow-y:hidden;overflow-x:auto;padding:5px 5px 5px 60px;border:1px solid rgba(128, 128, 128, 0.075);box-sizing:border-box;margin-top:0px;margin-bottom:1.1em;font-family:&quot;font-size:14px;line-height:1.45;word-break:break-all;color:#333333;border-radius:0px;widows:1;background-color:rgba(128, 128, 128, 0.047);"><code class="hljs vbscript has-numbering" style="display:block;padding:0px;background:transparent;color:inherit;box-sizing:border-box;font-family:&quot;white-space:pre;border-radius:0px;word-wrap:normal;"># What ports/sockets <span class="hljs-keyword" style="color:#000088;box-sizing:border-box;">to</span> listen <span class="hljs-keyword" style="color:#000088;box-sizing:border-box;">on</span>, <span class="hljs-keyword" style="color:#000088;box-sizing:border-box;">and</span> what options <span class="hljs-keyword" style="color:#000088;box-sizing:border-box;">for</span> them.
#listen <span class="hljs-string" style="color:#008800;box-sizing:border-box;">"127.0.0.1:8080"</span>, :tcp_nopush =&gt; <span class="hljs-literal" style="color:#006666;box-sizing:border-box;">true</span> listen <span class="hljs-string" style="color:#008800;box-sizing:border-box;">"127.0.0.1:8082"</span>, :tcp_nopush =&gt; <span class="hljs-literal" style="color:#006666;box-sizing:border-box;">true</span> listen <span class="hljs-string" style="color:#008800;box-sizing:border-box;">"/var/opt/gitlab/gitlab-rails/sockets/gitlab.socket"</span>, :backlog =&gt; <span class="hljs-number" style="color:#006666;box-sizing:border-box;">1024</span> </code>
	<ul class="pre-numbering" style="box-sizing:border-box;position:absolute;width:50px;top:0px;left:0px;margin:0px;padding:6px 0px 40px;border-right:1px solid #DDDDDD;list-style:none;text-align:right;background-color:#EEEEEE;">
		
		<li style="box-sizing:border-box;padding:0px 5px;">
			1
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			2
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			3
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			4
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			5
		</li>

	</ul>

	<ul class="pre-numbering" style="box-sizing:border-box;position:absolute;width:50px;top:0px;left:0px;margin:0px;padding:6px 0px 40px;border-right:1px solid #DDDDDD;list-style:none;text-align:right;background-color:#EEEEEE;">
		
		<li style="box-sizing:border-box;padding:0px 5px;">
			1
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			2
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			3
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			4
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			5
		</li>

	</ul>
</pre>
	<h2 id="gitlab-nginx-修改" style="margin:0px;padding:0px;color:#555555;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		<a name="t2"></a><a name="t2"></a>gitlab nginx 修改
	</h2>
	<ul style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		<li>
			配置文件 /var/opt/gitlab/nginx/conf/gitlab-http.conf。这个文件是gitlab内置的nginx的配置文件，里面可以影响到nginx真实监听端口号。
		</li>
	</ul>
<pre code_snippet_id="2142887" snippet_file_name="blog_20170120_4_304931" class="prettyprint" name="code" style="white-space:nowrap;word-wrap:break-word;position:relative;overflow-y:hidden;overflow-x:auto;padding:5px 5px 5px 60px;border:1px solid rgba(128, 128, 128, 0.075);box-sizing:border-box;margin-top:0px;margin-bottom:1.1em;font-family:&quot;font-size:14px;line-height:1.45;word-break:break-all;color:#333333;border-radius:0px;widows:1;background-color:rgba(128, 128, 128, 0.047);"><code class="hljs sql has-numbering" style="display:block;padding:0px;background:transparent;color:inherit;box-sizing:border-box;font-family:&quot;white-space:pre;border-radius:0px;word-wrap:normal;">server {
  listen *:82;

  server_name gitlab.123.123.cn;
  server_tokens off; ## Don't <span class="hljs-operator" style="box-sizing:border-box;"><span class="hljs-keyword" style="color:#000088;box-sizing:border-box;">show</span> the nginx version <span class="hljs-keyword" style="color:#000088;box-sizing:border-box;">number</span>, a security best practice</span></code>
	<ul class="pre-numbering" style="box-sizing:border-box;position:absolute;width:50px;top:0px;left:0px;margin:0px;padding:6px 0px 40px;border-right:1px solid #DDDDDD;list-style:none;text-align:right;background-color:#EEEEEE;">
		
		<li style="box-sizing:border-box;padding:0px 5px;">
			1
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			2
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			3
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			4
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			5
		</li>

	</ul>

	<ul class="pre-numbering" style="box-sizing:border-box;position:absolute;width:50px;top:0px;left:0px;margin:0px;padding:6px 0px 40px;border-right:1px solid #DDDDDD;list-style:none;text-align:right;background-color:#EEEEEE;">
		
		<li style="box-sizing:border-box;padding:0px 5px;">
			1
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			2
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			3
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			4
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			5
		</li>

	</ul>
</pre>
	<ul style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		<li>
			修改完成后，重启下，就可以放82端口的gitlab了。
		</li>
	</ul>
<pre code_snippet_id="2142887" snippet_file_name="blog_20170120_5_2910679" class="prettyprint" name="code" style="white-space:nowrap;word-wrap:break-word;position:relative;overflow-y:hidden;overflow-x:auto;padding:5px 5px 5px 60px;border:1px solid rgba(128, 128, 128, 0.075);box-sizing:border-box;margin-top:0px;margin-bottom:1.1em;font-family:&quot;font-size:14px;line-height:1.45;word-break:break-all;color:#333333;border-radius:0px;widows:1;background-color:rgba(128, 128, 128, 0.047);"><code class="hljs lasso has-numbering" style="display:block;padding:0px;background:transparent;color:inherit;box-sizing:border-box;font-family:&quot;white-space:pre;border-radius:0px;word-wrap:normal;">gitlab<span class="hljs-attribute" style="box-sizing:border-box;">-ctl</span> restart</code>
	<ul class="pre-numbering" style="box-sizing:border-box;position:absolute;width:50px;top:0px;left:0px;margin:0px;padding:6px 0px 40px;border-right:1px solid #DDDDDD;list-style:none;text-align:right;background-color:#EEEEEE;">
		
		<li style="box-sizing:border-box;padding:0px 5px;">
			1
		</li>

	</ul>

	<ul class="pre-numbering" style="box-sizing:border-box;position:absolute;width:50px;top:0px;left:0px;margin:0px;padding:6px 0px 40px;border-right:1px solid #DDDDDD;list-style:none;text-align:right;background-color:#EEEEEE;">
		
		<li style="box-sizing:border-box;padding:0px 5px;">
			1
		</li>

	</ul>
</pre>
	<h2 id="os-nginx修改" style="margin:0px;padding:0px;color:#555555;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		<a name="t3"></a><a name="t3"></a>OS nginx修改
	</h2>
	<ul style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		<li>
			如果还是想从80端口访问gitlab，我们可以用监听在80端口的nginx做一个反向代理。service nginx restart后可以正常访问。
		</li>
	</ul>
<pre code_snippet_id="2142887" snippet_file_name="blog_20170120_6_7468274" class="prettyprint" name="code" style="white-space:nowrap;word-wrap:break-word;position:relative;overflow-y:hidden;overflow-x:auto;padding:5px 5px 5px 60px;border:1px solid rgba(128, 128, 128, 0.075);box-sizing:border-box;margin-top:0px;margin-bottom:1.1em;font-family:&quot;font-size:14px;line-height:1.45;word-break:break-all;color:#333333;border-radius:0px;widows:1;background-color:rgba(128, 128, 128, 0.047);"><code class="hljs lasso has-numbering" style="display:block;padding:0px;background:transparent;color:inherit;box-sizing:border-box;font-family:&quot;white-space:pre;border-radius:0px;word-wrap:normal;">server {
    listen <span class="hljs-number" style="color:#006666;box-sizing:border-box;">80</span>;
    server_name gitlab<span class="hljs-number" style="color:#006666;box-sizing:border-box;">.123</span><span class="hljs-number" style="color:#006666;box-sizing:border-box;">.123</span><span class="hljs-built_in" style="color:#660066;box-sizing:border-box;">.</span><span class="hljs-literal" style="color:#006666;box-sizing:border-box;">cn</span>;

    location <span class="hljs-subst" style="color:#000000;box-sizing:border-box;">/</span> { <span class="hljs-variable" style="color:#660066;box-sizing:border-box;">#rewrite</span> ^(<span class="hljs-built_in" style="color:#660066;box-sizing:border-box;">.</span><span class="hljs-subst" style="color:#000000;box-sizing:border-box;">*</span>) http:<span class="hljs-comment" style="color:#880000;box-sizing:border-box;">//127.0.0.1:8082;</span> proxy_pass http:<span class="hljs-comment" style="color:#880000;box-sizing:border-box;">//127.0.0.1:8082;</span> }
}</code>
	<ul class="pre-numbering" style="box-sizing:border-box;position:absolute;width:50px;top:0px;left:0px;margin:0px;padding:6px 0px 40px;border-right:1px solid #DDDDDD;list-style:none;text-align:right;background-color:#EEEEEE;">
		
		<li style="box-sizing:border-box;padding:0px 5px;">
			1
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			2
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			3
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			4
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			5
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			6
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			7
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			8
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			9
		</li>

	</ul>

	<ul class="pre-numbering" style="box-sizing:border-box;position:absolute;width:50px;top:0px;left:0px;margin:0px;padding:6px 0px 40px;border-right:1px solid #DDDDDD;list-style:none;text-align:right;background-color:#EEEEEE;">
		
		<li style="box-sizing:border-box;padding:0px 5px;">
			1
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			2
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			3
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			4
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			5
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			6
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			7
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			8
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			9
		</li>

	</ul>
</pre>
	<h2 id="giltab-shell修改" style="margin:0px;padding:0px;color:#555555;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
		<a name="t4"></a><a name="t4"></a>giltab-shell修改
	</h2>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		后来在提交的时候，出现了错误：
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		<img title="" alt="这里写图片描述" src="http://img.blog.csdn.net/20161031103029328" style="border-width:initial;border-style:none;max-width:602px;max-height:100%;height:auto;" />
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		找了关于8080端口的相关信息，最后发现
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		配置文件：/var/opt/gitlab/gitlab-shell
	</p>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		修改成
	</p>
<pre code_snippet_id="2142887" snippet_file_name="blog_20170120_7_5613921" class="prettyprint" name="code" style="white-space:nowrap;word-wrap:break-word;position:relative;overflow-y:hidden;overflow-x:auto;padding:5px 5px 5px 60px;border:1px solid rgba(128, 128, 128, 0.075);box-sizing:border-box;margin-top:0px;margin-bottom:1.1em;font-family:&quot;font-size:14px;line-height:1.45;word-break:break-all;color:#333333;border-radius:0px;widows:1;background-color:rgba(128, 128, 128, 0.047);"><code class="hljs avrasm has-numbering" style="display:block;padding:0px;background:transparent;color:inherit;box-sizing:border-box;font-family:&quot;white-space:pre;border-radius:0px;word-wrap:normal;"><span class="hljs-preprocessor" style="color:#444444;box-sizing:border-box;"># GitLab user. git by default</span> <span class="hljs-label" style="box-sizing:border-box;">user:</span> git <span class="hljs-preprocessor" style="color:#444444;box-sizing:border-box;"># Url to gitlab instance. Used for api calls. Should end with a slash.</span> <span class="hljs-preprocessor" style="color:#444444;box-sizing:border-box;">#gitlab_url: "http://127.0.0.1:8080"</span> <span class="hljs-label" style="box-sizing:border-box;">gitlab_url:</span> <span class="hljs-string" style="color:#008800;box-sizing:border-box;">"http://127.0.0.1:82"</span> <span class="hljs-preprocessor" style="color:#444444;box-sizing:border-box;">## 关键是这个地方，因为82是gitlab nginx端口，不过上面的端口干嘛是8080来，8080应该是unicorn的监听端口。</span> <span class="hljs-label" style="box-sizing:border-box;">http_settings:</span></code>
	<ul class="pre-numbering" style="box-sizing:border-box;position:absolute;width:50px;top:0px;left:0px;margin:0px;padding:6px 0px 40px;border-right:1px solid #DDDDDD;list-style:none;text-align:right;background-color:#EEEEEE;">
		
		<li style="box-sizing:border-box;padding:0px 5px;">
			1
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			2
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			3
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			4
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			5
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			6
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			7
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			8
		</li>

	</ul>

	<ul class="pre-numbering" style="box-sizing:border-box;position:absolute;width:50px;top:0px;left:0px;margin:0px;padding:6px 0px 40px;border-right:1px solid #DDDDDD;list-style:none;text-align:right;background-color:#EEEEEE;">
		
		<li style="box-sizing:border-box;padding:0px 5px;">
			1
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			2
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			3
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			4
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			5
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			6
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			7
		</li>

		<li style="box-sizing:border-box;padding:0px 5px;">
			8
		</li>

	</ul>
</pre>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		<img title="" alt="这里写图片描述" src="http://img.blog.csdn.net/20161031103049398" style="border-width:initial;border-style:none;max-width:602px;max-height:100%;height:auto;" />
	</p>
	<ul style="color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		<li>
			果然，修改成8082端口，也是可以的哦。
		</li>
	</ul>
	<p style="margin-top:0px;margin-bottom:0px;padding:0px;color:#555555;font-family:&quot;font-size:15px;white-space:normal;background-color:#FFFFFF;">
		<img title="" alt="这里写图片描述" src="http://img.blog.csdn.net/20161031103401824" style="border-width:initial;border-style:none;max-width:602px;max-height:100%;height:auto;" />
	</p>
</p>