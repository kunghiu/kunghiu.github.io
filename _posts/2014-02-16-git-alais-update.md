---
title: 使用alias批处理更新github pages
nav: blog
layout: post
categories: 
- "github pages"
---

每每次上传博文，都要来一套git add，commit，push，输入用户名密码，实在繁琐，于是，想到了使用批处理的方法来实现博客更新。		
首先，要确认自己的repository是使用ssh方式同步的，可以避免http方式的需要每次都填写用户名和密码。  
{% highlight Ruby %}
git clone git@github.com:kunghiu/kunghiu.github.io.git
# donot use https method.
{% endhighlight %} 
通常，我们需要在git terminal输入如下命令：  
{% highlight Ruby %}
cd kunghiu.github.io
git add  --all
git commit -m "blog update"
git push origin master
{% endhighlight %} 
现在，我们来对上述命令建立一个假名（alias），使用批处理的方式来实现：  
{% highlight Ruby %}
git config --global alias.blog '!cd kunghiu.github.io && git add  --all && git commit -m "blog update" && git push origin master'
{% endhighlight %}
之后，每次在本地site/kunghiu.github.io下更新完博客之后，只需要在git端输入git blog，一切就统统解决啦！  
赶快来试试吧！