---
layout: post
title: 毕业设计把人给整疯了！
date: 2009-06-16
tags: ["代码","备份","心情随笔","毕业设计","脚本"]
---

一个毕业设计，害的我每天都忙得不亦乐乎。到现在也没发现整个毕业设计的必要性，倒是其它方面学到了不少，像是 WORD 排版、EXCEL 知识学了一大堆，还有就是各种我们的专业规范，以及苛刻的论文格式。

我也是担心自己的毕业论文丢失，还专门写了个 CMD 脚本，以实现增量备份。

<!--more-->

`@echo off
set /a a=1
set filebak=F:\bak
set filesource=E:\My Documents\毕业设计
:fanfu
set filebakname=%filebak%\毕业设计-%date%-%a%.7z
if not exist "%filebakname%" goto :zhixing
set /a b=%a%+1
set /a a=%b%
goto :fanfu
:zhixing
@echo on
"%ProgramFiles%\7-Zip\7z.exe" a -t7z "%filebakname%" "%filesource%" -r -mx=5
`