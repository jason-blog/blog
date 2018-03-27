在Python中要连接数据库，首先我们得先安装几个重要的东西，主要有：<br />
<br />
&nbsp;（1）Python-dev包<br />
&nbsp;（2）setuptools-0.6c11.tar.gz<br />
&nbsp;（3）MySQL-python-1.2.3.tar.gz<br />
<br />
下面分别来说说这三个主要的包的安装步骤：<br />
<br />
（1）Python-dev包 &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; 直接yum install python-devel<br />
<br />
（2）setuptools-0.6c11.tar.gz<br />
&nbsp; &nbsp; 在网上下载后，先解压：tar zxf setuptools-0.6c11.tar.gz，完毕后cd到解压后的文件夹，执行：<br />
&nbsp; &nbsp; &nbsp;python setup.py build<br />
&nbsp; &nbsp; &nbsp; python setup.py install<br />
<br />
（3）MySQL-python-1.2.3.tar.gz<br />
&nbsp; &nbsp; 跟安装setuptools-0.6c11.tar.gz步骤一样，先解压：tar zxfMySQL-python-1.2.3.tar.gz，<br />
&nbsp; &nbsp; 完毕后cd到解压后的文件夹，执行：<br />
&nbsp; &nbsp; &nbsp; python setup.py build<br />
&nbsp; &nbsp; &nbsp; python setup.py install<br />
<br />
&nbsp; &nbsp; 在执行上述命令之前，最好先修改一个文件，我们先查找mysql_config的位置，使用命令：<br />
&nbsp; &nbsp; &nbsp; find / -name mysql_config<br />
&nbsp; &nbsp; 然后我们获取到它的路径,我的是：/usr/bin/mysql_config，然后修改MySQL-python-1.2.3目录下<br />
&nbsp; &nbsp; 的site.cfg文件,去掉mysql_config=XXX这行前面的#，改为：<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;mysql_config = /usr/bin/mysql_config<br />
<br />
经过上面的步骤，我们基本就可以MySQLdb安装好了。<br />
<br />
可以测试一下，在Python的交互式命令行，输入import MySQLdb，如果没有报错，就说明已经安装好。<br />
<br />
<br />
下面的Python代码展示了如何连接数据库，并执行数据库的一些操作：<br />
[python] view plain copy 在CODE上查看代码片派生到我的代码片<br />
import MySQLdb &nbsp;<br />
&nbsp;&nbsp;<br />
try: &nbsp;<br />
&nbsp; &nbsp; conn = MySQLdb.connect(host='localhost',user='root',passwd='root',port=3306) &nbsp;<br />
&nbsp; &nbsp; cur = conn.cursor() &nbsp;<br />
&nbsp;&nbsp;<br />
&nbsp; &nbsp; cur.execute('create database if not exists PythonDB') &nbsp;<br />
&nbsp; &nbsp; conn.select_db('PythonDB') &nbsp;<br />
&nbsp; &nbsp; cur.execute('create table Test(id int,name varchar(20),info varchar(20))') &nbsp;<br />
&nbsp;&nbsp;<br />
&nbsp; &nbsp; value = [1,'ACdreamer','student'] &nbsp;<br />
&nbsp; &nbsp; cur.execute('insert into Test values(%s,%s,%s)',value) &nbsp;<br />
&nbsp;&nbsp;<br />
&nbsp; &nbsp; values = [] &nbsp;<br />
&nbsp; &nbsp; for i in range(20): &nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; values.append((i,'Hello World!','My number is '+str(i))) &nbsp;<br />
&nbsp;&nbsp;<br />
&nbsp; &nbsp; cur.executemany('insert into Test values(%s,%s,%s)',values) &nbsp;<br />
&nbsp; &nbsp; cur.execute('update Test set name="ACdreamer" where id=3') &nbsp;<br />
&nbsp;&nbsp;<br />
&nbsp; &nbsp; conn.commit() &nbsp;<br />
&nbsp; &nbsp; cur.close() &nbsp;<br />
&nbsp; &nbsp; conn.close() &nbsp;<br />
except MySQLdb.Error,msg: &nbsp;<br />
&nbsp; &nbsp; print "MySQL Error %d: %s" %(msg.args[0],msg.args[1]) &nbsp;<br />
<br />
<br />
可以看出，连接数据库大致分为以下步骤：<br />
<br />
&nbsp; （1）建立和数据库系统的连接<br />
&nbsp; （2）获取操作游标<br />
&nbsp; （3）执行SQL，创建一个数据库（当然这一步不是必需的，因为我们可以用已经存在的数据库）<br />
&nbsp; （4）选择数据库<br />
&nbsp; （5）进行各种数据库操作<br />
&nbsp; （6）操作完毕后，提交事务（这一步很重要，因为只有提交事务后，数据才能真正写进数据库）<br />
&nbsp; （7）关闭操作游标<br />
&nbsp; （8）关闭数据库连接<br />
<br />
当然，如果我们使用已经存在的数据库，那么在获取连接时就可以制定了，比如：<br />
conn = MySQLdb.connect(host='localhost', user='root', passwd='root', db='PythonDB')<br />
<br />
如果数据库中有中文，为了防止乱码，我们加入属性charset = 'uft-8'或者'gb2312',charset要跟数据库的编码一致。<br />
conn = MySQLdb.connect(host='localhost', user='root',&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp;passwd='root', db='PythonDB',charset='utf8')&nbsp;<br />
<br />
<br />
下面贴一下常用的函数：<br />
<br />
数据库连接对事务操作的方法：commit() 提交 &nbsp; &nbsp;rollback() 回滚<br />
<br />
cursor用来执行命令的方法：<br />
<br />
callproc(self,procname,args)<br />
用来执行存储过程,接收的参数为存储过程名和参数列表,返回值为受影响的行数<br />
<br />
execute(self, query, args)<br />
执行单条sql语句,接收的参数为sql语句本身和使用的参数列表,返回值为受影响的行数<br />
<br />
executemany(self, query, args)<br />
执行单挑sql语句,但是重复执行参数列表里的参数,返回值为受影响的行数<br />
<br />
nextset(self)<br />
移动到下一个结果集<br />
<br />
<br />
<br />
cursor用来接收返回值的方法：<br />
<br />
fetchall(self)<br />
接收全部的返回结果行<br />
<br />
fetchmany(self, size=None)<br />
接收size条返回结果行.如果size的值大于返回的结果行的数量,则会返回cursor.arraysize条数据<br />
<br />
fetchone(self)<br />
返回一条结果行<br />
<br />
scroll(self, value, mode='relative')<br />
移动指针到某一行，如果mode='relative',则表示从当前所在行移动value条,如果 mode='absolute',则表示从结果集的第一行移动value条。<br />
<br />
<br />
<br />
export LD_LIBRARY_PATH="/usr/local/mysql/mysql/lib"<br />
<div style="white-space:nowrap;">
	<br />
</div>