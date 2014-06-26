---
layout: post
category: 电子数码
title: 安卓手机修改音量键为 HOME 和 BACK 键
tags : [Android]
image:
    feature: feature.jpg
comments: true
share: true
---


本文参考[《Galaxy Nexus如何把音量键修改为功能键》](http://samsung.anqu.com/xinshou_263/12733)和[《修改音量键为HOME和BACK，只需改动两个参量》](http://benyouhui.it168.com/thread-2224793-1-1.html)的两篇文章，经过整理编辑后完成。


## 步骤

#### 1. 手机要root；

#### 2. 打开RE管理器用记事本打开键盘定义文件，常见的文件名为“system/usr/keylayout/***gpio-keypad.kl”；

#### 3. 在记事本的最下方找到一下三行文字：

    key 114 VOLUME_DOWM WAKE
    key 115 VOLUME_UP   WAKE  　　　
    key 116 POWER       WAKE

#### 4. 下面就可以按照自己的意思来修改了：

    音量减少键 改为 HOME键：“key 114 VOLUME_DOWM WAKE” 改为 “key 114 HOME WAKE”；
    音量增加键 改为 BACK键：“key 115 VOLUME_UP WAKE”   改为 “key 115 BACK WAKE”；

#### 5. 保存文件，重启即可修改完成。

#### 6. 如果要恢复原来的功能，修改回原来的文本就可以了。

## 一般实体键的设置

    HOME         主页
    MENU         菜单
    BACK         返回
    SEARCH       搜索
    POWER        电源
    VOLUME_DOWN  音量减少
    VOLUME_UP    音量增加

## 说明

可以设置按音量键或其他按键唤醒手机。

* WAKE：当设备进入睡眠的时候，按下这个键将唤醒，而且发送消息给应用层。
* WAKE_DROPPED：当设备进入睡眠的时候，按下这个键将唤醒，但是不发送消息给应用层。

所以要使用按键唤醒，应该改为：POWER   WAKE_DROPPED


