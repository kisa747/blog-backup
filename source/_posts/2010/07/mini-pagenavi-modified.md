---
layout: post
title: Mini Pagenavi 强力修改版
date: 2010-07-22
tags: ["wordpress","wordpress","插件","翻页"]
---

看了 willin 大师的 [Mini pagenavi](http://kan.willin.org/?p=1323) 代码后，有种醍醐灌顶的感觉，惊叹原来代码可以写的这么简单，不仅实现同样的功能，而且要代码清晰易懂。仔细地研究了一番后，决定替换掉原来使用的代码。不过我比较喜欢分页显示固定的页数，于是决定进行强力修改。

修改后效果参看本站，其实跟之前代码实现的效果是一样一样的。

贴上代码：

<!--more-->

```php
// Mini Pagenavi 分页功能
function pagenavi( $p = 4 ){
global $paged, $wp_query, $max_page;
$max_page = $wp_query->max_num_pages;
if ( $max_page == 1 ) return; // 只有一页不用
if ( empty( $paged ) ) $paged = 1;
if($paged != 1){echo "<a href='" . get_pagenum_link(1) . "'>返回首页</a>"; }
previous_posts_link('上一页');
if ($max_page <= $p*2+1) {$i=1; $m=$max_page; }
elseif ($paged <= $p) {$i=1; $m=$p*2+1; }
elseif ( ($max_page-$paged) <= $p ) {$i=$max_page-$p*2; $m=$max_page; }
else { $i=$paged-$p; $m=$paged+$p; }
for ( $i; $i <= $m; $i++ ) {
if ($i == $paged) echo "<span class='current'>{$i}</span>";
else echo "<a class='page' href='" . get_pagenum_link( $i ) . "'>{$i}</a>";
}
next_posts_link('下一页');
if($paged != $max_page){echo "<a href='" . get_pagenum_link($max_page) . "'>最后一页</a>"; }
}
// -- END ----------------------------------------
```

嘿嘿，自我感觉代码更清爽了～ :mrgreen:

同理，在合适的地方通过插入：

```php
<div id="pagenavi"><?php pagenavi(4); ?></div>
```

括号中的参数 4，即固定显示 2×4=1=9 项的分页。

CSS 部分参考我的 CSS 样式：

```php
/*分页样式*/
#pagenavi{width:100%;height:36px;font-size:12px;line-height:36px;text-align:center;overflow:hidden;padding:1em 0;}
#pagenavi a, #pagenavi .current{padding:3px 8px;margin:2px;text-decoration:none;color:#888;border:1px solid #ccf;}
#pagenavi a:hover, #pagenavi .current{border:1px solid #356aa0;color:#356aa0;font-weight:bolder;}
```
