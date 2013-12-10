---
layout: post
title: 通过 lshw 找出 SSD
date: 2013-12-10 16:16
post-link:
---

一台服务器包括 4 块盘，其中有一块是 SSD，其余三块是普通磁盘。
现在想找出哪块盘是 SSD。在 Linux 下，使用 lshw 即可。

    lshw -c disk | grep -C 9 -i ssd

执行该命令后，输出结果为：

    *-disk:0
        description: ATA Disk
        product: Samsung SSD 840
        physical id: 0.3.0
        bus info: scsi@0:0.3.0
        logical name: /dev/sda
        version: BB0Q
        serial: S1D9NEAD914775T
        size: 931GiB (1TB)
        capacity: 931GiB (1TB)
        capabilities: 15000rpm partitioned partitioned:dos
        configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=000667d7

现在，我们知道 `sda` 就是 SSD。
