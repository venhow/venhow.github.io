---
layout: post
title: VMware产品线简介
date: 2018-06-25 15:59
author: venhow
comments: true
categories: [IT资讯]
---
VMware Workstation
主条目：VMware Workstation
VMware Workstation是VMware公司销售的商业软件产品之一。该工作站软件包含一个用于英特尔x86兼容电脑的虚拟机套装，其允许用户同时创建和运行多个x86虚拟机。每个虚拟机可以运行其安装的操作系统，如（但不限于）Windows、Linux、BSD变生版本。用简单术语来描述就是，VMware Workstation允许一台真实的电脑在一个操作系统中同时打开并运行数个操作系统，其它VMware产品帮助在多个宿主电脑之间管理或移植VMware虚拟机。免费版本为VMware Workstation Player。

VMware官方网站提供多个经过预先配置的操作系统和应用程序的免费虚拟盘映像，这之中有不少是社会募捐的。

VMware Fusion
VMware Fusion是VMware面向Mac电脑推出的一款虚拟机软件。

VMware Server
2006年2月6日，VMware发布了VMware Server产品的1.0版本，替换原先的VMware GSX Server[8]。VMware服务器可以创建、编辑、运行虚拟机。除了具有可以运行由其它VMware产品创建的虚拟机的功能外，它还可运行由微软Virtual PC产品创建的虚拟机。VMware将VMware服务器产品作为可免费获得的产品，这是因为希望用户们最终能选择升级至VMware ESX服务器产品。

VMware不正式支持运行于Windows XP或专业版Windows 2000上的VMware服务器产品，这不同于VMware工作站产品。然而，已有用户报告在Windows XP专业版下成功安装并提供VMware服务器功能的例子（但有个别限制要求）[9]。VMware提供一个受支持的宿主操作系统的清单[10]。

2010年1月，VMware宣布2011年6月30日结束对VMware Server的支持。

VMware ESX服务器
ESX服务器使用了派生自史丹佛大学开发的SimOS核心，该核心在硬件初始化后替换原开机的Linux内核。ESX服务器2.x的服务控制平台（亦称为“COS”或“vmnix”）是基于Red Hat Linux 7.2的。ESX服务器3.0的服务控制平台源自一个Red Hat Linux 7.2的经过修改的版本——它是作为一个用来加载vmkernel的引导加载程序运行的，并提供了各种管理界面（如CLI、浏览器界面MUI、远程控制台）。该虚拟化系统管理的方式提供了更少的管理开销以及更好的控制和为虚拟机分配资源时能达到的粒度（指精细的程度）；这也增加了安全性，从而使VMware ESX成为一种企业级产品。

VMware ESXi服务器
Vmware ESXi是Vmware vSphere 4.1版本开始提供的服务器系统。相比Vmware ESX，ESXi剔除了基于Red Hat Linux的服务控制平台，使VMware代理可以直接在VMkernel上运行。由于脱离对基于Linux的控制台操作系统的依赖，整个软件平台的尺寸由ESX的约2GB缩减至不到150MB，并消除了底层Linux系统可能带来的安全性和稳定性隐患，而获得授权的第三方模块也可在VMkernel上运行。ESXi同时使用了新的管理控制台PowerCLI。

从Vmware vSphere 5.0版本开始，Vmware不再提供ESX服务器产品，ESXi成为Vmware产品线中唯一一款服务器平台产品。

VMware vSphere
VMware vSphere，原称为VMware Infrastructure，是一整套虚拟化应用产品，它包含VMware ESX Server 4、VMware Virtual Center 4.0、最高支持8路的虚拟对称多处理器（Virtual SMP）和VMotion，以及例如VMware HA、VMware DRS和VMware统一备份服务等分布式服务。VMware国际公司在2009年4月发布了VMware vSphere 4。该套装提供六个档次的组合方案

数据中心
VMware国际公司对数据中心应用提供两种主要产品：VMware ESX和VMware服务器（旧称为VMware GSX）。

VMware ESX服务器是作为VMware用于在数据中心应用中运行企业级应用的旗舰产品。由于ESX是在‘近硬件’层级上加载的，它能使x86的利用效率提高60%到80%。
数据中心亦可使用VMware服务器产品运行，但运行该产品须依赖于宿主环境的基本操作系统；此外，在运行软件的额外层面时也会产生对机器的附加开销。然而VMware服务器产品具有一点超过ESX产品的优势：它支持的设备的规格更多，例如可支持USB连接方式和某些PCI设备。
亦请注意VMware ACE产品。

其它产品
其它三种与ESX协同运行的产品是：虚拟中心（VirtualCenter）、VMotion和P2V（将物理计算机运行环境直接移植为虚拟机的工具）。

虚拟中心可用来监视和管理多个ESX或GSX服务器。
VMotion可用来在服务器之间实现几乎无停滞地移动运行中的虚拟机。
P2V允许用户通过使用映像软件，将一台物理的服务器制作为虚拟机映像，从而创造出一个从物理机到虚拟机的重现。它用虚拟的驱动文件代替了实际的驱动文件，并且在VMware的数据存储中创建出机器空间。

免费产品

VMware Workstation Player 相当于是VMware Workstation 的免费版

下载地址：http://www.vmware.com/go/downloadplayer-cn

VMware Workstation Player 免费版和付费版之间有什么区别？

VMware Workstation Player 可以免费下载，但购买并输入许可证密钥可让用户获得以下额外好处：

在许可后，VMware Workstation Player 可用于商业用途。它经许可后可供员工、培训组织、合同工使用，并且可以转让给合作伙伴或潜在客户。
在许可后，VMware Workstation Player 能够运行由 VMware Fusion Pro 或 VMware Workstation Pro 创建的受限虚拟机。
在许可后，VMware Workstation Player 可更有效地支持数千用户的大规模部署，它包含多种安装选项和自定义配置设置，可用于通过系统配置软件进行无人参与的安装以及隐藏不需要的功能。

VMware Workstation Player 与 VMware Workstation Pro 相比如何？

利用 VMware Workstation Player 可以快速、轻松地创建和运行虚拟机。Workstation Player 的用户界面设计以尽可能易于使用为宗旨。它针对需要运行虚拟机的人员，这些虚拟机通常由 IT 组织、系统管理员、讲师、软件供应商等为他们提供。VMware Workstation Pro 则要高级得多，可提供快照、克隆、与 vSphere 或 vCloud Air 的远程连接、共享虚拟机、高级虚拟机设置等强大功能。Workstation Pro 旨在供专业技术人员使用，如开发人员、质量保障工程师、系统工程师、IT 管理员、技术支持代表、培训师等。“Workstation Pro 与 Workstation Player 比较表”中提供了更多比较详细信息。

VMware Workstation Player 是否可以运行由 VMware Workstation Pro 或 VMware Fusion Pro 创建的受限虚拟机？ 可以。前提是您必须购买 VMware Workstation Player。仅在对 Workstation Player 授予许可后，才激活此功能。

VMware vSphere Hypervisor相当于是VMware vSphere的免费版

关于 安装配置以及客户端 参加 官网地址 https://www.vmware.com/cn/products/vsphere-hypervisor.html

Copy: https://hi-andy.com/index.php/2016/08/05/vmware/
