<pre class="prettyprint lang-js linenums">http://www.jb51.net/article/96604.htm
</pre>
<pre class="prettyprint lang-js linenums">#!/bin/sh
. /etc/profile
 
# 参数：
# args[0] ,数据日期,日期格式yyyy-MM-dd
# 取30天以前的日期
 
function get_date_30daysbefore()
{
 sec=`date -d $1 +%s`
 sec_30daysbefore=$((sec - 86400*30))
 days_before=`date -d @$sec_30daysbefore +%F`
 echo $days_before
}
 
if [ $# == 1 ]; then
 today=$1
 dates_30=`get_date_30daysbefore $1`
else
 today=`date -d -1days '+%Y-%m-%d'`
 dates_30=`date -d -30days '+%Y-%m-%d'`
fi
 
echo $today
echo $dates_30</pre>
<br />