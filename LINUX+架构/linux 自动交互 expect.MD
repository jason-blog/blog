#!/usr/bin/expect -f &nbsp;<br />
&nbsp;set ip 127.0.0.1<br />
&nbsp;set password 1123456 &nbsp;<br />
&nbsp;set timeout 10 &nbsp;<br />
&nbsp;spawn ssh username@$ip &nbsp;<br />
&nbsp;expect { &nbsp;<br />
&nbsp;"*yes/no" { send "yes\r"; exp_continue} &nbsp;<br />
&nbsp;"*password:" { send "$password\r" } &nbsp;<br />
&nbsp;} &nbsp;<br />
&nbsp;interact &nbsp;<br />
<p>
	<br />
</p>