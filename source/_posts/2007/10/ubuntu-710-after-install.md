---
layout: post
title: Ubuntu 7.10 安装后做的几件事
date: 2007-10-24
categories: linux
tags: ["linux","ubuntu","安装"]
---

网络配置，上网才是首要任务

使用 ADSL 上网的，这里先设置 ADSL：

<!--more-->
> sudo pppoeconf                     配置 ADSL
> 
> pon dsl-provider                  ADSL 手工拨号上线
> 
> poff                                                  ADSL 下线
<span style="color: #ff0000;">sudo /etc/ppp/pppoe_on_boot    激活 ADSL</span>
非拨号用户使用以下命令设置网络
<span style="color: #ff0000;">sudo vi /etc/network/interfaces</span>

网卡通过 DHCP 自动获取 IP 地址
> # The primary network interface（配置主网络接口）
> 
> #开机自动激活 eth0 接口
> 
> auto eth0
> 
> #配置 eth0 接口为 DHCP 自动获取
> 
> iface eth0 inet dhcp
获取 IP 地址

<span style="color: #ff0000;">sudo dhclient eth0</span>

网卡静态分配 IP 地址
> #开机自动激活 eth0 接口
> 
> auto eth0
> 
> #配置 eth0 接口为静态设置 IP 地址
> 
> iface eth0 inet static
> 
> address 192.168.1.2
> 
> netmask 255.255.255.0
> 
> network 192.168.1.0
> 
> broadcast 192.168.1.255
> 
> gateway 192.168.1.1
激活以上设置

<span style="color: #ff0000;">sudo /etc/init.d/networking restart</span>

我的这样总是无法激活网络，但 stop，再激活却可以，奇怪！

<span style="color: #ff0000;">sudo /etc/init.d/networking stop && sudo /etc/init.d/networking start</span>

DNS 设置

<span style="color: #ff0000;">sudo /etc/resolv.conf</span>

加入

<span style="color: #3366ff;">nameserver 202.102.152.3</span>

1，重新设置 apt 的源，我使用的是 cn99 的源

<span style="color: #3366ff;">sudo gedit /etc/apt/sources.list</span>

把其中的内容改为

`deb http://ubuntu.cn99.com/ubuntu/ gutsy main restricted universe multiverse
deb http://ubuntu.cn99.com/ubuntu/ gutsy-security main restricted universe multiverse
deb http://ubuntu.cn99.com/ubuntu/ gutsy-updates main restricted universe multiverse
deb http://ubuntu.cn99.com/ubuntu/ gutsy-proposed main restricted universe multiverse
deb http://ubuntu.cn99.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://ubuntu.cn99.com/ubuntu/ gutsy main restricted universe multiverse
deb-src http://ubuntu.cn99.com/ubuntu/ gutsy-security main restricted universe multiverse
deb-src http://ubuntu.cn99.com/ubuntu/ gutsy-updates main restricted universe multiverse
deb-src http://ubuntu.cn99.com/ubuntu/ gutsy-proposed main restricted universe multiverse
deb-src http://ubuntu.cn99.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb http://ubuntu.cn99.com/ubuntu-cn/ gutsy main restricted universe multiverse
`
2，然后就可以升级系统到最新。

<span style="color: #3366ff;">sudo aptitude update && sudo aptitude upgrade</span>

更新可能出现错误：
> updating fontconfig cache
> 
> failed to write cache
终端输入以下命令修正错误：

`sudo fc-cache -fv 2>&1 ' grep failed ' cut -f1 -d":" ' xargs -i sudo touch {} && sudo fc-cache -fv`

3，安装 firefox 扩展，登录 [Firefox 附加软件](http://addons.sociz.com/firefox)
> Adblock_Plus
> 
> All-in-One Gestures
> 
> Tab Mix Plus
> 
> ScrapBook
> 
> Menu Editor
> 
> Fasterfox
> 
> DownThemAll!
4，安装 nautilus-gksu，右键添加"以管理员打开"的选项

<span style="color: #800000;">sudo aptitude install nautilus-gksu</span>

5,ubuntu 右键在当前目录执行终端 terminal 程序

在 $HOME/.gnome2/nautilus-scripts 目录下增加一个文件：Open in terminal

设置它的权限成为可执行。

然后编辑它的内容如下：

`gnome-terminal --working-directory= $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS`

或是用命令

`cd ~/.gnome2/nautilus-scripts
touch 'Open in terminal'
chmod a+x 'Open in terminal'
echo 'gnome-terminal --working-directory= $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS' > 'Open in terminal'
`

保存后，重启 X

在你想要终端运行的目录中，点右键选择 Scripts->Open in terminal，就可以打开终端了，并且终端的起始目录就是你的当前目录

6，安装解码器、flashplayer、java 虚拟机、微软字体，这是 ubuntu 推出的一个新软件包，将一次性将上面几个东东自动装好

在终端输入

<span style="color: #ff0000;">sudo apt-get install ubuntu-restricted-extras</span>

即可完成安装

7，安装 rar 支持

<span style="color: #ff0000;">sudo aptitude install rar</span>

8，安装 fcix 输入法

<span style="color: #ff0000;">sudo apt-get install fcitx</span>

设置 fcix 为默认的输入法

<span style="color: #ff0000;">im-switch -s fcitx -z default</span>

然后要稍微设置一下

修改 fcitx 的配置文件，使它好看一点

<span style="color: #ff0000;">sudo gedit ~/.fcitx/config</span>

找到以下部分修改一下就行了
> [界面]
> 候选词个数=8
> 
> 主窗口是否使用 3D 界面=0
> 
> 输入条使用 3D 界面=2
> 
> 主窗口隐藏模式=0
> 
> 是否自动隐藏输入条=1
9，在 7.04 版里，可以通过"登录窗口"设置登录的背景颜色，但在 7.10 下这个方法不灵了，可能是 BUG 吧。这就需要边界 GDM 的配置文件了

<span style="color: #ff0000;">sudo gedit /etc/gdm/PreSession/Default</span>

修改其中的字段

<span style="color: #3366ff;">BACKCOLOR="#3C61D2"</span>

"#3C61D2"为对应的背景色，共有三处，都可以修改，"#3C61D2"是我配的蓝色调，你也可以自己配出来，简单方法就是依次点击

系统－》系统管理－》登录窗口－》本地选项卡》背景颜色

然后调配出自己喜欢的颜色，下面就有对应的颜色的代码。

10，让 pdf 支持中文。

<span style="color: #ff0000;">sudo aptitude install xpdf-chinese-simplified xpdf-chinese-traditional</span>

11，我的 ATI X300 显卡，安装对应显卡驱动

<span style="color: #ff0000;">sudo aptitude install xorg-driver-fglrx</span>

12，安装英汉词典，和一个简明英汉词库

<span style="color: #ff0000;">sudo aptitude install stardict-cdict-gb stardict</span>