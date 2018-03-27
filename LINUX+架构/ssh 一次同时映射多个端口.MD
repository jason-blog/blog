<p style="color:#333333;font-size:14px;white-space:normal;background-color:#FFFFFF;line-height:25px;margin-top:0px;margin-bottom:10px;padding-top:0px;padding-bottom:0px;font-family:Arial, Helvetica, simsun, u5b8bu4f53;">
	<strong>一次同时映射多个端口</strong>
</p>
<pre style="white-space:pre-wrap;word-wrap:break-word;color:#333333;font-size:14px;line-height:25px;background-color:#FFFFFF;">ssh -L 8888:www.host.com:80 -L 110:mail.host.com:110 -L    25:mail.host.com:25 user@host -N  </pre>