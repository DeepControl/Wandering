---
layout: post
title: Fedora中允许普通用户使用sudo命令
date: 2015-05-14 16:45:52 +08:00
categories: Linux
---

**1. sudo的特性**

&emsp;&emsp;使用`su`切换到root后权限没有限制，并不适合多人共管的服务器。`sudo`却可以针对每个人的不同工作内容做出权限上的约定。对于远程服务器的管理，禁止root用户通过ssh访问转而以普通用户身份通过`sudo`访问和管理也可以有效提高远程主机安全性。​使用`sudo`，当前用户切换到root权限执行命令，执行完成后超时即会退回普通用户权限，也不需要普通用户知道root密码，这也在一定程度上提高了安全性。

**2. 普通用户添加sudo**

    $ su #切换到root用户
    # ll /etc/sudoers #查看读写权限
    # chmod 777 /etc/sudoers #修改权限
    # vi /etc/sudoers #编辑文件
    光标找到root    ALL=(ALL)    ALL这一行，
    按a，进入append模式，
    添加username    ALL=(ALL)    ALL这一行，
    按Esc，再输入:wq保存文件并退出​。
    # chmod 440 /etc/sudoers​ #恢复权限
    # exit #退出root
    $ sudo whoami #查看结果

&emsp;&emsp;__* 本文内容均由网上搜集而来。__
