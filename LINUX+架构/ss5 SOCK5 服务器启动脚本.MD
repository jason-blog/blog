#!/bin/sh<br />
#<br />
# chkconfig: 345 20 80<br />
# description: This script takes care of starting \<br />
# &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;and stopping ss5<br />
#<br />
<br />
# Source function library.<br />
&nbsp;. /etc/rc.d/init.d/functions<br />
<br />
# Source networking configuration.<br />
&nbsp;. /etc/sysconfig/network<br />
<br />
# Check that networking is up.<br />
&nbsp;[ ${NETWORKING} = "no" ] &amp;&amp; exit 0<br />
<br />
&nbsp;[ -f /usr/sbin/ss5 ] || exit 0<br />
<br />
# Test custom variables<br />
[ -f /etc/sysconfig/ss5 ] &amp;&amp; . /etc/sysconfig/ss5<br />
<br />
export SS5_CONFIG_FILE=/etc/ss5.conf<br />
export SS5_SOCKS_PORT=9999<br />
export SS5_SOCKS_ADDR=61.218.72.2<br />
<br />
# See how we were called.<br />
case "$1" in<br />
&nbsp; start)<br />
&nbsp; &nbsp; &nbsp; &nbsp; # Start daemon.<br />
&nbsp; &nbsp; &nbsp; &nbsp; echo -n "Starting ss5... "<br />
&nbsp; &nbsp; &nbsp; &nbsp; /usr/sbin/ss5 -t $SS5_OPTS<br />
&nbsp; &nbsp; &nbsp; &nbsp; touch /var/lock/subsys/ss5<br />
echo "done"<br />
&nbsp; &nbsp; &nbsp; &nbsp; ;;<br />
&nbsp; stop)<br />
&nbsp; &nbsp; &nbsp; &nbsp; # Stop daemon.<br />
&nbsp; &nbsp; &nbsp; &nbsp; echo "Shutting down ss5... "<br />
killproc ss5<br />
&nbsp; &nbsp; &nbsp; &nbsp; rm -f /var/lock/subsys/ss5<br />
&nbsp; &nbsp; &nbsp; &nbsp; rm -f /var/run/ss5/ss5.pid<br />
echo "done"<br />
&nbsp; &nbsp; &nbsp; &nbsp; ;;<br />
&nbsp; reload)<br />
&nbsp; &nbsp; &nbsp; &nbsp; # Reload configuration<br />
&nbsp; &nbsp; &nbsp; &nbsp; echo -n "Reloading ss5... "<br />
killproc ss5 -1<br />
;;<br />
&nbsp; restart)<br />
&nbsp; &nbsp; &nbsp; &nbsp; # Restart daemon<br />
&nbsp; &nbsp; &nbsp; &nbsp; echo -n "Restarting ss5... "<br />
$0 stop<br />
$0 start<br />
;;<br />
&nbsp; status)<br />
&nbsp; &nbsp; &nbsp; &nbsp; status ss5<br />
;;<br />
&nbsp; *)<br />
&nbsp; &nbsp; &nbsp; &nbsp; echo "Usage: ss5 {start|stop|status|restart|reload}"<br />
&nbsp; &nbsp; &nbsp; &nbsp; exit 1<br />
;;<br />
esac<br />
<br />
exit 0<br />
<div style="white-space:nowrap;">
	<br />
</div>