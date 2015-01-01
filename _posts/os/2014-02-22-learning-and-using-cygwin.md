---
layout: post
category: 操作系统
title: Cygwin 学习及使用
tags : [Cygwin,操作系统]
image:
    feature: feature.jpg
comments: true
share: true
---

## 1. 概述

## 2. 安装Cygwin

略……

## 3. 安装包

* 安装“vim”
* 安装“util-tool”
* 安装“libiconv”
* 安装“git”

## 4. 环境设置

### 4.1. 设置全局配置文件 `Cygwin\etc\profile`：

```cfg
#-----------------------------------------------------------
# BuXing Settings
#-----------------------------------------------------------
# 定义语言环境变量
export LC_ALL=en_US.UTF-8
export LANG=en_US.UTF-8

# 定义用户HOME环境变量
HOME='/cygdrive/d/LinuxHome/xuan'

# Interactive operation...
# alias rm='rm -i'
# alias cp='cp -i'
# alias mv='mv -i'
#
# Default to human readable figures
alias df='df -h'
alias du='du -h'
#
# Misc :)
alias less='less -r'                          # raw control characters
alias whence='type -a'                        # where, of a sort
alias grep='grep --color'                     # show differences in colour
alias egrep='egrep --color=auto'              # show differences in colour
alias fgrep='fgrep --color=auto'              # show differences in colour
#
# Some shortcuts for different directory listings
alias ls='ls -hF --color=tty'                 # classify files in colour
alias dir='ls --color=auto --format=vertical'
alias vdir='ls --color=auto --format=long'
alias ll='ls -l'                              # long list
alias la='ls -A'                              # all but . and ..
alias l='ls -CF'                              #

# Umask
#
# /etc/profile sets 022, removing write perms to group + others.
# Set a more restrictive umask: i.e. no exec perms for others:
# umask 027
# Paranoid: neither group nor others have any perms:
# umask 077
```

### 4.2. 设置用户配置文件 `${HOME}\.bashrc`：

```bash
# 自动补全不区分大小写
shopt -s nocaseglob
```

### 4.3. 设置用户配置文件 `${HOME}\.inputrc`：

```bash
# 自动补全不区分大小写
set completion-ignore-case on

# 按单词移动/删除
# Ctrl+Left/Right to move by whole words
"\e[1;5C": forward-word
"\e[1;5D": backward-word
# Ctrl+Backspace/Delete to delete whole words
"\e[3;5~": kill-word
"\C-_": backward-kill-word
```

### 4.4. 链接磁盘及常用文件夹：

```bash
ln -s /cygdrive/c /c
ln -s /cygdrive/d /d
ln -s /cygdrive/e /e
ln -s /cygdrive/f /f
d:/UserData/LinuxHome /home
d:/UserData/Tech/Repositories/git /repo
d:/UserData/Work/Projects /projects
d:/UserData/Work/Codes /codes
e:/Downloads /dl
f:/Repositories/git /lrepo
```

### 4.5. 修改 `Cygwin.bat` 文件，增加设置环境变量 `HOME`：

```cfg
set HOME=d:/UserData/LinuxHome/xuan
```

## 5. 右键菜单打开Cygwin在当前目录

### 5.1. 增加注册表项：

```registry
Windows Registry Editor Version 5.00

[HKEY_CLASSES_ROOT\Directory\shell\opencygwin]
@="打开用 Cygwin"
[HKEY_CLASSES_ROOT\Directory\shell\opencygwin\command]
@="d:\\GSoft\\Linux\\Cygwin\\Cygwin.bat %V"
```

### 5.2. 修改 `Cygwin.bat` 文件，增加设置路径变量 `set _T=%*`：

```bat
@echo off
set _T=%*
set HOME=d:/UserData/LinuxHome/xuan
D:
chdir d:/GSoft/Linux/Cygwin/bin

bash --login -i
REM mintty.exe -i /Cygwin-Terminal.ico -
```

### 5.3. 设置用户配置文件 `${HOME}\.bash_profile`，在最后增加：

```bash
# 右键菜单打开Cygwin在当前目录
export _T=${_T//\\//}   # replace backslash to fowardslash
if [[ $_T == "" ]]; then
    export _T=${HOME}
fi
cd "$_T"
```

## 6. Git设置

### 6.1. 初始化配置：

```bash
#配置ID
git config --global user.name "your_id"
#配置EMAIL
git config --global user.email "your_name@email_address"

# git输出（比如log、status）彩色显示
git config --global color.ui auto

# 全局配置Git不会进行换行符的转换
git config --global core.autocrlf false

# 全局配置文件权限
git config --global core.filemode false
```

### 6.2. 配置 SSH 证书：

##### 6.2.1. 新建 SSH 证书：

```bash
ssh-keygen -t rsa -C "your_name@email_address"
```

##### 6.2.2. 恢复备份 SSH 证书：

1. 建立目录“~/.ssh“；
2. 复制备份的“id_rsa”(私钥) 和“id_rsa.pub”(公钥) 文件至目录“~/.ssh“；

### 6.2.3. 通过 github 测试 SSH 证书：


ssh -T git@github.com


如果看到“You've successfully authenticated, but GitHub does not provide shell access”信息，就表示连接成功。

## 7. 小技巧

### 7.1. 可以建立指向Windows系统的符号链接，例如：

```bash
ln -s /cygdrive/e/Downloads ~/dl
```

### 7.2. Cygwin下的cd命令可以直接使用Windows的路径表示，路径加上单引号转义 `\`，例如：

```bash
cd 'C:\Windows\System32\drivers\etc'
```

### 7.3. 错误“$'\r': command not found”，原因是脚本文件里使用的是Windows的回车换行，修改文件为Unix的换行即可：

### 7.4. Cygwin字符集设置为UTF-8的时候运行Windows命令，会因为编码的关系出现乱码。解决方法就是写个shell脚本放在“/bin”目录下，例如：

```bash
#!/bin/sh
ping.exe $@ 2>&1 | iconv -f gbk -t utf-8
```

并增加可执行权限：

```bash
chmod +x ping
```

### 7.5. 同步Windows系统用户：

```bash
mkpasswd -l > /etc/passwd
mkgroup -l > /etc/group
```



