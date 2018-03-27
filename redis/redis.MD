redis-cli //链接<br />
<br />
redis-cli keys * //所有KEY<br />
<br />
exists name 查看n是否有name这个key<br />
<br />
<br />
redis-cli &nbsp;<br />
redis 127.0.0.1:6379&gt; set redisKey value &nbsp;<br />
OK &nbsp;<br />
redis 127.0.0.1:6379&gt; get redisKey &nbsp;<br />
"value" &nbsp;<br />
redis 127.0.0.1:6379&gt; del redisKey &nbsp;<br />
(integer) 1 &nbsp;<br />
redis 127.0.0.1:6379&gt; exists key &nbsp;<br />
(integer) 0 &nbsp;<br />
<br />
hset hash1 field1 hello1 &nbsp; //设置hash表hash1的field1域的值为hello1<br />
<br />
<br />
hgetall //获取所有hash field<br />
<br />
<br />
<br />
<br />
<br />
<br />
//////////////////////////数据类型和对应操作方法////////////////////////////////<br />
<br />
Redis的数据类型及操作<br />
Strings<br />
最简单的类型，一个Key对应一个Value，string类型是二进制安全的。Redis的string可以包含任何数据，如图片或序列化的对象<br />
<br />
操作<br />
Set：设置key对应的值为string类型的value，如 set name Fahy<br />
Setnx：设置key对应的值为string类型的value，如果key已经存在，返回0，如 setnx name Fahy<br />
Setex：设置key对应的值为string类型的value，并指定此键值对的有效期，如 setex name 10 Fahy<br />
Setrange：设置指定key的value值的子字符串，替换相同长度的字符，如 已有一对key-value为email=hwj1993@sina.com，则 setrange email 8 qq.com 会使email=hwj1993@qq.com<br />
mset：一次设置多个key的值，成功返回ok表示所以值都被设置，失败返回0表示没有任何值被设置，如 mset key1 huangweijian key2 others<br />
msetnx：一次设置多个key的值，成功返回ok表示所有值都被设置，失败返回0表示没有任何值被设置，但不会覆盖以存在的key，如 msetnx key3 huangweineng key4 yellow<br />
get：获取key对应的value，如果key不存在，返回nill，如 get key1<br />
getset：设置key的值，并返回key的旧值，如 getset key2 huangsurong<br />
getrange：获取key的value值的子字符串，如 getrange key1 0 4，返回从第0到第4个字符"huang"<br />
mget：一次获取多个key的值，如果对应的key不存在，返回nil，如 mget key1 key2 key3<br />
incr：对key的值做++操作，并返回新的值，当key不存在时，设置key值为0再进行加操作，如 incr key5<br />
incrby：对key的值做加指定值操作，当key不存在时，设置key值为0再进行加操作，如 incrby key6 &nbsp;7<br />
decr：对key的值做--操作，当key不存在时，设置key值为0再进行减操作，如 decr key7<br />
decrby：对key的值做减指定值操作，当key不存在时，设置key值为0再进行减操作，如 decrby key8 &nbsp;7<br />
append：给指定key的字符串追加value，返回新字符串值的长度，当key不存在时，添加该key，如 append key1 @sina.com<br />
strlen：返回指定key的value长度，如 strlen key1<br />
del：删除指定key，如 del key1<br />
hashes：可建立一张hash表<br />
Redis hash是一个string类型的field(字段)和value的映射表，它的添加、删除操作都是O(I)(平均)。适合存储对象，占用更少的内存，并且方便存钱整个对象<br />
<br />
操作<br />
hset：设置hash field为指定值，如果key不存在，则先创建，如 hset hashtable field hello<br />
hsetnx：设置hash field为指定值，如果key不存在，则先创建，如果存在返回0，如 hsetnx hashtable field1 world<br />
hmset：同时设置hash的多个field，如 hmset hashtable field2 helloween field3 christmas<br />
hget：获取指定的hash field，如 hget hashtable field<br />
hmget：获取全部指定的hash field，如 hmget hashtable field field1 field2<br />
hincrby：指定的hash field加上特定值，如 hincrby hashtable field4 5<br />
hdecrby：指定的hash field减去特定值，如 hdecrby hashtable field4 5<br />
hexists：判断指定field是否存在，如 hexists hashtable field4<br />
hlen：返回指定hash的field数量，如 hlen hashtable<br />
hdel：删除指定hash的field，如 hdel hashtable field<br />
hkeys：返回hash的所有field，如 hkeys hashtable<br />
hvals：返回hash的所有value，如 hvals hashtable<br />
hgetall：获取某个hash中全部的field几value，如 hgetall hashtable<br />
lists：一个链表结构，主要功能是push,pop,获取一个范围的所有值等等，操作中key理解为链表的名字。<br />
Redis的list类型其实就是一个每个子元素都是string类型的双向链表。既可作为栈，又可作为堆<br />
<br />
操作<br />
lpush：在key对应list的头部添加字符串元素，如 lpush list hello<br />
rpush：在key对应的list的尾部添加字符串元素，如 rpush list world<br />
linsert：在key对应list的特定位置前或后添加字符串，如 linsert list before world my 或 linsert list after hello you<br />
lset：设置list中指定下表的元素值，如 lset list 1 he<br />
lrange：返回指定范围内的元素，如 lrange list 0 -1<br />
lrem：从key对应的list中删除n个和value相同的元素，n&lt;0从尾删除，n=0全部删除，如 lrem list 1 you<br />
ltrim：保留指定范围内的数据，如 ltrim list 1 -1<br />
lpop：从list头部删除元素，并返回删除元素，如 lpop list<br />
rpop：从list尾部删除元素，并返回删除元素，如 rpop list<br />
rpoplpush：移除第一个list尾部元素到第二个list头部，如 rpoplpush list1 list2<br />
lindex：返回名称为key的list的index位置的元素，如 lindex list 1<br />
llen：返回key对应的list的长度，如 llen list<br />
sets：集合，是string类型的无序集合<br />
Redis的set类型通过hash table实现的，添加、删除和查找的复杂度都是O(1)。对集合可以取并集、交集和差集。<br />
<br />
操作<br />
sadd：向名称为key的set中添加元素，如 sadd settable hello<br />
srem：删除名称为key的set中的元素，如 srem settable two<br />
smember：获取名称为key的set中的所有元素，如 smember settable<br />
spop：随机返回并删除名称为key的set中的元素，如 spop settable<br />
sdiff：返回以key1为标准，与其他key不同的元素，如 sdiff set1 set2<br />
skiffstore：将以key1为标准，与其他key不同的元素，存到key3中，如 sdiffstore key3 key1 key2<br />
sinter：返回所有给定key的交集，如 sinter set1 set2<br />
sinterstore：将所有给定key的交集存储到另一个key中，如 sinterstore key key1 key2<br />
sunion：返回所有给定key的并集，如 sunion set1 set2<br />
sunionstore：将所有给定key的并集存储到另一个key中，如 sunionstore key key1 key2<br />
smove：从第一个key对应的set中移除member并添加到第二个对应的set中，如 smove set1 set2 hello<br />
scard：返回名称为key的set元素个数，如 scard set1<br />
sismember：测试member是否属于名称为key的set的元素，如 sismember set member<br />
srandmember：随机返回名称为key的set的一个元素，如 srandmember set<br />
sorted sets：在set的基础上增加了一个顺序属性，这一属性在添加修改元素的时候可以制定，每次指定后，zset会重新按新的值调整顺序，序号可相同，值不可相同<br />
操作<br />
zadd：向名称为key的set中添加元素，并指定序号，如 zadd settable 1 hello<br />
zrange：返回指定索引范围内的元素，添加withscores，返回序号，如 zrange settable 0 -1 withscores<br />
zrem：删除名称为key的zset中个元素member，如 zrem settable hello<br />
zincrby：如果在名称为key的zset中给已经存在元素member，则该元素的score增加increment，否则，向该集合中添加该元素，起score的值为increment，如 zincrby settable 2 earth<br />
zrank：返回名称为key的zset中member元素的排名（按score从小到大排序），如 zrank settable earth withscores<br />
zrevrank：返回名称为key的zset中member元素的排名（按score从大到小排序），如 zrevrank settable earth withscores<br />
zrevrange：返回名称为key的zset（按score从大到小顺序）中的index从start到end的所有元素，如 zrevrange settable 0 -1 withscores<br />
zrangebyscore：返回集合中score在给定区间的元素，如 zrangebyscore settable 1 3 withscores<br />
zcount：返回集合中score在给定区间的元素个数，如 zcount settable 1 3<br />
zcard：返回集合中的元素个数，如 zcard settable<br />
zremrangebyrank：删除集合中排名的索引在给定区间的元素，如 zremrangebyrank settable 1 1<br />
zremrangebyscore：删除集合中score在给定区间的元素，如 zremrangebyscore settable 1 2<br />
<br />
<br />
<br />