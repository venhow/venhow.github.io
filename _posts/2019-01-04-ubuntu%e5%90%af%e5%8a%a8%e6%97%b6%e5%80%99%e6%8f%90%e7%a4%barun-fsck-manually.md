---
layout: post
title: Ubuntu启动时候提示RUN fsck MANUALLY
date: 2019-01-04 11:17
author: venhow
comments: true
categories: [IT资讯]
---
fsck from util-linux 2.26.2
/dev/sda1 contains a file system with errors, check forced.
/dev/sda1: Inodes that were part of a corrupted orphan linked list found.

/dev/sda6: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
(i.e., without -a or -p options)
fsck exited with status code 4
The root filesystem on /dev/sda1 requires a manual fsck

Busybox v1.22.1 (Ubuntu 1:1.22.0-15ubuntu1) built in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _

这个时候呢，输入fsck /dev/sda1 -fy回车，修复完成后重启即可。是磁盘有点文件错误，就像Windows的开机磁盘扫描。
