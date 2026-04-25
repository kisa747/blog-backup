---
layout: post
title: 让 firefox3 也兼容 2.0 的扩展
date: 2008-06-18
tags: ["firefox","扩展","技巧分享"]
---

让 firefox3 也兼容 2.0 的扩展

1. 地址栏里输入 about:config
2. 右键点击页面，新建 ->   <span style="color: #0000ff;">布尔</span> ，名称为 <span style="color: #0000ff;">extensions.checkCompatibility </span> 值为        <span style="color: #ff0000;">false</span>
3. 右键点击页面，新建 ->   <span style="color: #0000ff;">布尔</span> ，名称为 <span style="color: #0000ff;">extensions.checkUpdateSecurity </span>值为      <span style="color: #ff0000;">false</span>