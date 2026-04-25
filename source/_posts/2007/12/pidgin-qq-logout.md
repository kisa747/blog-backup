---
layout: post
title: 这个平安夜 ─ pidgin 无法登录 qq 了
date: 2007-12-24
tags: ["linux","pidgin","qq","ubuntu"]
---

平安夜回来登录 pidgin，发现它竟登录不上 qq 了。郁闷...

在源里添加个新的源，更新下 pidgin，更新后把这俩行给注释掉就 OK 了
在 apt 源 (/etc/apt/sources.list 中加入如下两行，我几乎不用 src，就把第二行给注释了：

<!--more-->
<span style="color: #0000ff;">deb http://apt.schmidtke-hb.de gutsy main
#deb-src http://apt.schmidtke-hb.de gutsy main</span>

下载 key 文件：

<span style="color: #800000;">wget http://apt.schmidtke-hb.de/aptrepository.asc</span>

导入 key 文件：aptrepository.asc

<span style="color: #800000;">sudo apt-key add aptrepository.asc</span>

之后升级下就行了

<span style="color: #800000;"> sudo aptitude update && sudo aptitude safe-upgrade</span>

<span style="color: #000000;">嘿嘿，还真的有三个文件要升级，好像都是 pidgin 的</span>
<span style="color: #0000ff;">
The following packages will be upgraded:
libpurple0 pidgin pidgin-data
3 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.</span>

升级后，pidgin 就成了 2.3.1 版，想应该能登录了吧，结果还是登不上，怒了！在 virtualbox 里一登录，提示 qq 非法登录，需要激活等一大堆废话，看的我一肚子火，平安夜腾讯竟然这样来祝福，无奈啊！可怜的腾讯！激活后 qq 仍 然载 pidgin 下无法登录，应该是腾讯要验证码的缘故吧。对腾讯，除了无奈，还能怎样，可能最近好长时间都无法用 qq 了。暂时用 MSN 替代了，可惜 MSN 下的好友少的可怜。