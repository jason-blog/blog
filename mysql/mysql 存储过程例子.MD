<pre class="prettyprint lang-php linenums">create procedure telCrmOpData(IN `limit_start` VARCHAR(30),IN `limit_end` VARCHAR(30))

BEGIN     
           DECLARE update_time VARCHAR(30);  
           DECLARE create_time VARCHAR(30);  
           DECLARE user_idF int;  
           DECLARE op_nameF VARCHAR(30); 
           DECLARE SQLSTRING VARCHAR(255); 
           DECLARE s int default 0;   
   #DECLARE CONTINUE HANDLER FOR SQLSTATE '02000' SET s=1;  
/*
  
create temporary table if not exists TmonthData
         (  
            `create_time` varchar(20) ,  
            `update_time` varchar(20),  
            `user_id` int(11) ,  
`op_name` varchar(50),  
             KEY `op_name` (`op_name`)
         );  
         truncate TABLE TmonthData;   

*/

      DROP TABLE IF EXISTS DataT;  
    CREATE TEMPORARY TABLE DataT(  
        `id` INT UNSIGNED NOT NULL AUTO_INCREMENT,  
        `create_time` VARCHAR(30) NOT NULL,  
        `update_time` VARCHAR(30) ,  
        `username`  VARCHAR(30) NOT NULL,  
        `op_name` VARCHAR(30) NOT NULL,
        `agenttype` INT(5),
        PRIMARY KEY (`id`)  
    )ENGINE=MyISAM DEFAULT CHARSET=utf8;  

    truncate TABLE DataT;    


     DROP TABLE IF EXISTS TmonthDataMoney;
CREATE TEMPORARY TABLE IF NOT EXISTS TmonthDataMoney
         (  
            `user_id` varchar(50) ,  
`is_first` int(5) ,  
            `countMoneyIn` int(5),
            `opprofit` double(10,2),
            `agentprofit` double(10,2),
`profit` double(10,2),
 `opmoneyIn` double(10,2),
 `agentmoneyIn` double(10,2),
 `moneyIn` double(10,2),
`moneyOut` double(10,2),
            `flowAgent` double(10,2),
            `flowOp` double(10,2),
`flowTotal` double(10,2),
`op_name` varchar(50),  
            `date` varchar(50),  
             KEY `op_name` (`op_name`)
         );  
         truncate TABLE TmonthDataMoney;   


   SET @tSql = CONCAT(' INSERT INTO DataT (`create_time`,`update_time`,`username`,`op_name`,`agenttype`)
 SELECT
L.create_time,
L.update_time,
  L.username,
  L.op_name,
CASE WHEN L.agent_name=L.op_agent_id THEN 1 ELSE 0 END AS agent 
FROM rfcorp_record_days as MM
INNER JOIN rfcorp_tel_crm_limit AS L ON L.username = MM.username
WHERE  MM.balance_date BETWEEN FROM_UNIXTIME(UNIX_TIMESTAMP("',limit_start,'"),"%Y%m%d") AND FROM_UNIXTIME(UNIX_TIMESTAMP("',limit_end,'"),"%Y%m%d")
AND (ISNULL(L.update_time) OR L.update_time="" OR L.update_time &gt;= UNIX_TIMESTAMP("',limit_start,'")) AND (L.create_time &lt;= UNIX_TIMESTAMP("',limit_end,'") )
GROUP BY
MM.username,L.id;');  

    PREPARE gatherData FROM @tSql;  
    EXECUTE gatherData;  
#SELECT @tSql;
#SELECT * FROM DataT;
    SELECT MIN(`id`) INTO @minCnt FROM DataT;  
    SELECT MAX(`id`) INTO @maxCnt FROM DataT; 
 #SELECT * FROM DataT;
 #SELECT @minCnt;

       WHILE @minCnt &lt;= @maxCnt DO 

     # SELECT create_time, update_time, user_id, op_name  INTO create_time, update_time, user_idF, op_nameF FROM DataT WHERE id = @minCnt;  
SET @DataTsql= CONCAT("SELECT create_time, update_time ,username ,agenttype,op_name INTO @create_time, @update_time,@username,@agenttype,@op_nameF FROM DataT WHERE id =", @minCnt,""); 
PREPARE DataTstmt FROM @DataTsql ;
EXECUTE DataTstmt ;

  #SELECT @DataTsql;
#SELECT @create_time, @update_time;

IF @update_time='' OR ISNULL(@update_time) then
SET @update_time=UNIX_TIMESTAMP();
END IF;
IF @create_time='' OR ISNULL(@create_time) then
SET @create_time=UNIX_TIMESTAMP();
END IF;

SET @SQLSTRING= CONCAT('SELECT
MM.username,
ROUND(SUM(CASE WHEN  MM.op_flag !=6 THEN  MM.real_bet+ MM.bonus_bet ELSE 0 END ),2) AS flow,
ROUND(SUM(CASE WHEN  MM.op_flag = 6 THEN  MM.result_money ELSE 0 END ),2) AS moneyIn,
ROUND(SUM(CASE WHEN  MM.op_flag = 6 THEN  MM.turnover_money ELSE 0 END ),2) AS moneyOut,
ROUND(SUM(CASE WHEN  MM.op_flag = 6 THEN  MM.result_money-MM.turnover_money ELSE 0 END ),2) AS profit,
MAX(CASE WHEN  MM.op_flag = 6 THEN  MM.real_win ELSE 0 END ) AS is_first,
MM.balance_date
INTO @Uid,@flow,@moneyIn,@moneyOut,@profit,@is_first,@date
FROM rfcorp_record_days as MM
WHERE  MM.balance_date BETWEEN FROM_UNIXTIME("',@create_time,'","%Y%m%d")
AND FROM_UNIXTIME("',@update_time,'","%Y%m%d" ) AND MM.balance_date BETWEEN FROM_UNIXTIME(UNIX_TIMESTAMP("',limit_start,'"),"%Y%m%d") AND FROM_UNIXTIME(UNIX_TIMESTAMP("',limit_end,'"),"%Y%m%d") 
AND MM.username="',@username,'"
GROUP BY
MM.username'); 
PREPARE stmt FROM @SQLSTRING ;
EXECUTE stmt ;

#SET s=0;
   #SELECT @SQLSTRING ;

      IF @Uid !=''  then
          SET @agentprofit=0;
   	SET @opprofit=@profit;
          SET @opmoneyIn=@moneyIn;
          SET @agentmoneyIn=0;
          SET @flowAgent=0;
          SET @flowOp=@flow;
         IF @agenttype =1 THEN
          SET @agentprofit=@profit;
   	SET @opprofit=0;
          SET @opmoneyIn=0;
          SET @agentmoneyIn=@moneyIn;
          SET @flowAgent=@flow;
          SET @flowOp=0;
          END IF;


insert into TmonthDataMoney (`user_id`,`is_first`,`opprofit`, `agentprofit`,`profit`,`opmoneyIn`,`agentmoneyIn`,`moneyIn`,`moneyOut`,`flowAgent`,`flowOp`,`flowTotal`,`op_name`,`date`)
      values(@Uid,@is_first,@opprofit,@agentprofit,@profit,@opmoneyIn,@agentmoneyIn,@moneyIn,@moneyOut,@flowAgent,@flowOp,@flow,@op_nameF,@date);  

      SET @Uid='';
      END IF;
  

   SET @create_time='';
SET @update_time='';
SET @username='';
SET @op_nameF='';
      SET @agenttype='';


      SET @minCnt = @minCnt + 1; 

      END WHILE;  

      #SELECT * FROM TmonthDataMoney;

SELECT
     `op_name`,
      SUM(`agentprofit`) AS agentProfit,
      SUM(`opprofit`) AS opProfit,
      SUM(`profit`) AS sumProfit,
SUM(`agentmoneyIn`) AS sumMoneyInAgent,
SUM(`opmoneyIn`) AS sumMoneyInOp,
SUM(`moneyIn`) AS sumMoneyIn,
      COUNT( `user_id` ) AS countMoneyIn,
COUNT(CASE WHEN is_first=1 THEN is_first END ) AS countIsfirst,
      SUM(`flowAgent`) AS flowAgent,
SUM(`flowOp`) AS flowOp,
SUM(`flowTotal`) AS flowTotal,
CONCAT(limit_start,'---',limit_end) AS `date`,
      UNIX_TIMESTAMP() AS create_time
FROM TmonthDataMoney GROUP BY op_name ORDER BY date,op_name ASC ;


/*
      INSERT INTO `rfcorp_tel_crm_statistics` ( `op_name`, `agentProfit`, `opProfit`, `sumProfit`, `sumMoneyInAgent`, `sumMoneyInOp`, 
      `sumMoneyIn`, `countMoneyIn`, `countIsfirst`, `flowAgent`, `flowOp`, `flowTotal`, `date`, `create_time`) 
      SELECT
     `op_name`,
      SUM(`agentprofit`) AS agentProfit,
      SUM(`opprofit`) AS opProfit,
      SUM(`profit`) AS sumProfit,
SUM(`agentmoneyIn`) AS sumMoneyInAgent,
SUM(`opmoneyIn`) AS sumMoneyInOp,
SUM(`moneyIn`) AS sumMoneyIn,

      COUNT(CASE WHEN `user_id` != '' THEN user_id END ) AS countMoneyIn,
COUNT(CASE WHEN is_first=1 THEN is_first END ) AS countIsfirst,

      SUM(`flowAgent`) AS flowAgent,
SUM(`flowOp`) AS flowOp,
SUM(`flowTotal`) AS flowTotal,
`date`,
      UNIX_TIMESTAMP()

FROM TmonthDataMoney GROUP BY op_name ORDER BY date,op_name ASC ;
*/

#SELECT * FROM TmonthDataMoney;
#SELECT COUNT(*) FROM TmonthDataMoney;
   DROP TABLE DataT;
   DROP TABLE TmonthDataMoney;
   END</pre>
<br />