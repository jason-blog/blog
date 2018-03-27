<br />
<br />
<br />
&nbsp;拉取实例<br />
rsync -avzP -e 'ssh -p 22' &nbsp;root@192.168.35.2:/root/data1 /root<br />
<br />
<br />
rsync -av nohupRun.sh root@58.96.182.163:/tasks /home/jason/<br />
<br />
&nbsp;<br />
&nbsp;<br />
推送实例<br />
rsync -avzP -e 'ssh -p 22' &nbsp;root@192.168.35.2:/root/data1 /root<br />
<br />
<br />
rsync -av nohupRun.sh &nbsp;/home/jason/ root@58.96.182.163:/tasks&nbsp;<br />
<br />
<br />
<br />
<br />
<br />
<br />
<p>
	<span style="color:#555555;font-family:&quot;font-size:13px;white-space:normal;background-color:#F6F5F4;">-progress 在传输时显示传输过程</span>
</p>
<p>
</p>
rsync 命令常用参数<br />
-a 递归方式传输文件，并保持文件属性，等价-rlptgoD不包含-H<br />
-r 子目录以递归模式处理<br />
-l 保持符号链接文件<br />
-H 保持硬链接文件<br />
-p 保持文件权限<br />
-t 保持文件时间信息<br />
-g 保持文件归属组信息<br />
-o 保持文件归属用户信息<br />
-D 保持设备文件和特殊文件<br />
-z 在传输文件时进行压缩处理<br />
--exclude=PATTERN 指定排除一个不需要传输文件匹配模式<br />
--exclude-from=FILE 从FILE中读取排除规则<br />
--include=PATTERN 指定需要传输的文件匹配模式<br />
--include-from=FILE 从FILE中读取匹配规则<br />
--copy-unsafe-links 复制指向复制源路径目录以外的链接文件<br />
--safe-links 忽略指向复制源路径目录以外的链接文件（默认）<br />
--existing 仅更新那些已经存在于接收端的文件，而不复制新创建文件<br />
--ignore-existing 忽略那些已经存在于接收端的文件，只复制新创建文件<br />
-b 当有变化时，对目标目录中的旧文件进行备份<br />
--backup-dir=DIR 与-b结合使用，指定备份路径<br />
--link-dest=DIR 当文件未改变时在指定路径创建硬链接文件<br />
--delete 删除接收端还存在而保存端不存在的文件<br />
--delete-before 接收端在传输之前进行删除操作（默认）<br />
--delete-during 接收端在传输过程中进行删除操作<br />
--delete-after 接收端在传输之后进行删除操作<br />
--delete-excluded 接收端在传输同时进行删除操作<br />
--e,--rsh=COMMAND 指定代替rsh的shell程序<br />
--ignore-erros 即使出现I/O错误也要进行删除<br />
--partial 保留因故没有完全传输的文件，以加快随后的再次传输<br />
--progress 在传输时显示传输过程<br />
-p 等价于—partial—progress<br />
--delay-updates 将正在更新的文件先保存到.~tmp~临时目录，待传输完毕再更新目标文件<br />
-v,--verbose 详细输出模式<br />
-q,--quiet 精简输出模式<br />
-h,--human-readable 输出文件大小<br />
-n,--dry-run 显示那些文件将要被传输<br />
--list-only 仅列出文件而不进行复制<br />
--rsync-path=PROGRAM 指定远程服务器上的rsync命令所在路径<br />
--password-file=FILE 指定从FILE中读取口令，避免在终端中输入口令<br />
-4,-6 使用IPv4或者IPv6<br />
--version 打印版本信息<br />
--help 显示帮组信息<br />