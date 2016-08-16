---
layout: post
title: jquery实践笔记
description: "学习jqueasdasdry时候"
tags: [笔记, 参数,jquery,js]
modified: 2016-02-24
categories: [笔记]
---

### 动画

停止动画的时候用stop()函数,
立即停止动画要这样学：
{% highlight JavaScript %}
$(selector).stop(stopAll,goToEnd);
$(selector).stop(true,true);
{% endhighlight %}
解释可选的 stopAll 参数规定是否应该清除动画队列。默认是 false，即仅停止活动的动画，允许任何排入队列的动画向后执行。
可选的 goToEnd 参数规定是否立即~完成当前动画。默认是 false。
因此，默认地，stop() 会清除在被选元素上指定的当前动画。


<!-- more -->

## 关于input的checkbox 的checked属性！

我遇到的问题是，用jquery控制checkbox的选中与否，用的是checked属性。就是要实现联动，比如点击别的东西，是的这个checkbox点击完成，结果第一次点击可以成功，但是取消选中后再次点击，不能实现联动。
解决办法是：
{% highlight javascript %}
.prop("checked", true); 
{% endhighlight %}
使用prop，不要用：
{% highlight javascript %}
.attr("checked", true); 
{% endhighlight %}

### indexOf查询

变量必须为字符串，不是字符串的，请toString()

### on事件