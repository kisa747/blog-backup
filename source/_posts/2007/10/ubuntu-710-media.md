---
layout: post
title: Ubuntu 7.10 多媒体解决方案
date: 2007-10-19
categories: linux
tags: ["linux","ubuntu","多媒体"]
---

<span style="color: #ff0000;">**我的多媒体解决方案**</span>

一般普通的播放任务使用 Mplayer 的前端 smplayer，偶尔遇到不能播放的情况或者看大碟时就选用 Totem 电影播放机，播放音乐使用 audacious。

<!--more-->

为了方便所以来个一键全媒体方案

sudo apt-get remove totem-mozilla

sudo apt-get install mplayer mozilla-mplayer  audacious realplay smplayer

装多媒体软件和相应解码器

安装 audacious      Ubuntu 中类似千千静听的的播放器，
支持播放 ogg*, flac*, mp3, wma, wav, 3gp 这些格式。
安装 mplayer 和 totem (播放 xvid/divx 编码的 avi 格式视频，rm/rmvb/asf/wmv 等流媒体视频，外加 vcd/dvd和其他 mpeg2/mpeg4 视频。)
对于 totem，播放对应格式的多媒体时会自动搜索所需的解码器，所以就不必专门安装解码器了，但 mplayer 需单独安装强大的 win32codes 解码器。
win32codes 的下载地址：
[http://archive.ubuntu.org.cn/ubuntu-cn/dists/edgy/main/binary-i386/media/w32codecs_20060611-1plf6.10_i386.deb](http://archive.ubuntu.org.cn/ubuntu-cn/dists/edgy/main/binary-i386/media/w32codecs_20060611-1plf6.10_i386.deb)
[ftp://211.86.156.210/debian-multimedia/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb](ftp://211.86.156.210/debian-multimedia/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb)

Totem（或使用 xine）播放 rmvb 没有声音的解决办法
打开主文件夹，按 Ctrl+H 显示所有文件
找到并编辑~/.xine/catalog.cache 文件
[/usr/lib/xine/plugins/1.1.4/xineplug_decode_real_audio.so]
把 decoder_priority 增加到 10

Audacious 的设置
1）解决 audacious 中文乱码现象：在 audacious 上右键选择"首选项"，在"播放列表"中，把标题格式改为"Custom",再把自定格式改为
"%f"（不要引号）。
2) 如果要让 audacious 播放 APE 格式的音乐：
sudo apt-get install audacious-mac
3) 如果需要把 APE 转换为 FLAC：
sudo apt-get install mac flac cuetools shntool
cuebreakpoints xx.cue 'shnsplit -o flac -n xx xx.ape

Mplayer 的中文字幕设置方法
1) 在 Preferences-Font 里面点击 "Browse" 选择一个中文字体，Encodeing 选择 Unicode。
2) 在 Preferences-Subtitle&OSD 里面的 Encoding 选择：
Simplified Chinese Charset(cp936)
3) 在 Preferences-Font "Text scale" 这里调整字幕大小 (我调整为 3.8 )。
如果播放时提示错误，设置一下：
Preferences-Video 选择 "xv X11/Xv" "Enable frame dropping"
Preferences-Codecs&demuxer 选择 "FFmpeg/libavcodec audio decoders"
如果要让 Rhythmbox 和 Banshee 这些使用 gstreamer 为后端的播放器，能播放 mp3, wma, ra, ram, wav 等格式音乐，就装上：
sudo apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-pitfdll gstreamer0.10-ffmpeg

2、安装 Realplayer 播放器
sudo apt-get install realplay
安装了 realplay，如果打不开。可能是因为和 SCIM 输入法有冲突，可这样处理：
sudo gedit /usr/bin/realplay
在第二行也就是"#!/bin/sh"的下一行加入 CODE 代码：
GTK_IM_MODULE=xim; export GTK_IM_MODULE

3、安装 smplayer：一个非常好的播放器！
sudo apt-get install smplayer

4、使用 Firefox 在线播放解决办法
1) 内嵌播放，可以安装 MediaWrap 这个扩展。
2) 如果喜欢调用外部播放器播放，安装 MediaPlayerConnectivity。
播放不了在线的 MP3 文件的，就像在百度 MP3／SOSO，有可能是因
为用了 totem 的插件，因此我们把 totem 的 firefox 插件删除就可以了
，使用命令：
sudo apt-get remove totem-mozilla

这样 firefox 就会用 MPLAYER 的播放了

5、安装 LyricZilla（可能 CPU 占用比较高）
LyricZilla 是为 Linux 下的多款音乐播放器做的插件（现在可插于 beep-media-player 和 audacious）。它能够自动搜索当前播放歌曲的歌词，而且当前行会在播放时滚动。
1. 加入 APT 源：
sudo wget http://lyriczilla.googlecode.com/svn/trunk/package/lyriczilla.list -O /etc/apt/sources.list.d/lyriczilla.list
2. 安装：sudo apt-get update
sudo apt-get install lyriczilla lyriczilla-plugin-audacious lyriczilla-plugin-bmp
安装好之后，在 beep-media-player 或 audacious 的首选项－插件－常规里面，勾选它。