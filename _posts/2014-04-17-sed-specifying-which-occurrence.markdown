---
layout: post
title: sed 中通过 /n 指定匹配出现次数
date: 2014-04-17 14:36
post-link: http://www.grymoire.com/Unix/Sed.html#uh-8
---

在 sed 中，通过 `/n` (n 代表数字) 可以指定匹配出现的次数。

例 1：

    sed 's/[a-zA-Z]* //2' <old >new

这里的 `/2` 将匹配到的第二个单词删除。

例 2：

    sed 's/./&:/80' <file >new

这里的 `/80` 在第 80 个字符后面添加一个 `:`。

例 3：

    sed 's/[a-zA-Z]* /DELETED /2g' <old >new

与 `/g` 连用，将匹配到的第二个、第三个……替换成 DELETED。

`/n` 中的 n 可以取 1 ~ 512 中的数。

注意，`/n` 与 `\n` 的区别，后者指引用捕获匹配的内容，n 取 1 ~ 9。
