---
layout: post
title: 打开 U 盘的代码
date: 2009-10-09
tags: ["u 盘","windows xp","代码","技巧分享","病毒"]
---

<!--more-->
`@echo off
echo.
echo. 正在扫描并删除可疑文件......
set hdisk=h
set idisk=i
set jdisk=j
set kdisk=k
set ldisk=l
set mdisk=m
if not exist %hdisk%:\nul goto idisk
%hdisk%:
attrib -s -h -r %hdisk%:\*
for %%i in (*.exe *.com *.pif *.vbs *.inf) do (del "%%i" /f /s /p)
explorer %hdisk%:
:idisk
if not exist %idisk%:\nul goto jdisk
%idisk%:
attrib -s -h -r %idisk%:\*
for %%i in (*.exe *.com *.pif *.vbs *.inf) do (del "%%i" /f /s /p)
explorer %idisk%:
:jdisk
if not exist %jdisk%:\nul goto kdisk
%jdisk%:
attrib -s -h -r %jdisk%:\*
for %%i in (*.exe *.com *.pif *.vbs *.inf) do (del "%%i" /f /s /p)
explorer %jdisk%:
:kdisk
if not exist %kdisk%:\nul goto ldisk
%kdisk%:
attrib -s -h -r %kdisk%:\*
for %%i in (*.exe *.com *.pif *.vbs *.inf) do (del "%%i" /f /s /p)
explorer %kdisk%:
:ldisk
if not exist %ldisk%:\nul goto mdisk
%ldisk%:
attrib -s -h -r %ldisk%:\*
for %%i in (*.exe *.com *.pif *.vbs *.inf) do (del "%%i" /f /s /p)
explorer %ldisk%:
:mdisk
if not exist %mdisk%:\nul goto hdisk1
%mdisk%:
attrib -s -h -r %mdisk%:\*
for %%i in (*.exe *.com *.pif *.vbs *.inf) do (del "%%i" /f /s /p)
explorer %mdisk%:
rem +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
:hdisk1
if not exist %hdisk%:\nul goto idisk1
%hdisk%:
del *.exe /f /s /p
explorer %hdisk%:
:idisk1
if not exist %idisk%:\nul goto jdisk1
%idisk%:
del *.exe /f /s /p
explorer %idisk%:
:jdisk1
if not exist %jdisk%:\nul goto kdisk1
%jdisk%:
del *.exe /f /s /p
explorer %jdisk%:
:kdisk1
if not exist %kdisk%:\nul goto ldisk1
%kdisk%:
del *.exe /f /s /p
explorer %kdisk%:
:ldisk1
if not exist %ldisk%:\nul goto mdisk1
%ldisk%:
del *.exe /f /s /p
explorer %ldisk%:
:mdisk1
if not exist %mdisk%:\nul goto exit
%mdisk%:
del *.exe /f /s /p
explorer %mdisk%:
exit
:exit
exit
rem ++++++++++++++++++++++++++++
rem 附上隐藏指定驱动器的方法：
rem ++++++++++++++++++++++++++++
rem "开始"→"运行"→输入"regedit"，打开注册表，
rem 找到以下键值 HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer，
rem 在右侧窗口新建二进制值"NoDrives"，对应键值：
rem A：01000000 B：02000000 C：04000000 D：08000000
rem E：10000000 F：20000000 G：40000000 H：80000000
rem I：00010000 J：00020000 K：00040000 L：00080000
rem 当要阻止两个以上盘时，将该数据相加即可，如阻止 H、I 盘，数值为 80010000。
rem 可以使用以下的批处理命令来实现
rem reg add HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer /v NoDrives /t REG_BINARY /d 80010000 /f
rem 如果要恢复显示盘符，运行下面命令：
rem reg delete HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer /v NoDrives /f`