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

## 1. 概述

## 2. Golang 安装

### 2.1. Windows 平台安装

### 2.2. Linux 平台安装

**下载安装**

```bash
sudo add-apt-repository ppa:gophers/go
sudo apt-get update
sudo apt-get install golang-stable
```

或

```bash
sudo apt-get install golang
```


**环境配置**

```cfg
export Dev_Lib=$HOME/UserData/Work/DevelopLibraries
export GOROOT=/usr/lib/go
export GOARCH=amd64
export GOOS=linux
export GOPATH=%Dev_Lib%/Golang/3rd:%Dev_Lib%/Golang/own:$HOME/UserData/Work/Codes/Golang/example
export GOBIN=$GOPATH/bin
export PATH=$GOPATH/bin:$PATH
```

## 3. Golang 使用点滴

### mymysql调用提示错误

在日常工作中，应用程序不使用数据库的是越来越少了，学习用，也就不考虑太多了，直接MySQL的上手，Go语言MySQL数据库驱动选择的mymysql。但找了例子测试时，怎么都运行出错。

**原因分析：**

无法调用MySQL数据库程序命令。

**解决方法：**

在环境变量Path里增加MySQL程序的bin路径。
