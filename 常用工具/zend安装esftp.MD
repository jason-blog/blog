http://www.genshuixue.com/i-cxy/p/8042656<br />
<br />
先说一下如何安装zend的esftp插件，下载插件esftp-1.1.1.zip，下载地址http://sourceforge.net/projects/esftp/<br />
或者 http://yun.baidu.com/share/link?shareid=3306382839&amp;uk=3307299408<br />
解压将com.antimatterstudios.esftp_1.1.1.jar放到zend安装目录下plugins文件下，<br />
<br />
重启zend，如果工具栏没有esftp的图标<br />
<br />
<br />
在Zend Studio安装目录下，找到configuration\org.eclipse.equinox.simpleconfigurator\bundles.info文件，加入<br />
com.antimatterstudios.esftp,1.1.1,plugins/com.antimatterstudios.esftp_1.1.1.jar,4,false<br />
保存，重启Zend即可<br />