<div class="text" style="font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">
	<div class="phpcode">
<pre class="prettyprint lang-php linenums">After reading through original notes and example above as well as wading through the documentation, I finally got a loop to work with two stored procedures.
Using the results of the first one as a parameter for the second one. Easier to do this way than a huge modified sequence of Inner Join queries.
Hope this helps others...
&lt;?php
// Connect to server and database
$mysqli        = new mysqli("$dbServer", "$dbUser", "$dbPass", "$dbName");
// Open First Stored Procedure using MYSQLI_STORE_RESULT to retain for looping
$resultPicks = $mysqli-&gt;query("CALL $proc ($searchDate, $maxRSI, $incRSI, $minMACD, $minVol, $minTrades, $minClose, $maxClose)", MYSQLI_STORE_RESULT);
// process one row at a time from first SP
while($picksRow = $resultPicks-&gt;fetch_array(MYSQLI_ASSOC)) {
    // Get Parameter for next SP
    $symbol     = $picksRow['Symbol'];
    // Free stored results
    clearStoredResults($mysqli);
    // Execute second SP using value from first as a parameter (MYSQLI_USE_RESULT and free result right away)
    $resultData    = $mysqli-&gt;query("CALL prcGetLastMACDDatesBelowZero('$symbol', $searchDate)", MYSQLI_USE_RESULT);
    $dataRow    = $resultData-&gt;fetch_array(MYSQLI_ASSOC);
    // Dump result from both related queries
    echo "&lt;p&gt;$symbol ... Num Dates: " . $dataRow['NumDates'];
    // Free results from second SP
    $resultData-&gt;free();
}
// Free results from first SP
$resultPicks-&gt;free();
// close connections
$mysqli-&gt;close();
#------------------------------------------
function clearStoredResults($mysqli_link){
#------------------------------------------
    while($mysqli_link-&gt;next_result()){
      if($l_result = $mysqli_link-&gt;store_result()){
              $l_result-&gt;free();
      }
    }
}
?&gt;


Warner 21-Jul-2009 09:45
It also seems, that executing a SET statement in multi_query() returns an extra recordset too, which one would not expect.


lau at goldenweb dot com dot au 13-Apr-2007 08:29
Beware when using stored procedures:
If you connect to the database and then call dbproc A followed by a call to db proc B and then close the connection to the db, the second procedure call will not work.
It looks like there is a bug in MYSQL or mysqli that returns an extra recordset than you would expect. It then doesn't let you call another stored procedure until you finish processing all the recordsets from the first stored procedure call. 
The solution is to simply loop through the additional recordsets between calls to db procs. Here is a function that I call between db proc calls:
&lt;?php
#--------------------------------
function ClearRecordsets($p_Result){
#--------------------------------
    $p_Result-&gt;free();    
    while($this-&gt;Mysqli-&gt;next_result()){
      if($l_result = $this-&gt;Mysqli-&gt;store_result()){
              $l_result-&gt;free();
      }
    }
}
?&gt;</pre>
<br />
	</div>
</div>