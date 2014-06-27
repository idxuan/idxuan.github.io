---
layout: post
category: 工具
title: PowerDesigner 学习及使用
tags : [PowerDesigner,研发,设计]
image:
    feature: feature.jpg
comments: true
share: true
---

## 1. 概述

## PowerDesigner 使用点滴

### PowerDesigner 脚本创建Oracle视图时提示错误：“with read only”

用Power Designer生成脚本，在PLSql Developer里用Command窗口创建视图，总是报错，用SQL窗口运行则一切正常。

##### 原因分析：

仔细看了看脚本，发现有的视图创建成功了，再对比一下，发现出错的“with read only”语句在SQL语句中总是有空行，删除空行，一切OK。

##### 解决方法：

在Power Designer里找了找原因，只是写创建视图的SQL语句结束时，顺手回了个车，结果Power Designer生成脚本时就多了个空行，手欠啊！
