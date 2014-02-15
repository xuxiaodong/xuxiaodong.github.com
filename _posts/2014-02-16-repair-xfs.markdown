---
layout: post
title: 修复 XFS 文件系统错误
date: 2014-02-16 00:10
post-link:
---

在强制关机后，我的 Funtoo 重启时遇到了下面的错误:

    mount: mount /dev/mapper/vg-home on /home failed: Structure
    needs cleaning

从出错提示可以看出，将 `/dev/mapper/vg-home` 挂载到 `/home` 时
失败了。

通过 `TTY2` 登录系统后，执行 `xfs_repair` 命令对 XFS 文件系统
先进行检查。

    xfs_repair -n -v /dev/mapper/vg-home

一番扫描下来果然发现了错误。接着，修复这些错误：

    xfs_repair -L -v /dev/mapper/vg-home

完成后，再次 mount 正常。
