---
layout: post
title: 我开机自动启动的服务列表
date: 2007-11-27
categories: windows
tags: [windows xp，启动，技巧分享，服务]
---

说明：可以可以运行 `services.msc` 设置服务选项

>windows image acquisition
>
>Windows 图像获取服务，主要包括了 Windows XP 对图像设备的支持以及对图像信息的处理编辑等功能。一些扫描仪、摄像头、数码相机需要使用此服务。
>
>terminal services
>
>终端服务，允许多位用户连接并控制一台机器。另外，如关掉此服务，则"任务管理器"无法显示 用户名。
>
>themes
>
>主题服务，资源占用挺大的，约需 5M 的内存，当然还占用虚拟内存，基本不占用 cpu。如果不想用 xp 的主题大可以关掉
>
>kaspersky anti-virus 6.0
>
>我的卡巴斯基杀毒软件监护进程，没什么可说的。
>
>application management      软件安装服务
>
>event log                              日志服务
>
>telephony                             拔号服务（用不着拔号时可关）
>
>windows installer                  软件安装和御载用的（改为手动，但不要禁用）
>
>workstation                          工程软件 PROE 需要这个服务是开启的（可关）


终极后优化后就成了：

>plug and play        即插即用，也就是插 U 盘等之类的
>
>dhcp client DHCP 的作用是自动分配 IP。如果是自己手动设置的 IP 地址，就可以关掉它了。
>
>dcom server process  launcher       关掉的话，使用微软的 office 将会提示无法注册。
>
>windows management instrumentation(WMI)     为访问大量的 Windows 管理数据和方法的提供了一个统一的机制。
>
>windows audio                                            声音控制功能，关了系统就没有声音了。
>
>remote procedure call (PRC)                                  系统核心服务。