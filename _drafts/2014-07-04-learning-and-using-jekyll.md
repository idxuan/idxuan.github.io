---
layout: post
category: 软件
title: Jekyll 学习及使用
tags : [Jekyll,Ruby,,研发]
image:
    feature: feature.jpg
comments: true
share: true
---

## 1. 概述

## 2. Jekyll 设置

### 2.1. 初始化配置：

## 3. Git 使用点滴

### 3.1 错误：`cannot close fd before spawn`

**原因分析：**

`Pygments.rb` 版本有 `Bug`。

**解决方法：**

更换 `Pygments.rb` 到没有问题的版本 `0.5.0`。

```bash
gem uninstall pygments.rb --version "=0.6.0"
gem install pygments.rb --version "=0.5.0"
```

### 3.2 `Pygments.rb` 不支持 Python3

**原因分析：**

无。

**解决方法：**

[下载 `Pygments.rb` 支持 Python3 的分支版本](https://github.com/tmm1/pygments.rb/tree/support-python3) 。

### 3.3 错误：`Conversion error: There was an error converting`

**原因分析：**

`Markdown` 解释器 `redcarpet` 和 `maruku` 问题。

**解决方法：**

编辑 `_config.yml` 配置文件，更换其他 `Markdown` 解释器。

```cfg
markdown: rdiscount
```
