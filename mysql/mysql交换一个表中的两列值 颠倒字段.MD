<h2 class="title content-title" style="margin:0px;padding:0px 0px 15px;list-style:none;white-space:normal;">
	mysql交换一个表中的两列值&nbsp;
</h2>
<p>
	<br />
</p>
<p>
	<br />
</p>
<pre class="prettyprint lang-php linenums">UPDATE table AS a JOIN table AS b  on a.id=b.id SET a.column1 = b.column2 ,a.column2=b.column1;
update table a,table b set a.column1 = b.column2, a.column2=b.column1 where a.id=b.id;</pre>
<p>
	<br />
</p>