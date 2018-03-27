<pre class="prettyprint lang-js linenums">查看 pod信息 
kubectl get pod memory-demo --namespace=mem-example</pre>
<pre class="prettyprint lang-js linenums">kubectl get pod memory-demo --output=yaml --namespace=mem-example</pre>
<pre class="prettyprint lang-js linenums">
<pre class="prettyprint lang-js linenums">查看pod详情</pre>
<pre class="prettyprint lang-js linenums">kubectl describe pod memory-demo-2 --namespace=mem-example</pre>
</pre>
<pre class="prettyprint lang-js linenums">查看某一pod内存使用情况</pre>
<pre class="prettyprint lang-js linenums">
<pre class="prettyprint lang-js linenums">kubectl proxy</pre>
curl http://localhost:8001/api/v1/proxy/namespaces/kube-system/services/heapster/api/v1/model/namespaces/mem-example/pods/memory-demo/metrics/memory/usage</pre>
<pre class="prettyprint lang-js linenums">查看node信息</pre>
<pre class="prettyprint lang-js linenums">
<pre class="prettyprint lang-js linenums">kubectl describe nodes</pre>
<br />
</pre>