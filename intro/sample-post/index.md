---
layout: post
title: 教你如何用
description: "一些样式"
modified: 2014-12-24
tags: [示例]
categories: [模板]
---



# 标题 1

## 标题 2

### 标题 3

#### 标题 4

##### 标题 5

###### 标题 6

### 正文文本

**这是加粗文本**

![Smithsonian Image]({{ site.url }}/images/3953273590_704e3899d5_m.jpg)
{: .image-right}

*这是斜体*
H<sub>2</sub>O
<cite>(这是引用)</cite>
<u>下划线</u>

<abbr title="缩写">缩写<abbr> 

### 引用

> 飞雪连天射白鹿,笑书神侠倚碧鸳

## 列表格式

### 有序

1. 秋风清
   1. 秋风清1
   2. 秋风清2
   3. 秋风清3
2. 秋风清2

### 无序

* 秋风清
* 秋风清
* 秋风清


## 表格

| 扫地僧 | 扫地僧 | 扫地僧 |
|:--------|:-------:|--------:|
| 燕北飞1   | 燕北飞2   | 燕北飞3   |
| 燕北飞4   | 燕北飞5   | 燕北飞6   |
|----
| 燕北飞1   | 燕北飞2   | 燕北飞3   |
| 燕北飞4   | 燕北飞5   | 燕北飞6   |
|=====
| 倚天剑  | 倚天剑   | 倚天剑
{: rules="groups"}

## 代码

高亮用的是Pygments

{% highlight css %}
#container {
  float: left;
  margin: 0 -240px 0 0;
  width: 100%;
}
{% endhighlight %}

不高亮长这样

    <div id="awesome">
        <p>This is great isn't it?</p>
    </div>

## 按钮

跟bootstrap一样加一个 `.btn` class.

{% highlight html %}
<a href="#" class="btn btn-success">Success Button</a>
{% endhighlight %}

<div markdown="0"><a href="#" class="btn">Primary Button</a></div>
<div markdown="0"><a href="#" class="btn btn-success">Success Button</a></div>
<div markdown="0"><a href="#" class="btn btn-warning">Warning Button</a></div>
<div markdown="0"><a href="#" class="btn btn-danger">Danger Button</a></div>
<div markdown="0"><a href="#" class="btn btn-info">Info Button</a></div>
