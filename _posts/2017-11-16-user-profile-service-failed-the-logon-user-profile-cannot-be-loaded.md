---
layout: post
title: User Profile Service failed the logon. User profile cannot be loaded.
date: 2017-11-16 15:14
author: venhow
comments: true
categories: [IT资讯]
---
有一台加入了域的计算机，新添加的Administrators成员居然无法登录，提示：

<h1>User Profile Service failed the logon. User profile cannot be loaded.</h1>

第一就想起是否因为两台域控被hack了，新创建的两台域控的问题？但是以前添加的老用户登录正常。

于是google，结果一大堆单系统的win7，win8什么的，都是修改注册表什么的，可是我是新用户，哪里来的注册表信息呢。

好了，知道看到这个：https://social.technet.microsoft.com/Forums/windows/en-US/cd6f6995-a683-49de-af35-329a09b4a6f1/user-profile-service-failed-the-logon-user-profile-cannot-be-loaded?forum=w7itproinstall&amp;prof=required

神了，只需要修改C盘users目录里面的Default folder权限即可，勾选Replace all child object permission with inheritable permissions from this object。
