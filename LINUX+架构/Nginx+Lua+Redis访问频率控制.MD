<h2 id="前言" style="margin:0.8em 0px;padding:0px;box-sizing:border-box;font-weight:100;font-family:&quot;white-space:normal;background-color:#FFFFFF;">
<pre class="prettyprint lang-js linenums">前言：

Nginx来处理访问控制的方法有多种，实现的效果也有多种，访问IP段，访问内容限制，访问频率限制等。

用Nginx+Lua+Redis来做访问限制主要是考虑到高并发环境下快速访问控制的需求。

Nginx处理请求的过程一共划分为11个阶段，分别是：

post-read、server-rewrite、find-config、rewrite、post-rewrite、 preaccess、access、post-access、try-files、content、log.

在openresty中，可以找到：

set_by_lua，access_by_lua，content_by_lua，rewrite_by_lua等方法。

那么访问控制应该是，access阶段。

怎么做？

1、方案 
按照正常的逻辑思维，我们会想到的访问控制方案如下： 
1.检测是否被forbidden？ 
=》是，forbidden是否到期：是，清除记录，返回200，正常访问；否，返回403； 
=》否，返回200，正常访问 
2.每次访问，访问用户的访问频率+1处理 
3.检测访问频率是否超过限制，超过即添加forbidden记录，返回403

这是简单地方案，还可以添加点枝枝叶叶，访问禁止时间通过算法导入，每次凹曲线增加。

2、配置 
首先为nginx添加vhost配置文件，vhost.conf部分内容如下：

lua_package_path "/usr/local/openresty/lualib/?.lua;;";#告诉openresty库地址
lua_package_cpath "/usr/local/openresty/lualib/?.so;;";
error_log /usr/local/openresty/nginx/logs/openresty.debug.log debug;

server {
    listen 8080 default;
    server_name localhost;    
    root  /www/openresty;

    location /login {
        default_type 'text/html';
        access_by_lua_file "/usr/local/openresty/nginx/lua/access_by_redis.lua";#通过lua来处理访问控制
    }
}

3.Access_by_redis.lua 
参考了下v2ex.com的做法，redis存储方案只做简单地string存储就足够了。key分别是：

用户登录记录：user:127.0.0.1:time（unix时间戳） 
访问限制：block:127.0.0.1

local red = redis:new()
// 连接Redis
function M:redis()
    red:set_timeout(1000)
    local ok, err = red:connect("127.0.0.1", 6379)
    if not ok then
        ngx.exit(ngx.HTTP_INTERNAL_SERVER_ERROR)
    end
end

// 检测是否forbidden，下面我们就检测block:127.0.0.1，如果搜索到数据，检测时间是否过期，未过期返回403，否则直接返回200：
function M:check1()
    local time=os.time()    --system time
    local res, err = red:get("block:"..ngx.var.remote_addr)
    if not res then -- redis error
        ngx.exit(ngx.HTTP_INTERNAL_SERVER_ERROR) --redis get data error     end

    if type(res) == "string" then --if red not null then type(red)==string
        if tonumber(res) &gt;= tonumber(time) then  --check if forbidden expired
            ngx.exit(ngx.HTTP_FORBIDDEN)
            --ngx.say("forbidden")
        end
    end
}

// 检测，是否访问频率过高，如果过高，要拉到黑名单的，
实现的方法是，检测user:127.0.0.1:time的值是否超标：
function M:check2()
    local time=os.time()    --system time
    local res, err = red:get("user:"..ngx.var.remote_addr..":"..time)
    if not res then -- redis error
        ngx.exit(ngx.HTTP_INTERNAL_SERVER_ERROR) --redis get data error
    end

    if type(res) == "string" then
        if tonumber(res) &gt;= 10 then -- attack, 10 times request/s
            red:del("block:"..self.ip)  
            red:set("block:"..self.ip, tonumber(time)+5*60 ) --set block time
            ngx.exit(ngx.HTTP_FORBIDDEN)
        end
    end
end

// 把每次访问时间做一个自增长，user:127.0.0.1:time：
function M:add()
    local time=os.time()    --system time
    ok, err = red:incr("user:"..ngx.var.remote_addr..":"..time)
    if not ok then
        ngx.exit(ngx.HTTP_INTERNAL_SERVER_ERROR) --redis get data error
    end
end

那么，测试，强刷几次浏览器，发现过一会，返回了403，ok，搞定。

本文转载自： 夏日小草 
原文作者： 夏日小草 
原文出处 : http://homeway.me/2015/08/11/nginx-lua-redis-access-control/</pre>
<br />
</h2>