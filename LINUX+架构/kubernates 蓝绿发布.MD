<p>
	https://www.ianlewis.org/en/bluegreen-deployments-kubernetes
</p>
<p>
	<br />
</p>
<p>
	<h1 class="title" itemprop="title" style="padding:0px;font-size:45px;line-height:1.35;letter-spacing:-0.02em;margin:-20px 0px 24px;font-family:Roboto, Helvetica, Arial, sans-serif;font-weight:400;color:rgba(0, 0, 0, 0.87);white-space:normal;">
		Blue/Green Deployments on Kubernetes
	</h1>
	<div style="color:rgba(0, 0, 0, 0.87);font-family:Helvetica, Arial, sans-serif;font-size:14px;white-space:normal;">
		<em>Sept. 15, 2017</em>
	</div>
	<div style="color:rgba(0, 0, 0, 0.87);font-family:Helvetica, Arial, sans-serif;font-size:14px;white-space:normal;float:right;">
		<div id="___plusone_0" style="margin:0px;padding:0px;background-image:initial;background-position:initial;background-size:initial;background-repeat:initial;background-attachment:initial;background-origin:initial;background-clip:initial;border-style:none;float:none;line-height:normal;font-size:1px;vertical-align:baseline;display:inline-block;width:32px;height:20px;">
			<iframe ng-non-bindable="" frameborder="0" hspace="0" marginheight="0" marginwidth="0" scrolling="no" tabindex="0" vspace="0" width="100%" id="I0_1512626792258" name="I0_1512626792258" src="https://apis.google.com/u/0/se/0/_/+1/fastbutton?usegapi=1&amp;size=medium&amp;annotation=none&amp;origin=https%3A%2F%2Fwww.ianlewis.org&amp;url=https%3A%2F%2Fwww.ianlewis.org%2Fen%2Fbluegreen-deployments-kubernetes&amp;gsrc=3p&amp;ic=1&amp;jsh=m%3B%2F_%2Fscs%2Fapps-static%2F_%2Fjs%2Fk%3Doz.gapi.en_GB.XGzTsglXBGw.O%2Fm%3D__features__%2Fam%3DAQ%2Frt%3Dj%2Fd%3D1%2Frs%3DAGLTcCPzU1ZBFh7KM-q1zDRBeFKb5b_1xw#_methods=onPlusOne%2C_ready%2C_close%2C_open%2C_resizeMe%2C_renderstart%2Concircled%2Cdrefresh%2Cerefresh&amp;id=I0_1512626792258&amp;_gfid=I0_1512626792258&amp;parent=https%3A%2F%2Fwww.ianlewis.org&amp;pfname=&amp;rpctoken=11439094" data-gapiattached="true" title="G+" style="vertical-align:middle;display:block;width:32px;border-width:initial;border-style:none;position:static;top:0px;margin:0px;left:0px;visibility:visible;height:20px;">
			</iframe>
		</div>
		<iframe id="twitter-widget-0" scrolling="no" frameborder="0" allowtransparency="true" class="twitter-share-button twitter-share-button-rendered twitter-tweet-button" title="Twitter Tweet Button" src="https://platform.twitter.com/widgets/tweet_button.6b8337773e8a8ecc4f0b054fec8f1482.en.html#dnt=false&amp;id=twitter-widget-0&amp;lang=en&amp;original_referer=https%3A%2F%2Fwww.ianlewis.org%2Fen%2Fbluegreen-deployments-kubernetes&amp;related=IanMLewis&amp;size=m&amp;text=Blue%2FGreen%20Deployments%20on%20Kubernetes&amp;time=1512626792072&amp;type=share&amp;url=https%3A%2F%2Fwww.ianlewis.org%2Fen%2Fbluegreen-deployments-kubernetes&amp;via=IanMLewis" style="vertical-align:middle;display:block;width:63px;border-width:initial;border-style:none;position:static;visibility:visible;height:20px;">
		</iframe>
	</div>
	<p style="padding:0px;line-height:24px;font-size:14px;margin-top:0px;margin-bottom:16px;color:rgba(0, 0, 0, 0.87);font-family:Helvetica, Arial, sans-serif;white-space:normal;">
		<a href="https://www.ianlewis.org/en/tag/kubernetes" class="mdl-chip" style="-webkit-tap-highlight-color:rgba(255, 255, 255, 0);color:rgba(0, 0, 0, 0.87);height:32px;font-family:Roboto, Helvetica, Arial, sans-serif;line-height:32px;padding:0px 12px;border:0px;border-radius:16px;background-color:#DEDEDE;display:inline-block;margin:2px 0px;font-size:0px;white-space:nowrap;">kubernetes</a>
	</p>
	<div class="post-content" style="font-size:18px;color:rgba(0, 0, 0, 0.87);font-family:Helvetica, Arial, sans-serif;white-space:normal;">
		<blockquote style="font-family:Roboto, Helvetica, Arial, sans-serif;position:relative;font-size:24px;font-style:italic;line-height:1.35;letter-spacing:0.08em;padding:0px 0px 0px 15px;margin:0px 0px 18px;border-left:5px solid #EEEEEE;">
			<p style="padding:0px;line-height:22.5px;font-size:16px;letter-spacing:0px;margin-top:0px;margin-bottom:16px;">
				For those that want to dive right in, I have put up a tutorial and some sample manifests on github. Check it out at&nbsp;<a href="https://github.com/IanLewis/kubernetes-bluegreen-deployment-tutorial" style="-webkit-tap-highlight-color:rgba(255, 255, 255, 0);color:#448AFF;">https://github.com/IanLewis/kubernetes-bluegreen-deployment-tutorial</a>
			</p>
		</blockquote>
		<p style="padding:0px;line-height:24px;letter-spacing:0px;margin-top:0px;margin-bottom:16px;">
			Kubernetes has a really awesome built-in feature called&nbsp;<a href="https://github.com/kubernetes/kubernetes/tree/master/pkg/controller/deployment" style="-webkit-tap-highlight-color:rgba(255, 255, 255, 0);color:#448AFF;">Deployments</a>. Deployments come with the ability to do rolling updates of containers when you update your application to a new version. Rolling updates are a great way to update applications because your app uses about the same amount of resources during an update as it does when not updating, all with minimal impact to performance and availability.
		</p>
		<p style="padding:0px;line-height:24px;letter-spacing:0px;margin-top:0px;margin-bottom:16px;">
			However, there are many legacy applications out there that don't work well with rolling updates. Some applications simply need to deploy a new version and cut over to it right away. For this, we need to perform a&nbsp;<a href="https://martinfowler.com/bliki/BlueGreenDeployment.html" style="-webkit-tap-highlight-color:rgba(255, 255, 255, 0);color:#448AFF;">blue/green deployment</a>. With blue/green deployments a new copy of the application (green) is deployed alongside the existing version (blue). Then the ingress/router to the app is updated to switch to the new version (green). You then need to wait for the old (blue) version to finish the requests sent to it, but for the most part traffic to the app changes to the new version all at once.
		</p>
		<p style="padding:0px;line-height:24px;letter-spacing:0px;margin-top:0px;margin-bottom:16px;">
			<img class="align-center" src="https://storage.googleapis.com/static.ianlewis.org/prod/img/765/bg.gif" style="vertical-align:middle;max-width:100%;display:block;margin:0px auto;" />
		</p>
		<p style="padding:0px;line-height:24px;letter-spacing:0px;margin-top:0px;margin-bottom:16px;">
			Kubernetes doesn't have support for blue/green deployments built in. Currently the best way to do it is create a new deployment and then update the service for the application to point to the new deployment. Let's look at what that means.
		</p>
		<h2 style="padding:0px;font-family:Roboto, Helvetica, Arial, sans-serif;font-weight:400;font-size:34px;line-height:48px;margin:24px 0px;">
			The Blue Deployment
		</h2>
		<p style="padding:0px;line-height:24px;letter-spacing:0px;margin-top:0px;margin-bottom:16px;">
			A Kubernetes deployment specifies a group of instances of an application. Behind the scenes it creates a replicaset which is responsible for keeping the specified number of instances up and running.
		</p>
		<p style="padding:0px;line-height:24px;letter-spacing:0px;margin-top:0px;margin-bottom:16px;">
			<img class="align-center" src="https://storage.googleapis.com/static.ianlewis.org/prod/img/765/deployments.png" width="80%" style="vertical-align:middle;max-width:100%;display:block;margin:0px auto;" />
		</p>
		<p style="padding:0px;line-height:24px;letter-spacing:0px;margin-top:0px;margin-bottom:16px;">
			We can create our "blue" deployment by saving the following yaml to a file&nbsp;<code>blue.yaml</code>.
		</p>
		<div class="highlight" style="padding-left:5px;overflow:auto;">
<pre style="padding:15px;margin-top:0px;margin-bottom:9px;line-height:18px;word-break:break-all;word-wrap:break-word;white-space:pre-wrap;background-color:#F5F5F5;border:1px solid rgba(0, 0, 0, 0.15);border-radius:4px;font-family:Consolas, Inconsolata, Monoaco, monospace;"><span class="l l-Scalar l-Scalar-Plain">apiVersion</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">extensions/v1beta1</span> <span class="l l-Scalar l-Scalar-Plain">kind</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">Deployment</span> <span class="l l-Scalar l-Scalar-Plain">metadata</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">name</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">nginx-1.10</span> <span class="l l-Scalar l-Scalar-Plain">spec</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">replicas</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">3</span> <span class="l l-Scalar l-Scalar-Plain">template</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">metadata</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">labels</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">name</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">nginx</span> <span class="l l-Scalar l-Scalar-Plain">version</span><span class="p p-Indicator">:</span> <span class="s" style="color:#BA2121;">"1.10"</span> <span class="l l-Scalar l-Scalar-Plain">spec</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">containers</span><span class="p p-Indicator">:</span> <span class="p p-Indicator">-</span> <span class="l l-Scalar l-Scalar-Plain">name</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">nginx</span> <span class="l l-Scalar l-Scalar-Plain">image</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">nginx:1.10</span> <span class="l l-Scalar l-Scalar-Plain">ports</span><span class="p p-Indicator">:</span> <span class="p p-Indicator">-</span> <span class="l l-Scalar l-Scalar-Plain">name</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">http</span> <span class="l l-Scalar l-Scalar-Plain">containerPort</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">80</span> </pre>
		</div>
		<p style="padding:0px;line-height:24px;letter-spacing:0px;margin-top:0px;margin-bottom:16px;">
			You can then create the deployment using the kubectl command.
		</p>
		<div class="highlight" style="padding-left:5px;overflow:auto;">
<pre style="padding:15px;margin-top:0px;margin-bottom:9px;line-height:18px;word-break:break-all;word-wrap:break-word;white-space:pre-wrap;background-color:#F5F5F5;border:1px solid rgba(0, 0, 0, 0.15);border-radius:4px;font-family:Consolas, Inconsolata, Monoaco, monospace;">$ kubectl apply -f blue.yaml
</pre>
		</div>
		<p style="padding:0px;line-height:24px;letter-spacing:0px;margin-top:0px;margin-bottom:16px;">
			Once we have a deployment we can provide a way to access the instances of the deployment by creating a&nbsp;<a href="https://kubernetes.io/docs/concepts/services-networking/service/" style="-webkit-tap-highlight-color:rgba(255, 255, 255, 0);color:#448AFF;">Service</a>. Services are decoupled from deployments so that means that you don't explicitly point a service at a deployment. What you do instead is specify a&nbsp;<a href="https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/" style="-webkit-tap-highlight-color:rgba(255, 255, 255, 0);color:#448AFF;">label selector</a>&nbsp;which is used to list the pods that make up the service. When using deployments, this is typically set up so that it matches the pods for a deployment.
		</p>
		<p style="padding:0px;line-height:24px;letter-spacing:0px;margin-top:0px;margin-bottom:16px;">
			In this case we have two labels,&nbsp;<code>name=nginx</code>&nbsp;and&nbsp;<code>version=1.10</code>. We will set these as the label selector for the service below. Save this to&nbsp;<code>service.yaml</code>.
		</p>
		<div class="highlight" style="padding-left:5px;overflow:auto;">
<pre style="padding:15px;margin-top:0px;margin-bottom:9px;line-height:18px;word-break:break-all;word-wrap:break-word;white-space:pre-wrap;background-color:#F5F5F5;border:1px solid rgba(0, 0, 0, 0.15);border-radius:4px;font-family:Consolas, Inconsolata, Monoaco, monospace;"><span class="l l-Scalar l-Scalar-Plain">apiVersion</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">v1</span> <span class="l l-Scalar l-Scalar-Plain">kind</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">Service</span> <span class="l l-Scalar l-Scalar-Plain">metadata</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">name</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">nginx</span> <span class="l l-Scalar l-Scalar-Plain">labels</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">name</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">nginx</span> <span class="l l-Scalar l-Scalar-Plain">spec</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">ports</span><span class="p p-Indicator">:</span> <span class="p p-Indicator">-</span> <span class="l l-Scalar l-Scalar-Plain">name</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">http</span> <span class="l l-Scalar l-Scalar-Plain">port</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">80</span> <span class="l l-Scalar l-Scalar-Plain">targetPort</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">80</span> <span class="l l-Scalar l-Scalar-Plain">selector</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">name</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">nginx</span> <span class="l l-Scalar l-Scalar-Plain">version</span><span class="p p-Indicator">:</span> <span class="s" style="color:#BA2121;">"1.10"</span> <span class="l l-Scalar l-Scalar-Plain">type</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">LoadBalancer</span> </pre>
		</div>
		<p style="padding:0px;line-height:24px;letter-spacing:0px;margin-top:0px;margin-bottom:16px;">
			Creating the service will create a load balancer that is accessible outside the cluster.
		</p>
		<div class="highlight" style="padding-left:5px;overflow:auto;">
<pre style="padding:15px;margin-top:0px;margin-bottom:9px;line-height:18px;word-break:break-all;word-wrap:break-word;white-space:pre-wrap;background-color:#F5F5F5;border:1px solid rgba(0, 0, 0, 0.15);border-radius:4px;font-family:Consolas, Inconsolata, Monoaco, monospace;">$ kubectl apply -f service.yaml
</pre>
		</div>
		<p style="padding:0px;line-height:24px;letter-spacing:0px;margin-top:0px;margin-bottom:16px;">
			Now we have something that looks like this.
		</p>
		<p style="padding:0px;line-height:24px;letter-spacing:0px;margin-top:0px;margin-bottom:16px;">
			<img class="align-center" src="https://storage.googleapis.com/static.ianlewis.org/prod/img/765/blue.png" style="vertical-align:middle;max-width:100%;display:block;margin:0px auto;" />
		</p>
		<p style="padding:0px;line-height:24px;letter-spacing:0px;margin-top:0px;margin-bottom:16px;">
			You can test that the service is accessible and get the version.
		</p>
		<div class="highlight" style="padding-left:5px;overflow:auto;">
<pre style="padding:15px;margin-top:0px;margin-bottom:9px;line-height:18px;word-break:break-all;word-wrap:break-word;white-space:pre-wrap;background-color:#F5F5F5;border:1px solid rgba(0, 0, 0, 0.15);border-radius:4px;font-family:Consolas, Inconsolata, Monoaco, monospace;">$ <span class="nv" style="color:#19177C;">EXTERNAL_IP</span><span class="o" style="color:#666666;">=</span><span class="k" style="color:#008000;font-weight:bold;">$(</span>kubectl get svc nginx -o <span class="nv" style="color:#19177C;">jsonpath</span><span class="o" style="color:#666666;">=</span><span class="s2" style="color:#BA2121;">"{.status.loadBalancer.ingress[*].ip}"</span><span class="k" style="color:#008000;font-weight:bold;">)</span> $ curl -s http://<span class="nv" style="color:#19177C;">$EXTERNAL_IP</span>/version <span class="p">|</span> grep nginx
</pre>
		</div>
		<h2 style="padding:0px;font-family:Roboto, Helvetica, Arial, sans-serif;font-weight:400;font-size:34px;line-height:48px;margin:24px 0px;">
			Creating Green Deployment
		</h2>
		<p style="padding:0px;line-height:24px;letter-spacing:0px;margin-top:0px;margin-bottom:16px;">
			For the "green" deployment we will deploy a new deployment in parallel wit the "blue" deployment. If the following is in&nbsp;<code>green.yaml</code>...
		</p>
		<div class="highlight" style="padding-left:5px;overflow:auto;">
<pre style="padding:15px;margin-top:0px;margin-bottom:9px;line-height:18px;word-break:break-all;word-wrap:break-word;white-space:pre-wrap;background-color:#F5F5F5;border:1px solid rgba(0, 0, 0, 0.15);border-radius:4px;font-family:Consolas, Inconsolata, Monoaco, monospace;"><span class="l l-Scalar l-Scalar-Plain">apiVersion</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">extensions/v1beta1</span> <span class="l l-Scalar l-Scalar-Plain">kind</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">Deployment</span> <span class="l l-Scalar l-Scalar-Plain">metadata</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">name</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">nginx-1.11</span> <span class="l l-Scalar l-Scalar-Plain">spec</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">replicas</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">3</span> <span class="l l-Scalar l-Scalar-Plain">template</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">metadata</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">labels</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">name</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">nginx</span> <span class="l l-Scalar l-Scalar-Plain">version</span><span class="p p-Indicator">:</span> <span class="s" style="color:#BA2121;">"1.11"</span> <span class="l l-Scalar l-Scalar-Plain">spec</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">containers</span><span class="p p-Indicator">:</span> <span class="p p-Indicator">-</span> <span class="l l-Scalar l-Scalar-Plain">name</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">nginx</span> <span class="l l-Scalar l-Scalar-Plain">image</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">nginx:1.11</span> <span class="l l-Scalar l-Scalar-Plain">ports</span><span class="p p-Indicator">:</span> <span class="p p-Indicator">-</span> <span class="l l-Scalar l-Scalar-Plain">name</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">http</span> <span class="l l-Scalar l-Scalar-Plain">containerPort</span><span class="p p-Indicator">:</span> <span class="l l-Scalar l-Scalar-Plain">80</span> </pre>
		</div>
		<p style="padding:0px;line-height:24px;letter-spacing:0px;margin-top:0px;margin-bottom:16px;">
			... I can create the new deployment like so.
		</p>
		<div class="highlight" style="padding-left:5px;overflow:auto;">
<pre style="padding:15px;margin-top:0px;margin-bottom:9px;line-height:18px;word-break:break-all;word-wrap:break-word;white-space:pre-wrap;background-color:#F5F5F5;border:1px solid rgba(0, 0, 0, 0.15);border-radius:4px;font-family:Consolas, Inconsolata, Monoaco, monospace;">$ kubectl apply -f green.yaml
</pre>
		</div>
		<p style="padding:0px;line-height:24px;letter-spacing:0px;margin-top:0px;margin-bottom:16px;">
			Now I have two deployments but the service is still pointing to the "blue" one.
		</p>
		<p style="padding:0px;line-height:24px;letter-spacing:0px;margin-top:0px;margin-bottom:16px;">
			<img class="align-center" src="https://storage.googleapis.com/static.ianlewis.org/prod/img/765/bg_progress.png" style="vertical-align:middle;max-width:100%;display:block;margin:0px auto;" />
		</p>
		<h2 style="padding:0px;font-family:Roboto, Helvetica, Arial, sans-serif;font-weight:400;font-size:34px;line-height:48px;margin:24px 0px;">
			Updating the App
		</h2>
		<p style="padding:0px;line-height:24px;letter-spacing:0px;margin-top:0px;margin-bottom:16px;">
			To cut over to the "green" deployment we will update the selector for the service. Edit the&nbsp;<code>service.yaml</code>&nbsp;and change the selector version to "1.11". That will make it so that it matches the pods on the "green" deployment.
		</p>
		<div class="highlight" style="padding-left:5px;overflow:auto;">
<pre style="padding:15px;margin-top:0px;margin-bottom:9px;line-height:18px;word-break:break-all;word-wrap:break-word;white-space:pre-wrap;background-color:#F5F5F5;border:1px solid rgba(0, 0, 0, 0.15);border-radius:4px;font-family:Consolas, Inconsolata, Monoaco, monospace;"><span class="n">apiVersion</span><span class="o" style="color:#666666;">:</span> <span class="n">v1</span> <span class="n">kind</span><span class="o" style="color:#666666;">:</span> <span class="n">Service</span> <span class="n">metadata</span><span class="o" style="color:#666666;">:</span> <span class="n">name</span><span class="o" style="color:#666666;">:</span> <span class="n">nginx</span> <span class="n">labels</span><span class="o" style="color:#666666;">:</span> <span class="n">name</span><span class="o" style="color:#666666;">:</span> <span class="n">nginx</span> <span class="n">spec</span><span class="o" style="color:#666666;">:</span> <span class="n">ports</span><span class="o" style="color:#666666;">:</span> <span class="o" style="color:#666666;">-</span> <span class="n">name</span><span class="o" style="color:#666666;">:</span> <span class="n">http</span> <span class="n">port</span><span class="o" style="color:#666666;">:</span> <span class="mi" style="color:#666666;">80</span> <span class="n">targetPort</span><span class="o" style="color:#666666;">:</span> <span class="mi" style="color:#666666;">80</span> <span class="n">selector</span><span class="o" style="color:#666666;">:</span> <span class="n">name</span><span class="o" style="color:#666666;">:</span> <span class="n">nginx</span> <span class="n">version</span><span class="o" style="color:#666666;">:</span> <span class="s2" style="color:#BA2121;">"1.11"</span> <span class="n">type</span><span class="o" style="color:#666666;">:</span> <span class="n">LoadBalancer</span> </pre>
		</div>
		<p style="padding:0px;line-height:24px;letter-spacing:0px;margin-top:0px;margin-bottom:16px;">
			This apply will update the existing&nbsp;<code>nginx</code>&nbsp;service in place.
		</p>
		<div class="highlight" style="padding-left:5px;overflow:auto;">
<pre style="padding:15px;margin-top:0px;margin-bottom:9px;line-height:18px;word-break:break-all;word-wrap:break-word;white-space:pre-wrap;background-color:#F5F5F5;border:1px solid rgba(0, 0, 0, 0.15);border-radius:4px;font-family:Consolas, Inconsolata, Monoaco, monospace;">$ kubectl apply -f service.yaml
</pre>
		</div>
		<p style="padding:0px;line-height:24px;letter-spacing:0px;margin-top:0px;margin-bottom:16px;">
			Now we have something that looks like this.
		</p>
		<p style="padding:0px;line-height:24px;letter-spacing:0px;margin-top:0px;margin-bottom:16px;">
			<img class="align-center" src="https://storage.googleapis.com/static.ianlewis.org/prod/img/765/green.png" style="vertical-align:middle;max-width:100%;display:block;margin:0px auto;" />
		</p>
		<p style="padding:0px;line-height:24px;letter-spacing:0px;margin-top:0px;margin-bottom:16px;">
			Updating the selector for the service is applied immediately and so you should see that the new version of nginx is serving traffic.
		</p>
		<div class="highlight" style="padding-left:5px;overflow:auto;">
<pre style="padding:15px;margin-top:0px;margin-bottom:9px;line-height:18px;word-break:break-all;word-wrap:break-word;white-space:pre-wrap;background-color:#F5F5F5;border:1px solid rgba(0, 0, 0, 0.15);border-radius:4px;font-family:Consolas, Inconsolata, Monoaco, monospace;">$ <span class="nv" style="color:#19177C;">EXTERNAL_IP</span><span class="o" style="color:#666666;">=</span><span class="k" style="color:#008000;font-weight:bold;">$(</span>kubectl get svc nginx -o <span class="nv" style="color:#19177C;">jsonpath</span><span class="o" style="color:#666666;">=</span><span class="s2" style="color:#BA2121;">"{.status.loadBalancer.ingress[*].ip}"</span><span class="k" style="color:#008000;font-weight:bold;">)</span> $ curl -s http://<span class="nv" style="color:#19177C;">$EXTERNAL_IP</span>/version <span class="p">|</span> grep nginx
</pre>
		</div>
		<h2 style="padding:0px;font-family:Roboto, Helvetica, Arial, sans-serif;font-weight:400;font-size:34px;line-height:48px;margin:24px 0px;">
			Automating
		</h2>
		<p style="padding:0px;line-height:24px;letter-spacing:0px;margin-top:0px;margin-bottom:16px;">
			You can automate your blue/green deployment a bit with some scripting. The following script takes the name of the service, the version you want to deploy, and the path to the green deployment's yaml file and runs through a full blue/green deployment using kubectl to output raw JSON from the API and parsing it with jq. It waits for the green deployment to become ready by inspecting the&nbsp;<code>status.conditions</code>&nbsp;on the deployment object before updating the service definition.
		</p>
		<p style="padding:0px;line-height:24px;letter-spacing:0px;margin-top:0px;margin-bottom:16px;">
			The script makes some assumptions for simplicity's sake, such as expecting the deployment's name to be of the form&nbsp;<service>-<version>&nbsp;and that there are&nbsp;<code>name</code>&nbsp;and&nbsp;<code>version</code>&nbsp;labels that are used for the selector.&nbsp;<code>kubectl</code>&nbsp;is super flexible you can imagine writing something like this for your own needs.</version></service>
		</p>
		<div class="highlight" style="padding-left:5px;overflow:auto;">
<pre style="padding:15px;margin-top:0px;margin-bottom:9px;line-height:18px;word-break:break-all;word-wrap:break-word;white-space:pre-wrap;background-color:#F5F5F5;border:1px solid rgba(0, 0, 0, 0.15);border-radius:4px;font-family:Consolas, Inconsolata, Monoaco, monospace;"><span class="ch">#!/bin/bash</span> <span class="c1" style="color:#408080;font-style:italic;"># bg-deploy.sh &lt;servicename&gt; &lt;version&gt; &lt;green-deployment.yaml&gt;</span> <span class="c1" style="color:#408080;font-style:italic;"># Deployment name should be &lt;service&gt;-&lt;version&gt;</span> <span class="nv" style="color:#19177C;">DEPLOYMENTNAME</span><span class="o" style="color:#666666;">=</span><span class="nv" style="color:#19177C;">$1</span>-<span class="nv" style="color:#19177C;">$2</span> <span class="nv" style="color:#19177C;">SERVICE</span><span class="o" style="color:#666666;">=</span><span class="nv" style="color:#19177C;">$1</span> <span class="nv" style="color:#19177C;">VERSION</span><span class="o" style="color:#666666;">=</span><span class="nv" style="color:#19177C;">$2</span> <span class="nv" style="color:#19177C;">DEPLOYMENTFILE</span><span class="o" style="color:#666666;">=</span><span class="nv" style="color:#19177C;">$3</span> kubectl apply -f <span class="nv" style="color:#19177C;">$DEPLOYMENTFILE</span> <span class="c1" style="color:#408080;font-style:italic;"># Wait until the Deployment is ready by checking the MinimumReplicasAvailable condition.</span> <span class="nv" style="color:#19177C;">READY</span><span class="o" style="color:#666666;">=</span><span class="k" style="color:#008000;font-weight:bold;">$(</span>kubectl get deploy <span class="nv" style="color:#19177C;">$DEPLOYMENTNAME</span> -o json <span class="p">|</span> jq <span class="s1" style="color:#BA2121;">'.status.conditions[] | select(.reason == "MinimumReplicasAvailable") | .status'</span> <span class="p">|</span> tr -d <span class="s1" style="color:#BA2121;">'"'</span><span class="k" style="color:#008000;font-weight:bold;">)</span> <span class="k" style="color:#008000;font-weight:bold;">while</span> <span class="o" style="color:#666666;">[[</span> <span class="s2" style="color:#BA2121;">"</span><span class="nv" style="color:#19177C;">$READY</span><span class="s2" style="color:#BA2121;">"</span> !<span class="o" style="color:#666666;">=</span> <span class="s2" style="color:#BA2121;">"True"</span> <span class="o" style="color:#666666;">]]</span><span class="p">;</span> <span class="k" style="color:#008000;font-weight:bold;">do</span> <span class="nv" style="color:#19177C;">READY</span><span class="o" style="color:#666666;">=</span><span class="k" style="color:#008000;font-weight:bold;">$(</span>kubectl get deploy <span class="nv" style="color:#19177C;">$DEPLOYMENTNAME</span> -o json <span class="p">|</span> jq <span class="s1" style="color:#BA2121;">'.status.conditions[] | select(.reason == "MinimumReplicasAvailable") | .status'</span> <span class="p">|</span> tr -d <span class="s1" style="color:#BA2121;">'"'</span><span class="k" style="color:#008000;font-weight:bold;">)</span> sleep <span class="m" style="color:#666666;">5</span> <span class="k" style="color:#008000;font-weight:bold;">done</span> <span class="c1" style="color:#408080;font-style:italic;"># Update the service selector with the new version</span> kubectl patch svc <span class="nv" style="color:#19177C;">$SERVICE</span> -p <span class="s2" style="color:#BA2121;">"{\"spec\":{\"selector\": {\"name\": \"</span><span class="si" style="color:#BB6688;font-weight:bold;">${</span><span class="nv" style="color:#19177C;">SERVICE</span><span class="si" style="color:#BB6688;font-weight:bold;">}</span><span class="s2" style="color:#BA2121;">\", \"version\": \"</span><span class="si" style="color:#BB6688;font-weight:bold;">${</span><span class="nv" style="color:#19177C;">VERSION</span><span class="si" style="color:#BB6688;font-weight:bold;">}</span><span class="s2" style="color:#BA2121;">\"}}}"</span> <span class="nb" style="color:#008000;">echo</span> <span class="s2" style="color:#BA2121;">"Done."</span> </pre>
		</div>
		<p style="padding:0px;line-height:24px;letter-spacing:0px;margin-top:0px;margin-bottom:16px;">
			Hopefully Kubernetes will support blue/green deployments natively but until then you can get by with some automation like this. To connect with folks who care about how applications are deployed on Kubernetes check out the&nbsp;<code>#sig-apps</code>&nbsp;channel in the&nbsp;<a href="http://slack.kubernetes.io/" style="-webkit-tap-highlight-color:rgba(255, 255, 255, 0);color:#448AFF;">Kubernetes Slack</a>.
		</p>
	</div>
</p>