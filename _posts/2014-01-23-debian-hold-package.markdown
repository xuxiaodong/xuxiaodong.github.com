---
layout: post
title: Debian 下阻止包升级
date: 2014-01-23 09:56
post-link: http://manpages.ubuntu.com/manpages/trusty/en/man8/apt-mark.8.html
---

在执行系统更新时，有时候我想阻止某些个别的包升级，
Debian 下可以使用 `apt-mark` 命令。

**阻止包**

    apt-mark hold <pkg>

比如，阻止升级 Perl，执行 `apt-mark hold perl` 即可。

**取消阻止**

如果不想阻止了，那么可以通过 `apt-mark unhold` 取消：

    apt-mark unhold <pkg>

**显示已阻止的包**

要查看已经被阻止的包，则可以执行：

    apt-mark showhold
