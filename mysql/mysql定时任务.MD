查询已有定时任务<br />
<br />
select * from mysql.event &nbsp;<br />
<br />
////////////////////////////////////设置定时任务////////<br />
<br />
set time_zone = '+8:00'; &nbsp;<br />
set GLOBAL event_scheduler = 1; &nbsp;<br />
&nbsp;&nbsp;<br />
-- 设置该事件使用或所属的数据库base数据库 &nbsp;<br />
use game; &nbsp;<br />
&nbsp;&nbsp;<br />
# 如果原来存在该名字的任务计划则先删除 &nbsp;<br />
drop event if exists upload_to_sdmp; &nbsp;<br />
&nbsp;&nbsp;<br />
# 设置分隔符为 '$$' ，mysql默认的语句分隔符为 ';' ，这样在后续的 create 到 end 这段代码都会看成是一条语句来执行 &nbsp;<br />
DELIMITER $$ &nbsp;<br />
# 创建计划任务，设置第一次执行时间为'2014-07-30 10:00:00'，并且每天执行一次 &nbsp; on schedule every 30 second&nbsp;<br />
create event upload_to_sdmp &nbsp;&nbsp;<br />
on schedule every 1 day starts timestamp '2016-06-14 16:02:00' &nbsp;<br />
#on schedule every 1 SECOND &nbsp;<br />
do &nbsp;<br />
&nbsp;&nbsp;<br />
# 开始该计划任务要做的事 &nbsp;<br />
begin &nbsp;<br />
&nbsp;&nbsp;<br />
&nbsp;&nbsp;<br />
-- do something 编写你的计划任务要做的事 &nbsp;<br />
&nbsp; CALL telCrmGetDateOneDay('2016-06-13');<br />
&nbsp;&nbsp;<br />
&nbsp; CALL telCrmGetDateOneDay( CONCAT(date_sub(curdate(),interval 1 day) ) );<br />
&nbsp;&nbsp;<br />
-- 结束计划任务 &nbsp;<br />
end $$ &nbsp;<br />
DELIMITER ; &nbsp;<br />
<br />
<br />
<br />
///////////////////////////////////////////////////////////////<br />
<br />
<br />
////////////////////////////开启关闭事件////////////////////////////<br />
//关闭事件：<br />
ALTER EVENT upload_to_sdmp DISABLE; &nbsp;<br />
<br />
开启事件： &nbsp;<br />
ALTER EVENT upload_to_sdmp ENABLE; &nbsp; &nbsp;<br />
<br />
删除事件<br />
drop event if exists &nbsp;upload_to_sdmp;<br />
///////////////////////////////////////////////////////////////<br />
<br />
////////////////////////查询是否开启///////////////////<br />
<br />
SHOW VARIABLES LIKE 'event_scheduler';<br />
///////////////////////////////////////////////////////<br />
<br />
<br />
/////////////////////////////常用执行时间/////////////////////////<br />
--每隔一秒自动调用e_test()存储过程&nbsp;<br />
CREATE EVENT IF NOT EXISTS event_test&nbsp;<br />
ON SCHEDULE EVERY 1 SECOND&nbsp;<br />
ON COMPLETION PRESERVE&nbsp;<br />
<br />
从现在开始每隔九天定时执行&nbsp;<br />
CREATE EVENT EVENT1&nbsp;<br />
ON SCHEDULE EVERY 9 DAY STARTS NOW()&nbsp;<br />
ON COMPLETION PRESERVE ENABLE&nbsp;<br />
<br />
每个月的一号凌晨1 点执行&nbsp;<br />
CREATE EVENT EVENT2&nbsp;<br />
ON SCHEDULE EVERY 1 MONTH STARTS DATE_ADD(DATE_ADD(DATE_SUB(CURDATE(),INTERVAL DAY(CURDATE())-1 DAY), INTERVAL 1 MONTH),INTERVAL 1 HOUR)&nbsp;<br />
ON COMPLETION PRESERVE ENABLE&nbsp;<br />
<br />
<br />
每个季度一号的凌晨2点执行&nbsp;<br />
CREATE EVENT TOTAL_SEASON_EVENT&nbsp;<br />
ON SCHEDULE EVERY 1 QUARTER STARTS DATE_ADD(DATE_ADD(DATE( CONCAT(YEAR(CURDATE()),'-',ELT(QUARTER(CURDATE()),1,4,7,10),'-',1)),INTERVAL 1 QUARTER),INTERVAL 2 HOUR)&nbsp;<br />
ON COMPLETION PRESERVE ENABLE&nbsp;<br />
<br />
每年1月1号凌晨四点执行&nbsp;<br />
CREATE EVENT TOTAL_YEAR_EVENT&nbsp;<br />
ON SCHEDULE EVERY 1 YEAR STARTS DATE_ADD(DATE(CONCAT(YEAR(CURDATE()) + 1,'-',1,'-',1)),INTERVAL 4 HOUR)&nbsp;<br />
<br />
ON COMPLETION PRESERVE ENABLE&nbsp;<br />
<br />
<br />
/////////////////////////////////////////////////////////////////<br />
<br />
<br />
<br />
<br />
示例<br />
<br />
<p>
	<br />
</p>
<p>
<pre class="prettyprint lang-php linenums">set time_zone = '+8:00';  
#show variables like 'event_scheduler';
set GLOBAL event_scheduler = 1;  
 
#use '';  
  
drop event if exists EVENTNAME;  
  
DELIMITER $$  
create event EVENTNAME  
#设置第一次启动时间 之后每天执行一次
on schedule every 1 day starts timestamp '2016-06-14 00:30:00'  
do  
begin  
  CALL functiony( CONCAT(date_sub(curdate(),interval 1 day) ) );
end $$  
DELIMITER ;  </pre>
</p>
<br />