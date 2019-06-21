---
layout: post
title: Local changes to the following would be overwritten by merge
date: 2019-06-04 11:02
author: venhow
comments: true
categories: [IT资讯]
---
git pull错误：

Your local changes to the following files would be overwritten by merge
error: Your local changes to the following files would be overwritten by merge:

xxx文件

Please, commit your changes or stash them before you can merge.

解决办法：

<ol>
    <li>如果希望保留生产服务器上所做的改动，仅仅并入新配置项, 方法如下:
git stash
git pull
git stash pop
然后可以使用git diff -w +文件名 来确认代码自动合并的情况.</li>
    <li>反过来,如果希望用服务器代码库中的文件完全覆盖本地工作版本，方法如下:
git reset --hard
git pull       其中git reset是针对版本,如果想针对文件回退本地修改，使用：
git checkout HEAD file/to/restore</li>
    <li>error: Untracked working tree file 'xxx文件' would be overwritten by merge.
需要执行下面的命令才能修复：
git reset --hard HEAD
git clean -f -d
git pull</li>
</ol>
