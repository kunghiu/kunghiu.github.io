---
title: R语言拾遗之三[结果输出]
nav: blog
layout: post
---

##结果输出，最主要的是数据集输出和表格输出两类  

###数据集输出  

数据集读取和输出，用spss格式读入，stata格式输出，实在是太方便了：  
{% highlight R %}
library("foreign")
datain <- read.spss(file="F:/DATA/data.sav")
write.dta(datain, file="F:/DATA/finaldata.dta")
{% endhighlight %}   
  
###表格输出  
表格输出，最有爱的就是使用xtable啦！  
{% highlight R %}
library("xtable")
xtable <- xtable(outbox,caption="title")

print(xtable, type = "html")
#output into html, usually used in Rmd.
#and if you use R Markdown, you should make sure the option "results='asis'" is set.

print(xtable)
#output into latex style. 
#and if you use R Sweave, you should make sure the option "results=tex" is set.
{% endhighlight %} 
  
今天新见到一个使用stargazer包的方法，确实很方便，但目前只支持Latex输出。  
{% highlight R %}
<<results=tex>>=
library(stargazer)
stargazer(attitude)
#output basic statistics.

stargazer(linear.1, linear.2, probit.model, title="Regression Results", align=TRUE)
#compare sever models in one table.
#It's really awesome!
@
{% endhighlight %}
实际上，我的博客现在也支持Latex语言了，信不信？我输出一段儿Latex给各位看一下，哈哈。  
————没成功！！！只能支持公式，不支持表格！！！  
{::comment}
Regression Results
=============================================================================
                                       Dependent variable:                   
                    ---------------------------------------------------------
                                       rating                     high.rating
                                         OLS                        probit   
                             (1)                    (2)               (3)    
-----------------------------------------------------------------------------
complaints                 0.692***               0.682***                   
                           (0.149)                (0.129)                    
                                                                             
privileges                  -0.104                 -0.103                    
                           (0.135)                (0.129)                    
                                                                             
learning                    0.249                  0.238*          0.164***  
                           (0.160)                (0.139)           (0.053)  
                                                                             
raises                      -0.033                                           
                           (0.202)                                           
                                                                             
critical                    0.015                                   -0.001   
                           (0.147)                                  (0.044)  
                                                                             
advance                                                             -0.062   
                                                                    (0.042)  
                                                                             
Constant                    11.011                 11.258          -7.476**  
                           (11.704)               (7.318)           (3.570)  
                                                                             
-----------------------------------------------------------------------------
Observations                  30                     30               30     
R2                          0.715                  0.715                     
Adjusted R2                 0.656                  0.682                     
Log Likelihood                                                      -9.087   
Akaike Inf. Crit.                                                   26.175   
Residual Std. Error    7.139 (df = 24)        6.863 (df = 26)                
F Statistic         12.063*** (df = 5; 24) 21.743*** (df = 3; 26)            
=============================================================================
Note:                                             *p<0.1; **p<0.05; ***p<0.01
{:/comment}
  
###图片输出  
图片输出，在Rmd中，应设置fig.show='asis'；在Rnw中，应设置fig=TRUE。  
  
###万能的例外情况  
当然，很多情况下，也会遇到xtable不识别的情况，特别是复杂建模使用不常见的程序之时。那怎么办呢？capture.output可以直接输出屏显内容，真正的所见即所得：  
{% highlight R %}
capture.output(..., file = NULL, append = FALSE)
capture.output(summary(modelfit), file = "F:/DATA/output.txt" )
{% endhighlight %} 