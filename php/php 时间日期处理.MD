<div style="white-space:nowrap;">
<pre class="prettyprint lang-php linenums">&lt;?php   
     date("Y-m-d H:i:s")

echo strtotime(date("Y-m-d")); //时间戳

  $today=date("Y-m-d H:i:s"); 
 
     $todays=date("Y-m-d",strtotime('+1 day'));//明天

     $Lstart=date("Ym01",strtotime("$create_time -1 month")); //上个月第一天
 
 $Lend=date("Ymd",strtotime("$Lstart +1 month -1 day"));//本月最后一天

     $today=strtotime($today);
     $todays=strtotime($todays);



date_default_timezone_set('PRC'); //默认时区     
echo "今天:",date("Y-m-d",time()),"&lt;br&gt;";     
echo "今天:",date("Y-m-d",strtotime("18 june 2008")),"&lt;br&gt;";     
echo "昨天:",date("Y-m-d",strtotime("-1 day")), "&lt;br&gt;";     
echo "明天:",date("Y-m-d",strtotime("+1 day")), "&lt;br&gt;";     
echo "一周后:",date("Y-m-d",strtotime("+1 week")), "&lt;br&gt;";     
echo "一周零两天四小时两秒后:",date("Y-m-d G:H:s",strtotime("+1 week 2 days 4 hours 2 seconds")), "&lt;br&gt;";     
echo "下个星期四:",date("Y-m-d",strtotime("next Thursday")), "&lt;br&gt;";     
echo "上个周一:".date("Y-m-d",strtotime("last Monday"))."&lt;br&gt;";     
echo "一个月前:".date("Y-m-d",strtotime("last month"))."&lt;br&gt;";     
echo "一个月后:".date("Y-m-d",strtotime("+1 month"))."&lt;br&gt;";     
echo "十年后:".date("Y-m-d",strtotime("+10 year"))."&lt;br&gt;";   


function getthemonth($date) 
{ 
$firstday = date('Y-m-01', strtotime($date)); 
$lastday = date('Y-m-d', strtotime("$firstday +1 month -1 day")); 
return array($firstday, $lastday); 
} 
</pre>
<br />
</div>
<p>
	<br />
</p>