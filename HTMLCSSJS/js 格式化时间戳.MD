<br />
var formatDate=function (now) {&nbsp;<br />
var year=now.getFullYear();&nbsp;<br />
var month=now.getMonth()+1;&nbsp;<br />
var date=now.getDate();&nbsp;<br />
var hour=now.getHours();&nbsp;<br />
var minute=now.getMinutes();&nbsp;<br />
var second=now.getSeconds();&nbsp;<br />
&nbsp; &nbsp;if (month &lt; 10) month = "0" + month;<br />
&nbsp; &nbsp;if (date &lt; 10) date = "0" + date;<br />
&nbsp; &nbsp;if (hour &lt; 10) hour = "0" + hour;<br />
&nbsp; &nbsp;if (minute &lt; 10) minute = "0" + minute;<br />
&nbsp; &nbsp;if (second &lt; 10) second = "0" + second;<br />
return year+"-"+month+"-"+date+" "+hour+":"+minute+":"+second;&nbsp;<br />
};<br />