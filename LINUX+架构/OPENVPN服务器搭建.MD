<pre class="prettyprint lang-js linenums">http://blog.csdn.net/technofiend/article/details/52452572</pre>
<pre class="prettyprint lang-js linenums">docker OPENVPN服务器搭建

我的服务器系统是centos 7.0，将下面一步步贴到shell（ssh、vps）执行即可。

// 第一步
yum install <span style="color:#555555;font-family:consolas, Menlo, &quot;font-size:13px;text-align:justify;white-space:normal;background-color:#EEEEEE;">docker.io</span> docker pull kylemanna/openvpn

OVPN_DATA="/root/ovpn-data"
// 下面的全局变量换成你的服务器的外网ip
IP="xxx.xxx.xxx.xxx"
mkdir ${OVPN_DATA}

// 第二步
docker run -v ${OVPN_DATA}:/etc/openvpn --rm kylemanna/openvpn ovpn_genconfig -u tcp://${IP}

// 第三步
docker run -v ${OVPN_DATA}:/etc/openvpn --rm -it kylemanna/openvpn ovpn_initpki

// ---------------------------------------------------------
Enter PEM pass phrase: 输入123456（你是看不见的）
Verifying - Enter PEM pass phrase: 输入123456（你是看不见的）
Common Name (eg: your user, host, or server name) [Easy-RSA CA]:回车一下
Enter pass phrase for /etc/openvpn/pki/private/ca.key:输入123456
// ---------------------------------------------------------

// 第五步
docker run -v ${OVPN_DATA}:/etc/openvpn --rm -it kylemanna/openvpn easyrsa build-client-full CLIENTNAME nopass

// ---------------------------------------------------------
Enter pass phrase for /etc/openvpn/pki/private/ca.key:输入123456
// ---------------------------------------------------------

// 第六步
docker run -v ${OVPN_DATA}:/etc/openvpn --rm kylemanna/openvpn ovpn_getclient CLIENTNAME &gt; ${OVPN_DATA}/CLIENTNAME.ovpn

// 第七步
docker run --name openvpn -v ${OVPN_DATA}:/etc/openvpn -d -p 1194:1194 --privileged kylemanna/openvpn

经过以上七个步骤，你将会在/root/ovpn-data中看到一个CLIENTNAME.ovpn文件，将其下载到本地，利用OpenVPN GUI连接，即可。

经过整理后即：

yum install docker
docker pull kylemanna/openvpn
OVPN_DATA="/root/ovpn-data"
IP="123.123.123.123"
mkdir ${OVPN_DATA}
docker run -v ${OVPN_DATA}:/etc/openvpn --rm kylemanna/openvpn ovpn_genconfig -u tcp://${IP}
docker run -v ${OVPN_DATA}:/etc/openvpn --rm -it kylemanna/openvpn ovpn_initpki
docker run -v ${OVPN_DATA}:/etc/openvpn --rm -it kylemanna/openvpn easyrsa build-client-full CLIENTNAME nopass
docker run -v ${OVPN_DATA}:/etc/openvpn --rm kylemanna/openvpn ovpn_getclient CLIENTNAME &gt; ${OVPN_DATA}/CLIENTNAME.ovpn
docker run --name openvpn -v ${OVPN_DATA}:/etc/openvpn -d -p 1194:1194 --privileged kylemanna/openvpn

OPENVPN连接

下载openvpn，http://openvpn.net/index.php/open-source/downloads.html，并安装。 
将CLIENTNAME.ovpn复制到C:\Program Files\OpenVPN\config中。

编辑CLIENTNAME.ovpn文件，将里面的udp改成tcp。至于为什么，嘿嘿嘿，听说免什么什么流量的。

运行OpenVPN GUI，在桌面右下角，可以看到OpenVPN 的图标。右键点击connect即可连接VPN。不信，你可以在百度输入IP，查看下自己的IP。

误区

有人把openvpn客户端和服务端混在一起配置了。 
其实它的服务器和客户端都在一个软件之中。但是服务器有服务器的配置方法，客户端有客户端的配置方法而已。 
对了，这个人就是我。</pre>
<pre class="prettyprint lang-js linenums"></pre>
<pre class="prettyprint lang-js linenums"></pre>
<pre class="prettyprint lang-js linenums">配置文件很关键啊  </pre>
<pre class="prettyprint lang-js linenums">```</pre>
<pre class="prettyprint lang-js linenums">duplicate-cn
max-clients 10
</pre>
<pre class="prettyprint lang-js linenums">```</pre>
<pre class="prettyprint lang-js linenums"></pre>
<pre class="prettyprint lang-js linenums">

<pre class="prettyprint lang-js linenums">$ vim /etc/openvpn/server.conf

#本机要侦听使用的IP地址
local 192.168.1.201
#使用的端口，默认1194
port 1194
#改成tcp，默认使用udp，如果使用HTTP Proxy，必须使用tcp协议
proto tcp
#使用的设备可选tap和tun，tap是二层设备，支持链路层协议。
#tun是ip层的点对点协议，限制稍微多一些，建议使用tun,如果使用桥接的话，就必须要使用tap
dev tun
#路径前面加keys，全路径为/etc/openvpn/keys/ca.crt
#OpenVPN使用的ROOT CA，使用build-ca生成的，用于验证客户是证书是否合法
ca keys/ca.crt
#Server使用的证书文件
cert keys/server.crt
#Server使用的证书对应的key，注意文件的权限，防止被盗
key keys/server.key  # This file should be kept secret
dh keys/dh2048.pem
#注销用户需要增加
#crl-verify /usr/share/easy-rsa/2.0/keys/crl.pem
#默认虚拟局域网网段，不要和实际的局域网冲突即可
server 10.8.0.0 255.255.255.0
#用于记录某个Client获得的IP地址，类似于dhcpd.lease文件，
#防止openvpn重新启动后“忘记”Client曾经使用过的IP地址
ifconfig-pool-persist ipp.txt
#通过VPN Server往Client push路由，client通过pull指令获得Server push的所有选项并应用
#10.0.0.0/8是我这台VPN服务器所在的内网的网段，读者应该根据自身实际情况进行修改
push "route 10.0.0.0 255.0.0.0"
#配置客户端dns
push "dhcp-option DNS 114.114.114.114"
push "dhcp-option DNS 8.8.4.4"
#可以让客户端之间相互访问直接通过openvpn程序转发，根据需要设置
#不用发送到tun或者tap设备后重新转发，优化Client to Client的访问效率
client-to-client
#如果客户端都使用相同的证书和密钥连接VPN，一定要打开这个选项，否则每个证书只允许一个人连接VPN,建议一人一个证书。
duplicate-cn
#定义最大连接数
max-clients 10
#NAT后面使用VPN，如果VPN长时间不通信，NAT Session可能会失效，
#导致VPN连接丢失，为防止之类事情的发生，keepalive提供一个类似于ping的机制，
#下面表示每10秒通过VPN的Control通道ping对方，如果连续120秒无法ping通，
#认为连接丢失，并重新启动VPN，重新连接
#(对于mode server模式下的openvpn不会重新连接)。
keepalive 10 120
tls-auth keys/ta.key 0 # This file is secret
#对数据进行压缩，注意Server和Client一致
comp-lzo
#通过keepalive检测超时后，重新启动VPN，不重新读取keys，保留第一次使用的keys
persist-key
#通过keepalive检测超时后，重新启动VPN，一直保持tun或者tap设备是linkup的，
#否则网络连接会先linkdown然后linkup
persist-tun
#OpenVPN的状态日志，默认为/etc/openvpn/openvpn-status.log
status openvpn-status.log
#OpenVPN的运行日志，默认为/etc/openvpn/openvpn.log，和log一致，每次重新启动openvpn后保留原有的log信息，新信息追加到文件最后 
log-append  /var/log/openvpn/openvpn.log
#相当于debug level
verb 3</pre>
<br />
</pre>