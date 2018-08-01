# Nginx
Nginx 是一个可靠、高效的web服务和代理中间件

## Nginx的优势
1. 使用epoll的方式进行IO多路复用
2. Nginx轻量级：它的功能模块少，代码模块化
3. cpu亲和，一个worker对应一个内核
4. 文件传递只经过内核空间，不经过用户空间，对静态资源的处理性能高

## Nginx的目录

 路径 | 类型 | 作用 
:---|:---:|:---:
/etc/logrotate.d/nginx | 配置文件 | Nginx日志轮转，用于logrotate服务的日志切割
/etc/nginx  <br> /etc/nginx/nginx.conf  <br> /etc/nginx/conf.d <br> /etc/nginx/conf.d/default.conf |目录<br>配置文件|Ngnix主配置文件
/etc/nginx/fastcgi_params <br> /etc/nginx/uwsgi_params <br> /etc/nginx/scgi_params |配置文件|cgi配置相关 fastcgi相关配置
/etc/nginx/koi-utf <br> /etc/nginx/koi-win <br> /etc/nginx/win-utf |配置文件|编码转换映射转化文件
/etc/nginx/mime.type |配置文件|设置http协议的Content-Type与扩展名对应关系
/usr/lib/systemd/system/nginx-debug.service <bt> /usr/lib/systemd/system/nginx.service <br> /etc/sysconfig/nginx <br> /etc/sysconfig/ngnix-debug |配置文件|用于配置出系统守护进程管理器管理方式
/usr/lib64/nginx/modules <br> /etc/nginx/modules |目录| Nginx模块目录
/usr/sbin/nginx <br> /usr/sbin/nginx-debug |命令| Nginx服务的启动管理的终端命令
/usr/share/doc/nginx-1.12.0 <br> /usr/share/doc/nginx-1.12.0/COPYRIGHT <br> /usr/share/man/man8/nginx.8.gz |文件<br>目录|Nginx手册和帮助文件
/var/cecha/nginx |目录|Nginx的缓存目录
/var/log/nginx |目录| Nginx的日志目录
