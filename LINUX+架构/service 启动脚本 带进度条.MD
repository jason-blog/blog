<pre class="prettyprint lang-js linenums">#!/bin/sh
# chkconfig: 2345 55 25

proc_name="{%proc_name%}"
service_name="{%service_name%}"
#nohup java -jar *** &gt; proc_name.log 2&gt;&amp;1 &amp; 
{%cd_dir%}

start(){
proc_id=`ps -ef|grep -i ${proc_name}|grep -v "grep"|awk '{print $2}'`

if [ -z "$proc_id" ];then
echo -e "\033[32m${service_name} starting\033[0m"
{%start_script%}
proword='start progress'
progress
echo -e "\033[32mstart complete\033[0m"
status
else
 echo -e "\033[31m${service_name} is running please stop or restart!\033[0m"
fi
}
status(){
proc_id=`ps -ef|grep -i ${proc_name}|grep -v "grep"|awk '{print $2}'`
if [ -z "$proc_id" ];then
    echo -e "\033[32m${service_name} is not running!\033[0m"
else
    echo -e "\033[32m${service_name} is running!\033[0m"
fi
}
stop(){
proc_id=`ps -ef|grep -i ${proc_name}|grep -v "grep"|awk '{print $2}'`
if [ -z "$proc_id" ];then
  echo -e "\033[31m${service_name} is not running please start!\033[0m"
else  
  echo -e "\033[32ms${service_name} stopping\033[0m"
  kill -9 $proc_id
  proword='stop progress'
  progress
  echo -e "\033[32mstop complete\033[0m"
  status
fi  
}
progress(){
b=''
i=0
while [ $i -le  100 ]
do
printf "${proword}:[%-50s]%d%%\r" $b $i
sleep 0.01
i=`expr 2 + $i`        
b=#$b
done
echo
}


keepStart(){
{%start_script%}

echo -e "\033[32mstart complete\033[0m"
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