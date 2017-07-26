---
layout: post
title: Linux开机后自动发送邮件的一种方案
date: 2017-04-14 21:39:40 +08:00
categories: Linux
---

**1. 方案背景**

&emsp;&emsp;博主在Raspberry上安装的Fedora Server，由于树莓派的网线连在交换机上，ip无法固定，给远程ssh登录造成了麻烦。初步考虑方案一采用花生壳动态域名解析，方案二采用每次开机发送DHCP获得的ip到指定邮箱。莫名对方案二一见倾心，所以写了一下实现过程。

**2. 环境描述​**

>Fedora Server 26 for Raspberry Pi 3

>Xshell

>wo.cn沃邮箱

**3. 实现过程**

```
$ sudo dnf install mailx sendmail #安装mailx和sendmail服务
$ sudo service sendmail start #启动服务
$ netstat -ant #查看25端口是否在侦听
$ whereis mail.rc #查找sendmail的配置文件
vi /etc/mail.rc #添加如下五条后保存并重启sendmail服务
```
```
set from=沃邮箱@wo.cn
set smtp=smtp.wo.cn
set smtp-auth-user=沃邮箱@wo.cn
set smtp-auth-password=沃邮箱密码
set smtp-auth=login
```
```
$ sudo vi /root/ifconfigmail.sh #创建发邮件脚本
写入以下内容后保存
```
```
#!/bin/sh
sendmail -t >/dev/null 2>&1 <<EOF
to:指定的目标邮箱@hotmail.com
from:沃邮箱@wo.cn
subject:Your Raspberry restarted on $(date '+%Y-%m-%d')
IP may changed.
ipv4  $(ifconfig eth0 | awk '/inet /{gsub(//,"");print $2}')
ipv6  $(ifconfig eth0 | awk '/inet6 /{gsub(//,"");print $2}')
From Raspberry at $(date '+%Y-%m-%d %H:%M:%S')
EOF
```
```
$ sudo chmod 777 /root/ifconfigmail.sh #加可执行权限
$ sudo sh /root/ifconfigmail.sh #测试脚本能否正常发出邮件
$ sudo vi /etc/rc.d/rc.local #编辑开机启动脚本
添加以下内容后保存
```

    #!/bin/bash
    sleep 3m #延迟3分可以确保IP准确
    sh /root/ifconfigmail.sh

```
$ sudo chmod +x /etc/rc.d/rc.local #加可执行权限
$ sudo vi /usr/lib/systemd/system/rc-local.service
编辑开机启动，末尾添加如下一条
```
```
[Install]
WantedBy=multi-user.target
```
```
systemctl enable rc-local.service #开启开机自启动服务
```


&emsp;&emsp;__* 全文难免有叙述不当之处，见谅。__
