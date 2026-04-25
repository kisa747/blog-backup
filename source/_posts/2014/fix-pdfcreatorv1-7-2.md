---
layout: post
title: 解决 PDFCreator(v1.7.2）打印为空白页
date: 2014-05-14
categories: windows
tags: ["pdf", "打印", "技巧分享"]
---

最近的几个版本的 PDFCreator 一直都存在这个问题，就是打印后的 PDF 文档一片空白，什么也没有，网上随便搜了搜，说是因为文件名、路径之类的含有中文名的原因，太扯了，这么低级的 BUG 到现在还没有修复。

看来只有自己动手修复了，网上已经有人找到了解决方法：[關於 PDFCreator (v1.7.1) 列印空白頁之解決辦法](http://mt-tp-tw.blogspot.com/2013/09/pdfcreator-v171.html)

不过是台湾的朋友文章，我们自然是无福看到了。我就顺便帮忙转了过来。

<!-- more -->

打开 PDFCreator--选项，找到 "动作"--"保存前动作"

勾选"保存前动作"后，在"程序/脚本"下面浏览找到以下文件：

> C:\Program Files\PDFCreator\Scripts\RunProgramBeforeSaving\AddBookmarks.vbs

点击"保存"，OK，一切搞定，随便找个文档或是图片打印下试试，果然正常打印。

![fix-pdfcreatorv1-7-2](img/2014/051401.jpg)
