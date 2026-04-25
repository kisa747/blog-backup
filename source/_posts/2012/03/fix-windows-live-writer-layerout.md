---
layout: post
title: 解决 Windows Live Writer 下页面错位问题
date: 2012-03-31
categories: 随笔
tags: ["css3","html5","ie","wordpress","wordpress","主题"]
---

最近经常修改主题，用 WLW 更新主题后，发现在 WLW 下编辑和预览页面显示错位，整个页面无法居中。起初推测 WLW 是调用 IE 的内核来显示网页的样式的，难道我的主题本来在 IE 下显示错位么？

于是赶紧调出 IE9 测试，发现显示一切正常啊。在 WLW 中预览显示没有 CSS3 的圆角，那 WLW 调用的肯定不是 IE9 内核了，可能是 IE8 了，现在最新版的 WLW 的发布时间应该是 2010～2011 之间。于是调出 IEtester，用 IE7、IE8 进行测试，也是显示正常，甚至在 IE6 下都正常。一下子没辙了，不知道 WLW 这货哪里抽筋了。

于是放狗搜，还没有任何结果。

<!-- more -->

就这样一直没有结果，反正也就是页面不居中，别的也没什么问题，对正常使用没有任何影响。本来也就放弃解决它了，那天在验证 HTML5 时，突然想到，莫非是 IE8 不支持 HTML5，才导致的页面错位？

我现在的主题为了支持 HTML5，header 的声明是现在的形式：

```html
<!DOCTYPE html>
<html>
```

赶紧把 header 里的声明修改为：

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
```

测试一下，一切恢复正常了。原来都是 IE8 不支持 HTML5 惹得祸。

这样的话，只要 WLW 更新主题前，先头部声明给修改一下就可以了。等 WLW 更新完主题后再恢复回来就行了。

![032501](img/2012/032501.png)