<pre class="prettyprint lang-js linenums">&lt;script&gt;

$(function(){
$("#mcancel").click(function(){
	  var order=$(this).attr('data');
	  $.post("/user.php?s=/Moneyout_moneyOutCancel",{order:order},function(result){
		  result= eval('('+result+')');
		  if(result.status==1){
			  location.reload();
		  }else{
			  alert('取消失败！');
		  }
	  });
	});
});



$(function(){
	    data={ajaxpage:1};
	    url="/index.php?s=/Index_mgJackPotajax.html";
	  	$.ajax({
		    type : "POST",
		    url  : url ,
		    data : data ,
		    dataType:'json',
			beforeSend : function (XMLHttpRequest) {
	            XMLHttpRequest.setRequestHeader("request_type","ajax");
	        },
		    success:function(response,textStatus,jqHXR){
		    		  var num=response.data[jack];
		    	
		    	
		      }
		   });
});








&lt;/script&gt;</pre>