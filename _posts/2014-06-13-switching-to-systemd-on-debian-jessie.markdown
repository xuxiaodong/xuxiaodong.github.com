---
layout: post
title: Debian Jessie 切换 systemd
date: 2014-06-13 12:56
post-link: https://major.io/2014/05/20/switching-to-systemd-on-debian-jessie/
---

目前，许多 Linux 发行版都相继切换到了 systemd。在 Debian Jessie
中，要从 SysVinit 切换到 systemd，可执行如下命令：

    apt-get update
    apt-get install systemd systemd-sysv
    reboot

在切换前，注意查看系统[是否满足需求][r]。

[r]: https://wiki.debian.org/systemd
