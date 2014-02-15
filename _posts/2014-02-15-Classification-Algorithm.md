---
title: The Most Frequently Used Classification Algorithm
nav: blog
layout: post
---

常见的分类算法都有哪些？  
分类算法，在计算机科学中，是相当繁杂的一个领域。本文撇开那些高深的诸如模式识别之类的理论，仅就医学领域中经常会遇到的分类算法做一个粗浅的总结。  
既然是粗浅的总结，便从最粗浅的问题入手。  
——什么？分类算法？那你要分几类呀？  
分几类，这可不是个小问题。作为研究者的你，思考一下自己科研或者工作中的问题，你想将它分几类呢？  
——实在是不知道分几类，你学统计的，能帮我分一下么？  
那就是说，在不知道如何分类的情况下进行分类，我们通常称之为无监督的学习。这里所谓“监督”，就是说作为指导的分类标杆。而与之相对应的，就是有监督的分类，就是说，你的分组是确定的，患病的一组，不患病的一组；良性的一组，恶性的一组；等等。  
——这么神奇，那怎么做无监督的学习？  
做无监督学习，最常用的就是聚类算法。所谓“物以类聚，人以群分”，相似的物、相似的人，自然可以归为类群。那分类方法就很明显了，根据相似性（无论是距离的远近，或者说特征的一致性等等）将你的研究对象分在几组里。组数可以由你来定，统计软件自然有办法将其完成。深入学习，请查阅Cluster analysis。  
——那有监督的学习，又包括哪些方法呢？  
Logistic回归，大家应该都耳熟能详的，它的因变量是1或0，自然也就是对分组的区分了。此外，logistic回归，还有多分类的情况，也就是说，可以对因变量赋以等级的涵义，1、2、3三个等级类别，一样可以用logistic回归来做。详情请查阅Ordinal logistic regression。  
此外，还有其他的一些方法，平时在医学科研中较为少用。但如果刚好能用在你的科研上，也不失为一种创新。  
决策树，它实际上是对你整个数据进行一次一次的细分，像树杈一样，一次一次的分下去。完美的话，到最末分叉时，数据就很纯粹的是A组或者B组。  
贝叶斯，贝叶斯是个人名啦，这种方法，是指根据条件概率的方法来对分组进行预测，除了条件概率，其实颇有几分决策树的味道。
支持向量机，SVM，这个东西蛮有趣的，不是统计学家开发的，其中也没有用到统计理论，但对于很复杂的数据，却可以很高效的对数据进行分类，效果也相当理想。合并上核理论（Kernel），可对SVM做如下理解，SVM可以在多组数据中画出一条条曲线甚至曲面，将不同组的数据分开，而将错分的数据降到最低。
除上述方法之外，还有一些诸如人工神经网络，集成学习等等一些方法，实践中确实少用，以后有机会再整理。