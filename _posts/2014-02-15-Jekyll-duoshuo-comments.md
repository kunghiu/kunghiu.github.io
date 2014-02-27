---
title: 为Jekyll添加多说评论系统
nav: blog
layout: post
categories: 
- "github pages"
---
为Jekyll添加多说评论系统，Havee有一篇同名的博文，有兴趣可以搜索一下。  
这篇文章略繁琐，我没看太懂，其核心思想是将多说整合进Jekyll体系，用Jekyll的方式来操作多说的评论。灵活性自不必说，但是考虑到Occam's Razor（[奥卡姆剃刀](http://zh.wikipedia.org/zh/%E5%A5%A5%E5%8D%A1%E5%A7%86%E5%89%83%E5%88%80)），太Geek也就意味着太浪费。  
实际上，像我等新手来做这个的话，根本用不着那么麻烦。  
首先，登陆[多说](http://duoshuo.com/)，注册一个账号是必须的了。紧接着，多说就会提供一个通用代码，在工具菜单之下。类似：  
{% highlight javascript %}
<!-- Duoshuo Comment BEGIN -->  
	<div class="ds-thread"></div>  
<script type="text/javascript">  
var duoshuoQuery = {short_name:"yourshortnamehere"};  
	(function() {  
		var ds = document.createElement('script');  
		ds.type = 'text/javascript';ds.async = true;  
		ds.src = 'http://static.duoshuo.com/embed.js';  
		ds.charset = 'UTF-8';  
		(document.getElementsByTagName('head')[0]  
 		|| document.getElementsByTagName('body')[0]).appendChild(ds);  
	})();  
	</script>  
<!-- Duoshuo Comment END -->
{% endhighlight %}  
之后，将其复制粘贴到模板（我的是post.html）中正文div下面，保存上传，即可。  
祝好运！