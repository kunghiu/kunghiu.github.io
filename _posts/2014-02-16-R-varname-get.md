---
title: R语言拾遗之二[function中变量名操作]
nav: blog
layout: post
---

函数编程中，经常会遇到新建变量名的操作，如何使R可以自动新建变量名，就成为一个问题。  
本文对R中操作变量名的get()，exists()，assign()函数进行一个简单总结。  
其实，最靠谱的，就是get()，它负责把某个字符（串）转换成变量名，可以在<-符号左边出现。顾名思义，exists()就是看变量名存在与否，assign()是给某变量名赋值，与<-符号类似。  
如下get()的使用示例，shortname[i]所指向的元素自动成为一个变量名参与到函数之中。  
{% highlight R %}
newdata <- array(iniarray)
#assuming shortname is a vector of varnames
for (i in 1:length(shortname)){
  newdata <- cbind(newdata, get(shortname[i])$value)
}
{% endhighlight %} 
如下，"a[1]"整个是一个变量名，而不代表向量a的第一个元素。  
{% highlight R %}
a <- 1:4
assign("a[1]", 2)
a[1] == 2          #FALSE
exists("a[1]")     #TRUE
get("a[1]") == 2   #TRUE
{% endhighlight %} 
