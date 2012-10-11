---
layout: post
title: 读取文件中间部分内容
date: 2012-10-11 11:05
post-link:
---

我们知道，head 可以读取文件开头，而 tail 能够读取文件结尾；将 head 与 tail
组合使用则能读取文件的中间部分的内容。

假如我们想从文件的第 10 行开始读取 15 行的内容，则可以执行：

    % cat file | head -n 24 | tail -n 15
