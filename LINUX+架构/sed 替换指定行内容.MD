grep -n name apply-service.yaml | awk -F ":" '{print $1}' | awk 'BEGIN {min = 1000} {if ($1+0 &lt; min+0) min=$1} END {print min}'<br />
<br />
<br />
<p>
	sed "4c\\$(sed -n "4p" apply-service.yaml | sed "s/service/service-develop/g")" apply-service.yaml
</p>
<p>
	<br />
</p>
<p>
	<br />
</p>