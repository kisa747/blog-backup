---
layout: post
title: FUCK，网站被人插了！
date: 2012-04-08
categories: wordpress
tags: ["wordpress","安全","密码","心情随笔","数据库"]
---

昨晚上突然发现博客 wp-config.php 里被插了一段代码，原代码如下：

```php
eval(base64_decode("DQplc>>>>=="));
```

解码后包含有 `http://minkof.sellclassics.com/` 这个网址。

也懒的研究这段代码什么含义了，还好影响不大。于是直接直接 K 掉所有文件和数据库，重新安装 wordpress，免得不知道哪里还有被插的地方。折腾了 1 个多小时才终于搞定。

<!-- more -->

网上随便一搜，还真有人遇到和我一模一样的情况，这位 [妹纸](http://www.mintrix.net/blog/2012/04/04/damn-you-hackers-go-to-hell/) 的火气还很大，直接就破口骂了。

![040801](img/2012/040801.jpg)![040802](img/2012/040802.jpg)

还看到了另一篇文章，不仅详细讲了清楚类似 (eval(base64_decode) 的方法，而且还讲了 wordpress 应注意的安全事项，以免再次被黑，原文：[WordPress Security](http://designpx.com/tutorials/wordpress-security/) -Protect your WordPress blog from being hacked by (eval(base64_decode); Tips for WordPress security; make your WordPress blog secure from hackers.。

我就不翻译了，下面是如何清除恶意代码：

### 一、清除所有的恶意代码

这次我的只是 config.php 被注入了代码，其实直接删除恶意代码即可，但如果是每个 php 文件都被注入了代码，逐个删除显然不大可能。如果每个 php 文件的头部都出现以下代码：

```php
<?php eval(base64_decode("aWYoZnVuY3Rpb25fZXhpc3RzKCdvYl9zdG.......
```

解决方法很简单，首先下载下面的文件：

【下载地址】：[wordpress-fix.7z](http://dl.dropbox.com/u/3633907/download/wordpress-fix.7z)

解压后上传至网站的根目录，然后在浏览器里进入 _http://yoursite.com/wordpress-fix.php_，稍后直至看到下面的提示就说明成功了。

> **You are now malware free.**
> Everything _should_ be in working order.

### 二、加强你的 wordpress 安全

经过上一步的清理，可以确定恶意代码已经被清除了。为了安全起见，你还应该进行以下操作：

**1、重新设置 Wordpress 密码**

重设包括 FTP、SFTP，数据库以及 Wordpress 后台等在内的所有密码，不要忘了重设数据库密码后，记得修改你的"wp-config.php"文件。

**2、修改 Secret Keys**

即使网站入侵者通过某种途径获得了你的密码，然后你即使更换了密码，他们仍旧可以通过 cookies 访问你的管理面板。重设 secret keys 会强制所有的用户登录失效，必须重新登录。

通过这个网址，你可以获取唯一的 secret keys: [https://api.wordpress.org/secret-key/1.1/salt/](https://api.wordpress.org/secret-key/1.1/salt/)

上面的页面会自动生成一个唯一的 secret keys，替换掉 config.php 原来对应的 keys 即可。

**3、设置文件的权限**

要确保你的网站上文件夹默认是 755，文件的默认权限是 644。

<span style="color: #ff0000;">修改 wp-config.php 的权限为 400。</span>（设置后将无法再编辑，若要编辑它的内容，必须先修改权限后才可以进行编辑，这样可以最大限度保证安全。）

**4、更改 WordPress 数据库表名的前缀**

在你的 wordpress 的 wp-config.php 文件里找到以下行：

`$table_prefix  = 'wp_';`

默认为表名的前缀为"wp_"，你可以修改为任意值，例如：

`$table_prefix  = 'wp786$&9#@_';`

如果不是第一次安装 worpdress，可不能这样简单的修改，具体修改方法参见水煮鱼的[ WordPress 技巧：如何修改 WordPress 数据库前缀](http://fairyfish.net/m/how-to-change-the-wordpress-database-prefix/)

更多的 wordpress 安全技巧可以查看：**[轻松几招增强 wordpress 安全](http://www.kisa747.com/wordpress-security.html)**。

其余像使用高强度密码，用杀毒软件全盘扫描电脑，升级 Wordpress 为最新版本，这些技巧就无需再多讲了，有了一次被黑的经历，以后就更要小心了。

最后咒那些乱黑人家网站的都木有小 JJ。