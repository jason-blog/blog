<p>
	docker ps
</p>
<p>
	<br />
</p>
<p>
	<span style="font-family:Consolas, &quot;white-space:normal;background-color:#FFFFFF;">docker&nbsp;inspect&nbsp;-f&nbsp;{{.State.Pid}}&nbsp;44fc0f0582d9 &nbsp;</span>
</p>
<p>
	<br />
</p>
<p>
	<span style="font-family:Consolas, &quot;white-space:normal;background-color:#FFFFFF;">sudo&nbsp;nsenter&nbsp;--target&nbsp;3326&nbsp;--mount&nbsp;--uts&nbsp;--ipc&nbsp;--net&nbsp;--pid &nbsp;</span>
</p>