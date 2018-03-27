&nbsp;//获取当前运行模式<br />
&nbsp; &nbsp; echo php_sapi_name(); &nbsp;<br />
&nbsp; // 只允许在cli下面运行 &nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; if (php_sapi_name() != "cli"){ &nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; die("only run in command line mode\n"); &nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; } &nbsp;<br />
<div>
	<br />
</div>