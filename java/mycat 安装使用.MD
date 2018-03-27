<p>
	官方网址&nbsp;http://www.mycat.io
</p>
<p>
	官方文档&nbsp;http://www.mycat.io/document/Mycat_V1.6.0.pdf
</p>
<p>
	schema.xml&nbsp;
</p>
<p>
	<br />
</p>
<p>
	&lt;mycat:schema xmlns:mycat="http://io.mycat/"&gt;<br />
<br />
&nbsp; &nbsp; &lt;schema name="mygame" checkSQLschema="false" sqlMaxLimit="100"&nbsp; dataNode="dn1" &gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &lt;table name="rfcorp_user" primaryKey="id" dataNode="dn2"&nbsp; rule="rule1" /&gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &lt;table name="test" dataNode="dn1"&nbsp; /&gt;<br />
&nbsp; &nbsp; &lt;/schema&gt;<br />
&nbsp; &nbsp; &lt;dataNode name="dn1" dataHost="localhost1" database="test" /&gt;<br />
&nbsp; &nbsp; &lt;dataNode name="dn2" dataHost="localhost2" database="game" /&gt;<br />
&nbsp; &nbsp; &lt;dataNode name="dn3" dataHost="localhost3" database="game" /&gt;<br />
<br />
&nbsp; &nbsp; &lt;dataHost name="localhost1" maxCon="1000" minCon="10" balance="0" dbType="mysql" dbDriver="jdbc" writeType="0" switchType="1"&nbsp; slaveThreshold="100"&gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &lt;heartbeat&gt;select user()&lt;/heartbeat&gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &lt;writeHost host="hostM1" url="jdbc:mysql://10.1.0.44:3306" user="root" password=""&gt;&lt;/writeHost&gt;<br />
&nbsp; &nbsp; &lt;/dataHost&gt;<br />
&nbsp; &nbsp; &lt;dataHost name="localhost2" maxCon="1000" minCon="1" balance="0" dbType="mysql" dbDriver="jdbc"&gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &lt;heartbeat&gt;&nbsp; &nbsp; &nbsp; &nbsp;&lt;/heartbeat&gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&lt;writeHost host="hostM2" url="jdbc:mysql://localhost:3306" user="root"&nbsp; password=""&gt;&lt;/writeHost&gt;<br />
&nbsp; &nbsp; &nbsp;&lt;/dataHost&gt;<br />
&nbsp; &nbsp; &lt;dataHost name="localhost3" maxCon="1000" minCon="1" balance="0" dbType="mysql" dbDriver="jdbc"&gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &lt;heartbeat&gt;&nbsp; &nbsp; &nbsp; &nbsp;&lt;/heartbeat&gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&lt;writeHost host="hostM3" url="jdbc:mysql://10.1.0.44:3306" user="root"&nbsp; password=""&gt;&lt;/writeHost&gt;<br />
&nbsp; &nbsp; &nbsp;&lt;/dataHost&gt;<br />
<br />
&lt;/mycat:schema&gt;
</p>