---
layout: post
title: 轻松体验 Ubuntu 10.04 LTS
date: 2010-04-27
tags: ["grub","linux","ubuntu","windows 7"]
---

![](img/2010/042701.png)Ubuntu 10.04 LTS 再有 2 天就要正式发布了，现在 RC 版已经可用。Ubuntu 10.04 作为一个 LTS 长期支持版本，你是不是早已按奈不住内心的冲动，想体验一把 Ubuntu 10.04。至于我折腾的 Ubuntu 桌面，可以看 → [这里](http://www.kisa747.com/config-wordpress-ubuntu-10-04.html)。

通过昨天介绍的 Windows 7 下使用 Grub4DOS 的方法，我们可以很方便地在 Windows 下体验 Ubuntu，这时 Grub 作为优秀的启动管理器，所有的优点都展现无遗。

<!--more-->

先下载 Ubuntu LiveCD

【下载地址】：[http://releases.ubuntu.com/10.04/](http://releases.ubuntu.com/10.04/)
> PS：*desktop-i386.iso 为 32 位版，*desktop-amd64.iso 为 64 位版。Desktop 版的才是 LiveCD，不要下错了。

### 一、体验 Ubuntu LiveCD

不用刻录 ISO 镜像即可直接体验 LiveCD，跟用光盘启动没什么两样。

1、提取出光盘中 casper 目录下的 vmlinuz 和 initrd.lz 两个文件到任意盘的根目录。比如放到 D:\vmlinuz 和 D:\initrd.lz，原 ISO 光盘镜像文件放到哪里也无所谓。

2、在 menu.lst 里添加以下内容，即可用 Grub 引导 Ubuntu LiveCD。
<pre>title Ubuntu 10.04 LiveCD
    find --set-root --ignore-floppies /vmlinuz
    kernel /vmlinuz boot=casper iso-scan/filename=/ubuntu-10.04-rc-desktop-i386.iso ro quiet splash locale=zh_CN.UTF-8
    initrd /initrd.lz
    boot</pre>
> PS：其中的"ubuntu-10.04-rc-desktop-i386.iso"，必须与你下载的镜像文件名一致。

### 二、体验 Wubi 安装 Ubuntu

用虚拟光驱加载 Ubuntu LiveCD，运行光盘根目录下的 wubi.exe，选择"在 Windows 中安装"，即可 wubi 安装 Ubuntu 到硬盘，跟安装软件没什么两样，不用格式化硬盘。比如安装到 D 盘，则会在 D 盘创建一个 ubuntu 文件夹，在 BOOTMGR 启动项里添加一个 Ubuntu 启动项，仅此而已。

如果我们重装系统了，那么曾经 wubi 安装的 ubuntu 是不是需要重装呢？

肯定不需要了。只要我们 Wubi 安装到非系统盘，重装系统后：

1、将安装目录下的\ubuntu\winboot\wubildr 拷贝至 C:\（即 C 盘根目录）；

2、然后在 menu.lst 中添加以下内容，grub 菜单里便会重现 Ubuntu 的启动项，即可重新引导你曾经安装过的 Wubi Ubuntu。你会得到一个像软件一样的 Ubuntu 系统，可以永远放在你的硬盘里。
<pre>title Ubuntu 10.04 Wubi
    find --set-root --ignore-floppies /ubuntu/winboot/wubildr.mbr
    chainloader /ubuntu/winboot/wubildr.mbr</pre>