---
layout: post
title: 在fc项目开发中炸鸡【札记】
description: "学习的时刻"
tags: [笔记, javascript]
modified: 2016-06-14
categories: [笔记]
---

一些注意的小知识嗲！！！

<!-- more -->

### 返回按钮

{% highlight html %}

<a type="button" href="javascript:window.history.back(-1);" class="btn btn-default">返回</a>
{% endhighlight %}

### dot使用：先判断有无属性，然后在添加属性
{% highlight javascript %}

{{?data.disabled}}disabled="disabled"{{?}}
{% endhighlight %}


### CSS让段落开头自动空两格代码
{% highlight CSS %}
.box{    text-indent:2em;}
{% endhighlight %}

### 转换钱钱，s字符串，n保留位数

{% highlight javascript %}
var moneyNumFormat = function(s,n){

	n = n > 0 && n <= 20 ? n : 2;   
	   s = parseFloat((s + "").replace(/[^\d\.-]/g, "")).toFixed(n) + "";   
	   var l = s.split(".")[0].split("").reverse(),   
	   r = s.split(".")[1];   
	   t = "";   
	   for(i = 0; i < l.length; i ++ )   
	   {   
	      t += l[i] + ((i + 1) % 3 == 0 && (i + 1) != l.length ? "," : "");   
	   }   
	   return t.split("").reverse().join("") + "." + r;   
}
{% endhighlight %}

### 随便限制任何dom内的内容字符

{% highlight javascript %}
$.fn.wordLimit = function(num){   
        this.each(function(){     
            if(!num){  
                var copyThis = $(this.cloneNode(true)).hide().css({  
                    'position': 'absolute',  
                    'width': 'auto',  
                    'overflow': 'visible'  
                });   
                $(this).after(copyThis);  
                if(copyThis.width()>$(this).width()){  
                    $(this).text($(this).text().substring(0,$(this).text().length-4));  
                    $(this).html($(this).html()+'...');  
                    copyThis.remove();  
                    $(this).wordLimit();  
                }else{  
                    copyThis.remove(); //清除复制  
                    return;  
                }     
            }else{  
                var maxwidth=num;  
                if($(this).text().length>maxwidth){  
                    $(this).text($(this).text().substring(0,maxwidth));  
                    $(this).html($(this).html()+'...');  
                }  
            }                      
        });  
    }
{% endhighlight %}


### 比上面那个还牛，限制字节数
{% highlight javascript %}

//xxx加，用来限制td的字符数


// 判断是否为全角

function yushiIsFull (pChar) {  
    if ((pChar.charCodeAt(0) > 128)) {  
        return true;  
    } else {  
        return false;  
    }  
}
//取得指定长度的字符串
function yushiCutString(pStr, pLen) {  

    // 原字符串长度  ，反斜杠都去掉
    var \_strLen = pStr.length;  

    var \_tmpCode;  

    var \_cutString;  

    // 默认情况下，返回的字符串是原字符串的一部分  
    var \_cutFlag = "1";  

    var \_lenCount = 0;  

    var \_ret = false;  

    if (\_strLen <= pLen/2) {  
        \_cutString = pStr;  
        \_ret = true;  
    }  

    if (!\_ret) {  
        for (var i = 0; i < \_strLen ; i++ ) {  
            if (yushiIsFull(pStr.charAt(i))) {  
                \_lenCount += 2;  
            } else {  
                \_lenCount += 1;  
            }  

            if (\_lenCount > pLen) {  
                \_cutString = pStr.substring(0, i);  
                \_ret = true;  
                break;  
            } else if (\_lenCount == pLen) {  
                \_cutString = pStr.substring(0, i + 1);  
                \_ret = true;  
                break;  
            }  
        }  
    }  

    if (!\_ret) {  
        \_cutString = pStr;  
        \_ret = true;  
    }  

    if (\_cutString.length == \_strLen) {  
        \_cutFlag = "0";  
    }  

    return {"cutstring":\_cutString, "cutflag":\_cutFlag};  
}

function yushiAutoAddEllipsis(pStr, pLen) {  

    var \_ret = yushiCutString(pStr, pLen);  
    var \_cutFlag = \_ret.cutflag;  
    var \_cutStringn = \_ret.cutstring;  

    if ("1" == \_cutFlag) {  
        return \_cutStringn + "...";  
    } else {  
        return \_cutStringn;  
    }  
}


$.fn.yushiWordLimit = function(limit){   
    this.each(function(){    
            var maxbytes=limit;  
            //两个星号前面的反斜杠 "\" ，去掉
            var strbytes = $(this).text().replace(/[^\x00-\xff]/g, "\**").length;
            if(strbytes>maxbytes){  
            	var newtext =  yushiAutoAddEllipsis($(this).text(),maxbytes);
                $(this).text(newtext);
                $(this).html($(this).html()+'...');  
            }                       
    });  
}        

//用法 $("td").yushiWordLimit("24");//限制td中的字节数

{% endhighlight %}

### form表单里面的input如果不想被编辑

form表单里面的input如果不想被编辑，但是有别的按钮可以修改，不是通过输入修改的，要用readonly = "readonly"
而不是disabled="disabled" ，

readonly = "readonly"            input内的值会被再次提交；
disabled="disabled"              input内的值不会被再次提交；
