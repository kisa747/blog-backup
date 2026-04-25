---
layout: post
title: ubuntu 简单优化
date: 2007-12-15
tags: ["linux","ubuntu","优化"]
---

<span style="color: #800000;">sudo aptitude install sysv-rc-conf </span>

<span style="color: #800000;"> who -r </span> 查看系统运行级别

<span style="color: #800000;"> sudo sysv-rc-conf</span>

acpid      acpi-supp        高级电源管理。笔记本用户开启它。

<!--more-->

avahi-daemon           Avahi 是 zeroconf 协议的实现。除非你有兼容的设备或使用 zeroconf 协议的服务，去掉。
ConsoleKit               Fast User Switchin，快速用户切换，关掉
dbus                       自动挂载服务，开着
dhcdbd                   D-BUS 系统网络接口，主要为你提供网络连接设置，强烈建议开着，除非你用固定 IP 上网。
HAL（Hardware Abstraction Layer）硬件抽象层 服务，开着
hotkey-setup          只有笔记本可能需要，你可以尝试去掉，有副作用就改回来
klogd                      linux 守护程序，接受来自内核和发送信息到 syslogd 的记录，并记录为一个文件，所以开着有用，关了也无妨
makedev                用来创建设备到/dev/，开着
powernowd             如果 CPU 支持变频，可以留着省电，没有的去掉
rc.local                    开着
rmnologin              如果发现 nologin，就去掉，在笔记本上不用开启。
rsync                      rsync 协议守护，如果不知道干嘛的，去掉
stop-read             不清楚，开着吧
sysklogd               用于记录系统日志信息，去掉也无妨
vbesave               显卡 bios 配置工具，开着
xserver-x             开着
cupsys                  如果你常用打印机，就留着
hdparm               如果都是 SATA 硬盘 去掉吧
dns-clean              如果是拨号上网的，留着
ppp                    拨号上网用的 不拨号的就关掉
ppp-dns             同上

evms，cron，anacron，apmd，atd，mdamd,lvm 如果不知道是什么，可以放心去掉

关闭 IPV6

<span style="color: #800000;"> sudo gedit /etc/modprobe.d/aliases</span>

找到           <span style="color: #0000ff;">alias net-pf-10 ipv6</span>
改为           <span style="color: #0000ff;">alias net-pf-10 off #ipv6</span>

<span style="color: #800000;"> sudo gedit /etc/hosts</span>

顺便将 localhost 化名为主机名 ubuntu

<span style="color: #0000ff;"> 127.0.0.1 localhost ubuntu
127.0.1.1 ubuntu</span>

然后注释掉 hosts 文件中所有与 IPV6 有关的行，这将会禁止所有使用 IPV6 的网络接口，你需要重新启动计算机。

禁用 pango
<span style="color: #800000;">sudo echo 'MOZ_DISABLE_PANGO="1"' >> /etc/environment</span>