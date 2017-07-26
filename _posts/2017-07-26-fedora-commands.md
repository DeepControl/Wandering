---
layout: post
title: Fedora入门命令（更新至2015.09.26）
date: 2015-05-14 18:52:27 +08:00
categories: Linux
---

**1. 添加sudo**

[上篇日志][]

**2. 系统更新**

    $ sudo dnf update #或者dnf update
    $ sudo reboot

**3. 删除旧内核**

    $ uname -r​ #查看正在使用的内核
    $ rpm -qa | grep kernel #查找内核包
    $ sudo dnf remove #remove后列出旧内核名称

**4. 安装gnome shell**
```
$ sudo dnf install gnome-tweak-tool
```
**5. 安装其他桌面**
```
$ sudo dnf install @mate-desktop #Mate桌面环境
$ sudo dnf install @kde-desktop #KDE桌面环境
$ sudo dnf install @xfce-desktop #XFCE桌面环境
$ sudo dnf install @lxde-desktop #LXDE桌面环境
$ sudo dnf install @cinnamon-desktop #Cinnamon桌面环境
```
**6. 安装第三方源rpmfusion和VLC播放器**
```
$ sudo rpm -ivh http://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-stable.noarch.rpm
$ sudo dnf install vlc
$ sudo dnf install mozilla-vlc (optional)
```
**7. 安装谷歌chrome**
```
$ sudo dnf install https://dl.google.com/linux/direct/google-chrome-stable_current_x86_64.rpm
```
**8. dnf启动断点续传**
```
$ man dnf.conf
用vi命令在dnf.conf里写入keepcache=true​
```
**9. 安装flash**
```
$ sudo rpm -ivh http://linuxdownload.adobe.com/adobe-release/adobe-release-x86_64-1.0-1.noarch.rpm
$ sudo rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-adobe-linux
$ ​sudo dnf -y install flash-plugin
```
**10. 安装LibreOffice中文语言包**
```
$ sudo dnf -y install  libreoffice-langpack-zh-Han*
```
**11. Fedora下临时挂载ntfs分区**
```
$ sudo mount -t ntfs /dev/sda* /mnt/FileName
```

&emsp;&emsp;__* 本文内容均由网上搜集而来。__



[上篇日志]: http://blog.deepcontrol.info/linux/2015/05/14/how-to-use-sudo-in-fedora.html
