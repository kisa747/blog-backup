---
layout: post
title: deepin xp lite V5.7 两点小设置
date: 2007-11-25
tags: ["deepin","windows xp","技巧分享","设置"]
---

deepin xp lite V5.7 由于精简了许多 xp 的组件，加上为了最大限度地提高系统的性能，系统安装后往往设置优化模式为"最精简优化模式"，但这样会有些服务默认未打开，给使用带来些许不便。

1、"任务管理器"无法显示用户名

运行 services.msc，找到 Terminal Services，启动它，并把启动方式改为"自动"

<!--more-->

2，任务栏声音控制按钮不见了，而且连带本地连接和删除硬件的按钮也不见了，即使在"控制面板"－"声音和音频设备"里勾选 "将音量图标放入任务栏"，重启后任务栏里它的图标仍会消失。这时就需要设置一下注册表，为简单，直接在命令提示符下执行以下命令就 OK 了！

`reg add HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Run /v Systray /d "c:\\windows\\system32\\Systray.exe"`

或是点击直接下载批处理程序   ** [添加开机打开音量图标.rar](http://cid-6abece639ad907b9.skydrive.live.com/self.aspx/public/%e6%b7%bb%e5%8a%a0%e5%bc%80%e6%9c%ba%e6%89%93%e5%bc%80%e9%9f%b3%e9%87%8f%e5%9b%be%e6%a0%87.rar)**