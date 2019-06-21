---
layout: post
title: OpenWRT for x86
date: 2019-01-16 15:34
author: venhow
comments: true
categories: [IT资讯]
---
<ol>
    <li>下载：<a href="https://downloads.openwrt.org/releases/18.06.1/targets/x86/64/openwrt-18.06.1-x86-64-combined-ext4.img.gz">https://downloads.openwrt.org/releases/18.06.1/targets/x86/64/openwrt-18.06.1-x86-64-combined-ext4.img.gz</a></li>
    <li>Ubuntu下面把img转换为vmdk，sudo apt-get install qemu-utils -y
sudo qemu-img convert -f raw -O vmdk xxx.img  xxx.vmdk</li>
    <li>使用VM创建一个双网卡的虚拟机，分配256M内存1个CPU，使用刚才转换的vmdk作为启动硬盘</li>
</ol>

&nbsp;

CP: https://cokebar.info/archives/2444
