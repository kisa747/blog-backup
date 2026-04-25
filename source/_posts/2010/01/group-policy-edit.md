---
layout: post
title: 用组策略武装你的 Windows XP
date: 2010-01-30
tags: ["windows xp","技巧分享","组策略","配置"]
---

这个是针对 XP 系统。不用任何软件，XP 下就可以实现简单的 Hips 功效，对 U 盘的 Autorun.inf 之类的病毒还是很有效果的。关键是系统自带的，不用白不用。

### 设置效果：

1、设置 IE 浏览器的权限为"基本用户"

2、限制特定的文件格式在 C、D、E 盘的根目录下运行，而且严格禁止 F 盘及以后的所有盘下的所有文件禁止执行。

<!--more-->

### 操作步骤：

1、下载需要用到的文件。

【下载地址】：[group-policy.7z](https://dl.dropbox.com/u/3633907/download/group-policy.7z)

包含了："开启"基本用户"策略.reg"，"Registry.pol"，"使用方法"，共三个文件。

2、首先导入"开启"基本用户"策略.reg"，软件限制策略选项上多出一个"基本用户"选项

3、先任意创建一个软件策略。

先运行 gpedit.msc → 计算机配置 → windows 设置 → 安全设置 → 软件限制策略 → 右键随便创建一个软件策略。

![创建新的组策略](013001.gif "创建新的组策略")

如果没有这一步，则无法执行下一步。

4、将"Registry.pol"复制到"C:\WINDOWS\system32\GroupPolicy\Machine\"目录下。注意该文件夹为隐藏的。

5、然后在"命令提示符"里运行 **<span style="color: #0000ff;">gpupdate /force</span>** ，刷新一下策略，设置的策略就起效了，如果暂时未生效，等注销或重启后就会自动生效。

附："Registry.pol"组策略设置的内容如表：
<div>
<table border="1" cellspacing="0" cellpadding="0" align="center">
<tbody>
<tr>
<td width="355">名称</td>
<td width="183">安全级别</td>
</tr>
<tr>
<td width="355">%Program Files%\Internet Explorer\iexplore.exe</td>
<td width="183">基本用户</td>
</tr>
<tr>
<td width="355">?:\*.bat</td>
<td width="183">不允许的</td>
</tr>
<tr>
<td width="355">?:\*.cmd</td>
<td width="183">不允许的</td>
</tr>
<tr>
<td width="355">?:\*.com</td>
<td width="183">不允许的</td>
</tr>
<tr>
<td width="355">?:\*.exe</td>
<td width="183">不允许的</td>
</tr>
<tr>
<td width="355">?:\*.inf</td>
<td width="183">不允许的</td>
</tr>
<tr>
<td width="355">?:\*.lnk</td>
<td width="183">不允许的</td>
</tr>
<tr>
<td width="355">?:\*.msi</td>
<td width="183">不允许的</td>
</tr>
<tr>
<td width="355">?:\*.msp</td>
<td width="183">不允许的</td>
</tr>
<tr>
<td width="355">?:\*.pif</td>
<td width="183">不允许的</td>
</tr>
<tr>
<td width="355">?:\*.reg</td>
<td width="183">不允许的</td>
</tr>
<tr>
<td width="355">?:\*.scr</td>
<td width="183">不允许的</td>
</tr>
<tr>
<td width="355">?:\*.vbs</td>
<td width="183">不允许的</td>
</tr>
<tr>
<td width="355">?:\Recycle?\*</td>
<td width="183">不允许的</td>
</tr>
<tr>
<td width="355">?:\System Volume Information\*</td>
<td width="183">不允许的</td>
</tr>
<tr>
<td width="355">F:\*</td>
<td width="183">不允许的</td>
</tr>
<tr>
<td width="355">H:\*</td>
<td width="183">不允许的</td>
</tr>
<tr>
<td width="355">I:\*</td>
<td width="183">不允许的</td>
</tr>
<tr>
<td width="355">J:\*</td>
<td width="183">不允许的</td>
</tr>
<tr>
<td width="355">K:\*</td>
<td width="183">不允许的</td>
</tr>
<tr>
<td width="355">L:\*</td>
<td width="183">不允许的</td>
</tr>
<tr>
<td width="355">M:\*</td>
<td width="183">不允许的</td>
</tr>
<tr>
<td width="355">N:\*</td>
<td width="183">不允许的</td>
</tr>
<tr>
<td width="355">O:\*</td>
<td width="183">不允许的</td>
</tr>
<tr>
<td width="355">P:\*</td>
<td width="183">不允许的</td>
</tr>
</tbody>
</table>
</div>