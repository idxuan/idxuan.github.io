---
layout: post
category: 操作系统
title: Ubuntu 更新源
tags : [Ubuntu,操作系统]
image:
    feature: feature.jpg
comments: true
share: true
---

本文参考了[Ubuntu 中文 Wiki](http://wiki.ubuntu.org.cn/Qref/Source)。

## 更新步骤

### 1. 首先备份源列表：

```bash
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```

### 2. 而后用gedit或其他编辑器打开：

```bash
gksu gedit /etc/apt/sources.lis
```

### 3. 从下面“Ubuntu13.10源列表”中选择合适的源，替换掉文件中所有的内容，保存编辑好的文件，注意一定要选对版本：

### 4. 刷新列表，注意：一定要执行刷新：

```bash
sudo apt-get update
```

### 5. 更新系统（可选）：

```bash
sudo apt-get upgrade
```

## 使用 "apt-fast" 更新提速

### 1. 安装 "apt-fast"：

```bash
sudo apt-get install axel aria2
sudo add-apt-repository ppa:apt-fast/stable
sudo apt-get update
sudo apt-get install apt-fast
```

### 2. 对 "apt-fast" 进行设置（新版本安装完成后会显示设置窗口）：

```bash
sudo gedit /etc/axelrc

# 设置合适的线程数，默认为4
num_connections = Num
```

### 3. 用 "apt-fast" 代替 "apt-get" 使用：

```bash
sudo apt-fast update
sudo apt-fast install ***
sudo apt-fast upgrade
```

## Ubuntu13.10源列表

##### 注意： `deb` 是软件源，`deb-src` 是软件源代码源。源码源已经删除，如需要请自行复制软件源并修改前缀 `deb` 为 'deb-src'。

```
#中科大源
deb http://mirrors.ustc.edu.cn/ubuntu/ saucy main restricted universe multiverse
deb http://mirrors.ustc.edu.cn/ubuntu/ saucy-security main restricted universe multiverse
deb http://mirrors.ustc.edu.cn/ubuntu/ saucy-updates main restricted universe multiverse
deb http://mirrors.ustc.edu.cn/ubuntu/ saucy-proposed main restricted universe multiverse
deb http://mirrors.ustc.edu.cn/ubuntu/ saucy-backports main restricted universe multiverse

#华中科技大学源
deb http://mirror.hust.edu.cn/ saucy main restricted universe multiverse
deb http://mirror.hust.edu.cn/ saucy-security main restricted universe multiverse
deb http://mirror.hust.edu.cn/ saucy-updates main restricted universe multiverse
deb http://mirror.hust.edu.cn/ saucy-proposed main restricted universe multiverse
deb http://mirror.hust.edu.cn/ saucy-backports main restricted universe multiverse

#官方源
deb http://archive.ubuntu.com/ubuntu/ saucy main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ saucy-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ saucy-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ saucy-proposed main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ saucy-backports main restricted universe multiverse

#Ubuntu官方提供的其他软件（第三方闭源软件等）：
deb http://archive.canonical.com/ubuntu/ saucy partner
deb http://extras.ubuntu.com/ubuntu/ saucy main

#上海交大
deb http://ftp.sjtu.edu.cn/ubuntu/ saucy main restricted universe multiverse
deb http://ftp.sjtu.edu.cn/ubuntu/ saucy-security main restricted universe multiverse
deb http://ftp.sjtu.edu.cn/ubuntu/ saucy-updates main restricted universe multiverse
deb http://ftp.sjtu.edu.cn/ubuntu/ saucy-proposed main restricted universe multiverse
deb http://ftp.sjtu.edu.cn/ubuntu/ saucy-backports main restricted universe multiverse


#清华大学
deb http://mirrors.tuna.tsinghua.edu.cn/ubutu/ saucy main restricted universe multiverse
deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ saucy-security main restricted universe multiverse
deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ saucy-updates main restricted universe multiverse
deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ saucy-proposed main restricted universe multiverse
deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ saucy-backports main restricted universe multiverse


#天津大学
deb http://mirror.tju.edu.cn/ubuntu/ saucy main restricted universe multiverse
deb http://mirror.tju.edu.cn/ubuntu/ saucy-security main restricted universe multiverse
deb http://mirror.tju.edu.cn/ubuntu/ saucy-updates main restricted universe multiverse
deb http://mirror.tju.edu.cn/ubuntu/ saucy-proposed main restricted universe multiverse
deb http://mirror.tju.edu.cn/ubuntu/ saucy-backports main restricted universe multiverse


#东北大学
deb http://mirror.neu.edu.cn/ubuntu/ saucy main restricted universe multiverse
deb http://mirror.neu.edu.cn/ubuntu/ saucy-security main restricted universe multiverse
deb http://mirror.neu.edu.cn/ubuntu/ saucy-updates main restricted universe multiverse
deb http://mirror.neu.edu.cn/ubuntu/ saucy-proposed main restricted universe multiverse
deb http://mirror.neu.edu.cn/ubuntu/ saucy-backports main restricted universe multiverse


#台湾源（台湾的ubuntu 更新源还是很给力的）
deb http://tw.archive.ubuntu.com/ubuntu/ saucy main universe restricted multiverse
deb http://tw.archive.ubuntu.com/ubuntu/ saucy-security universe main multiverse restricted
deb http://tw.archive.ubuntu.com/ubuntu/ saucy-updates universe main multiverse restricted
deb http://tw.archive.ubuntu.com/ubuntu/ saucy-proposed universe main multiverse restricted
deb http://tw.archive.ubuntu.com/ubuntu/ saucy-backports universe main multiverse restricted

#搜狐的源
deb http://mirrors.sohu.com/ubuntu/ saucy main restricted universe multiverse
deb http://mirrors.sohu.com/ubuntu/ saucy-updates main restricted universe multiverse
deb http://mirrors.sohu.com/ubuntu/ saucy-backports main restricted universe multiverse
deb http://mirrors.sohu.com/ubuntu/ saucy-security main restricted universe multiverse
deb http://mirrors.sohu.com/ubuntu/ saucy-proposed main restricted universe multiverse
```
