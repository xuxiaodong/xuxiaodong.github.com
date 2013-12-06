---
layout: post
title: 使用 Nmap 诊断网络端口
date: 2013-12-06 15:42
post-link: http://nmap.org/
---

在拿 Tinyproxy 架设 HTTP 代理服务后，发现并不能正常工作。Tinyproxy 默认使用 
8888 端口号，于是用 Nmap 诊断如下：

    nmap -p 8888 216.108.229.6

    Starting Nmap 6.40 ( http://nmap.org ) at 2013-12-06 15:18 CST
    Nmap scan report for lasvegas-nv-datacenter.com (216.108.229.6)
    Host is up (0.22s latency).
    PORT     STATE    SERVICE
    8888/tcp filtered sun-answerbook

    Nmap done: 1 IP address (1 host up) scanned in 3.88 seconds

从 `STATE` 列可以看出该端口已被过滤掉，即有防火墙阻挡。知道了原因，便可用
`iptables` 解决：

    iptables -I INPUT -p tcp --dport 8888 -j ACCEPT

再次用 Nmap 查看结果为：

    PORT     STATE SERVICE
    8888/tcp open  sun-answerbook

于此问题得到解决。
