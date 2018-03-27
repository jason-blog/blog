安装<br />
<br />
wget https://github.com/akopytov/sysbench/archive/0.5.zip<br />
unzip 0.5.zip&nbsp;<br />
cd sysbench-0.5/<br />
./autogen.sh<br />
<br />
<br />
如果提示automake 1.10.x (aclocal) wasn't found, exiting，则需要安装automake<br />
<br />
yum -y install automake*<br />
<br />
<br />
如果提示libtoolize 1.4+ wasn't found, exiting，则需要安装libtool<br />
<br />
yum -y install libtool*<br />
<br />
<br />
再次执行autogen.sh<br />
<br />
./configure --prefix=/usr/local/sysbench --with-mysql-includes=/usr/local/mysql/include --with-mysql-libs=/usr/local/mysql/lib<br />
make<br />
make install<br />
ln -s /usr/local/sysbench/bin/sysbench /usr/local/bin/sysbench<br />
<br />
<br />
==============================================================================<br />
<br />
http://www.shixinke.com/mysql/mysql-bench<br />
<br />
<br />
=======================IO==================================<br />
./sysbench --test=fileio --file-num=1000 &nbsp;--file-total-size=10000M --file-test-mode=rndrw &nbsp;--file-rw-ratio=1 prepare<br />
<br />
./sysbench --test=fileio --file-num=1000 &nbsp;--file-total-size=10000M --file-test-mode=rndrw &nbsp;--file-rw-ratio=1 run<br />
<br />
./sysbench --test=fileio --file-num=1000 &nbsp;--file-total-size=10000M --file-test-mode=rndrw &nbsp;--file-rw-ratio=1 run<br />
<br />
<br />
执行完之后需要清除这些测试文件：<br />
<br />
./sysbench --test=fileio --file-num=1000 &nbsp;--file-total-size=10000M --file-test-mode=rndrw &nbsp;--file-rw-ratio=1 cleanup<br />
<br />
<br />
<br />
===========================CPU==============================<br />
./sysbench --test=cpu --cpu-max-prime=20000 run<br />
<br />
<br />
<br />
==============================MYSQL================================<br />
<br />
cd /usr/local/src/sysbench-0.5/sysbench/tests<br />
mkdir /usr/local/sysbench/tests<br />
cp -R db /usr/local/sysbench/tests/<br />
<br />
<br />
<br />
sysbench --test=/usr/local/sysbench/tests/oltp.lua --oltp-test-mode=nontrx --oltp-table-size=10000 --mysql-host=localhost --mysql-db=test --mysql-user=root --mysql-password=spade9.inc --oltp-nontrx-mode=insert --mysql-socket=/tmp/mysql.sock prepare<br />
<br />
<br />
sysbench --test=/usr/local/sysbench/tests/db/oltp.lua --oltp-table-size=1000000 --mysql-db=test --mysql-user=test --mysql-password=test --mysql-socket=/tmp/mysql.sock run<br />
<br />
<br />
sysbench --test=/usr/local/sysbench/tests/db/oltp.lua --oltp-table-size=1000000 --mysql-db=test --mysql-user=test --mysql-password=test --mysql-socket=/tmp/mysql.sock cleanup<br />
<br />
<br />
######################<br />
./sysbench: error while loading shared libraries: libmysqlclient.so.18: cannot open shared object file: No such file or directory &nbsp;<br />
export LD_LIBRARY_PATH=/usr/mysql/lib &nbsp;<br />
<br />
<br />
<br />
http://blog.csdn.net/mchdba/article/details/8970056<br />
<br />
<br />
<br />
#time sysbench --test=/usr/local/sysbench/tests/oltp.lua --oltp-test-mode=nontrx --mysql-table-engine=innodb --mysql-user=root --mysql-password=spade9.inc --db-driver=mysql --num-threads=20 --max-requests=200 &nbsp;--oltp-nontrx-mode=insert --mysql-db=test &nbsp;--oltp-table-size=20000 --oltp-table-name=t1 &nbsp;--mysql-socket=/tmp/mysql.sock run &nbsp;1&gt; 2.log<br />
<br />
<br />
<br />
sysbench --test=/usr/local/sysbench/tests/oltp.lua --oltp-test-mode=nontrx --oltp-table-size=10000 &nbsp;--mysql-db=azurerepdb --mysql-user=bd5840eb722cd3 --mysql-host=ap-cdbr-azure-east-c.cloudapp.net --mysql-password=cdec6e68 &nbsp;--oltp-nontrx-mode=insert --mysql-socket=/tmp/mysql.sock prepare<br />
<br />
<br />
<br />
sysbench --test=/usr/local/sysbench/tests/oltp.lua --mysql-table-engine=innodb --num-threads=20 --max-requests=200 --oltp-table-size=40000 --mysql-db=azurerepdb --mysql-user=bd5840eb722cd3 --mysql-host=207.46.136.162 --mysql-password=cdec6e68 prepare<br />
<br />
<br />
<br />
#注意 测试远程数据库的时候去掉socket地址<br />
<br />
==============================MYSQL================================<br />
<br />
oltp options:<br />
&nbsp; --oltp-test-mode=STRING &nbsp; &nbsp;执行模式{simple,complex(advanced transactional),nontrx(non-transactional),sp}。默认是complex<br />
&nbsp; --oltp-reconnect-mode=STRING 重新连接模式{session(不使用重新连接。每个线程断开只在测试结束),transaction(在每次事务结束后重新连接),query(在每个SQL语句执行完重新连接),random(对于每个事务随机选择以上重新连接模式)}。默认是session<br />
&nbsp; --oltp-sp-name=STRING &nbsp; &nbsp; &nbsp;存储过程的名称。默认为空<br />
&nbsp; --oltp-read-only=[on|off] &nbsp;只读模式。Update，delete，insert语句不可执行。默认是off<br />
&nbsp; --oltp-skip-trx=[on|off] &nbsp; 省略begin/commit语句。默认是off<br />
&nbsp; --oltp-range-size=N &nbsp; &nbsp; &nbsp; &nbsp;查询范围。默认是100<br />
&nbsp; --oltp-point-selects=N &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;number of point selects [10]<br />
&nbsp; --oltp-simple-ranges=N &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;number of simple ranges [1]<br />
&nbsp; --oltp-sum-ranges=N &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; number of sum ranges [1]<br />
&nbsp; --oltp-order-ranges=N &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; number of ordered ranges [1]<br />
&nbsp; --oltp-distinct-ranges=N &nbsp; &nbsp; &nbsp; &nbsp;number of distinct ranges [1]<br />
&nbsp; --oltp-index-updates=N &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;number of index update [1]<br />
&nbsp; --oltp-non-index-updates=N &nbsp; &nbsp; &nbsp;number of non-index updates [1]<br />
&nbsp; --oltp-nontrx-mode=STRING &nbsp;查询类型对于非事务执行模式{select, update_key, update_nokey, insert, delete} [select]<br />
&nbsp; --oltp-auto-inc=[on|off] &nbsp; AUTO_INCREMENT是否开启。默认是on<br />
&nbsp; --oltp-connect-delay=N &nbsp; &nbsp; 在多少微秒后连接数据库。默认是10000<br />
&nbsp; --oltp-user-delay-min=N &nbsp; &nbsp;每个请求最短等待时间。单位是ms。默认是0<br />
&nbsp; --oltp-user-delay-max=N &nbsp; &nbsp;每个请求最长等待时间。单位是ms。默认是0<br />
&nbsp; --oltp-table-name=STRING &nbsp; 测试时使用到的表名。默认是sbtest<br />
&nbsp; --oltp-table-size=N &nbsp; &nbsp; &nbsp; &nbsp;测试表的记录数。默认是10000<br />
&nbsp; --oltp-dist-type=STRING &nbsp; &nbsp;分布的随机数{uniform(均匀分布),Gaussian(高斯分布),special(空间分布)}。默认是special<br />
&nbsp; --oltp-dist-iter=N &nbsp; &nbsp; &nbsp; &nbsp; 产生数的迭代次数。默认是12<br />
&nbsp; --oltp-dist-pct=N &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;值的百分比被视为'special' (for special distribution)。默认是1<br />
&nbsp; --oltp-dist-res=N &nbsp; &nbsp; &nbsp; &nbsp; ‘special’的百分比值。默认是75<br />
&nbsp;&nbsp;<br />
General database options:<br />
&nbsp; --db-driver=STRING &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;指定数据库驱动程序('help' to get list of available drivers)<br />
&nbsp; --db-ps-mode=STRING &nbsp; &nbsp; &nbsp; &nbsp; 编制报表使用模式{auto, disable} [auto]<br />
Compiled-in database drivers:<br />
&nbsp; &nbsp; mysql - MySQL driver<br />
mysql options:<br />
&nbsp;--mysql-host=[LIST,...] &nbsp; &nbsp; &nbsp; 数据库地址<br />
&nbsp;--mysql-port=N &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;端口号，默认3306<br />
&nbsp;--mysql-user=STRING &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 用户名<br />
&nbsp;--mysql-password=STRING &nbsp; &nbsp; &nbsp; 密码<br />
&nbsp;--mysql-db=STRING &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 测试数据库名<br />
&nbsp;--mysql-table-engine=STRING &nbsp; 数据库存储引擎，默认innodb{myisam,innodb,bdb,heap,ndbcluster,federated}<br />
&nbsp;--mysql-socket=STRING &nbsp; &nbsp; &nbsp; &nbsp; socket文件的位置<br />
&nbsp;--mysql-engine-trx=STRING &nbsp; &nbsp; 是否使用事务，与存储引擎选择有关，默认auto{yes,no,auto}<br />
&nbsp;--mysql-ssl=[on|off] &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;在客户端是否使用SSL连接，默认off<br />
&nbsp;--myisam-max-rows=N &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;MyISAM表最大行数，默认1000000<br />
&nbsp;--mysql-create-options=STRING additional options passed to CREATE TABLE []<br />