---
layout: page
permalink: /about/
title: 关于
image:
    feature: feature.jpg
---

## 概述

我的博客记录了学习和生活的经历过程，既为了再次查询时的备忘，也想留下了一路走过的痕迹。

## 版权说明

* 本网站所有作品，除明确申明作者为他人以外，版权为本人所有，以商业盈利目的使用需经本人授权同意。
* 非商业盈利目的使用，在不侵犯法律赋予的著作权人享有的权利，并指明作者姓名、作品名称，作品出处后，允许转载使用。

## 近期博文

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date: "%Y年%m月%d日" }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

## 相关链接

* 我在 `Github` 的源码 [Github](https://github.com/idxuan)
