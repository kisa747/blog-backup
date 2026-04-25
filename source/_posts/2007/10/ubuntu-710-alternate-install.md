---
layout: post
title: 硬盘安装 Ubuntu 7.10（alternate 版）（转）
date: 2007-10-18
categories: linux
tags: ["linux","ubuntu","安装"]
---

2007 年 10 月 18 日，酝酿了半年之久的"长臂猿"--Ubuntu 7.10 Gutsy Gibbon 正式发布了！

硬盘安装 Ubuntu 7.10           配图文（alternate 版，文本安装界面）

<!--more-->

1、下载光盘镜像

首先下载我们需要的光盘镜像，如果你喜欢刻盘安装那就下载 desktop 版本刻盘安装，

我们这里讨论的是使用 7.10 的最后一个测试版

）<span style="color: #993300;">ubuntu-7.10--alternate-i386.iso</span>

进行硬盘安装，所以推荐下载 alternate 版。

下载地址：

[http://releases.ubuntu.com/releases/gutsy/ubuntu-7.10-alternate-i386.iso](http://releases.ubuntu.com/releases/gutsy/ubuntu-7.10-alternate-i386.iso)

[http://releases.ubuntu.com/releases/gutsy/ubuntu-7.10-alternate-amd64.iso
](http://releases.ubuntu.com/releases/gutsy/ubuntu-7.10-alternate-i386.iso)

[
](http://releases.ubuntu.com/releases/gutsy/ubuntu-7.10-alternate-i386.iso)

如果你刻盘安装，那么把刻好的盘直接放到光驱中，desktop 版本启动之后可以进入一个 livecd 模式，你可以在里面先体验一下，点击桌面上的 install 进行安装，按提示一步步安装就行了。alternate 版本的就会出现下面的画面，直接选择第一项进入。（直接跳到第 5 步）

下面说一下硬盘安装的方法。

2、下载引导文件

先下载好<span style="color: #0000ff;">光盘镜像，</span><span style="color: #0000ff;">放在某个分区根目录下</span>（如 D:\\），然后下载硬盘安装的引导文件

，下载地址：

http://ubuntu.cn99.com/ubuntu/dists/gutsy/main/installer-i386/current/images/hd-media/initrd.gz

http://ubuntu.cn99.com/ubuntu/dists/gutsy/main/installer-i386/current/images/hd-media/vmlinuz

<span style="color: #333333;">注：也可以到我的 [纳米盘下载](http://www.namipan.com/d/d9c36e3899ca9227b04138244ce213eba377a71e3c077400)</span>

将以上两个文件下载，放在某个分区里。这里我们放置在<span style="color: #000000;">C:</span><span style="color: #333333;"> \\
</span>

<span style="color: #0000ff;">C:\\initrd.gz                      C:\\vmlinuz</span>
<div>3、准备分区</div>
<div>在硬盘上用分区魔术师之类的软件分出来一个 ext3 的分区（最好大于 5G，我的是 12G），
作为 linux 根分区，分出一个大小为内存 2 倍的 swap 分区
（如果是 512 内存可以就用 512M 是 swap 交换区），作为 linux 的虚拟内存。</div>
<div>最基本的要分出：一个/<span style="color: #0000ff;">swap</span>，一个<span style="color: #0000ff;">/</span></div>
4、准备 grub，引导安装程序

然后下载一个 grub for dos，下载地址：<span style="color: #ff0000; font-size: small;">[http://download.gna.org/grub4dos/grub4dos-0.4.3.zip](http://download.gna.org/grub4dos/grub4dos-0.4.3.zip)</span>

将此文件解压到 C:<span style="color: #333333;"> \\ </span>，再用记事本打开 menu.lst，并将里面的文字删掉后加

入如下代码（"#"可包括也可不包括，"#"是用来注释用的）：

<span style="color: #0000ff;">############################
color black/cyan yellow/cyan
timeout 30
default 0
fallback 1</span>

<span style="color: #0000ff;">title Install Ubuntu7.10
kernel (hd0,0)/vmlinuz
initrd (hd0,0)/initrd.gz
boot</span>

<span style="color: #0000ff;">title Back To (Windwos OS)
rootnoverify (hd0,0)
makeactive
chainloader                                 +1</span>

<span style="color: #0000ff;">title commandline
savedefault --wait=2
commandline</span>

<span style="color: #0000ff;">title Reboot
savedefault --wait=2
reboot
############################</span>

然后保存退出。

注意：命令里面的 (hd0,0) 不是绝对的，要看你文件放置的分区和目录决定。

hd 第一个 0 代表你第一个硬盘，第二个 0 代表第一个分区！！

5、进行安装

>>重启进入安装（先选择，进入 GRUB，再选择<span style="color: #0000ff;">Install Ubuntu7.10</span>，进入安装界面
<div>
<div>
<div>>>选择语言，这里我们选择中文简体（看着舒服^_^）</div>
<div>
<div>位置就选中国吧~</div>
<div>
<div>
<div>>>选择键盘，这里选"否"，在下面手动选择键盘，这里选"是"的话还要测试，麻烦</div>
<div>
<div>>>选择 USEnglish</div>
</div>
</div>
</div>
</div>
</div>
</div>
<div>>>还选 USEnglish</div>
<div>>>系统探测硬件，如果是硬盘安装，这里会显示自动装载分区，探测光盘镜像</div>
<div>>>自动载入安装需要的文件</div>
<div>>>探测网络</div>
<div>>>自动配置网络，貌似没什么用。。。</div>
<div>>>随便输入个主机名</div>
<div>>>探测你的硬件配置</div>
<div>>>自动扫描磁盘分区情况。</div>
<div>>>这里选手动，否则你硬盘上的其他东东都会玩完了。</div>
<div>
<div>
<div>>>将你需要把 ubuntu 安装进去的根分区改成如上图所示的状态</div>
<div>>>选择分区设定结束写入硬盘。</div>
<div>
<div>>>再检查一遍，不要弄错了。。。</div>
<div>
<div>>>安装程序自动格式化分区</div>
<div>>>还是选"否"，选"是"的话有可能系统时间混乱。</div>
<div>>>输入用户名</div>
<div>
<div>>>这个是真正在登录时用到的用户名。</div>
</div>
</div>
</div>
</div>
</div>
<div>>>设置帐户的密码。</div>
<div>>>自动安装基本系统</div>
<div>>>这个要选"否"，如果选"是"，会在一会安装过程中卡在 85%                                          另外在安装过程中会询问你是否安装 ubuntu-desktop，当然要用空格把它选上，然后按 tab 切换到"确定"按钮，回车。</div>
<div>>>设置你的 x-window</div>
<div>>>安装结束。选择"继续"重启。</div>
<div>>>重启后 ubuntu 漂亮的引导画面</div>
<div>>>登录界面</div>
<div>gnome 启动。。。</div>
<div>安装流程到此结束。</div>
注：如果安装盘没能装您的显卡驱动，则将不能进入桌面系统。若系统不能自动完成对应版本的驱动，可以以低分辨率显示进入。

进入 7.10 的桌面