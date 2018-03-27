webbench最多可以模拟3万个并发连接去测试网站的负载能力，个人感觉要比Apache自带的ab压力测试工具好，安装使用也特别方便。<br />
<br />
1、适用系统：Linux<br />
<br />
2、编译安装：<br />
引用<br />
wget http://blog.zyan.cc/soft/linux/webbench/webbench-1.5.tar.gz<br />
tar zxvf webbench-1.5.tar.gz<br />
cd webbench-1.5<br />
make &amp;&amp; make install<br />
<br />
3、使用：<br />
引用<br />
webbench -c 500 -t 30 http://127.0.0.1/test.jpg<br />
参数说明：-c表示并发数，-t表示时间(秒)<br />
<br />
4、测试结果示例：<br />
引用<br />
Webbench - Simple Web Benchmark 1.5<br />
Copyright (c) Radim Kolar 1997-2004, GPL Open Source Software.<br />
<br />
Benchmarking: GET http://127.0.0.1/test.jpg<br />
500 clients, running 30 sec.<br />
<br />
Speed=3230 pages/min, 11614212 bytes/sec.<br />
Requests: 1615 susceed, 0 failed.<br />