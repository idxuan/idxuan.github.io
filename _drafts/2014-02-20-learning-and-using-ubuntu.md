---
layout: post
category: 操作系统
title: Ubuntu 学习及使用
tags : [Ubuntu,操作系统]
image:
    feature: feature.jpg
comments: true
share: true
---

## 1. 概述

本文只是记录学习过程，为了以后使用备忘而已，本文参考了多处互联网资料，来源无法探究，如果侵犯了您的权限，请联系我。

## 安装IBus输入法

### 1. 安装IBus框架：

```bash
sudo apt-get install ibus ibus-clutter ibus-gtk ibus-gtk3 ibus-qt4
```

### 2. 选择安装下列拼音引擎，完成安装后重启系统：

```bash
sudo apt-get install ibus-table python-ibus ibus-pinyin* ibus-***
```

*   拼音： `ibus-pinyin、ibus-sunpinyin、ibus-googlepinyin`；
*   五笔： `ibus-table-wubi`；
* 中州韵： `ibus-rime` 。

### 3. 设置默认输入法（可选，可能需要重启系统）：

```bash
im-config
```

### 4. 设置IBus框架（可选）：

```bash
ibus-setup
```

### 5. 设置IBUS：

### 6. 通常情况下，IBus图标（一个小键盘）会出现在桌面右上角的任务栏中。有时候这个图标会自行消失，可使用以下命令，找回消失的IBus图标：

```bash
ibus-daemon -drx
```

## 安装小企鹅输入法

### 1. 可以卸载原装的IBUS输入法：

```bash
killall ibus-daemon
sudo apt-get purge ibus ibus-gtk ibus-gtk3 ibus-pinyin* ibus-sunpinyin ibus-table python-ibus
rm -rf ~/.config/ibus
```

### 2. 安装fcitx搜狗拼音输入法：

```bash
sudo add-apt-repository ppa:fcitx-team/nightly
sudo apt-get update
```

### 3. 选择安装下列拼音引擎，完成安装后重启系统：

*   拼音： `fcitx-pinyin、fcitx-sunpinyin、fcitx-sogoupinyi、fcitx-googlepinyin`；
*   五笔： `fcitx-table-wubi、fcitx-table、fcitx-table-wbpy`；
* 中州韵： `fcitx-rime` 。

```bash
sudo apt-get install fcitx-***
```

### 4. 安装fcitx默认的所有输入法（可选）

```bash
sudo apt-get install fcitx-table-all
```

### 5. 设置默认输入法（可选，可能需要重启系统）：

```bash
im-config
```

### 6. 设置输入法：

点击屏幕右上角输入法选择按钮，点击“配置当前输入法”。

## 中州韵輸入方案

```bash
# 朙月拼音（預裝）
sudo make install librime-data-luna-pinyin
sudo apt-get install librime-data-double-pinyin
# 宮保拼音
sudo apt-get install librime-data-combo-pinyin
# 速記打字法
sudo apt-get install librime-data-stenotype
# 注音、地球拼音
sudo apt-get install librime-data-terra-pinyin librime-data-bopomofo
# 倉頡五代（預裝）
sudo apt-get install librime-data-cangjie5
# 速成五代
sudo apt-get install librime-data-quick5
# 五筆86、袖珍簡化字拼音、五筆畫
sudo apt-get install librime-data-wubi librime-data-pinyin-simp librime-data-stroke-simp
# IPA (X-SAMPA)
sudo apt-get install librime-data-ipa-xsampa
# 上海吳語
sudo apt-get install librime-data-wugniu
# 粵拼
sudo apt-get install librime-data-jyutping
# 中古漢語拼音
sudo apt-get install librime-data-zyenpheng librime-data-triungkox3p
# 快速倉頡
sudo apt-get install librime-data-scj6
# 筆順五碼
sudo apt-get install librime-data-stroke5
```
