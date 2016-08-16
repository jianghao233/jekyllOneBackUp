---
layout: post
title: 2016-08-16 js札记
description: "学习的时刻"
tags: [笔记, javascript]
modified: 2016-08-10
categories: [笔记]
---

<!-- more  -->

### 单目加法运算符
将字符串转换为数字的另一种方法是使用单目加法运算符。

{% highlight javascript %}
"1.1" + "1.1" = "1.11.1"
(+"1.1") + (+"1.1") = 2.2   // 注：加入括号为清楚起见，不是必需的。
{% endhighlight %}

>`parseInt()`和`parseFloat()`
