---
layout: post
title: Ubuntu修改sudoers文件出错/etc/sudoers: syntax error
date: 2019-06-19 18:07
author: venhow
comments: true
categories: [IT资讯]
---
Ubuntu修改sudoers文件出错/etc/sudoers: syntax error：

<blockquote>/etc/sudoers: syntax error near line 21 &lt;&lt;&lt;

sudo: parse error in /etc/sudoers near line 21

sudo: no valid sudoers sources found, quitting

<span style="background-color:#ffffff;color:var(--color-text);">sudo: unable to initialize policy plugin</span></blockquote>

21行应该是新增了用户权限，但是写错了某个字母导致的。这个时候用vi、nano；gedit等打开都是提示这个错误。

跳转到etc目录，运行命令：pkexec visudo，再次进行编辑，修正字母错误，保存okay。
