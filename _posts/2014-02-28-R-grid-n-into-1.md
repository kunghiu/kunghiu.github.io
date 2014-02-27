---
title: R语言拾遗之四[将多图绘制到一页]
nav: blog
layout: post
categories: 
- "R语言"
---

高大上的ggplot2，估计很多人都尝过其甜头了。  
ggplot2在生成一页多图方面，有个facet，分面的命令，可以自动根据分组，每组对应一幅图出来。  
但是，如果是不同类型的图，想拼到一起，就比较麻烦了。  
在这里，Hiu给大家提供两种方法。  
第一种，使用grid包的viewport功能。  
{% highlight R %}
library(ggplot2)
library(grid)
#generate a new page, or erase the current one.
grid.newpage()
#maintain a Viewport tree, which describe the regions and coordinate systems.
pushViewport(viewport(layout=grid.layout(1,2)))
#generate two ggplot2 objects.
a <- qplot(TMPRSS4, ECADHERIN, data=spear)
b <- qplot(TMPRSS4, ECADHERIN, data=spear, geom="jitter")
#print them into the Viewport, or the page.
print(a, vp=viewport(layout.pos.row=1,layout.pos.col=1))
print(b, vp=viewport(layout.pos.row=1,layout.pos.col=2))
#also, you can define a function to make the print process more concise.
{% endhighlight %}
第二种，使用一个新包，叫做gridExtra。  
{% highlight R %}
library(gridExtra)
a <- qplot(TMPRSS4, ECADHERIN, data=spear)
b <- qplot(TMPRSS4, ECADHERIN, data=spear, geom="jitter")
grid.arrange(a,b,ncol=2)
{% endhighlight %}
于是，我们就得到了二合一的图片：  
![grid 2 into 1](http://kunghiu.github.io/pic/grid2in1.png)
