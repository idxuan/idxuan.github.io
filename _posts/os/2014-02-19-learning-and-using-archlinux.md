---
layout: post
category: 操作系统
title: ArchLinux 学习及使用
tags : [ArchLinux,操作系统]
image:
  feature: feature.jpg
comments: true
share: true
---

本文只是记录学习过程，为了以后使用备忘而已。

使用点滴
--------

### netctl

有时候 `interface` 的名称不是 `eth0`

```bash
dmesg|grep -i rename
```

### 静态地址

输入命令：

```bash
cp /etc/netctl/example/ethernet-static /etc/netctl/my_network
vi my_network
```

输入配置：

```cfg
Connection='ethernet'
Description='Five different addresses on the same NIC.'
Interface=eth0
IP='static'
# "/24"是子网掩码"255.255.255.0"
Address=('192.168.1.10/24')
Gateway='192.168.1.1'
DNS=('192.168.1.1')
```

### 字体包

```bash
# 字符终端使用这条命令即可
fc-cache:fontconfig

mkfontscale:xorg-font-utils
mkfontdir:xorg-font-utils
```