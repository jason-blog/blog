<br />
////////////// ArrayObject 1/////////////////////////////////////////////<br />
$array = array('1' =&gt; 'one',<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;'2' =&gt; 'two',<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;'3' =&gt; 'three');<br />
<br />
$arrayobject = new ArrayObject($array); //构造一个ArrayObject对象<br />
<br />
for($iterator = $arrayobject-&gt;getIterator();//构造一个迭代器<br />
&nbsp; &nbsp; $iterator-&gt;valid();//检查是否还含有元素<br />
&nbsp; &nbsp; $iterator-&gt;next()) { //指向下个元素<br />
<br />
&nbsp; &nbsp; echo $iterator-&gt;key() . ' =&gt; ' . $iterator-&gt;current() . "\n";//打印数组元素<br />
}<br />
<br />
<br />
////////////////////// ArrayObject 2///////////////////////<br />
$arrayobject = new ArrayObject();<br />
<br />
$arrayobject[] = 'zero';<br />
$arrayobject[] = 'one';<br />
$arrayobject[] = 'two';<br />
<br />
$iterator = $arrayobject-&gt;getIterator();<br />
<br />
$iterator-&gt;next();<br />
echo $iterator-&gt;key(); // 1<br />
<br />
$iterator-&gt;rewind(); //重置指针到头部<br />
echo $iterator-&gt;key(); // 0<br />
<br />
/////////////////////////////////////////////<br />