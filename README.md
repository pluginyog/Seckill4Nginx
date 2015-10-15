# Seckill4Nginx
Nginx Plugin, for e-commence mall second kill activity. using Lua, PHP and Redis.


##architecture
client ->nginx -> lua (+1)->redis->

if  left>0 ->->PHP-FPM (handle request) ->client

else ->->client


##Install
1.install openresty,php,redis

2.copy lua_script and php_scripts to web document, default path is /opt/htdocs/lua_queue,

3.config nginx, copy nginx configration to openresty directory , for instance /opt/ngx_openresty_1.7.2.1/nginx/conf

4.edit configure, conf/vhosts/lua_queue.com.conf

	line 2: redis service cofig, server ip:port
	
	line 8: web domain config, 
	
	line 9: web and php config，root directory, default path is /opt/htdocs/lua_queue/php_scripts
	
	line 27: lua config, root directory, default path is /opt/htdocs/lua_queue/lua_scripts/content.lua
	
5.restart nginx

6.config /etc/hosts

7.redis config, php_script/config.php

8.add a cron task,*/1 * * * * php /opt/htdocs/lua_queue/php_scripts/cron_queue.php

9. open the index page for testing.


##Thanks To:
http://openresty.org/cn/index.html

http://wiki.nginx.org/HttpRedis2Module
