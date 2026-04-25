---
layout: post
title: 如何制作绿色版 Google Chrome
date: 2010-05-21
tags: ["chrome","diy","google","技巧分享","绿色版","谷歌浏览器","软件"]
---

由于 Chrome 默认采用的是在线安装形式，秉承 Google 软件的一贯风格，甚至无法自定义安装位置。各个版本的在线安装地址如下：

Chrome 稳定版（Stable）在线安装：【[点击这里](http://www.google.com/chrome/eula.html)】
Chrome 测试版（Beta）在线安装： 【[点击这里](http://www.google.com/chrome/eula.html?extra=betachannel)】
Chrome 开发版（Dev）在线安装： 【[点击这里](http://www.google.com/chrome/eula.html?extra=devchannel)】
Chromium 下载地址：【[点击这里](http://build.chromium.org/buildbot/snapshots/chromium-rel-xp/?O=D)】

通过上面的地址安装，显然 DIY 度不高。显然这是一个 Geeker 不愿看到的，所以本文主要介绍制作绿色的 Chrome，即使重装系统，仍可以使用，而且修改用户数据位置非系统盘。

<!--more-->

### 如何制作 Chrome 绿色版：

> PS：只有离线版的 Chrome 才可以做成绿色版。离线版 Chrome 不会自动更新。
1、下载 Chrome 离线安装包

①、稳定版下载：

Chrome 稳定版（Stable）：【[下载地址](http://www.google.com/chrome/eula.html?standalone=1)】

下载得到名为 ChromeStandaloneSetup.exe 的离线安装包。

②、Beta 版和 Dev 版下载：

首先要知道最新 Beta 版或 Dev 版 Chrome 的版本号，查看它的官方博客： [Chrome Releases Blog](http://googlechromereleases.blogspot.com/)，得到最新版的版本号（需翻墙）。取版本号第二个小数点的数字，比如 5.0.375.53 的下载地址就是：

[http://dl.google.com/chrome/install/375.53/chrome_installer.exe](http://dl.google.com/chrome/install/375.53/chrome_installer.exe)

下载得到名为 chrome_installer.exe 的离线安装包。

下面以 Google Chrome 5.0.375.38 为例，它的离线安装包是 chrome_installer.exe。

3、解压下载的离线安装包，并修改目录结构。
> PS：如果你的 winrar 无法解压，不要惊讶。安装 7-zip 即可。
> 
> 7-zip 官方主页地址：【[7-zip 官方主页](http://www.7-zip.org/)】
解压 chrome_installer.exe，得到一个名为 chrome.7z 的压缩文件。

再次解压，得到一个 Chrome-bin 文件夹。

剪切 Chrome-bin 里的 5.0.375.38 文件夹（其它版本的也是类似的名字）里面的所有文件到 Chrome-bin 文件夹下。

3、新建一个 D:\program\chrome 的文件夹，在 chrome 文件夹下新建一个名为：User Data 的文件夹。

然后将 Chrome-bin 文件夹剪切至 Chrome 文件夹下。

最终得到以下目录结构：

```
D:\PROGRAM\CHROME
├─Chrome-bin
│      ├─<span style="color: #0000ff;">chrome.exe</span>
│      ├─Dictionaries
│      ├─Extensions
│      ├─Locales
│      ├─Resources
│      └─Themes
└─User Data
```

4、为 Chrome-bin 文件夹下的 Chrome.exe 创建快捷方式到桌面。

接着，我们来自定义 Chrome 用户数据存放的位置（Chrome 默认的用户数据在 C 盘）。

修改 Chrome 的快捷方式的目标为：

```
"D:\PROGRAM\Chrome\Chrome-bin\chrome.exe" --user-data-dir="D:\program\chrome\User Data"
```

这样，Chrome 就会把数据存放在 chrome 文件夹下。

5、我们自己制作的 DIY 版的绿色版 Chrome 就诞生了。
> 缺点：DIY 的 Chrome 不会自动更新。
> 
> 如需更新绿色版的 Chrome，仅需手动下载新版 Chrome 的离线安装包，解压修改后替换原来的 Chrome-bin 文件夹。
> 
> 但对于经常恢复系统，追求软件稳定性，有计划更新软件的朋友，这种方法似乎更适合。