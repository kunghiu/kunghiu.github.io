---
title: R语言拾遗之一[文件名操作]
nav: blog
layout: post
---

设定工作目录：  
{% highlight R %}
getwd()
setwd("F:/DATA")
{% endhighlight %}  
批量文件名获取（包含后缀）：  
{% highlight R %}
list.files(path = "F:/DATA" ,pattern="*.sav" )
{% endhighlight %}  
生成完整路径：  
{% highlight R %}
(f <- file.path("F:/DADA",list.files(path = "F:/DATA" ,pattern="*.sav" )))
# file.path("F:/DADA", *filenamevector)
{% endhighlight %}  
去掉文件名后缀：  
{% highlight R %}
strsplit("nameabc.sav",split="\\.")[[1]][1]
{% endhighlight %}  
批量去掉文件名后缀：  
{% highlight R %}
matrix(unlist(strsplit(list.files(path = "F:/DATA" ,pattern="*.sav" ),split="\\.")),2)[1,]
{% endhighlight %}  
上述语句相对简单，以后如果有空，可以整理成function来使用。