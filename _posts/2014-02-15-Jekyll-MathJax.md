---
title: 在github pages上使用MathJax
nav: blog
layout: post
categories: 
- "github pages"
---
MathJax没有专门给Jekyll配备插件，所以，需要使用常规的JavaScript方法来调用。  
首先，在<head>...</head>中添加JS链接：  
{% highlight HTML %}
<script type="text/javascript"  
   src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>  
{% endhighlight %}
其次，将Jekyll解析器改为Kramdown，以支持Latex标记。（在_config.yml文件中修改）  
如此，配置部分结束。  
文章撰写时，使用双$符号标记Latex语言。前后皆有双$。  
如果公式（包括双$）前后各有一个空行，则产生换行居中的公式。效果如下：  
  
$$\sum_{n=1}^\infty 1/n^2 = \frac{\pi^2}{6}$$  
  