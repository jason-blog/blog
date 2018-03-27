<div class="postTitle" style="box-sizing:border-box;font-size:14.7px;font-weight:bold;margin-bottom:10px;color:#4B4B4B;font-family:Verdana, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
	<h1 style="margin:10px 0px;font-size:14.7px;color:#666666;box-sizing:border-box;">
		<a id="cb_post_title_url" class="postTitle2" href="http://www.cnblogs.com/davidwang456/p/3784102.html" style="box-sizing:border-box;text-decoration:none;color:#3468A4;">linux shell pushd popd dirs命令</a>
	</h1>
</div>
<div id="cnblogs_post_body" style="box-sizing:border-box;margin-bottom:20px;word-break:break-word;color:#4B4B4B;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:13px;white-space:normal;background-color:#FFFFFF;">
	<p style="box-sizing:border-box;margin:10px auto;">
		<strong style="box-sizing:border-box;">1、dirs</strong><br style="box-sizing:border-box;" />
<br style="box-sizing:border-box;" />
<span style="box-sizing:border-box;">1）功能</span><br style="box-sizing:border-box;" />
<span style="box-sizing:border-box;">显示当前目录栈中的所有记录（不带参数的dirs命令显示当前目录栈中的记录）</span><br style="box-sizing:border-box;" />
<br style="box-sizing:border-box;" />
<span style="box-sizing:border-box;">2）语法</span><br style="box-sizing:border-box;" />
<span style="box-sizing:border-box;">（1）格式：dirs&nbsp; [-clpv]&nbsp; [+n]&nbsp; [-n]</span><br style="box-sizing:border-box;" />
<span style="box-sizing:border-box;">（2）选项</span><br style="box-sizing:border-box;" />
<span style="box-sizing:border-box;">-c &nbsp;&nbsp; 删除目录栈中的所有记录</span><br style="box-sizing:border-box;" />
<span style="box-sizing:border-box;">-l&nbsp;&nbsp;&nbsp;&nbsp; 以完整格式显示</span><br style="box-sizing:border-box;" />
<span style="box-sizing:border-box;">-p&nbsp;&nbsp;&nbsp; 一个目录一行的方式显示</span><br style="box-sizing:border-box;" />
<span style="box-sizing:border-box;">-v&nbsp;&nbsp;&nbsp; 每行一个目录来显示目录栈的内容，每个目录前加上的编号</span><br style="box-sizing:border-box;" />
<span style="box-sizing:border-box;">+N&nbsp; 显示从左到右的第n个目录，数字从0开始</span><br style="box-sizing:border-box;" />
<span style="box-sizing:border-box;">-N&nbsp;&nbsp; 显示从右到左的第n个日录，数字从0开始</span><br style="box-sizing:border-box;" />
<span style="box-sizing:border-box;">注意：dirs始终显示当然目录, 再是堆栈中的内容；即使目录堆栈为空, dirs命令仍然只显示当然目录</span><br style="box-sizing:border-box;" />
<br style="box-sizing:border-box;" />
<strong style="box-sizing:border-box;">2、pushd<br style="box-sizing:border-box;" />
</strong><br style="box-sizing:border-box;" />
<span style="box-sizing:border-box;">1）功能</span><br style="box-sizing:border-box;" />
<span style="box-sizing:border-box;">pushd命令常用于将目录加入到栈中，加入记录到目录栈顶部，并切换到该目录；若pushd命令不加任何参数，则会将位于记录栈最上面的2个目录对换位置</span><br style="box-sizing:border-box;" />
<br style="box-sizing:border-box;" />
<span style="box-sizing:border-box;">2）语法</span><br style="box-sizing:border-box;" />
<span style="box-sizing:border-box;">（1）格式：pushd&nbsp; [目录 | -N | +N]&nbsp;&nbsp; [-n]</span><br style="box-sizing:border-box;" />
<span style="box-sizing:border-box;">（2）选项</span><br style="box-sizing:border-box;" />
<span style="box-sizing:border-box;">目录&nbsp;&nbsp; 将该目录加入到栈顶，并执行"cd 目录"，切换到该目录</span><br style="box-sizing:border-box;" />
<span style="box-sizing:border-box;">+N&nbsp;&nbsp; 将第N个目录移至栈顶（从左边数起，数字从0开始）</span><br style="box-sizing:border-box;" />
<span style="box-sizing:border-box;">-N&nbsp;&nbsp;&nbsp; 将第N个目录移至栈顶（从右边数起，数字从0开始）</span><br style="box-sizing:border-box;" />
<span style="box-sizing:border-box;">-n&nbsp;&nbsp;&nbsp; 将目录入栈时，不切换目录</span>
	</p>
	<p style="box-sizing:border-box;margin:10px auto;">
		------------------------------------------------------------------------------------------
	</p>
	<h1 style="margin:10px 0px 5px;font-size:28px;color:#666666;box-sizing:border-box;line-height:1.5;">
		pushd
	</h1>
	<p style="box-sizing:border-box;margin:10px auto;">
		Save and then change the current directory. With no arguments,&nbsp;<code style="box-sizing:border-box;">pushd</code>&nbsp;exchanges the top two directories.
	</p>
<pre style="margin-top:0px;margin-bottom:0px;white-space:pre-wrap;word-wrap:break-word;box-sizing:border-box;">SYNTAX
      pushd [<var style="box-sizing:border-box;">dir</var> | <var style="box-sizing:border-box;">+N</var> | <var style="box-sizing:border-box;">-N</var>] [-n]
KEY
   +N   Brings the Nth directory (counting from the left of the list 
        printed by dirs, starting with zero) to the top of the list by 
        rotating the stack. 

   -N   Brings the Nth directory (counting from the right of the list 
        printed by dirs, starting with zero) to the top of the list by 
        rotating the stack. 

   -n   Suppresses the normal change of directory when adding directories to the 
        stack, so that only the stack is manipulated. 

   dir  Makes the current working directory be the top of the stack, and then executes 
        the equivalent of `cd dir'. cds to dir.</pre>
	<p style="box-sizing:border-box;margin:10px auto;">
		<br style="box-sizing:border-box;" />
<br style="box-sizing:border-box;" />
<strong style="box-sizing:border-box;">3、popd</strong><br style="box-sizing:border-box;" />
<br style="box-sizing:border-box;" />
<span style="box-sizing:border-box;">1）功能</span><br style="box-sizing:border-box;" />
<span style="box-sizing:border-box;">popd用于删除目录栈中的记录；如果popd命令不加任何参数，则会先删除目录栈最上面的记录，然后切换到删除过后的目录栈中的最上面的目录</span><br style="box-sizing:border-box;" />
<br style="box-sizing:border-box;" />
<span style="box-sizing:border-box;">2）语法</span><br style="box-sizing:border-box;" />
<span style="box-sizing:border-box;">（1）格式：popd&nbsp; [-N | +N]&nbsp;&nbsp; [-n]</span><br style="box-sizing:border-box;" />
<span style="box-sizing:border-box;">（2）选项</span><br style="box-sizing:border-box;" />
<span style="box-sizing:border-box;">+N&nbsp;&nbsp; 将第N个目录删除（从左边数起，数字从0开始）</span><br style="box-sizing:border-box;" />
<span style="box-sizing:border-box;">-N&nbsp;&nbsp;&nbsp; 将第N个目录删除（从右边数起，数字从0开始）</span><br style="box-sizing:border-box;" />
<span style="box-sizing:border-box;">-n&nbsp;&nbsp;&nbsp; 将目录出栈时，不切换目录</span>
	</p>
	<p style="box-sizing:border-box;margin:10px auto;">
		&nbsp;-------------------------------------------------------------------------------------------
	</p>
	<h1 style="margin:10px 0px 5px;font-size:28px;color:#666666;box-sizing:border-box;line-height:1.5;">
		popd
	</h1>
	<p style="box-sizing:border-box;margin:10px auto;">
		Remove the top entry from the directory stack, and&nbsp;<code style="box-sizing:border-box;">cd</code>&nbsp;to the new top directory.
	</p>
<pre style="margin-top:0px;margin-bottom:0px;white-space:pre-wrap;word-wrap:break-word;box-sizing:border-box;">SYNTAX
      popd [+<em style="box-sizing:border-box;">N</em> | -<em style="box-sizing:border-box;">N</em>] [-n]

Key
   +<em style="box-sizing:border-box;">N</em> Remove the <em style="box-sizing:border-box;">N</em>th directory (counting from the left of the list 
        printed by dirs), starting with zero. 

   -<em style="box-sizing:border-box;">N</em> Remove the <em style="box-sizing:border-box;">N</em>th directory (counting from the right of the list 
        printed by dirs), starting with zero. 

   -n   Suppress the normal change of directory when removing directories from 
        the stack, so that only the stack is manipulated. </pre>
	<p style="box-sizing:border-box;margin:10px auto;">
		When no arguments are given, popd removes the top directory from the stack and performs a cd to the new top directory.&nbsp;<br style="box-sizing:border-box;" />
<br style="box-sizing:border-box;" />
The elements are numbered from 0 starting at the first directory listed with dirs; i.e., popd is equivalent to popd +0.
	</p>
	<p style="box-sizing:border-box;margin:10px auto;">
		<span style="box-sizing:border-box;">参考：http://hi.baidu.com/linuxtrip/item/47a38c8eec00e98f4414cfb7</span>
	</p>
</div>