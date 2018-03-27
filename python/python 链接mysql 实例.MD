import MySQLdb &nbsp;<br />
&nbsp;&nbsp;<br />
try: &nbsp;<br />
#db='dbname'<br />
&nbsp; &nbsp; conn = MySQLdb.connect(host='localhost',user='root',passwd='test',port=3306) &nbsp;<br />
&nbsp; &nbsp; conn.select_db('test') &nbsp;<br />
&nbsp;<br />
cur = conn.cursor() &nbsp;<br />
&nbsp;&nbsp;<br />
&nbsp; &nbsp; #cur.execute('create database if not exists PythonDB') &nbsp;<br />
&nbsp; &nbsp;<br />
&nbsp; &nbsp; cur.execute('select * from a limit 1') &nbsp;<br />
&nbsp; &nbsp; row=cur.fetchone()<br />
#fetchall()<br />
&nbsp; &nbsp; print row<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; #value = [1,'ACdreamer','student'] &nbsp;<br />
&nbsp; &nbsp; #cur.execute('insert into Test values(%s,%s,%s)',value) &nbsp;<br />
&nbsp;&nbsp;<br />
&nbsp; &nbsp;# values = [] &nbsp;<br />
&nbsp; &nbsp; #for i in range(20): &nbsp;<br />
&nbsp; &nbsp; &nbsp;# &nbsp; values.append((i,'Hello World!','My number is '+str(i))) &nbsp;<br />
&nbsp;&nbsp;<br />
&nbsp; &nbsp; #cur.executemany('insert into Test values(%s,%s,%s)',values) &nbsp;<br />
&nbsp; &nbsp;# cur.execute('update Test set name="ACdreamer" where id=3') &nbsp;<br />
&nbsp;&nbsp;<br />
&nbsp; &nbsp; conn.commit() &nbsp;<br />
&nbsp; &nbsp; cur.close() &nbsp;<br />
&nbsp; &nbsp; conn.close() &nbsp;<br />
except MySQLdb.Error,msg: &nbsp;<br />
&nbsp; &nbsp; print "MySQL Error %d: %s" %(msg.args[0],msg.args[1]) &nbsp;<br />