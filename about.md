---
layout: page
permalink: /about/
title: 关于
image:
  feature: feature.jpg
---

##### 我的博客记录了学习和生活的过程经历，既为了再次查询时的备忘，也想留下了一路走过的痕迹。

## 近期博文

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date: "%Y年%m月%d日" }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

#### 备注

* 我在 `Github` 的源码 [Github](https://github.com/idxuanjun)
* 我在 `CSDN` 的博客 [CSDN](http://blog.csdn.net/idxuanjun)
