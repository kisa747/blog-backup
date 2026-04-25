---
layout: post
title: 解决了 vsftpd 的配置
date: 2007-06-01
categories: linux
tags: ["linux","vsftp","配置"]
---

太有成就感了，继配置好 samba 之后，又解决了 vsftpd 的配置，先贴上我的 vsftpd.conf

```ini
#服务器以 standalong 模式运行，这样可以进行下面的控制
listen=YES
#接受匿名用户
anonymous_enable=YES
#匿名用户 login 时不询问口令
no_anon_password=YES

#接受本地用户
local_enable=YES
#本地帐户登陆后有\\无权删除和修改文件
write_enable=NO

#本地用户上传文件的 umask
local_umask=022
#使用上传/下载日志，日志文件默认为/var/log/vsftpd.log，可以通过 xferlog_file 选项修改
xferlog_enable=YES
#login 时的欢迎信息
ftpd_banner=Welcome to XIAOMEI`s FTP service.

#本地用户 login 后所在目录，若没有设置此项，则本地用户 login 后将在他的 home 目录 (/etc/passwd 的第六个字段) 中。
local_root=/home/ftp
#匿名用户的对应选项
#anon_root=/home/ftp

#启用 FTP 数据端口的数据连接
connect_from_port_20=YES
#验证方式
pam_service_name=vsftpd
```

加#的是注释
经验介绍：
1，首先 sudo apt-get install vsftpd 来安装

安装好 vsftpd 后，就配置/etc/vsftpd.conf

2，注意到了

```ini
#接受本地用户
local_enable=YES
```

这一句，就是表示允许本地用户登录，因此要配置本地登录
执行命令： `sudo nano /etc/vsftp.user_list`
输入：
> ftpuser
> anonymous
保存后退出
3，执行命令 sudo /etc/init.d/vsftpd start
重启 vsftpd 服务

顺便介绍一下 vsftpd 命令

```bash
# 分别是         重启｜停止｜启动          vsftpd服务
sudo /etc/init.d/vsftpd restart stop start
```

