---
layout: post
title: 'ss: socket 统计'
date: 2013-10-22 10:10
post-link: http://www.tecmint.com/11-lesser-known-useful-linux-commands/
---

一般来说，使用 `netstat` 命令可以获得有关 socket 的信息。但其实，有一个专门的
socket 统计工具 `ss`。ss 即 socket statistics 的简称，用来获取 socket 的
统计信息。

例如，在 Linux 下执行 `ss -t -l -4` 后输出如下：

    State      Recv-Q Send-Q      Local Address:Port          Peer Address:Port   
    LISTEN     0      10                      *:8888                     *:*       
    LISTEN     0      20              127.0.0.1:smtp                     *:*       
    LISTEN     0      128                     *:42301                    *:*       
    LISTEN     0      3                       *:4000                     *:*       
    LISTEN     0      3                       *:4001                     *:*       
    LISTEN     0      3                       *:6881                     *:*       
    LISTEN     0      3                       *:6882                     *:*       
    LISTEN     0      50              127.0.0.1:mysql                    *:*       
    LISTEN     0      128                     *:sunrpc                   *:*       
    LISTEN     0      3                       *:4080                     *:*       
    LISTEN     0      5                       *:10128                    *:*       
    LISTEN     0      5                       *:4242                     *:*       
    LISTEN     0      10                      *:26323                    *:*       
    LISTEN     0      128                     *:ssh                      *:*       

这显示正在监听的 IPv4 TCP socket。`ss` 包含许多重要的选项，其主要作用为：

    -t 显示 TCP socket
    -u 显示 UDP socket
    -x 显示 Unix 域 socket
    -a 显示监听及非监听 socket
    -l 仅显示正在监听的 socket
    -4 仅显示 IPv4 socket
    -6 仅显示 IPv6 socket
    -m 显示 socket 内存占用
    -p 显示使用 socket 的进程
    -s 打印汇总信息

当然，关于 `ss` 的更多用法可以通过 `ss -h` 或 `man ss` 了解。
