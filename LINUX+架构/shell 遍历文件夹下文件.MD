<pre class="prettyprint lang-js linenums">#!/bin/bash 
 
function show()
{
    cd $1
 
    for i in `ls -a`
    do
        if [ "$i" == "." ] || [ "$i" == ".." ]
        then
            continue;
        fi
 
        if [ -d "$i" ]
        then
            show "$i"
        else
            echo "$i"
        fi
    done
 
    cd ..
}
 
show $1
 
exit 0</pre>