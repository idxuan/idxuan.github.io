---
layout: post
category: 研发
title: Golang 学习及使用
tags : [Golang,研发]
image:
  feature: feature.jpg
comments: true
share: true
---

Golang 使用点滴
------------------------

### mymysql调用提示错误

在日常工作中，应用程序不使用数据库的是越来越少了，学习用，也就不考虑太多了，直接MySQL的上手，Go语言MySQL数据库驱动选择的mymysql。但找了例子测试时，怎么都运行出错。

#### 原因分析：

无法调用MySQL数据库程序命令。

#### 解决方法：

在环境变量Path里增加MySQL程序的bin路径。
