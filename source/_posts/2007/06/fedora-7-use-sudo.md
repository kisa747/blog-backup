---
layout: post
title: fedora 7 中也用 sudo 命令
date: 2007-06-30
categories: linux
tags: ["fedora","linux","sudo","设置"]
---

1，将当前用户加入 sudoer 组中，以根用户运行

`echo 'your_user_name ALL=(ALL) ALL' >> /etc/sudoers`

其中 your_user_name 为要加入 sudoer 中的用户名

<!--more-->

或是直接编辑/etc/sudoers

`~su -
#visudo`

用法跟 vi 一样

在最后一段添加

`your_user_name ALL=(ALL) ALL`