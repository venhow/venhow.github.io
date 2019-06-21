---
layout: post
title: Cisco CP 启动后提示Your security settings have blocked an application with an expired or not-yet-valid certificate from running
date: 2018-06-21 14:13
author: venhow
comments: true
categories: [IT资讯]
---
安装好Java SE和Cisco CP，启动Cisco CP时候提示：<em>Your security settings have blocked an application</em> with an<em>expired or not</em>-<em>yet</em>-<em>valid certificate</em> from running。

一：Java Control Pannel - Security，添加Exception Site List；

二：Java Control Pannel - Advanced，勾选Show site certificate from server even if it is valid。
