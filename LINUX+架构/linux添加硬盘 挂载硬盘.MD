挂载好新硬盘后输入fdisk -l命令看当前磁盘信息<br />
<br />
可以看到除了当前的第一块硬盘外还有一块sdb的第二块硬盘，然后用fdisk /dev/sdb 进行分区<br />
<br />
进入fdisk命令，输入h可以看到该命令的帮助，按n进行分区<br />
<br />
这里输入e即分为逻辑分区，按p即分为主分区，我们要将这块盘分为主分区即输入p<br />
<br />
到这里输入该主分区为第几个主分区，由于是新盘我们输入1来分第一个主分区<br />
<br />
First Cylinder是选择该分区的起始磁盘数，这里可自定义也可不做选择，默认是1，<br />
如无特殊需求强烈建议选择默认，也就是1来分区（直接按回车）<br />
<br />
接下来是定义该分区的大小，如果按默认（按回车）即是使用全部可用存储额，<br />
也可以是用M或m单位结尾的数字(大写M是大B的意思，如果输入1M实际上是X8也就是8m的空间)，<br />
这里我们先分一个1G的空间，所以输入+1024m<br />
<br />
之后输入w写入分区，等待结束皆可<br />
<br />
再输入fdisk -l 可以看到我们刚才分的一个分区，之后用mkfs -t ext3 -c /dev/sdb1进行格式化，<br />
如有多个分区可把sdb1改成sdb2 sdb3...以此类推，具体可用fdisk -l看到每个分区的名字<br />
<br />
上图蓝色部分是写硬盘卷标的，如不想要卷标可直接按回车，现在分区好了我们用mount&nbsp;<br />
挂载一下该分区即可使用了，这里我把它挂载到mnt目录下，也可以自建一个目录挂载<br />
<br />
<br />
来看一下分区大小是否和预定的一样，使用df -TH命令看一下当前挂载的分区和大小，看到我们刚分的分区了吧<br />
<br />
如果想每次系统重启都能自动挂载该分区可修改/etc/fstab文件，<br />
在最后加一段 /dev/sdb1 &nbsp; &nbsp;/www &nbsp; &nbsp;ext3 &nbsp; &nbsp;defaults 1 2&nbsp;<br />
(格式说明：<br />
&nbsp;/dev/sdb1 代表哪个分区 &nbsp;<br />
&nbsp;ext3 &nbsp; &nbsp; 是该分区的格式&nbsp;<br />
&nbsp;defaults 是挂载时所要设定的参数(只读，读写，启用quota等)，<br />
&nbsp;输入defaults包括的参数有(rw、dev、exec、auto、nouser、async) ，<br />
&nbsp;1是使用dump是否要记录，0是不要。&nbsp;<br />
&nbsp;2是开机时检查的顺序，是boot系统文件就为1，其他文件系统都为2，如不要检查就为0)<br />
<br />