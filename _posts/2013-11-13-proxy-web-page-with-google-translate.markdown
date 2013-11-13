---
layout: post
title: 利用 Google Translate 访问被禁网页
date: 2013-11-13 17:17
post-link: https://github.com/xuxiaodong/bin/blob/master/proxy-web
---

众所周知，在天朝访问某些网页会出现“连接被重置”的情况。偶然发现利用
Google Translate 可以突破此限制，比如 blogspot.com、wordpress.com、
slideshare.net 等。

为了方便与 Firefox 配合使用，我写了一个简单的 Shell 脚本，其用法为：

    % proxy-web <url>

例如：

    % proxy-web http://www.slideshare.net

这样就可以正常访问 Slideshare 了。
