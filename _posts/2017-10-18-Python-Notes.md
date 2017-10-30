---
layout: post
title: Python学习笔记
date: 2017-10-18 22:35:55 +08:00
categories: Python
---


1.不定长参数
```
def func(a,b,*args,**kwargs):
```
2.元组和字典的拆包
```
A = ()
B = {}
func(11,22,*A,**{})
```
3.引用
```
变量指向内存，详见Python内存管理
```
4.不可变、可变类型
```
可变类型：列表、字典
不可变类型：元组、字符串等
*字典的key必须是不可变类型
```
5.递归
```
层层分包，反过来交工
```
6.匿名函数
```
sum = lambda arg1, arg2 : arg1 + arg2
```
7.Python语言动态特性
```
可以在获取用户输入后继续执行某段程序
func = input("请输入匿名函数")
func = eval(func)
```
8.变量交换
```
a,b = b,a
a,b,c = b,c,a
```
9.引用
```
python不是赋值，而是引用
num+=num不等价于num = num + num
```
10.文件操作
```
file = open("file.txt","w")
file.close()
file.read()
file.readlines(2048) #大文件
file.write("")
file.seek(0,0)
file.tell()

import os
os.listdir()
```
11.类
```
类的名称
类的属性
类的方法
class Exp:
    #初始化对象
    def __init__(self):

    #方法
    def func(self):
```
12.
```

```

```
```

```
```

```
```
```
```

```
```
```
```

```
```
```
```

```
```
```
```

```
```
```
```

```
```
```
```

```
```
