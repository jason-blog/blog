mysql获取自增id的几种方法
使用max函数：select max(id) from tablename 
优点：使用方便快捷。
缺点：获取的不是真正的自增id，是表中最大的Id，如果有删除数据的话，那么该值和自增id相差比较大。如果有连表数据，有可能导致数据错乱。
使用LAST_INSERT_ID函数：select LAST_INSERT_ID()
优点：获取到的是真正的自增id。
缺点：该函数是与table无关的，永远保留最新插入的自增列的id。如果多客户端操作，而且不能保证原子性，这个值可能会出现错误。所以需要在插入之后调用。
使用@@IDENTITY变量：select @@IDENTITY 
此方法和LAST_INSERT_ID()功能差不多，优缺点也一致。需要在插入后调用。
使用mysql查询函数：SHOW TABLE STATUS; 
优点：能够准确的查到自增id。而且可以在语句后面加上where语句或者like语句来过滤。
缺点：该语句返回的是一个记录集，不能单独的返回自增值。所以需要额外的操作来获取。
使用自定义查询方法：mysql表相关的信息是放在information_schema表里。所以我们参考 SHOW TABLE STATUS来构建查询语句。如： 
select Auto_increment into autoId from information_schema.tables where Table_Schema = ‘dbname’ and table_name = ‘tablename’;
优点：高度自定义，能够准确的得到想得到的任何信息。
确定：不容易记住。呵呵。
mysql自增id的重置
使用truncate：truncate table； 
说明：使用truncate会删除表的数据释放空间，并且重置字自增id，但不会删除表的定义。
用处：需要清空表的时候才能使用。
使用修改标识：dbcc checkident (‘table_name’ , reseed, new_reseed_value) ; 
说明：new_reseed_value是设置的当前标识，下次插入则从new_reseed_value+1开始。如果new_reseed_value小于表中当前标识的值，有可能会产生重复key，会产生 2627 号错误信息。
用处：此方法不会清空已有数据。适用于大量删除后修改新的标识，但不能比当前表中最大值小。
使用修改表的方法：alter table tablename auto_increment=new 
说明：此方法和上面的二方法类似。也不会清空数据，有可能会出现重复key的可能，所以此方法也只适用于清空表之后重置自增id或者大量删除后修改自增id。