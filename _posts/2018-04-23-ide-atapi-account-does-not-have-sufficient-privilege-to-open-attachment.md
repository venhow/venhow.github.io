---
layout: post
title: IDE/ATAPI ACCOUNT DOES NOT HAVE SUFFICIENT PRIVILEGE TO OPEN ATTACHMENT
date: 2018-04-23 11:16
author: venhow
comments: true
categories: [IT资讯]
---
<p class="textborder"><b>An error occurred while attempting to start the selected virtual machine(s).</b></p>

<pre>'TestVM' failed to start.
Microsoft Emulated IDE Controller (Instance ID
{83F8638B-8DCA-4152-9EDA-2CA8B33039B4}): Failed to Power on with Error 'General
access denied error'
IDE/ATAPI Account does not have sufficient privilege to open attachment
'D:VMTestVMTestVM.vhd. Error: ‘General access denied error'
Account does not have sufficient privilege to open attachment
'D:VMTestVMTestVM.vhd. Error: ‘General access denied error'</pre>

微软说了一堆，要如何如何，还需要命令行什么的。其实呢，哈哈。

https://support.microsoft.com/en-us/help/2249906/hyper-v-virtual-machine-may-not-start-and-you-receive-a-general-access ，这是微软的方案，CMD运行一串命令：icacls "D:\HyperV\Virtual Hard Disks\SCCM2.vhdx" /grant "NT VIRTUAL MACHINE\8093F3E5-E40C-4651-9B6F-B946AA54CEC0":(F) 。

实际上，也可以简单的可视化操作如下：

<ol>
    <li>Open Hyper-V manager, Right click settings of the virtual machine</li>
    <li>Find the Virtual Hard Drive and choose “Remove”.</li>
    <li>Re-add the same Virtual Hard Drive back to the machine.</li>
    <li>Now start the VM again, it should boot successfully.</li>
</ol>
