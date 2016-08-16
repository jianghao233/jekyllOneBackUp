---
layout: post
title: javascript学习笔记
description: "学习的时候"
tags: [笔记, javascript]
modified: 2016-03-24
categories: [笔记]
---


## Array 对象

### Array 对象属性

* **constructor** 属性返回对创建此对象的数组函数。
* **length** 属性可设置或返回数组中元素的数目。
* **prototype** 属性使您有能力向对象添加属性和方法。

<!-- more -->

## Array 对象方法

* **concat()** 方法用于连接两个或多个数组。该方法不会改变现有的数组，而仅仅会返回被连接数组的一个副本。

##### 语法
{% highlight javascript %}
arrayObject.concat(arrayX,arrayX,......,arrayX)
{% endhighlight %}

* **join()** 方法用于把数组中的所有元素放入一个字符串。元素是通过指定的分隔符进行分隔的。

##### 语法

{% highlight javascript %}
arrayObject.join(separator)
{% endhighlight %}

返回一个字符串。该字符串是通过把 arrayObject 的每个元素转换为字符串，然后把这些字符串连接起来，在两个元素之间插入separator 字符串而生成的。

* **pop()**  方法用于删除并返回数组的最后一个元素。（会打印出该元素）

* **shift()** 方法用于把数组的第一个元素从其中删除，并返回第一个元素的值。

* **push()** 方法可向数组的末尾添加一个或多个元素，并返回新的长度。（会打印出长度）

* **unshift()** 方法可向数组的开头添加一个或更多元素，并返回新的长度。（会打印出长度）

* **reverse()** 方法用于颠倒数组中元素的顺序。

* **slice(start,end)** 方法可从已有的数组中返回选定的元素。（该方法并不会修改数组，而是返回一个子数组）

* **splice()** 方法向/从数组中添加/删除项目，然后返回被删除的项目。

##### 语法

{% highlight javascript %}
arrayObject.splice(index,howmany,item1,.....,itemX)
{% endhighlight %}

* **index**	必需。整数，规定添加/删除项目的位置，使用负数可从数组结尾处规定位置。
* **howmany**	必需。要删除的项目数量。如果设置为 0，则不会删除项目。

* **sort(sortNum)** 方法用于对数组的元素进行排序。（请注意，数组在原数组上进行排序，不生成副本）
{% highlight javascript %}
function sortNum(a,b) {
 return a - b;
//升序，如降序，把“a - b”该成“b - a”。不必深究。
{% endhighlight %}

若深究：
因为sort()函数使用的是冒泡排序，冒泡排序会重复地走访要排序的数列，一次比较两个元素，如果他们的顺序错误就把他们交换过来，一直重复地进行直到说该数列已经排序完成。
如果a-b>0(即正数)就把a和b的位置交换，也就是较小的一个数会排到前面；
如果b-a>0就把a和b的位置交换，也就是较大的一个数会排到前面

* **toString()** 方法可把数组转换为字符串，并返回结果。（返回值与没有参数的 join() 方法返回的字符串相同）


### Boolean 对象方法

* **toString()** 方法可把一个逻辑值转换为字符串，并返回结果。

### Date 对象

* **Date()** 方法可返回当天的日期和时间。
*getDate()** 方法可返回月份的某一天。（该方法总是结合一个 Date 对象来使用）
* **getDay()** 方法可返回表示星期的某一天的数字。（返回值是 0（周日） 到 6（周六） 之间的一个整数）
* **getMonth()** 方法可返回表示月份的数字。（返回值是 0（一月） 到 11（十二月） 之间的一个整数）
* **getFullYear()** 方法可返回一个表示年份的 4 位数字。
* **getHours()** 方法可返回时间的小时字段。
* **getMinutes()** 方法可返回时间的分钟字段。
* **getSeconds()** 方法可返回时间的秒。
* **getMilliseconds()** 方法可返回时间的毫秒。
* **getTime()** 方法可返回距 1970 年 1 月 1 日之间的毫秒数。
* **getTimezoneOffset()** 方法可返回格林威治时间和本地时间之间的时差，以分钟为单位
* **setDate()** 方法用于设置一个月的某一天。
* …

### Math 对象

* **abs()** 方法可返回数的绝对值。
* **floor()** 方法可对一个数进行下舍入。
* **ceil()** 方法可对一个数进行上舍入。
* **max()** 方法可返回两个指定的数中带有较大的值的那个数。
* **random()** 方法可返回介于 0 ~ 1 之间的一个随机数。
* **round()** 方法可把一个数字舍入为最接近的整数。

### Number 对象

* **toPrecision()** 方法可在对象的值超出指定位数时将其转换为指数计数法。
* **toFixed()** 方法可把 Number 四舍五入为指定小数位数的数字。

### String 对象

* **length** 属性可返回字符串中的字符数目。
* **anchor()** 方法用于创建HTML锚。
* **charAt()** 方法可返回指定位置的字符。
* **concat()** 方法用于连接两个或多个字符串。（使用 + 运算符来进行字符串的连接运算通常会更简便一些）
* **indexOf()** 方法可返回某个指定的字符串值在字符串中首次出现的位置。
* **lastIndexOf()** 方法可返回一个指定的字符串值最后出现的位置，在一个字符串中的指定位置从后向前搜索。
* **substring()** 方法用于提取字符串中介于两个指定下标之间的字符。（不接受负的参数）
* **match()** 方法可在字符串内检索指定的值，或找到一个或多个正则表达式的匹配。（它返回指定的值，而不是字符串的位置）
* **replace()** 方法用于在字符串中用一些字符替换另一些字符，或替换一个与正则表达式匹配的子串。
* **search()** 方法用于检索字符串中指定的子字符串，或检索与正则表达式相匹配的子字符串。
* **slice()** 方法可提取字符串的某个部分，并以新的字符串返回被提取的部分。
* **split(separator,howmany)** 方法用于把一个字符串分割成字符串数组。
* **toUpperCase()** 方法用于把字符串转换为大写。

### JavaScript 全局对象

* **parseInt()** 函数可解析一个字符串，并返回一个整数。（可以用来进制转换）
* **escape()** 函数可对字符串进行编码，这样就可以在所有的计算机上读取该字符串。
* **unescape()** 函数可对通过 escape() 编码的字符串进行解码。
* **isNaN()** 函数用于检查其参数是否是非数字值。
* **parseFloat()** 函数可解析一个字符串，并返回一个浮点数。

### 正则表达式

http://tool.chinaz.com/regex/

### History 对象

* **History** 对象包含用户（在浏览器窗口中）访问过的 URL。
* **back()** 方法可加载历史列表中的前一个 URL（如果存在）。等价于点击前进按钮或调用 history.go(-1)。
* **forward()** 方法可加载历史列表中的下一个 URL。（等价于点击前进按钮或调用 history.go(1)。）
* **go()** 方法可加载历史列表中的某个具体的页面。

### Location 对象

* **assign(URL)** 方法可加载一个新的文档。
* **reload()** 方法用于重新加载当前文档。
* **replace()** 方法可用一个新文档取代当前文档。

### Window 对象方法

* **alert()** 方法用于显示带有一条指定消息和一个OK按钮的警告框。
* **close()** 方法用于关闭浏览器窗口。
* **confirm()** 方法用于显示一个带有指定消息和OK及取消按钮的对话框。
* **print()** 方法用于打印当前窗口的内容。
* **prompt()** 方法用于显示可提示用户进行输入的对话框。
* **scrollTo()** 方法可把内容滚动到指定的坐标。
* **scrollBy()** 方法可把内容滚动指定的像素数。
* **setTimeout()** 方法用于在指定的毫秒数后调用函数或计算表达式。
* **clearTimeout()** 方法可取消由setTimeout()方法设置的timeout。
* **setInterval()** 方法可按照指定的周期（以毫秒计）来调用函数或计算表达式。
* **clearInterval()** 方法可取消由setInterval()设置的timeout。

### Form 对象方法

* **formObject.submit()**
* **formObject.reset()**    //把表单中的元素重置为它们的默认值

### Select 对象方法

* **add()**  方法用于向 select 添加一个 option 元素。

### Table 对象方法

* **deleteRow()** 方法用于从表格删除指定位置的行。
* **insertRow()** 方法用于在表格中的指定位置插入一个新行。

### Meta 对象属性

* metaObject.httpEquiv=content-type/expires/refresh/set-cookie
* metaObject.name=author/description/keywords/generator/revised/others
