---
layout: post
title: 社会化分享按钮代码
date: 2010-02-01
tags: ["wordpress","wordpress","代码","分享","插件"]
---

之前使用过许多社会化分享的插件，后来转用 Add Bookmarks 插件，不过插件已经很老了，好多的按钮都已失效，而且又好多的估计已经没有在使用了。靠人不如靠自己，最终决定亲自对它进行大修。

其实挺简单的，根本不用插件，直接用代码就可以实现该功能。除了 Twitter 全是 Java 弹出窗口模式，尽管代码麻烦，但感觉弹出窗口模式很酷，我很喜欢。

使用方法：下载 sharelink.7z，解压得到 sharelink.php 和 sharelink 文件夹，上传至主题根目录下，然后在主题合适的地方通过下面的代码调用。

<!--more-->

`<?php get_template_part( 'sharelink' ); ?>`

【下载地址】：[sharelink1.3.7z](https://dl.dropbox.com/u/3633907/download/sharelink1.3.7z)
> _Update:2012-02-26_，删除了 Google Reader 分享和 Google Buzz 按钮，修改了 include 方式。
> 
> _Update:2010-09-22_，添加了腾讯微博转发按钮。
> 
> _Update：2010-07-02_，更新为单独的 php 文件和图标文件夹，放到主题内，方便调用。
> 
> _Update_：新增了 Google Buzz 转发按钮。
sharelink.php 里的代码如下：

`
<style type="text/css">
.sharelink {margin-right:3px;}
</style>
» 收藏 + 分享：
<!-- Delicious -->
<a href="http://delicious.com/save" onclick="window.open('http://delicious.com/save?v=5&noui&jump=close&url='+encodeURIComponent('<?php the_permalink() ?>')+'&title='+encodeURIComponent(document.title), 'delicious','toolbar=no,width=550,height=550,left=50,top=50,'); return false;">![Delicious](delicious.ico "收藏到Delicious")</a>
<!-- Google -->
<a href="javascript:window.open('http://www.google.com/bookmarks/mark?op=add&bkmk='+encodeURIComponent('<?php the_permalink() ?>')+'&title='+encodeURIComponent(document.title)+'&jumpback=2&noui=1','favit','width=800,height=600,left=50,top=50,toolbar=no,menubar=no,location=no,scrollbars=yes,status=yes,resizable=yes');void(0)">![Google](google.ico "添加到Google书签")</a>
<!-- facebook -->
<a href="javascript:window.open('http://www.facebook.com/share.php?u='+encodeURIComponent('<?php the_permalink() ?>')+'&t='+encodeURIComponent(document.title)+'&jumpback=2&noui=1','favit','width=800,height=600,left=50,top=50,toolbar=no,menubar=no,location=no,scrollbars=yes,status=yes,resizable=yes');void(0)">![facebook](facebook.ico "分享到facebook")</a>
<!-- Live -->
<a href="javascript:window.open('https://skydrive.live.com/sharefavorite.aspx/.SharedFavorites/?url='+encodeURIComponent('<?php the_permalink() ?>')+'&title='+encodeURIComponent(document.title)+'&jumpback=2&noui=1','favit','width=640,height=600,left=50,top=50,toolbar=no,menubar=no,location=no,scrollbars=yes,status=yes,resizable=yes');void(0)">![Live 收藏夹](live.gif "添加到Live收藏夹")</a>
<!-- baidu -->
<a href="javascript:window.open('http://cang.baidu.com/do/add?it='+encodeURIComponent(document.title.substring(0,76))+'&iu='+encodeURIComponent('<?php the_permalink() ?>')+'&fr=ien#nw=1','_blank','scrollbars=no,width=600,height=450,left=50,top=50,status=no,resizable=yes'); void 0">![百度搜藏](baidu.gif "搜藏到百度搜藏")</a>
<!-- QQ -->
<a href="javascript:window.open('http://shuqian.qq.com/post?from=3&title='+encodeURIComponent(document.title)+'&uri='+encodeURIComponent('<?php the_permalink() ?>')+'&jumpback=2&noui=1','favit','width=930,height=470,left=50,top=50,toolbar=no,menubar=no,location=no,scrollbars=yes,status=yes,resizable=yes');void(0)">![QQ 书签](qq.ico "收藏到QQ书签")</a>
<!-- renren -->
<a href="javascript:window.open('http://share.renren.com/share/buttonshare.do?link='+encodeURIComponent('<?php the_permalink() ?>')+'&title='+encodeURIComponent(document.title)+'&jumpback=2&noui=1','favit','width=600,height=400,left=50,top=50,toolbar=no,menubar=no,location=no,scrollbars=yes,status=yes,resizable=yes');void(0)">![人人网](renren.ico "分享到人人网")</a>
<!-- kaixin -->
<a href="javascript:window.open('http://www.kaixin001.com/~repaste/repaste.php?rtitle='+encodeURIComponent(document.title)+'&url='+encodeURIComponent('<?php the_permalink() ?>')+'&jumpback=2&noui=1','favit','width=930,height=470,left=50,top=50,toolbar=no,menubar=no,location=no,scrollbars=yes,status=yes,resizable=yes');void(0)">![开心网](kaixin.ico "分享到开心网")</a>
<!-- douban -->
<a href="javascript:window.open('http://www.douban.com/recommend/?url='+encodeURIComponent('<?php the_permalink() ?>')+'&title='+encodeURIComponent(document.title)+'&jumpback=2&noui=1','favit','width=600,height=400,left=50,top=50,toolbar=no,menubar=no,location=no,scrollbars=yes,status=yes,resizable=yes');void(0)">![豆瓣](douban.ico "推荐到豆瓣")</a>
<!-- 饭否 -->
<a href="javascript:var d=document,w=window,f='http://fanfou.com/share',l=d.location,e=encodeURIComponent,p='?u='+e(l.href)+'?t='+e(d.title)+'?d='+e(w.getSelection?w.getSelection().toString():d.getSelection?d.getSelection():d.selection.createRange().text)+'?s=bl';if(!w.open(f+'r'+p,'sharer','toolbar=0,status=0,width=640,height=440')){l.href=f+'.new'+p;}void(0)">![饭否](fanfou.gif "分享到饭否")</a>
<!-- 腾讯微博 -->
<a href="javascript:window.open('http://v.t.qq.com/share/share.php?title='+encodeURIComponent(document.title)+'&url='+encodeURIComponent('<?php the_permalink() ?>')+'&jumpback=2&noui=1','favit','width=600,height=400,left=200,top=50,toolbar=no,menubar=no,location=no,scrollbars=yes,status=yes,resizable=yes');void(0)">![腾讯微博](tencent.ico "转发到腾讯微博")</a>
<!-- Sina -->
<a href="javascript:window.open('http://v.t.sina.com.cn/share/share.php?title='+encodeURIComponent(document.title)+'&url='+encodeURIComponent('<?php the_permalink() ?>')+'&jumpback=2&noui=1','favit','width=640,height=400,left=200,top=50,toolbar=no,menubar=no,location=no,scrollbars=yes,status=yes,resizable=yes');void(0)">![新浪微博](sina.ico "转发到新浪微博")</a>
<!-- Twitter -->
<a href="http://twitter.com/home?status=<?php the_title(); ?> « <?php bloginfo('name'); ?>+-+<?php the_permalink() ?>+" target="_blank">![Twitter](twitter.ico "转发到Twitter")</a>`

&nbsp;