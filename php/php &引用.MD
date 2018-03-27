&lt;?php<br />
<br />
header('Content-Type: text/html; charset=UTF-8');<br />
<br />
//引用 PHP。。。。。。<br />
<br />
function &amp;test(){<br />
&nbsp; &nbsp; &nbsp;static $_testArray=array('ceshi1'=&gt;1,'ceshi2'=&gt;100);<br />
&nbsp; &nbsp; &nbsp;<br />
&nbsp; &nbsp; &nbsp;$_testArray['ceshi1']= $_testArray['ceshi1']+100;<br />
&nbsp; &nbsp; &nbsp;<br />
&nbsp; &nbsp; &nbsp;return $_testArray;<br />
}<br />
$a=5;<br />
<br />
$a=test();<br />
<br />
print_r($a);<br />
<br />
print_R(test());<br />
<br />
$a=&amp;test();<br />
<br />
$a['ceshi1']=100000;<br />
<br />
print_R(test());<br />
<br />
$a['ceshi1']=200000;<br />
<br />
print_R(test());<br />
<br />
<br />
<br />
<br />
function test(&amp;$a){<br />
&nbsp; &nbsp; $a=$a+100;<br />
}<br />
$b=1;<br />
echo $b;//输出１ test($b); &nbsp; //这里$b传递给函数的其实是$b的变量内容所处的内存地址，通过在函数里改变$a的值　就可以改变$b的值了 echo "&lt;br&gt;"; echo $b;//输出101<br />
<br />
<br />
$a="ABC";<br />
$b =&amp;$a;<br />
echo $a;//这里输出:ABC<br />
echo $b;//这里输出:ABC<br />
$b="EFG";<br />
echo $a;//这里$a的值变为EFG 所以输出EFG echo $b;//这里输出EFG<br />
<br />
<br />
<br />
<br />
?&gt;<br />
<div style="white-space:nowrap;">
	<br />
</div>