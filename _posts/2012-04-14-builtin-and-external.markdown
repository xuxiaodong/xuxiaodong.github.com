---
layout: post
title: 避免执行 Shell 内置命令
date: 2012-04-14 15:31
post-link:
---

当外部程序与 Shell 内置命令同名时，在 Shell 中总是会优先执行其内置命令。以
time 为例：

    % which -a time
    time: shell reserved word
    /usr/bin/time

我们想要执行的是 /usr/bin/time，当然可以带绝对路径来执行。除此之外，也可以在
time 前面添加 \（反斜杠）来避免 Shell 执行同名的内置命令。

    % \time
