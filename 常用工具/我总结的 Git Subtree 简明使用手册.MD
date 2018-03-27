<h2 id="articleHeader8" style="box-sizing:border-box;font-family:-apple-system, &quot;font-weight:500;line-height:1.2;color:#333333;margin:1.5em 0px 0px;font-size:1.75em;border-bottom:1px solid #EEEEEE;padding-bottom:10px;white-space:normal;background-color:#FFFFFF;">
	我总结的 Git Subtree 简明使用手册
</h2>
<p style="box-sizing:border-box;margin-top:1.5em;margin-bottom:1.5em;color:#333333;font-family:-apple-system, &quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	假设，你要在各个项目里的<em style="box-sizing:border-box;">components/zenjs</em>这个目录对&nbsp;<em style="box-sizing:border-box;"><a href="http://github.com/youzan/zenjs.git" target="_blank" style="box-sizing:border-box;background:transparent;color:#009A61;text-decoration-line:none;outline:0px;">http://github.com/youzan/zenjs.git</a></em>&nbsp;这个项目做Subtree
</p>
<p style="box-sizing:border-box;margin-top:1.5em;margin-bottom:1.5em;color:#333333;font-family:-apple-system, &quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	1.首先必须确保各个项目已经添加zenjs 这个 remote（关于remote是什么可以看<a href="http://git-scm.com/docs/git-remote" target="_blank" style="box-sizing:border-box;background:transparent;color:#009A61;text-decoration-line:none;outline:0px;">这里</a>）:
</p>
<pre class="hljs awk" style="box-sizing:border-box;overflow:auto;font-family:&quot;font-size:0.93em;padding:1em;margin-bottom:1.5em;line-height:1.45;word-break:break-all;word-wrap:break-word;color:#333333;border:none;border-radius:4px;max-height:35em;position:relative;margin-top:0px !important;"><code class="shell" style="box-sizing:border-box;font-family:&quot;font-size:1em;padding:0px;color:inherit;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;border-radius:0px;white-space:initial;overflow-wrap:normal;word-break:break-word;">git remote add zenjs http:<span class="hljs-regexp" style="box-sizing:border-box;color:#009926;">//gi</span>thub.com<span class="hljs-regexp" style="box-sizing:border-box;color:#009926;">/youzan/</span>zenjs.git</code></pre>
<p style="box-sizing:border-box;margin-top:1.5em;margin-bottom:1.5em;color:#333333;font-family:-apple-system, &quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	2.将zenjs添加到各个项目里
</p>
<pre class="hljs mipsasm" style="box-sizing:border-box;overflow:auto;font-family:&quot;font-size:0.93em;padding:1em;margin-bottom:1.5em;line-height:1.45;word-break:break-all;word-wrap:break-word;color:#333333;border:none;border-radius:4px;max-height:35em;position:relative;margin-top:0px !important;"><code class="shell" style="box-sizing:border-box;font-family:&quot;font-size:1em;padding:0px;color:inherit;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;border-radius:0px;white-space:initial;overflow-wrap:normal;word-break:break-word;">git&nbsp;<span class="hljs-keyword" style="box-sizing:border-box;font-weight:bold;">subtree&nbsp;</span><span class="hljs-keyword" style="box-sizing:border-box;font-weight:bold;">add&nbsp;</span>--<span class="hljs-keyword" style="box-sizing:border-box;font-weight:bold;">prefix=components/zenjs&nbsp;</span>zenjs master</code></pre>
<p style="box-sizing:border-box;margin-top:1.5em;margin-bottom:1.5em;color:#333333;font-family:-apple-system, &quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	3.各项目更新zenjs代码的方法:
</p>
<pre class="hljs maxima" style="box-sizing:border-box;overflow:auto;font-family:&quot;font-size:0.93em;padding:1em;margin-bottom:1.5em;line-height:1.45;word-break:break-all;word-wrap:break-word;color:#333333;border:none;border-radius:4px;max-height:35em;position:relative;margin-top:0px !important;"><code class="shell" style="box-sizing:border-box;font-family:&quot;font-size:1em;padding:0px;color:inherit;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;border-radius:0px;white-space:initial;overflow-wrap:normal;word-break:break-word;">git subtree pull --<span class="hljs-built_in" style="box-sizing:border-box;color:#0086B3;">prefix</span>=<span class="hljs-built_in" style="box-sizing:border-box;color:#0086B3;">components</span>/zenjs zenjs master</code></pre>
<p style="box-sizing:border-box;margin-top:1.5em;margin-bottom:1.5em;color:#333333;font-family:-apple-system, &quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	4.各项目提交zenjs代码的方法:
</p>
<pre class="hljs maxima" style="box-sizing:border-box;overflow:auto;font-family:&quot;font-size:0.93em;padding:1em;margin-bottom:1.5em;line-height:1.45;word-break:break-all;word-wrap:break-word;color:#333333;border:none;border-radius:4px;max-height:35em;position:relative;margin-top:0px !important;"><code class="shell" style="box-sizing:border-box;font-family:&quot;font-size:1em;padding:0px;color:inherit;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;border-radius:0px;white-space:initial;overflow-wrap:normal;word-break:break-word;">git subtree&nbsp;<span class="hljs-built_in" style="box-sizing:border-box;color:#0086B3;">push</span>&nbsp;--<span class="hljs-built_in" style="box-sizing:border-box;color:#0086B3;">prefix</span>=<span class="hljs-built_in" style="box-sizing:border-box;color:#0086B3;">components</span>/zenjs zenjs hotfix/zenjs_xxxx</code></pre>
<p style="box-sizing:border-box;margin-top:1.5em;margin-bottom:1.5em;color:#333333;font-family:-apple-system, &quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	这会在远程的zenjs的仓库里生成一个叫 hotfix/zenjs_xxxx 的的分支，包含了你过去对components/zenjs 所有的更改记录
</p>
<p style="box-sizing:border-box;margin-top:1.5em;margin-bottom:1.5em;color:#333333;font-family:-apple-system, &quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	5.把hotfix/zenjs_xxx分支更新并合并到master并提交
</p>
<p style="box-sizing:border-box;margin-top:1.5em;margin-bottom:1.5em;color:#333333;font-family:-apple-system, &quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	这样其他工程就可以更新到你提交的代码了。
</p>
<blockquote style="box-sizing:border-box;padding:10px 20px;margin:1.5em 0px;font-size:14px;border-left:2px solid #009A61;background:#F6F6F6;color:#555555;font-family:-apple-system, &quot;white-space:normal;">
	<p style="box-sizing:border-box;margin-top:0px;margin-bottom:1.5em;">
		有人可能会问，只用master分支，不管版本，太有风险了。
	</p>
	<p style="box-sizing:border-box;margin-top:1.5em;margin-bottom:1.5em;">
		对的，正如我们前面说到的那样，subtree的方案适用的场景是：各个项目共用一个库，而这个库正在快速迭代更新的过程中。如果追求稳定，只需要给库拉出一个如v0.1.0这样的版本号命名的稳定分支，subtree只用这个分支即可。
	</p>
	<p style="box-sizing:border-box;margin-top:1.5em;margin-bottom:0px;">
		我们现在使用的方式就是：A项目经常会对zenjs做更新，所以A项目用subtree来双向同步；B项目只是使用，所以用bower用来按版本来更新代码。
	</p>
</blockquote>
<h2 id="articleHeader9" style="box-sizing:border-box;font-family:-apple-system, &quot;font-weight:500;line-height:1.2;color:#333333;margin:1.5em 0px 0px;font-size:1.75em;border-bottom:1px solid #EEEEEE;padding-bottom:10px;white-space:normal;background-color:#FFFFFF;">
	高阶功能
</h2>
<p style="box-sizing:border-box;margin-top:1.5em;margin-bottom:1.5em;color:#333333;font-family:-apple-system, &quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	重新split出一个新起点（这样，每次提交subtree的时候就不会从头遍历一遍了）
</p>
<pre class="hljs haxe" style="box-sizing:border-box;overflow:auto;font-family:&quot;font-size:0.93em;padding:1em;margin-bottom:1.5em;line-height:1.45;word-break:break-all;word-wrap:break-word;color:#333333;border:none;border-radius:4px;max-height:35em;position:relative;margin-top:0px !important;"><code class="shell" style="box-sizing:border-box;font-family:&quot;font-size:1em;padding:0px;color:inherit;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;border-radius:0px;white-space:inherit;overflow-wrap:normal;">git subtree split --rejoin --prefix=components/zenjs --branch <span class="hljs-keyword" style="box-sizing:border-box;font-weight:bold;">new</span><span class="hljs-type" style="box-sizing:border-box;color:#445588;font-weight:bold;">_zenjs</span> git push zenjs <span class="hljs-keyword" style="box-sizing:border-box;font-weight:bold;">new</span><span class="hljs-type" style="box-sizing:border-box;color:#445588;font-weight:bold;">_zenjs</span>:master</code></pre>