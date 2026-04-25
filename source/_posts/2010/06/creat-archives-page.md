---
layout: post
title: 为 Wordpress 建立一个基于 jQuery 效果的存档页
date: 2010-06-09
tags: ["css","jquery","wordpress","wordpress"]
---

从这里看来的文章：[Create a Powerful jQuery-Powered Archives Page in Wordpress](http://themethesis.com/tutorials/jquery-wordpress-archives/)，觉得很好，实现效果可以看我的[文章存档](http://www.kisa747.com/archives)。

像 Easy Archives、Clean Archives Reloaded 等插件都可以实现类似的功能。然而用这个方法，只用几行代码就完全可以实现拉风的效果。而且这么简单的功能，就没用插件的必要了吧。

<!--more-->

### 实现方法：

首先复制一个你所使用主题的 single.php 或是 page.php，命名为 archives.php，并也放到主题根目录下。然后开始创建存档页的模板：

1、声明这是个模板文件，名字是 Custom Archives。

在 archives.php 的顶部添加：
```
<?php
/*
Template Name: Custom Archives
*/
?>
```

2、替换 content 内容：

找到类似这样的函数：

```
<?php the_content(); ?>
```

替换为：
```
<pre><div class="archive">
<?php
// 声明变量
$previous_year = $year = 0;
$previous_month = $month = 0;
$ul_open = false;
// 获取文章
$myposts = get_posts('numberposts=-1&amp;orderby=post_date&amp;order=DESC');
?>
<?php foreach($myposts as $post) : ?>
	<?php
 	global $post;
	// Setup the post variables
	setup_postdata($post);
	$year = mysql2date('Y', $post->post_date);
	$month = mysql2date('n', $post->post_date);
	$day = mysql2date('j', $post->post_date);
	?>
	<?php if($year != $previous_year '' $month != $previous_month) : ?>
		<?php if($ul_open == true) : ?>
		</ul>
		<?php endif; ?>
		<h3><?php the_time('F Y'); ?></h3>
		<ul>
		<?php $ul_open = true; ?>
	<?php endif; ?>
	<?php $previous_year = $year; $previous_month = $month; ?>
	<li><span class="the_article"><a href="<?php the_permalink(); ?>"><?php the_title(); ?></a></span></li>
<?php endforeach; ?>
	</ul>
</div></pre>
```
3、如果你的 header 已经加载过 jQuery 库，只需在 footer 里添加：
```
<pre><script type="text/javascript">
$(document).ready(function() {
  $('div.archive:eq(0)> ul').hide();
  $('div.archive:eq(0)> h3').click(function() {
    $(this).next().slideToggle('fast');
  });
});
</script></pre>
```
如果你还没加载过，还要在 header.php 里添加：

```
<script type="text/javascript" src="jquery.min.js"></script>
```

4、OK！然后就可以在 wordpress 后台新建一个页面，模板选用刚才建立的 Custom Archives。看看刚才建立的页面，效果是不是出来了。

当然了，可能还需要一点 CSS 美化，否则太难看了。
```
.archive {margin:1em 1em;display: block;}
.archive h3{font-size:14px;margin:10px 0;color:#2970A6;}
.archive h3:hover{cursor:s-resize;color:#df0031;text-decoration:none;}
.archive li a{padding:0.5em 2em;}
```