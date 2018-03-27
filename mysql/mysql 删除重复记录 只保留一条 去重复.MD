<pre class="prettyprint lang-php linenums">


<pre class="prettyprint lang-js linenums"> DELETE FROM people WHERE peopleId IN (
		SELECT	peopleId FROM people GROUP BY peopleId HAVING count(peopleId) &gt; 1
	)
AND rowid NOT IN ( SELECT min(rowid) FROM people GROUP BY	peopleId HAVING
		count(peopleId) &gt; 1
)</pre>
<br />
<pre class="prettyprint lang-js linenums">DELETE
FROM
	user
WHERE
	id NOT IN (
SELECT id FROM (
		SELECT
			MAX(id) AS id
		FROM
			user
		GROUP BY
			username
	) AS d
)</pre>
</pre>