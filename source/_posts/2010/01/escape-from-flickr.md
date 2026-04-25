---
layout: post
title: A 计划逃离 Flickr
date: 2010-01-23
tags: ["flickr","wordpress","wordpress","数据库"]
---

![A 计划逃离 Flickr](012306.jpg "A计划逃离Flickr")前一段时间我去鄂尔多斯玩，用朋友的电脑上网打开我的博客，发现无法显示博客上的图片，一片的红叉啊。忙问他用的网络是什么线路，竟是神奇的中国移动线路。看来不仅只有我的手机移动 GPRS 无法访问 Flickr，还有众多朋友的 Flickr 在墙外啊。所以决定将图床迁移到本地主机上，亲自管理图片。准备实施 A 计划逃离 Flickr！

要彻底脱离 Flickr 图床，这么优秀的图片服务，十分不舍得。可如今河蟹肆虐，还是自己管理图片，心里比较踏实。

<!--more-->

PS：我是十分懒于自己管理一大堆的图片，很喜欢将图片仍到 Flickr 上，那样眼不见心不烦。但左思右想，决定长痛不如短痛，还是早点动手逃离 Flickr 图床。

### 1、下载所有 Flickr 上的图片

Flickr 的第三方应用真是多，有各种各样的软件，都能将 Flickr 账户上的图片全部下载回来。但普遍存在一个问题，就是下载后的图片格式一律变为了"jpg"，尽管只是更改了后缀名，并不影响使用，但仍是不爽。

偶然发现了 quickrpickr 这个网站，很方便就能将 Flickr 账户上的图片全部下载回来。

①、打开：[http://quickrpickr.com/users/kisa747/1000](http://quickrpickr.com/users/kisa747/1000 "http://quickrpickr.com/users/kisa747/1000")

②、点击上面的"Check All"，选中所有图片。

③、size 选 original，选择原始大小图片。

④、点击下面的"Generate HTML from Selected Photos and Descriptions"

![](012307.jpg)⑤、然后就生成了包含所有原始大小图片的一页，想要下载所有的图片，想到方法了吧！对，直接保存整个网页就行了。

⑥、保存后，在"quickr pickf_files"文件夹里面，包含了所有的 Flickr 图片，由于 Flickr 上的图片的文件名是又长又奇特，很容易识别，删除多余的图片就行了。

### 2、上传图片至服务器

得到了 Flickr 上的所有图片，将所有图片上传至

`http://localhost/img/2009/`

至于具体位置，这个随便，个人爱好而已。

### 3、博客上的 Flickr 链接的地址

Flickr 上图片的地址如下格式：
<pre>http://farm3.static.flickr.com/2689/4270934953_575e1cf34c_o.jpg
http://farm4.static.flickr.com/3498/4059005105_a665631988_o.gif
http://farm5.static.flickr.com/4023/4271682380_11dc96b5f2_o.jpg</pre>
![](012308.gif)

要将图片地址修改为以下形式：

`http://localhost/img/2009/4270934953_575e1cf34c_o.jpg`

从图示可以明显看出地址中有哪些地方需要修改，本来猜测 Mysql 应该支持通配符替换，可惜不行。无奈只有导出数据库，用工具替换内容了。

### 4、修改数据库中的链接地址

①、MyAdmin，导出数据库"kisa747.sql"，并备份。

②、用 Notepad2 打开以"kisa747.sql"结尾的数据库文件。

Notepad2 介绍及下载地址请看：[建立 wordpress 博客系列（1）](http://www.kisa747.com/build-wordpress-01.html)

③、快捷键"Ctrl+H"，注意选中"正则表达式"选项，然后开始替换。

将：

`http://farm[0-9].static.flickr.com/[0-9][0-9][0-9][0-9]/`

全部替换为：

`http://localhost/img/2009/`

如图：

![](012305.jpg)

④、将修改后的"kisa747.sql"导入数据库。

大功告成！所有图片地址替换完毕，成功实施 A 计划逃离 Flickr，哦耶～