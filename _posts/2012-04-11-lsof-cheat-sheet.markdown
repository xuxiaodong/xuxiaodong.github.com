---
layout: post
title: lsof Cheat Sheet
date: 2012-04-11 21:59
post-link: http://www.catonmat.net/blog/unix-utilities-lsof/
---

lsof 即 list open files，它能够列出进程所打开文件的相关信息。lsof 被誉为 Unix
调试的瑞士军刀，值得我们花时间掌握之。

    lsof                       # 列出所有打开的文件
    lsof /path/to/file         # 查询谁在使用文件
    lsof +D /usr/lib           # 递归查询目录中打开的所有文件 (较慢)
    lsof | grep '/usr/lib'     # 同上，较快
    lsof -u user               # 列出由 user 打开的所有文件 (逗号可分隔多个用户)
    lsof -c program            # 列出由 program 程序打开的所有文件
    lsof -a -u user -c program # 列出由 user 及 program 打开的所有文件
    lsof -u ^user              # 列出除 user 之外用户打开的所有文件
    lsof -p num                # 列出 PID 为 num 打开的所有文件
    lsof -i                    # 列出所有网络连接
    lsof -i tcp                # 列出所有 TCP 网络连接
    lsof -i udp                # 列出所有 UDP 网络连接
    lsof -i :port              # 查询谁使用端口
    lsof -i tcp:port           # 查询谁使用 TCP 端口
    lsof -a -u user -i         # 查询 user 的所有网络活动
    lsof -N                    # 列出所有 NFS 文件
    lsof -U                    # 列出所有 Unix 域 socket 文件
    lsof -g num                # 列出具有组 ID 进程打开的所有文件
    lsof -d num                # 列出与文件描述符 num 关联的所有文件
    lsof -t -i                 # 输出使用某些资源的 PID
    lsof -r second             # 重复列出文件
