---
layout: post
title: 找回 git rm -f 删除的文件
date: 2013-11-19 15:14
post-link: http://stackoverflow.com/questions/14475003/recover-files-after-git-rm-rf
---

本想撤销 Git 暂存的文件，没想到执行 `git rm -f` 后这些文件被直接从磁盘上抹掉了。
好在 Git 还给后悔药吃，找回过程为：

先执行 `git fsck` 扫描丢失的文件：

    git fsck --lost-found --unreachable

结果找到了 4 个文件：

    Checking object directories: 100% (256/256), done.
    unreachable blob 24cae55acf8d615751060aee8a573a872cab467d
    unreachable blob 681227313a5f19a582b1203ab497da37804c4b02
    unreachable blob 729e27bb5b240bb5081956fd93debedbd76fb6b6
    unreachable blob 5de3cc6a8348ca08790ac55b6be3b021ceed73d1

然后再用 `git cat-file` 就可以看到文件的内容，如：

    git cat-file -p 24cae55
