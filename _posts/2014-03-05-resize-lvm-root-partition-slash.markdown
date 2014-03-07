---
layout: post
title: 增大 LVM root 分区空间
date: 2014-03-05 14:20
post-link:
---

最近发现我的 Debian root 分区已经占满了，于是打算给它
增加一些新的空间。

因为我使用了 LVM，所以即便是 root 分区，也可以直接为
其扩容，不用 umount，也不用 reboot，真的是十分方便。

首先，利用 `lvdisplay` 可以看到目前逻辑卷的一些信息：

    --- Logical volume ---
    LV Path                /dev/toy/root
    LV Name                root
    VG Name                toy
    LV UUID                wCBCHD-Ddrg-2tev-3xHV-ZXHI-tYB3-R2fhuu
    LV Write Access        read/write
    LV Creation host, time toy, 2013-06-13 11:25:53 +0800
    LV Status              available
    # open                 1
    LV Size                9.31 GiB
    Current LE             2384
    Segments               1
    Allocation             inherit
    Read ahead sectors     auto
    - currently set to     256
    Block device           254:0

接着，使用 `lvextend -L+7G /dev/toy/root -v` 来给 root 分区增加
7G。

    Finding volume group toy
    Archiving volume group "toy" metadata (seqno 5).
    Extending logical volume root to 16.31 GiB
    Found volume group "toy"
    Found volume group "toy"
    Loading toy-root table (254:0)
    Suspending toy-root (254:0) with device flush
    Found volume group "toy"
    Resuming toy-root (254:0)
    Creating volume group backup "/etc/lvm/backup/toy" (seqno 6).
    Logical volume root successfully resized

最后，通过 `resize2fs /dev/toy/root` 将文件系统也进行扩容。
我的 root 分区的文件系统为 ext4，需要注意的是，目前的 Linux
内核可能对某些文件系统不支持这种 on-line 的调整方式。所以在动手
前先做好功课就显得很重要了。

    resize2fs 1.42.9 (28-Dec-2013)
    Filesystem at /dev/toy/root is mounted on /; on-line resizing required
    old_desc_blocks = 1, new_desc_blocks = 2
    The filesystem on /dev/toy/root is now 4276224 blocks long.

再用 `df -Th` 看一下，发现 root 分区的空间已经增大了。

    Filesystem           Type      Size  Used Avail Use% Mounted on
    /dev/mapper/toy-root ext4       16G  7.7G  7.6G  51% /
    udev                 devtmpfs   10M     0   10M   0% /dev
    tmpfs                tmpfs     402M  308K  402M   1% /run
    tmpfs                tmpfs     5.0M     0  5.0M   0% /run/lock
    tmpfs                tmpfs     804M   68K  804M   1% /run/shm
    /dev/sda1            ext2      228M   44M  172M  21% /boot
    /dev/mapper/toy-home ext4      442G  172G  248G  42% /home
