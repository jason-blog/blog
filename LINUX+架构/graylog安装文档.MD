官方安装文档<br />
http://docs.graylog.org/en/2.3/pages/installation.html<br />
<br />
安装mogodb&nbsp;<br />
sudo apt-get install mongodb-server<br />
===============================================================<br />
或者下载源码 进入目录<br />
&nbsp;./bin/mongod --dbpath=/home/mongodb/mongodb-linux-x86_64-3.0.6/data --logpath=/home/mongodb/mongodb-linux-x86_64-3.0.6/mongo.log --logappend --port=27017 --fork<br />
============================================================<br />
安装Elasticsearch<br />
<br />
$ wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -<br />
$ echo "deb https://artifacts.elastic.co/packages/5.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-5.x.list<br />
$ sudo apt-get update &amp;&amp; sudo apt-get install elasticsearch<br />
<br />
修改 /etc/elasticsearch/elasticsearch.yml 中 cluster.name 为 graylog<br />
cluster.name: graylog<br />
<br />
reload 并重启 elasticsearch 服务<br />
$ sudo systemctl daemon-reload<br />
$ sudo systemctl enable elasticsearch.service<br />
$ sudo systemctl restart elasticsearch.service<br />
<br />
============================================================<br />
或者去官网https://www.elastic.co/downloads/elasticsearch下载源码&nbsp;<br />
得到源码后 unzip&nbsp;<br />
进入 cd elasticsearch-5.6.3/bin/&nbsp;<br />
elasticsearch -d 启动后台执行<br />
elasticsearch.yml 文件在 cd elasticsearch-5.6.3/config中<br />
<br />
=============================================================<br />
<br />
&nbsp;<br />
安装&nbsp; Graylog<br />
$ wget https://packages.graylog2.org/repo/packages/graylog-2.3-repository_latest.deb<br />
$ sudo dpkg -i graylog-2.3-repository_latest.deb<br />
$ sudo apt-get update &amp;&amp; sudo apt-get install graylog-server<br />
<br />
修改 /etc/graylog/server/server.conf 中的&nbsp;<br />
利用 pwgen -N 1 -s 96 修改 password_secret&nbsp;<br />
利用 echo -n test | sha256sum 生成 root_password_sha2 的密码 用于登录管理面板<br />
(管理面板默认用户名admin 密码为 sha256sum生成的 root_password_sha2 )<br />
<p>
	<br />
</p>
<p>
	password_secret =<br />
root_password_sha2 =<br />
root_timezone = Asia/Shanghai<br />
rest_listen_uri =&nbsp; http://0.0.0.0:9000/api/<br />
web_listen_uri = http://0.0.0.0:9000/<br />
allow_highlighting = true （运行查询结果高亮）<br />
elasticsearch_shards = 1 （当前只安装了一个elasticsearch）<br />
elasticsearch_index_prefix = graylog<br />
</p>
修改rest_listen_uri 和&nbsp; web_listen_uri 为可以访问的ip地址默认端口号为9000<br />
<br />
reload 和启动服务<br />
$ sudo systemctl daemon-reload<br />
$ sudo systemctl enable graylog-server.service<br />
$ sudo systemctl start graylog-server.service<br />
<br />
graylog-server的启动日志在 /var/log/graylog-server/server.log中<br />
所以启动的时候可以 tail -f /var/log/graylog-server/server.log<br />
<br />
<br />
&nbsp;========基本使用=======<br />
&nbsp;浏览器中输入url web_listen_uri:9000 用户名: admin 密码 设置的root_password_sha2<br />
&nbsp;<br />
新建 gelf ：<br />
&nbsp;<br />
<span style="white-space:pre;"> </span>进入 System &gt; Inputs &gt; Inputs in Cluster &gt; GELF HTTP Launch new input<br />
<span style="white-space:pre;"> </span>取名"http 12201" 完成创建<br />
<span style="white-space:pre;"> </span>任何安装curl的Linux机器上执行：<br />
&nbsp; &nbsp; curl -XPOST http://web_listen_uri/12201 -d '{"short_message":"这是一个测试", "host":"test.com", "facility":"test", "_foo":"bar"}'<br />
<br />
设置时区&nbsp;<br />
&nbsp; &nbsp; vim /etc/graylog/server/server.conf<br />
&nbsp; &nbsp; root_timezone = Asia/Shanghai&nbsp;<br />
&nbsp; &nbsp; 重启graylog-server服务<br />
<span style="white-space:pre;"> </span><br />
<span style="white-space:pre;"> </span><br />
===============docker安装=========================<br />
<br />
Graylog 官方提供了 docker 镜像：<br />
docker pull mongo:3<br />
docker pull elasticsearch:2<br />
docker pull graylog2/server:2.1.2-1<br />
<br />
docker-compose 拉起服务：<br />
<br />
version: '2'<br />
services:<br />
&nbsp; mongo:<br />
&nbsp; &nbsp; image: "mongo:3"<br />
&nbsp; &nbsp; volumes:<br />
&nbsp; &nbsp; &nbsp; &nbsp; - /data/mongo:/data/db<br />
&nbsp; elasticsearch:<br />
&nbsp; &nbsp; image: "elasticsearch:2"<br />
&nbsp; &nbsp; volumes:<br />
&nbsp; &nbsp; &nbsp; &nbsp; - /data/elasticsearch:/usr/share/elasticsearch/data<br />
&nbsp; &nbsp; command: "elasticsearch -Des.cluster.name='graylog'"<br />
&nbsp; graylog:<br />
&nbsp; &nbsp; image: graylog2/server:2.1.2-1<br />
&nbsp; &nbsp; environment:<br />
&nbsp; &nbsp; &nbsp; GRAYLOG_WEB_ENDPOINT_URI: http://x.x.x.x:9000/api<br />
&nbsp; &nbsp; depends_on:<br />
&nbsp; &nbsp; &nbsp; - mongo<br />
&nbsp; &nbsp; &nbsp; - elasticsearch<br />
&nbsp; &nbsp; ports:<br />
&nbsp; &nbsp; &nbsp; - "9000:9000"<br />
&nbsp; &nbsp; &nbsp; - "514:514"<br />
&nbsp; &nbsp; &nbsp; - "515:515"&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br />
<br />
docker-compose -f graylog.yml up -d<br />
<span style="white-space:pre;"> </span>浏览器访问 http://x.x.x.x:9000， 默认账户名和密码均为 admin，&nbsp;<br />
<span style="white-space:pre;"> </span><br />
log时间的问题 <span style="white-space:pre;"> </span><br />
https://github.com/Graylog2/graylog2-server/issues/2689&nbsp;<br />
<br />
<br />
<br />
<span style="white-space:pre;"> </span><br />
&nbsp;&nbsp;<br />