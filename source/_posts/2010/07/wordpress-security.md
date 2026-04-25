---
layout: post
title: 轻松几招增强 wordpress 安全
date: 2010-07-23
tags: ["wordpress","wordpress","安全"]
---

![Wordpress Security 安全](img/2010/072301.jpg)

我们日常上网，一般都是动态 IP 上网，每次上网前，ISP 提供者随机分配一个 IP 地址，由于 IP 不停在变化，被 Hacker 盯上的概率很小。而我们的网站就大不相同了，网站的域名一般是固定的，而且 IP 地址是固定的，一旦被盯上，被黑的可能性很大，不是被植入恶意代码就是沦为肉鸡，所以加强网站的安全是很有必要的。

其实只需通过修改 .htaccess 和在主题的 functions.php 函数，就可以显著提高 wordpress 的安全性，很简单，但很有效。

<!--more-->

### 1、禁止访问 _.htaccess _文件

在网站根目录下的 _.htaccess_ 文件中加入如下代码：

```
<Files .htaccess>
order allow,deny
deny from all
</Files>
```

设置后，即可禁止任何人访问 _.htaccess_ 文件：

### 2、保护 _wp-config.php_ 文件

由于 _wp-config.php _文件记录了 Wordpress 的核心配置信息，例如：数据库用户名、密码，重要性不言而喻，所以限制对 _wp-config.php _的访问权限就变得尤为必要。

在网站根目录下的 _.htaccess_ 文件中加入如下代码：

```
<files wp-config.php>
order allow,deny
deny from all
</files>
```

修改后会即可拒绝任何人访问 _wp-config.php _文件。

### 3、禁止目录浏览

默认情况下，大多数主机允许目录列表。如果在浏览器的地址栏键入 http://www.***.com/wp-includes/ ，就会以列表形式看到该目录下的所有文件，无疑增加了网站的安全风险，因此我们要做的是就是设置禁止目录浏览。

在网站根目录下的 _.htaccess_ 文件中加入如下代码：

```
Options -Indexes
```

注意：修改后只是禁止目录浏览，并不会影响用户正常的访问这些文件。

### 4、删除登录 WordPress 后台失败时会显示的错误信息提示

作用不言而喻。在 _functions.php_ 中添加并添加如下代码：

```
//删除登录WordPress后台失败时显示错误信息提示
add_filter('login_errors',create_function('$a', "return null;"));
```

设置后，如果登录后台密码错误，不会显示任何错误信息提示。

### 5、删除 WordPress 版本号

默认 wordpress 会自动显示版本号，如果你的 wordpress 没有及时升级至最新版本，这无疑是向任何人暴露了自己的漏洞，因此终极的解决方法就是让它不显示 wordpress 的版本号。

在 _functions.php_ 中添加并添加如下代码：

```
//删除WordPress版本号
remove_action('wp_head', 'wp_generator');
```