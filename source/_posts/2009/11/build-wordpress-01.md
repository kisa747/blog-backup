---
layout: post
title: 建立 wordpress 博客系列（1）
date: 2009-11-19 08:01
categories: wordpress
tags: ["easyphp","notepad2","wordpress","安装"]
---

建立这个博客，从有这个想法到付诸行动，可花了我不少的时间。之前没弄过 wordpress，自然想到了先在自己电脑上搭建个本地服务器来测试下，再考虑下一步购买域名和空间，免得到时候不会弄。

我选择了 EasyPHP 这个软件来在我的 windows XP 上搭建了一个 PHP 和 MySQL 环境。

废话不多说了，下面就开始动手吧。

准备软件：

[EasyPHP](http://www.easyphp.org/download_easyphp.php)

[wordpress 中文版](http://cn.wordpress.org/)

[Notepad2-4.0.23 中文版](https://dl.dropbox.com/u/3633907/download/notepad2.7z)

> 注：EasyPHP 一般下载中间那个 recommended version 就行了，就是推荐的版本。
> 
> Notepad2→我用它来编辑 wordpress 下的 php 和 css 文件
> 
> Notepad2 可是很好很强大哦，可以自由切换 LF，CR，CR+LF 的换行模式，自由更改编码（如 ANSI，UTF-8），支持语法高亮。程序本身也十分的小巧
> 
> 建议下面在修改 PHP 文件时用**<span style="color: #ff0000;">UTF-8 编码</span>**，
（1）安装 EasyPHP

一步步安装 EasyPHP。安装完成后，更改语言为中文

右击任务栏通知区域的小 e 图标→Configuration→EasyPHP→Language→Chinese，更改默认语言为中文。

打开浏览器，在地址栏中输入 `http://localhost/home/mysql/`

进入 phpAdmin 界面，（用[http://127.0.0.1/home/mysql/](http://127.0.0.1/home/mysql/)也可以），然后按下面的步骤操作。


（2）建立 wordpress 的数据库

在 phpAdmin 下创建用户

（3）创建数据库

（4）配置 wordpress
> PS:这一步非必需步骤，可以直接调至第五步。如果懒得配置 wp-config.php，则在第五步会提示你填写数据库名和用户名，然后自动生成新的 wp-config.php 文件。
将 WordPress 的安装文件解压后放在 EasyPHP 安装目录的 www 文件夹下，重命名 wp-config-sample.php 为 wp-config.php，并用 notepad2 编辑 wp-config.php 文件（强烈建议用 UTF-8 编码），加入刚才建立的数据库的用户名和密码。

```php
// ** MySQL 设置 - 具体信息来自您正在使用的主机 ** //

/** WordPress 数据库的名称，我的为"wordpress" */
define('DB_NAME', 'wordpress');

/** MySQL 数据库用户名，我的为"kisa747" */
define('DB_USER', 'kisa747');

/** MySQL 数据库密码，替换掉 "你的密码" */
define('DB_PASSWORD', '你的密码');

/** MySQL 主机名 */
define('DB_HOST', 'localhost');
```
（5）开始安装 wordpress

在浏览器中输入  [http://localhost/](http://localhost/)

进入 wordpress 的安装界面

接着就可以一步步安装属于自己的 wordpress 喽！