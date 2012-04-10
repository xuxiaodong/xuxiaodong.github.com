---
layout: post
title: VPS 升级到 Debian 6.0
date: 2012-04-10 22:36
post-link: http://www.debian.org/releases/stable/i386/release-notes/ch-upgrading.en.html
---

日前，将 [Linuxtoy.org][l] 所在的 VPS (基于 Xen) 升级到了 Debian 6.0，这里记
一笔供以后参考：

更改 sources.list：

    # cd /etc/apt
    # cp sources.list{,.old}
    # vim sources.list
    # :%s/lenny/squeeze/g
    # :x

更新源及 Debian 包密钥：

    # aptitude update
    # aptitude install debian-archive-keyring

升级：

    # aptitude full-upgrade

升级时注意保留 GRUB 旧版本，使用 GRUB 2 在安装时会有问题。

[l]: http://linuxtoy.org
