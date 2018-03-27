<span style="color:#555555;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">&lt;?php</span><br style="color:#555555;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">for ($i = 0; $i &lt;= 50; $i++) {</span><br style="color:#555555;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">printf("progress: [%-50s] %d%%\r", str_repeat('#',$i), $i * 2);</span><br style="color:#555555;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">usleep(1000 * 100);</span><br style="color:#555555;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">}</span><br style="color:#555555;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<span style="color:#555555;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">echo "/n";</span><br style="color:#555555;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;" />
<p>
	<span style="color:#555555;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">echo "Done./n";</span>
</p>
<p>
	<span style="color:#555555;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;"><br />
</span>
</p>
<p>
	<span style="color:#555555;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;"><br />
</span>
</p>
<p>
	<span style="color:#555555;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;"><br />
</span>
</p>
<p>
	<span style="color:#555555;font-family:font-size:14px;white-space:normal;background-color:#FFFFFF;">//<span style="color:#555555;font-family:&quot;font-size:14px;white-space:normal;background-color:#FFFFFF;">每次用 /r 结尾就是了。/n 是 new line，/r 是 return 。也就是回到行首。</span></span>
</p>