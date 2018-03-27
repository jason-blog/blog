<pre style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">

<pre style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;"><span style="margin:0px;padding:0px;line-height:1.5 !important;">#本地圆环地址就是那个127.0.0.1，是本机上使用的,它进与出都设置为允许</span></pre>
<pre style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">#允许本地回环地址可以正常使用</pre>
</pre>
<pre style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">iptables -A INPUT -i lo -<span style="margin:0px;padding:0px;line-height:1.5 !important;">j ACCEPT  
iptables </span>-A OUTPUT -o lo -j ACCEPT</pre>
<pre style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;"></pre>
<pre style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">#允许ssh端口连接</pre>
<pre style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">

<pre style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">iptables -A INPUT -s <span style="margin:0px;padding:0px;color:#800080;line-height:1.5 !important;">192.168</span>.<span style="margin:0px;padding:0px;color:#800080;line-height:1.5 !important;">1.0</span>/<span style="margin:0px;padding:0px;color:#800080;line-height:1.5 !important;">24</span> -p tcp --dport <span style="margin:0px;padding:0px;color:#800080;line-height:1.5 !important;">22</span> -j ACCEPT </pre>
#允许某一ip所有端口<br />
iptables -A INPUT -s yourip/32 -j ACCEPT</pre>
<pre style="margin-top:0px;margin-bottom:0px;padding:0px;word-wrap:break-word;">

<pre style="font-family:&quot;white-space:pre-wrap;margin-top:0px;margin-bottom:0px;padding:0px;word-wrap:break-word;">iptables -A INPUT -p tcp --dport <span style="margin:0px;padding:0px;color:#800080;line-height:1.5 !important;">80</span> -<span style="margin:0px;padding:0px;line-height:1.5 !important;">j ACCEPT #开启80端口，因为web对外都是这个端口
iptables </span>-A INPUT -p icmp --icmp-type <span style="margin:0px;padding:0px;color:#800080;line-height:1.5 !important;">8</span> -<span style="margin:0px;padding:0px;line-height:1.5 !important;">j ACCEPT #允许被ping
iptables </span>-A INPUT -m state --state ESTABLISHED,RELATED -<span style="margin:0px;padding:0px;line-height:1.5 !important;">j ACCEPT #已经建立的连接得让它进来</span></pre>
<pre style="font-family:&quot;white-space:pre-wrap;margin-top:0px;margin-bottom:0px;padding:0px;word-wrap:break-word;"><span style="margin:0px;padding:0px;line-height:1.5 !important;">配置默认
<pre style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">iptables -<span style="margin:0px;padding:0px;line-height:1.5 !important;">P INPUT DROP #配置默认的不让进
iptables </span>-<span style="margin:0px;padding:0px;line-height:1.5 !important;">P FORWARD DROP #默认的不允许转发
iptables </span>-P OUTPUT ACCEPT #默认的可以出去</pre>
</span></pre>
<span style="white-space:pre-wrap;"> </span> 
<pre style="font-family:&quot;white-space:pre-wrap;margin-top:0px;margin-bottom:0px;padding:0px;word-wrap:break-word;"></pre>
<span style="white-space:pre-wrap;"> </span> 
<pre style="font-family:&quot;white-space:pre-wrap;margin-top:0px;margin-bottom:0px;padding:0px;word-wrap:break-word;">-p tcp是指按照tcp协议操作
-m tcp是指装入tcp的协议
</pre>
<span style="white-space:pre-wrap;"> </span> 
<pre style="font-family:&quot;white-space:pre-wrap;margin-top:0px;margin-bottom:0px;padding:0px;word-wrap:break-word;"><span style="font-family:&quot;"> </span></pre>
<span style="font-family:'sans serif, tahoma, verdana, helvetica';"><span style="white-space:nowrap;"> </span></span></pre>
<pre style="margin-top:0px;margin-bottom:0px;padding:0px;word-wrap:break-word;"></pre>