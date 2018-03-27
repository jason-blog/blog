<div class="para-title level-3" label-module="para-title" style="clear:both;zoom:1;margin:20px 0px 12px;line-height:20px;font-size:18px;font-family:&quot;color:#333333;white-space:normal;background-color:#FFFFFF;">
	<h3 class="title-text" style="margin:0px;padding:0px;font-size:18px;font-weight:400;">
		找出ARP病毒源
	</h3>
</div>
<div class="para" label-module="para" style="font-size:14px;color:#333333;margin-bottom:15px;text-indent:2em;line-height:24px;zoom:1;font-family:arial, 宋体, sans-serif;white-space:normal;background-color:#FFFFFF;">
	第一招：使用Sniffer<a target="_blank" href="http://baike.baidu.com/item/%E6%8A%93%E5%8C%85" style="color:#136EC2;text-decoration-line:none;">抓包</a>
</div>
<div class="para" label-module="para" style="font-size:14px;color:#333333;margin-bottom:15px;text-indent:2em;line-height:24px;zoom:1;font-family:arial, 宋体, sans-serif;white-space:normal;background-color:#FFFFFF;">
	在网络内任意一台<a target="_blank" href="http://baike.baidu.com/item/%E4%B8%BB%E6%9C%BA" style="color:#136EC2;text-decoration-line:none;">主机</a>上运行抓包软件，捕获所有到达本机的数据包。如果发现有某个IP不断发送
</div>
<div class="para" label-module="para" style="font-size:14px;color:#333333;margin-bottom:15px;text-indent:2em;line-height:24px;zoom:1;font-family:arial, 宋体, sans-serif;white-space:normal;background-color:#FFFFFF;">
	ARP　Request请求包，那么这台电脑一般就是病毒源。原理：无论何种ARP病毒变种，行为方式有两种，一是欺骗网关，二是欺骗网内的所有主机。最终的结果是，在<a target="_blank" href="http://baike.baidu.com/item/%E7%BD%91%E5%85%B3" style="color:#136EC2;text-decoration-line:none;">网关</a>的ARP缓存表中，网内所有活动主机的MAC地址均为中毒主机的MAC地址；网内所有主机的ARP缓存表中，网关的MAC地址也成为中毒主机的MAC地址。前者保证了从网关到网内主机的数据包被发到中毒主机，后者相反，使得主机发往网关的数据包均发送到中毒主机。
</div>
<div class="para" label-module="para" style="font-size:14px;color:#333333;margin-bottom:15px;text-indent:2em;line-height:24px;zoom:1;font-family:arial, 宋体, sans-serif;white-space:normal;background-color:#FFFFFF;">
	第二招：使用arp -a命令任意选两台不能上网的<a target="_blank" href="http://baike.baidu.com/item/%E4%B8%BB%E6%9C%BA" style="color:#136EC2;text-decoration-line:none;">主机</a>，在DOS命令窗口下运行arp -a命令。例如在结果中，两台电脑除了网关的IP，MAC地址对应项，都包含了192.168.0.186的这个IP，则可以断定192.168.0.186这台主机就是病毒源。原理：一般情况下，网内的主机只和<a target="_blank" href="http://baike.baidu.com/item/%E7%BD%91%E5%85%B3" style="color:#136EC2;text-decoration-line:none;">网关</a>通信。正常情况下，一台主机的ARP缓存中应该只有网关的MAC地址。如果有其他主机的MAC地址，说明<a target="_blank" href="http://baike.baidu.com/item/%E6%9C%AC%E5%9C%B0%E4%B8%BB%E6%9C%BA" style="color:#136EC2;text-decoration-line:none;">本地主机</a>和这台主机最后有过数据通信发生。如果某台主机（例如上面的192.168.0.186）既不是网关也不是服务器，但和网内的其他主机都有通信活动，且此时又是ARP病毒发作时期，那么，病毒源也就是它了。
</div>
<div class="para" label-module="para" style="font-size:14px;color:#333333;margin-bottom:15px;text-indent:2em;line-height:24px;zoom:1;font-family:arial, 宋体, sans-serif;white-space:normal;background-color:#FFFFFF;">
	第三招：使用tracert命令在任意一台受影响的<a target="_blank" href="http://baike.baidu.com/item/%E4%B8%BB%E6%9C%BA" style="color:#136EC2;text-decoration-line:none;">主机</a>上，在DOS命令窗口下运行如下命令：tracert61.135.179.148。假定设置的<a target="_blank" href="http://baike.baidu.com/item/%E7%BC%BA%E7%9C%81%E7%BD%91%E5%85%B3" style="color:#136EC2;text-decoration-line:none;">缺省网关</a>为10.8.6.1，在跟踪一个外网地址时，第一跳却是10.8.6.186，那么，10.8.6.186就是病毒源。原理：中毒主机在受影响主机和网关之间，扮演了“中间人”的角色。所有本应该到达网关的<a target="_blank" href="http://baike.baidu.com/item/%E6%95%B0%E6%8D%AE%E5%8C%85" style="color:#136EC2;text-decoration-line:none;">数据包</a>，由于错误的MAC地址，均被发到了中毒主机。此时，中毒主机越俎代庖，起了缺省网关的作用。
</div>