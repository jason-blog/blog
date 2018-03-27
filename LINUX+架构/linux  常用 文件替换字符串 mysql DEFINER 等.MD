<p>
	&nbsp;find -name config.properties |&nbsp; xargs perl -pi -e 's|test(.*?)$|test=0 0 \* \* \* ?|g'
</p>
<p>
	&nbsp;find -name config.* | xargs grep -l 'service' | xargs sed -i 's/localhost/docker/g'
</p>
<p>
	&nbsp;find -name config.* | xargs grep -l 'service' | xargs perl -pi -e 's/docker/localhost-docker/g'
</p>
<p>
	<br />
</p>
<p>
	&nbsp;sed -n '100,200p'&nbsp;filename //显示100-200行
</p>
<p>
	<span style="white-space:normal;">&nbsp;sed -n '100,$p'&nbsp;filename //显示100-最后行</span> 
</p>
<p>
	&nbsp;sed -i&nbsp;sed -e 's/DEFINER=`root.*`/''/g' t.sql //特么的没有&nbsp;括号和？
</p>
<div>
	<br />
</div>
<p>
	<br />
</p>
<p style="white-space:normal;">
	&nbsp;sed -n '100,200d'&nbsp;filename //删除100-200行
</p>
<div>
	<span style="white-space:normal;">&nbsp;sed -i 's/localhost/docker/g'</span>&nbsp;<span style="white-space:normal;">filename&nbsp; 替换文件</span><br />
</div>
<p>
	<br />
</p>
<p>
	&nbsp;grep 'test.*.jar' //.*&nbsp;没有?&nbsp;我去你大爷的&nbsp;浪费我半天时间
</p>
<p>
	&nbsp;grep -rl 'windows' ./path | xargs sed -i 's/windows/linux/g'
</p>
<p>
	<span style="font-family:Monaco, &quot;white-space:normal;background-color:#FAFAFA;">&nbsp;find -name config.* | xargs grep&nbsp; 'service' |awk -F ':' '{print $1}' |sort |uniq</span> 
</p>
<p>
	<span style="font-family:Monaco, &quot;white-space:normal;background-color:#FAFAFA;">&nbsp;</span> 
</p>
<p>
	<span style="font-family:Monaco, &quot;white-space:normal;background-color:#FAFAFA;">&nbsp;#remove DEFINER&nbsp;</span> 
</p>
<p>
	<span style="font-family:Monaco, &quot;white-space:normal;background-color:#FAFAFA;">&nbsp;cat&nbsp;test.sql | sed -e 's/DEFINER=`.*`@`[^`][^`]*`//g' &gt; test.sql<br />
</span> 
</p>
<p>
	<span style="font-family:Monaco, &quot;white-space:normal;background-color:#FAFAFA;">&nbsp;正则中&nbsp;<span style="font-family:Monaco, &quot;white-space:normal;background-color:#FAFAFA;">[^`]*&nbsp;是可以包含&nbsp;指定的范围标识的&nbsp;比如 `[`localhost`]`&nbsp;&nbsp;</span></span> 
</p>
<p>
	<span style="font-family:Monaco, &quot;white-space:normal;background-color:#FAFAFA;"><span style="font-family:Monaco, &quot;white-space:normal;background-color:#FAFAFA;"><br />
</span></span>
</p>
<p>
	<span style="font-family:Monaco, &quot;white-space:normal;background-color:#FAFAFA;"><span style="font-family:Monaco, &quot;white-space:normal;background-color:#FAFAFA;">#去掉 <span style="font-family:Monaco, &quot;white-space:normal;background-color:#FAFAFA;">AUTO_INCREMENT</span><br />
</span></span>
</p>
<p>
	<span style="font-family:Monaco, &quot;white-space:normal;background-color:#FAFAFA;"><span style="font-family:Monaco, &quot;white-space:normal;background-color:#FAFAFA;">sed 's/AUTO_INCREMENT=[0-9]*//g'<br />
</span></span>
</p>
<p>
	<span style="font-family:Monaco, &quot;white-space:normal;background-color:#FAFAFA;"><br />
</span> 
</p>