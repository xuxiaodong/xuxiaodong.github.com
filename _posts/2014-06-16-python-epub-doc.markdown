---
layout: post
title: 将 Python 文档打包成 ePub 格式
date: 2014-06-16 11:23
post-link: https://github.com/xuxiaodong/pydoc-epub
---

虽然 Python 官方文档针对最新版本提供有 ePub 格式，但是这个
包包含所有的内容，在我的手机上打开十分慢。另外，Python 2.x
系列并不提供 ePub 格式。于是，我编写了 [pydocepub][p] 这个
脚本用来将 Python 文档自动打包成 ePub 格式。

要使用 pydocepub，首先需要安装 Mercurial 和 [Sphinx][s]，
在 Debian 下可执行：

    apt-get install mercurial sphinx-doc

接着，从 GitHub 克隆该脚本：

    git clone https://github.com/xuxiaodong/pydoc-epub.git

比如，要打包 Python 2.7.7 的教程：

    ./pydocepub 2.7.7 tutorial

打包完成后的 ePub 文件可在以下目录中找到：

    2.7.7/tutorial/build/epub

[p]: https://github.com/xuxiaodong/pydoc-epub
[s]: http://sphinx-doc.org/
