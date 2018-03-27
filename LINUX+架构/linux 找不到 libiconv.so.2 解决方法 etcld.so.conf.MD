在安装一个软件包时，最后输入sudo make install命令后，出现以下错误信息：<br style="white-space:normal;" />
error while loading shared libraries: libiconv.so.2: cannot open shared object file: No such file or directory<br style="white-space:normal;" />
<br style="white-space:normal;" />
但是在/usr/local/lib下却能找到libiconv.so.2，解决方法是将/usr/local/lib路径添加到/etc/ld.so.conf文件中，然后用sudo ldconfig命令加载，再重新输入sudo make install命令就可以了。