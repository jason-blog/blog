<pre class="prettyprint lang-php linenums">BEGIN  
           #定义 变量  
           DECLARE uname VARCHAR(30);  
           DECLARE amo VARCHAR(30);  
           DECLARE rodid int;  
           DECLARE cttime VARCHAR(30); 
           DECLARE SQLSTRING VARCHAR(255);    
           DECLARE nogsid int; 
           DECLARE isexit int;  
           DECLARE Result int; 
           #这个用于处理游标到达最后一行的情况   DECLARE CONTINUE HANDLER FOR SQLSTATE '02000' SET s=1;  
           DECLARE s int default 0;   

           #声明游标cursor_name（cursor_name是个多行结果集）  
           DECLARE cursor_name CURSOR FOR SELECT user_name,nogsgameid,roundid,amount,create_time FROM `rfcorp_nyx_transaction` WHERE amount &gt;= winamount_max AND STATUS = 'pending' AND (create_time BETWEEN limit_start AND limit_end);
           #设置一个终止标记   
           DECLARE CONTINUE HANDLER FOR SQLSTATE '02000' SET s=1;  
                #打开游标  
                OPEN cursor_name;  
                    #获取游标当前指针的记录，读取一行数据并传给变量 
                    fetch  cursor_name into uname,nogsid,rodid,amo,cttime;  
                    #开始循环，判断是否游标已经到达了最后作为循环条件   while循环
                    while s &lt;&gt; 1 do 
 #组装字符串进行查询 
SET @SQLSTRING= CONCAT("select id as shabi,user_name as nimabi FROM ceshi WHERE id=",idd,""); 
PREPARE stmt FROM @SQLSTRING;
EXECUTE stmt;
 #组装字符串进行查询 
 #md5
select md5('sdf');
 #md5
 #判断
    IF isexit=0 then
      IF isexit&gt;0 then
     insert into ceshi(user_name,amount,roundid,create_transaction_time,platform,create_time,type) values(uname,amo,rodid,cttime,'nyx',UNIX_TIMESTAMP(NOW()),types);  
#获取插入后返回的id
     ELSE
SET Result=LAST_INSERT_ID();
SELECT Result;
       END IF;
       END IF;
       #读取下一行的数据  
       fetch cursor_name into uname,nogsid,rodid,amo,cttime;  
       end while;  
     #关闭游标  
    CLOSE cursor_name ;  
    #语句执行结束  
    END

#create procedure sp_name()	创建</pre>
<br />