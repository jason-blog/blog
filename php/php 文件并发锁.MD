<pre class="prettyprint lang-js linenums">阻塞模式</pre>
<pre class="prettyprint lang-js linenums"> &lt;?php
$fp = fopen("lock.txt", "w+");
if(flock($fp,LOCK_EX))
{
&nbsp; //..处理订单
&nbsp; flock($fp,LOCK_UN);
}
fclose($fp);
?&gt;
</pre>
<pre class="prettyprint lang-js linenums">非阻塞模式</pre>
<pre class="prettyprint lang-js linenums"></pre>
<pre class="prettyprint lang-js linenums"></pre>
<pre class="prettyprint lang-js linenums">&lt;?php  $fp = fopen("lock.txt", "w+");   
if (flock($fp, LOCK_NB | LOCK_EX)) {  
    echo 'do something';  
    @flock($fp, LOCK_UN);  
} else {  
    echo '系统繁忙';  
}  
@fclose($fp); </pre>