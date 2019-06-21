---
layout: post
title: SCCM 2016: Distribution manager failed to connect to the distribution point
date: 2018-06-07 16:20
author: venhow
comments: true
categories: [IT资讯]
---
SCCM 2016的一个粪坑：当配置Operating System Images分发的时候，出现Failed信息：distribution manager failed to connect to the distribution point。

解决办法：安装<em>IS 6 WMI Compatibility service。</em>
