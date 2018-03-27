<p>
	http://www.cnblogs.com/liwanggui/archive/2016/06/28/5624147.html
</p>
<p>
	<div id="cnblogs_post_body" class="cnblogs-markdown" style="margin:0px 0px 20px;padding:0px;word-break:break-word;">
		<h1 id="svn-常用操作命令" style="margin:10px 0px;padding:0px;font-size:28px;line-height:1.5;">
			svn 常用操作命令
		</h1>
		<h2 id="检出" style="margin:10px 0px;padding:0px;font-size:21px;line-height:1.5;">
			检出
		</h2>
<pre style="margin-top:10px;margin-bottom:10px;padding:0px;white-space:pre-wrap;word-wrap:break-word;"><code class="hljs nginx" style="margin:auto;vertical-align:middle;display:block;background:#FFFFFF;height:auto;overflow-x:auto;padding:5px !important;line-height:1.5 !important;font-family:&quot;border:1px solid #CCCCCC !important;border-radius:3px !important;"><span class="hljs-attribute" style="margin:0px;padding:0px;color:#A31515;">svn</span> checkout  http://路径(目录或文件的全路径)　[本地目录全路径] --username　用户名
svn  checkout  svn://路径(目录或文件的全路径)　[本地目录全路径]  --username　用户名 <span class="hljs-comment" style="margin:0px;padding:0px;color:green;"># 例子：</span> svn co svn://localhost/测试工具 /home/testtools --username wzhnsc
svn co http://localhost/test/testapp --username wzhnsc
svn checkout svn://localhost/测试工具 /home/testtools --username wzhnsc
svn checkouthttp://localhost/test/testapp --username wzhnsc</code></pre>
		<blockquote style="margin:10px 0px;padding:5px 10px;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;border:2px solid #EFEFEF;line-height:1.6;color:#333333;">
			<p style="margin:10px auto;padding:0px;">
				注：如果不带--password 参数传输密码的话，会提示输入密码，建议不要用明文的--password 选项。<br style="margin:0px;padding:0px;" />
其中 username 与 password前是两个短线，不是一个。<br style="margin:0px;padding:0px;" />
不指定本地目录全路径，则检出到当前目录下。
			</p>
		</blockquote>
		<h2 id="导出导出一个干净的不带.svn文件夹的目录树" style="margin:10px 0px;padding:0px;font-size:21px;line-height:1.5;">
			导出(导出一个干净的不带.svn文件夹的目录树)
		</h2>
<pre style="margin-top:10px;margin-bottom:10px;padding:0px;white-space:pre-wrap;word-wrap:break-word;"><code class="hljs cpp" style="margin:auto;vertical-align:middle;display:block;background:#FFFFFF;height:auto;overflow-x:auto;padding:5px !important;line-height:1.5 !important;font-family:&quot;border:1px solid #CCCCCC !important;border-radius:3px !important;">svn <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">export</span> [-r 版本号]  http:<span class="hljs-comment" style="margin:0px;padding:0px;color:green;">//路径(目录或文件的全路径) [本地目录全路径]　--username　用户名</span> svn <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">export</span> [-r 版本号]  svn:<span class="hljs-comment" style="margin:0px;padding:0px;color:green;">//路径(目录或文件的全路径) [本地目录全路径]　--username　用户名</span> svn <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">export</span> 本地检出的(即带有.svn文件夹的)目录全路径  要导出的本地目录全路径

例子：
svn <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">export</span> svn:<span class="hljs-comment" style="margin:0px;padding:0px;color:green;">//localhost/测试工具 /home/testtools --username wzhnsc</span> svn <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">export</span> svn:<span class="hljs-comment" style="margin:0px;padding:0px;color:green;">//localhost/test/testapp --username wzhnsc</span> svn <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">export</span> /home/testapp /home/testtools</code></pre>
		<blockquote style="margin:10px 0px;padding:5px 10px;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;border:2px solid #EFEFEF;line-height:1.6;color:#333333;">
			<p style="margin:10px auto;padding:0px;">
				注：第一种从版本库导出干净工作目录树的形式是指定URL，<br style="margin:0px;padding:0px;" />
如果指定了修订版本号，会导出相应的版本，<br style="margin:0px;padding:0px;" />
如果没有指定修订版本，则会导出最新的，导出到指定位置。<br style="margin:0px;padding:0px;" />
如果省略 本地目录全路径，URL的最后一部分会作为本地目录的名字。<br style="margin:0px;padding:0px;" />
第二种形式是指定 本地检出的目录全路径 到 要导出的本地目录全路径，所有的本地修改将会保留，<br style="margin:0px;padding:0px;" />
但是不在版本控制下(即没提交的新文件，因为.svn文件夹里没有与之相关的信息记录)的文件不会拷贝。
			</p>
		</blockquote>
		<h2 id="添加新文件" style="margin:10px 0px;padding:0px;font-size:21px;line-height:1.5;">
			添加新文件
		</h2>
<pre style="margin-top:10px;margin-bottom:10px;padding:0px;white-space:pre-wrap;word-wrap:break-word;"><code class="hljs sql" style="margin:auto;vertical-align:middle;display:block;background:#FFFFFF;height:auto;overflow-x:auto;padding:5px !important;line-height:1.5 !important;font-family:&quot;border:1px solid #CCCCCC !important;border-radius:3px !important;">svn　add　文件名
注：告诉SVN服务器要添加文件了，还要用svn commint -m真实的上传上去！
例子：
svn add test.php ＜－ 添加test.php 
svn <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">commit</span> -<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">m</span> “添加我的测试用<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">test</span>.php“ <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">test</span>.php
svn <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">add</span> *.php ＜－ 添加当前目录下所有的php文件
svn <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">commit</span> -<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">m</span> “添加我的测试用全部php文件“ *.php</code></pre>
		<h2 id="提交" style="margin:10px 0px;padding:0px;font-size:21px;line-height:1.5;">
			提交
		</h2>
<pre style="margin-top:10px;margin-bottom:10px;padding:0px;white-space:pre-wrap;word-wrap:break-word;"><code class="hljs sql" style="margin:auto;vertical-align:middle;display:block;background:#FFFFFF;height:auto;overflow-x:auto;padding:5px !important;line-height:1.5 !important;font-family:&quot;border:1px solid #CCCCCC !important;border-radius:3px !important;">svn <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">commit</span> -<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">m</span> “提交备注信息文本“　[-<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">N</span>]　[<span class="hljs-comment" style="margin:0px;padding:0px;color:green;">--no-unlock]　文件名</span> svn　ci　-<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">m</span> “提交备注信息文本“　[-<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">N</span>]　[<span class="hljs-comment" style="margin:0px;padding:0px;color:green;">--no-unlock]　文件名</span> 必须带上-<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">m</span>参数，参数可以为空，但是必须写上-<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">m</span> 例子：
svn <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">commit</span> -<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">m</span> “提交当前目录下的全部在版本控制下的文件“ * ＜－ 注意这个*表示全部文件
svn <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">commit</span> -<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">m</span> “提交我的测试用<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">test</span>.php“ <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">test</span>.php
svn <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">commit</span> -<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">m</span> “提交我的测试用<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">test</span>.php“ -<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">N</span> <span class="hljs-comment" style="margin:0px;padding:0px;color:green;">--no-unlock test.php ＜－ 保持锁就用–no-unlock开关</span> svn ci -<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">m</span> “提交当前目录下的全部在版本控制下的文件“ * ＜－ 注意这个*表示全部文件
svn ci -<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">m</span> “提交我的测试用<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">test</span>.php“ <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">test</span>.php
svn ci -<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">m</span> “提交我的测试用<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">test</span>.php“ -<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">N</span> <span class="hljs-comment" style="margin:0px;padding:0px;color:green;">--no-unlock test.php ＜－ 保持锁就用–no-unlock开关</span></code></pre>
		<h2 id="更新文件" style="margin:10px 0px;padding:0px;font-size:21px;line-height:1.5;">
			更新文件
		</h2>
<pre style="margin-top:10px;margin-bottom:10px;padding:0px;white-space:pre-wrap;word-wrap:break-word;"><code class="hljs sql" style="margin:auto;vertical-align:middle;display:block;background:#FFFFFF;height:auto;overflow-x:auto;padding:5px !important;line-height:1.5 !important;font-family:&quot;border:1px solid #CCCCCC !important;border-radius:3px !important;">svn <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">update</span> svn <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">update</span> -r　修正版本　文件名
svn <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">update</span> 文件名
例子：
svn <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">update</span> ＜－ 后面没有目录，默认将当前目录以及子目录下的所有文件都更新到最新版本
svn <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">update</span> -r <span class="hljs-number" style="margin:0px;padding:0px;">200</span> <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">test</span>.cpp ＜－ 将版本库中的文件 <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">test</span>.cpp 还原到修正版本（revision）<span class="hljs-number" style="margin:0px;padding:0px;">200</span> svn <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">update</span> <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">test</span>.php ＜－ 更新与版本库同步。
　　　　　　　　　　　 提交的时候提示过期冲突，需要先 <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">update</span> 修改文件，
　　　　　　　　　　　 然后清除svn resolved，最后再提交<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">commit</span>。</code></pre>
		<h2 id="删除文件" style="margin:10px 0px;padding:0px;font-size:21px;line-height:1.5;">
			删除文件
		</h2>
<pre style="margin-top:10px;margin-bottom:10px;padding:0px;white-space:pre-wrap;word-wrap:break-word;"><code class="hljs sql" style="margin:auto;vertical-align:middle;display:block;background:#FFFFFF;height:auto;overflow-x:auto;padding:5px !important;line-height:1.5 !important;font-family:&quot;border:1px solid #CCCCCC !important;border-radius:3px !important;">svn <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">delete</span> svn://路径(目录或文件的全路径) -<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">m</span> “删除备注信息文本”
推荐如下操作：
svn <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">delete</span> 文件名 
svn　ci　-<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">m</span> “删除备注信息文本”
例子：
svn <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">delete</span> svn://localhost/testapp/<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">test</span>.php -<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">m</span> “删除测试文件<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">test</span>.php”
推荐如下操作：
svn <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">delete</span> <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">test</span>.php 
svn ci -<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">m</span> “删除测试文件<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">test</span>.php”</code></pre>
		<h2 id="加锁解锁" style="margin:10px 0px;padding:0px;font-size:21px;line-height:1.5;">
			加锁/解锁
		</h2>
<pre style="margin-top:10px;margin-bottom:10px;padding:0px;white-space:pre-wrap;word-wrap:break-word;"><code class="hljs sql" style="margin:auto;vertical-align:middle;display:block;background:#FFFFFF;height:auto;overflow-x:auto;padding:5px !important;line-height:1.5 !important;font-family:&quot;border:1px solid #CCCCCC !important;border-radius:3px !important;">svn <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">lock</span> -<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">m</span> “加锁备注信息文本“　[<span class="hljs-comment" style="margin:0px;padding:0px;color:green;">--force]　文件名 </span> svn <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">unlock</span> 文件名
例子：
svn <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">lock</span> -<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">m</span> “锁信测试用<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">test</span>.php文件“ <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">test</span>.php 
svn <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">unlock</span> <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">test</span>.php</code></pre>
		<h2 id="比较差异" style="margin:10px 0px;padding:0px;font-size:21px;line-height:1.5;">
			比较差异
		</h2>
<pre style="margin-top:10px;margin-bottom:10px;padding:0px;white-space:pre-wrap;word-wrap:break-word;"><code class="hljs css" style="margin:auto;vertical-align:middle;display:block;background:#FFFFFF;height:auto;overflow-x:auto;padding:5px !important;line-height:1.5 !important;font-family:&quot;border:1px solid #CCCCCC !important;border-radius:3px !important;"><span class="hljs-selector-tag" style="margin:0px;padding:0px;color:#0000FF;">svn</span> <span class="hljs-selector-tag" style="margin:0px;padding:0px;color:#0000FF;">diff</span> 文件名 <span class="hljs-selector-tag" style="margin:0px;padding:0px;color:#0000FF;">svn</span> <span class="hljs-selector-tag" style="margin:0px;padding:0px;color:#0000FF;">diff</span> <span class="hljs-selector-tag" style="margin:0px;padding:0px;color:#0000FF;">-r</span> 修正版本号<span class="hljs-selector-tag" style="margin:0px;padding:0px;color:#0000FF;">m</span>:修正版本号<span class="hljs-selector-tag" style="margin:0px;padding:0px;color:#0000FF;">n</span> 文件名
例子： <span class="hljs-selector-tag" style="margin:0px;padding:0px;color:#0000FF;">svn</span> <span class="hljs-selector-tag" style="margin:0px;padding:0px;color:#0000FF;">diff</span> <span class="hljs-selector-tag" style="margin:0px;padding:0px;color:#0000FF;">test</span><span class="hljs-selector-class" style="margin:0px;padding:0px;">.php</span>＜－ 将修改的文件与基础版本比较 <span class="hljs-selector-tag" style="margin:0px;padding:0px;color:#0000FF;">svn</span> <span class="hljs-selector-tag" style="margin:0px;padding:0px;color:#0000FF;">diff</span> <span class="hljs-selector-tag" style="margin:0px;padding:0px;color:#0000FF;">-r</span> 200<span class="hljs-selector-pseudo" style="margin:0px;padding:0px;color:#2B91AF;">:201</span> <span class="hljs-selector-tag" style="margin:0px;padding:0px;color:#0000FF;">test</span><span class="hljs-selector-class" style="margin:0px;padding:0px;">.php</span>＜－ 对 修正版本号200 和 修正版本号201 比较差异</code></pre>
		<h2 id="查看文件或者目录状态" style="margin:10px 0px;padding:0px;font-size:21px;line-height:1.5;">
			查看文件或者目录状态
		</h2>
<pre style="margin-top:10px;margin-bottom:10px;padding:0px;white-space:pre-wrap;word-wrap:break-word;"><code class="hljs fortran" style="margin:auto;vertical-align:middle;display:block;background:#FFFFFF;height:auto;overflow-x:auto;padding:5px !important;line-height:1.5 !important;font-family:&quot;border:1px solid #CCCCCC !important;border-radius:3px !important;">svn st 目录路径/名
svn <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">status</span> 目录路径/名＜－ 目录下的文件和子目录的状态，正常状态不显示 
　　　　　　　　　　　　　【?：不在svn的控制中；  M：内容被修改；C：发生冲突；
　　　　　　　　　　　　　　A：预定加入到版本库；K：被锁定】 
svn  -v 目录路径/名
svn <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">status</span> -v 目录路径/名＜－ 显示文件和子目录状态
　　　　　　　　　　　　　　【第一列保持相同，第二列显示工作版本号，
　　　　　　　　　　　　　　 第三和第四列显示最后一次修改的版本号和修改人】 </code></pre>
		<blockquote style="margin:10px 0px;padding:5px 10px;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;border:2px solid #EFEFEF;line-height:1.6;color:#333333;">
			<p style="margin:10px auto;padding:0px;">
				注：svn status、svn diff和 svn revert这三条命令在没有网络的情况下也可以执行的，<br style="margin:0px;padding:0px;" />
原因是svn在本地的.svn中保留了本地版本的原始拷贝。
			</p>
		</blockquote>
		<h2 id="查看日志" style="margin:10px 0px;padding:0px;font-size:21px;line-height:1.5;">
			查看日志
		</h2>
<pre style="margin-top:10px;margin-bottom:10px;padding:0px;white-space:pre-wrap;word-wrap:break-word;"><code class="hljs cpp" style="margin:auto;vertical-align:middle;display:block;background:#FFFFFF;height:auto;overflow-x:auto;padding:5px !important;line-height:1.5 !important;font-family:&quot;border:1px solid #CCCCCC !important;border-radius:3px !important;">svn <span class="hljs-built_in" style="margin:0px;padding:0px;color:#0000FF;">log</span> 文件名
例子：
svn <span class="hljs-built_in" style="margin:0px;padding:0px;color:#0000FF;">log</span> test.php＜－ 显示这个文件的所有修改记录，及其版本号的变化 </code></pre>
		<h2 id="查看文件详细信息" style="margin:10px 0px;padding:0px;font-size:21px;line-height:1.5;">
			查看文件详细信息
		</h2>
<pre style="margin-top:10px;margin-bottom:10px;padding:0px;white-space:pre-wrap;word-wrap:break-word;"><code class="hljs nginx" style="margin:auto;vertical-align:middle;display:block;background:#FFFFFF;height:auto;overflow-x:auto;padding:5px !important;line-height:1.5 !important;font-family:&quot;border:1px solid #CCCCCC !important;border-radius:3px !important;"><span class="hljs-attribute" style="margin:0px;padding:0px;color:#A31515;">svn</span> <span class="hljs-literal" style="margin:0px;padding:0px;color:#A31515;">info</span> 文件名
例子：
svn <span class="hljs-literal" style="margin:0px;padding:0px;color:#A31515;">info</span> test.php</code></pre>
		<h2 id="svn-帮助" style="margin:10px 0px;padding:0px;font-size:21px;line-height:1.5;">
			SVN 帮助
		</h2>
<pre style="margin-top:10px;margin-bottom:10px;padding:0px;white-space:pre-wrap;word-wrap:break-word;"><code class="hljs dos" style="margin:auto;vertical-align:middle;display:block;background:#FFFFFF;height:auto;overflow-x:auto;padding:5px !important;line-height:1.5 !important;font-family:&quot;border:1px solid #CCCCCC !important;border-radius:3px !important;">svn <span class="hljs-built_in" style="margin:0px;padding:0px;color:#0000FF;">help</span> ＜－ 全部功能选项
svn <span class="hljs-built_in" style="margin:0px;padding:0px;color:#0000FF;">help</span> ci ＜－ 具体功能的说明</code></pre>
		<h2 id="查看版本库下的文件和目录列表" style="margin:10px 0px;padding:0px;font-size:21px;line-height:1.5;">
			查看版本库下的文件和目录列表
		</h2>
<pre style="margin-top:10px;margin-bottom:10px;padding:0px;white-space:pre-wrap;word-wrap:break-word;"><code class="hljs groovy" style="margin:auto;vertical-align:middle;display:block;background:#FFFFFF;height:auto;overflow-x:auto;padding:5px !important;line-height:1.5 !important;font-family:&quot;border:1px solid #CCCCCC !important;border-radius:3px !important;">svn　list <span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">svn:</span><span class="hljs-comment" style="margin:0px;padding:0px;color:green;">//路径(目录或文件的全路径)</span> svn　ls <span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">svn:</span><span class="hljs-comment" style="margin:0px;padding:0px;color:green;">//路径(目录或文件的全路径)</span> 例子：
svn list <span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">svn:</span><span class="hljs-comment" style="margin:0px;padding:0px;color:green;">//localhost/test</span> svn ls <span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">svn:</span><span class="hljs-comment" style="margin:0px;padding:0px;color:green;">//localhost/test ＜－ 显示svn://localhost/test目录下的所有属于版本库的文件和目录 </span></code></pre>
		<h2 id="创建纳入版本控制下的新目录" style="margin:10px 0px;padding:0px;font-size:21px;line-height:1.5;">
			创建纳入版本控制下的新目录
		</h2>
<pre style="margin-top:10px;margin-bottom:10px;padding:0px;white-space:pre-wrap;word-wrap:break-word;"><code class="hljs perl" style="margin:auto;vertical-align:middle;display:block;background:#FFFFFF;height:auto;overflow-x:auto;padding:5px !important;line-height:1.5 !important;font-family:&quot;border:1px solid #CCCCCC !important;border-radius:3px !important;">svn <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">mkdir</span> 目录名
svn <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">mkdir</span> -<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">m</span> <span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">"新增目录备注文本"</span> http:<span class="hljs-regexp" style="margin:0px;padding:0px;">//</span>目录全路径
例子：
svn <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">mkdir</span> newdir
svn <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">mkdir</span> -<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">m</span> <span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">"Making a new dir."</span> svn:<span class="hljs-regexp" style="margin:0px;padding:0px;">//localhost</span><span class="hljs-regexp" style="margin:0px;padding:0px;">/test/newdir</span> </code></pre>
		<blockquote style="margin:10px 0px;padding:5px 10px;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;border:2px solid #EFEFEF;line-height:1.6;color:#333333;">
			<p style="margin:10px auto;padding:0px;">
				注：添加完子目录后，一定要回到根目录更新一下，不然在该目录下提交文件会提示“提交失败”
			</p>
		</blockquote>
<pre style="margin-top:10px;margin-bottom:10px;padding:0px;white-space:pre-wrap;word-wrap:break-word;"><code class="hljs nginx" style="margin:auto;vertical-align:middle;display:block;background:#FFFFFF;height:auto;overflow-x:auto;padding:5px !important;line-height:1.5 !important;font-family:&quot;border:1px solid #CCCCCC !important;border-radius:3px !important;"><span class="hljs-attribute" style="margin:0px;padding:0px;color:#A31515;">svn</span> update</code></pre>
		<blockquote style="margin:10px 0px;padding:5px 10px;background-image:none;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;border:2px solid #EFEFEF;line-height:1.6;color:#333333;">
			<p style="margin:10px auto;padding:0px;">
				注：如果手工在checkout出来的目录里创建了一个新文件夹newsubdir，<br style="margin:0px;padding:0px;" />
再用svn mkdir newsubdir命令后，SVN会提示：<br style="margin:0px;padding:0px;" />
svn: 尝试用 “svn add”或 “svn add --non-recursive”代替？<br style="margin:0px;padding:0px;" />
svn: 无法创建目录“hello”: 文件已经存在<br style="margin:0px;padding:0px;" />
此时，用如下命令解决：<br style="margin:0px;padding:0px;" />
svn add --non-recursive newsubdir<br style="margin:0px;padding:0px;" />
在进入这个newsubdir文件夹，用ls -a查看它下面的全部目录与文件，会发现多了：.svn目录<br style="margin:0px;padding:0px;" />
再用 svn mkdir -m "添hello功能模块文件"&nbsp;<a href="svn://localhost/test/newdir/newsubdir" class="uri" style="margin:0px;padding:0px;color:black;">svn://localhost/test/newdir/newsubdir</a>&nbsp;命令，<br style="margin:0px;padding:0px;" />
SVN提示：<br style="margin:0px;padding:0px;" />
svn: File already exists: filesystem '/data/svnroot/test/db', transaction '4541-1',<br style="margin:0px;padding:0px;" />
path '/newdir/newsubdir '
			</p>
		</blockquote>
		<h2 id="恢复本地修改" style="margin:10px 0px;padding:0px;font-size:21px;line-height:1.5;">
			恢复本地修改
		</h2>
<pre style="margin-top:10px;margin-bottom:10px;padding:0px;white-space:pre-wrap;word-wrap:break-word;"><code class="hljs fortran" style="margin:auto;vertical-align:middle;display:block;background:#FFFFFF;height:auto;overflow-x:auto;padding:5px !important;line-height:1.5 !important;font-family:&quot;border:1px solid #CCCCCC !important;border-radius:3px !important;">svn　revert　[--<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">recursive</span>]　文件名
注意: 本子命令不会存取网络，并且会解除冲突的状况。但是它不会恢复被删除的目录。
例子：
svn revert foo.c ＜－ 丢弃对一个文件的修改
svn revert --<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">recursive</span> . ＜－恢复一整个目录的文件，. 为当前目录 </code></pre>
		<h2 id="把工作拷贝更新到别的url" style="margin:10px 0px;padding:0px;font-size:21px;line-height:1.5;">
			把工作拷贝更新到别的URL
		</h2>
<pre style="margin-top:10px;margin-bottom:10px;padding:0px;white-space:pre-wrap;word-wrap:break-word;"><code class="hljs groovy" style="margin:auto;vertical-align:middle;display:block;background:#FFFFFF;height:auto;overflow-x:auto;padding:5px !important;line-height:1.5 !important;font-family:&quot;border:1px solid #CCCCCC !important;border-radius:3px !important;">svn <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">switch</span> <span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">http:</span><span class="hljs-comment" style="margin:0px;padding:0px;color:green;">//目录全路径　本地目录全路径</span> 例子：
svn <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">switch</span> <span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">http:</span><span class="hljs-comment" style="margin:0px;padding:0px;color:green;">//localhost/test/456 . ＜－ (原为123的分支)当前所在目录分支到localhost/test/456</span></code></pre>
		<h2 id="解决冲突" style="margin:10px 0px;padding:0px;font-size:21px;line-height:1.5;">
			解决冲突
		</h2>
<pre style="margin-top:10px;margin-bottom:10px;padding:0px;white-space:pre-wrap;word-wrap:break-word;"><code class="hljs sql" style="margin:auto;vertical-align:middle;display:block;background:#FFFFFF;height:auto;overflow-x:auto;padding:5px !important;line-height:1.5 !important;font-family:&quot;border:1px solid #CCCCCC !important;border-radius:3px !important;">svn　resolved　[本地目录全路径]
例子：
$ svn <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">update</span> <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">C</span> foo.<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">c</span> <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">Updated</span> <span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">to</span> revision <span class="hljs-number" style="margin:0px;padding:0px;">31.</span> 如果你在更新时得到冲突，你的工作拷贝会产生三个新的文件：
$ ls
foo.<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">c</span> foo.<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">c</span>.mine
foo.<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">c</span>.r30
foo.<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">c</span>.r31
当你解决了foo.<span class="hljs-keyword" style="margin:0px;padding:0px;color:#0000FF;">c</span>的冲突，并且准备提交，运行svn resolved让你的工作拷贝知道你已经完成了所有事情。
你可以仅仅删除冲突的文件并且提交，但是svn resolved除了删除冲突文件，还修正了一些记录在工作拷贝管理区域的记录数据，所以我们推荐你使用这个命令。</code></pre>
		<h2 id="不checkout而查看输出特定文件或url的内容" style="margin:10px 0px;padding:0px;font-size:21px;line-height:1.5;">
			不checkout而查看输出特定文件或URL的内容
		</h2>
<pre style="margin-top:10px;margin-bottom:10px;padding:0px;white-space:pre-wrap;word-wrap:break-word;"><code class="hljs go" style="margin:auto;vertical-align:middle;display:block;background:#FFFFFF;height:auto;overflow-x:auto;padding:5px !important;line-height:1.5 !important;font-family:&quot;border:1px solid #CCCCCC !important;border-radius:3px !important;">svn　cat　http:<span class="hljs-comment" style="margin:0px;padding:0px;color:green;">//文件全路径</span> 例子：
svn cat http:<span class="hljs-comment" style="margin:0px;padding:0px;color:green;">//localhost/test/readme.txt</span> <span class="hljs-number" style="margin:0px;padding:0px;">19</span>、新建一个分支<span class="hljs-built_in" style="margin:0px;padding:0px;color:#0000FF;">copy</span> svn <span class="hljs-built_in" style="margin:0px;padding:0px;color:#0000FF;">copy</span> branchA branchB  -m <span class="hljs-string" style="margin:0px;padding:0px;color:#A31515;">"make B branch"</span> <span class="hljs-comment" style="margin:0px;padding:0px;color:green;">// 从branchA拷贝出一个新分支branchB</span> <span class="hljs-number" style="margin:0px;padding:0px;">20</span>、合并内容到分支merge
svn merge branchA branchB <span class="hljs-comment" style="margin:0px;padding:0px;color:green;">// 把对branchA的修改合并到分支branchB</span></code>
		<div>
			<span class="hljs-comment" style="margin:0px;padding:0px;color:green;"> </span>
		</div>
</pre>
	</div>
	<div class="clear" style="margin:0px;padding:0px;clear:both;">
	</div>
	<div id="blog_post_info_block" style="margin:20px 0px 0px;padding:0px;">
		<div id="BlogPostCategory" style="margin:0px 0px 10px;padding:0px;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
		</div>
	</div>
</p>