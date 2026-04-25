---
layout: post
title: gconf-editor  的设置
date: 2007-06-23
categories: linux
tags: ["editor","gconf","linux","图标","设置"]
---

介绍一下 gconf-editor  的设置
下面这个是设置在桌面显示的东东：

> /apps/nautilus/desktop/computer_icon_name   在桌面显示"我的电脑"名称
>
> /apps/nautilus/desktop/computer_icon_visible  是否在桌面显示"我的电脑"图标
>
> /apps/nautilus/desktop/trash_icon_visible         是否在桌面显示"垃圾箱"图标
>
> /apps/nautilus/desktop/volumes_visible             在桌面上显示已挂载的卷

/apps/panel/objiects/objiect-x

当那个 object-x 里面的 object _type 值为 menu-object，修改里面的 custom_icon 就是开始菜单的图标，改为自定义的路径。

且保证 use_custom_icon 为 true，则定制图标设置就被用作按钮的定制图标。如果为 false，则忽略定制图标设置。该设置只在对象类型为"菜单对象"或"抽屉对象"时才有效。附上几个好看的图标，是我在 gnomelook.org 上下的，[**Vista-Panel.zip**
](http://cid-6abece639ad907b9.skydrive.live.com/self.aspx/public/Vista-Panel.zip)

> /apps/metacity/global_keybindings
>
> /apps/metacity/keybinding_commands

这两个设置快捷键和快捷键对应的命令。