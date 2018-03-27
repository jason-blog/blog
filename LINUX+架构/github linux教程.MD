在linux下搭建git环境<br />
1、创建Github账号，https://github.com<br />
2、Linux创建SSH密钥：<br />
[plain] view plain copy<br />
ssh-keygen &nbsp;##一直默认就可以了 &nbsp;<br />
3、将公钥 id_rsa.pub 加入到Github账户信息Account Settings-&gt;SSH Key<br />
4、测试验证是否成功。<br />
[plain] view plain copy<br />
ssh -T git@github.com &nbsp;<br />
Hi someone! You've successfully authenticated, but GitHub does not provide shell access. &nbsp;<br />
<br />
同步github到本地<br />
1、复制项目到本地：<br />
[plain] view plain copy<br />
git clone git://github.com:xxxx/test.git ##以gitreadonly方式克隆到本地，只可以读 &nbsp;<br />
git clone git@github.com:xxx/test.git &nbsp;##以SSH方式克隆到本地，可以读写 &nbsp;<br />
git clone https://github.com/xxx/test.git ##以https方式克隆到本地，可以读写 &nbsp;<br />
git fetch git@github.com:xxx/xxx.git &nbsp;##获取到本地但不合并 &nbsp;<br />
git pull git@github.com:xxx/xxx.git ##获取并合并内容到本地 &nbsp;<br />
<br />
本地提交项目到github<br />
1、本地配置<br />
[plain] view plain copy<br />
git config --global user.name 'onovps' &nbsp;<br />
git config --global user.email 'onovps@onovps.com' #全局联系方式，可选 &nbsp;<br />
2、新建Git项目并提交到Github。<br />
[plain] view plain copy<br />
mkdir testdir &amp; cd testdir &nbsp;<br />
touch README.md &nbsp;<br />
git init #初始化一个本地库 &nbsp;<br />
git add README.md #添加文件到本地仓库 &nbsp;<br />
git rm README.md #本地倒库内删除 &nbsp;<br />
git commit -m "first commit" #提交到本地库并备注，此时变更仍在本地。 &nbsp;<br />
git commit -a &nbsp;##自动更新变化的文件，a可以理解为auto &nbsp;<br />
<p>
	git remote add xxx git@github.com:xxx/xxx.git &nbsp;#增加一个远程服务器的别名。 &nbsp;
</p>
<p>
	git branch -a #查看分支
</p>
git remote rm xxx &nbsp; ##删除远程版本库的别名 &nbsp;<br />
git push -u remotename master #将本地文件提交到Github的remoname版本库中。此时才更新了本地变更到github服务上。 &nbsp;<br />
<br />
分支版本操作<br />
1、创建和合并分支<br />
[plain] view plain copy<br />
git branch #显示当前分支是master &nbsp;<br />
git branch new-feature &nbsp;#创建分支 &nbsp;<br />
git checkout new-feature &nbsp;#切换到新分支 &nbsp;<br />
vi page_cache.inc.php &nbsp;<br />
git add page_cache.inc.php &nbsp;<br />
git commit -a -m "added initial version of page cache" &nbsp;<br />
git push origin new-feature &nbsp;##把分支提交到远程服务器，只是把分支结构和内容提交到远程，并没有发生和主干的合并行为。 &nbsp;<br />
2、如果new-feature分支成熟了，觉得有必要合并进master<br />
[plain] view plain copy<br />
git checkout master &nbsp;#切换到新主干 &nbsp;<br />
git merge new-feature &nbsp;##把分支合并到主干 &nbsp;<br />
git branch #显示当前分支是master &nbsp;<br />
git push &nbsp;#此时主干中也合并了new-feature的代码 &nbsp;<br />