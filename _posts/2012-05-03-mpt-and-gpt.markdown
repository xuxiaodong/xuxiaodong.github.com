---
layout: post
title: MSDOS 分区表与 GUID 分区表（GPT）
date: 2012-05-03 22:11
post-link: http://www.sysresccd.org/Sysresccd-Partitioning-EN-The-new-GPT-disk-layout
---

时至今日，MSDOS 分区表仅支持最多 4 个主分区及无法寻址超过 2TB
空间的硬伤愈加显得突出了。好在我们还有新的选择——GPT，即 GUID 分区表。

GPT 具有如下优势：

* 能够寻址大于 2TB 的空间
* 可以拥有多于 4 个主分区
* 更加健壮
* 支持广泛的分区类型

目前，在 Linux 下使用 GPT 的条件包括：内核要支持 GPT，分区工具 gdisk，以及
GRUB2（GRUB 0.97 需打补丁）用于引导。
