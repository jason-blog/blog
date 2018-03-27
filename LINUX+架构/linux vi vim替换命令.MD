<p style="margin:10px auto;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:14px;white-space:normal;background-color:#FFFFFF;">
<pre class="prettyprint lang-js linenums">1.         :s/vivian/sky/ 替换当前行第一个 vivian 为 sky
            :s/vivian/sky/g 替换当前行所有 vivian 为 sky

2.         :n,$s/vivian/sky/ 替换第 n 行开始到最后一行中每一行的第一个 vivian 为 sky
            :n,$s/vivian/sky/g 替换第 n 行开始到最后一行中每一行所有 vivian 为 sky
                     (n 为数字，若 n 为 .，表示从当前行开始到最后一行)


3.         :%s/vivian/sky/（等同于 :g/vivian/s//sky/） 替换每一行的第一个 vivian 为 sky
            :%s/vivian/sky/g（等同于 :g/vivian/s//sky/g） 替换每一行中所有 vivian 为 sky

4.         可以使用 # 作为分隔符，此时中间出现的 / 不会作为分隔符
            :s#vivian/#sky/# 替换当前行第一个 vivian/ 为 sky/

5.         删除文本中的^M
            问题描述：对于换行,window下用回车换行(0A0D)来表示，linux下是回车(0A)来表示。这样，将window上的文件拷到unix上用时，总会有个^M.请写个用在unix下的过滤windows文件的换行符(0D)的shell或c程序。
· 使用命令：cat filename1 | tr -d “^V^M” &gt; newfile； 
· 使用命令：sed -e “s/^V^M//” filename &gt; outputfilename。需要注意的是在1、2两种方法中，^V和^M指的是Ctrl+V和Ctrl+M。你必须要手工进行输入，而不是粘贴。 
· 在vi中处理：首先使用vi打开文件，然后按ESC键，接着输入命令：%s/^V^M//。 
· :%s/^M$//g 
             如果上述方法无用，则正确的解决办法是：
· tr -d   "\r"        &lt; src   &gt;dest 
· tr -d   "\015" &lt;src    &gt;dest 
· strings              A&gt;B</pre>
</p>