---
layout: post
title: 文章内插入视频
description: "文章内插入视频"
tags: [教程, 视频]
categories: [教程]
---

<iframe width="560" height="315" src="http://static.youku.com/v1.0.0597/v/swf/loader.swf?VideoIDS=XMTQ1MjM5MDYyNA%3D%3D&winType=BDskin&embedid=MTE0LjIxNS4yNTAuMzICMzYzMDk3NjU2AgI%3D&wd=&partnerid=0edbfd2e4fc91b72&vext=pid%3D0edbfd2e4fc91b72%26emb%3DMTE0LjIxNS4yNTAuMzICMzYzMDk3NjU2AgI%3D%26bc%3D%26type%3D0%26embsig%3D1_1453696555_9c4d92355ead7c1c84a661c51e24d886" frameborder="0"> </iframe>

支持文章内插入视频，尺寸帮助可参考[FitVids](http://fitvidsjs.com/)。

Kramdown使用完全没有问题，但是Markdown可能会有点问题。添加油土鳖视频会出错，以下是解决方法：`<iframe>` 之间加一个空格，删掉`allowfullscreen`。

{% highlight html %}
<iframe width="560" height="315" src="url" frameborder="0"> </iframe>
{% endhighlight %}
