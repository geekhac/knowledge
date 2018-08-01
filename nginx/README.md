# Nginx
Nginx 是一个可靠、高效的web服务和代理中间件

## Nginx的优势
1. 使用epoll的方式进行IO多路复用
2. Nginx轻量级：它的功能模块少，代码模块化
3. cpu亲和，一个worker对应一个内核
4. 文件传递只经过内核空间，不经过用户空间，对静态资源的处理性能高

## Nginx的目录
| :--: | :--: | :--: |
| 路径 | 类型 | 作用 |
| /etc/logrotate.d/nginx | 配置文件 | Nginx日志轮转，用于logrotate服务的日志切割 ｜
