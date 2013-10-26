---
layout: post
title: Vim 使用 hjkl 键的由来
date: 2012-03-18 21:11
post-link: http://www.catonmat.net/blog/why-vim-uses-hjkl-as-arrow-keys/
---

用过 Vim 的朋友想必都知道 hjkl 这四个键的用途就跟方向键一样。既然如此，Vim 为
什么不直接使用方向键，而要另起炉灶选用 hjkl 呢? 有种说法是，当手指在键盘上敲
打时，hjkl 比方向键距离手指更近，自然输入效率就更高。听起来似乎很有道理，其实
Vim 使用 hjkl 的背后另有原因。

根据 Peteris Krumins 的说法，当年 [Bill Joy][b] 在开发 vi 文本编辑器时所
使用的计算机是一个被称为 [ADM-3A][a] 的终端，该终端附带键盘的 hjkl 键本就和方
向键同位一体。这自然不难解释 Bill Joy 为何要选用 hjkl 键了。

Vim 作为 vi 的衍生作品，当然会遵循历史的选择。

[b]: http://en.wikipedia.org/wiki/Bill_Joy
[a]: http://en.wikipedia.org/wiki/ADM-3A
