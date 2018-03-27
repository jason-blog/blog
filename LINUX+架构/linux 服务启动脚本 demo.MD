<p>
<pre class="prettyprint lang-js linenums">
#!/bin/sh
# chkconfig: 2345 55 25
openfire_start(){
/tasks/AGAPI/runAll.sh
}
openfrie_status(){
ps -aux | grep java
}
openfire_stop(){
killall java
}
case $1 in
start)
openfire_start
;;
stop)
 #ps x|grep java |awk '{print $1}'
openfrie_stop
;;
status)
openfrie_status
*)
echo 'Usage:openfire start|stop'
;;
esac
</pre>
</p>