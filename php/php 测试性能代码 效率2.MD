<br />
&nbsp;/**<br />
&nbsp; &nbsp; * $tics_hight 是否启用时间限制<br />
&nbsp; &nbsp; * $tics_dlimit 设置时间<br />
&nbsp; &nbsp; */<br />
&nbsp; &nbsp;declare(ticks=1);<br />
&nbsp; &nbsp;$tics_stime = microtime(true);<br />
&nbsp; &nbsp;$tics_sM=memory_get_usage();<br />
&nbsp; &nbsp;<br />
&nbsp; &nbsp;//设置执行多久打印<br />
&nbsp; &nbsp;$tics_dlimit=0.009;<br />
&nbsp; &nbsp;<br />
&nbsp; &nbsp;define('tics_sM', $tics_sM);<br />
&nbsp; &nbsp;define('tics_dlimit', $tics_dlimit);<br />
&nbsp; &nbsp;define('tics_stime', $tics_stime);<br />
&nbsp; &nbsp;$GLOBALS['tics_Times']=0;<br />
&nbsp; &nbsp;function ticks_checkTimeout(){<br />
&nbsp; &nbsp; &nbsp; &nbsp;static $tics_c=0,$tics_time=0,$tics_mem=0;<br />
&nbsp; &nbsp; &nbsp; &nbsp;$ticks_bt = debug_backtrace();<br />
&nbsp; &nbsp; &nbsp; &nbsp;$tics_hight=0;<br />
&nbsp; &nbsp; &nbsp; &nbsp;$tics_etime = microtime(true);<br />
&nbsp; &nbsp; &nbsp; &nbsp;$tics_eM=memory_get_usage();<br />
&nbsp; &nbsp; &nbsp; &nbsp;$tics_limitTime=($tics_etime - tics_stime - $tics_time);<br />
&nbsp; &nbsp; &nbsp; &nbsp;$tics_time=$tics_limitTime + $tics_time;<br />
&nbsp; &nbsp; &nbsp; &nbsp;$tics_limitMem=(($tics_eM - tics_sM - $tics_mem)/1024);<br />
&nbsp; &nbsp; &nbsp; &nbsp;$tics_mem=$tics_mem + $tics_limitMem;<br />
&nbsp; &nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp;$debug="&amp;nbsp; File: ".$ticks_bt[0]['file']." Line: ".$ticks_bt[0]['line'];<br />
&nbsp; &nbsp; &nbsp; &nbsp;$tics_console="&amp;nbsp;&lt;font color='red'&gt;---&gt;&lt;/font&gt;&amp;nbspMem: ".$tics_limitMem." TIMES: ". $tics_limitTime."s";<br />
&nbsp; &nbsp; &nbsp; &nbsp;if($tics_limitTime&gt;tics_dlimit):<br />
&nbsp; &nbsp; &nbsp; &nbsp;$tics_console.= '&amp;nbspExecute:&lt;font color="red"&gt; Timeout:'. $tics_c++.'&lt;/font&gt;'.$debug.'&lt;br/&gt; \n';<br />
&nbsp; &nbsp; &nbsp; &nbsp;$tics_hight=1;<br />
&nbsp; &nbsp; &nbsp; &nbsp;else:<br />
&nbsp; &nbsp; &nbsp; &nbsp;$tics_console.= '&amp;nbspExecute:&lt;font color="#3eaf1b"&gt;'. $tics_c++.'&lt;/font&gt;'.$debug.'&lt;br/&gt; \n';<br />
&nbsp; &nbsp; &nbsp; &nbsp;endif;<br />
&nbsp; &nbsp;<br />
&nbsp; &nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp;// if($tics_hight&gt;0)<br />
&nbsp; &nbsp; &nbsp; &nbsp;putTo($tics_console);<br />
&nbsp; &nbsp; &nbsp; &nbsp;// &nbsp;if($tics_c&gt;1)echo $tics_console;<br />
&nbsp; &nbsp; &nbsp; &nbsp;// &nbsp;file_put_contents('./serverDebug',$tics_console, FILE_APPEND);<br />
&nbsp; &nbsp;<br />
&nbsp; &nbsp;}<br />
&nbsp; &nbsp;<br />
&nbsp; &nbsp;function putTo($data){<br />
&nbsp; &nbsp; &nbsp; &nbsp;//echo $data;<br />
&nbsp; &nbsp; &nbsp; &nbsp;file_put_contents('./serverDebug',$data, FILE_APPEND);<br />
&nbsp; &nbsp;}<br />
&nbsp; &nbsp;<br />
&nbsp; &nbsp;putTo("&lt;br/&gt;\n =======================================================================&lt;br/&gt; \n");<br />
&nbsp; &nbsp;register_tick_function('ticks_checkTimeout');<br />
<br />