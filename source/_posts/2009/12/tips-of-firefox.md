---
layout: post
title: Firefox 使用技巧汇总
date: 2009-12-14
tags: ["firefox","技巧","技巧分享","软件"]
---

kisa747 用 firefox 这个可爱的小狐狸已经有 3 年了，最早从 1.5 版到现在的 3.5 版，亲眼看着 firefox 的成长，如今 chrome 是强势来袭，怕是再不写关于 firefox 的应用，很快 chrome 即将成为我的主浏览器了。

<!--more-->

### 一、安装

当然推荐安装官方的简体中文版，官方下载地址：
> [http://www.mozilla.com](http://www.mozilla.com/ "http://www.mozilla.com/")或[http://www.mozillaonline.com](http://www.mozillaonline.com/)
下载中文最新版，不要安装"火狐中国版"，里面带了一大堆无用的插件。

安装插件：

1、[Super Tab Mode](https://addons.mozilla.org/zh-CN/firefox/addon/13288)

这个必装。轻量级的标签增强工具，还有其它多种个性功能：老板键迅速隐藏 firefox，屏蔽图片和广告，设置 firefox 缓存移到虚拟硬盘。

2、[Coral IE Tab](https://addons.mozilla.org/zh-CN/firefox/addon/10909)

添加一个临时切换为 IE 的按钮。IETab 的增强版本，除具备 IETab 的全部功能外，还可以在 IE 引擎中用 Adblock Plus 过滤广告，以及同步 Cookie 使得切换到 IE 引擎时不需要重新登录。

3、[FireGestures](https://addons.mozilla.org/zh-CN/firefox/addon/6366/)

鼠标手势扩展。

4、[Firefox Sync](https://addons.mozilla.org/zh-CN/firefox/addon/10868/)

Mozilla 官方出品的同步书签、设置等的扩展。

更多的扩展可以查看：[我收藏的 Firefox 扩展](https://addons.mozilla.org/zh-CN/firefox/collection/kisa747)

### 二、外观设置

![](4180906191_855d42dfd5_o.jpg)

上一步中，点击"定制"，可以设置工具栏。

[![](http://localhost/img/2009/4181669628_dd94c81920_o.gif)](4181669628_dd94c81920_o.gif)

最终达到这个效果

[![](http://localhost/img/2009/4181669700_e349cd71d4_o.gif)](4181669700_e349cd71d4_o.gif)

### 三、扩展设置

其中的 Tab Mix Lite CE 还是需要设置一下才能符合使用习惯。

在菜单的"工具"--"附加组件"--"扩展"

![](4180906269_849b84c32c_o.gif)

![](4181669412_e6ba5e51ba_o.gif)

默认的 Google 搜索地址是 http://www.google.com/firefox，十分不爽。

修改安装目录下的 searchplugins\google.xml
> 查找"http://www.google.com/firefox"替换为" http://www.google.com/ "即可。
其实 firefox 的搜索还可安装 Google.cn，作为 Google.com 被重置时的临时替代品。在附加组件里面找了半天，竟没找到，一怒之下，自己做了一个，不就是个搜索嘛。
> 安装地址：[Google.com.hk 谷歌中国搜索](https://addons.mozilla.org/zh-CN/firefox/addon/54454/)

### 四、修改配置文件到其它盘

默认火狐的配置都会在系统盘，如何设置配置文件到其它盘，以避免重装系统后配置丢失？

其实只要修改下火狐的快捷方式就行了

1、现在 D 盘创建"firefox-profile"文件夹，作为配置文件的位置。

即 d:\firefox-profile

2、右击火狐的快捷方式--"属性"

修改目标项目，在 firefox.exe 后面添加 <span style="color: #ff0000;">-profile "D:\firefox-profile"</span> 的选项

以后随便重装系统，所有配置都在 D 盘。不过打开火狐要用这个修改过的快捷方式哦！

![](4181169681_c5dee325fd_o.jpg)

3、删除多余的右键菜单选项 → "<span style="color: #ff0000;">在新窗口打开 (W)</span>"

找到以下位置，编辑 serChrome.css，如果没有自己动手新建一个
> D:\firefox-profile\chrome\userChrome.css
添加以下内容：

`#context-openlink { display:none !important; }`

效果如图：

![](4184356796_d1f94b8193_o.jpg)

如果要更高级地编辑右键菜单，可以参考[这里](http://wiki.mozcn.org/index.php/Firefox:%E5%88%A0%E9%99%A4%E5%A4%9A%E4%BD%99%E7%9A%84%E5%8F%B3%E9%94%AE%E8%8F%9C%E5%8D%95%E9%80%89%E9%A1%B9)，也可以直接安装[Menu Editor](https://addons.mozilla.org/zh-CN/firefox/addon/710)这个扩展。

通过修改 userChrome 来实现 Firefox 自定义界面可以查看该文件  [userchrome.css](http://dl.dropbox.com/u/3633907/file/userchrome.css)