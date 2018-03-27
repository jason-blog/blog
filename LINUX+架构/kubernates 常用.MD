gcloud compute --project "test-projeck" ssh --zone "asia-east1-a" "test-conputer"<br />
<br />
gcloud beta sql connect "test-sql"<br />
<br />
gcloud compute ssh --zone "asia-east1-a" "release<br />
<br />
<p>
	gcloud beta sql connect "test-sql" --user root
</p>
<br />
<br />
gcloud compute instances<br />
<br />
gcloud compute instances list<br />
<br />
gcloud container images list<br />
<br />
gcloud compute ssh INSTANCE_NAME \<br />
&nbsp; &nbsp; --project PROJECT<br />
&nbsp; &nbsp; --zone ZONE<br />
<span style="white-space:pre;"> </span><br />
gcloud container clusters get-credentials cluster-cc<br />
<span style="white-space:pre;"> </span><br />
<span style="white-space:pre;"> </span><br />
kubectl create -f&nbsp;cc-core-registry.yaml<br />
<br />
https://cloud.google.com/container-optimized-os/docs/how-to/create-configure-instance<br />
<br />
<br />
https://cloud.google.com/kubernetes-engine/docs/quickstart<br />
<br />
<br />
https://cloud.google.com/kubernetes-engine/docs/tutorials/hello-app<br />
<br />
kubectl run hello-web --image=gcr.io/${PROJECT_ID}/hello-app:v1 --port 8080<br />
<br />
kubectl run rcs --image=gcr.io/test-project/test/release<br />
kubectl run&nbsp;cc-rcs --image=gcr.io/test-projeckt/rcs/release --replicas=3 --namespace=cc-core-develop&nbsp; --port=8083<br />
kubectl get pods<br />
kubectl get po --namespace=cc-infrastructure<br />
kubectl get pod&nbsp;cc-rcs-674c9bdc94-5j4tc -o wide --namespace=cc-core-develop<br />
kubectl get node<br />
<br />
kubectl create namespace&nbsp;cc-core-develop&nbsp;<br />
<br />
kubectl apply -f C:\Users\buzhidao\Desktop\service.yaml<br />
<br />
kubectl get nodes<br />
<br />
//查看状态<br />
kubectl describe pod&nbsp;cc-core-product-20171220-3-6fcdb6d7-5942x --namespace=cc-core-product<br />
<br />
kubectl describe rs/cc-core-product-20171220-3-6fcdb6d7 --namespace=cc-core-product<br />
<br />
kubectl delete namespace limit-example<br />
<br />
kubectl delete pods &lt;pod&gt; --grace-period=0 --force<br />
<br />
//LimitRange<br />
kubectl create -f https://k8s.io/docs/tasks/administer-cluster/cpu-constraints-pod.yaml --namespace=constraints-cpu-example<br />
<br />
kubectl get pod constraints-cpu-demo --output=yaml --namespace=constraints-cpu-example<br />
<br />
kubectl delete pod&nbsp;cc-core-registry-v1.1-8b6d9976c-2kkw6 --namespace&nbsp;cc-core-develop<br />
<br />
kubectl 常用命令<br />
http://blog.csdn.net/xingwangc2014/article/details/51204224<br />
<br />
https://www.kubernetes.org.cn/resource-quotas<br />
<br />
http://blog.csdn.net/u011957758/article/details/53750419<br />
<br />
kubernetes node节点调度<br />
http://blog.csdn.net/tiger435/article/details/73650147<br />
<br />
挂载数据卷<br />
https://www.cnblogs.com/zhenyuyaodidiao/p/6594541.html<br />
<br />
<br />
cloud provider 导流量<br />
<br />
//service类型<br />
https://www.jianshu.com/p/bbb673e79c3e<br />