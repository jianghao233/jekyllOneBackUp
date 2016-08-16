---
layout: post
title: jquery学习笔记（三）
description: "学习jquery时候"
tags: [笔记, 参数,jquery,js]
modified: 2016-02-16
categories: [笔记]
---


#### 返回 CSS 属性值
**注释：** 当用于返回一个值时，不支持简写的 CSS 属性（比如 "background" 和 "border"）。
{% highlight JavaScript %}
$(selector).css(name)
{% endhighlight %}

#### 设置 CSS 属性
{% highlight JavaScript %}
$(selector).css(“name”, “value”)
{% endhighlight %}

<!-- more -->

#### 设置多个 CSS 属性/值对
{% highlight JavaScript %}
$(selector).css({property:value, property:value, ...})
{% endhighlight %}

#### 使用函数来设置 CSS 属性
{% highlight JavaScript %}
$(selector).css(name,function(index,value))
{% endhighlight %}

* index - 可选。接受选择器的 index 位置
* oldvalue - 可选。接受 CSS 属性的当前值。字符串形式，若是要做数字运算，要用函数parseFloat专为数字

#### 返回偏移坐标
$(selector).offset()
该方法返回的对象包含两个整型属性：top 和 left，以像素计。此方法只对可见元素有效。

#### 设置偏移坐标
{% highlight JavaScript %}
$(selector).offset({top:100,left:0})
{% endhighlight %}

#### 使用函数来设置偏移坐标
{% highlight JavaScript %}
$(selector).offset(function(index,oldoffset))
{% endhighlight %}

* index - 可选。接受选择器的 index 位置
* oldvalue - 可选。接受选择器的当前坐标。

#### offsetParent() 方法返回最近的祖先定位元素。

#### position() 方法返回匹配元素相对于父元素的位置（偏移）。
该方法返回的对象包含两个整型属性：top 和 left，以像素计。

### 实例
{% highlight JavaScript %}
$(".btn1").click(function(){
  x=$("p").position();
  $("#span1").text(x.left);
  $("#span2").text(x.top);
});

{% endhighlight %}

## jQuery 参考手册 - DOM 元素方法

| 函数 | 描述 |
|:--------|:-------:|
| .get()  | 获得由选择器指定的 DOM 元素。 |
|----       
| .index()  | 返回指定元素相对于其他指定元素的 index 位置。  |
|----       
| .size() | 返回被 jQuery 选择器匹配的元素的数量。 |
|====      
| .toArray()  | 以数组的形式返回 jQuery 选择器匹配的元素。 |
{: rules="groups"}

## jQuery 参考手册 - 数据

| 函数 | 描述 |
|:--------|:-------:|
| .clearQueue() | 从队列中删除所有未运行的项目。 |
|----       
| .data() | 存储与匹配元素相关的任意数据。 |
|----       
| jQuery.data() | 存储与指定元素相关的任意数据。 |
|----       
| .dequeue()  | 从队列最前端移除一个队列函数，并执行它。  |
|----       
| jQuery.dequeue()  | 从队列最前端移除一个队列函数，并执行它。  |
|----       
| jQuery.hasData()  | 存储与匹配元素相关的任意数据。 |
|----       
| .queue()  | 显示或操作匹配元素所执行函数的队列。  |
|----       
| jQuery.queue()  | 显示或操作匹配元素所执行函数的队列。  |
|----       
| .removeData() | 移除之前存放的数据。  |
|====       
| jQuery.removeData() | 移除之前存放的数据。  |
{: rules="groups"}

## jQuery 参考手册 - 遍历

| 函数 | 描述 |
|:--------|:-------:|
| .add()  | 将元素添加到匹配元素的集合中。 |
|----       
| .andSelf()  | 把堆栈中之前的元素集添加到当前集合中。 但事实是看懂了，下次再看不知道还记得不，大概意思就是不仅仅选中具体到最后一个dom还要把前面参与选择的dom都选中 |
|----       
| .children() | 获得匹配元素集合中每个元素的所有子元素。  |
|----       
| .closest()  | 从元素本身开始，逐级向上级元素匹配，并返回最先匹配的祖先元素。 |
|----       
| .contents() | 获得匹配元素集合中每个元素的子元素，包括文本和注释节点。  |
|----       
| .each() | 对 jQuery 对象进行迭代，为每个匹配元素执行函数。  |
|----       
| .end()  | 结束当前链中最近的一次筛选操作，并将匹配元素集合返回到前一次的状态。  |
|----       
| .eq() | 将匹配元素集合缩减为位于指定索引的新元素。 |
|----       
| .filter() | 将匹配元素集合缩减为匹配选择器或匹配函数返回值的新元素。  |
|----       
| .find() | 获得当前匹配元素集合中每个元素的后代，由选择器进行筛选。  |
|----       
| .first()  | 将匹配元素集合缩减为集合中的第一个元素。  |
|----       
| .has()  | 将匹配元素集合缩减为包含特定元素的后代的集合。 |
|----       
| .is() | 根据选择器检查当前匹配元素集合，如果存在至少一个匹配元素，则返回 true。  |
|----       
| .last() | 将匹配元素集合缩减为集合中的最后一个元素。 |
|----       
| .map()  | 把当前匹配集合中的每个元素传递给函数，产生包含返回值的新 jQuery 对象。 |
|----       
| .next() | 获得匹配元素集合中每个元素紧邻的同辈元素。 |
|----       
| .nextAll()  | 获得匹配元素集合中每个元素之后的所有同辈元素，由选择器进行筛选（可选）。  |
|----       
| .nextUntil()  | 获得每个元素之后所有的同辈元素，直到遇到匹配选择器的元素为止。 |
|----       
| .not()  | 从匹配元素集合中删除元素。 |
|----       
| .offsetParent() | 获得用于定位的第一个父元素。  |
|----       
| .parent() | 获得当前匹配元素集合中每个元素的父元素，由选择器筛选（可选）。 |
|----       
| .parents()  | 获得当前匹配元素集合中每个元素的祖先元素，由选择器筛选（可选）。  |
|----       
| .parentsUntil() | 获得当前匹配元素集合中每个元素的祖先元素，直到遇到匹配选择器的元素为止。  |
|----       
| .prev() | 获得匹配元素集合中每个元素紧邻的前一个同辈元素，由选择器筛选（可选）。 |
|----       
| .prevAll()  | 获得匹配元素集合中每个元素之前的所有同辈元素，由选择器进行筛选（可选）。  |
|----       
| .prevUntil()  | 获得每个元素之前所有的同辈元素，直到遇到匹配选择器的元素为止。 |
|----       
| .siblings() | 获得匹配元素集合中所有元素的同辈元素，由选择器筛选（可选）。  |
|====      
| .slice()  | 将匹配元素集合缩减为指定范围的子集。  |
{: rules="groups"}

## jQuery 参考手册 – Ajax

| 函数 | 描述 |
|:--------|:-------:|
| jQuery.ajax() | 执行异步 HTTP (Ajax) 请求。  |
|----       
| .ajaxComplete() | 当 Ajax 请求完成时注册要调用的处理程序。这是一个 Ajax 事件。  |
|----       
| .ajaxError()  | 当 Ajax 请求完成且出现错误时注册要调用的处理程序。这是一个 Ajax 事件。 |
|----       
| .ajaxSend() | 在 Ajax 请求发送之前显示一条消息。  |
|----       
| jQuery.ajaxSetup()  | 设置将来的 Ajax 请求的默认值。  |
|----       
| .ajaxStart()  | 当首个 Ajax 请求完成开始时注册要调用的处理程序。这是一个 Ajax 事件。  |
|----       
| .ajaxStop() | 当所有 Ajax 请求完成时注册要调用的处理程序。这是一个 Ajax 事件。  |
|----       
| .ajaxSuccess()  | 当 Ajax 请求成功完成时显示一条消息。 |
|----       
| jQuery.get()  | 使用 HTTP GET 请求从服务器加载数据。 |
|----       
| jQuery.getJSON()  | 使用 HTTP GET 请求从服务器加载 JSON 编码数据。 |
|----       
| jQuery.getScript()  | 使用 HTTP GET 请求从服务器加载 JavaScript 文件，然后执行该文件。 |
|----       
| .load() | 从服务器加载数据，然后把返回到 HTML 放入匹配元素。  |
|----       
| jQuery.param()  | 创建数组或对象的序列化表示，适合在 URL 查询字符串或 Ajax 请求中使用。  |
|----       
| jQuery.post() | 使用 HTTP POST 请求从服务器加载数据。  |
|----       
| .serialize()  | 将表单内容序列化为字符串。 |
|====       
| .serializeArray() | 序列化表单元素，返回 JSON 数据结构数据。 |
{: rules="groups"}