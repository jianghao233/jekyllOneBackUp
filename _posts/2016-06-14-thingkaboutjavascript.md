---
layout: post
title: 关于js中类方法、对象方法、原型方法区别
description: "学习的时刻"
tags: [笔记, javascript]
modified: 2016-06-14
categories: [笔记]
---

JavaScript 不包含传统的类继承模型，而是使用 prototype 原型模型。
虽然这经常被当作是 JavaScript 的缺点被提及，其实基于原型的继承模型比传统的类继承还要强大。 实现传统的类继承模型是
很简单，但是实现 JavaScript 中的原型继承则要困难的多。 (It is for example fairly trivial to build a classic model on top of it,
while the other way around is a far more difficult task.)

<!-- more -->

{% highlight javascript %}
// 关于类方法、对象方法、原型方法区别

<script type="text/javascript">

function baseClass()
{
//写在闭包内部的 就是对象方法，不要问为什么，记住就好
    this.showMsg = function()
    {
        alert("baseClass::showMsg");   
    }

    this.baseShowMsg = function()
    {
        alert("baseClass::baseShowMsg");
    }
}
//定义在外面的就是类方法
baseClass.showMsg = function()
{
    alert("baseClass::showMsg static");
}

function extendClass()
{
    this.showMsg =function ()
    {
        alert("extendClass::showMsg");
    }
}
extendClass.showMsg = function()
{
    alert("extendClass::showMsg static")
}
下面这样的甬道prototype的就是原型方法
extendClass.prototype = new baseClass();
var instance = new extendClass();



//下面是分别的调用方法
//调用对象，prototype不会克隆同名函数。来自extendClass中的showMsg
instance.showMsg(); //显示extendClass::showMsg
//调用对象
instance.baseShowMsg(); //显示baseClass::baseShowMsg
//调用对象，prototype不会克隆同名函数。来自extendClass中的showMsg
instance.showMsg(); //显示extendClass::showMsg

//调用类方法
baseClass.showMsg.call(instance);//显示baseClass::showMsg static


//调用对象，即使有同名，还是调用baseClass中的对象
var baseinstance = new baseClass();
baseinstance.showMsg.call(instance);//显示baseClass::showMsg

</script>
{% endhighlight %}
