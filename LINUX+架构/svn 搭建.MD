WINDOWS<br />
================================================================<br />
1.DOWNLOAD TortoiseSVN（TortoiseSVN-1.4.5.10425-win32-svn-1.4.5.msi）<br />
2.安装 ing<br />
3.建立版本库<br />
&nbsp;(1)dos -&gt;&gt;&gt;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;mkdir svndemo<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;svnadmin create *******<br />
&nbsp;(2)windows -&gt;&gt;&gt;<br />
&nbsp; &nbsp; 右键-&gt;tortoiseSVN-&gt;Create Repository here ...<br />
4.进入conf文件夹配置<br />
5.运行DOS 》》》 svnserve -d -r 版本路径<br />
6.URL:<br />
&nbsp; &nbsp; &nbsp;svn://******/***<br />
======================================================================<br />
LINUX<br />
1.yum install subversion<br />
2.rpm -sl subversion<br />
&nbsp; svn --help<br />
&nbsp;&nbsp;<br />
3.创建版本库<br />
mkdir -p /var/svn/svnrepos<br />
4.创建版本库&nbsp;<br />
svnadmin create /var/svn/svnrepos<br />
5.进入conf目录<br />
authz文件是权限控制文件<br />
passwd是帐号密码文件<br />
svnserve.conf SVN服务配置文件<br />
6、设置帐号密码<br />
vi passwd<br />
在[users]块中添加用户和密码，格式：帐号=密码，如dan=dan<br />
<br />
7、设置权限<br />
vi authz<br />
在末尾添加如下代码：<br />
[/]<br />
dan=rw<br />
w=r<br />
意思是版本库的根目录dan对其有读写权限，w只有读权限。<br />
<br />
<br />
<br />
&nbsp; &nbsp;# vi /home/svn/project_1/conf/authz<br />
&nbsp; &nbsp; &nbsp; &nbsp; [groups]<br />
&nbsp; &nbsp; &nbsp; &nbsp; managers=manager1,manager2 &nbsp; &nbsp; &nbsp; &nbsp; #定义群组 managers 包含 manager1 和 manager2 两个用户<br />
&nbsp; &nbsp; &nbsp; &nbsp; [/]<br />
&nbsp; &nbsp; &nbsp; &nbsp; @managers=rw &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; #定义群组 managers 有读写权限<br />
&nbsp; &nbsp; &nbsp; &nbsp; manager3=r &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; #定义 manager3 有读权限<br />
&nbsp; &nbsp; &nbsp; &nbsp; *= &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; #以上没有定义的用户都没有任何权限<br />
<br />
<br />
<br />
8、修改svnserve.conf文件<br />
vi svnserve.conf<br />
打开下面的几个注释：<br />
anon-access = read #匿名用户可读<br />
auth-access = write #授权用户可写<br />
password-db = passwd #使用哪个文件作为账号文件<br />
authz-db = authz #使用哪个文件作为权限文件<br />
realm = /var/svn/svnrepos # 认证空间名，版本库所在目录<br />
<br />
9、启动svn版本库<br />
svnserve -d -r /var/svn/svnrepos<br />
<br />
<br />
开启多个版本库的时候要启动不同的端口 svnserve -d --listen-port 3688 -r /static/<br />
&nbsp;<br />
&nbsp;<br />
&nbsp;<br />
&nbsp;<br />
&nbsp;<br />
1，启动SVN&nbsp;<br />
sudo svnserve -d -r /home/data/svn/&nbsp;<br />
<br />
其中 -d 表示守护进程， -r 表示在后台执行&nbsp;<br />
/home/data/svn/ &nbsp;为svn的安装目录&nbsp;<br />
<br />
<br />
2，关闭SVN&nbsp;<br />
这里采取linux杀死进程的方式处理的&nbsp;<br />
ps -ef|grep svnserve&nbsp;<br />
root &nbsp; &nbsp; &nbsp;4967 &nbsp; &nbsp; 1 &nbsp;0 Aug23 ? &nbsp; &nbsp; &nbsp; &nbsp;00:00:00 svnserve -d -r repository/ &nbsp;<br />
这里 &nbsp;kill -9 4967杀死进程， 此4967为进程号 <br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
/×××××××××××××<br />
启动版本库的文件夹中可以分若干个<br />
svnadmin create /var/svn/svnrepos &nbsp;<br />
/×××××××××××××<br />
<br />
<br />
<br />
<br />
*************钩子程序*****************<br />
<br />
<br />
svn同步版本库到网站目录就是利用post-commit钩子：<br />
首先你要到网站目录(/var/www/test) checkout一份项目：<br />
svn://42.121.145.230/test_repo<br />
然后你要编辑钩子了，先copy一份：<br />
cp &nbsp;post-commit.tmpl post-commit<br />
全部注释掉后编辑：vi post-commit<br />
#!/bin/sh&nbsp;<br />
export LANG="zh_CN.UTF-8" &nbsp; &nbsp;#防止乱码&nbsp;<br />
svn update /var/www/test --username mckee --password phpddt.com --no-auth-cache&nbsp;<br />
<br />
<br />
*****************************************<br />
<br />
<br />
<br />
<br />