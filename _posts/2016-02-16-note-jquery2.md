---
layout: post
title: jquery学习笔记（二）
description: "学习jquery时候"
tags: [笔记, 参数,jquery,js]
modified: 2016-02-16
categories: [笔记]
---

## jQuery - AJAX load() 方法

{% highlight JavaScript %}
$(selector).load(URL,data,callback);
//Example
$("#div1").load("demo_test.txt");      //把文件中所有内容，加载到指定的 div 元素中
$("#div1").load("demo_test.txt #p1");   //把文件中 id="p1" 的元素的内容，加载到指定的 div 元素中

{% endhighlight %}
可选的 callback 参数规定当 load() 方法完成后所要允许的回调函数。回调函数可以设置不同的参数：
  * responseTxt - 包含调用成功时的结果内容
  * statusTXT - 包含调用的状态
  * xhr - 包含 XMLHttpRequest 对象

<!-- more -->

## jQuery $.get() 方法
$.get() 方法通过 HTTP GET 请求从服务器上请求数据。

{% highlight JavaScript %}
$.get(URL,callback);
{% endhighlight %}

### 实例

{% highlight JavaScript %}
$("button").click(function(){
  $.get("demo_test.asp",function(data,status){
    alert("Data: " + data + "\nStatus: " + status);
  });
});

{% endhighlight %}
第二个参数是回调函数。第一个回调参数存有被请求页面的内容，第二个回调参数存有请求的状态。

## jQuery $.post() 方法

$.post() 方法通过 HTTP POST 请求从服务器上请求数据。
{% highlight JavaScript %}
$.post(URL,data,callback);
{% endhighlight %}
可选的 data 参数规定连同请求发送的数据。

## jQuery noConflict() 方法

noConflict() 方法会释放会 $ 标识符的控制，这样其他脚本就可以使用它了。
### 实例1

{% highlight JavaScript %}
$.noConflict();
jQuery(document).ready(function(){
  jQuery("button").click(function(){
    jQuery("p").text("jQuery 仍在运行！");
  });
});

{% endhighlight %}

### 实例2

{% highlight JavaScript %}
var jq = $.noConflict();
jq(document).ready(function(){
  jq("button").click(function(){
    jq("p").text("jQuery 仍在运行！");
  });
});
{% endhighlight %}

## jQuery 参考手册 - 事件

| 方法 | 实例 |
|:--------|:-------:|
| bind()  | 向匹配元素附加一个或更多事件处理器 |
|----       
| blur()  | 触发、或将函数绑定到指定元素的 blur   (当元素失去焦点时发生 blur 事件。)事件  |
|----       
| change()  | 触发、或将函数绑定到指定元素的 change 事件 |
|----       
| click() | 触发、或将函数绑定到指定元素的 click 事件  |
|----       
| dblclick()  | 触发、或将函数绑定到指定元素的 double click 事件 |
|----       
| delegate()  | 向匹配元素的当前或未来的子元素附加一个或多个事件处理器 |
|----       
| die() | 移除所有通过 live() 函数添加的事件处理程序。  |
|----       
| error() | 触发、或将函数绑定到指定元素的 error 事件  |
|----       
| event.isDefaultPrevented()  | 返回 event 对象上是否调用了 event.preventDefault()。 |
|----       
| event.pageX | 相对于文档左边缘的鼠标位置。  |
|----       
| event.pageY | 相对于文档上边缘的鼠标位置。  |
|----       
| event.preventDefault()  | 阻止事件的默认动作。  |
|----       
| event.result  | 包含由被指定事件触发的事件处理器返回的最后一个值。 |
|----       
| event.target  | 触发该事件的 DOM 元素。  |
|----       
| event.timeStamp | 该属性返回从 1970 年 1 月 1 日到事件发生时的毫秒数。  |
|----       
| event.type  | 描述事件的类型。  |
|----       
| event.which | 指示按了哪个键或按钮。 |
|----       
| focus() | 触发、或将函数绑定到指定元素的 focus 事件  |
|----       
| keydown() | 触发、或将函数绑定到指定元素的 key down 事件 |
|----       
| keypress()  | 触发、或将函数绑定到指定元素的 key press 事件  |
|----       
| keyup() | 触发、或将函数绑定到指定元素的 key up 事件 |
|----       
| live()  | 为当前或未来的匹配元素添加一个或多个事件处理器 |
|----       
| load()  | 触发、或将函数绑定到指定元素的 load 事件 |
|----       
| mousedown() | 触发、或将函数绑定到指定元素的 mouse down 事件 |
|----       
| mouseenter()  | 触发、或将函数绑定到指定元素的 mouse enter 事件  |
|----       
| mouseleave()  | 触发、或将函数绑定到指定元素的 mouse leave 事件  |
|----       
| mousemove() | 触发、或将函数绑定到指定元素的 mouse move 事件 |
|----       
| mouseout()  | 触发、或将函数绑定到指定元素的 mouse out 事件  |
|----       
| mouseover() | 触发、或将函数绑定到指定元素的 mouse over 事件 |
|----       
| mouseup() | 触发、或将函数绑定到指定元素的 mouse up 事件 |
|----       
| one() | 向匹配元素添加事件处理器。每个元素只能触发一次该处理器。  |
|----       
| ready() | 文档就绪事件（当 HTML 文档就绪可用时）  |
|----       
| resize()  | 当调整浏览器窗口的大小时，发生 resize 事件。  |
|----       
| scroll()  | 当用户滚动指定的元素时，会发生 scroll 事件。  |
|----       
| select()  | 当 textarea 或文本类型的 input 元素中的文本被选择时，会发生 select 事件。 |
|----       
| submit()  | 当提交表单时，会发生 submit 事件，该事件只适用于表单元素。 |
|----       
| toggle()  | 绑定两个或多个事件处理器函数，当发生轮流的 click 事件时执行。  |
|----       
| trigger() | 所有匹配元素的指定事件 |
|----       
| triggerHandler()  | 第一个被匹配元素的指定事件 |
|----       
| unbind()  | 从匹配元素移除一个被添加的事件处理器  |
|----       
| undelegate()  | 从匹配元素移除一个被添加的事件处理器，现在或将来  |
|=====      
| unload()  | 当用户离开页面时，会发生 unload 事件。 |
{: rules="groups"}

#### bind

{% highlight JavaScript %}
$(selector).bind({event:function, event:function, ...})
{% endhighlight %}

#### live

为被选元素附加一个或多个事件处理程序，并规定当这些事件发生时运行的函数。使用方法等同于bind ，但是结果优于bind,下面例子


{% highlight Html %}
<head>
<script type="text/javascript" src="/jquery/jquery.js"></script>
<script type="text/javascript">
$(document).ready(function(){
  $("p").live("click",function(){
    $(this).slideToggle();
  });
  $("button").click(function(){
    $("<p>This is a new paragraph.</p>").insertAfter("button");
  });
});
</script>
</head>
<body>
<p>这是一个段落。</p>
<p>点击任意 p 元素会令其消失。包括本段落。</p>
<button>在本按钮后面插入新的 p 元素</button>
<p><b>注释：</b>通过使用 live() 方法而不是 bind() 方法，新的 p 元素同样会在点击时消失。</p>
</body>

{% endhighlight %}

#### change  

当元素的值发生改变时，会发生 change 事件,该事件仅适用于文本域（text field），以及 textarea 和 select 元素。

#### delegate()
方法为指定的元素（属于被选元素的子元素）添加一个或多个事件处理程序，并规定当这些事件发生时运行的函数。

{% highlight JavaScript %}
$(selector).delegate(childSelector,event,data,function)
{% endhighlight %}

childSelector 必需。规定要附加事件处理程序的一个或多个子元素。

#### die()
方法移除所有通过 live() 方法向指定元素添加的一个或多个事件处理程序。

#### error()
方法触发 error 事件，或规定当发生 error 事件时运行的函数。
**提示：** 该方法是 bind('error', handler) 的简写方式。

#### preventDefault()
方法阻止元素发生默认的行为（例如，当点击提交按钮时阻止对表单的提交）。

#### result 
属性包含由被指定事件触发的事件处理器返回的最后一个值，除非这个值未定义。例子:
{% highlight Html %}
<head>
<script type="text/javascript" src="/jquery/jquery.js"></script>
<script type="text/javascript">
$(document).ready(function(){
  $("button").click(function(e) {
    return ("最后一次点击的鼠标位置是： X" +e.pageX + ", Y" + e.pageY);
  });
  $("button").click(function(e) {
    $("p").html(e.result);
  });  
});
</script>
</head>
<body>
<p>这是一个段落。</p>
<button>请点击这里</button>
</body>

{% endhighlight %}

当鼠标指针移动到元素上方，并按下鼠标按键时，会发生 mousedown 事件。
与 click 事件不同，mousedown 事件仅需要按键被按下，而不需要松开即可发生。
**注释：** 与 mouseover 事件不同，只有在鼠标指针穿过被选元素时，才会触发 mouseenter 事件。如果鼠标指针穿过任何子元素，同样会触发 mouseover 事件。用户把鼠标移动一个像素，就会发生一次 mousemove 事件。处理所有 mousemove 事件会耗费系统资源。请谨慎使用该事件。

{% highlight JavaScript %}
$(document).ready(function) ==  $().ready(function)  ===  $(function)
语法 1                                    语法 2                     语法 3  

{% endhighlight %}

**trigger()** 方法触发被选元素的指定事件类型。
**triggerHandler()** 方法触发被选元素的指定事件类型。但不会执行浏览器默认动作，也不会产生事件冒泡。
**triggerHandler()** 方法与 trigger() 方法类似。不同的是它不会触发事件（比如表单提交）的默认行为，而且只影响第一个匹配元素。

### 与 trigger() 方法相比的不同之处
* 它不会引起事件（比如表单提交）的默认行为
* .trigger() 会操作 jQuery 对象匹配的所有元素，而 .triggerHandler() 只影响第一个匹配元素。
* 由 .triggerHandler() 创建的事件不会在 DOM 树中冒泡；如果目标元素不直接处理它们，则不会发生任何事情。
* 该方法的返回的是事件处理函数的返回值，而不是具有可链性的 jQuery 对象。此外，如果没有处理程序被触发，则这个方法返回 undefined。

## jQuery 参考手册 - 效果

| 方法 | 描述 |
|:--------|:-------:|
| animate() | 对被选元素应用“自定义”的动画 |
|----       
| clearQueue()  | 对被选元素移除所有排队的函数（仍未运行的） |
|----       
| delay() | 对被选元素的所有排队函数（仍未运行）设置延迟  |
|----       
| dequeue() | 运行被选元素的下一个排队函数  |
|----       
| fadeIn()  | 逐渐改变被选元素的不透明度，从隐藏到可见  |
|----       
| fadeOut() | 逐渐改变被选元素的不透明度，从可见到隐藏  |
|----       
| fadeTo()  | 把被选元素逐渐改变至给定的不透明度 |
|----       
| hide()  | 隐藏被选的元素 |
|----       
| queue() | 显示被选元素的排队函数 |
|----       
| show()  | 显示被选的元素 |
|----       
| slideDown() | 通过调整高度来滑动显示被选元素 |
|----       
| slideToggle() | 对被选元素进行滑动隐藏和滑动显示的切换 |
|----       
| slideUp() | 通过调整高度来滑动隐藏被选元素 |
|----       
| stop()  | 停止在被选元素上运行动画  |
|====       
| toggle()  | 对被选元素进行隐藏和显示的切换 |
{: rules="groups"}

## jQuery 参考手册 - 文档操作

| 方法 | 描述 |
|:--------|:-------:|
| addClass()  | 向匹配的元素添加指定的类名。  |
|----       
| after() | 在匹配的元素之后插入内容。 |
|----       
| append()  | 向匹配元素集合中的每个元素结尾插入由参数指定的内容。  |
|----       
| appendTo()  | 向目标结尾插入匹配元素集合中的每个元素。  |
|----       
| attr()  | 设置或返回匹配元素的属性和值。 |
|----       
| before()  | 在每个匹配的元素之前插入内容。 |
|----       
| clone() | 创建匹配元素集合的副本。  |
|----       
| detach()  | 从 DOM 中移除匹配元素集合。  |
|----       
| empty() | 删除匹配的元素集合中所有的子节点。 |
|----       
| hasClass()  | 检查匹配的元素是否拥有指定的类。  |
|----       
| html()  | 设置或返回匹配的元素集合中的 HTML 内容。 |
|----       
| insertAfter() | 把匹配的元素插入到另一个指定的元素集合的后面。 |
|----       
| insertBefore()  | 把匹配的元素插入到另一个指定的元素集合的前面。 |
|----       
| prepend() | 向匹配元素集合中的每个元素开头插入由参数指定的内容。  |
|----       
| prependTo() | 向目标开头插入匹配元素集合中的每个元素。  |
|----       
| remove()  | 移除所有匹配的元素。  |
|----       
| removeAttr()  | 从所有匹配的元素中移除指定的属性。 |
|----       
| removeClass() | 从所有匹配的元素中删除全部或者指定的类。  |
|----       
| replaceAll()  | 用匹配的元素替换所有匹配到的元素。 |
|----       
| replaceWith() | 用新内容替换匹配的元素。  |
|----       
| text()  | 设置或返回匹配元素的内容。 |
|----       
| toggleClass() | 从匹配的元素中添加或删除一个类。  |
|----       
| unwrap()  | 移除并替换指定元素的父元素。  |
|----       
| val() | 设置或返回匹配元素的值。  |
|----       
| wrap()  | 把匹配的元素用指定的内容或元素包裹起来。      分别  |
|----       
| wrapAll() | 把所有匹配的元素用指定的内容或元素包裹起来。     整个   |
|====    
| wrapinner() | 将每一个匹配的元素的子内容用指定的内容或元素包裹起来。 |
{: rules="groups"}

#### detach() 方法移除被选元素，包括所有文本和子节点。

这个方法会保留 jQuery 对象中的匹配的元素，因而可以在将来再使用这些匹配的元素。
detach() 会保留所有绑定的事件、附加的数据，这一点与 remove() 不同。

#### html()
方法返回或设置被选元素的内容 (inner HTML)。如果该方法未设置参数，则返回被选元素的当前内容。

#### remove() 方法移除被选元素，包括所有文本和子节点。
该方法不会把匹配的元素从 jQuery 对象中删除，因而可以在将来再使用这些匹配的元素。
但除了这个元素本身得以保留之外，remove() 不会保留元素的 jQuery 数据。其他的比如绑定的事件、附加的数据等都会被移除。这一点与 detach() 不同。

#### replaceAll()
replaceAll() 与 replaceWith() 作用相同，差异在于语法：内容和选择器的位置，以及 replaceWith() 能够使用函数进行替换。
{% highlight JavaScript %}
$(selector).replaceWith(content)
$(content).replaceAll(selector)
{% endhighlight %}

#### wrapInner()
方法使用指定的 HTML 内容或元素，来包裹每个被选元素中的所有内容 (inner HTML)。

## jQuery 参考手册 - 属性操作

| 方法 | 描述 |
|:--------|:-------:|
| addClass()  | 向匹配的元素添加指定的类名。  |
|----       
| attr()  | 设置或返回匹配元素的属性和值。 |
|----       
| hasClass()  | 检查匹配的元素是否拥有指定的类。  |
|----       
| html()  | 设置或返回匹配的元素集合中的 HTML 内容。 |
|----       
| removeAttr()  | 从所有匹配的元素中移除指定的属性。 |
|----       
| removeClass() | 从所有匹配的元素中删除全部或者指定的类。  |
|----       
| toggleClass() | 从匹配的元素中添加或删除一个类。  |
|====       
| val() | 设置或返回匹配元素的值。  |
{: rules="groups"}

## jQuery 参考手册 - CSS 操作

| CSS 属性 | 描述 |
|:--------|:-------:|
| css() | 设置或返回匹配元素的样式属性。 |
|----       
| height()  | 设置或返回匹配元素的高度。 |
|----       
| offset()  | 返回第一个匹配元素相对于文档的位置。  |
|----       
| offsetParent()  | 返回最近的定位祖先元素。  |
|----       
| position()  | 返回第一个匹配元素相对于父元素的位置。 |
|----       
| scrollLeft()  | 设置或返回匹配元素相对滚动条左侧的偏移。  |
|----       
| scrollTop() | 设置或返回匹配元素相对滚动条顶部的偏移。  |
|====     
| width() | 设置或返回匹配元素的宽度。 |
{: rules="groups"}