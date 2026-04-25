---
layout: post
title: Avira antivir 9 Free 版三点设置
date: 2009-05-19
tags: ["avira","代理","广告","技巧分享","杀毒","软件"]
---

![avira antivus](4207098349_887d901376_o.jpg)附上一个有用的教程：**[AviraV9 精美电子书 (P 版).rar](https://skydrive.live.com/redir.aspx?cid=6abece639ad907b9&resid=6ABECE639AD907B9!223&parid=6ABECE639AD907B9!134)**

### （1）屏蔽升级广告

点击开始菜单，选择"运行"，在里面输入<span style="color: #ff0000;">gpedit.msc</span>，打开组策略。

<!--more-->

[![](http://localhost/img/2009/4118829871_da3e592229_o.jpg)](4118829871_da3e592229_o.jpg)

### （2）屏蔽开机画面

方法一：运行 SREng 工具，修改 avria 的启动项，添加<span style="color: #ff0000;"> /nosplash</span> 参数就行了

附上 SREng 工具的下载地址： ** [sReng](http://www.kztechs.com/sreng/download.html)**
[![](http://localhost/img/2009/4081850918_1307ab9d7d_o.gif)](4081850918_1307ab9d7d_o.gif)

方法二：『开始』菜单=>运行=>输入 <span style="color: #ff0000;"> regedit</span> ，打开注册表管理器，找到

`HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Run`

编辑里面的<span style="color: #ff0000;">avgnt</span> 项目，并在该项上点鼠标右键选择修改，在"/min"后加<span style="color: #ff0000;"> /nosplash</span>（/前面有一空格）,并点确定保存即可。如图：

![](4003885289_43b59c9499_o.jpg)

### （3）升级

> Update：现在 Avira 已经推出中文版了，这条基本可以无视了，除非你的 avira 升级太慢，或是根本无法升级可以考虑一下。
<del>如果觉得默认官方升级太慢 (否则就大可不必设置了，毕竟用代理的稳定性还是**O(∩_∩)O)，最新代理地址请关注 [http://www.avira.org.cn](http://www.avira.org.cn)</del>

<del>设置如下：</del>
<del> 代理升级 1(适合于 v7/v8/v9) <span style="color: #ff0000;">upd.avira.net.cn:808</span></del>
<del> 代理升级 2(适合于 v7/v8/v9)  <span style="color: #ff0000;">60.173.10.79:808</span> (建议在域名代理无法使用的时候使用)</del>