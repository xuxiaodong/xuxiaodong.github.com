---
layout: post
title: 利用 Synergy 共享鼠标和键盘
date: 2014-03-19 14:46
post-link: http://synergy-foss.org/
---

在办公室工作的时候，如果想要将台式机的鼠标和键盘共享
给笔记本使用，通过 Synergy 是很方便的。

要达到上述目的，首先在台式机和笔记本上都安装 Synergy，
注意保证两边的版本一致，以免出现兼容问题。

**台式机：服务端**

因为我们是打算共享台式机的鼠标和键盘，所以这里将台式
机作为 Synergy 的服务端。同时，在 `/etc/synergy.conf`
中添加下列内容：

    section: screens
        codefun: 
        codetoy: 
    end

    section: links
        codefun:
            left  = codetoy
        codetoy:
            right = codefun
    end

其中，`codetoy` 和 `codefun` 分别为台式机和笔记本的主机
名。`screens` 节定义要使用共享鼠标和键盘的两台机器，也
可以同时定义多台。`links` 节则定义两台机器的屏幕所处的
位置，这里我们将台式机设置在左边，相应地笔记本则在台式机
的右边。除了左右关系，也能定义上下关系。

配置好后，通过以下命令启动 Synergy 的服务端：

    synergys -f -n codetoy

**笔记本：客户端**

客户端无需配置，直接使用如下命令连接服务端即可：

    synergyc -f -n codetoy 192.168.1.58

其中，`192.168.1.58` 为 Synergy 服务端所在机器的 IP。 

现在，当将鼠标指针从台式机的屏幕右边移出时，你会发现它
已经进到笔记本的屏幕了。如果要返回台式机屏幕，则从笔记
本屏幕的左边移出即可。
