---
layout: post
title: 建立 wordpress 博客系列（2）
date: 2009-11-19 08:02
categories: wordpress
tags: ["easyphp","inove","wordpress","主题"]
---

在上一篇[建立 wordpress 博客系列（1）](../build-wordpress-01.html)里，在本地通过 EasyPHP 搭建的 PHP 和 MySQL 环境成功安装了 wordpress。就可以尽情地在本地折腾主题和插件啦！

我现在用的就是大名鼎鼎的 mg12 的 iNove 主题，插件 iNove 主题推荐安装的那几个插件我差不多都装了。

现在记下几点常用的设置。

### （1）开启 Apache 的 mod_rewrite 功能

通过开启 mod_rewrite 功能，实现 wordpress 的伪静态化，轻松去掉 URL 里的"index.php"。

右击任务栏通知区域的小 e 图标→配置→Apache，即开始编辑"httpd.conf"

1. 让 Apache 加载 mod_rewrite.so 模块，找到如下部分：

```
#LoadModule rewrite_module modules/mod_rewrite.so
```

去掉：`#LoadModule rewrite_module modules/mod_rewrite.so` 前的 #

2. 设置允许在任何目录中使用".htaccess"文件，找到如下部分：

```
# AllowOverride controls what directives may be placed in .htaccess files.
# It can be "All", "None", or any combination of the keywords:
#   Options FileInfo AuthConfig Limit
#
AllowOverride None
```

将 `AllowOverride None` 改为 `AllowOverride All`

至此就可以自由设置 wordpress 的固定链接格式了，我的固定链接格式是："%postname%.html"。

### （2）设置 inove 主题嵌入 Google 自定义搜索

以下参考自 Let's whisper 的  [美化 iNove 的 Google 自定义搜索](http://www.whisperer.name/2009/09/improve-the-google-custom-search-results-of-inove/)

1、登陆到[Google 自定义搜索](http://www.google.com/coop/cse/)，创建你的自定义搜索。

2、创建一个搜索结果模板。把下面代码保存为 cse.php，上传至 iNove 主题的文件夹（放到/themes/iNove/下）。（cse 意为 custom search engine，你可以换成其它。）
```php
<?php
/*
Template Name: cse
*/
?>
<?php get_header(); ?>
<div id="cse-search-results"></div>
<script type="text/javascript">
var googleSearchIframeName = "cse-search-results";
var googleSearchFormName = "cse-search-box";
var googleSearchFrameWidth =605;
var googleSearchDomain = "www.google.com";
var googleSearchPath = "/cse";
</script>
<script type="text/javascript"
src="show_afs_search.js"></script>
<?php get_footer(); ?>
```
var googleSearchFrameWidth =605 为搜索结果页面的宽度，iNove 默认的宽度是 605。

3、在 WordPress 中创建一个页面，比如我的地址为 http://www.kisa747.com/cse，标题为"搜索结果"，模板选择刚刚创建的 cse。

然后在导航栏隐藏这个页面，在 iNove 的文件夹下找到/templates/header.php，找到下面一行：

```php
wp_list_pages('title_li=0&sort_column=menu_order');
```

改成：

```php
wp_list_pages('title_li=0&sort_column=menu_order&exclude=41');
```

其中 exclude=41 意思是在导航栏隐藏这个 cse 页面，41 是这个页面的 ID，在/wp-admin/edit-pages.php 页面，鼠标悬浮在页面的标题上，在下面状态栏就可以看到 post=41。

4、定义搜索框。仍然是 templates/header.php，找到下面代码：

```php+HTML
<form action="http://www.google.com/cse" method="get">
<div class="content">
<input type="text" class="textfield" name="q" size="24" />
<input type="submit" class="button" name="sa" value="" />
<input type="hidden" name="cx" value="<?php echo $options['google_cse_cx']; ?>" />
<input type="hidden" name="ie" value="UTF-8" />
</div>
</form>
```
改成：

```php+HTML
<form action="<?php bloginfo('wpurl') ?>/cse" id="cse-search-box">
<div class="content">
<input type="hidden" name="cx" value="<?php echo $options['google_cse_cx']; ?>" />
<input type="hidden" name="cof" value="FORID:11" />
<input type="hidden" name="ie" value="UTF-8" />
<input type="text" class="textfield" id="searchtxt" name="q" size="24" />
<input type="submit" class="button" id="searchbtn" name="sa" value="" />
</div>
</form>
```

其中第一行的 `< ?php bloginfo('wpurl') ?>/cse` 是刚刚你创建的搜索结果页面的地址。

5、在 iNove 的主题选项中，勾选使用 Google 自定义引擎，填上你的 CX 值。

这样，所有的工作都做完了。你可以随时在 WordPress 默认搜索和 Google 自定义搜索之间进行切换。并且不需要再另外用 css 定义搜索框了，已经沿用原来的搜索框样式了。

Update：感谢为我留言的网友 [林](http://www.lanpoly.cn) ，热情地提醒我下面这个问题，并给出了解决方法。

设置 inove 主题嵌入 Google 自定义搜索后，在 IE6 下会出现导航条下面有条空白的错位，连搜索框内输入内容的地方都跑到了下面。


解决方法：是 CSS 的问题，修改 iNove 主题的 style.css 即可。只需要把搜索框的长度设置的短一点，IE6 下就完全正常了。

在 style.css 中找到以下：

```css
#searchbox .textfield {
background:none;
border:0px;
width:185px;
float:left;
margin-right:2px;
padding-left:2px;
}
```

将 width 值改为 183 即可。