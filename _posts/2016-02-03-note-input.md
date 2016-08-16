---
layout: post
title: html笔记
description: "总结平时的问题"
tags: [笔记, html]
modified: 2016-02-04
categories: [笔记]
---


### 关于input的问题

首先是在多行表格内都有 
{% highlight html %}
<input type='radio'>
{% endhighlight %}
因为每个单元格唯一，所以出现每个input都可以选中，不能单选。解决办法是加一个name标签
{% highlight html %}
<input type='radio' name='state'>
{% endhighlight %}

<!-- more -->

## 关于input的checkbox 的checked属性！

我遇到的问题是，用jquery控制checkbox的选中与否，用的是checked属性，结果导致第一次点击
可以成功，但是取消选中后再次点击，不能实现联动。
解决办法是：
{% highlight javascript %}
.prop("checked", true); 
{% endhighlight %}
使用prop，不要用：
{% highlight javascript %}
.attr("checked", true); 
{% endhighlight %}

### 第二个问题是一条js判断，最初我是这样写的：

{% highlight javascript %}
if($(".table").find("input").attr("checked")==true){
           		var hehe = $(".table").find("input[name='state']:checked").parent().siblings("td:last").children(a).attr("href");
           		
           			arr=hehe.split("=");
           			console.log(arr[1])
           		var	baseClientInfoId=arr[1];
           		str = baseClientInfoId+","+accountID+","+prid;
           		
              	window.location="${ctx}/baseClientInfoManage/baseClientInfo/creatBaseClientInfo?baseClientInfoID="+str; 
           	}else{
           		alert("你需要选中才能开户")
       			};
{% endhighlight %}
这样遇到的问题是有两个，一个是要在html中的input 里面加上checked="",这样的结果是刷新页面就会有一个选项已经被选中了，不行！
第二个问题是因为是遍历所有的input，所以只要有input没有checked就会alert，所以上述写法本身逻辑就出现错误了！不行！
然后请教大神（大神想了两秒），解决办法如下：
{% highlight javascript %}
if($(".table").find("input[name='state']:checked").size()>0){
           		var hehe = $(".table").find("input[name='state']:checked").parent().siblings("td:last").children(a).attr("href");
           		
           			arr=hehe.split("=");
           			console.log(arr[1])
           		var	baseClientInfoId=arr[1];
           		str = baseClientInfoId+","+accountID+","+prid;
           		
              	window.location="${ctx}/baseClientInfoManage/baseClientInfo/creatBaseClientInfo?baseClientInfoID="+str; 
           	}else{
           		alert("你需要选中才能开户")
       			};
{% endhighlight %}
学习到的东西 input[name='state']:checked



### 关于input的问题
对于旧的页面，左侧导航的链接点击后跳转新页面，加载之前页面的状态会被清除，给二级菜单添加样式就需要对比当前连接和导航链接，代码如下：
{% highlight javascript %}
$(document).ready(function($){           
      var urlstr = location.href;          //获得当前页面url
      //console.log(urlstr);
      $(".sub-menu-list a").each(function () {            
    if ((urlstr + '/').indexOf($(this).attr('href')) > -1) {           //在当前页面rul里面寻找导航的链接，有就返回0，没有返回-1
          $(this).addClass('active');
          $(this).parents('.menu-list').addClass('nav-active')
        } else {
          $(this).removeClass('active');
        }     
    });
{% endhighlight %}
这样也会有bug，比如某两个页面的链接是 xxxxxxxxx/list  &&   xxxxxxxxx/list_xx。所以把条件改成
{% highlight javascript %}
if ($(this)[0].href == String(window.location)) {
{% endhighlight %}
这样又会出现问题，如果list页面内有manage页，仅仅把url最后面的list换成managexxxxxx等，这样就不能定位manage页面了