---
layout: post
title: Windows 7 三个小技巧
date: 2010-01-23
tags: ["windows 7","优化","技巧","技巧分享","软件"]
---

### 1、解决 hosts 无法修改

Hosts 位置：`C:\Windows\System32\drivers\etc\hosts`

跨栏技巧之一就有修改 hosts 文件，可 win 7 默认无法修改该文件，很郁闷。可以不上×网，但不可以不跨栏滴。观察了一下，发现方法很简单，只需将 hosts 文件拷贝至其它任意位置，比如桌面，然后随意修改，再覆盖回原文件就行了。

不明白 Windows 7 这样设计的初衷是什么，能防止恶意修改么？未必吧！

<!--more-->

### 2、右键添加"显示隐藏文件"菜单

我之前的那篇文章：[SuperHidden(XP 右键添加"显示隐藏文件"菜单)](http://www.kisa747.com/superhidden-for-xp.html)，介绍过 XP 下可以为右键添加"显示隐藏文件"菜单，其实该方法同样适用于 Windows 7。

**【下载地址】**：[SuperHidden.7z](https://dl.dropbox.com/u/3633907/download/superhidden.7z)

### 3、Windows live Writer 插入网络图片

> PS:新版的 WLW 已经添加了该功能，所以这个插件已经不必要了。
Win7 下的 WLW 竟无法添加网络图片，只能添加本地图片和自家的 Sky Drive 上的图片，很不爽。不过很快找到解决方法了，也就是安装个插件：InsertWebImageForWin7。

**【下载地址】**：<del datetime="2012-02-26T01:40:43+00:00">InsertWebImageForWin7.7z</del>

安装方法，解压文件到以下位置即可。

`C:\program files\windows live\writer\plugins\`

PS：我的 Win 7 下好多软件都无法正常运行，尤其是我钟爱的旧软件，甚至连旧版本的迅雷都有点问题，就是迅雷自带的那个火狐扩展无法工作，我又不愿使用 flashgot 插件，让我对 Win 7 是进退两难呀。不过上次折腾好了那个测试版的 QQ2009，还算是有点收获。