<pre class="prettyprint lang-js linenums">function GetDateStr(AddDayCount) {   
   var dd = new Date();  
   dd.setDate(dd.getDate()+AddDayCount);//获取AddDayCount天后的日期  
   var y = dd.getFullYear();   
   var m = (dd.getMonth()+1)&lt;10?"0"+(dd.getMonth()+1):(dd.getMonth()+1);//获取当前月份的日期，不足10补0  
   var d = dd.getDate()&lt;10?"0"+dd.getDate():dd.getDate();//获取当前几号，不足10补0  
   return y+"-"+m+"-"+d;   
}  
  
  
console.log("半年前："+GetDateStr(-180));  
console.log("三月前："+GetDateStr(-90));  
console.log("一月前："+GetDateStr(-30));  
console.log("昨天："+GetDateStr(-1));  
console.log("今天："+GetDateStr(0));  
console.log("明天："+GetDateStr(1));  
console.log("后天："+GetDateStr(2));  
console.log("一月后："+GetDateStr(30));  
console.log("三月后："+GetDateStr(90));  
console.log("半年后："+GetDateStr(180));   </pre>