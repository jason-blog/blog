<br />
&nbsp;var cookieUtil={<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; set :function(name,value,expires,path,domain,secure){<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; var cookieText=encodeURIComponent(name)+'='+<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; encodeURIComponent(value);<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; if(expires instanceof Date){<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; cookieText+=';expires='+expires.toGMTString();<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; if(path){<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; cookieText+=';path='+path;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; if(domain){<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; cookieText+=';domain='+domain;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; if(secure){<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; cookieText+=';secure';<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; document.cookie=cookieText; &nbsp; &nbsp; &nbsp; &nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; get:function(name){<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; var cookieName=encodeURIComponent(name)+'=',<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; cookieStart=document.cookie.indexOf(cookieName),<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; cookieValue=null;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; if(cookieStart&gt;-1){<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; var cookieEnd=document.cookie.indexOf(';',cookieStart);<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; if(cookieEnd==-1){<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; cookieEnd=document.cookie.length;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; cookieValue=decodeURIComponent(document.cookie.substring(cookieStart+cookieName.length,cookieEnd))<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; return cookieValue;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; },<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; unset:function(name,path,domain,secure){<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; this.set(name,'',new Date(0),domain,path)<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; &nbsp;function setCookieDate(day){<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;var date=null;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;if(typeof day=='number'&amp;&amp;day&gt;0){<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;date=new Date();<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;date.setDate(date.getDate()+day);<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;}else{<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; throw new Error('!!') &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;}<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;return date;<br />
&nbsp; &nbsp; &nbsp; &nbsp;}<br />
<br />
<br />
function getQueryString(name) {<br />
&nbsp; &nbsp; var reg = new RegExp('(^|&amp;)' + name + '=([^&amp;]*)(&amp;|$)', 'i');<br />
&nbsp; &nbsp; var r = window.location.search.substr(1).match(reg);<br />
&nbsp; &nbsp; if (r != null) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; return unescape(r[2]);<br />
&nbsp; &nbsp; }<br />
&nbsp; &nbsp; return null;<br />
}<br />
<div style="white-space:nowrap;">
	<br />
</div>