---
layout: post
title: 快速查询语言 API
date: 2014-03-11 16:28
post-link: https://github.com/xuxiaodong/bin/blob/master/search-api
---

由 Thibaut Courouble 所创建的 [DevDocs][d] 的确是相当不错的工具，
它将 CSS、HTML、JavaScript、PHP、Python、Ruby 等各种 API 文档整
合在一起，并提供统一的搜索接口，极大的方便了编写代码的程序员朋友。

为了便于从命令行下查询，我编写了 `search-api` 这个脚本。该脚本
支持如下两种方式来进行查询：

1. `search-api <keyword>`：这将查询以 keyword 作为关键字的内容。

2. `search-api <language> <keyword>`：针对特定语言进行查询。

例如，在 Vim 中我执行 `:!search-api js replace` 将查询 JavaScript
中 replace 的用法。脚本会调用 Firefox 打开一个窗口来展示查询的结果。

[d]: http://devdocs.io/
