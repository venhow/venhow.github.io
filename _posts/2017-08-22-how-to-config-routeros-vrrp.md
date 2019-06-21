---
layout: post
title: How to config RouterOS VRRP
date: 2017-08-22 09:53
author: venhow
comments: true
categories: [IT资讯]
---
这次把SaaS机房部署为ROS的高可用性。

Mikrotik官网有一个配置的例子：​<a href="https://wiki.mikrotik.com/wiki/Manual:VRRP-examples">https://wiki.mikrotik.com/wiki/Manual:VRRP-examples</a>，但是这个例子其实不完整。只针对了LAN端的配置，而忽略了WAN端的配置。

也就是说，假如有两个ROS，ROS1为主，LAN口为192.168.1.252；ROS2为辅，LAN口为192.168.1.253；VRRP为192.168.1.254。

ROS前面放置一个二层交换机，但是问题来了，假如是光纤IP，我们有5个可用公网IP，比如10.0.0.33/29，那么问题来了，如果WAN口也配置为VRRP，就浪费了两个公网IP，需要总共3个公网IP；而且另外一个情况是单IP、ADSL拨号网络的情形，这个时候根本就没有3个公网IP去给你使用。

所以理论上，一个完整可靠的ROS高可用性需要WAN口配置一个VRRP，LAN口配置一个VRRP，但是这么做第一浪费了两个公网IP，第二两个VRRP更不好协调。

所以解决办法是，在LAN配置VRRP，在Script里面配置当ROS1为主时，ROS1的WAN口启用，ROS2这个时候为辅，WAN口禁用；当ROS2为主时，WAN口启用，ROS1这个时候为辅，WAN口禁用。
