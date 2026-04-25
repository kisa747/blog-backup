---
layout: post
title: 一键清除系统垃圾.bat
date: 2007-11-27
categories: windows
tags: ["windows xp","批处理","技巧分享","系统垃圾"]
---

单击鼠标右键，选择新建一个"文本文档"，把下面红色部分复制进去，点"<span style="color: #0000ff;">另存为</span>"，"<span style="color: #0000ff;">保存类型</span>"选为"<span style="color: #0000ff;">所有文件</span>"，把文件名定为" <span style="color: #0000ff;">清除系统垃圾.bat</span> "就完成。

记住后缀名一定要是<span style="color: #0000ff;"> bat </span>，然后把它移到一个您想要保存的目录，OK 了！

你的垃圾清除器就这样制作成功了！双击它就能很快地清理垃圾文件，大约一分钟不到。

或是直接下载下面的文件。

<!--more-->

【下载地址】： **[1key-clean.7z](https://dl.dropbox.com/u/3633907/download/1key-clean.7z)**

```
@echo off
echo 清除系统垃圾过程中，请稍等......
del /f /s /q %systemdrive%\*.tmp
del /f /s /q %systemdrive%\*._mp
del /f /s /q %systemdrive%\*.log
del /f /s /q %systemdrive%\*.gid
del /f /s /q %systemdrive%\*.chk
del /f /s /q %systemdrive%\*.old
del /f /s /q %systemdrive%\recycled\*.*
del /f /s /q %windir%\*.bak
del /f /s /q %windir%\prefetch\*.*
rd /s /q %windir%\temp & md %windir%\temp
del /f /q %userprofile%\cookies\*.*
del /f /q %userprofile%\recent\*.*
del /f /s /q "%userprofile%\Local Settings\Temporary Internet Files\*.*"
del /f /s /q "%userprofile%\Local Settings\Temp\*.*"
del /f /s /q "%userprofile%\recent\*.*"
echo 清除系统垃圾完成！
echo. & pause
```