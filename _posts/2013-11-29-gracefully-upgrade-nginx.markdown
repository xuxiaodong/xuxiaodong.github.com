---
layout: post
title: NGINX 平滑升级
date: 2013-11-29 10:27
post-link: http://wiki.nginx.org/CommandLine#Upgrading_To_a_New_Binary_On_The_Fly
---

NGINX 允许对自身进行平滑升级，这样可以继续保持服务，不至于让网站下线。在对 NGINX
升级后，只需执行以下步骤即可：

1、对 NGINX 的 master 进程发送 `USR2` 信号。这将重命名 `.pid` 文件为
`.oldbin`，并执行新的二进制文件。

    cd /usr/local/webserver/nginx
    kill -USR2 $(cat logs/nginx.pid)

2、对 NGINX 的旧 master 进程发送 `WINCH` 信号。这将平滑关闭旧的 worker 进程。

    kill -WINCH $(cat logs/nginx.pid.oldbin)

3、对 NGINX 的旧 master 进程发送 `QUIT` 信号。如果升级成功，那么可以关闭旧的
master 进程，仅保留新的进程提供服务。

    kill -QUIT $(cat logs/nginx.pid.oldbin)
