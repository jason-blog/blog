<div style="white-space:nowrap;">
<pre class="prettyprint lang-html linenums">&lt;!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd"&gt;
&lt;html&gt;
 &lt;head&gt;
  &lt;meta http-equiv="content-type" content="text/html; charset=utf-8"&gt;
  &lt;title&gt; Local Storage and Session Storage &lt;/title&gt;
 &lt;/head&gt;

 &lt;body&gt;
  &lt;p&gt;姓名:&lt;input type="text" name="name" id="name"&gt;&lt;/p&gt;
  &lt;p&gt;性别:&lt;input type="radio" name="gender" id="gender1" value="1"&gt; 男 &lt;input type="radio" name="gender" id="gender2" value="2"&gt; 女&lt;/p&gt;
  &lt;p&gt;&lt;input type="button" id="saveBtn" value="save"&gt; &lt;input type="button" id="getBtn" value="get"&gt; &lt;input type="button" id="removeBtn" value="remove name"&gt; &lt;input type="button" id="clearBtn" value="clear"&gt; &lt;/p&gt;

  &lt;script type="text/javascript"&gt;
var oStorage = window.localStorage;

function $(id){
return document.getElementById(id);
}

// 保存数据
$('saveBtn').onclick = function(){
oStorage.setItem('name', $('name').value);

if($('gender1').checked==true){
oStorage.setItem('gender', 1);
}else if($('gender2').checked==true){
oStorage.setItem('gender', 2);
}
}

// 获取数据
$('getBtn').onclick = function(){
$('name').value = oStorage.getItem('name');
if(oStorage.getItem('gender')==1){
$('gender1').checked = true;
}else if(oStorage.getItem('gender')==2){
$('gender2').checked = true;
}
}

// 删除数据name
$('removeBtn').onclick = function(){
oStorage.removeItem('name');
}

// 清空数据
$('clearBtn').onclick = function(){
oStorage.clear();
}

  &lt;/script&gt;

 &lt;/body&gt;
&lt;/html&gt;
</pre>
<br />
</div>