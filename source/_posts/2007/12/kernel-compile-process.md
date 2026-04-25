---
layout: post
title: 实战内核编译全过程
date: 2007-12-15
tags: ["linux","linux","内核","编译"]
---

1、确定自己内核的版本

`uname -r`

我的内核版本是 <span style="color: #0000ff;">2.6.22-14 </span>，我下载了对应版本的源码包进行编译

<!--more-->

`wget ftp://ftp.kernel.org/pub/linux/kernel/v2.6/linux-2.6.22.14.tar.bz2`

下载完后，将源代码解压开：

`tar xjf linux-2.6.22.14.tar.bz2`

安装编译内核所有需要的软件包

sudo aptitude install kernel-package libncurses5-dev

进入源码目录进行操作

<span style="color: #800000;">cd linux-2.6.22.14</span>

下面开始配置内核，使用现有内核的配置文件作为新内核配置文件的基础，这样 不容易出错。
先复制已经存在的配置文件到当前目录中

<span style="color: #800000;">cp /boot/config-`uname -r` ./.config</span>

然后运行

<span style="color: #800000;">make menuconfig</span>

这将显示出内核配置菜单。在下面选择 "Load an Alternate Configuration File"，再选择你刚才拷贝过来的.config 文件作为配置文件，然后确定。当结束后，你选择退出时，会提示问你 "Do you wish to save your new kernel configuration?"选择 yes 即可。

编译进内核是*号，编译成模块是 M 号，不编译是空白。

里面复杂的内容参照[Linux 2.6.19.x 内核编译配置选项简介](http://lamp.linux.gov.cn/Linux/kernel_options.html)

或是参考这里[kernel_options.html](http://dl.dropbox.com/u/3633907/file/kernel_options.html)
配置完后，创建内核，执行下面两个命令：

清理一下

<span style="color: #800000;">make-kpkg clean</span>

真正开始编译

<span style="color: #800000;">sudo make-kpkg --initrd --append-to-version kisa747 kernel_image</span>

近一个小时内核的编译终于结束，安装新的内核

<span style="color: #800000;">cd ..</span>

<span style="color: #800000;">sudo dpkg -i linux-image-2.6.22.14</span> (用 Tab 键补全)

重启就在 grub 菜单里就看到自己编译的内核的选项。但由于第一次编译内核未能成功，以后有时间多学习希望能编译成功。