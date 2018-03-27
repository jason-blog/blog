<pre class="prettyprint lang-js linenums">       long start = System.currentTimeMillis();  


        endGate.await();  


        long end = System.currentTimeMillis();  
        System.out.println("TIME:" + (end - start));</pre>