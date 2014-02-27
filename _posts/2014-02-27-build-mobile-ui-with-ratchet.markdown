---
layout: post
title: 通过 Ratchet 为 Linuxtoy 构建移动界面
date: 2014-02-27 21:07
post-link: https://github.com/twbs/ratchet
---

今天在 HTML5 Weekly 中看到了对 Ratchet 的介绍，它是一个移动
应用构建框架，主要支持使用 HTML、CSS、JavaScript 等技术。鉴
于 Linuxtoy.org 一直缺少一个面向移动终端的界面，于是马上决定
试试 Ratchet。

初步的实现想法是：

1. 使用 jQuery 和 FeedEk 解析 Feed，以便获得内容
2. 接着，使用 Ratchet 来渲染所得到的内容

效果如下，可通过 <http://m.linuxtoy.org> 访问：

![mtoy](/images/mtoy-index.png)

首页显示最新的 10 篇文章。

![mtoy](/images/mtoy-single.png)

文章的具体内容。

通过试用，感觉 Ratchet 还是挺好上手的。有时间不妨再深入
研究下。

实现的源代码可从 <http://git.linuxtoy.org/mtoy/> 得到。
