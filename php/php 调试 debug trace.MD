<pre class="prettyprint lang-js linenums">function print_stack_trace()
{
    $array =debug_backtrace();
  //print_r($array);//信息很齐全
   unset($array[0]);
   foreach($array as $row)
    {
       $html .=$row['file'].':'.$row['line'].'行,调用方法:'.$row['function']."&lt;p&gt;";
    }
    return$html;
<p>
	}
</p>

<p>
	-----------------------------------
</p>

<p>
	or
</p>

<p>
	----------------------------------
</p>

<p>
	&nbsp; &nbsp; &nbsp;$e = new Exception;
&nbsp; &nbsp; &nbsp; &nbsp; var_dump($e-&gt;getTraceAsString());
</p>
</pre>