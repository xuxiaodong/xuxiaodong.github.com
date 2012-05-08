---
layout: post
title: Ebuild 文件的命名规范
date: 2012-05-09 01:10
post-link: http://www.gentoo.org/proj/en/devrel/handbook/handbook.xml?part=2&chap=1
---

最近因为要做一个名为 gem2ebuild 的小项目，于是温习了 Gentoo 相关文档，了解
Ebuild 文件的命名规范。

一个典型的 Ebuild 文件如下所示：

    foobar-1.2.0_beta3-r4.ebuild

抽象一下就是：

    pkg-ver{_suf{#}}{-r#}.ebuild

其中，

1. pkg 为包名，例子中为 foobar
2. ver 为版本号，例子中为 1.2.0
3. suf 为后缀名，是可选部分，例子中为 beta3
4. r 为修订号，也是可选部分，例子中为 r4

除了 2、3 部分采用 _ 连接外，其余部分通过 - 连接。
