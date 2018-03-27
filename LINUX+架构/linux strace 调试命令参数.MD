<p>
	<span class="pln" style="font-family:Consolas, Menlo, Monaco, &quot;font-size:13.568px;white-space:pre;">strace </span><span class="pun" style="font-family:Consolas, Menlo, Monaco, &quot;font-size:13.568px;white-space:pre;">-</span><span class="pln" style="font-family:Consolas, Menlo, Monaco, &quot;font-size:13.568px;white-space:pre;">ttt </span><span class="pun" style="font-family:Consolas, Menlo, Monaco, &quot;font-size:13.568px;white-space:pre;">-</span><span class="pln" style="font-family:Consolas, Menlo, Monaco, &quot;font-size:13.568px;white-space:pre;">o log</span><span class="pun" style="font-family:Consolas, Menlo, Monaco, &quot;font-size:13.568px;white-space:pre;">.</span><span class="pln" style="font-family:Consolas, Menlo, Monaco, &quot;font-size:13.568px;white-space:pre;">txt php test</span><span class="pun" style="font-family:Consolas, Menlo, Monaco, &quot;font-size:13.568px;white-space:pre;">.</span><span class="pln" style="font-family:Consolas, Menlo, Monaco, &quot;font-size:13.568px;white-space:pre;">php </span>
</p>
<p>
	-c 统计每一系统调用的所执行的时间,次数和出错的次数等.&nbsp;
</p>
-d 输出strace关于标准错误的调试信息.&nbsp;<br />
-f 跟踪由fork调用所产生的子进程.&nbsp;<br />
-ff 如果提供-o filename,则所有进程的跟踪结果输出到相应的filename.pid中,pid是各进程的进程号.&nbsp;<br />
-F 尝试跟踪vfork调用.在-f时,vfork不被跟踪.&nbsp;<br />
-h 输出简要的帮助信息.&nbsp;<br />
-i 输出系统调用的入口指针.&nbsp;<br />
-q 禁止输出关于脱离的消息.&nbsp;<br />
-r 打印出相对时间关于,,每一个系统调用.&nbsp;<br />
-t 在输出中的每一行前加上时间信息.&nbsp;<br />
-tt 在输出中的每一行前加上时间信息,微秒级.&nbsp;<br />
-ttt 微秒级输出,以秒了表示时间.&nbsp;<br />
-T 显示每一调用所耗的时间.&nbsp;<br />
-v 输出所有的系统调用.一些调用关于环境变量,状态,输入输出等调用由于使用频繁,默认不输出.&nbsp;<br />
-V 输出strace的版本信息.&nbsp;<br />
-x 以十六进制形式输出非标准字符串&nbsp;<br />
-xx 所有字符串以十六进制形式输出.&nbsp;<br />
-a column&nbsp;<br />
设置返回值的输出位置.默认 为40.&nbsp;<br />
-e expr&nbsp;<br />
指定一个表达式,用来控制如何跟踪.格式如下:&nbsp;<br />
[qualifier=][!]value1[,value2]...&nbsp;<br />
qualifier只能是 trace,abbrev,verbose,raw,signal,read,write其中之一.value是用来限定的符号或数字.默认的 qualifier是 trace.感叹号是否定符号.例如:&nbsp;<br />
-eopen等价于 -e trace=open,表示只跟踪open调用.而-etrace!=open表示跟踪除了open以外的其他调用.有两个特殊的符号 all 和 none.&nbsp;<br />
注意有些shell使用!来执行历史记录里的命令,所以要使用\\.&nbsp;<br />
-e trace=set&nbsp;<br />
只跟踪指定的系统 调用.例如:-e trace=open,close,rean,write表示只跟踪这四个系统调用.默认的为set=all.&nbsp;<br />
-e trace=file&nbsp;<br />
只跟踪有关文件操作的系统调用.&nbsp;<br />
-e trace=process&nbsp;<br />
只跟踪有关进程控制的系统调用.&nbsp;<br />
-e trace=network&nbsp;<br />
跟踪与网络有关的所有系统调用.&nbsp;<br />
-e strace=signal&nbsp;<br />
跟踪所有与系统信号有关的 系统调用&nbsp;<br />
-e trace=ipc&nbsp;<br />
跟踪所有与进程通讯有关的系统调用&nbsp;<br />
-e abbrev=set&nbsp;<br />
设定 strace输出的系统调用的结果集.-v 等与 abbrev=none.默认为abbrev=all.&nbsp;<br />
-e raw=set&nbsp;<br />
将指 定的系统调用的参数以十六进制显示.&nbsp;<br />
-e signal=set&nbsp;<br />
指定跟踪的系统信号.默认为all.如 signal=!SIGIO(或者signal=!io),表示不跟踪SIGIO信号.&nbsp;<br />
-e read=set&nbsp;<br />
输出从指定文件中读出 的数据.例如:&nbsp;<br />
-e read=3,5&nbsp;<br />
-e write=set&nbsp;<br />
输出写入到指定文件中的数据.&nbsp;<br />
-o filename&nbsp;<br />
将strace的输出写入文件filename&nbsp;<br />
-p pid&nbsp;<br />
跟踪指定的进程pid.&nbsp;<br />
-s strsize&nbsp;<br />
指定输出的字符串的最大长度.默认为32.文件名一直全部输出.&nbsp;<br />
-u username&nbsp;<br />
以username 的UID和GID执行被跟踪的命令<br />