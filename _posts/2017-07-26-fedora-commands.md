---
layout: post
title: Fedora入门命令（更新至2017-10-27）
date: 2015-05-14 18:52:27 +08:00
categories: Linux
---

**0. 目录及说明**

    新版本Fedora不一定继续适用
    2015-09-26 更新1-11
    2017-09-19 更新12-22
    2017-10-18 更新23
    2017-10-27 更新24-31

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
$ find dnf.conf
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

------------------------------
------------------------------
<br/>

**12. 安装Remmina远程桌面**

　`$ sudo dnf install remmina #控制Windows等主机，支持多种协议`

**13. 升级Fedora到高版本**

　`FedoraProject Wiki中提供的方法:`[DNF_system_upgrade](http://fedoraproject.org/wiki/DNF_system_upgrade)

**14. Ｍarkdown输入空格**

　`&emsp;`或者`&nbsp;`或者`全角空格`

**15. 键盘按键的英文名**

```
　逗号：comma
　句号：period
　减号：minus
　等号：equal
```
**16. Fedora添加全局快捷键**

设置--->键盘--->下拉到最后--->添加自定义快捷键，填写诸如:

> 打开终端

> /usr/bin/gnome-terminal

> shift+ctrl+n

或者

> 打开文件管理器

> /usr/bin/nautilus

> 你想设置的快捷键

**17. 查看终端命令记录history**

`$ history`

其中history文件存放在~/.bash_history

**18. 终端常用命令和快捷键**

```
1.$ tty #查看当前所在终端
2.$ who #查看当前已登录的用户
   （$ w #增加显示详细统计信息，tty表示本地用户，pts/表示远程用户）
3.ctrl+s 终端挂起
4.ctrl+q 解除挂起
5.ctrl+l 清屏
6.ctrl+a 光标移动到本条命令行首
7.ctrl+e 光标移动到本条命令行尾
8.ctrl+u 清除光标所在条命令，同时历史记录中也清除

```

**19. Fedora修改hostname主机名**

```
$ hostname
oldhostname
$ sudo hostname newhostname #新主机名
$ hostname
newhostname
$ echo $HOSTNAME #打印系统环境变量，重启后就会变成新主机名了
oldhostname
$ sudo hostnamectl set-hostname newhostname #另一种修改主机名方式
```
**20. 从图形界面切换到字符界面**

```
$ sudo systemctl isolate runlevel3
```

**21. Fedora安装sublime-text (ST暂不支持中文输入)**

> Install the GPG key:

>     sudo rpm -v --import https://download.sublimetext.com/sublimehq-rpm-pub.gpg

> Select the channel to use:

> Stable

>     sudo dnf config-manager --add-repo https://download.sublimetext.com/rpm/stable/x86_64/sublime-text.repo

> Dev

>     sudo dnf config-manager --add-repo https://download.sublimetext.com/rpm/dev/x86_64/sublime-text.repo

> Update dnf and install Sublime Text

>     sudo dnf install sublime-text

**22. Fedora使用ss-qt5**

```
查看https://github.com/shadowsocks/shadowsocks-qt5/wiki
$ sudo dnf copr enable librehat/shadowsocks
$ sudo dnf install shadowsocks-qt5 #安装后添加信息
$ sudo pip install genpac #genpac是pac文件生成工具，原料是gfwlist
$ touch user-rules.txt
$ genpac -p "SOCKS5 127.0.0.1:1080" --gfwlist-proxy="SOCKS5 127.0.0.1:1080" --output="autoproxy.pac" --gfwlist-url="https://raw.githubusercontent.com/gfwlist/gfwlist/master/gfwlist.txt" --user-rule-from="user-rules.txt"
# 上条命令中端口和文件信息需要自行修改
file:///home/(user)/vpnPAC/autoproxy.pac #系统设置和firefox填写文件地址
```

------------------------------
------------------------------
<br/>

**23. Fedora server版本安装使用gnome**

```
$ sudo dnf -y groupinstall "Fedora Workstation"
$ sudo echo "exec /usr/bin/gnome-session" >> ~/.xinitrc
$ sudo startx
```

**24. Fedora安装mediainfo**

```
$ sudo dnf install mediainfo
```

**25. Fedora安装adb调试android工具**

```
$ sudo dnf install android-tools
$ adb devices
$ adb -d shell sh /data/data/me.piebridge.brevent/brevent.sh
并安装黑域
```

**26. Fedora向github添加ssh key**

```
$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com" #生成rsa文件
Enter a file in which to save the key (/home/you/.ssh/id_rsa):
Enter passphrase (empty for no passphrase): [Type a passphrase]
按照自己的需要修改目录和口令
$ eval "$(ssh-agent -s)" #启动ssh-agent
$ ssh-add ~/.ssh/id_rsa #添加rsa到ssh-agent
登录github，在settings里找到SSH and GPG keys，把id_rsa.pub的内容复制上去并保存。
$ ssh -T git@github.com #测试
测试结果及说明https://help.github.com/articles/testing-your-ssh-connection/
$ git clone git@github.com:*** #Clone with SSH用github的ssh链接进行克隆
```

**27. Fedora安装miredo实现ipv6协议的teredo隧道**

```
$ sudo dnf install miredo-client
$ sudo service miredo-client start
$ sudo service miredo-client status
$ ping -6 ipv6.baidu.com
$ ping6 ipv6.google.com
```

**28. Fedora安装namp和zenmap**

```
$ sudo rpm -vhU https://nmap.org/dist/nmap-7.60-1.x86_64.rpm
$ sudo rpm -vhU https://nmap.org/dist/zenmap-7.60-1.noarch.rpm
$ nmap 192.168.18.1/28
$ nmap -Pn 192.168.18.17
```

**29. Fedora在Firefox中为Complete Youtube Saver配置ffmpeg**

```
$ sudo dnf install ffmpeg
在firefox附加组件中安装Complete Youtube Saver
然后在CYS的首选项中选择ffmpeg目录为/usr/bin即可
```

**30. git使用操作**

```
$ git config --global user.email "you@example.com" #填写身份标识
$ git -C path/repository_name status #检查有没有需要提交的文件
$ git -C path/repository_name commit -am '***' #星号处填写commit内容
$ git -C path/repository_name push
```

**31. Fedora安装wireshark**

```
$ sudo dnf install wireshark wireshark-qt
$ sudo groupadd wireshark
$ groups
$ sudo usermod -a -G wireshark $(whoami)
$ more /etc/group | grep wireshark
注销当前用户重新登陆即可正常使用wireshark
```


&emsp;&emsp;__* 本文内容均由网上搜集而来。__



[上篇日志]: http://blog.deepcontrol.info/linux/2015/05/14/how-to-use-sudo-in-fedora.html
