Linux学习篇-SVN命令详解 &nbsp;此博文包含图片	(2011-12-23 17:02:11)转载▼<br />
标签： 杂谈	分类： Linux<br />
在开发中，除了在本机文件夹上进行svn更新外，在命令行中进行svn操作也非常关键，下面列举下网站摘抄的一些文档：<br />
1、将文件checkout到本地目录<br />
svn checkout path（path是服务器上的目录）<br />
例如：svn checkout svn://192.168.1.1/pro/domain<br />
简写：svn co<br />
<br />
2、往版本库中添加新的文件<br />
svn add file<br />
例如：svn add test.php(添加test.php)<br />
svn add *.php(添加当前目录下所有的php文件)<br />
<br />
3、将改动的文件提交到版本库<br />
svn commit -m “LogMessage“ [-N] [--no-unlock] PATH(如果选择了保持锁，就使用–no-unlock开关)<br />
例如：svn commit -m “add test file for my test“ test.php<br />
简写：svn ci<br />
<br />
4、加锁/解锁<br />
svn lock -m “LockMessage“ [--force] PATH<br />
例如：svn lock -m “lock test file“ test.php<br />
svn unlock PATH<br />
<br />
5、更新到某个版本<br />
svn update -r m path<br />
例如：<br />
svn update如果后面没有目录，默认将当前目录以及子目录下的所有文件都更新到最新版本。<br />
svn update -r 200 test.php(将版本库中的文件test.php还原到版本200)<br />
svn update test.php(更新，于版本库同步。如果在提交的时候提示过期的话，是因为冲突，需要先update，修改文件，然后清除svn resolved，最后再提交commit)<br />
简写：svn up<br />
<br />
6、查看文件或者目录状态<br />
svn status path...（目录下的文件和子目录的状态，正常状态不显示）<br />
【?：不在svn的控制中；M：内容被修改；C：发生冲突；A：预定加入到版本库；K：被锁定】<br />
2）svn status -v path(显示文件和子目录状态)<br />
第一列保持相同，第二列显示工作版本号，第三和第四列显示最后一次修改的版本号和修改人。<br />
注：svn status、svn diff和 svn revert这三条命令在没有网络的情况下也可以执行的，原因是svn在本地的.svn中保留了本地版本的原始拷贝。<br />
简写：svn st<br />
<br />
7、删除文件<br />
svn delete path -m “delete test fle“<br />
例如：svn delete svn://192.168.1.1/pro/domain/test.php -m “delete test file”<br />
或者直接svn delete test.php 然后再svn ci -m ‘delete test file‘，推荐使用这种<br />
简写：svn (del, remove, rm)<br />
<br />
8、移动文件或者目录或文件更名<br />
svn move -m “move test fle“<br />
例如：svn move -m “move test file” a.php &nbsp;b.php 把当前目录下的a.php改名为b.php<br />
svn move -m “move test file” address admin/address 把当前目录下得address目录移动到当前目录下的admin/address下<br />
或者直接svn delete test.php 然后再svn ci -m ‘delete test file‘，推荐使用这种<br />
简写：svn (del, remove, rm)<br />
<br />
<br />
9、查看日志<br />
svn log path<br />
例如：svn log test.php 显示这个文件的所有修改记录，及其版本号的变化<br />
<br />
10、查看文件详细信息<br />
svn info path<br />
例如：svn info test.php<br />
<br />
11、比较差异<br />
svn diff path(将修改的文件与基础版本比较)<br />
例如：svn diff test.php<br />
svn diff -r m:n path(对版本m和版本n比较差异)<br />
例如：svn diff -r 200:201 test.php<br />
简写：svn di<br />
<br />
<br />
12、将两个版本之间的差异合并到当前文件<br />
svn merge -r m:n path<br />
例如：svn merge -r 200:205 test.php（将版本200与205之间的差异合并到当前文件，但是一般都会产生冲突，需要处理一下）<br />
<br />
13、SVN 帮助<br />
svn help<br />
svn help ci<br />
<br />
<br />
——————————————————————————<br />
以上是常用命令，下面写几个不经常用的<br />
——————————————————————————<br />
14、版本库下的文件和目录列表<br />
svn list path<br />
显示path目录下的所有属于版本库的文件和目录<br />
简写：svn ls<br />
15、创建纳入版本控制下的新目录<br />
svn mkdir: 创建纳入版本控制下的新目录。<br />
用法: 1、mkdir PATH…<br />
2、mkdir URL…<br />
创建版本控制的目录。<br />
1、每一个以工作副本 PATH 指定的目录，都会创建在本地端，并且加入新增<br />
调度，以待下一次的提交。<br />
2、每个以URL指定的目录，都会透过立即提交于仓库中创建。<br />
在这两个情况下，所有的中间目录都必须事先存在。<br />
16、恢复本地修改<br />
svn revert: 恢复原始未改变的工作副本文件 (恢复大部份的本地修改)。revert:<br />
用法: revert PATH…<br />
注意: 本子命令不会存取网络，并且会解除冲突的状况。但是它不会恢复<br />
被删除的目录<br />
17、代码库URL变更<br />
svn switch (sw): 更新工作副本至不同的URL。<br />
用法: 1、switch URL [PATH]<br />
2、switch –relocate FROM TO [PATH...]<br />
1、更新你的工作副本，映射到一个新的URL，其行为跟“svn update”很像，也会将<br />
服务器上文件与本地文件合并。这是将工作副本对应到同一仓库中某个分支或者标记的<br />
方法。<br />
2、改写工作副本的URL元数据，以反映单纯的URL上的改变。当仓库的根URL变动<br />
(比如方案名或是主机名称变动)，但是工作副本仍旧对映到同一仓库的同一目录时使用<br />
这个命令更新工作副本与仓库的对应关系。<br />
18、解决冲突<br />
svn resolved: 移除工作副本的目录或文件的“冲突”状态。<br />
用法: resolved PATH…<br />
注意: 本子命令不会依语法来解决冲突或是移除冲突标记；它只是移除冲突的<br />
相关文件，然后让 PATH 可以再次提交。<br />
19、输出指定文件或URL的内容。<br />
svn cat 目标[@版本]…如果指定了版本，将从指定的版本开始查找。<br />
svn cat -r PREV filename &gt; filename (PREV 是上一版本,也可以写具体版本号,这样输出结果是可以提交的)<br />