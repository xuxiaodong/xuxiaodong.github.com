---
layout: post
title: 在 Godaddy 中添加泛域名解析
date: 2013-12-31 10:53
post-link:
---

最近因为玩各种有趣的东东，所以为 <linuxtoy.org> 添加了不少
子域。为了避免频繁的添加过程，于是想到用泛域名解析来解决。

在 Godaddy 中添加泛域名解析十分简单，只要追加一条 `A` 记录
，并分别将 Host 设为 `*`、Points To 设为目标 IP 地址即可。

Godaddy 的 DNS 设置生效时间非常快，几乎是设置完成后便可以
使用。
