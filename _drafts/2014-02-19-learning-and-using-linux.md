---
layout: post
category: 操作系统
title: Linux 学习及使用
tags : [Linux,操作系统]
image:
    feature: feature.jpg
comments: true
share: true
---

## 1. 概述

本文只是记录学习过程，为了以后使用备忘而已。

## 使用点滴

### 添加新字体

```bash
cd /usr/share/fonts
sudo cp -r myfonts newfonts
cd newfonts
mkfontscale
mkfontdir
fc-cache
```

### 环境配置

系统环境变量：

```
/etc/environment
/etc/profile
/etc/bash.bashrc
```

用户环境变量：

```
~/.profile
~/.bash_profile 或者 ~./bash_login
~/.bashrc
```

上述“.profile"对所有环境有效，而“.bashrc“只针对“bash shell”有效。

Sudo环境变量继承

在/etc/sudoers.d目录下添加任意文件，前提是不包括～结尾和.字符,权限要设置成440，具体要求看改目录下的README文件，文件内容：

```
Defaults env_keep += "CONFIG_ENV"
```

以上设置的变量“CONFIG_ENV”就能在sudo中使用，在“/etc/sudoers”中去除“#includedir /etc/sudoers.d/”的注释以开启这个目录。请注意，新版好像不需要。
