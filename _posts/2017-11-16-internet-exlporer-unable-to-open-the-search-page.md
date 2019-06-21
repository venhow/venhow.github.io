---
layout: post
title: Internet Exlporer: Unable to open the search page
date: 2017-11-16 15:14
author: venhow
comments: true
categories: [IT资讯]
---
公司新员工的一台笔记本，安装的是Windows10企业版，来公司之后加入了域。发现IE打不开任何网页，而其他浏览器入Chrome、Edge都正常。

寻思，难道是360卫士搞鬼？因为我最讨厌360的产品，安装了它们系统就会经常无缘无故的问题频频发生。

于是升级系统到最新，删除用户配置文件，退域再加域，问题依旧。

只好试试万能命令：CMD（管理员模式）运行netsh winsock reset，重启okay。
