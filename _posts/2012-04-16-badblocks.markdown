---
layout: post
title: 使用 badblocks 检测磁盘坏块
date: 2012-04-16 21:53
post-link: https://calomel.org/badblocks_wipe.html
---

badblocks 既可用来检测磁盘是否具有坏块（bad blocks），也能破坏性擦除磁盘的数
据。它来自 e2fsprogs 程序包。

**检测坏块**

    # badblocks -b 4096 -c 98304 -p 0 -s /dev/sda

该命令对 sda 进行检测，使用块大小为 4096 字节（-b），一次检测 98304
块（-c）。其输出为：

    Checking for bad blocks (read-only test):  27.68% done, 18:21 elapsed. (0/0/0 errors)

**擦除数据**

    # badblocks -b 4096 -c 98304 -p 0 -w -s /dev/sda

追加 -w 选项可以将 sda 上的数据擦除掉。
