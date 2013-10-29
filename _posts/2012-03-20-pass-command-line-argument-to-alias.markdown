---
layout: post
title: 给 alias 添加命令行参数
date: 2012-03-20 23:10
post-link: 
---

昨天在定义 alias 时，有想到用命令行参数的需求。但通过查证文档的结果是，alias
根本就不支持传递命令行参数。不过，我们可以变通的解决这个问题，即定义函数。

下例截取自我为方便使用 Octopress 撰写 Blog 而定义的 alias:

    alias pn='new() { bundle exec rake new_post\["$1"\] }; new'

这里，我通过定义 new() 函数来将 $1 参数传递给别名 pn。现在只需执行:

    pn 'post title'

就可以新建一篇 post 了。

另一个用于提交 source 的 alias:

    alias pc='commit() { git add .; git commit -m "$1"; git push origin source }; commit'
