---
layout: post
title: 正确计算剩余内存
date: 2012-03-31 20:39
post-link: http://blog.scoutapp.com/articles/2010/10/06/determining-free-memory-on-linux
---

在 Linux 中，当我们需要了解系统的内存使用情况时，通常会执行 free
命令，这将产生类似下面的输出：

                 total       used       free     shared    buffers     cached
    Mem:          2965       1869       1096          0        222        968
    -/+ buffers/cache:        678       2287
    Swap:         2047          0       2047

从该输出结果的 total 列，我们可以看到系统总共有 2965M 内存。那么，free 列下的
1096M 是否就是实际的剩余内存呢？要回答这个问题，首先我们需明白什么是内存缓存。

由于从磁盘上读取数据远慢于直接从内存访问数据，所以 Linux 将在内存中划出一个 
buffer cache 区。这样可以尽量高效的读取数据。buffer cache 能够自动收缩或扩充，
以适应程序的内存需要。

综上，实际的剩余内存应为

    free (1096) + buffers (222) + cached (968) = 2286M
