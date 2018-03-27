<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;line-height:1.5;font-size:16px;"> 1.查看本地有没有安装mysql，命令就是mysql，如果有这个命令就表示安装了mysql数据库软件。如果没有就自行安装。</span><br style="margin:0px;padding:0px;" />
<span style="margin:0px;padding:0px;line-height:1.5;font-size:16px;"> MySQL-server-4.0.16-0.i386.rpm　　　&nbsp;</span><br style="margin:0px;padding:0px;" />
<span style="margin:0px;padding:0px;line-height:1.5;font-size:16px;"> MySQL-client-4.0.16-0.i386.rpm</span>
</p>
<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	<br style="margin:0px;padding:0px;" />
<span style="margin:0px;padding:0px;line-height:1.5;font-size:16px;"> 2.查看本地有没有安装mysql的开发包。命令是 `mysql_config --cflags --libs` 如果有安装就会有一串编译选项和连接库。如果没有就自行安装 mysql-devel-*****的rpm包 后面是版本号。mysql开发包提供了基本操作接口。安装后头文件在/usr/include/mysql 而动态库在 /usr/lib/mysql 上。</span>
</p>
<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;line-height:1.5;font-size:16px;"> 3.创建一个用于练习的数据库test.进入mysql&gt; 然后依次输入:</span>
</p>
<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;line-height:1.5;font-size:16px;"> mysql&gt;<span style="margin:0px;padding:0px;line-height:1.5;">create database test;&nbsp;</span></span>
</p>
<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;line-height:1.5;font-size:16px;"> mysql&gt;use test; &nbsp; &nbsp;//切换到test数据库中</span>
</p>
<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;line-height:1.5;font-size:16px;"> mysql&gt; create table test(name varchar(255),num int(10) ); //创建一个叫test的表</span>
</p>
<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;line-height:1.5;font-size:16px;"> mysql&gt;show create table test; &nbsp;//显示刚才创建的表信息</span>
</p>
<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;line-height:1.5;font-size:16px;"> mysql&gt; select * from test;&nbsp;　　//查询test表中数据</span>
</p>
<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	<span style="margin:0px;padding:0px;line-height:1.5;font-size:16px;"> mysql&gt;quit</span>
</p>
<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	<span style="font-family:verdana, &quot;font-size:16px;white-space:normal;background-color:#FFFFFF;"> 4.编写一个c++程序，代码如下:</span>
</p>
<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	<br />
</p>
<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
<pre class="prettyprint lang-js linenums">#include &lt;stdio.h&gt;
#include &lt;mysql.h&gt;

int main(int argc,char *argv[])
{
    MYSQL conn;
    int res;
    mysql_init(&amp;conn);
    if(mysql_real_connect(&amp;conn,"localhost","root","","test",0,NULL,CLIENT_FOUND_ROWS)) //"root":数据库管理员 "":root密码 "test":数据库的名字
    {
    　　printf("connect success!\n");
    　　res=mysql_query(&amp;conn,"insert into test values('user','123456')");
    　　if(res)
    　　{
       　　 printf("error\n");
    　　}
    　　else
    　　{
        　　printf("OK\n");
    　　}
    　　mysql_close(&amp;conn);
    }
    return 0;
}</pre>
</p>
<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	<span style="font-family:verdana, &quot;font-size:16px;white-space:normal;background-color:#FFFFFF;"> 代码不是很难理解，就不解释了。</span>
</p>
<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	<br />
</p>
<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	<br />
</p>
<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
</p>
<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
	<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
		<span style="margin:0px;padding:0px;line-height:1.5;font-size:16px;"> 5.编译程序</span>
	</p>
	<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
		<span style="margin:0px;padding:0px;line-height:1.5;font-size:16px;"> 使用的编译代码（注意哪两个不是单引号而是反单引号）</span>
	</p>
	<div class="cnblogs_code" style="margin:5px 0px;padding:5px;background-color:#F5F5F5;border:1px solid #CCCCCC;overflow:auto;white-space:normal;font-family:&quot;">
<pre style="margin-top:0px;margin-bottom:0px;padding:0px;white-space:pre-wrap;word-wrap:break-word;font-family:&quot;">g++ test.<span style="margin:0px;padding:0px;line-height:1.5;color:#0000FF;">cpp</span> `mysql_config --cflags --libs` -o test</pre>
	</div>
	<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
		<span style="margin:0px;padding:0px;line-height:1.5;font-size:16px;"> </span>
	</p>
	<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
		<span style="margin:0px;padding:0px;line-height:1.5;font-size:16px;"> 6.运行代码</span>
	</p>
	<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
		<span style="margin:0px;padding:0px;line-height:1.5;font-size:16px;"> ./test</span>
	</p>
	<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
		&nbsp;
	</p>
	<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
		<span style="margin:0px;padding:0px;line-height:1.5;font-size:16px;"> 7.再次查看数据库</span>
	</p>
	<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
		<span style="margin:0px;padding:0px;line-height:1.5;font-size:16px;"> mysql&gt;use test;</span>
	</p>
	<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
		<span style="margin:0px;padding:0px;line-height:1.5;font-size:16px;"> mysql&gt;select * from test;</span>
	</p>
	<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
		<span style="margin:0px;padding:0px;line-height:1.5;font-size:16px;"> 这样就可以查看到插入的信息了。</span>
	</p>
	<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
		<br />
	</p>
	<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
		<br />
	</p>
	<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
		<br />
	</p>
	<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
		<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
			<span style="margin:0px;padding:0px;line-height:1.5;font-size:16px;"> 6.运行代码</span>
		</p>
		<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
			<span style="margin:0px;padding:0px;line-height:1.5;font-size:16px;"> ./test</span>
		</p>
		<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
			&nbsp;
		</p>
		<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
			<span style="margin:0px;padding:0px;line-height:1.5;font-size:16px;"> 7.再次查看数据库</span>
		</p>
		<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
			<span style="margin:0px;padding:0px;line-height:1.5;font-size:16px;"> mysql&gt;use test;</span>
		</p>
		<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
			<span style="margin:0px;padding:0px;line-height:1.5;font-size:16px;"> mysql&gt;select * from test;</span>
		</p>
		<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
			<span style="margin:0px;padding:0px;line-height:1.5;font-size:16px;"> 这样就可以查看到插入的信息了。<br style="margin:0px;padding:0px;" />
</span>
		</p>
		<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
			<span style="margin:0px;padding:0px;line-height:1.5;font-size:16px;"><img src="http://images.cnitblog.com/i/485067/201403/222320454744987.jpg" alt="" style="margin:0px;padding:0px;max-width:900px;" /></span>
		</p>
		<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
			&nbsp;
		</p>
		<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
			&nbsp;================我是分割线============================
		</p>
<pre class="prettyprint lang-js linenums">#include &lt;stdio.h&gt;
#include &lt;mysql.h&gt;
#define HOST "localhost"
#define USERNAME "root"
#define PASSWORD ""
#define DATABASE "test"

void insert_sql(char * sql);
void query_sql(char* sql);
int main(int argc,char *argv[])
{
    //insert_sql("insert into test values('user','123456')");
    query_sql("select * from test");
    return 0;
}

void insert_sql(char * sql)
{
    MYSQL conn;
    int res;
    mysql_init(&amp;conn);
    if(mysql_real_connect(&amp;conn,"localhost","root","","test",0,NULL,CLIENT_FOUND_ROWS))
    {
    printf("connect success!\n");
    res=mysql_query(&amp;conn,sql);
    if(res)
    {
        printf("error\n");
    }
    else
    {
        printf("OK\n");
    }
    mysql_close(&amp;conn);
    }

}

void query_sql(char* sql) 
{
    MYSQL my_connection; /*这是一个数据库连接*/
    int res; /*执行sql語句后的返回标志*/
    MYSQL_RES *res_ptr; /*指向查询结果的指针*/
    MYSQL_FIELD *field; /*字段结构指针*/
    MYSQL_ROW result_row; /*按行返回的查询信息*/

    int row, column; /*查询返回的行数和列数*/
    int i, j; /*只是控制循环的两个变量*/

    /*初始化mysql连接my_connection*/
    mysql_init(&amp;my_connection);

    /*这里就是用了mysql.h里的一个函数，用我们之前定义的那些宏建立mysql连接，并
     *     返回一个值，返回不为空证明连接是成功的*/
    if (mysql_real_connect(&amp;my_connection, HOST, USERNAME, PASSWORD, DATABASE, 0, NULL, CLIENT_FOUND_ROWS)) 
    {
    /*连接成功*/
    printf("数据库查询query_sql连接成功！\n");
    /*这句话是设置查询编码为utf8，这样支持中文*/
    mysql_query(&amp;my_connection, "set names utf8");

    /*下面这句话就是用mysql_query函数来执行我们刚刚传入的sql語句，
     *         这会返回一个int值，如果为0，证明語句执行成功*/
    res = mysql_query(&amp;my_connection, sql);

    if (res) 
    { /*现在就代表执行失败了*/
        printf("Error： mysql_query !\n");
        /*不要忘了关闭连接*/
        mysql_close(&amp;my_connection);
    }
    else 
    { 
        /*现在就代表执行成功了*/
        /*将查询的結果给res_ptr*/
        res_ptr = mysql_store_result(&amp;my_connection);

        /*如果结果不为空，就把结果print*/
        if (res_ptr) 
        {
        /*取得結果的行数和*/
        column = mysql_num_fields(res_ptr);
        row = mysql_num_rows(res_ptr) + 1;
        printf("查询到 %lu 行 \n", row);

        /*输出結果的字段名*/
        for (i = 0; field = mysql_fetch_field(res_ptr); i++)
            printf("%s\t", field-&gt;name);
        printf("\n");

        /*按行输出結果*/
        for (i = 1; i &lt; row; i++)
        {
            result_row = mysql_fetch_row(res_ptr);
            for (j = 0; j &lt; column; j++)
            printf("%s\t", result_row[j]);
            printf("\n");  
        }  

        }  

        /*不要忘了关闭连接*/  
        mysql_close(&amp;my_connection);  
    }  
    }  
} 

完整代码</pre>
	</p>
	<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
		<br />
	</p>
	<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
		<br />
	</p>
	<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
		<span style="margin:0px;padding:0px;line-height:1.5;font-size:16px;"> 其实数据库的增加，删除，更新等操作比较简单，都是返回一个值表示成功与否。而查询比较麻烦。返回一个结果集，所以操作起来比较麻烦！&nbsp;</span>
	</p>
	<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
		&nbsp;
	</p>
	<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
		<span style="margin:0px;padding:0px;line-height:1.5;font-size:16px;color:#FF0000;">===============2015年6月29日 更新========================</span>
	</p>
	<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
		<span style="margin:0px;padding:0px;line-height:1.5;font-size:16px;"> 上面的这段代码我在平时练习中经常使用到包括近一年来的那些连接mysql数据库的代码都是以这个为模版的。但是最近在实际项目中用到这个代码，一开始没有发现问题，但是在项目进行测试的时候发现出现内存泄漏的问题，经查询是上面代码存在两处内存泄漏问题。&nbsp;</span>
	</p>
	<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
		<span style="margin:0px;padding:0px;line-height:1.5;font-size:16px;"> 1.mysql结果集问题。由mysql_store_result()、mysql_use_result()、mysql_list_dbs()等为结果集分配的内存。完成对结果集的操作后，必须调用mysql_free_result()释放结果集使用的内存。</span>
	</p>
	<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
		<span style="margin:0px;padding:0px;line-height:1.5;font-size:16px;"> 2.本以为这样就应该没有问题了，但是进行模拟压力测试时，发现每次连接都会产生8~16K的内存(单纯的进行mysql连接)，查了一下资料，是每次调用mysql连接后除了进行mysql_close之外，还要使用mysql_library_end进行释放。(http://www.cnblogs.com/cobbliu/p/3709051.html)</span>
	</p>
	<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
		&nbsp;
	</p>
	<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
		<span style="margin:0px;padding:0px;line-height:1.5;font-size:16px;">参考资料:</span>
	</p>
	<p style="margin:10px auto;padding:0px;line-height:1.5;font-size:13px;font-family:verdana, &quot;white-space:normal;background-color:#FFFFFF;">
		<span style="margin:0px;padding:0px;line-height:1.5;font-size:16px;">http://blog.csdn.net/fykhlp/article/details/5950485#</span>
	</p>
</p>