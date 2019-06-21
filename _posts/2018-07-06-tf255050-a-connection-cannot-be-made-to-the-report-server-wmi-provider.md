---
layout: post
title: TF255050: A connection cannot be made to the Report Server WMI provider
date: 2018-07-06 15:51
author: venhow
comments: true
categories: [IT资讯]
---
当配置TFS2018时候出现此错误，SQL安装在同一台：

<hr />

TF255050: A connection cannot be made to the Report Server WMI provider. Verify the following:
1. You have entered the correct name for the server, including the instance name.
2. The Windows Management Instrumentation service is running on tfsssrs.
3. The service is not blocked by Windows Firewall.
4. You have the required permissions to connect.
Details:
The RPC server is unavailable. (Exception from HRESULT: 0x800706BA)

<hr />

第一：Reporting Service Instance填写：计算机名\ReportServer实例名；

第二：在Report Server Configuration Manager配置好Service Acount、Web Service URL和Web Portal URL，点击Apply起作用。
