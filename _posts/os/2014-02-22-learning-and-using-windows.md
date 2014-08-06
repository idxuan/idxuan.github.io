---
layout: post
category: 操作系统
title: Windows 学习及使用
tags : [Windows,操作系统]
image:
    feature: feature.jpg
comments: true
share: true
---

## 1. 概述

## 2. 设置库

使用“mlink”建立链接目录，避开系统盘。

```bat
mlink /j link_dir original_dir
```

## 3. 特殊文件处理

通过文件的“隐藏属性”和“自定义属性”中“恢复默认图标”来处理系统链接文件。

## 4. 自定义字体

### 4.1. 字体 `Consolas` 链接到中文字体

如果字体 `Consolas` 中文字体链接到雅微软黑，中文字体会略扁，编辑注册表

```registry
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\FontLink\SystemLink]
```

新建一条 “多字符串值”名称为 “Consolas”，下列可选项

```
MSYH.TTC,Microsoft YaHei,112,110 //字号：9、10、11、14
MSYH.TTC,Microsoft YaHei,120,100 //字号：10、12
MSYH.TTC,Microsoft YaHei,128,96  //字号：9、11
MSYH.TTC,Microsoft YaHei
SIMYOU.TTF,YouYuan
SIMSUN.TTC,NSimSun
```

新建一条 “多字符串值”名称为 “Consolas Bold”，下列可选项

```
MSYHBD.TTC,Microsoft YaHei Bold,112,110 //字号：9、10、11、14
MSYHBD.TTC,Microsoft YaHei Bold,120,100 //字号：10、12
MSYHBD.TTC,Microsoft YaHei Bold,128,96  //字号：9、11
MSYHBD.TTC,Microsoft YaHei Bold
SIMYOU.TTF,YouYuan
SIMSUN.TTC,NSimSun
```

推荐的中文字体链接配置

```
Comic Sans MS = MSYH.TTF,128,96
Trebuchet MS = MSYH.TTF
Consolas = SIMYOU.TTF       //轻微扁
Lucida Console = SIMYOU.ttf //略扁
Verdana = SIMYOU.TTF
Monaco = SIMYOU.TTF         //略窄
```

## 5. 修改 Windows 7 控制台（CMD）的字体

### 5.1. 检查注册表，系统里存在的“TrueType”字体

```registry
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WindowsNT\CurrentVersion\fonts]
```

### 5.2. 打开注册表并备份

```registry
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WindowsNT\CurrentVersion\Console\TrueTypeFont]
```

### 5.3. 增加子项名为“0936”的控制台“简体中文代码页”字体，值为系统里存在的“TrueType”字体名称。也可以新增子项名为“000”的控制台“美国代码页”字体

### 5.4. 修改控制台（CMD）默认值的字体

#### 5.4.1 方式一：修改注册表：

```registry
Windows Registry Editor Version 5.00

[HKEY_CURRENT_USER\Console\%SystemRoot%_system32_cmd.exe]
"FaceName"="字体名称"
```

#### 5.4.2 方式二：增加控制台（CMD）快捷键，修改快捷键属性及默认值的字体名称和大小

### 5.5. 重新启动完成控制台的字体的修改

## 6. 通过增加注册表项，使右键菜单打开控制台（CMD）在当前目录

```registry
Windows Registry Editor Version 5.00

[HKEY_CLASSES_ROOT\Directory\shell\opencmd]
@="打开用 CMD"
[HKEY_CLASSES_ROOT\Directory\shell\opencmd\command]
@="cmd.exe /k cd %1"
```

