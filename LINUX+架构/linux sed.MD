<pre class="prettyprint lang-js linenums">  BASENAME=`basename $FILE`
  MARKEDNAME=`echo ${BASENAME} | sed -r -e "s@^([^.]*)(.*).xml@\1-${DATE}\2.xml@g"`
<p>
	将文件名替换为按照 . 分割 的第一位+时间+第二位.xml
</p>

<p>
	<br />

</p>

<p>
	
	<div style="color:#333333;font-size:14px;white-space:normal;background-color:#FFFFFF;margin:0px;padding:0px;font-family:verdana, Arial, Helvetica, sans-serif;line-height:25px;">
		<span style="margin:0px;padding:0px;font-size:12pt;">1.简介</span>
	</div>

	<div style="color:#333333;font-size:14px;white-space:normal;background-color:#FFFFFF;margin:0px;padding:0px;font-family:verdana, Arial, Helvetica, sans-serif;line-height:25px;">
		sed是非交互式的编辑器。它不会修改文件，除非使用shell重定向来保存结果。默认情况下，所有的输出行都被打印到屏幕上。
	</div>

	<div style="color:#333333;font-size:14px;white-space:normal;background-color:#FFFFFF;margin:0px;padding:0px;font-family:verdana, Arial, Helvetica, sans-serif;line-height:25px;">
		sed编辑器逐行处理文件（或输入），并将结果发送到屏幕。具体过程如下：首先sed把当前正在处理的行保存在一个临时缓存区中（也称为模式空间），然后处理临时缓冲区中的行，完成后把该行发送到屏幕上。sed每处理完一行就将其从临时缓冲区删除，然后将下一行读入，进行处理和显示。处理完输入文件的最后一行后，sed便结束运行。sed把每一行都存在临时缓冲区中，对这个副本进行编辑，所以不会修改原文件。
	</div>

	<div style="color:#333333;font-size:14px;white-space:normal;background-color:#FFFFFF;margin:0px;padding:0px;font-family:verdana, Arial, Helvetica, sans-serif;line-height:25px;">
		&nbsp;
	</div>

	<div style="color:#333333;font-size:14px;white-space:normal;background-color:#FFFFFF;margin:0px;padding:0px;font-family:verdana, Arial, Helvetica, sans-serif;line-height:25px;">
		
	</div>

	<div style="color:#333333;font-size:14px;white-space:normal;background-color:#FFFFFF;margin:0px;padding:0px;font-family:verdana, Arial, Helvetica, sans-serif;line-height:25px;">
		
	</div>

	<div style="color:#333333;font-size:14px;white-space:normal;background-color:#FFFFFF;margin:0px;padding:0px;font-family:verdana, Arial, Helvetica, sans-serif;line-height:25px;">
		
	</div>

	<div style="color:#333333;font-size:14px;white-space:normal;background-color:#FFFFFF;margin:0px;padding:0px;font-family:verdana, Arial, Helvetica, sans-serif;line-height:25px;">
		
	</div>

	<div style="color:#333333;font-size:14px;white-space:normal;background-color:#FFFFFF;margin:0px;padding:0px;font-family:verdana, Arial, Helvetica, sans-serif;line-height:25px;">
		<span style="margin:0px;padding:0px;font-size:12pt;">2.定址</span>
	</div>

	<div style="color:#333333;font-size:14px;white-space:normal;background-color:#FFFFFF;margin:0px;padding:0px;font-family:verdana, Arial, Helvetica, sans-serif;line-height:25px;">
		定址用于决定对哪些行进行编辑。地址的形式可以是数字、正则表达式、或二者的结合。如果没有指定地址，sed将处理输入文件的所有行。
	</div>

	<div style="color:#333333;font-size:14px;white-space:normal;background-color:#FFFFFF;margin:0px;padding:0px;font-family:verdana, Arial, Helvetica, sans-serif;line-height:25px;">
		&nbsp;
	</div>

	<div style="color:#333333;font-size:14px;white-space:normal;background-color:#FFFFFF;margin:0px;padding:0px;font-family:verdana, Arial, Helvetica, sans-serif;line-height:25px;">
		地址是一个数字，则表示行号；是“$"符号，则表示最后一行。例如：&nbsp;
	</div>

	<div style="color:#333333;font-size:14px;white-space:normal;background-color:#FFFFFF;margin:0px;padding:0px;font-family:verdana, Arial, Helvetica, sans-serif;line-height:25px;">
		
	</div>

	<div style="color:#333333;font-size:14px;white-space:normal;background-color:#FFFFFF;margin:0px;padding:0px;font-family:verdana, Arial, Helvetica, sans-serif;line-height:25px;">
		
	</div>

	<div style="color:#333333;font-size:14px;white-space:normal;background-color:#FFFFFF;margin:0px;padding:0px;font-family:verdana, Arial, Helvetica, sans-serif;line-height:25px;">
		
		<table cellspacing="0" cellpadding="0" width="95%" bgcolor="#f1f1f1" border="1" style="margin:0px;padding:0px;border:1px solid #C0C0C0;">
			
			<tbody style="margin:0px;padding:0px;">
				
				<tr style="margin:0px;padding:0px;">
					
					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						
						<p style="margin-right:5px;margin-left:5px;padding-top:0px;padding-bottom:0px;line-height:21px;">
							<span style="margin:0px;padding:0px;font-size:10pt;"><code style="margin:0px;padding:0px;">sed&nbsp;<span style="margin:0px;padding:0px;color:#0000CC;">-</span>n&nbsp;<span style="margin:0px;padding:0px;color:#FF00FF;">'3p'</span>&nbsp;datafile
只打印第三行</code></span>
						</p>

					</td>

				</tr>

			</tbody>

		</table>

	</div>

	<p style="color:#333333;font-size:14px;white-space:normal;background-color:#FFFFFF;margin:10px auto;padding-top:0px;padding-bottom:0px;font-family:verdana, Arial, Helvetica, sans-serif;line-height:25px;">
		&nbsp;
	</p>

	<p style="color:#333333;font-size:14px;white-space:normal;background-color:#FFFFFF;margin:10px auto;padding-top:0px;padding-bottom:0px;font-family:verdana, Arial, Helvetica, sans-serif;line-height:25px;">
		&nbsp;只显示指定行范围的文件内容，例如：
	</p>

	<div class="cnblogs_code" style="color:#333333;white-space:normal;margin:5px 0px;padding:5px;background-color:#F5F5F5;font-family:&quot;border:1px solid #CCCCCC;overflow:auto;">
		
		<div style="margin:0px;padding:0px;">
			#&nbsp;只查看文件的第100行到第200行
sed&nbsp;-n&nbsp;'100,200p'&nbsp;mysql_slow_query.log
		</div>

	</div>

	<p style="color:#333333;font-size:14px;white-space:normal;background-color:#FFFFFF;margin:10px auto;padding-top:0px;padding-bottom:0px;font-family:verdana, Arial, Helvetica, sans-serif;line-height:25px;">
		&nbsp;
	</p>

	<p style="color:#333333;font-size:14px;white-space:normal;background-color:#FFFFFF;margin:10px auto;padding-top:0px;padding-bottom:0px;font-family:verdana, Arial, Helvetica, sans-serif;line-height:25px;">
		地址是逗号分隔的，那么需要处理的地址是这两行之间的范围（包括这两行在内）。范围可以用数字、正则表达式、或二者的组合表示。例如：
	</p>

	<div style="color:#333333;font-size:14px;white-space:normal;background-color:#FFFFFF;margin:0px;padding:0px;font-family:verdana, Arial, Helvetica, sans-serif;line-height:25px;">
		
		<table cellspacing="0" cellpadding="0" width="95%" bgcolor="#f1f1f1" border="1" style="margin:0px;padding:0px;border:1px solid #C0C0C0;">
			
			<tbody style="margin:0px;padding:0px;">
				
				<tr style="margin:0px;padding:0px;">
					
					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						
						<p style="margin-right:5px;margin-left:5px;padding-top:0px;padding-bottom:0px;line-height:21px;">
							<span style="margin:0px;padding:0px;font-size:10pt;"><code style="margin:0px;padding:0px;">sed&nbsp;<span style="margin:0px;padding:0px;color:#FF00FF;">'2,5d'</span>&nbsp;datafile
#删除第二到第五行
sed&nbsp;<span style="margin:0px;padding:0px;color:#FF00FF;">'/My/,/You/d'</span>&nbsp;datafile
#删除包含<span style="margin:0px;padding:0px;color:#FF00FF;">"My"<span style="margin:0px;padding:0px;color:#000000;">的</span></span>行到包含<span style="margin:0px;padding:0px;color:#FF00FF;">"You"<span style="margin:0px;padding:0px;color:#000000;">的</span></span>行之间的行
sed&nbsp;<span style="margin:0px;padding:0px;color:#FF00FF;">'/My/,10d'</span>&nbsp;datafile
#删除包含<span style="margin:0px;padding:0px;color:#FF00FF;">"My"<span style="margin:0px;padding:0px;color:#000000;">的</span></span>行到第十行的内容</code></span>
						</p>

					</td>

				</tr>

			</tbody>

		</table>

	</div>

	<div style="color:#333333;font-size:14px;white-space:normal;background-color:#FFFFFF;margin:0px;padding:0px;font-family:verdana, Arial, Helvetica, sans-serif;line-height:25px;">
		
	</div>

	<p style="color:#333333;font-size:14px;white-space:normal;background-color:#FFFFFF;margin:10px auto;padding-top:0px;padding-bottom:0px;font-family:verdana, Arial, Helvetica, sans-serif;line-height:25px;">
		<span style="margin:0px;padding:0px;font-size:12pt;">&nbsp;</span>
	</p>

	<p style="color:#333333;font-size:14px;white-space:normal;background-color:#FFFFFF;margin:10px auto;padding-top:0px;padding-bottom:0px;font-family:verdana, Arial, Helvetica, sans-serif;line-height:25px;">
		<span style="margin:0px;padding:0px;font-size:12pt;">&nbsp;</span>
	</p>

	<p style="color:#333333;font-size:14px;white-space:normal;background-color:#FFFFFF;margin:10px auto;padding-top:0px;padding-bottom:0px;font-family:verdana, Arial, Helvetica, sans-serif;line-height:25px;">
		<span style="margin:0px;padding:0px;font-size:12pt;">3.命令与选项</span>
	</p>

	<p style="color:#333333;font-size:14px;white-space:normal;background-color:#FFFFFF;margin:10px auto;padding-top:0px;padding-bottom:0px;font-family:verdana, Arial, Helvetica, sans-serif;line-height:25px;">
		sed命令告诉sed如何处理由地址指定的各输入行，如果没有指定地址则处理所有的输入行。
	</p>

	<p style="color:#333333;font-size:14px;white-space:normal;background-color:#FFFFFF;margin:10px auto;padding-top:0px;padding-bottom:0px;font-family:verdana, Arial, Helvetica, sans-serif;line-height:25px;">
		&nbsp;
	</p>

	<p style="color:#333333;font-size:14px;white-space:normal;background-color:#FFFFFF;margin:10px auto;padding-top:0px;padding-bottom:0px;font-family:verdana, Arial, Helvetica, sans-serif;line-height:25px;">
		<span style="margin:0px;padding:0px;">3.1 sed命令</span>
	</p>

	<div style="color:#333333;font-size:14px;white-space:normal;background-color:#FFFFFF;margin:0px;padding:0px;font-family:verdana, Arial, Helvetica, sans-serif;line-height:25px;">
		
		<table cellspacing="1" cellpadding="1" width="500" border="1" style="margin:0px;padding:0px;border:1px solid #C0C0C0;">
			
			<tbody style="margin:0px;padding:0px;">
				
				<tr style="margin:0px;padding:0px;">
					
					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						&nbsp;<span style="margin:0px;padding:0px;font-size:10pt;">命令</span>
					</td>

					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;功能</span>
					</td>

				</tr>

				<tr style="margin:0px;padding:0px;">
					
					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;a\</span>
					</td>

					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						
						<p style="margin:10px auto;padding-top:0px;padding-bottom:0px;">
							<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;在当前行后添加一行或多行。多行时除最后一行外，每行末尾需用“\”续行</span>
						</p>

					</td>

				</tr>

				<tr style="margin:0px;padding:0px;">
					
					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;c\</span>
					</td>

					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;用此符号后的新文本替换当前行中的文本。多行时除最后一行外，每行末尾需用"\"续行</span>
					</td>

				</tr>

				<tr style="margin:0px;padding:0px;">
					
					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;i\</span>
					</td>

					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;在当前行之前插入文本。多行时除最后一行外，每行末尾需用"\"续行</span>
					</td>

				</tr>

				<tr style="margin:0px;padding:0px;">
					
					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;d</span>
					</td>

					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;删除行</span>
					</td>

				</tr>

				<tr style="margin:0px;padding:0px;">
					
					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;h</span>
					</td>

					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;把模式空间里的内容复制到暂存缓冲区</span>
					</td>

				</tr>

				<tr style="margin:0px;padding:0px;">
					
					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;H</span>
					</td>

					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;把模式空间里的内容追加到暂存缓冲区</span>
					</td>

				</tr>

				<tr style="margin:0px;padding:0px;">
					
					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;g</span>
					</td>

					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;把暂存缓冲区里的内容复制到模式空间，覆盖原有的内容</span>
					</td>

				</tr>

				<tr style="margin:0px;padding:0px;">
					
					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;G</span>
					</td>

					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;把暂存缓冲区的内容追加到模式空间里，追加在原有内容的后面</span>
					</td>

				</tr>

				<tr style="margin:0px;padding:0px;">
					
					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;l</span>
					</td>

					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;列出非打印字符</span>
					</td>

				</tr>

				<tr style="margin:0px;padding:0px;">
					
					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;p</span>
					</td>

					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;打印行</span>
					</td>

				</tr>

				<tr style="margin:0px;padding:0px;">
					
					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;n</span>
					</td>

					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;读入下一输入行，并从下一条命令而不是第一条命令开始对其的处理</span>
					</td>

				</tr>

				<tr style="margin:0px;padding:0px;">
					
					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;q</span>
					</td>

					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;结束或退出sed</span>
					</td>

				</tr>

				<tr style="margin:0px;padding:0px;">
					
					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;r</span>
					</td>

					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;从文件中读取输入行</span>
					</td>

				</tr>

				<tr style="margin:0px;padding:0px;">
					
					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;!</span>
					</td>

					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;对所选行以外的所有行应用命令</span>
					</td>

				</tr>

				<tr style="margin:0px;padding:0px;">
					
					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;s</span>
					</td>

					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;用一个字符串替换另一个</span>
					</td>

				</tr>

				<tr style="margin:0px;padding:0px;">
					
					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;g</span>
					</td>

					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;在行内进行全局替换</span>
					</td>

				</tr>

				<tr style="margin:0px;padding:0px;">
					
					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;</span>
					</td>

					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						&nbsp;
					</td>

				</tr>

				<tr style="margin:0px;padding:0px;">
					
					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;w</span>
					</td>

					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;将所选的行写入文件</span>
					</td>

				</tr>

				<tr style="margin:0px;padding:0px;">
					
					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;x</span>
					</td>

					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;交换暂存缓冲区与模式空间的内容</span>
					</td>

				</tr>

				<tr style="margin:0px;padding:0px;">
					
					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;y</span>
					</td>

					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;将字符替换为另一字符（不能对正则表达式使用y命令）</span>
					</td>

				</tr>

			</tbody>

		</table>

	</div>

	<p style="color:#333333;font-size:14px;white-space:normal;background-color:#FFFFFF;margin:10px auto;padding-top:0px;padding-bottom:0px;font-family:verdana, Arial, Helvetica, sans-serif;line-height:25px;">
		<span style="margin:0px;padding:0px;">&nbsp;</span>
	</p>

	<p style="color:#333333;font-size:14px;white-space:normal;background-color:#FFFFFF;margin:10px auto;padding-top:0px;padding-bottom:0px;font-family:verdana, Arial, Helvetica, sans-serif;line-height:25px;">
		<span style="margin:0px;padding:0px;">3.2 sed选项</span>
	</p>

	<div style="color:#333333;font-size:14px;white-space:normal;background-color:#FFFFFF;margin:0px;padding:0px;font-family:verdana, Arial, Helvetica, sans-serif;line-height:25px;">
		
		<table cellspacing="1" cellpadding="1" width="500" border="1" style="margin:0px;padding:0px;border:1px solid #C0C0C0;">
			
			<tbody style="margin:0px;padding:0px;">
				
				<tr style="margin:0px;padding:0px;">
					
					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;选项</span>
					</td>

					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;功能</span>
					</td>

				</tr>

				<tr style="margin:0px;padding:0px;">
					
					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;-e</span>
					</td>

					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;进行多项编辑，即对输入行应用多条sed命令时使用</span>
					</td>

				</tr>

				<tr style="margin:0px;padding:0px;">
					
					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;-n</span>
					</td>

					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;取消默认的输出</span>
					</td>

				</tr>

				<tr style="margin:0px;padding:0px;">
					
					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;-f</span>
					</td>

					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;指定sed脚本的文件名</span>
					</td>

				</tr>

			</tbody>

		</table>

	</div>

	<div style="color:#333333;font-size:14px;white-space:normal;background-color:#FFFFFF;margin:0px;padding:0px;font-family:verdana, Arial, Helvetica, sans-serif;line-height:25px;">
		
	</div>

	<div style="color:#333333;font-size:14px;white-space:normal;background-color:#FFFFFF;margin:0px;padding:0px;font-family:verdana, Arial, Helvetica, sans-serif;line-height:25px;">
		
	</div>

	<div style="color:#333333;font-size:14px;white-space:normal;background-color:#FFFFFF;margin:0px;padding:0px;font-family:verdana, Arial, Helvetica, sans-serif;line-height:25px;">
		<span style="margin:0px;padding:0px;font-size:12pt;">&nbsp;</span>
	</div>

	<div style="color:#333333;font-size:14px;white-space:normal;background-color:#FFFFFF;margin:0px;padding:0px;font-family:verdana, Arial, Helvetica, sans-serif;line-height:25px;">
		<span style="margin:0px;padding:0px;font-size:12pt;">&nbsp;</span>
	</div>

	<div style="color:#333333;font-size:14px;white-space:normal;background-color:#FFFFFF;margin:0px;padding:0px;font-family:verdana, Arial, Helvetica, sans-serif;line-height:25px;">
		<span style="margin:0px;padding:0px;font-size:12pt;">4.退出状态</span>
	</div>

	<div style="color:#333333;font-size:14px;white-space:normal;background-color:#FFFFFF;margin:0px;padding:0px;font-family:verdana, Arial, Helvetica, sans-serif;line-height:25px;">
		sed不向grep一样，不管是否找到指定的模式，它的退出状态都是0。只有当命令存在语法错误时，sed的退出状态才不是0。
	</div>

	<div style="color:#333333;font-size:14px;white-space:normal;background-color:#FFFFFF;margin:0px;padding:0px;font-family:verdana, Arial, Helvetica, sans-serif;line-height:25px;">
		
	</div>

	<div style="color:#333333;font-size:14px;white-space:normal;background-color:#FFFFFF;margin:0px;padding:0px;font-family:verdana, Arial, Helvetica, sans-serif;line-height:25px;">
		
	</div>

	<div style="color:#333333;font-size:14px;white-space:normal;background-color:#FFFFFF;margin:0px;padding:0px;font-family:verdana, Arial, Helvetica, sans-serif;line-height:25px;">
		
	</div>

	<div style="color:#333333;font-size:14px;white-space:normal;background-color:#FFFFFF;margin:0px;padding:0px;font-family:verdana, Arial, Helvetica, sans-serif;line-height:25px;">
		
		<div style="margin:0px;padding:0px;">
			<span style="margin:0px;padding:0px;font-size:12pt;">5.正则表达式元字符</span>
		</div>

		<div style="margin:0px;padding:0px;">
			&nbsp;与grep一样，sed也支持特殊元字符，来进行模式查找、替换。不同的是，sed使用的正则表达式是括在斜杠线"/"之间的模式。
		</div>

		<div style="margin:0px;padding:0px;">
			如果要把正则表达式分隔符"/"改为另一个字符，比如o，只要在这个字符前加一个反斜线，在字符后跟上正则表达式，再跟上这个字符即可。例如：sed -n '\o^Myop' datafile
		</div>

		<div style="margin:0px;padding:0px;">
			&nbsp;
		</div>

		<div style="margin:0px;padding:0px;">
			
			<table cellspacing="1" cellpadding="1" width="500" border="1" style="margin:0px;padding:0px;border:1px solid #C0C0C0;">
				
				<tbody style="margin:0px;padding:0px;">
					
					<tr style="margin:0px;padding:0px;">
						
						<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
							&nbsp;<span style="margin:0px;padding:0px;font-size:10pt;">元字符</span>
						</td>

						<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
							<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;功能</span>
						</td>

						<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
							<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;示例</span>
						</td>

					</tr>

					<tr style="margin:0px;padding:0px;">
						
						<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
							<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;^</span>
						</td>

						<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
							<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;行首定位符</span>
						</td>

						<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
							<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;/^my/&nbsp; 匹配所有以my开头的行</span>
						</td>

					</tr>

					<tr style="margin:0px;padding:0px;">
						
						<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
							<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;$</span>
						</td>

						<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
							<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;行尾定位符</span>
						</td>

						<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
							<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;/my$/&nbsp; 匹配所有以my结尾的行</span>
						</td>

					</tr>

					<tr style="margin:0px;padding:0px;">
						
						<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
							<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;.</span>
						</td>

						<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
							<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;匹配除换行符以外的单个字符</span>
						</td>

						<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
							<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;/m..y/&nbsp; 匹配包含字母m，后跟两个任意字符，再跟字母y的行</span>
						</td>

					</tr>

					<tr style="margin:0px;padding:0px;">
						
						<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
							<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;*</span>
						</td>

						<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
							<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;匹配零个或多个前导字符</span>
						</td>

						<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
							<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;/my*/&nbsp; 匹配包含字母m,后跟零个或多个y字母的行</span>
						</td>

					</tr>

					<tr style="margin:0px;padding:0px;">
						
						<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
							<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;[]</span>
						</td>

						<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
							<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;匹配指定字符组内的任一字符</span>
						</td>

						<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
							<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;/[Mm]y/&nbsp; 匹配包含My或my的行</span>
						</td>

					</tr>

					<tr style="margin:0px;padding:0px;">
						
						<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
							<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;[^]</span>
						</td>

						<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
							<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;匹配不在指定字符组内的任一字符</span>
						</td>

						<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
							<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;/[^Mm]y/&nbsp; 匹配包含y，但y之前的那个字符不是M或m的行</span>
						</td>

					</tr>

					<tr style="margin:0px;padding:0px;">
						
						<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
							<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;<span class="MathJax_Preview" style="color:#888888;"></span><nobr style="transition:none;border:0px;padding:0px;margin:0px;max-width:none;max-height:none;min-width:0px;min-height:0px;vertical-align:0px;line-height:normal;">..</nobr></span>
						</td>

						<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
							<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;保存已匹配的字符</span>
						</td>

						<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
							<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;1,20s/<span class="MathJax_Preview" style="color:#888888;"></span><nobr style="transition:none;border:0px;padding:0px;margin:0px;max-width:none;max-height:none;min-width:0px;min-height:0px;vertical-align:0px;line-height:normal;">you</nobr>self/\1r/&nbsp; 标记元字符之间的模式，并将其保存为标签1，之后可以使用\1来引用它。最多可以定义9个标签，从左边开始编号，最左边的是第一个。此例中，对第1到第20行进行处理，you被保存为标签1，如果发现youself，则替换为your。</span>
						</td>

					</tr>

					<tr style="margin:0px;padding:0px;">
						
						<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
							<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;&amp;</span>
						</td>

						<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
							<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;保存查找串以便在替换串中引用</span>
						</td>

						<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
							<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;s/my/**&amp;**/&nbsp;&nbsp;符号&amp;代表查找串。my将被替换为**my**</span>
						</td>

					</tr>

					<tr style="margin:0px;padding:0px;">
						
						<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
							<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;\&lt;</span>
						</td>

						<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
							<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;词首定位符</span>
						</td>

						<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
							<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;/\&lt;my/&nbsp; 匹配包含以my开头的单词的行</span>
						</td>

					</tr>

					<tr style="margin:0px;padding:0px;">
						
						<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
							<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;\&gt;</span>
						</td>

						<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
							<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;词尾定位符</span>
						</td>

						<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
							<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;/my\&gt;/&nbsp; 匹配包含以my结尾的单词的行</span>
						</td>

					</tr>

					<tr style="margin:0px;padding:0px;">
						
						<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
							<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;x\{m\}</span>
						</td>

						<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
							<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;连续m个x</span>
						</td>

						<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
							<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;/9\{5\}/ 匹配包含连续5个9的行</span>
						</td>

					</tr>

					<tr style="margin:0px;padding:0px;">
						
						<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
							<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;x\{m,\}</span>
						</td>

						<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
							<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;至少m个x</span>
						</td>

						<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
							<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;/9\{5,\}/&nbsp; 匹配包含至少连续5个9的行</span>
						</td>

					</tr>

					<tr style="margin:0px;padding:0px;">
						
						<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
							<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;x\{m,n\}</span>
						</td>

						<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
							<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;至少m个，但不超过n个x</span>
						</td>

						<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
							<span style="margin:0px;padding:0px;font-size:10pt;">&nbsp;/9\{5,7\}/&nbsp; 匹配包含连续5到7个9的行</span>
						</td>

					</tr>

				</tbody>

			</table>

		</div>

		<div style="margin:0px;padding:0px;">
			
		</div>

		<div style="margin:0px;padding:0px;">
			
		</div>

		<div style="margin:0px;padding:0px;">
			&nbsp;
		</div>

		<div style="margin:0px;padding:0px;">
			
		</div>

		<div style="margin:0px;padding:0px;">
			<span style="margin:0px;padding:0px;font-size:12pt;">6.范例</span>
		</div>

		<div style="margin:0px;padding:0px;">
			&nbsp;
		</div>

		<div style="margin:0px;padding:0px;">
			<span style="margin:0px;padding:0px;">6.1 p命令</span>
		</div>

		<div style="margin:0px;padding:0px;">
			命令p用于显示模式空间的内容。默认情况下，sed把输入行打印在屏幕上，选项-n用于取消默认的打印操作。当选项-n和命令p同时出现时,sed可打印选定的内容。
		</div>

		<div style="margin:0px;padding:0px;">
			&nbsp;
		</div>

		<table cellspacing="0" cellpadding="0" width="95%" bgcolor="#f1f1f1" border="1" style="margin:0px;padding:0px;border:1px solid #C0C0C0;">
			
			<tbody style="margin:0px;padding:0px;">
				
				<tr style="margin:0px;padding:0px;">
					
					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						
						<p style="margin-right:5px;margin-left:5px;padding-top:0px;padding-bottom:0px;line-height:21px;">
							<span style="margin:0px;padding:0px;font-size:10pt;"><code style="margin:0px;padding:0px;">sed&nbsp;<span style="margin:0px;padding:0px;color:#FF00FF;">'/my/p'</span>&nbsp;datafile
#默认情况下，sed把所有输入行都打印在标准输出上。如果某行匹配模式my，p命令将把该行另外打印一遍。</code></span>
						</p>

						<p style="margin-right:5px;margin-left:5px;padding-top:0px;padding-bottom:0px;line-height:21px;">
							<span style="margin:0px;padding:0px;font-size:10pt;"><code style="margin:0px;padding:0px;"> sed&nbsp;<span style="margin:0px;padding:0px;color:#0000CC;">-</span>n&nbsp;<span style="margin:0px;padding:0px;color:#FF00FF;">'/my/p'</span>&nbsp;datafile
#选项<span style="margin:0px;padding:0px;color:#0000CC;">-</span>n取消sed默认的打印，p命令把匹配模式my的行打印一遍。 </code></span>
						</p>

					</td>

				</tr>

			</tbody>

		</table>

		<p style="margin:10px auto;padding-top:0px;padding-bottom:0px;">
			<span style="margin:0px;padding:0px;">&nbsp;</span>
		</p>

		<p style="margin:10px auto;padding-top:0px;padding-bottom:0px;">
			<span style="margin:0px;padding:0px;">6.2 d命令</span>
		</p>

		<p style="margin:10px auto;padding-top:0px;padding-bottom:0px;">
			命令d用于删除输入行。sed先将输入行从文件复制到模式空间里，然后对该行执行sed命令，最后将模式空间里的内容显示在屏幕上。如果发出的是命令d，当前模式空间里的输入行会被删除，不被显示。
		</p>

		<table cellspacing="0" cellpadding="0" width="95%" bgcolor="#f1f1f1" border="1" style="margin:0px;padding:0px;border:1px solid #C0C0C0;">
			
			<tbody style="margin:0px;padding:0px;">
				
				<tr style="margin:0px;padding:0px;">
					
					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						
						<p style="margin-right:5px;margin-left:5px;padding-top:0px;padding-bottom:0px;line-height:21px;">
							<span style="margin:0px;padding:0px;font-size:10pt;"><code style="margin:0px;padding:0px;">sed&nbsp;<span style="margin:0px;padding:0px;color:#FF00FF;">'$d'</span>&nbsp;datafile
#删除最后一行，其余的都被显示

sed&nbsp;<span style="margin:0px;padding:0px;color:#FF00FF;">'/my/d'</span>&nbsp;datafile
#删除包含my的行，其余的都被显示</code></span>
						</p>

					</td>

				</tr>

			</tbody>

		</table>

		<p style="margin:10px auto;padding-top:0px;padding-bottom:0px;">
			<span style="margin:0px;padding:0px;">&nbsp;</span>
		</p>

		<p style="margin:10px auto;padding-top:0px;padding-bottom:0px;">
			<span style="margin:0px;padding:0px;">6.3 s命令</span>
		</p>

		<div style="margin:0px;padding:0px;">
			
		</div>

		<table cellspacing="0" cellpadding="0" width="95%" bgcolor="#f1f1f1" border="1" style="margin:0px;padding:0px;border:1px solid #C0C0C0;">
			
			<tbody style="margin:0px;padding:0px;">
				
				<tr style="margin:0px;padding:0px;">
					
					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						
						<p style="margin-right:5px;margin-left:5px;padding-top:0px;padding-bottom:0px;line-height:21px;">
							<span style="margin:0px;padding:0px;font-size:10pt;"><code style="margin:0px;padding:0px;">sed&nbsp;<span style="margin:0px;padding:0px;color:#FF00FF;">'s/^My/You/g'</span>&nbsp;datafile
#命令末端的g表示在行内进行全局替换，也就是说如果某行出现多个My，所有的My都被替换为You。

sed&nbsp;<span style="margin:0px;padding:0px;color:#0000CC;">-</span>n&nbsp;<span style="margin:0px;padding:0px;color:#FF00FF;">'1,20s/My$/You/gp'</span>&nbsp;datafile
#取消默认输出，处理1到20行里匹配以My结尾的行，把行内所有的My替换为You，并打印到屏幕上。</code></span>
						</p>

					</td>

				</tr>

			</tbody>

		</table>

		<div style="margin:0px;padding:0px;">
			&nbsp;&nbsp;
		</div>

		<table cellspacing="0" cellpadding="0" width="95%" bgcolor="#f1f1f1" border="1" style="margin:0px;padding:0px;border:1px solid #C0C0C0;">
			
			<tbody style="margin:0px;padding:0px;">
				
				<tr style="margin:0px;padding:0px;">
					
					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						
						<p style="margin-right:5px;margin-left:5px;padding-top:0px;padding-bottom:0px;line-height:21px;">
							<span style="margin:0px;padding:0px;font-size:10pt;"><code style="margin:0px;padding:0px;">sed&nbsp;<span style="margin:0px;padding:0px;color:#FF00FF;">'s#My#Your#g'</span>&nbsp;datafile
#紧跟在s命令后的字符就是查找串和替换串之间的分隔符。分隔符默认为正斜杠，但可以改变。无论什么字符（换行符、反斜线除外），只要紧跟s命令，就成了新的串分隔符。</code></span>
						</p>

					</td>

				</tr>

			</tbody>

		</table>

		<p style="margin:10px auto;padding-top:0px;padding-bottom:0px;">
			<span style="margin:0px;padding:0px;">&nbsp;</span>
		</p>

		<p style="margin:10px auto;padding-top:0px;padding-bottom:0px;">
			<span style="margin:0px;padding:0px;">6.4 e选项</span>
		</p>

		<p style="margin:10px auto;padding-top:0px;padding-bottom:0px;">
			-e是编辑命令，用于sed执行多个编辑任务的情况下。在下一行开始编辑前，所有的编辑动作将应用到模式缓冲区中的行上。
		</p>

		<table cellspacing="0" cellpadding="0" width="95%" bgcolor="#f1f1f1" border="1" style="margin:0px;padding:0px;border:1px solid #C0C0C0;">
			
			<tbody style="margin:0px;padding:0px;">
				
				<tr style="margin:0px;padding:0px;">
					
					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						
						<p style="margin-right:5px;margin-left:5px;padding-top:0px;padding-bottom:0px;line-height:21px;">
							<span style="margin:0px;padding:0px;font-size:10pt;"><code style="margin:0px;padding:0px;">sed&nbsp;<span style="margin:0px;padding:0px;color:#0000CC;">-</span>e&nbsp;<span style="margin:0px;padding:0px;color:#FF00FF;">'1,10d'</span>&nbsp;<span style="margin:0px;padding:0px;color:#0000CC;">-</span>e&nbsp;<span style="margin:0px;padding:0px;color:#FF00FF;">'s/My/Your/g'</span>&nbsp;datafile</code></span>
						</p>

						<p style="margin-right:5px;margin-left:5px;padding-top:0px;padding-bottom:0px;line-height:21px;">
							<span style="margin:0px;padding:0px;font-size:10pt;"><code style="margin:0px;padding:0px;">#选项-e用于进行多重编辑。第一重编辑删除第1-3行。第二重编辑将出现的所有My替换为Your。因为是逐行进行这两项编辑（即这两个命令都在模式空间的当前行上执行），所以编辑命令的顺序会影响结果。</code></span>
						</p>

					</td>

				</tr>

			</tbody>

		</table>

		<p style="margin:10px auto;padding-top:0px;padding-bottom:0px;">
			<span style="margin:0px;padding:0px;">&nbsp;</span>
		</p>

		<p style="margin:10px auto;padding-top:0px;padding-bottom:0px;">
			<span style="margin:0px;padding:0px;">6.5 r命令</span>
		</p>

		<p style="margin:10px auto;padding-top:0px;padding-bottom:0px;">
			r命令是读命令。sed使用该命令将一个文本文件中的内容加到当前文件的特定位置上。
		</p>

		<table cellspacing="0" cellpadding="0" width="95%" bgcolor="#f1f1f1" border="1" style="margin:0px;padding:0px;border:1px solid #C0C0C0;">
			
			<tbody style="margin:0px;padding:0px;">
				
				<tr style="margin:0px;padding:0px;">
					
					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						
						<p style="margin-right:5px;margin-left:5px;padding-top:0px;padding-bottom:0px;line-height:21px;">
							<span style="margin:0px;padding:0px;font-size:10pt;"><code style="margin:0px;padding:0px;">sed&nbsp;<span style="margin:0px;padding:0px;color:#FF00FF;">'/My/r introduce.txt'</span>&nbsp;datafile
#如果在文件datafile的某一行匹配到模式My，就在该行后读入文件introduce<span style="margin:0px;padding:0px;color:#0000CC;">.</span>txt的内容。如果出现My的行不止一行，则在出现My的各行后都读入introduce<span style="margin:0px;padding:0px;color:#0000CC;">.</span>txt文件的内容。</code></span>
						</p>

					</td>

				</tr>

			</tbody>

		</table>

		<div style="margin:0px;padding:0px;">
			&nbsp;
		</div>

		<div style="margin:0px;padding:0px;">
			<span style="margin:0px;padding:0px;">6.6 w命令</span>
		</div>

		<table cellspacing="0" cellpadding="0" width="95%" bgcolor="#f1f1f1" border="1" style="margin:0px;padding:0px;border:1px solid #C0C0C0;">
			
			<tbody style="margin:0px;padding:0px;">
				
				<tr style="margin:0px;padding:0px;">
					
					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						
						<p style="margin-right:5px;margin-left:5px;padding-top:0px;padding-bottom:0px;line-height:21px;">
							<span style="margin:0px;padding:0px;font-size:10pt;"><code style="margin:0px;padding:0px;">sed&nbsp;<span style="margin:0px;padding:0px;color:#0000CC;">-</span>n&nbsp;<span style="margin:0px;padding:0px;color:#FF00FF;">'/hrwang/w me.txt'</span>&nbsp;datafile </code></span>
						</p>

					</td>

				</tr>

			</tbody>

		</table>

		<p style="margin:10px auto;padding-top:0px;padding-bottom:0px;">
			<span style="margin:0px;padding:0px;">&nbsp;</span>
		</p>

		<p style="margin:10px auto;padding-top:0px;padding-bottom:0px;">
			<span style="margin:0px;padding:0px;">6.7 a\ 命令</span>
		</p>

		<p style="margin:10px auto;padding-top:0px;padding-bottom:0px;">
			a\ 命令是追加命令，追加将添加新文本到文件中当前行（即读入模式缓冲区中的行）的后面。所追加的文本行位于sed命令的下方另起一行。如果要追加的内容超过一行，则每一行都必须以反斜线结束，最后一行除外。最后一行将以引号和文件名结束。
		</p>

		<table cellspacing="0" cellpadding="0" width="95%" bgcolor="#f1f1f1" border="1" style="margin:0px;padding:0px;border:1px solid #C0C0C0;">
			
			<tbody style="margin:0px;padding:0px;">
				
				<tr style="margin:0px;padding:0px;">
					
					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						
						<p style="margin-right:5px;margin-left:5px;padding-top:0px;padding-bottom:0px;line-height:21px;">
							<span style="margin:0px;padding:0px;font-size:10pt;"><code style="margin:0px;padding:0px;">sed&nbsp;<span style="margin:0px;padding:0px;color:#FF00FF;">'/^hrwang/a\
&gt;hrwang and mjfan are husband\
&gt;and wife'</span>&nbsp;datafile
#如果在datafile文件中发现匹配以hrwang开头的行，则在该行下面追加hrwang and mjfan are husband and wife</code></span>
						</p>

					</td>

				</tr>

			</tbody>

		</table>

		<p style="margin:10px auto;padding-top:0px;padding-bottom:0px;">
			<span style="margin:0px;padding:0px;">&nbsp;</span>
		</p>

		<p style="margin:10px auto;padding-top:0px;padding-bottom:0px;">
			<span style="margin:0px;padding:0px;">6.8 i\ 命令</span>
		</p>

		<p style="margin:10px auto;padding-top:0px;padding-bottom:0px;">
			i\ 命令是在当前行的前面插入新的文本。
		</p>

		<p style="margin:10px auto;padding-top:0px;padding-bottom:0px;">
			<span style="margin:0px;padding:0px;">&nbsp;</span>
		</p>

		<p style="margin:10px auto;padding-top:0px;padding-bottom:0px;">
			<span style="margin:0px;padding:0px;">6.9 c\ 命令</span>
		</p>

		<p style="margin:10px auto;padding-top:0px;padding-bottom:0px;">
			sed使用该命令将已有文本修改成新的文本。
		</p>

		<p style="margin:10px auto;padding-top:0px;padding-bottom:0px;">
			<span style="margin:0px;padding:0px;">&nbsp;</span>
		</p>

		<p style="margin:10px auto;padding-top:0px;padding-bottom:0px;">
			<span style="margin:0px;padding:0px;">6.10 n命令</span>
		</p>

		<p style="margin:10px auto;padding-top:0px;padding-bottom:0px;">
			sed使用该命令获取输入文件的下一行，并将其读入到模式缓冲区中，任何sed命令都将应用到匹配行紧接着的下一行上。
		</p>

		<div style="margin:0px;padding:0px;">
			
		</div>

		<table cellspacing="0" cellpadding="0" width="95%" bgcolor="#f1f1f1" border="1" style="margin:0px;padding:0px;border:1px solid #C0C0C0;">
			
			<tbody style="margin:0px;padding:0px;">
				
				<tr style="margin:0px;padding:0px;">
					
					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						
						<p style="margin-right:5px;margin-left:5px;padding-top:0px;padding-bottom:0px;line-height:21px;">
							<code style="margin:0px;padding:0px;"><span style="margin:0px;padding:0px;font-size:10pt;">sed&nbsp;<span style="margin:0px;padding:0px;color:#FF00FF;">'/hrwang/{n;s/My/Your/;}'</span>&nbsp;datafile</span> </code>
						</p>

					</td>

				</tr>

			</tbody>

		</table>

		<div style="margin:0px;padding:0px;">
			<span style="margin:0px;padding:0px;color:#339999;">注：如果需要使用多条命令，或者需要在某个地址范围内嵌套地址，就必须用花括号将命令括起来，每行只写一条命令，或这用分号分割同一行中的多条命令。</span>
		</div>

		<div style="margin:0px;padding:0px;">
			&nbsp;
		</div>

		<div style="margin:0px;padding:0px;">
			<span style="margin:0px;padding:0px;">6.11 y命令</span>
		</div>

		<div style="margin:0px;padding:0px;">
			该命令与UNIX/Linux中的tr命令类似，字符按照一对一的方式从左到右进行转换。例如，y/abc/ABC/将把所有小写的a转换成A，小写的b转换成B，小写的c转换成C。
		</div>

		<div style="margin:0px;padding:0px;">
			&nbsp;
		</div>

		<table cellspacing="0" cellpadding="0" width="95%" bgcolor="#f1f1f1" border="1" style="margin:0px;padding:0px;border:1px solid #C0C0C0;">
			
			<tbody style="margin:0px;padding:0px;">
				
				<tr style="margin:0px;padding:0px;">
					
					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						
						<p style="margin-right:5px;margin-left:5px;padding-top:0px;padding-bottom:0px;line-height:21px;">
							<span style="margin:0px;padding:0px;font-size:10pt;"><code style="margin:0px;padding:0px;">sed&nbsp;<span style="margin:0px;padding:0px;color:#FF00FF;">'1,20y/hrwang12/HRWANG^$/'</span>&nbsp;datafile
#将1到20行内，所有的小写hrwang转换成大写，将1转换成^<span style="margin:0px;padding:0px;color:#0000CC;">,</span>将2转换成<span style="margin:0px;padding:0px;color:#0000FF;">$</span><span style="margin:0px;padding:0px;color:#008080;">。</span> #正则表达式元字符对y命令不起作用。与s命令的分隔符一样，斜线可以被替换成其它的字符。</code></span>
						</p>

					</td>

				</tr>

			</tbody>

		</table>

		<p style="margin:10px auto;padding-top:0px;padding-bottom:0px;">
			<span style="margin:0px;padding:0px;">&nbsp;</span>
		</p>

		<p style="margin:10px auto;padding-top:0px;padding-bottom:0px;">
			<span style="margin:0px;padding:0px;">6.12 q命令</span>
		</p>

		<p style="margin:10px auto;padding-top:0px;padding-bottom:0px;">
			q命令将导致sed程序退出，不再进行其它的处理。
		</p>

		<table cellspacing="0" cellpadding="0" width="95%" bgcolor="#f1f1f1" border="1" style="margin:0px;padding:0px;border:1px solid #C0C0C0;">
			
			<tbody style="margin:0px;padding:0px;">
				
				<tr style="margin:0px;padding:0px;">
					
					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						
						<p style="margin-right:5px;margin-left:5px;padding-top:0px;padding-bottom:0px;line-height:21px;">
							<code style="margin:0px;padding:0px;"><span style="margin:0px;padding:0px;font-size:10pt;">sed&nbsp;<span style="margin:0px;padding:0px;color:#FF00FF;">'/hrwang/{s/hrwang/HRWANG/;q;}'</span>&nbsp;datafile</span> </code>
						</p>

					</td>

				</tr>

			</tbody>

		</table>

		<p style="margin:10px auto;padding-top:0px;padding-bottom:0px;">
			<span style="margin:0px;padding:0px;">&nbsp;</span>
		</p>

		<p style="margin:10px auto;padding-top:0px;padding-bottom:0px;">
			<span style="margin:0px;padding:0px;">6.13 h命令和g命令</span>
		</p>

		<table cellspacing="0" cellpadding="0" width="95%" bgcolor="#f1f1f1" border="1" style="margin:0px;padding:0px;border:1px solid #C0C0C0;">
			
			<tbody style="margin:0px;padding:0px;">
				
				<tr style="margin:0px;padding:0px;">
					
					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						
						<p style="margin-right:5px;margin-left:5px;padding-top:0px;padding-bottom:0px;line-height:21px;">
							<span style="margin:0px;padding:0px;font-size:10pt;"><code style="margin:0px;padding:0px;">#cat datafile</code></span>
						</p>

						<p style="margin-right:5px;margin-left:5px;padding-top:0px;padding-bottom:0px;line-height:21px;">
							<span style="margin:0px;padding:0px;font-size:10pt;"><code style="margin:0px;padding:0px;">My name is hrwang.</code></span>
						</p>

						<p style="margin-right:5px;margin-left:5px;padding-top:0px;padding-bottom:0px;line-height:21px;">
							<span style="margin:0px;padding:0px;font-size:10pt;"><code style="margin:0px;padding:0px;">Your name is mjfan.</code></span>
						</p>

						<p style="margin-right:5px;margin-left:5px;padding-top:0px;padding-bottom:0px;line-height:21px;">
							<span style="margin:0px;padding:0px;font-size:10pt;"><code style="margin:0px;padding:0px;">hrwang is mjfan's husband.</code></span>
						</p>

						<p style="margin-right:5px;margin-left:5px;padding-top:0px;padding-bottom:0px;line-height:21px;">
							<span style="margin:0px;padding:0px;font-size:10pt;"><code style="margin:0px;padding:0px;">mjfan is hrwang's wife.</code></span>
						</p>

						<p style="margin-right:5px;margin-left:5px;padding-top:0px;padding-bottom:0px;line-height:21px;">
							<span style="margin:0px;padding:0px;font-size:10pt;"><code style="margin:0px;padding:0px;"><span style="margin:0px;padding:0px;">&nbsp;</span></code>&nbsp;</span>
						</p>

						<p style="margin-right:5px;margin-left:5px;padding-top:0px;padding-bottom:0px;line-height:21px;">
							<span style="margin:0px;padding:0px;font-size:10pt;"><code style="margin:0px;padding:0px;">sed&nbsp;<span style="margin:0px;padding:0px;color:#0000CC;">-</span>e&nbsp;<span style="margin:0px;padding:0px;color:#FF00FF;">'/hrwang/h'</span>&nbsp;<span style="margin:0px;padding:0px;color:#0000CC;">-</span>e&nbsp;<span style="margin:0px;padding:0px;color:#FF00FF;">'$G'</span>&nbsp;datafile</code></span>
						</p>

						<p style="margin-right:5px;margin-left:5px;padding-top:0px;padding-bottom:0px;line-height:21px;">
							<span style="margin:0px;padding:0px;font-size:10pt;"><code style="margin:0px;padding:0px;">sed -e '/hrwang/H' -e '$G' datafile</code></span>
						</p>

						<p style="margin-right:5px;margin-left:5px;padding-top:0px;padding-bottom:0px;line-height:21px;">
							<span style="margin:0px;padding:0px;font-size:10pt;"><code style="margin:0px;padding:0px;">#通过上面两条命令，你会发现h会把原来暂存缓冲区的内容清除，只保存最近一次执行h时保存进去的模式空间的内容。而H命令则把每次匹配hrwnag的行都追加保存在暂存缓冲区。 </code></span>
						</p>

						<p style="margin-right:5px;margin-left:5px;padding-top:0px;padding-bottom:0px;line-height:21px;">
							<span style="margin:0px;padding:0px;font-size:10pt;"><code style="margin:0px;padding:0px;">sed -e '/hrwang/H' -e '$g' datafile</code></span>
						</p>

						<p style="margin-right:5px;margin-left:5px;padding-top:0px;padding-bottom:0px;line-height:21px;">
							<span style="margin:0px;padding:0px;font-size:10pt;"><code style="margin:0px;padding:0px;">sed -e '/hrwang/H' -e '$G' datafile</code></span>
						</p>

						<p style="margin-right:5px;margin-left:5px;padding-top:0px;padding-bottom:0px;line-height:21px;">
							<span style="margin:0px;padding:0px;font-size:10pt;"><code style="margin:0px;padding:0px;">#通过上面两条命令，你会发现g把暂存缓冲区中的内容替换掉了模式空间中当前行的内容，此处即替换了最后一行。而G命令则把暂存缓冲区的内容追加到了模式空间的当前行后。此处即追加到了末尾。</code></span>
						</p>

					</td>

				</tr>

			</tbody>

		</table>

		<p style="margin:10px auto;padding-top:0px;padding-bottom:0px;">
			<span style="margin:0px;padding:0px;font-size:12pt;">&nbsp;</span>
		</p>

		<p style="margin:10px auto;padding-top:0px;padding-bottom:0px;">
			<span style="margin:0px;padding:0px;font-size:12pt;">&nbsp;</span>
		</p>

		<p style="margin:10px auto;padding-top:0px;padding-bottom:0px;">
			<span style="margin:0px;padding:0px;font-size:12pt;">7. sed脚本</span>
		</p>

		<p style="margin:10px auto;padding-top:0px;padding-bottom:0px;">
			sed脚本就是写在文件中的一列sed命令。脚本中，要求命令的末尾不能有任何多余的空格或文本。如果在一行中有多个命令，要用分号分隔。执行脚本时，sed先将输入文件中第一行复制到模式缓冲区，然后对其执行脚本中所有的命令。每一行处理完毕后，sed再复制文件中下一行到模式缓冲区，对其执行脚本中所有命令。使用sed脚本时，不再用引号来确保sed命令不被shell解释。例如sed脚本script：
		</p>

		<table cellspacing="0" cellpadding="0" width="95%" bgcolor="#f1f1f1" border="1" style="margin:0px;padding:0px;border:1px solid #C0C0C0;">
			
			<tbody style="margin:0px;padding:0px;">
				
				<tr style="margin:0px;padding:0px;">
					
					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						
						<p style="margin-right:5px;margin-left:5px;padding-top:0px;padding-bottom:0px;line-height:21px;">
							<span style="margin:0px;padding:0px;font-size:10pt;"><code style="margin:0px;padding:0px;"><span style="margin:0px;padding:0px;"><span style="margin:0px;padding:0px;color:#FF9900;">#handle datafile</span> 3i\ <span style="margin:0px;padding:0px;color:#0000CC;">~</span><span style="margin:0px;padding:0px;color:#0000CC;">~</span><span style="margin:0px;padding:0px;color:#0000CC;">~</span><span style="margin:0px;padding:0px;color:#0000CC;">~</span><span style="margin:0px;padding:0px;color:#0000CC;">~</span><span style="margin:0px;padding:0px;color:#0000CC;">~</span><span style="margin:0px;padding:0px;color:#0000CC;">~</span><span style="margin:0px;padding:0px;color:#0000CC;">~</span><span style="margin:0px;padding:0px;color:#0000CC;">~</span><span style="margin:0px;padding:0px;color:#0000CC;">~</span><span style="margin:0px;padding:0px;color:#0000CC;">~</span><span style="margin:0px;padding:0px;color:#0000CC;">~</span><span style="margin:0px;padding:0px;color:#0000CC;">~</span><span style="margin:0px;padding:0px;color:#0000CC;">~</span><span style="margin:0px;padding:0px;color:#0000CC;">~</span><span style="margin:0px;padding:0px;color:#0000CC;">~</span><span style="margin:0px;padding:0px;color:#0000CC;">~</span><span style="margin:0px;padding:0px;color:#0000CC;">~</span><span style="margin:0px;padding:0px;color:#0000CC;">~</span><span style="margin:0px;padding:0px;color:#0000CC;">~</span><span style="margin:0px;padding:0px;color:#0000CC;">~</span> 3<span style="margin:0px;padding:0px;color:#0000CC;">,</span><span style="margin:0px;padding:0px;color:#0000FF;">$</span><span style="margin:0px;padding:0px;color:#008080;">s</span><span style="margin:0px;padding:0px;color:#0000CC;">/</span><span style="margin:0px;padding:0px;color:#0000CC;">\</span><span style="margin:0px;padding:0px;color:#0000CC;">(</span>hrwang\<span style="margin:0px;padding:0px;color:#0000CC;">)</span>&nbsp;is</span></code><code style="margin:0px;padding:0px;"><span style="margin:0px;padding:0px;">&nbsp;\<span style="margin:0px;padding:0px;color:#0000CC;">(</span>mjfan\<span style="margin:0px;padding:0px;color:#0000CC;">)</span><span style="margin:0px;padding:0px;color:#0000CC;">/</span><span style="margin:0px;padding:0px;color:#0000CC;">\</span>2 is \1<span style="margin:0px;padding:0px;color:#0000CC;">/</span></span></code><code style="margin:0px;padding:0px;"><span style="margin:0px;padding:0px;"> <span style="margin:0px;padding:0px;color:#0000FF;">$</span><span style="margin:0px;padding:0px;color:#008080;">a</span><span style="margin:0px;padding:0px;color:#008080;">\</span> We will love eachother&nbsp;<span style="margin:0px;padding:0px;color:#0000FF;">for</span>ever！！</span></code><code style="margin:0px;padding:0px;"><span style="margin:0px;padding:0px;">&nbsp;</span></code></span>
						</p>
&nbsp;
					</td>

				</tr>

			</tbody>

		</table>

		<p style="margin:10px auto;padding-top:0px;padding-bottom:0px;">
			&nbsp;
		</p>

		<div style="margin:0px;padding:0px;">
			
		</div>

		<table cellspacing="0" cellpadding="0" width="95%" bgcolor="#f1f1f1" border="1" style="margin:0px;padding:0px;border:1px solid #C0C0C0;">
			
			<tbody style="margin:0px;padding:0px;">
				
				<tr style="margin:0px;padding:0px;">
					
					<td style="margin:0px;padding:3px;border:1px solid #C0C0C0;border-collapse:collapse;word-break:normal !important;">
						
						<p style="margin-right:5px;margin-left:5px;padding-top:0px;padding-bottom:0px;line-height:21px;">
							<span style="margin:0px;padding:0px;font-size:10pt;"><code style="margin:0px;padding:0px;"><span style="margin:0px;padding:0px;color:#FF9900;">#sed -f script datafile</span> <span style="margin:0px;padding:0px;"><span style="margin:0px;padding:0px;color:#0000FF;">My</span>&nbsp;</span>name is hrwang
Your name is mjfan <span style="margin:0px;padding:0px;color:#0000CC;">~</span><span style="margin:0px;padding:0px;color:#0000CC;">~</span><span style="margin:0px;padding:0px;color:#0000CC;">~</span><span style="margin:0px;padding:0px;color:#0000CC;">~</span><span style="margin:0px;padding:0px;color:#0000CC;">~</span><span style="margin:0px;padding:0px;color:#0000CC;">~</span><span style="margin:0px;padding:0px;color:#0000CC;">~</span><span style="margin:0px;padding:0px;color:#0000CC;">~</span><span style="margin:0px;padding:0px;color:#0000CC;">~</span><span style="margin:0px;padding:0px;color:#0000CC;">~</span><span style="margin:0px;padding:0px;color:#0000CC;">~</span><span style="margin:0px;padding:0px;color:#0000CC;">~</span><span style="margin:0px;padding:0px;color:#0000CC;">~</span><span style="margin:0px;padding:0px;color:#0000CC;">~</span><span style="margin:0px;padding:0px;color:#0000CC;">~</span><span style="margin:0px;padding:0px;color:#0000CC;">~</span><span style="margin:0px;padding:0px;color:#0000CC;">~</span><span style="margin:0px;padding:0px;color:#0000CC;">~</span><span style="margin:0px;padding:0px;color:#0000CC;">~</span><span style="margin:0px;padding:0px;color:#0000CC;">~</span><span style="margin:0px;padding:0px;color:#0000CC;">~</span> mjfan is hrwang<span style="margin:0px;padding:0px;color:#FF00FF;"><span style="margin:0px;padding:0px;color:#000000;">'s&nbsp;</span><span style="margin:0px;padding:0px;color:#000000;">husband</span>.&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ＃啦啦～～～ <span style="margin:0px;padding:0px;color:#000000;">mjfan is hrwang'</span></span><span style="margin:0px;padding:0px;">s wife<span style="margin:0px;padding:0px;color:#0000CC;">.</span> </span>We will love eachother forever！！</code></span>
						</p>

					</td>

				</tr>

			</tbody>

		</table>

	</div>

</p>
</pre>