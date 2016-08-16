---
layout: post
title: 教程：如何为文章添加背景
description: "教程：如何为文章添加背景"
tags: [教程]
categories: [图片]
image:
  background: triangular.png
---

该文章背景引用了一个背景图片。 使用方法是在文章内容头部添加下面一段yaml标记语言。

{% highlight yaml %}
image:
  background: filename.png
{% endhighlight %}

这句话使用前提是：默认图片路径在`/images`文件夹内。如果放在别处活来自网络，就直接完善路径或url即可！不论哪一种方式，背景图片都是平铺！

如果你想设置全局背景图片，就在 `_config.yml` 添加 `background: filename.png` 这样就可以实现！

