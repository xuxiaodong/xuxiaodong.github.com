---
layout: post
title: Asus EeePC X101CH 双显屏设置
date: 2014-03-19 11:06
post-link: https://wiki.archlinux.org/index.php/Poulsbo
---

最近用 `xrandr` 为这台 Asus EeePC X101CH 设置双显示屏时，遇到
了下列错误:

    xrandr: Failed to get size of gamma for output default
    Screen 0: minimum 1024 x 600, current 1024 x 600, maximum 1024 x 600
    default connected 1024x600+0+0 0mm x 0mm
    1024x600        0.0* 

从 xrandr 的输出信息并不能看到 VGA、DVI 等其他输出接口。实事
上，这些接口是存在的。经过查证，在安装 xf86-video-modesetting 包，
并创建 `/usr/share/X11/xorg.conf.d/00-modesetting.conf` 文件后，
`xrandr` 执行正常。

00-modesetting.conf 的内容如下：

    Section "Device"
        Identifier "gma500_gfx"
        Driver     "modesetting"
        Option     "SWCursor"       "ON" 
    EndSection

连上外接显示器，再执行：

    % xrandr --output VGA-0 --auto

屏幕输出正常显示。
