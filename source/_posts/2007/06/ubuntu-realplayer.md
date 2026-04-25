---
layout: post
title: Ubuntu 下 Realplayer 的问题
date: 2007-06-23
categories: linux
tags: ["linux","realplayer","ubuntu"]
---

1，Realplayer 没有声音，这是因为 Realplayer 与 scim 冲突，修改/usr/lib/realplay-10.0.8/realplay

在第二行添加

export GTK_IM_MODULE=xim

2，修改后可能画面很卡，是因为声音输出的冲突，修改~/.realplayerrc 文件的配置，
在[Helix]下面添加一段

SoundDriver=1

就 OK 了，不行的话，把 1 改为 2