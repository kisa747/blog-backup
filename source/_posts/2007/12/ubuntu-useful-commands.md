---
layout: post
title: ubuntu 下一些有用的命令
date: 2007-12-15
tags: ["linux","ubuntu","命令"]
---

（1）软件包管理

sudo aptitude update && sudo aptitude safe-upgrade          一键升级系统
apt-cache search name                                                   搜索包含"name"软件包
sudo apt-get autoremove                                               自动卸载不需要的软件包
sudo apt-get autoclean                                                清理旧版本的软件缓存
sudo apt-get clean                                                         清理所有 apt 下载的软件缓存

<!--more-->

（2）硬件相关
sudo lshw                    显示系统详细硬件信息
uname -a                        查看系统、主机名称、内核版本、日期与时间、以及处理器等信息
df -h                                   查看磁盘的占用空间及可用空间
更改分区卷标，分别是 ext 和 xfsd：
sudo e2label /dev/hda5 E_Download
sudo xfs_admin -L E_Backup /dev/hda12

sudo hdparm -cdtT /dev/hda                       测试 IDE 硬盘的读写速度
以下仅适合 IDE 硬盘操作，sata 硬盘勿试
=====================================
sudo hdparm -c 1 -d 1 /dev/hda                  设置硬盘到 I/O 32 位，开启 DMA。
sudo hdparm -k 1 /dev/hda                         保存更改
=====================================

（3）用户和组
groups               查看你的帐号属于哪些用户组
hostname        显示主机名称
id                       查看用户 id、组 id 及你帐号的组
uname              查看系统、主机名称、内核版本、处理器等信息
w                       查看谁登录及他们在干什么
who                   查看谁登录了系统
whoami              查看你的用户名（或帐号名）
（4）进程。配合 df 命令可取代 gnome-system-monitor
ps -A                                                            查看当前有哪些进程
kill 进程号 (就是 ps -A 中的第一列的数字)           中止一个进程
killall 进程名                                                  中止一个进程（同上）
kill -9 进程号                                                  强制中止一个进程 (在上面进程中止不成功的时候使用)
killall -9 进程名                                               强制中止一个进程 (同上)
xkill                                                               图形方式中止一个程序
top                                                              查看当前进程的实时状况
lsof -p                                                          查看进程打开的文件

（4）其它
nautilus 的地址栏里输入 fonts:///                    可以查看本机所有的 fonts

sudo mkfontscale
sudo mkfontdir
fc-cache -f                                                   安装字体后刷新字体缓存（加上 -v 参数可以刷新所有字体缓存）
pwd：查看当前工作的目录
clear            清屏       <span style="color: #993300;"> <span style="color: #ff6600;"> Ctrl+L（快捷键）擦除并且重写屏幕</span>