---
layout: post
title: 右键添加“DOS 快速通道”
date: 2007-11-22
tags: ["dos","reg","windows xp","技巧分享"]
---

1、新建一个文本文件，更名为 dos.reg；

2、将下面的代码拷贝到 dos.reg 文件中

<!--more-->
```ini
Windows Registry Editor Version 5.00
[HKEY_CLASSES_ROOT\\Folder\\shell\\DOS]

@="DOS快速通道(&Y)"

[HKEY_CLASSES_ROOT\\Folder\\shell\\DOS\\command]
@="cmd.exe /K CD %1"

[HKEY_LOCAL_MACHINE\\SOFTWARE\\Classes\\Folder\\shell\\DOS]
@="DOS快速通道(&Y)"

[HKEY_LOCAL_MACHINE\\SOFTWARE\\Classes\\Folder\\shell\\DOS\\command] @="cmd.exe /K CD %1"
```

3.保存退出后，双击 dos.reg 文件，再在弹出的对话框中选择"是"就可以了！

或是直接下载写好的文件：[**右键添加 dos 快速通道.rar**](http://cid-6abece639ad907b9.skydrive.live.com/self.aspx/public/%e5%8f%b3%e9%94%ae%e6%b7%bb%e5%8a%a0dos%e5%bf%ab%e9%80%9f%e9%80%9a%e9%81%93.rar)

在文件夹上单击鼠标右键，就会有"DOS 快速通道"的选项，选择后命令行提示符就显示于此目录下了！
