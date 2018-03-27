&lt;?php&nbsp;<br />
<br />
//////////测试php性能的代码////////<br />
<br />
&nbsp; &nbsp;$list=array();<br />
&nbsp; &nbsp;for($i=0;$i&lt;10000;$i++){<br />
&nbsp; &nbsp; &nbsp; &nbsp;$list[]=$i;<br />
&nbsp; &nbsp;}<br />
<br />
&nbsp; echo $sM=memory_get_usage(); echo '&lt;br&gt;';<br />
&nbsp; $stime = microtime(true);<br />
&nbsp;<br />
&nbsp; $r=serialize($list);<br />
&nbsp; $etime = microtime(true);<br />
&nbsp; echo &nbsp;$eM=memory_get_usage();<br />
&nbsp;&nbsp;<br />
&nbsp;&nbsp;<br />
&nbsp; echo "unserialize :", ($etime - $stime),'&lt;br/&gt;';<br />
&nbsp; echo "unserialize momory :", ($eM - $sM)/1024,'&lt;br/&gt;';<br />
&nbsp;&nbsp;<br />
&nbsp; &nbsp;//////////////////////////////////////////////////////////////<br />
&nbsp; $sM=memory_get_usage();<br />
&nbsp; $stime = microtime(true);<br />
&nbsp;&nbsp;<br />
&nbsp; $r=unserialize($r);<br />
&nbsp;&nbsp;<br />
&nbsp; $etime = microtime(true);<br />
&nbsp; $eM=memory_get_usage();<br />
&nbsp;// echo "serialize :", ($etime - $stime) ,'&lt;br/&gt;';<br />
&nbsp;// echo "serialize momory :", ($eM - $sM)/1024,'&lt;br/&gt;';<br />
&nbsp;&nbsp;<br />
&nbsp;&nbsp;file_put_contents("./test.log",&nbsp; "times :". ($etime - $stime).'&lt;br/&gt;' ."momory :". (($eM - $sM)/1024 )."\n" ,FILE_APPEND );<br />
&nbsp;&nbsp;<br />
&nbsp; &nbsp;//////////////////////////////////////////////////////////////<br />
&nbsp;&nbsp;<br />
&nbsp;&nbsp;<br />
&nbsp; ////////////////////////////////////////////////<br />
&nbsp;&nbsp;<br />
&nbsp; &nbsp; $sM=memory_get_usage();<br />
&nbsp;&nbsp;<br />
&nbsp;&nbsp;<br />
&nbsp; &nbsp; $eM=memory_get_usage();<br />
&nbsp;&nbsp;<br />
&nbsp;&nbsp;<br />
&nbsp; echo ($eM - $sM)/1024,'&lt;br/&gt;';<br />
&nbsp;&nbsp;<br />
&nbsp; ////////////////////////////////////////////////<br />
&nbsp;&nbsp;<br />
&nbsp;&nbsp;<br />
&nbsp;&nbsp;<br />
&nbsp;&nbsp;<br />
&nbsp; &nbsp; ////////////////////////////////////////////////<br />
&nbsp;&nbsp;<br />
&nbsp; $stime = microtime(true);<br />
<br />
&nbsp;&nbsp;<br />
&nbsp;&nbsp;<br />
&nbsp; $etime = microtime(true);<br />
&nbsp; echo &nbsp;$etime - $stime;<br />
&nbsp;&nbsp;<br />
&nbsp; &nbsp; ////////////////////////////////////////////////<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
//////////////////////////////////////////////////<br />
<br />
&nbsp; &nbsp;declare(ticks=1);<br />
&nbsp; &nbsp;$tics_stime = microtime(true);<br />
&nbsp; &nbsp;$tics_sM=memory_get_usage();<br />
&nbsp; &nbsp;$tics_dlimit=0.009;<br />
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
&nbsp; &nbsp; &nbsp; &nbsp;$debug="&amp;nbsp; File: ".$ticks_bt[0]['file']." Line: ".$ticks_bt[0]['line'];<br />
&nbsp; &nbsp; &nbsp; &nbsp;$tics_console="&amp;nbsp;&lt;font color='red'&gt;---&gt;&lt;/font&gt;&amp;nbspMem: ".$tics_limitMem." TIMES: ". $tics_limitTime."s";<br />
&nbsp; &nbsp; &nbsp; &nbsp;if($tics_limitTime&gt;tics_dlimit):<br />
&nbsp; &nbsp; &nbsp; &nbsp;$tics_console.= '&amp;nbspExecute:&lt;font color="red"&gt; Timeout:'. $tics_c++.'&lt;/font&gt;'.$debug.'&lt;br/&gt;';<br />
&nbsp; &nbsp; &nbsp; &nbsp;$tics_hight=1;<br />
&nbsp; &nbsp; &nbsp; &nbsp;else:<br />
&nbsp; &nbsp; &nbsp; &nbsp;$tics_console.= '&amp;nbspExecute:&lt;font color="#3eaf1b"&gt;'. $tics_c++.'&lt;/font&gt;'.$debug.'&lt;br/&gt;';<br />
&nbsp; &nbsp; &nbsp; &nbsp;endif;<br />
&nbsp; &nbsp; &nbsp; &nbsp;if($tics_hight&gt;0)echo $tics_console;<br />
&nbsp; &nbsp; &nbsp; &nbsp;// &nbsp;if($tics_c&gt;1)echo $tics_console;<br />
&nbsp; &nbsp;}<br />
&nbsp; &nbsp;register_tick_function('ticks_checkTimeout');<br />
&nbsp; &nbsp;<br />
<br />
/////////////////////////////////////////////////////////////////////<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
?&gt;<br />
<br />
<br />
<br />