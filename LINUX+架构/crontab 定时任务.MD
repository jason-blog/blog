Crontab<br />
<br />
配置文件<br />
<br />
etc/crontab<br />
<br />
服务名 crond<br />
<br />
Service crond status<br />
<br />
<br />
<br />
<br />
SHELL=/bin/bash<br />
PATH=/sbin:/bin:/usr/sbin:/usr/bin<br />
MAILTO=root<br />
HOME=/<br />
<br />
# For details see man 4 crontabs<br />
<br />
# Example of job definition:<br />
# .---------------- minute (0 - 59)<br />
# | &nbsp;.------------- hour (0 - 23)<br />
# | &nbsp;| &nbsp;.---------- day of month (1 - 31)<br />
# | &nbsp;| &nbsp;| &nbsp;.------- month (1 - 12) OR jan,feb,mar,apr ...<br />
# | &nbsp;| &nbsp;| &nbsp;| &nbsp;.---- day of week (0 - 6) (Sunday=0 or 7) OR sun,mon,tue,wed,thu,fri,sat<br />
# | &nbsp;| &nbsp;| &nbsp;| &nbsp;|<br />
# * &nbsp;* &nbsp;* &nbsp;* &nbsp;* user-name command to be executed<br />
&nbsp; */5 &nbsp;* &nbsp;* &nbsp;* &nbsp;* root /usr/local/php/bin/php /home/wwwroot/index.php<br />
&nbsp;&nbsp;<br />
&nbsp;&nbsp;<br />
&nbsp;&nbsp;<br />
“*”字符被用来指定所有的值。如：”*“在分钟的字段域里表示“每分钟”。&nbsp;<br />
<br />
<br />
“-”字符被用来指定一个范围。如：“10-12”在小时域意味着“10点、11点、12点”。<br />
<br />
“,”字符被用来指定另外的值。如：“MON,WED,FRI”在星期域里表示”星期一、星期三、星期五”.&nbsp;<br />
<br />
“/” 没几分钟执行一次<br />
<br />
<br />
<br />
cronExpression<br />
<br />
"0 0 12 * * ?"	 	每天中午12点触发<br />
"0 15 10 ? * *"	 	每天上午10:15触发<br />
"0 15 10 * * ?"	 	每天上午10:15触发<br />
"0 15 10 * * ? *"	 	每天上午10:15触发<br />
"0 15 10 * * ? 2005"	 	2005年的每天上午10:15触发<br />
"0 * 14 * * ?"	 	在每天下午2点到下午2:59期间的每1分钟触发<br />
"0 0/5 14 * * ?"	 	在每天下午2点到下午2:55期间的每5分钟触发<br />
"0 0/5 14,18 * * ?"	 	在每天下午2点到2:55期间和下午6点到6:55期间的每5分钟触发<br />
"0 0-5 14 * * ?"	 	在每天下午2点到下午2:05期间的每1分钟触发<br />
"0 10,44 14 ? 3 WED"	 	每年三月的星期三的下午2:10和2:44触发<br />
"0 15 10 ? * MON-FRI"	 	周一至周五的上午10:15触发<br />
"0 15 10 15 * ?"	 	每月15日上午10:15触发<br />
"0 15 10 L * ?"	 	每月最后一日的上午10:15触发<br />
"0 15 10 ? * 6L"	 	每月的最后一个星期五上午10:15触发&nbsp;<br />
"0 15 10 ? * 6L 2002-2005"	 	2002年至2005年的每月的最后一个星期五上午10:15触发<br />
"0 15 10 ? * 6#3"	 	每月的第三个星期五上午10:15触发<br />
<br />
&nbsp;&nbsp;<br />
&nbsp;&nbsp;<br />
&nbsp;&nbsp;<br />
<div style="white-space:nowrap;">
	<br />
</div>