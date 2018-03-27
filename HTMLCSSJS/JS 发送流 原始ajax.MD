&lt;script&gt;<br />
//javascript发送流<br />
<br />
function createXmlObj(){&nbsp;<br />
&nbsp;var signatures = ["Msxml2.DOMDocument.5.0","Msxml2.DOMDocument.4.0","Msxml2.DOMDocument.3.0","Msxml2.DOMDocument","Microsoft.XmlDom"];<br />
&nbsp;for(var i = 0;i&lt;signatures.length;i++){&nbsp;<br />
&nbsp; try{&nbsp;<br />
&nbsp; &nbsp;var xmlDom = new ActiveXObject(signatures[i]);&nbsp;<br />
&nbsp; }catch(e){&nbsp;<br />
&nbsp; &nbsp;//忽略错误,继续测试下一个版本&nbsp;<br />
&nbsp; }&nbsp;<br />
&nbsp;}&nbsp;<br />
&nbsp;return xmlDom.xml;&nbsp;<br />
}&nbsp;<br />
<br />
/*&nbsp;<br />
创建XMLHttpRequest请求对象&nbsp;<br />
*/&nbsp;<br />
function createXMLhttp(){&nbsp;<br />
&nbsp;var xmlhttp;&nbsp;<br />
&nbsp;try{&nbsp;<br />
&nbsp; xmlhttp = new ActiveXObject("Msxml2.XMLHTTP");&nbsp;<br />
&nbsp;}catch(e){&nbsp;<br />
&nbsp; try{&nbsp;<br />
&nbsp; &nbsp;xmlhttp = new ActiveXObject("Microsoft.XMLHTTP");&nbsp;<br />
&nbsp; }catch(e){&nbsp;<br />
&nbsp; &nbsp;try{&nbsp;<br />
&nbsp; &nbsp; xmlhttp = new XMLHttpRequest();&nbsp;<br />
&nbsp; &nbsp;}catch(e){}&nbsp;<br />
&nbsp; }&nbsp;<br />
&nbsp;}&nbsp;<br />
&nbsp;return xmlhttp;&nbsp;<br />
}&nbsp;<br />
<br />
function sendInfor(){&nbsp;<br />
//var XmlObj = createXmlObj();&nbsp;<br />
//alert(XmlObj);&nbsp;<br />
//根据不同的浏览器创建不同的XMLHttpRequest对象&nbsp;<br />
var xmlhttp = createXMLhttp();&nbsp;<br />
xmlhttp.open("post",'/index.php?s=/Index_ceshi',false);&nbsp;<br />
//设置请求的HTTP头&nbsp;<br />
<br />
<br />
&nbsp; &nbsp;//xmlhttp.setRequestHeader("Content-Type","application/x-www-form-urlencoded"); &nbsp; &nbsp;可以用$_POST 接收<br />
//xmlhttp.send("user=SDFSD&amp;password=SDFSF");&nbsp;<br />
<br />
&nbsp; &nbsp; xmlhttp.setRequestHeader("Content-Type","text/xml;charset=UTF-8"); &nbsp;<br />
//xmlhttp.setRequestHeader("Content-Type","text/html;charset=UTF-8"); &nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;//text/plain;charset=UTF-8&nbsp;<br />
&nbsp;<br />
&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;//xmlhttp.send(JSON.stringify(objects)); 		&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;xmlhttp.send("ceshiyixia"); 		&nbsp;<br />
&nbsp; &nbsp; xmlhttp.onreadystatechange=function(){&nbsp;<br />
&nbsp; &nbsp; if (xmlhttp.readyState==4){&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;alert("发送成功!");&nbsp;<br />
&nbsp;var aa = xmlhttp.ResponseText;<br />
&nbsp;alert(aa);<br />
&nbsp; &nbsp; }&nbsp;<br />
&nbsp; } &nbsp;&nbsp;<br />
&nbsp; &nbsp;//发送请求&nbsp;<br />
&nbsp;<br />
&nbsp; // var aa = xmlhttp.ResponseText;//得到后台传递过来的text文本信息&nbsp;<br />
<br />
<br />
//var test =xmlhttp.responseStream;//得到后台传递过来的输入流信息--一般不用&nbsp;<br />
//alert(aa);&nbsp;<br />
//把后台传递过来的信息aa用js放到页面中指定的位置&nbsp;<br />
}&nbsp;<br />
&lt;/script&gt;<br />