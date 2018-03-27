<pre class="prettyprint lang-js linenums">&lt;script&gt;
$(function() {
 $("input[name='moneyCount']").not('input[NOJS=ture]').keyup(function() {
$(this).val($(this).val().match(/^([0-9])+[\.]?([0-9]){0,2}/g));
    }).bind("blur",function(){
  var val=$(this).val();
  if (val) {
  var val = val.match(/^([0-9])+([\.]?[0-9]{0,2})?/g);
  if (String(val).indexOf('.') &gt; 0) 
  val = parseFloat(val).toFixed(2);else val = parseInt(val);
   	  $(this).val(val);
  }});});
&lt;/script&gt;


s正则表达式限制文本框只能输入数字,小数点,英文字母,汉字等各类代码

1.文本框只能输入数字代码(小数点也不能输入)
&lt;input onkeyup="this.value=this.value.replace(/\D/g,'')" onafterpaste="this.value=this.value.replace(/\D/g,'')"&gt;
2.只能输入数字,能输小数点.
&lt;input onkeyup="if(isNaN(value))execCommand('undo')" onafterpaste="if(isNaN(value))execCommand('undo')"&gt;
&lt;input name=txt1 onchange="if(/\D/.test(this.value)){alert('只能输入数字');this.value='';}"&gt;
3.数字和小数点方法二
&lt;input type=text tvalue="" ovalue="" onkeypress="if(!this.value.match(/^[\+\-]?\d*?\.?\d*?$/))this.value=this.t_value;else this.tvalue=this.value;if(this.value.match(/^(?:[\+\-]?\d+(?:\.\d+)?)?$/))this.ovalue=this.value" onkeyup="if(!this.value.match(/^[\+\-]?\d*?\.?\d*?$/))this.value=this.t_value;else this.tvalue=this.value;if(this.value.match(/^(?:[\+\-]?\d+(?:\.\d+)?)?$/))this.ovalue=this.value" onblur="if(!this.value.match(/^(?:[\+\-]?\d+(?:\.\d+)?|\.\d*?)?$/))this.value=this.o_value;else{if(this.value.match(/^\.\d+$/))this.value=0+this.value;if(this.value.match(/^\.$/))this.value=0;this.ovalue=this.value}"&gt;
4.只能输入字母和汉字
&lt;input onkeyup="value=value.replace(/[\d]/g,'') "onbeforepaste="clipboardData.setData('text',clipboardData.getData('text').replace(/[\d]/g,''))" maxlength=10 name="Numbers"&gt;
5.只能输入英文字母和数字,不能输入中文
&lt;input onkeyup="value=value.replace(/[^\w\.\/]/ig,'')"&gt;
6.只能输入数字和英文&lt;font color="Red"&gt;chun&lt;/font&gt;
&lt;input onKeyUp="value=value.replace(/[^\d|chun]/g,'')"&gt;
7.小数点后只能有最多两位(数字,中文都可输入),不能输入字母和运算符号:
&lt;input onKeyPress="if((event.keyCode&lt;48 || event.keyCode&gt;57) &amp;&amp; event.keyCode!=46 || /\.\d\d$/.test(value))event.returnValue=false"&gt;
8.小数点后只能有最多两位(数字,字母,中文都可输入),可以输入运算符号:
&lt;input onkeyup="this.value=this.value.replace(/^(\-)*(\d+)\.(\d\d).*$/,'$1$2.$3')"&gt;
————————————————————————————————————————
只能输入汉字：
&lt;input onkeyup="value=value.replace(/[^\u4E00-\u9FA5]/g,'')" onbeforepaste="clipboardData.setData('text',clipboardData.getData('text').replace(/[^\u4E00-\u9FA5]/g,''))"&gt;
只能输入数字：
&lt;input onkeyup="value=value.replace(/[^\d]/g,'') "onbeforepaste="clipboardData.setData('text',clipboardData.getData('text').replace(/[^\d]/g,''))"&gt;

只能输入英文和数字：
&lt;input onkeyup="value=value.replace(/[\W]/g,'') "onbeforepaste="clipboardData.setData('text',clipboardData.getData('text').replace(/[^\d]/g,''))"&gt;
控制输入框只能输入文字或数字，也可以不允许输入特殊字符
这里不允许输入如下字符: (像 !@#$%^&amp;* 等)&lt;br&gt;
&lt;textarea rows=2 cols=20 name=comments onKeypress="if ((event.keyCode &gt; 32 &amp;&amp; event.keyCode &lt; 48) || (event.keyCode &gt; 57 &amp;&amp; event.keyCode &lt; 65) || (event.keyCode &gt; 90 &amp;&amp; event.keyCode &lt; 97)) event.returnValue = false;"&gt;
只禁止空格输入
onkeyup="value=value.replace(/\s/g,'')"
只能输入中文和英文：
onkeyup="value=value.replace(/[^\a-zA-Z\u4E00-\u9FA5]/g,'')" onbeforepaste="clipboardData.setData('text',clipboardData.getData('text').replace(/[^\a-zA-Z\u4E00-\u9FA5]/g,''))"







</pre>
<br />