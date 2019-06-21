---
layout: post
title: The system administrator has set policies to prevent this installation
date: 2018-04-26 14:29
author: venhow
comments: true
categories: [IT资讯]
---
在加入域的Windows Server安装TabsStudio时出现此错误：The system administrator has set policies to prevent this installation。而是用Administrator身份则没有问题。

域帐号登录，管理员身份运行CMD，定位到安装文件所在目录，运行如下命令：

<pre><code>msiexec /i xxx.msi</code></pre>
