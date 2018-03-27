<p style="padding:0px;margin-top:0px;margin-bottom:0px;clear:both;height:auto;overflow:hidden;color:#A7A7A7;font-family:宋体, &quot;font-size:14px;white-space:normal;background-color:#1C1C1C;">
<pre class="prettyprint lang-js linenums">example1：
#!/bin/sh   
b=''  
for ((i=0;$i&lt;=100;i+=2))   
do   
        printf "progress:[%-50s]%d%%\r" $b $i   
        sleep 0.1   
        b=#$b   
done   
echo  
效果：




example 2：
 
#!/bin/bash   
i=0  
while [ $i -lt 20 ]   
do   
       ((i++))   
       echo -ne "=&gt;\033[s"   
       echo -ne "\033[40;50H"$((i*5*100/100))%"\033[u\033[1D"   
   usleep 50000   
done   
echo  
 效果：

example 3：
 
#!/bin/bash   
COUNTER=0  
_R=0  
_C=`tput cols`   
_PROCEC=`tput cols`   
tput cup $_C $_R   
printf "["   
while [ $COUNTER -lt 100 ]   
do   
    COUNTER=`expr $COUNTER + 1`   
    sleep 0.1   
    printf "=&gt;"   
    _R=`expr $_R + 1`   
    _C=`expr $_C + 1`   
    tput cup $_PROCEC 101   
    printf "]%d%%" $COUNTER   
    tput cup $_C $_R   
done   
printf "\n"  
 效果：

 example 4：
 
#!/bin/bash   
i=0  
while [ $i -lt 50 ]   
do   
       ((i++))   
        for j in '-' '\\' '|' '/'   
        do   
       echo -ne "$j\033[s"   
       echo -ne "\033[40;50H"$((i*5*100/100))%"\033[u\033[1D"   
   usleep 50000   
done   
done   
echo  
效果：

 </pre>
</p>