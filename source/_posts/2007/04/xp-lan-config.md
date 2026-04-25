---
layout: post
title: 解决 XP 局域网访问故障 (转)
date: 2007-04-07
categories: windows
tags: ["windows xp", "局域网", "技巧分享", "故障", "设置"]
---

1.开启 guest 账户，确认安装了<span style="color: #ff0000;">NetBIOS</span>协议

2.检查是否拒绝 Guest 用户从网络访问本机
运行`GPEDIT.MSC`打开组策略编辑器，依次选择`计算机配置→Windows设置→安全设置→本地策略→用户权利指派`，双击"<span style="color: #0000ff;">拒绝从网络访问这台计算</span>机"策略，删除里面的"<span style="color: #0000ff;">GUEST</span>"账号。

3.改网络访问模式
打开组策略编辑器，依次选择"<span style="color: #0000ff;">计算机配置→Windows 设置→安全设置→本地策略→安全选项</span>"，双击"<span style="color: #0000ff;">网络访问：本地账号的共享和安全模式</span>"策略，将默认设置"<span style="color: #993366;">仅来宾 - 本地用户以来宾身份验证</span>"，更改为"<span style="color: #0000ff;">经典：本地用户以自己的身份验证</span>"。

我们可能还会遇到另外一个问题，即当用户的口令为空时，即使你做了上述的所有的更改还是不能进行登录，访问还是会被拒绝。这是因为，在系统"<span style="color: #0000ff;">安全选项</span>"中有"<span style="color: #0000ff;">账户：使用空白密码的本地账户只允许进行控制台登录</span>"策略默认是启用的，根据 Windows XP 安全策略中拒绝优先的原则，密码为空的用户通过网络访问使用 Windows XP 的计算机时便会被禁止。我们只要将这个策略停用即可解决问题。在安全选项中，找到"<span style="color: #0000ff;">使用空白密码的本地账户只允许进行控制台登录</span>"项，停用就可以，否 则即使开了 guest 并改成经典模式还是不能登录。经过以上的更改基本就可以访问了，你可以尝试选择一种适合你的方法。下面在再补充点其它可能会遇到的问 题。

5.关于用网络邻居访问不响应或者反应慢的问题
在 WinXP 和 Win2000 中浏览网上邻居时系统默认会延迟 30 秒，Windows 将使用这段时间去搜寻远程计算机是否有指定的计划任务（甚至有可 能到 Internet 中搜寻）。如果搜寻时网络时没有反应便会陷入无限制的等待，那么 10 多分钟的延迟甚至报错就不足为奇了。下面是具体的解决方法。

A.关掉 WinXP 的计划任务服务（Task Scheduler）
可以到"控制面板/管理工具/服务"中打开"Task Scheduler"的属性对话框，单击"停止"按钮停止该项服务，再将启动类型设为"手动"，这样下次启动时便不会自动启动该项服务了。

B.删除注册表中的两个子键
到注册表中找到主键"<span style="color: #0000ff;">HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Explorer\\RemoteComputer\\NameSpace</span>"
删除下面的两个子健：<span style="color: #0000ff;">{2227A280-3AEA-1069-A2DE-08002B30309D}和{D6277990-4C6A-11CF-87- 00AA0060F5BF}</span>。

其中，第一个子健决定网上邻居是否要搜索网上的打印机（甚至要到 Internet 中去搜寻），如果网络中没有共享的打印机便可删除此键。第二个子健则决定是否需要查找指定的计划任务，这是网上邻居很慢的罪魁祸首，必须将此子健删除。

附上一个可以快速进行局域网设置的小软件： [**局域网共享设置工具**
](http://cid-6abece639ad907b9.skydrive.live.com/self.aspx/public/%e5%b1%80%e5%9f%9f%e7%bd%91%e5%85%b1%e4%ba%ab%e8%ae%be%e7%bd%ae%e5%b7%a5%e5%85%b7.rar)