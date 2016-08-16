---
layout: post
title: jquery学习笔记（一）
description: "学习jquery时候"
tags: [笔记, 参数,jquery,js]
modified: 2016-02-16
categories: [笔记]
---

### 规范

{% highlight JavaScript %}
$(document).ready(function(){
--- jQuery functions go here ----
});
------------------------------------------------------------------------
$(this).hide()
$(this).show()
$(this).toggle()
------------------------------------------------------------------------
$(this).fadeIn()
$(this).fadeOut()
$(this).fadeToggle()
$(selector).fadeTo(speed,opacity,callback);
------------------------------------------------------------------------
$(selector).slideDown(speed,callback);
$(selector).slideUp(speed,callback);
$(selector).slideToggle(speed,callback);
------------------------------------------------------------------------
{% endhighlight %}

{% highlight JavaScript %}
$(selector).animate({params},speed,callback);
{% endhighlight %}
必需的 params 参数定义形成动画的 CSS 属性。
可选的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。
可选的 callback 参数是动画完成后所执行的函数名称。
提示：默认地，所有 HTML 元素都有一个静态位置，且无法移动。
如需对位置进行操作，要记得首先把元素的 CSS position 属性设置为 relative、fixed 或 absolute！
当使用 animate() 时，必须使用 Camel 标记法书写所有的属性名，比如，必须使用 paddingLeft 而不是 padding-left，使用 marginRight 而不是 margin-right，等等。

<!-- more -->

jQuery animate() - 使用相对值
也可以定义相对值（该值相对于元素的当前值）。需要在值的前面加上 += 或 -=：

jQuery animate() - 使用预定义的值
你甚至可以把属性的动画值设置为 "show"、"hide" 或 "toggle"：

#### 实例
{% highlight JavaScript %}
$("button").click(function(){
  $("div").animate({
    height:'toggle'
  });
});

{% endhighlight %}

### jQuery animate() - 使用队列功能
默认地，jQuery 提供针对动画的队列功能。
这意味着如果您在彼此之后编写多个 animate() 调用，jQuery 会创建包含这些方法调用的“内部”队列。然后逐一运行这些 animate 调用。
实例 1
隐藏，如果您希望在彼此之后执行不同的动画，那么我们要利用队列功能：
{% highlight JavaScript %}
$("button").click(function(){
  var div=$("div");
  div.animate({height:'300px',opacity:'0.4'},"slow");
  div.animate({width:'300px',opacity:'0.8'},"slow");
  div.animate({height:'100px',opacity:'0.4'},"slow");
  div.animate({width:'100px',opacity:'0.8'},"slow");
});

{% endhighlight %}
{% highlight JavaScript %}
$(selector).stop(stopAll,goToEnd);
{% endhighlight %}
可选的 stopAll 参数规定是否应该清除动画队列。默认是 false，即仅停止活动的动画，允许任何排入队列的动画向后执行。
可选的 goToEnd 参数规定是否立即完成当前动画。默认是 false。
因此，默认地，stop() 会清除在被选元素上指定的当前动画。
由于 JavaScript 语句（指令）是逐一执行的 - 按照次序，动画之后的语句可能会产生错误或页面冲突，因为动画还没有完成。为了避免这个情况，您可以以参数的形式添加 Callback 函数。当动画 100% 完成后，即调用 Callback 函数。

### 获得内容 - text()、html() 以及 val()
三个简单实用的用于 DOM 操作的 jQuery 方法：
	* text() - 设置或返回所选元素的文本内容
	* html() - 设置或返回所选元素的内容（包括 HTML 标记）
	* val() - 设置或返回表单字段的值

#### 实例
{% highlight JavaScript %}
$("#test").val()
$("#test").html()
$("#test").text()
{% endhighlight %}
修改上述三个只需要在括号内写“内容”即可。
修改下面这个，也就是元素属性的时候，需要按照格式
{% highlight JavaScript %}
$("#w3s").attr("href","xxxxxxxxx");            ------------------单一属性
$("#w3s").attr({
      "href" : "http://www.masteryu.site/",
      "title" : "呵呵"
    });                                              --------------------多条属性

{% endhighlight %}
### jQuery attr() 方法用于获取属性值。
{% highlight JavaScript %}
$("#w3s").attr("href")
{% endhighlight %}
### text()、html() 以及 val() 的回调函数
上面的三个 jQuery 方法：text()、html() 以及 val()，同样拥有回调函数。回调函数由两个参数：被选元素列表中当前元素的下标，以及原始（旧的）值。然后以函数新值返回您希望使用的字符串。

#### 实例
{% highlight JavaScript %}
$("#btn1").click(function(){
  $("#test1").text(function(i,origText){
    return "Old text: " + origText + " New text: Hello world!
    (index: " + i + ")";
  });


});

{% endhighlight %}

### attr() 的回调函数
jQuery 方法 attr()，也提供回调函数。回调函数由两个参数：被选元素列表中当前元素的下标，以及原始（旧的）值。然后以函数新值返回您希望使用的字符串。
#### 实例
{% highlight JavaScript %}
$("button").click(function(){
  $("#w3s").attr("href", function(i,origValue){
    return origValue + "/jquery";
  });
});

{% endhighlight %}
### 通过 jQuery，可以很容易地添加新元素/内容。
* append() - 在被选元素的结尾插入内容      区别是一个在备选元素内部
* prepend() - 在被选元素的开头插入内容
* after() - 在被选元素之后插入内容            这个在备选元素之后
* before() - 在被选元素之前插入内容
{% highlight JavaScript %}
$("p").append("Some appended text.");

{% endhighlight %}
Or
{% highlight JavaScript %}
function appendText()
{
var txt1="<p>Text.</p>";               // 以 HTML 创建新元素
var txt2=$("<p></p>").text("Text.");   // 以 jQuery 创建新元素
var txt3=document.createElement("p");  // 以 DOM 创建新元素
txt3.innerHTML="Text.";
$("p").append(txt1,txt2,txt3);         // 追加新元素
}

{% endhighlight %}
### 删除元素/内容
如需删除元素和内容，一般可使用以下两个 jQuery 方法：
* remove() - 删除被选元素（及其子元素）
* empty() - 从被选元素中删除子元素
### 过滤被删除的元素
{% highlight JavaScript %}
$("p").remove(".italic");
{% endhighlight %}
### jQuery 操作 CSS
* addClass() - 向被选元素添加一个或多个类
* removeClass() - 从被选元素删除一个或多个类
* toggleClass() - 对被选元素进行添加/删除类的切换操作
* css() - 设置或返回样式属性
### 返回 CSS 属性
下面的例子将返回首个匹配元素的 background-color 值：
{% highlight JavaScript %}
$("p").css("background-color");
{% endhighlight %}
### 设置 CSS 属性
如需设置指定的 CSS 属性，请使用如下语法：
{% highlight JavaScript %}
css("propertyname","value");
{% endhighlight %}
下面的例子将为所有匹配元素设置 background-color 值：
{% highlight JavaScript %}
$("p").css("background-color","yellow");
{% endhighlight %}

### 设置多个 CSS 属性
如需设置多个 CSS 属性，请使用如下语法：
{% highlight JavaScript %}
css({"propertyname":"value","propertyname":"value",...});
{% endhighlight %}
### jQuery 尺寸 方法
* width()     方法设置或返回元素的宽度（不包括内边距、边框或外边距）。
* height()    方法设置或返回元素的高度（不包括内边距、边框或外边距）。
* innerWidth()    方法返回元素的宽度（包括内边距）。
* innerHeight()    方法返回元素的高度（包括内边距）。
* outerWidth()    方法返回元素的宽度（包括内边距和边框）。 
* outerHeight()    方法返回元素的高度（包括内边距和边框）。
* outerWidth(true)      方法返回元素的宽度（包括内边距、边框和外边距）。
* outerHeight(true)     方法返回元素的高度（包括内边距、边框和外边距）。
{% highlight JavaScript %}
$("#div1").width(500).height(500);     //不用双引号
{% endhighlight %}

## jQuery 遍历

### 向上遍历 DOM 树
这些 jQuery 方法很有用，它们用于向上遍历 DOM 树：

*  parent()    返回被选元素的直接父元素。
*  parents()    返回被选元素的所有祖先元素，它一路向上直到文档的根元素 (<html>)。
*  parentsUntil()    返回介于两个给定元素之间的所有祖先元素。
下面的例子返回介于 <span> 与 <div> 元素之间的所有祖先元素：
{% highlight JavaScript %}
  $("span").parentsUntil("div");
{% endhighlight %}

### 向下遍历 DOM 树
下面是两个用于向下遍历 DOM 树的 jQuery 方法：

*  children()    返回被选元素的所有直接子元素。
*  find()   返回被选元素的后代元素，一路向下直到最后一个后代。
*  find(*)   返回被选元素的所有后代元素

### 在 DOM 树中水平遍历

有许多有用的方法让我们在 DOM 树进行水平遍历：

*  siblings()   返回被选元素的所有同胞元素。
*  next()    返回被选元素的下一个同胞元素。
*  nextAll()    返回被选元素的所有跟随的同胞元素。
*  nextUntil()   返回介于两个给定参数之间的所有跟随的同胞元素。
*  prev()
*  prevAll()
*  prevUntil()

其他过滤方法

*  first()      返回被选元素的首个元素。
*  last()     返回被选元素的最后一个元素。
*  even()     偶数元素
*  odd()      奇数元素
*  eq()        返回被选元素中带有指定索引号的元素。索引号从 0 开始
*  filter()     允许您规定一个标准。不匹配这个标准的元素会被从集合中删除，匹配的元素会被返回。
*  not()       返回不匹配标准的所有元素。

### jQuery 选择器



| 选择器 | 实例 | 选取 |
|:--------|:-------:|--------:|
| *   | $("*")   | 所有元素   |
|----
| #id   | $("#lastname")   | id="lastname" 的元素   |
|----
| .class   | $(".intro")   | 所有 class="intro" 的元素   |
|----
| element   | $("p")   | 所有 <p> 元素   |
|----
| .class.class   | $(".intro.demo")   | 所有 class="intro" 且 class="demo" 的元素   |
|----
| :first   | $("p:first")   | 第一个 <p> 元素   |
|----
| :last   | $("p:last")   | 最后一个 <p> 元素   |
|----
| :even   | $("tr:even")   | 所有偶数 <tr> 元素   |
|----
| :odd   | $("tr:odd")   | 燕北飞6   |
|----
| 燕北飞4   | 燕北飞5   | 所有奇数 <tr> 元素   |
|----
| :eq(index)  | $("ul li:eq(3)")  | 列表中的第四个元素（index 从 0 开始） |
|----           
| :gt(no) | $("ul li:gt(3)")  | 列出 index 大于 3 的元素 |
|----           
| :lt(no) | $("ul li:lt(3)")  | 列出 index 小于 3 的元素 |
|----           
| :not(selector)  | $("input:not(:empty)")  | 所有不为空的 input 元素 |
|----           
| :header | $(":header")  | 所有标题元素 <h1> - <h6>  |
|----           
| :animated |   | 所有动画元素  |
|----           
| :contains(text) | $(":contains('W3School')")  | 包含指定字符串的所有元素  |
|----           
| :empty  | $(":empty") | 无子（元素）节点的所有元素 |
|----           
| :hidden | $("p:hidden") | 所有隐藏的 <p> 元素  |
|----           
| :visible  | $("table:visible")  | 所有可见的表格 |
|----           
| s1,s2,s3  | $("th,td,.intro") | 所有带有匹配选择的元素 |
|----           
| [attribute] | $("[href]") | 所有带有 href 属性的元素 |
|----           
| [attribute=value] | $("[href='#']") | 所有 href 属性的值等于 "#" 的元素  |
|----           
| [attribute!=value]  | $("[href!='#']")  | 所有 href 属性的值不等于 "#" 的元素 |
|----           
| [attribute$=value]  | $("[href$='.jpg']") | 所有 href 属性的值包含以 ".jpg" 结尾的元素  |
|----           
| :input  | $(":input") | 所有 input 元素 |
|----           
| :text | $(":text")  | 所有 type="text" 的 input 元素 |
|----           
| :password | $(":password")  | 所有 type="password" 的 input 元素 |
|----           
| :radio  | $(":radio") | 所有 type="radio" 的 input 元素  |
|----           
| :checkbox | $(":checkbox")  | 所有 type="checkbox" 的 input 元素 |
|----           
| :submit | $(":submit")  | 所有 type="submit" 的 input 元素 |
|----           
| :reset  | $(":reset") | 所有 type="reset" 的 input 元素  |
|----           
| :button | $(":button")  | 所有 type="button" 的 input 元素 |
|----           
| :image  | $(":image") | 所有 type="image" 的 input 元素  |
|----           
| :file | $(":file")  | 所有 type="file" 的 input 元素 |
|----           
| :enabled  | $(":enabled") | 所有激活的 input 元素  |
|----           
| :disabled | $(":disabled")  | 所有禁用的 input 元素  |
|----           
| :selected | $(":selected")  | 所有被选取的 input 元素 |      
|=====
| :checked  | $(":checked") | 所有被选中的 input 元素 |
{: rules="groups"}