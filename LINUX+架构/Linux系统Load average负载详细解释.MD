<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	我们知道判断一个系统的负载可以使用top，uptime等命令去查看，它分别记录了一分钟、五分钟、以及十五分钟的系统平均负载
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	例如我的某台服务器：
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	$ uptime
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	09:50:21 up 200 days, 15:07, 1 user, load average: 0.27, 0.33, 0.37
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	大部分的人都认为这个数字越小越好，其实有很多关联的提示信息，今天看到这个好文，应该可以给大家说清楚很多问题，转一下：
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	原文链接：&nbsp;<a href="http://blog.scoutapp.com/articles/2009/07/31/understanding-load-averages" style="color:#004276;">http://blog.scoutapp.com/articles/2009/07/31/understanding-load-averages</a>
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	你可能对于 Linux 的负载均值（load averages）已有了充分的了解。负载均值在 uptime 或者 top 命令中可以看到，它们可能会显示成这个样子：
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	load average: 0.09, 0.05, 0.01
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	很多人会这样理解负载均值：三个数分别代表不同时间段的系统平均负载（一分钟、五 分钟、以及十五分钟），它们的数字当然是越小越好。数字越高，说明服务器的负载越 大，这也可能是服务器出现某种问题的信号。
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	而事实不完全如此，是什么因素构成了负载均值的大小，以及如何区分它们目前的状况是 “好”还是“糟糕”？什么时候应该注意哪些不正常的数值？
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	回答这些问题之前，首先需要了解下这些数值背后的些知识。我们先用最简单的例子说明， 一台只配备一块单核处理器的服务器。
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	行车过桥
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	一只单核的处理器可以形象得比喻成一条单车道。设想下，你现在需要收取这条道路的过桥 费 — 忙于处理那些将要过桥的车辆。你首先当然需要了解些信息，例如车辆的载重、以及 还有多少车辆正在等待过桥。如果前面没有车辆在等待，那么你可以告诉后面的司机通过。 如果车辆众多，那么需要告知他们可能需要稍等一会。
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	因此，需要些特定的代号表示目前的车流情况，例如：
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	0.00 表示目前桥面上没有任何的车流。 实际上这种情况与 0.00 和 1.00 之间是相同的，总而言之很通畅，过往的车辆可以丝毫不用等待的通过。
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	1.00 表示刚好是在这座桥的承受范围内。 这种情况不算糟糕，只是车流会有些堵，不过这种情况可能会造成交通越来越慢。
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	超过 1.00，那么说明这座桥已经超出负荷，交通严重的拥堵。 那么情况有多糟糕？ 例如 2.00 的情况说明车流已经超出了桥所能承受的一倍，那么将有多余过桥一倍的车辆正在焦急的等待。3.00 的话情况就更不妙了，说明这座桥基本上已经快承受不了，还有超出桥负载两倍多的车辆正在等待。
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	上面的情况和处理器的负载情况非常相似。一辆汽车的过桥时间就好比是处理器处理某线程 的实际时间。Unix 系统定义的进程运行时长为所有处理器内核的处理时间加上线程 在队列中等待的时间。
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	和收过桥费的管理员一样，你当然希望你的汽车（操作）不会被焦急的等待。所以，理想状态 下，都希望负载平均值小于 1.00 。当然不排除部分峰值会超过 1.00，但长此以往保持这 个状态，就说明会有问题，这时候你应该会很焦急。
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	“所以你说的理想负荷为 1.00 ？”
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	嗯，这种情况其实并不完全正确。负荷 1.00 说明系统已经没有剩余的资源了。在实际情况中 ，有经验的系统管理员都会将这条线划在 0.70：
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	“需要进行调查法则”： 如果长期你的系统负载在 0.70 上下，那么你需要在事情变得更糟糕之前，花些时间了解其原因。
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	“现在就要修复法则”：1.00 。 如果你的服务器系统负载长期徘徊于 1.00，那么就应该马上解决这个问题。否则，你将半夜接到你上司的电话，这可不是件令人愉快的事情。
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	“凌晨三点半锻炼身体法则”：5.00。 如果你的服务器负载超过了 5.00 这个数字，那么你将失去你的睡眠，还得在会议中说明这情况发生的原因，总之千万不要让它发生。
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	那么多个处理器呢？我的均值是 3.00，但是系统运行正常！
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	哇喔，你有四个处理器的主机？那么它的负载均值在 3.00 是很正常的。
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	在多处理器系统中，负载均值是基于内核的数量决定的。以 100% 负载计算，1.00 表示单个处理器，而 2.00 则说明有两个双处理器，那么 4.00 就说明主机具有四个处理器。
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	回到我们上面有关车辆过桥的比喻。1.00 我说过是“一条单车道的道路”。那么在单车道 1.00 情况中，说明这桥梁已经被车塞满了。而在双处理器系统中，这意味着多出了一倍的 负载，也就是说还有 50% 的剩余系统资源 — 因为还有另外条车道可以通行。
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	所以，单处理器已经在负载的情况下，双处理器的负载满额的情况是 2.00，它还有一倍的资源可以利用。
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	[NextPage]
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	多核与多处理器
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	先脱离下主题，我们来讨论下多核心处理器与多处理器的区别。从性能的角度上理解，一台主 机拥有多核心的处理器与另台拥有同样数目的处理性能基本上可以认为是相差无几。当然实际 情况会复杂得多，不同数量的缓存、处理器的频率等因素都可能造成性能的差异。
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	但即便这些因素造成的实际性能稍有不同，其实系统还是以处理器的核心数量计算负载均值 。这使我们有了两个新的法则：
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	“有多少核心即为有多少负荷”法则： 在多核处理中，你的系统均值不应该高于处理器核心的总数量。
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	“核心的核心”法则： 核心分布在分别几个单个物理处理中并不重要，其实两颗四核的处理器 等于 四个双核处理器 等于 八个单处理器。所以，它应该有八个处理器内核。
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	审视我们自己
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	让我们再来看看 uptime 的输出
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	~ $ uptime
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	23:05 up 14 days, 6:08, 7 users, load averages: 0.65 0.42 0.36
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	这是个双核处理器，从结果也说明有很多的空闲资源。实际情况是即便它的峰值会到 1.7，我也从来没有考虑过它的负载问题。
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	那么，怎么会有三个数字的确让人困扰。我们知道，0.65、0.42、0.36 分别说明上一分钟、最后五分钟以及最后十五分钟的系统负载均值。那么这又带来了一个问题：
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	我们以哪个数字为准？一分钟？五分钟？还是十五分钟？
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	其实对于这些数字我们已经谈论了很多，我认为你应该着眼于五分钟或者十五分钟的平均数 值。坦白讲，如果前一分钟的负载情况是 1.00，那么仍可以说明认定服务器情况还是正常的。 但是如果十五分钟的数值仍然保持在 1.00，那么就值得注意了（根据我的经验，这时候你应 该增加的处理器数量了）。
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	那么我如何得知我的系统装备了多少核心的处理器？
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	在 Linux 下，可以使用
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	cat /proc/cpuinfo
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	获取你系统上的每个处理器的信息。如果你只想得到数字，那么就使用下面的命令：
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	grep 'model name' /proc/cpuinfo | wc -l
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	Popularity: 11% [?]
</p>
<p style="margin-top:10px;margin-bottom:10px;padding:0px;color:#333333;background-color:#F8F8F8;text-indent:28px;font-family:宋体;font-size:14px;white-space:normal;">
	【编辑推荐】
</p>