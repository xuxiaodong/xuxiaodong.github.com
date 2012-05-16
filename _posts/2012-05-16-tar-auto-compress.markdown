---
layout: post
title: tar -a, --auto-compress
date: 2012-05-16 22:08
post-link: http://petereisentraut.blogspot.com/2012/05/time-to-retrain-fingers.html
---

以往在使用 tar 解包时，我总是会根据不同的存档格式去选择合适的选项。比如，要提
取 .tar.gz 就用 zxvf，而 .tar.bz2 则用 jxvf。事实上，tar 能够根据存档的后缀自
动选用相应的压缩程序。只需使用如下选项即可：

    -a, --auto-compress

仅管此选项已存在了 4 年之久，但看来似乎仍然鲜为人知。
