---
layout: post
title: 最近的笔记
description: "学习的时刻"
tags: [笔记, javascript]
modified: 2016-08-10
categories: [笔记]
---

* chrome 跨域
`--disable-web-security --user-data-dir`
* 淘宝镜像
[tnpm](http://web.npm.alibaba-inc.com/)
* 安装tnpm
`npm install -g tnpm@release-4 --registry=http://registry.npm.alibaba-inc.com`
* json数组循环
不用必须非得转化成格式`{"aba":"abc",....}`
{% highlight javascript %}
For(var key in json){
}
{% endhighlight %}



* 一些linux命令

1. 查看开的端口  netstat -ntpl
2. 启动nginx     service nginx restart
3. 启动php-fpm   service php-fpm restart
4. 找            whereis       find -[参数]

* undefined值在布尔类型环境中会被当作false。

<!-- more -->
