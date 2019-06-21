---
layout: post
title: Ubuntu 安装Shadowsocks和ShadowsocksR
date: 2019-01-08 10:30
author: venhow
comments: true
categories: [IT资讯]
---
<ul>
    <li>系统升级，sudo apt update，sudo apt upgrade</li>
    <li>安装Python和pip，sudo apt install Python-pip</li>
    <li>安装ss，sudo pip3 install https://github.com/shadowsocks/shadowsocks/archive/master.zip，查看版本 sudo ssserver --version</li>
    <li>创建配置文件，查看ip地址，ifconfig，sudo mkdir /etc/shadowsocks，sudo nano /etc/shadowsocks/config.json，port可以是443，然后按Ctrl + O保存文件，Ctrl + X退出</li>
</ul>

<pre>{
"server":"::",
"server_port":8388,
"local_address": "127.0.0.1",
"local_port":1080,
"password":"mypassword",
"timeout":300,
"method":"aes-256-cfb",
"fast_open": false
}</pre>

<ul>
    <li>查看ss是否运行正常，ssserver -c /etc/shadowsocks/config.json，客户端也配置好，就可以看到连接状态了</li>
    <li>新建ss管理文件，sudo nano /etc/systemd/system/shadowsocks-server.service，拷贝粘贴如下内容</li>
</ul>

<pre>[Unit]
Description=Shadowsocks Server
After=network.target

[Service]
ExecStart=/usr/local/bin/ssserver -c /etc/shadowsocks/config.json
Restart=on-abort

[Install]
WantedBy=multi-user.target</pre>

<ul>
    <li>启动ss：sudo systemctl start shadowsocks-server</li>
    <li>开机启动ss：sudo systemctl enable shadowsocks-server</li>
</ul>

&nbsp;

参考：<a href="https://www.polarxiong.com/archives/Ubuntu-16-04%E4%B8%8BShadowsocks%E6%9C%8D%E5%8A%A1%E5%99%A8%E7%AB%AF%E5%AE%89%E8%A3%85%E5%8F%8A%E4%BC%98%E5%8C%96.html">https://www.polarxiong.com/archives/Ubuntu-16-04%E4%B8%8BShadowsocks%E6%9C%8D%E5%8A%A1%E5%99%A8%E7%AB%AF%E5%AE%89%E8%A3%85%E5%8F%8A%E4%BC%98%E5%8C%96.html</a>

<a href="https://github.com/iMeiji/shadowsocks_install/wiki/shadowsocksR-%E4%B8%80%E9%94%AE%E5%AE%89%E8%A3%85">https://github.com/iMeiji/shadowsocks_install/wiki/shadowsocksR-%E4%B8%80%E9%94%AE%E5%AE%89%E8%A3%85</a>

<a href="http://blog.seanchao.xyz/2018/02/ShadowsocksR-Server-Deployment-Guide">http://blog.seanchao.xyz/2018/02/ShadowsocksR-Server-Deployment-Guide</a>
