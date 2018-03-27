<p style="margin:10px auto;padding:0px;font-family:Verdana, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
	ngx_lua模块的原理：
</p>
<p style="margin:10px auto;padding:0px;font-family:Verdana, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
	1、每个worker（工作进程）创建一个Lua VM，worker内所有协程共享VM；<br style="margin:0px;padding:0px;" />
2、将Nginx I/O原语封装后注入 Lua VM，允许Lua代码直接访问；<br style="margin:0px;padding:0px;" />
3、每个外部请求都由一个Lua协程处理，协程之间数据隔离；<br style="margin:0px;padding:0px;" />
4、Lua代码调用I/O操作等异步接口时，会挂起当前协程（并保护上下文数据），而不阻塞worker；<br style="margin:0px;padding:0px;" />
5、I/O等异步操作完成时还原相关协程上下文数据，并继续运行；
</p>
<p style="margin:10px auto;padding:0px;font-family:Verdana, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin:10px auto;padding:0px;font-family:Verdana, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
	<strong style="margin:0px;padding:0px;">ngx_lua 模块提供的指令和API等：</strong>
</p>
<table border="0" cellspacing="0" cellpadding="0" style="margin:0px;padding:0px;border-spacing:0px;border:1px solid silver;word-break:break-word;color:#000000;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:12px;background-color:#FFFFFF;" class="ke-zeroborder">
	<colgroup style="margin:0px;padding:0px;"><col width="404" style="margin:0px;padding:0px;" /><col width="615" style="margin:0px;padding:0px;" /></colgroup>
	<tbody style="margin:0px;padding:0px;">
		<tr style="margin:0px;padding:0px;">
			<td class="xl63" width="404" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				指令名称
			</td>
			<td class="xl63" width="615" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				说明
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				lua_use_default_type
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				是否使用default_type指令定义的Content-Type默认值
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				lua_code_cache
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				*_by_lua_file文件是否cache
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				lua_regex_cache_max_entries
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				lua_regex_match_limit
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				lua_package_path
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				用Lua写的lua外部库路径（.lua文件）
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				lua_package_cpath
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				用C写的lua外部库路径（.so文件）
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				init_by_lua
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				master进程启动时挂载的lua代码
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl68" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				init_by_lua_file
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				init_worker_by_lua
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				worker进程启动时挂载的lua代码，常用来执行一些定时器任务
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl68" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				init_worker_by_lua_file
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				set_by_lua
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				设置变量
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl68" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				set_by_lua_file
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				content_by_lua
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				handler模块
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl68" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				content_by_lua_file
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				rewrite_by_lua
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl68" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				rewrite_by_lua_file
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				access_by_lua
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl68" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				access_by_lua_file
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				header_filter_by_lua
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				header filter模块
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl68" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				header_filter_by_lua_file
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				body_filter_by_lua
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				body filter模块，ngx.arg[1]代表输入的chunk，ngx.arg[2]代表当前chunk是否为last
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl68" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				body_filter_by_lua_file
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				log_by_lua
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl68" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				log_by_lua_file
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				lua_need_request_body
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				是否读请求体，跟ngx.req.read_body()函数作用类似
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl64" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				lua_shared_dict
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				创建全局共享的table（多个worker进程共享）
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl66" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				lua_socket_connect_timeout
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				TCP/unix 域socket对象connect方法的超时时间
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl66" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				lua_socket_send_timeout
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				TCP/unix 域socket对象send方法的超时时间
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl66" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				lua_socket_send_lowat
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				设置cosocket send buffer的low water值
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl66" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				lua_socket_read_timeout
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				TCP/unix 域socket对象receive方法的超时时间
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl66" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				lua_socket_buffer_size
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				cosocket读buffer大小
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl66" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				lua_socket_pool_size
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				cosocket连接池大小
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl66" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				lua_socket_keepalive_timeout
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				cosocket长连接超时时间
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl66" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				lua_socket_log_errors
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				是否打开cosocket错误日志
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl65" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				lua_ssl_ciphers
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl65" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				lua_ssl_crl
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl65" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				lua_ssl_protocols
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl65" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				lua_ssl_trusted_certificate
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl65" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				lua_ssl_verify_depth
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				lua_http10_buffering
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				rewrite_by_lua_no_postpone
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				lua_transform_underscores_in_response_headers
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				lua_check_client_abort
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				是否监视client提前关闭请求的事件，如果打开监视，会调用ngx.on_abort()注册的回调
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				lua_max_pending_timers
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				lua_max_running_timers
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
	</tbody>
</table>
<p style="margin:10px auto;padding:0px;font-family:Verdana, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin:10px auto;padding:0px;font-family:Verdana, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<p style="margin:10px auto;padding:0px;font-family:Verdana, Arial, Helvetica, sans-serif;white-space:normal;background-color:#FFFFFF;">
	&nbsp;
</p>
<table border="0" cellspacing="0" cellpadding="0" style="margin:0px;padding:0px;border-spacing:0px;border:1px solid silver;word-break:break-word;color:#000000;font-family:Verdana, Arial, Helvetica, sans-serif;font-size:12px;background-color:#FFFFFF;" class="ke-zeroborder">
	<colgroup style="margin:0px;padding:0px;"><col width="262" style="margin:0px;padding:0px;" /><col width="389" style="margin:0px;padding:0px;" /></colgroup>
	<tbody style="margin:0px;padding:0px;">
		<tr style="margin:0px;padding:0px;">
			<td class="xl72" width="262" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				table
			</td>
			<td class="xl72" width="389" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				说明
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl74" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.arg
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				指令参数，如跟在content_by_lua_file后面的参数
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl74" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.var
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				变量，ngx.var.VARIABLE引用某个变量
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl74" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.ctx
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				请求的lua上下文
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.header
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				响应头，ngx.header.HEADER引用某个头
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.status
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				响应码
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl65" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl72" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				API
			</td>
			<td class="xl72" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				说明
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl75" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.log
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				输出到error.log
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl76" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				print
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				等价于 ngx.log(ngx.NOTICE, ...)
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl76" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.send_headers
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				发送响应头
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl76" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.headers_sent
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				响应头是否已发送
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl76" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.resp.get_headers
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				获取响应头
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl77" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.timer.at
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				注册定时器事件
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl76" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.is_subrequest
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				当前请求是否是子请求
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl75" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.location.capture
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				发布一个子请求
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl75" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.location.capture_multi
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				发布多个子请求
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl76" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.exec
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl76" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.redirect
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl77" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.print
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				输出响应
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl75" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.say
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				输出响应，自动添加'\n'
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl76" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.flush
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				刷新响应
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl75" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.exit
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				结束请求
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl76" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.eof
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl76" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.sleep
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				无阻塞的休眠（使用定时器实现）
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl76" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.get_phase
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl76" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.on_abort
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				注册client断开请求时的回调函数
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl76" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ndk.set_var.DIRECTIVE
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.req.start_time
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				请求的开始时间
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.req.http_version
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				请求的HTTP版本号
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.req.raw_header
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				请求头（包括请求行）
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.req.get_method
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				请求方法
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.req.set_method
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				请求方法重载
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.req.set_uri
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				请求URL重写
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.req.set_uri_args
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl71" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.req.get_uri_args
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				获取请求参数
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl71" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.req.get_post_args
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				获取请求表单
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.req.get_headers
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				获取请求头
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.req.set_header
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.req.clear_header
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.req.read_body
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				读取请求体
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.req.discard_body
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				扔掉请求体
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.req.get_body_data
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.req.get_body_file
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.req.set_body_data
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.req.set_body_file
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.req.init_body
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.req.append_body
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.req.finish_body
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.req.socket
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl68" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.escape_uri
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				字符串的url编码
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl68" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.unescape_uri
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				字符串url解码
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl68" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.encode_args
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				将table编码为一个参数字符串
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl68" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.decode_args
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				将参数字符串编码为一个table
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl68" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.encode_base64
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				字符串的base64编码
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl68" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.decode_base64
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				字符串的base64解码
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl68" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.crc32_short
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				字符串的crs32_short哈希
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl68" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.crc32_long
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				字符串的crs32_long哈希
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl68" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.hmac_sha1
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				字符串的hmac_sha1哈希
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl68" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.md5
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				返回16进制MD5
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl68" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.md5_bin
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				返回2进制MD5
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl68" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.sha1_bin
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				返回2进制sha1哈希值
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl68" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.quote_sql_str
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				SQL语句转义
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.today
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				返回当前日期
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.time
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				返回UNIX时间戳
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.now
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				返回当前时间
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.update_time
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				刷新时间后再返回
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.localtime
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.utctime
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.cookie_time
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				返回的时间可用于cookie值
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.http_time
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				返回的时间可用于HTTP头
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.parse_http_time
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				解析HTTP头的时间
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl68" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.re.match
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl68" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.re.find
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl68" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.re.gmatch
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl68" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.re.sub
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl68" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.re.gsub
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.shared.DICT
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.shared.DICT.get
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.shared.DICT.get_stale
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.shared.DICT.set
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.shared.DICT.safe_set
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.shared.DICT.add
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.shared.DICT.safe_add
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.shared.DICT.replace
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.shared.DICT.delete
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.shared.DICT.incr
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.shared.DICT.flush_all
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.shared.DICT.flush_expired
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.shared.DICT.get_keys
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl70" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.socket.udp
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl70" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				udpsock:setpeername
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl70" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				udpsock:send
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl70" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				udpsock:receive
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl70" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				udpsock:close
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl70" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				udpsock:settimeout
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl69" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.socket.tcp
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl69" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				tcpsock:connect
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl69" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				tcpsock:sslhandshake
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl69" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				tcpsock:send
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl69" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				tcpsock:receive
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl69" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				tcpsock:receiveuntil
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl69" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				tcpsock:close
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl69" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				tcpsock:settimeout
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl69" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				tcpsock:setoption
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl69" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				tcpsock:setkeepalive
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl69" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				tcpsock:getreusedtimes
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl69" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.socket.connect
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.thread.spawn
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.thread.wait
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.thread.kill
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				coroutine.create
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				coroutine.resume
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				coroutine.yield
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				coroutine.wrap
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				coroutine.running
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl67" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				coroutine.status
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl68" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.config.debug
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				编译时是否有 --with-debug选项
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl68" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.config.prefix
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				编译时的 --prefix选项
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl68" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.config.nginx_version
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				返回nginx版本号
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl68" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.config.nginx_configure
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				返回编译时 ./configure的命令行选项
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl68" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.config.ngx_lua_version
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				返回ngx_lua模块版本号
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl68" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.worker.exiting
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				当前worker进程是否正在关闭（如reload、shutdown期间）
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl68" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.worker.pid
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				返回当前worker进程的pid
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
			<td style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td class="xl73" height="18" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				常量
			</td>
			<td class="xl72" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				说明
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td height="108" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				Core constants
			</td>
			<td class="xl66" width="389" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.OK (0)<br style="margin:0px;padding:0px;" />
ngx.ERROR (-1)<br style="margin:0px;padding:0px;" />
ngx.AGAIN (-2)<br style="margin:0px;padding:0px;" />
ngx.DONE (-4)<br style="margin:0px;padding:0px;" />
ngx.DECLINED (-5)<br style="margin:0px;padding:0px;" />
ngx.nil
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td height="270" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				HTTP method constants
			</td>
			<td class="xl66" width="389" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.HTTP_GET<br style="margin:0px;padding:0px;" />
ngx.HTTP_HEAD<br style="margin:0px;padding:0px;" />
ngx.HTTP_PUT<br style="margin:0px;padding:0px;" />
ngx.HTTP_POST<br style="margin:0px;padding:0px;" />
ngx.HTTP_DELETE<br style="margin:0px;padding:0px;" />
ngx.HTTP_OPTIONS&nbsp;&nbsp;<br style="margin:0px;padding:0px;" />
ngx.HTTP_MKCOL&nbsp;&nbsp;&nbsp;&nbsp;<br style="margin:0px;padding:0px;" />
ngx.HTTP_COPY&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<br style="margin:0px;padding:0px;" />
ngx.HTTP_MOVE&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<br style="margin:0px;padding:0px;" />
ngx.HTTP_PROPFIND&nbsp;<br style="margin:0px;padding:0px;" />
ngx.HTTP_PROPPATCH&nbsp;<br style="margin:0px;padding:0px;" />
ngx.HTTP_LOCK&nbsp;<br style="margin:0px;padding:0px;" />
ngx.HTTP_UNLOCK&nbsp;&nbsp;&nbsp;&nbsp;<br style="margin:0px;padding:0px;" />
ngx.HTTP_PATCH&nbsp;&nbsp;&nbsp;<br style="margin:0px;padding:0px;" />
ngx.HTTP_TRACE&nbsp;&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td height="306" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				HTTP status constants
			</td>
			<td class="xl66" width="389" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.HTTP_OK (200)<br style="margin:0px;padding:0px;" />
ngx.HTTP_CREATED (201)<br style="margin:0px;padding:0px;" />
ngx.HTTP_SPECIAL_RESPONSE (300)<br style="margin:0px;padding:0px;" />
ngx.HTTP_MOVED_PERMANENTLY (301)<br style="margin:0px;padding:0px;" />
ngx.HTTP_MOVED_TEMPORARILY (302)<br style="margin:0px;padding:0px;" />
ngx.HTTP_SEE_OTHER (303)<br style="margin:0px;padding:0px;" />
ngx.HTTP_NOT_MODIFIED (304)<br style="margin:0px;padding:0px;" />
ngx.HTTP_BAD_REQUEST (400)<br style="margin:0px;padding:0px;" />
ngx.HTTP_UNAUTHORIZED (401)<br style="margin:0px;padding:0px;" />
ngx.HTTP_FORBIDDEN (403)<br style="margin:0px;padding:0px;" />
ngx.HTTP_NOT_FOUND (404)<br style="margin:0px;padding:0px;" />
ngx.HTTP_NOT_ALLOWED (405)<br style="margin:0px;padding:0px;" />
ngx.HTTP_GONE (410)<br style="margin:0px;padding:0px;" />
ngx.HTTP_INTERNAL_SERVER_ERROR (500)<br style="margin:0px;padding:0px;" />
ngx.HTTP_METHOD_NOT_IMPLEMENTED (501)<br style="margin:0px;padding:0px;" />
ngx.HTTP_SERVICE_UNAVAILABLE (503)<br style="margin:0px;padding:0px;" />
ngx.HTTP_GATEWAY_TIMEOUT (504)&nbsp;
			</td>
		</tr>
		<tr style="margin:0px;padding:0px;">
			<td height="162" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				Nginx log level constants
			</td>
			<td class="xl66" width="389" style="margin:0px;padding:3px;border:1px solid silver;border-collapse:collapse;">
				ngx.STDERR<br style="margin:0px;padding:0px;" />
ngx.EMERG<br style="margin:0px;padding:0px;" />
ngx.ALERT<br style="margin:0px;padding:0px;" />
ngx.CRIT<br style="margin:0px;padding:0px;" />
ngx.ERR<br style="margin:0px;padding:0px;" />
ngx.WARN<br style="margin:0px;padding:0px;" />
ngx.NOTICE<br style="margin:0px;padding:0px;" />
ngx.INFO<br style="margin:0px;padding:0px;" />
ngx.DEBUG<br style="margin:0px;padding:0px;" />
			</td>
		</tr>
	</tbody>
</table>