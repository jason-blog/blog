<p style="margin:10px auto;padding:0px;white-space:normal;">
	以前，一直以为在SpringMVC环境中，@RequestBody接收的是一个Json对象，一直在调试代码都没有成功，后来发现，其实 @RequestBody接收的是一个Json对象的字符串，而不是一个Json对象。然而在ajax请求往往传的都是Json对象，后来发现用 JSON.stringify(data)的方式就能将对象变成字符串。同时ajax请求的时候也要指定dataType: "json",contentType:"application/json" 这样就可以轻易的将一个对象或者List传到Java端，使用@RequestBody即可绑定对象或者List.
</p>
<p style="margin:10px auto;padding:0px;white-space:normal;">
	JavaScript 代码：
</p>
<div class="cnblogs_code" style="margin:5px 0px;padding:5px;background-color:#F5F5F5;border:1px solid #CCCCCC;overflow:auto;white-space:normal;font-family:&quot;">
	<div class="cnblogs_code_toolbar" style="margin:5px 0px 0px;padding:0px;">
		<br />
	</div>
<pre style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">&lt;script type="text/javascript"&gt;<span style="margin:0px;padding:0px;line-height:1.5 !important;"> $(document).ready(</span><span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">function</span><span style="margin:0px;padding:0px;line-height:1.5 !important;">(){ </span><span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">var</span> saveDataAry=<span style="margin:0px;padding:0px;line-height:1.5 !important;">[]; </span><span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">var</span> data1={"userName":"test","address":"gz"<span style="margin:0px;padding:0px;line-height:1.5 !important;">}; </span><span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">var</span> data2={"userName":"ququ","address":"gr"<span style="margin:0px;padding:0px;line-height:1.5 !important;">};  
        saveDataAry.push(data1);  
        saveDataAry.push(data2);         
        $.ajax({ 
            type:</span>"POST"<span style="margin:0px;padding:0px;line-height:1.5 !important;">, 
            url:</span>"user/saveUser"<span style="margin:0px;padding:0px;line-height:1.5 !important;">, 
            dataType:</span>"json"<span style="margin:0px;padding:0px;line-height:1.5 !important;">,      
            contentType:</span>"application/json"<span style="margin:0px;padding:0px;line-height:1.5 !important;">,               
            data:JSON.stringify(saveData), 
            success:</span><span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">function</span><span style="margin:0px;padding:0px;line-height:1.5 !important;">(data){ 
                                       
            } 
         }); 
    }); </span>&lt;/script&gt; </pre>
	<div class="cnblogs_code_toolbar" style="margin:5px 0px 0px;padding:0px;">
		<br />
	</div>
</div>
<p style="margin:10px auto;padding:0px;white-space:normal;">
	Java代码
</p>
<div class="cnblogs_code" style="margin:5px 0px;padding:5px;background-color:#F5F5F5;border:1px solid #CCCCCC;overflow:auto;white-space:normal;font-family:&quot;">
<pre style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">    @RequestMapping(value = "saveUser", method =<span style="margin:0px;padding:0px;line-height:1.5 !important;"> {RequestMethod.POST }}) 
    @ResponseBody </span><span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">public</span> <span style="margin:0px;padding:0px;color:#0000FF;line-height:1.5 !important;">void</span> saveUser(@RequestBody List&lt;User&gt;<span style="margin:0px;padding:0px;line-height:1.5 !important;"> users) { 
         userService.batchSave(users); 
    } </span></pre>
</div>