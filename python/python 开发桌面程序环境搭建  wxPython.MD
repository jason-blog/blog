<br />
<br />
<br />
http://www.crifan.com/use_pyinstaller_to_package_python_to_single_executable_exe/<br />
http://www.cnblogs.com/chjbbs/archive/2014/01/25/3533187.html<br />
=====================================================================================<br />
<br />
安装文件	下载地址<br />
python-2.6.2.msi	http://www.python.org/download/<br />
wxPython2.8-win32-unicode-2.8.10.1-py26.exe<br />
wxPython2.8-win32-docs-demos-2.8.10.1.exe	http://www.wxpython.org/download.php<br />
<br />
<br />
<br />
wxPython2.8-win32-unicode-2.8.10.1-py26.exe 安装后可以 import wx<br />
wxPython2.8-win32-docs-demos-2.8.10.1.exe 中是所有桌面程序demo<br />
<br />
http://blog.csdn.net/jia611/article/details/50498094<br />
<br />
<br />
<br />
PyInstaller 打包exe<br />
<br />
可以只是生成单独的可执行程序<br />
且支持的版本也多：2.3到2.7都支持。以及x64也支持<br />
也可以自定义图标<br />
所以先去试试PyInstaller。<br />
<br />
3.从主页<br />
<br />
http://www.pyinstaller.org/<br />
<br />
中下载对应的zip包：<br />
<br />
https://github.com/downloads/pyinstaller/pyinstaller/pyinstaller-2.0.zip<br />
<br />
cd pyinstaller-2.0 setup.py install<br />
<br />
结果说需要PyWin32，所以得先去装这个。<br />
<br />
<br />
去到pyinstaller.py所在目录，去运行：<br />
<br />
<br />
<br />
总结<br />
<br />
PyInstaller，的确非常好用啊。感谢作者们。<br />
<br />
简单总结其使用方法：<br />
<br />
生成单一的exe文件：<br />
<br />
pyinstaller.py -F ..\BlogsToWordpress\BlogsToWordpress.py<br />
添加必要的搜索路径：<br />
pyinstaller.py -F -p D:\tmp\tmp_dev_root\python\tutorial_summary\make_exe\BlogsToWordpress\libs;D:\tmp\tmp_dev_root\python\tutorial_summary\make_exe\BlogsToWordpress\libs\crifan;D:\tmp\tmp_dev_root\python\tutorial_summary\make_exe\BlogsToWordpress\libs\crifan\blogModules;D:\tmp\tmp_dev_root\python\tutorial_summary\make_exe\BlogsToWordpress\libs\thirdparty;D:\tmp\tmp_dev_root\python\tutorial_summary\make_exe\BlogsToWordpress\libs\thirdparty\chardet; ..\BlogsToWordpress\BlogsToWordpress.py<br />
添加必要的搜索路径，且带图标：<br />
pyinstaller.py -F -p D:\tmp\tmp_dev_root\python\tutorial_summary\make_exe\BlogsToWordpress\libs;D:\tmp\tmp_dev_root\python\tutorial_summary\make_exe\BlogsToWordpress\libs\crifan;D:\tmp\tmp_dev_root\python\tutorial_summary\make_exe\BlogsToWordpress\libs\crifan\blogModules;D:\tmp\tmp_dev_root\python\tutorial_summary\make_exe\BlogsToWordpress\libs\thirdparty;D:\tmp\tmp_dev_root\python\tutorial_summary\make_exe\BlogsToWordpress\libs\thirdparty\chardet; -i ..\BlogsToWordpress\BlogsToWordpress.ico ..\BlogsToWordpress\BlogsToWordpress.py<br />
&nbsp;<br />
<br />
需要注意的是：<br />
<br />
1.检查生成的<br />
<br />
pyinstaller-2.0\XXX\build\pyi.win32\XXX\warnXXX.txt<br />
<br />
(XXX是你的项目名）<br />
<br />
中，是否缺少了必要的模块。<br />
<br />
如果有缺少的，那么去如上所述，添加必要的搜素路径，使得pyinstaller在运行时，可以找到对应的模块并集成进来。<br />
<br />
2.此处我这里没有UPX，暂时没去折腾。<br />
<br />
<p>
	估计是用UPX去压缩，压缩后所生成的exe文件的大小，会小得多。
</p>
<p>
	<img src="http://images.cnitblog.com/blog/587257/201401/251143076323.png" alt="" width="605" height="611" title="" align="" /> 
</p>
<p>
	<strong>编译命令常用</strong> 
</p>
<p>
	<strong>C:\Python27\python.exe H:\Projects\PyCharm\PyInstaller-2.1\pyinstaller.py --onefile -i C:\Users\Json\Desktop\test\logo.png -w C:\***&nbsp;<br />
<br />
<br />
</strong> 
</p>
<div style="white-space:nowrap;">
	<br />
</div>