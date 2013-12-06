---
layout: post
title: 'post2wp: 发布 Post 到 WordPress'
date: 2013-11-20 14:06
post-link: https://github.com/xuxiaodong/bin/blob/master/post2wp
---

以前我用 Perl 写了一个 `blogpost` 用来从命令行发布 Post 到 WordPress。后来，随
着对 WordPress 的升级，`blogpost` 就不好使了。直到最近，看了一点 Python，于是
打算重写一个。所以现在有了 `post2wp`。

`post2wp` 目前仅支持发布新的 Post 及编辑旧的 Post。

首先，准备 WordPress 的帐号信息，在 `~/.post2wprc` 中添加如下内容：

    [post2wp]
    url = https://linuxtoy.org/xmlrpc.php
    username = <user>
    password = <pass>

之后，要发布新 Post 的话，可以执行：

    post2wp -t <title> -f <content>

这两个选项是必需的。此外，也可以跟上 slug、catetory、status 等选项：

    post2wp -t <title> -l <slug> -c <category> -f <content> -s <status>

其中：

* `-t` 指定标题
* `-l` 指定 slug，就是 Post 网址中显示的那部分
* `-c` 指定类别，可同时指定多个类别，只需空格分隔即可
* `-f` 指定要 Post 的文件，Markdown 格式就很好，WordPress 支持的 HTML 也行
* `-s` 指定发布状态，默认为草稿，设为 `publish` 的话就直接发布

编辑 Post 则可以使用：

    post2wp -t <title> -f <content> -i <post_id>

话说在 Python 中不用 Perl 的那些符号，看起来的确要干净不少。Python 简单、一致
的设计哲学确实不错。
