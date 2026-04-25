---
layout: post
title: Windows 7 小技巧与设置
date: 2010-04-21
tags: ["windows 7","代码","技巧","技巧分享","注册表"]
---

> PS：今天是默哀日，让我们为玉树的人民祈福。
> 
> 等捐款时，再贡献一点我的力量，我所能作的只能是这些了。
像我这种 XP 重度用户，必须要找到 Win 7 的许多优点，才会死心塌地的使用 win 7。所以嘛，我就不断探索它的新功能和一些设置，逐渐找到以前的那种感觉。

之前的[Windows 7 三个小技巧](http://www.kisa747.com/3-tips-of-win7.html)文章里已经提到了 Windows 7 的几个小问题的解决方法。其实 win 7 有更多很拉风的功能。

<!--more-->

### 1.、窗口管理

①、拖动窗口放到到屏幕的左边、右边、顶部三个边缘，就能把实现 dock 到屏幕的左半边、右半边、最大化窗口的拉风效果。

②、上下调整窗口大小，拖到顶部或下部边缘位置时，会自动高度最大化。

③、拖住一个窗口晃一晃，即可最小化其它窗口。或者是猛击 Win+Home 键。

尤其是靠左、右 dock 的特性在宽屏上特别有用。

### 2、windows 移动中心

如果是笔记本，右击右下角电源或电池图标，打开 windows 移动中心。包括：连接显示器、屏幕亮度、无线网络等设置选项。

连接显示器这个功能很方便，只要猛击"Win+P"快捷键即可直接唤出该界面。

![](img/2010/042101.gif)

> PS：该功能还有另外一个用处，设置宽屏为 4:3。
> 
> 比如当用宽屏笔记本全屏玩跑跑卡丁车时，画面比例会被破坏，而笔记本没有显示器的设置选项。这时设置连接显示器为"复制"，画面比例即可变为 4:3。

### 3、在此处打开命令窗口

Windows 7 根本不用任何设置或修改，只需在资源管理器中，按住 shift，右键空白处，即可在当前目录下打开命令行。

### 4、快速复制文件路径

选中要操作的文件，按住 shift，然后右击->"复制为路径"即可。

### 5、资源管理器临时显示经典菜单栏

在资源管理器窗口下，按"ALT：键，即可让资源管理器临时显示经典菜单栏。

### 6、转移"用户的文件"

进入"C:\用户\你的用户名"，在需要转移的文件夹上，右击→属性→位置→转移。

推荐转移这 4 个用户文件夹：我的文档，桌面，我的图片、我的音乐。

### 7、设置自动登录

这个设置对 XP 也有效。

猛击"Win+R"快捷键，打开"运行"对话框，输入 "control userpasswords2"

在弹出的对话框中选中你打算自动登陆的用户，然后将上面的那个"要使用本机，用户必须输入用户名和密码"的复选框取消。点击应用，就会又出现一个设置密码的对话框，输入密码，确认即可。

### 8、为文件属性添加"文件校验"

其实只是注册了一个"hashtab.dll"而已。

【下载地址】：[hashtab.7z](https://dl.dropbox.com/u/3633907/download/hashtab.7z)

### 9、右键添加"管理员取得所有权"

Windows 7 采用了更高级的权限管理（这是相对于 XP、vista 来说。然而相对于 Linux 的权限管理，这仍旧是小儿科），在系统盘里面，许多文件即使管理员帐户都无法对其进行修改和删除。这时，这个小功能就派上用户场了，通过右键可以取得文件夹和文件的权限。

注册表代码如下，复制代码保存为"*.reg"，双击导入即可。或是直接下面的注册表文件。
```
Windows Registry Editor Version 5.00

[HKEY_CLASSES_ROOT\*\shell\runas]
@="管理员取得所有权"
"NoWorkingDirectory"=""
"Icon"="imageres.dll,-78"

[HKEY_CLASSES_ROOT\*\shell\runas\command]
@="cmd.exe /c takeown /f \"%1\" && icacls \"%1\" /grant administrators:F"
"IsolatedCommand"="cmd.exe /c takeown /f \"%1\" && icacls \"%1\" /grant administrators:F"

[HKEY_CLASSES_ROOT\exefile\shell\runas2]
@="管理员取得所有权"
"NoWorkingDirectory"=""
"Icon"="imageres.dll,-78"

[HKEY_CLASSES_ROOT\exefile\shell\runas2\command]
@="cmd.exe /c takeown /f \"%1\" && icacls \"%1\" /grant administrators:F"
"IsolatedCommand"="cmd.exe /c takeown /f \"%1\" && icacls \"%1\" /grant administrators:F"

[HKEY_CLASSES_ROOT\Directory\shell\runas]
@="管理员取得所有权"
"NoWorkingDirectory"=""
"Icon"="imageres.dll,-78"

[HKEY_CLASSES_ROOT\Directory\shell\runas\command]
@="cmd.exe /c takeown /f \"%1\" /r /d y && icacls \"%1\" /grant administrators:F /t"
"IsolatedCommand"="cmd.exe /c takeown /f \"%1\" /r /d y && icacls \"%1\" /grant administrators:F /t"
```

【注册表文件下载】：[administrator.reg.7z](https://dl.dropbox.com/u/3633907/download/administrator.reg.7z)

### 10、右键"用记事本编辑"

对于任意的文件，都可以直右键用记事本进行编辑，很方便。

注册表代码如下，复制代码保存为"*.reg"，双击导入即可。或是直接下面的注册表文件。
```
Windows Registry Editor Version 5.00

[HKEY_CLASSES_ROOT\*\shell\notepad]
@="用记事本编辑"
"Icon"="SHELL32.dll,-152"

[HKEY_CLASSES_ROOT\*\shell\notepad\command]
@="C:\\windows\\system32\\notepad.exe %1"
```

【注册表文件下载】：[notepad.reg.7z](https://dl.dropbox.com/u/3633907/download/notepad.reg.7z)

11、关闭视频预览的缩略图

默认 Win 7 的资源管理器会将支持的视频文件，显示为缩略图。完全的鸡肋功能，而且当文件夹下视频文件过多时会很卡，而且很容易导致资源管理器假死。所以最好直接 K 掉这个功能。

```
Windows Registry Editor Version 5.00
[-HKEY_CLASSES_ROOT\.mp4\ShellEx]
[-HKEY_CLASSES_ROOT\.m4v\ShellEx]
[-HKEY_CLASSES_ROOT\.wmv\ShellEx]
[-HKEY_CLASSES_ROOT\.avi\ShellEx]
[-HKEY_CLASSES_ROOT\.asf\ShellEx]
[-HKEY_CLASSES_ROOT\.mpg\ShellEx]
[-HKEY_CLASSES_ROOT\.mkv\ShellEx]
[-HKEY_CLASSES_ROOT\.rmvb\ShellEx]
[-HKEY_CLASSES_ROOT\.rm\ShellEx]
[-HKEY_CLASSES_ROOT\.flv\ShellEx]
[-HKEY_CLASSES_ROOT\.mov\ShellEx]
[-HKEY_CLASSES_ROOT\.dat\ShellEx]
```

12、"打开方式"窗口，禁用提示"在互联网上搜索"

如果你尝试过更换一个文件的打开方式的话，你会发现 win7 多么的打击人。首先它会弹出一个在互联网搜索的界面，且不说这个功能有多蛋疼，关键是它慢慢搜索后，结果仍然是提示没有搜索到打开的程序。所以直接 K 掉这个功能，让选择打开方式时直接切换到本机已有的程序列表。

```
Windows Registry Editor Version 5.00
;"NoInternetOpenWith"=dword:00000000
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer]
"NoInternetOpenWith"=dword:00000001
```

四、删除创建快捷方式后的"快捷方式"字样

```
Windows Registry Editor Version 5.00
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer]
"link"=hex:00,00,00,00
```