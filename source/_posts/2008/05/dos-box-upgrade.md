---
layout: post
title: DOS 工具箱更新啦！
date: 2008-05-23
tags: ["dos","windows xp","工具箱","技巧分享"]
---

最近重新修改了 DOS 工具箱的安装方法，就赶紧释放出来了

**[DOS 工具箱.rar](http://cid-6abece639ad907b9.skydrive.live.com/self.aspx/public/DOS%e5%b7%a5%e5%85%b7%e7%ae%b1.rar)**

说明：

<!--more-->

1、安装后会在 C 盘建立以下文件：

`├─ GSLDR
│
└─boot
│     ├─ setup.cmd
└─gho1
       ├─ DM957.IMG
       ├─ DOSTOOLS.IMG
       ├─gdisk.img
       ├─ghost.img
       ├─HDDREG15.IMG
       ├─KV2006.IMG
       ├─MENU.LST
       ├─NU2002.IMG
       ├─ PM805.IMG
       └─xly2007.img
`

其中<span style="color: #ff0000;"> install.cmd</span>为安装配置文件，运行安装程序后就自动运行<span style="color: #ff0000;"> install.cmd</span>
代码如下：

`@echo off
color 0a
cls
C:
cd\
echo.
echo 正在设置中......
attrib -r -h -s c:\boot.ini
for /f "tokens=* delims=" %%i in (c:\boot.ini) do (for /f "tokens=*" %%m in (';findstr "timeout" c:\boot.ini';) do (if "%%i"=="%%m" ( echo timeout=3 >>boot_tmp)   else echo %%i >>boot_tmp))
move /y boot_tmp boot.ini
echo C:\GSLDR="DOS 工具箱" >>c:\boot.ini
attrib +r +h c:\boot.ini
exit
`

2、里面的工具都是 DOS 之家的超级 DOS 急救盘提取出来的。ghost 也为 11.0.1.1533 版
3、修改启动等待时间为 3 秒。