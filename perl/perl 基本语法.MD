<p>
	一．数据类型(Data type)：
</p>
<p>
	<br />
</p>
<p>
	Perl 的数据类型大致分为四种：Scalar（变量）、Scalar Array（数组）、Hash Array（散列）、References（指针），看起来虽少但用起来却绰绰有余。尤其在写Perl程序时可以不必事先宣告变量，这一点对刚学程序语言的人甚为方便，不过为了以后程序除错和维护方便，我建议你还是养成事先声明变量的习惯比较好。
</p>
<p>
	1 Scalar（纯量变量）：
</p>
<p>
	<br />
</p>
<p>
	纯量变量是Perl里最基本的一种数据型态，它可以代表一个字符、字符串、整数、甚至浮点数，而Perl把它们都看成是一样的东东! 你甚至可以混着用，不可思议吧。例如：
</p>
<p>
	# 井字号开头的后面都是批注。
</p>
<p>
	# 纯量变数以$开头。
</p>
<p>
	# my 是一种宣告变量的方式，它可以使变量区域化。
</p>
<p>
	# 宣告变量时若不加 my 或 local 则Perl会把它当作全域变量使用。
</p>
<p>
	# 习惯上，我们会将字符串用双引号括起来，而数值就不用加引号。
</p>
<p>
	my $x="abc";
</p>
<p>
	my $x=123;
</p>
<p>
	my $x=4.56;
</p>
<p>
	1-1 常用的操作运算符
</p>
<p>
	1)、算术运算符
</p>
<p>
	+(加)、-(减)、*(乘)、/(除)、**(幂)、%(余)、-(负)
</p>
<p>
	（1）求幂（**） 结果不能超出数的范围。当指数为小数时，底数不能为负数，例如：25**1.5=125，(-25)**1.5=?（不成立）
</p>
<p>
	（2）取余（%） 操作数为整数，否则要截取。第二个数不能为0（因为除数不能为0）
</p>
<p>
	（3）负（-） -$a=$a*(-1)
</p>
<p>
	此外，注意当一个字符串参加运算，需要转化为整数时，如果不能转化为整数则值为0。例如：'2'+1=3，'a'+1=1
</p>
<p>
	2)、数字比较运算符
</p>
<p>
	&lt;（小于）、=（等于）、&gt;（大于）、==（等于）、&lt;=（小于等于）、&gt;=（大于等于）、!=（不等于）、&lt;=&gt;（比较）
</p>
<p>
	（1）==：比较运算，比较的结果为真或非零，假或零
</p>
<p>
	（2）&lt;=&gt;：比较运算 例如：$a&lt;=&gt;$b，当$a&gt;$b时，值为1；当$a&lt;$b时，值为-1；当$a==$b时，值为0
</p>
<p>
	（3）自动把操作数转化为整数,不能转化为整数则为0
</p>
<p>
	（4）浮点数不精确，不要把值相近的数比较，否则得到的结果是出乎意料的
</p>
<p>
	3)、字符串比较运算符
</p>
<p>
	lt（小于）、gt（大于）、eq（等于）、le（小于等于）、ge（大于等于）、ne（等于）、cmp（比较）
</p>
<p>
	（1）字符串的比较原则：按照字母表的顺序比较，数字&lt;大写字母&lt;小写字母（a小—z大）
</p>
<p>
	（2）字符串比较的次序：字符串从左到右比较。'azz'&lt;‘bc'（即：首先a与b进行比较，然后z与c进行比较）
</p>
<p>
	（3）当一个串是另一个的前缀时，长度长的为大。例如：dog&lt;doghouse
</p>
<p>
	（4）字符串可以从右向左进位，且是字母数字分别进行
</p>
<p>
	（5）自动把操作数转化为字符串。123 lt 45 =&gt; '123' lt '45'
</p>
<p>
	（6）cmp等同于&lt;=&gt;，结果为-1,0, 1
</p>
<p>
	例如：$str1=”a”，$str2=”a“，则print ($str1 cmp $str2) ==&gt; 0
</p>
<p>
	例如：$str1=”a”，$str2=”b”，则print($str1 cmp $str2)===&gt; -1
</p>
<p>
	例如：$str1=”b”，$str2=”a”，则print($str1 cmp $str2)===&gt; 1
</p>
<p>
	（7）空串，0，Undef，这三种情况都为假
</p>
<p>
	例如：如下比较的结果
</p>
<p>
	35 != 30+5 &nbsp; &nbsp; #假
</p>
<p>
	35 == 35.0 &nbsp; &nbsp; #真
</p>
<p>
	'35' eq '35.0' &nbsp; #假（当成字符串来比较）
</p>
<p>
	'fred' &nbsp;lt &nbsp;'barney' &nbsp;#假
</p>
<p>
	'fred' &nbsp;lt &nbsp;'free' &nbsp; &nbsp; &nbsp;#假
</p>
<p>
	'fred' &nbsp;eq "fred" &nbsp; &nbsp;#真
</p>
<p>
	'fred' &nbsp;eq &nbsp;"Fred" &nbsp;#假
</p>
<p>
	' &nbsp; ' &nbsp;gt &nbsp;' ' &nbsp;#真
</p>
<p>
	4)、字符串连接（.）、字符/字符串重复（x）
</p>
<p>
	（1）连接（ “.“），例如：$a=‘a'.'b'; &nbsp;=&gt;‘ab'
</p>
<p>
	在print时可以直接写print $a$b=&gt;print $a.$b; 但是这两者的原理是不一样的
</p>
<p>
	（2）重复（ “x” ），注意：前后有空格（目的：为了和变量名分开），例如：‘a' &nbsp;x &nbsp;5=‘aaaaa'，若重复次数&lt;1，则返回空串
</p>
<p>
	例如："5" x 4，即为："5555"
</p>
<p>
	例如："love" x (4+1)，即为："lovelovelovelovelove"
</p>
<p>
	例如："4.8" x 4，即为："4.84.84.84.8"
</p>
<p>
	例如：6.1 x 3，即为："6.16.16.1"
</p>
<p>
	即：左边是一个字符串，右边是该字符串出现的次数
</p>
<p>
	5)、逻辑运算符（&amp;&amp;(and)（与）、||(or)（或）、!(not)（非）、xor（异或）
</p>
<p>
	（1）先算左边的值，后算右边的值
</p>
<p>
	（2）&amp;&amp;和and的优先级不同，但除非特殊情况，很难有区别
</p>
<p>
	6)、位操作运算符
</p>
<p>
	&amp;（按位与）、 |（按位或）、 ~（按位非）、 ^（按位异或）、 &lt;&lt;（左移）、&gt;&gt;（右移）
</p>
<p>
	（1）操作数为二进制整数，如果是小数则截取为整数
</p>
<p>
	（2）&lt;&lt;左移，移开后空位补0，值为原数值的2*N倍（例如：z&lt;&lt;4，则z=z*（2的4次方））
</p>
<p>
	（3）&gt;&gt;右移，首位补0，值为原值一半（并取整）（例如：z&gt;&gt;4，则z=z/（2的的次方））
</p>
<p>
	7)、赋值运算符
</p>
<p>
	=、+=、-=、*=、/=、%=、**=、&amp;=、|=、^=、.=
</p>
<p>
	（1）$a+=1=&gt;$a=$a+1
</p>
<p>
	（2）可以连等$a=$b=3;=&gt;$a=3;$b=3;
</p>
<p>
	（3）混用 ($a=$b)+=3;=&gt;$a=$b;$a=$a+3;（不建议使用）
</p>
<p>
	8)、自增（++）、自减（--）
</p>
<p>
	（1）不要在变量两边都使用此种操作符：++$var--
</p>
<p>
	（2）不要在变量自增/减后在同一表达式中再次使用：$var2 = $var1 + ++$var1;
</p>
<p>
	（3）可用于字符串的自增，当z、Z、9时进位。$a=‘caz'; $a++; ==&gt; $a=‘cba';
</p>
<p>
	（4）不能用于字符串的自减，当$a--时，按数字运算，字符先转化为0再自减
</p>
<p>
	（5）如果字符串含有非字母数字符号，或数字位于字母中时，自增也先化为0再自增
</p>
<p>
	例如：$a=‘ab*c'; $a++; &nbsp;==&gt; $a=1;
</p>
<p>
	例如：$a=‘ab5c'; $a++; &nbsp;==&gt; $a=1；
</p>
<p>
	（6）预增$b=++$a，$a先自增再赋值，后增$b=$a++；$a先赋值再自增；反之，同理
</p>
<p>
	例如：$a=1; $b=++$a; =&gt;$a=2,$b=2;
</p>
<p>
	例如：$a=1; $b=$a++; =&gt;$a=2,$b=1;
</p>
<p>
	（7）只能用于单一变量，不能对运算后的变量进行。例如：($a+$b)++
</p>
<p>
	9)、逗号（相当于：将两条语句写在一行）
</p>
<p>
	适用范围： 只有当两个语句关联紧密时才使用
</p>
<p>
	例如：$a+=1，$b=$a; &nbsp;=&gt; $a+=1; $b=$a;
</p>
<p>
	例如：$a="ab5c", print $a."\n";
</p>
<p>
	10、条件运算符
</p>
<p>
	条件？ 真：假
</p>
<p>
	（1）三个操作数：先对条件表达式运算，为真时执行：的左边的运算，为假时执行：的右边的运算
</p>
<p>
	例如：$result = $var == 0 ? 14 : 7；
</p>
<p>
	（2）用于简单的条件
</p>
<p>
	（3）条件表达式用在＝的左边
</p>
<p>
	例如：$condvar == 43 ? $var1 : $var2 = 14;
</p>
<p>
	例如：$condvar == 43 ? $var1 = 14 : $var2 = 14;
</p>
<p>
	三、操作符优先级别（ precedence--优先级）
</p>
<p>
	当一个表达式中出现几种不同的运算符，哪个先计算，哪个后计算
</p>
<p>
	例如：$condvar == 43 ? $var1 : $var2 = 14;（先算条件，后算赋值）
</p>
<p>
	例如：$x = $a == $b;（先算关系，后算赋值）
</p>
<p>
	例如：$x == 0 || $y / $x &gt; 5;（先算除，接着算大于、接着算等于，最后算关系或）
</p>
<p>
	例如：$result = 11 * 2 + 6 ** 2 &lt;&lt; 2;（先算幂，再算乘，接着算加，再接着算左移，最后算赋值）
</p>
<p>
	（1）一般的优先级如下：自增自减最高，单操作数高于多操作数，数字运算 &gt; 比较运算（数字比较与字符串比较） &gt; 位运算 &gt; 赋值运算 &gt; 逻辑运算
</p>
<p>
	（2）数字运算：幂 &gt; */&gt;+-
</p>
<p>
	（3）比较运算： &lt;（小于）、&gt;（大于）高于（== 与!=）
</p>
<p>
	2 Scalar Array：
</p>
<p>
	Perl数组变量和列表的概念，列表是包含在括号里的一序列的值，可以为任何数值，也可为空，并且列表存贮于Perl数组变量中，与简单变量不同，Perl数组变量以字符"@"打头。
</p>
<p>
	Perl数组变量和列表
</p>
<p>
	一、列表
</p>
<p>
	列表是包含在括号里的一序列的值，可以为任何数值，也可为空，如：
</p>
<p>
	(1,5.3,"hello",2)，空列表：()。
</p>
<p>
	注：只含有一个数值的列表(如：(43.2))与该数值本身(即：43.2)是不同的，但它们可
</p>
<p>
	以互相转化或赋值。
</p>
<p>
	列表例：
</p>
<p>
	(17,$var,"astring")
</p>
<p>
	(17,26&lt;&lt;2)
</p>
<p>
	(17,$var1+$var2)
</p>
<p>
	($value,"Theansweris$value")
</p>
<p>
	二、Perl数组--列表的存贮
</p>
<p>
	列表存贮于Perl数组变量中，与简单变量不同，Perl数组变量以字符"@"打头，如：
</p>
<p>
	@array=(1,2,3);
</p>
<p>
	注：
</p>
<p>
	(1)Perl数组变量创建时初始值为空列表：()。
</p>
<p>
	(2)因为PERL用@和$来区分Perl数组变量和简单变量，所以同一个名字可以同时用于Perl
</p>
<p>
	数组变量和简单变量，如：
</p>
<p>
	$var=1;
</p>
<p>
	@var=(11,27.1,"astring");
</p>
<p>
	但这样很容易混淆，故不推荐。
</p>
<p>
	1、Perl数组的存取
</p>
<p>
	◆对Perl数组中的值通过下标存取，第一个元素下标为0。试图访问不存在的Perl数组元
</p>
<p>
	素，则结果为NULL，但如果给超出Perl数组大小的元素赋值，则Perl数组自动增长，原
</p>
<p>
	来没有的元素值为NULL。如：
</p>
<p>
	@array=(1,2,3,4);
</p>
<p>
	$scalar=$array[0];
</p>
<p>
	$array[3]=5;#now@arrayis(1,2,3,5)
</p>
<p>
	$scalar=$array[4];#now$scalar=null;
</p>
<p>
	$array[6]=17;#now@arrayis(1,2,3,5,"","",17)
</p>
<p>
	◆Perl数组间拷贝
</p>
<p>
	@result=@original;
</p>
<p>
	◆用Perl数组给列表赋值
</p>
<p>
	@list1=(2,3,4);
</p>
<p>
	@list2=(1,@list1,5);#@list2=(1,2,3,4,5)
</p>
<p>
	◆Perl数组对简单变量的赋值
</p>
<p>
	(1)@array=(5,7,11);
</p>
<p>
	($var1,$var2)=@array;#$var1=5,$var2=7,11被忽略
</p>
<p>
	(2)@array=(5,7);
</p>
<p>
	($var1,$var2,$var3)=@array;#$var1=5,$var2=7,$var3=""(null)
</p>
<p>
	◆从标准输入(STDIN)给变量赋值
</p>
<p>
	$var=&lt;STDIN&gt;;
</p>
<p>
	@array=&lt;STDIN&gt;;#^D为结束输入的符号
</p>
<p>
	2、字符串中的方括号和变量替换
</p>
<p>
	"$var[0]"为Perl数组@var的第一个元素。
</p>
<p>
	"$var\[0]"将字符"["转义，等价于"$var"."[0]"，$var被变量替换，[0]保持不变。
</p>
<p>
	"${var}[0]"亦等价于"$var"."[0]"。
</p>
<p>
	"$\{var}"则取消了大括号的变量替换功能，包含文字：${var}.
</p>
<p>
	3、列表范围：
</p>
<p>
	(1..10)=(1,2,3,4,5,6,7,8,9,10)
</p>
<p>
	(2,5..7,11)=(2,5,6,7,11)
</p>
<p>
	(3..3)=(3)
</p>
<p>
	◆用于实数
</p>
<p>
	(2.1..5.3)=(2.1,3.1,4.1,5.1)
</p>
<p>
	(4.5..1.6)=()
</p>
<p>
	◆用于字符串
</p>
<p>
	("aaa".."aad")=("aaa","aab","aac","aad")
</p>
<p>
	@day_of_month=("01".."31")
</p>
<p>
	◆可包含变量或表达式
</p>
<p>
	($var1..$var2+5)
</p>
<p>
	◆小技巧：
</p>
<p>
	$fred="Fred";
</p>
<p>
	print(("Hello,".$fred."!\n")x2);
</p>
<p>
	其结果为：
</p>
<p>
	Hello,Fred!
</p>
<p>
	Hello,Fred!
</p>
<p>
	4、Perl数组的输出：
</p>
<p>
	(1)@array=(1,2,3);
</p>
<p>
	print(@array,"\n");
</p>
<p>
	结果为：
</p>
<p>
	123
</p>
<p>
	(2)@array=(1,2,3);
</p>
<p>
	print("@array\n");
</p>
<p>
	结果为：
</p>
<p>
	123
</p>
<p>
	5、列表/Perl数组的长度
</p>
<p>
	当Perl数组变量出现在预期简单变量出现的地方，则PERL解释器取其长度。
</p>
<p>
	@array=(1,2,3);
</p>
<p>
	$scalar=@array;#$scalar=3,即@array的长度
</p>
<p>
	($scalar)=@array;#$scalar=1,即@array第一个元素的值
</p>
<p>
	注：以Perl数组的长度为循环次数可如下编程：
</p>
<p>
	$count=1;
</p>
<p>
	while($count&lt;=@array){
</p>
<p>
	print("element$count:$array[$count-1]\n");
</p>
<p>
	$count++;
</p>
<p>
	}
</p>
<p>
	6、子Perl数组
</p>
<p>
	@array=(1,2,3,4,5);
</p>
<p>
	@subarray=@array[0,1];#@subarray=(1,2)
</p>
<p>
	@subarray2=@array[1..3];#@subarray2=(2,3,4)
</p>
<p>
	@array[0,1]=("string",46);#@array=("string",46,3,4,5)now
</p>
<p>
	@array[0..3]=(11,22,33,44);#@array=(11,22,33,44,5)now
</p>
<p>
	@array[1,2,3]=@array[3,2,4];#@array=(11,44,33,5,5)now
</p>
<p>
	@array[0..2]=@array[3,4];#@array=(5,5,"",5,5)now
</p>
<p>
	可以用子Perl数组形式来交换元素：
</p>
<p>
	@array[1,2]=@array[2,1];
</p>
<p>
	7、有关Perl数组的库函数
</p>
<p>
	(1)sort--按字符顺序排序
</p>
<p>
	@array=("this","is","a","test");
</p>
<p>
	@array2=sort(@array);#@array2=("a","is","test","this")
</p>
<p>
	@array=(70,100,8);
</p>
<p>
	@array=sort(@array);#@array=(100,70,8)now
</p>
<p>
	(2)reverse--反转Perl数组
</p>
<p>
	@array2=reverse(@array);
</p>
<p>
	@array2=reversesort(@array);
</p>
<p>
	(3)chop--Perl数组去尾
</p>
<p>
	chop的意义是去掉STDIN（键盘）输入字符串时最后一个字符--换行符。而如果它作用到Perl数组上，则将Perl数组中每一个元素都做如此处理。
</p>
<p>
	@list=("rabbit","12345","quartz");
</p>
<p>
	chop(@list);#@list=("rabbi","1234","quart")now
</p>
<p>
	(4)join/split--连接/拆分
</p>
<p>
	join的第一个参数是连接所用的中间字符，其余则为待连接的字符Perl数组。
</p>
<p>
	$string=join("","this","is","a","string");#结果为"thisisastring"
</p>
<p>
	@list=("words","and");
</p>
<p>
	$string=join("::",@list,"colons");#结果为"words::and::colons"
</p>
<p>
	@array=split(/::/,$string);#@array=("words","and","colons")now
</p>
<p>
	3 Hash Array(Associative Array)：
</p>
<p>
	perl hash 常见用法
</p>
<p>
	基本用法
</p>
<p>
	# 初始化 %h为空数组%h = {};# 用数组初始化%h为 a=&gt;1, b=&gt;2%h = ('a', 1, 'b', 2);# 意义同上，只是另一种更形象化的写法。%h = ('a'=&gt;1, 'b'=&gt;2);#如果key是字符串，可以省略引号。下面这行和上面那行是一样的%h = (a=&gt;1, b=&gt;2);# 用{}来访问print "$h{a}\n"; # 打印1$h{b} = '2b';print "$h{b}\n"; # 打印2b# 删除key用deletedelete $h{b}; # 从$h删除'b'
</p>
<p>
	清空hash
</p>
<p>
	undef %h
</p>
<p>
	得到hash的所有键值
</p>
<p>
	# 得到所有keys，顺序取决于hash函数，或者说是乱序
</p>
<p>
	@all_keys = keys %h;
</p>
<p>
	# 所有键值，是按hash的值从大往小排列的。值的比较是数字比较(比如说，10&gt;9)
</p>
<p>
	@all_keys = sort{$h{$b}&lt;=&gt;$h{$a}} (keys %h);
</p>
<p>
	# 所有键值，是按hash的值从小往大排列的。值的比较是数字比较
</p>
<p>
	@all_keys = sort{$h{$a}&lt;=&gt;$h{$b}} (keys %h);
</p>
<p>
	# 所有键值，是按hash的值从小往大排列的。值的比较是字符串比较（比如说，'10' &lt; '9'）
</p>
<p>
	@all_keys = sort{$h{$a} cmp $h{$b}} (keys %h);
</p>
<p>
	判断hash是否包含key
</p>
<p>
	exists($h{$key});
</p>
<p>
	Hash的长度
</p>
<p>
	想要知道一个hash存放多少数据
</p>
<p>
	$hash_size = keys %h
</p>
<p>
	# 把%h的长度放到$hash_size中
</p>
<p>
	print scalar kes %h, "\n"
</p>
<p>
	# 打印%h的长度。这里用了scalar来返回数组长度。
</p>
<p>
	遍历一个hash
</p>
<p>
	while (my ($k, $v) = each %h) {print "$k ---&gt; $v\n";}
</p>
<p>
	Reference引用
</p>
<p>
	Reference类似于C/C++的指针
</p>
<p>
	$h_ref = \%h;
</p>
<p>
	# 获得一个hash的reference%aHash = %{$h_ref};
</p>
<p>
	# 把hash reference当成hash用$value = $h_ref-&gt;{akey}
</p>
<p>
	# 这个和%h{akey}是一样的
</p>
<p>
	传递hash到函数
</p>
<p>
	一般都是传递一个reference到函数
</p>
<p>
	%h = ();$h{a}=1;foo(\%h)print $h{b}, "\n";
</p>
<p>
	# 打印出2。
</p>
<p>
	这个值来自于函数foo() sub foo {my ($h) = @_;print $h-&gt;{a}, "\n";
</p>
<p>
	# 打印出1$h-&gt;{b} = 2;}
</p>
<p>
	函数返回hash，或者hash引用(hash reference)
</p>
<p>
	函数可以返回hash
</p>
<p>
	sub foo {my %fh;$fh{a} = 1;return %h;} my %h = foo();print
</p>
<p>
	二 控制结构(Control Statements)
</p>
<p>
	1 选择 if结构
</p>
<p>
	Perl的条件控制叙述和C语言很像，让使用者很快就能掌握它。不过Perl比C语言又另外多了些实用的语法，我用底线标出来，大家一看便知。
</p>
<p>
	# Expression 就是条件叙述式，Perl和C一样没有定义布尔数据型态(Boolean datatype)，
</p>
<p>
	# 因此 0 是false、非0 是ture。另外要注意字符串运算子和数值运算子要分清楚哦。
</p>
<p>
	# Code Segment 就是用大括号括起来的一堆指令，也就是一个Block。
</p>
<p>
	if (Expression) {Code Segment}
</p>
<p>
	if (Expression) {Code Segment} else {Code Segment}
</p>
<p>
	if (Expression) {Code Segment} elsif (Expression) {Code Segment} else {CodeSegment}
</p>
<p>
	# elsif 就是 else if
</p>
<p>
	# 如果指令(statement)只有一项，我们可以使用倒装句法，看起来比较简洁。
</p>
<p>
	statement if (Expression);
</p>
<p>
	# unless 就是if not
</p>
<p>
	statement unless (Expression);例：
</p>
<p>
	print "HELLO!\n" if ($name eq "friend");
</p>
<p>
	$x-=10 if ($x == 100);
</p>
<p>
	看吧! C 语言有的Perl大部分都有，学过 C 的人可以毫不费力的学会Perl。
</p>
<p>
	2循环结构
</p>
<p>
	Perl的循环控制叙述也和C语言很像，当然，照例Perl也另外多了些实用的语法：
</p>
<p>
	# 注意：纯量变数前面要加个 $ 字号，这一点和C语言不一样哦。
</p>
<p>
	for($i=0; $i&lt;=10; $i++) {Code Segment}
</p>
<p>
	# foreach 是承袭UNIX的shell script来的，
</p>
<p>
	# 第一个自变量是纯量变数，第二个自变量要用括号括起来，里面是一个纯量数组，
</p>
<p>
	# 顾名思义它就是把数组中的每个元素依序传给第一个自变量，直到全部传完。
</p>
<p>
	# 它和 for($i=0; $i&lt;=$#array; $i++) 用法虽然不同，但目的都是要取出数组的每个元素。
</p>
<p>
	foreach $i (@array) {Code Segment}
</p>
<p>
	# 其实在Perl中，for和foreach是可以混着用的，就看个的人习惯了。
</p>
<p>
	# 下面这行就等于上面第一个叙述，不过简洁多了，大家可以试着用用看。
</p>
<p>
	for $i (0..10) {Code Segment}
</p>
<p>
	# while控制循环和后置循环。
</p>
<p>
	while($i&lt;=10) {Code Segment}
</p>
<p>
	do {Code Segment} while(Expression);
</p>
<p>
	# Perl也有和C语言的break和continue一样的指令，Perl叫它做 last 和 next (较口语化)。
</p>
<p>
	# last是跳出现在所在的循环，next则是跳过下面的指令直接执行下一次的循环。
</p>
<p>
	while(chomp($i=)) {
</p>
<p>
	next if ($i == 5);
</p>
<p>
	last unless ($i &gt; 10);
</p>
<p>
	}
</p>
<p>
	Perl 还有提供label(标记)的语法，也就是goto 指令，不过有经验的programer并不喜欢用它，我也不建议大家使用，所以就此按下不讲。有兴趣的人请自行查阅。还有一点值得注意的是Perl没有提供像C语言一样的 switch 叙述，不过Perl的pattern match的功能非常强，所以我建议你直接用 if else 叙述来做就好了。
</p>
<p>
	3子程序(Subroutines)
</p>
<p>
	(a) Syntax: sub NAME {Code}
</p>
<p>
	(b) 呼叫子程序： &amp;NAME(para1, para2,...)
</p>
<p>
	(c) 参数传递：@_
</p>
<p>
	Perl 和C一样是采用Call by value的方式，不过因为Perl不用事先宣告变量，所以建立子程序的时候也不用宣告要传递什么参数。当主程序在传递参数给子程序时，Perl会把括号括起来的参数按顺序放在一个特殊的全域变量 @_ 数组中，然后子程序就可以随意使用数组 @_ 里的参数，例如 $_[0] 是第一个参数， $_[1] 是第二个，或是用 my($a1,$a2,$a3,...) = @_;来取出各个参数，当然 my @arg=@_; 或 my %arg=@_; 也是可以的。由于Perl的语法非常活泼，使得程序在维护时特别棘手，因此写批注成为一项很重要的工作。我建议你最好在每个子程序前面加上对这段子程序的描述，特别是需要传递的参数要注明清楚。
</p>
<p>
	(d) Variable Localization：my or local
</p>
<p>
	通常我们在程序中定义的变量都是全域变量，所以在子程序中若要把变量区域化则要加上 my 或 local 关键词，例如：my $x=3;，若子程序所用的变量名不小心和主程相同，Perl会以目前正在执行的子程序里的变量为优先。
</p>
<p>
	4 I/O和档案处理
</p>
<p>
	(a) Syntax:
</p>
<p>
	open(FILEHANDLE,"Expression");
</p>
<p>
	close(FILEHANDLE);
</p>
<p>
	这里的Expression是一个叙述加上文件名称，若Expression只有文件名称没有加上叙述，则预设是只读。Expressions叙述如下：
</p>
<p>
	Expression &nbsp; &nbsp;Effect
</p>
<p>
	open(FH, " filename")
</p>
<p>
	open(FH, "+filename")
</p>
<p>
	open(FH, "&gt;filename") &nbsp; &nbsp; &nbsp;Opens filename for writing.
</p>
<p>
	open(FH, "+&gt;filename") &nbsp; &nbsp;Opens filename for both reading and writing.
</p>
<p>
	open(FH, "&gt;&gt;filename") &nbsp; &nbsp;Appends to filename.
</p>
<p>
	open(FH, "command|") &nbsp; &nbsp; Runs the command and pipes its output to thefilehandle.
</p>
<p>
	open(FH, "command|") &nbsp; &nbsp; Pipes the output along the filehandle to thecommand.
</p>
<p>
	open(FH, "-") &nbsp; &nbsp; Opens STDIN.
</p>
<p>
	open(FH, "&gt;-") &nbsp; &nbsp; Opens STDOUT.
</p>
<p>
	open(FH, "&lt;&amp;=N") Where N is a number, this performs the equivalent of C'sfdopen for reading.
</p>
<p>
	open(FH, "&gt;&amp;=N") &nbsp;Where N is a number, this performs the equivalent of C'sfdopen for writing.
</p>
<p>
	例：
</p>
<p>
	# 开启$filename这个档案，若开启失败则印出die后面的讯息，并结束程序。
</p>
<p>
	open(FILE, $filename) || die "Can't open file $filename : $!\n";
</p>
<p>
	# 下面是一个十分精简的写法，和 while($_=){print "$_";} 是等效的。
</p>
<p>
	print while();
</p>
<p>
	# 档案开启后要记得随手关闭，这才是写程序的好习惯。
</p>
<p>
	close(FILE);
</p>
<p>
	# $!和$_都是Perl的特殊变数，下面会介绍的。
</p>
<p>
	(b) Input：
</p>
<p>
	Perl没有特别用来输入的函数，因为Perl在执行程序时，会自动开启标准输入装置，其filehandle定为STDIN，所以在Perl中要输入数据的方法就是使用：
</p>
<p>
	# Perl不会自动去掉结尾的CR/LF，跟C语言不同，所以要用chomp函数帮你去掉它。
</p>
<p>
	# 大家常常会忘记这个动作，导致结果跟你想的不一样，要特别注意一下。
</p>
<p>
	$input=&lt;STDIN&gt;; chomp $input;
</p>
<p>
	# 下面是较简洁的写法。
</p>
<p>
	chomp($input=&lt;STDIN&gt;);
</p>
<p>
	(c) Output：print "variables or 字符串";
</p>
<p>
	Perl也有printf()函数，语法和C语言一模一样，我就不多做介绍了。Perl另外有个print函数，比printf()更方便、更好用，包你爱不释手。Output不外乎是输出到屏幕或档案，用例子来说明比较容易了解。
</p>
<p>
	# 不用再指定变量的data type，这样不是比printf()方便多了吗?
</p>
<p>
	print "Scalar value is $x\n";
</p>
<p>
	# . 是字符串加法的运算子，上下这两行是等效的。
</p>
<p>
	print "Scalar value is " . $x . "\n";
</p>
<p>
	# 输出到档案的方法。
</p>
<p>
	print FILE "print $x to a file.";
</p>
<p>
	# 下面是print的特殊用法，学自shell script的用法：
</p>
<p>
	print&lt;XXX
</p>
<p>
	这招叫做 here document，XXX可以是你取的任何标识符，在标识符之间的字都会按照你所写的样子输出，就像\标签一样。而当一行的开头是XXX你取的这个标识符时，才会停止输出。
</p>
<p>
	XXX
</p>
<p>
	Perl 也有和 C 一样以 "\" 开头的特殊字符：
</p>
<p>
	\t &nbsp; &nbsp;tab
</p>
<p>
	\n &nbsp; &nbsp;newline
</p>
<p>
	\r &nbsp; &nbsp;return
</p>
<p>
	\f &nbsp; &nbsp;form feed
</p>
<p>
	\b &nbsp; &nbsp;backspace
</p>
<p>
	\a &nbsp; &nbsp;alarm(bell)
</p>
<p>
	\e &nbsp; &nbsp;escape
</p>
<p>
	\033 &nbsp;octalchar
</p>
<p>
	\x1b &nbsp;hex char
</p>
<p>
	\c[ &nbsp; control char
</p>
<p>
	\l &nbsp; &nbsp;lowercase next char
</p>
<p>
	\u &nbsp; &nbsp;uppercase next char
</p>
<p>
	\L &nbsp; &nbsp;lowercase till \E
</p>
<p>
	\U &nbsp; &nbsp;uppercase till \E
</p>
<p>
	\E &nbsp; &nbsp;end case modification
</p>
<p>
	\Q &nbsp; &nbsp;quoteregexp metacharacters till \E
</p>
<p>
	另外需要说明的是 Perl 融合了unix shell script的使用惯例，以双引号("")括起来的字符串会先经过展开，但反斜线(\)后面的字符则不展开，当作一般字符看待。而以单引号('')括起来的字符串完全不会展开，以反单引号(``)括起来的字符串会把它当作命令列指令一样执行，等于system()一样。初学者常常会搞混，但习惯之后就会觉得不这样分清楚反而不行哩，举个例吧：
</p>
<p>
	$x="ls -l";
</p>
<p>
	print "$x"; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; # Output ls -l
</p>
<p>
	print "\$x"; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;# Output $x
</p>
<p>
	print '$x'; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; # Output $x
</p>
<p>
	print `$x`; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; # Output files in this directory
</p>
<p>
	函数
</p>
<p>
	1. Perl函数
</p>
<p>
	通过 &amp; 调用.
</p>
<p>
	2. Perl参数
</p>
<p>
	Perl天然支持可变数目个参数。
</p>
<p>
	在函数内部，所有参数按顺序放在数组 @_ 中，在函数内部，$_[0] 表示函数的第一个
</p>
<p>
	参数，其余类推。
</p>
<p>
	3. shift
</p>
<p>
	shift 后跟一个数组，表示将数组的第一个值返回。数组也被改变，其第一个元素被弹
</p>
<p>
	出。
</p>
<p>
	演示代码一(求最大值):
</p>
<p>
	#!/usr/bin/perl -w
</p>
<p>
	use strict;
</p>
<p>
	# 调用函数max，取得一组数值的最大值,并输出。
</p>
<p>
	my $maxCnt = &amp;max(11,22,33);
</p>
<p>
	print "maxCnt=$maxCnt\n";
</p>
<p>
	sub max {
</p>
<p>
	# 采用遍历算法。先将参数中的第一个值赋给$currentMaxCnt。
</p>
<p>
	# @_ 是默认的包含本函数所有参数 [如(11,22,33)]的数组。
</p>
<p>
	# shift @_ 有两个结果: 1. 将数组 @_ 中的第一个值做为返回值(赋给了
</p>
<p>
	$currentMaxCnt). 2. 将@_数组第一个值弹出[此后@_的值变为(22,33)].
</p>
<p>
	my $currentMaxCnt = shift @_;
</p>
<p>
	# 函数中使用shift时，@_可以省略。上面代码也可以写成这样。
</p>
<p>
	# &nbsp;my $currentMaxCnt = shift;
</p>
<p>
	# 遍历整个@_数组。
</p>
<p>
	foreach ( @_ ) {
</p>
<p>
	# $_ 表示数组@_中当前被遍历到的元素.
</p>
<p>
	if ( $_ &gt; $currentMaxCnt ) {
</p>
<p>
	# 如果发现当前数组元素比$currentMaxCnt大，那就将$currentMaxCnt重新赋值为当前
</p>
<p>
	元素。
</p>
<p>
	$currentMaxCnt = $_;
</p>
<p>
	}
</p>
<p>
	}
</p>
<p>
	# 函数返回值为标量$currentMaxCnt.
</p>
<p>
	return $currentMaxCnt;
</p>
<p>
	}
</p>
<p>
	演示代码二(求和):
</p>
<p>
	#!/usr/bin/perl -w
</p>
<p>
	use strict;
</p>
<p>
	# 求一组数的和并打印。
</p>
<p>
	my $s1 = &amp;sumvar(11,22,33);
</p>
<p>
	my $s2 = &amp;sumarg(22,33,44);
</p>
<p>
	my $s3 = &amp;sumgod(11,22,33,44,55);
</p>
<p>
	print "s1=$s1, s2=$s2, s3=$s3\n";
</p>
<p>
	# 办法1
</p>
<p>
	sub sumvar {
</p>
<p>
	# 将参数数组的前三个元素值相应地赋给($first, $second, $third)
</p>
<p>
	(my $first, my $second, my $third) = @_;
</p>
<p>
	# 返回其和值。缺点: 如果是求四个参数的和，依然只能给出前三个的和。
</p>
<p>
	return $first + $second + $third;
</p>
<p>
	}
</p>
<p>
	# 办法2
</p>
<p>
	sub sumarg {
</p>
<p>
	# $_[0] 表示参数数组@_的第一个元素。其余类推。
</p>
<p>
	my $first = $_[0];
</p>
<p>
	my $second = $_[1];
</p>
<p>
	my $third = $_[2];
</p>
<p>
	# 返回其和值。缺点: 同sumvar. 只是通过这里学习 $_[0] 这种用法。
</p>
<p>
	return $first + $second + $third;
</p>
<p>
	}
</p>
<p>
	# 办法3, 参数可以任意多。都能求其和。
</p>
<p>
	sub sumgod{
</p>
<p>
	my $s = shift @_;
</p>
<p>
	foreach ( @_ ) {
</p>
<p>
	$s = $s + $_;
</p>
<p>
	}
</p>
<p>
	# 同前面函数max。
</p>
<p>
	return $s;
</p>
<p>
	}
</p>
<p>
	8总结
</p>
<p>
	整理了一下自己觉得用的比较多的一些符号、用法、函数、库之类的，这些都是很基本
</p>
<p>
	的，但是“背熟”了，对提高效率会很有帮助。
</p>
<p>
	数据操作
</p>
<p>
	* $ - 声明与引用用一个scalar的变量
</p>
<p>
	* @ - 声明与引用一个list，但是当访问一个list的成员时，需使用$ListName[index]
</p>
<p>
	* % - 声明与引用一个hash表，但是当访问一个hash的成员时，需要使用$HashName
</p>
<p>
	{key}
</p>
<p>
	特殊变量
</p>
<p>
	* $0 - 当前运行脚本的文件名
</p>
<p>
	* @ARGV - 当前运行脚本的命令行参数列表
</p>
<p>
	* $_ - 默认变量，如循环中的当前变量
</p>
<p>
	* @_ - 函数的输入参数列表
</p>
<p>
	* %ENV - 系统的环境变量
</p>
<p>
	* @INC - Perl的Include路径列表，我们可以往该列表中添加我们自己的目录来方便引
</p>
<p>
	用自定义的库
</p>
<p>
	* $! - 当前系统提示，错误信息
</p>
<p>
	* $^O - 操作系统的名字
</p>
<p>
	* STDIN,STDOUT,STDERR - 输入输出的默认句柄，可以作一定的自定义
</p>
<p>
	* =&gt; - 声明一个hash时可以用来明确的表示出key=&gt;value的对应关系
</p>
<p>
	* $^I- 指定备份的文件的后缀名，如此，被修改的文件将会自动以该后缀名保存一个副
</p>
<p>
	本
</p>
<p>
	特殊用法
</p>
<p>
	* &amp;Sub - 调用一个函数，虽然Perl有些规则让你在某些时候可以省略这里的&amp;符号，但
</p>
<p>
	是处于一致性考虑，所以自定义的函数的调用，我一律采用此种方式。
</p>
<p>
	* $# - 用来取得模个数组的最大index, 一般情况下，也可以用-1来表示最后一个元素
</p>
<p>
	的index的
</p>
<p>
	* qw() - 快速声明一个字符串数组，可以省略那些烦人的引号
</p>
<p>
	正则表达式
</p>
<p>
	* $ - 获取被括号捕获的匹配
</p>
<p>
	* $`, $&amp;, $' - 获取匹配的字符串，以及其前后两个部分
</p>
<p>
	* ^,$ - 字符串的始末位置，用作定位
</p>
<p>
	常用函数
</p>
<p>
	* pop, push, shift, unshift, reverse - list的操作函数
</p>
<p>
	* keys，values, exists, each, delete - hash的操作函数
</p>
<p>
	* chomp, split, join, index, substr, sort - 字符串操作函数
</p>
<p>
	* sprintf,printf, print - 格式化输出函数
</p>
<p>
	* system, exec, `` - 系统命令调用函数
</p>
<p>
	* glob, unlink, mkdir, rmdir, rename,chmod,chown, open, close, opendir,
</p>
<p>
	closedir - 文件系统操作函数
</p>
<p>
	* stat, lstat,localtime,gmtime,utime - 文档属性，时间相关函数
</p>
<p>
	* hex, oct - 二进制，八进制，十六进制数转化成十进制的函数
</p>
<p>
	* grep, map - list高级操作函数
</p>
<p>
	这些函数的详细介绍，都可以通过命令：
</p>
<p>
	#perldoc -f functionname
</p>
<p>
	查到
</p>
<p>
	常用库
</p>
<p>
	* File::Basename - 根据path获取文件名或者文件路径
</p>
<p>
	* File::Spec - 根据文件名与路径组合成全路经
</p>
<p>
	* File::Find - 递归遍历某个目录下所有文件
</p>
<p>
	* XML::Simple - 以一个复杂的结构来表示xml文件，使用起来相当方便
</p>
<p>
	* Time::HiRes - 经常用来计算一个操作所耗费的时间
</p>
<p>
	* Getopt::Long - 当脚本需要复杂的输入参数与选项时用到
</p>
<p>
	* Cwd - 拿到当前工作目录
</p>
<p>
	* IO::File - 文件操作
</p>
<p>
	* Win32 - 当需要调用一些Windows API时我会用它
</p>