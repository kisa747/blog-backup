---
layout: post
title: VirtualBox 问题
date: 2007-10-23
categories: linux
tags: ["linux","virtualbox","设置"]
---

启动后提示如下

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..

<!--more-->

VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).
Result Code:

0x80004005

Component:

Console

Interface:

IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

sudo usermod -G vboxusers -A myname 搞不定，/dev/vboxdrv 的权限改了不能保存，重启后要重新改。晕哦

解决的方法：
<span style="color: #ff0000;"> sudo chmod 777 /dev/vboxdrv</span>