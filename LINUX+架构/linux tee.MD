<p>
	tee
</p>
<p>
	功能说明：读取标准输入的数据，并将其内容输出成文件。
</p>
<p>
	语 　 法：tee [-ai][--help][--version][文件…]
</p>
<p>
	补充说明：tee指令会从标准输入设备读取数据，将其内容输出到标准输出设备,同时保存成文件。我们可利用tee把管道导入的数据存成文件，甚至一次保存数份文件。
</p>
<p>
	参 　 数：-a 附加到既有文件的后面，而非覆盖它。如果给予tee指令的文件名称已经存在，预设会覆盖该文件的内容。加上此参数后，数据会新增在该文件内容的最后面，而不会删除原先之内容。
</p>
<p>
	-i 忽略中断信号
</p>
<p>
	--help 在线帮助
</p>
<p>
	--version 显示版本信息
</p>
<p>
	范 　 例：
</p>
<p>
	列出文本文件slayers.story的内容，同时复制3份副本，文件名称分别为ss-copy1、ss-copy2、ss-copy3：
</p>
<p>
	$ cat slayers.story |tee ss-copy1 ss-copy2 ss-copy3
</p>
<p>
	tee [-ai][--help][--version][文件...]
</p>
<p>
	【功能】
</p>
<p>
	tee以标准输入作为输入，标准输出和文件作为输出。
</p>
<p>
	【举例】
</p>
<p>
	tee file &nbsp; &nbsp; //覆盖
</p>
<p>
	tee -a file &nbsp; &nbsp;//追加
</p>
<p>
	tee - &nbsp; &nbsp; &nbsp; &nbsp;//输出到标准输出两次
</p>
<p>
	tee - - &nbsp; &nbsp;//输出到标准输出三次
</p>
<p>
	tee file1 file2 - &nbsp; &nbsp;//输出到标准输出两次,并写到那两个文件中
</p>
<p>
	ls | tee file &nbsp;
</p>
<p>
	另：把标准错误也被tee读取
</p>
<p>
	ls "*" 2&gt;&amp;1 | tee ls.txt
</p>
<p>
	*用tee生成一个文件，包含你敲入的内容：
</p>
<p>
	<br />
</p>
<p>
	复制代码代码如下:
</p>
<p>
	<br />
</p>
<p>
	$tee testfile
</p>
<p>
	这样，会提示要你用标准输入输入内容，然后敲回车会将你输入的内容写入testfile和输出到标准输出，如果用[Ctrl]d结束输入([Ctrl]c也行)。如果原来testfile有内容，将会覆盖。
</p>
<p>
	*把内容追加到文件的末尾行：
</p>
<p>
	<br />
</p>
<p>
	复制代码代码如下:
</p>
<p>
	<br />
</p>
<p>
	$tee -a testfile
</p>
<p>
	结果类似上，不过如果原来testfile有内容则不会覆盖而是追加。
</p>
<p>
	<br />
</p>
<p>
	*生成一个文件，敲入的时候，不接受中断信号：
</p>
<p>
	<br />
</p>
<p>
	复制代码代码如下:
</p>
<p>
	<br />
</p>
<p>
	$tee -i testfile
</p>
<p>
	结果同testfile，不过不会接收中断信号，只能用[Ctrl]d结束，而不能用[Ctrl]c了。
</p>
<p>
	*执行ls列出目录文件同时将输出保存到文件test中：
</p>
<p>
	<br />
</p>
<p>
	复制代码代码如下:
</p>
<p>
	<br />
</p>
<p>
	$ls | tee test
</p>
<p>
	这样，会像平时一样执行ls命令并将当前目录的文件名输出到标准输出。另外由于进行了tee命令，所以会生成一个test文件，这个test文件的内容和标准输出的内容一样。
</p>
<p>
	【描述】
</p>
<p>
	tee指令会从标准输入设备读取数据，将其内容输出到标准输出设备，同时保存成文件。可以用于既想看到标准输出，又想将标准输出保存到文件中的情况。
</p>
<p>
	参数：
</p>
<p>
	-a或--append 　附加到既有文件的后面，而非覆盖它．
</p>
<p>
	-i-i或--ignore-interrupts 　忽略中断信号。
</p>
<p>
	--help 　在线帮助。
</p>
<p>
	--version 　显示版本信息。
</p>
<p>
	常用参数
</p>
<p>
	格式：tee
</p>
<p>
	只输出到标准输出，因为没有指定文件嘛。
</p>
<p>
	格式：tee file
</p>
<p>
	输出到标准输出的同时，保存到文件file中。如果文件不存在，则创建；如果已经存在，则覆盖之。（If a file being written to does not already exist, it is created. If a file being written to already exists, the data it previously
</p>
<p>
	contained is overwritten unless the `-a' option is used.）
</p>
<p>
	格式：tee -a file
</p>
<p>
	输出到标准输出的同时，追加到文件file中。如果文件不存在，则创建；如果已经存在，就在末尾追加内容，而不是覆盖。
</p>
<p>
	格式：tee -
</p>
<p>
	输出到标准输出两次。（A FILE of `-' causes `tee' to send another copy of input to standard output, but this is typically not that useful as the copies are interleaved.）
</p>
<p>
	<br />
</p>
<p>
	格式：tee file1 file2 -
</p>
<p>
	输出到标准输出两次，同时保存到file1和file2中。
</p>