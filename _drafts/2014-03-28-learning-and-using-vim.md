---
layout: post
category: 工具
title: Vim 学习及使用
tags : [Vim,文本编辑]
image:
    feature: feature.jpg
comments: true
share: true
---

## 1. 概述

## 2. Vim 快捷键

### 2.2. 文件窗口


### 2.2. 移动定位


### 2.3. 选择


### 2.4. 编辑

* **Ctrl+Insert**: 复制
* **Shift+Insert**: 粘贴

### 2.5. 查找/替换


### 2.7. 标记

* **m[A~Z]**: 添加标记，Char是标记的ID，只能为单个字符
* **'[A~Z]**: 跳转到标记Char

### 2.7. 标签页

* **:tabnew**: 新建标签页
* **:tabs**: 显示已打开标签页的列表
* **:tabc**: 关闭当前标签页
* **:tabn**: 移动到下一个标签页
* **:tabp**: 移动到上一个标签页
* **:tabfirst**: 移动到第一个标签页
* **:tablast**: 移动到最后一个标签页
* **:tabm[0~Num]**: 移动当前标签页顺序位置

**注意**：

* `[A,B,C]` 表示A,B,C可选其一；
* `[A~C]` 表示A至C可选其一；
* `Num` 表示阿拉伯数字;
* `Char` 表示英文字母;
* `!` 前缀表示自定义快捷键或不符合日常习惯建议修改。

## 2. Vim 插件安装方式

### 2.2. 直接安装


### 2.2. 使用Package Control安装


## 3. Vim 配置

### Vim Shell 设置

## 4. Vim 编译

把 `vim72src.zip, vim72rt.zip` 解压后复制到 `runtime`，

```bash
src/make Make_ming_amd64.mak
```

* vim\vim72\src 下面的 gvim.exe, install.exe, uninstall.exe, vimrun.exe.
* vim\vim72\src\GvimExt 下的 gvimext.dll
* vim\vim72\src\xxd 下的 xxd.exe
* vim\vim72 下的 uninstal.txt
* vim\vim72 下的 libintl.dll
* vim\vim72 下的整个 lang 目录
* vim\vim72\runtime 下的所有 .vim 文件, README.txt, vimtutor.bat, rgb.txt
* vim\vim72\runtime 下的 colors 目录, compiler 目录, doc 目录(只留下 tags 文件和 .txt 文件, 其它删除), ftplugin 目录, indent 目录, macros 目录(下面的子目录都删除), plugin 目录, autoload 目录, syntax 目录, spell 目录(只留下 .txt, .vim, .spl, .sug 文件, 其它文件及子目录删除), tools 目录和 tutor 目录
* vim\vim72\runtime 下的 lang 目录中的文件, 都复制到刚才复制的那个 lang 目录中去, 这些是不同语言的菜单.

## 5. Vim 使用点滴

### 查看 `tab` 键的定义：

```
:verbose map <tab>
```

### 命令行编辑

进入命令行模式
按 Ctrl+F，就会弹出最近的命令列表，可以像普通文本一样进行复制。
按 Ctri+C，从列表跳回命令行，再按键一次关闭列表。

### 复制提示信息

输入下列命令可以把输出的内容弄上剪贴板：

```
:let @+=v:statusmsg
```

### 界面、菜单、提示语言设置

在配置里输入下列设置可以将菜单帮助设置为英文，详细信息查看":help lan"

```
let $LANG='en_US'  "set message language
set langmenu=en_US   "set menu's language of gvim. no spaces beside '='
```
