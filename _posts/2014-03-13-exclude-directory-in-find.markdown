---
layout: post
title: find 命令排除目录
date: 2014-03-13 15:57
post-link:
---

在编写 [mkme][m] 这个脚本的时候，我需要使用 `find` 命令来
找出当前目录下的可执行文件，但是要排除 `.git` 目录。查阅
find 的 Manpage 后，发现可以这样子来搞定：

    find . -type f -executable ! -path "./.git/*"

其选项说明如下：

* `.`：在当前目录下查找
* `-type f`：仅查找一般文件
* `-executable`：文件具有可执行权限
* `! -path "./.git/*"`：这里是关键，`!` 的作用是排除其后
  `-path` 所跟的目录

[m]: https://github.com/xuxiaodong/bin/blob/master/mkme
