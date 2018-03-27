<p>
	<br />
</p>
<p>
	$(function() {<br />
&nbsp;$("#moneyCount").keyup(function() {<br />
&nbsp;	if($(this).val())<br />
&nbsp; &nbsp; 				 &nbsp; &nbsp;$(this).val($(this).val().replace(/[^0-9]/g, ''));<br />
&nbsp; 				 &nbsp; &nbsp; }).bind("blur",function(){<br />
if($(this).val())<br />
&nbsp; $(this).val(parseInt($(this).val().replace(/[^0-9]/g, '')));<br />
});<br />
});<br />
</p>
<p>
	<br />
</p>
<p>
	<br />
</p>
<p>
	$(function() {
</p>
&nbsp;$("input[name='moneyCount']").keyup(function() {<br />
$(this).val($(this).val().match(/^([0-9])+[\.]?([0-9]){0,2}/g));<br />
&nbsp; &nbsp; }).bind("blur",function(){<br />
&nbsp; var val=$(this).val();<br />
&nbsp; if (val) {<br />
&nbsp; 	var val = val.match(/^([0-9])+([\.]?[0-9]{0,2})?/g);<br />
&nbsp; 	if (String(val).indexOf('.') &gt; 0)&nbsp;<br />
&nbsp; 		val = parseFloat(val).toFixed(2);else val = parseInt(val);<br />
&nbsp; &nbsp;		 &nbsp; 	$(this).val(val);<br />
<p>
	&nbsp; }});});
</p>
<p>
	<br />
</p>
<p>
	<br />
</p>