---
layout: post
title: KAV/KIS  6.0 / 7.0 永久免费激活方法！
date: 2007-10-25
categories: 技巧分享
tags: ["免费","卡巴斯基","批处理","技巧分享","注册表","激活"]
---

1.把卡巴关闭。

2.运行 → cmd，在命令提示符下执行以下命令：

<!--more-->

`reg delete HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\SystemCertificates\\SPC\\Certificates /f
reg delete HKEY_LOCAL_MACHINE\\SOFTWARE\\KasperskyLab\\LicStorage /f
reg delete HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Cryptography\\RNG /f`

3.打开卡巴，选择 30 天试用，然后激活就可以了，等到一个月后过期的时候再运行这个就可以了，这样反复下去就可以永久免费了！

或是直接下载写好的批处理程序   [**kaspersky key 清除.rar**
](http://cid-6abece639ad907b9.skydrive.live.com/self.aspx/public/kaspersky%20key%e6%b8%85%e9%99%a4.rar)
如果用 360 安全卫士申请 key，现在用 360 申请到的 key 现在大都不能用了，不过 360 申请过仍可以反复申请的，先关掉 360，命令提示符下运行以下命令

`reg delete HKEY_LOCAL_MACHINE\\SOFTWARE\\360safe /va /f`

就可以反复申请 key 了，如果能用，那用 360 申请到的能用半年，则就更方便了。