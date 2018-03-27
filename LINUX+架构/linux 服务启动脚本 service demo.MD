<pre class="prettyprint lang-js linenums">
<pre class="prettyprint lang-js linenums">#!/bin/sh
# chkconfig: 2345 55 25

proc_name="{%proc_name%}"
service_name="{%service_name%}"

{%cd_dir%}

start(){
proc_id=`ps -ef|grep -i ${proc_name}|grep -v "grep"|awk '{print $2}'`
#nohup java -jar *** &gt; proc_name.log 2&gt;&amp;1 &amp; 
if [ -z $proc_id ];then
{%start_script%}
echo "start complete"
status
else
 echo "${service_name} is running please stop or restart!"
fi
}
status(){
proc_id=`ps -ef|grep -i ${proc_name}|grep -v "grep"|awk '{print $2}'`
if [ -z $proc_id ];then
    echo "${service_name} is not running!"
else
    echo "${service_name} is running!"
fi
}
stop(){
  proc_id=`ps -ef|grep -i ${proc_name}|grep -v "grep"|awk '{print $2}'`
if [ -z $proc_id ];then
  echo "${service_name} is not running please start! "
else  
  kill -9 $proc_id
  echo "stop complete"
  status
fi  
}
keepStart(){
{%start_script%}
echo "start complete"
status
}
case $1 in
   start)
        start
  ;;
    stop)
        stop
  ;;
    status)
        status
  ;;
  keepStart)
        keepStart
  ;;
    restart)
        stop
        start
  ;;
    *)
        echo "Usage:service ${service_name} start|stop|status|restart"
  ;;
esac
</pre>
<br />
</pre>