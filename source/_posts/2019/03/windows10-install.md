---
layout: post
title: windows10 安装方法
date: 2019-3-27 9:13
categories: windows
tags: [windows]
---

## 准备工具

* windows 10 的 iso 镜像，推荐使用 ltsc 长期支持版：[cn_windows_10_enterprise_ltsc_2019_x64_dvd_9c09ff24.iso](ed2k://|file|cn_windows_10_enterprise_ltsc_2019_x64_dvd_9c09ff24.iso|4478906368|E7C526499308841A4A6D116C857DB669|/) 

  记得校验一下 SHA1 值：`24b59706d5eded392423936c82ba5a83596b50cc`

* 一个不小于 8G 的 U 盘。

* 下载 [Rufus](https://rufus.ie/)，用来创建 USB 启动盘。

<!-- more -->

## 安装步骤

1. 做好电脑的备份工作。
2. 使用 Rufus 将 windows 10 的 iso 镜像 创建 USB 启动盘。
3. 使用 U 盘启动电脑，安装 windows 10。

**搞定！**

## 注意

* 使用 Windows 自带的分区工具会创建 MSR 分区，如果不想要 MSR 分区，推荐使用 DiskGenius 等第三方工具。
* 安装时建议拔掉网线，不要联网。如果联网，有 2 个缺点：
* - 1、安装时会优先创建网络账号（可以手动更改）。
  - 2、安装成功进入系统，会自动更新。我的电脑会引起死机。但是安装完设备驱动后，再手动进行更新就没有问题。
* 推荐的做法是，安装成功后，先不要更新，待安装完设备驱动后，再手动更新。

