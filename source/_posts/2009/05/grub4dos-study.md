---
layout: post
title: Grub4Dos 学习手记
date: 2009-05-22
tags: ["dos","grldr","grub","技巧分享"]
---

Grub4Dos 很简单，最核心的文件就一个 grldr，我用的也就不过 4 个文件。结构如下：

> │  grldr
> └─kisa
>   └─grub
>     fonts
>     menu.lst
>     rhel.xpm.gz
<!--more-->

grldr 可以内置 menu.lst，编辑工具官网就有，就是 <span style="color: #0000ff;">grubmenu.exe</span> ，通过用 grubmenu.exe 的 export 和 import 命令就 OK 了。

grldr 内置菜单 menu.lst 内容如下：

`pxe detect
configfile
default 0
timeout 1
title find /menu.lst, /boot/grub/menu.lst, /grub/menu.lst
	errorcheck off
	configfile /menu.lst
	configfile /boot/grub/menu.lst
	configfile /grub/menu.lst
	find --set-root --ignore-floppies --ignore-cd /menu.lst && configfile /menu.lst
	find --set-root --ignore-floppies --ignore-cd /boot/grub/menu.lst && configfile /boot/grub/menu.lst
	find --set-root --ignore-floppies --ignore-cd /grub/menu.lst && configfile /grub/menu.lst
	errorcheck on
	commandline
title commandline
	commandline
title reboot
	reboot
title halt
	halt
`

外置 menu.lst 内容示例：

`timeout 10
default 0
splashimage /kisa/grub/rhel.xpm.gz
fontfile /kisa/grub/fonts
title Micro WinPE
chainloader /ldrxpe
title Windows XP
find --set-root --ignore-floppies /ntldr
chainloader /ntldr
title Windows VISTA
find --set-root --ignore-floppies /bootmgr
chainloader /bootmgr
title 重启
reboot
title 关机
halt
`

grub 及编辑器下载：  **[Grub.rar](http://cid-6abece639ad907b9.skydrive.live.com/self.aspx/public/grub.rar)**