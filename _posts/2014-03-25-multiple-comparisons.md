---
title: 关于假设检验
nav: blog
layout: post
categories: 
- "Statistics"
tags:
- "p values"
---
Multiple Comparisons  
=========  
  
Hypothesis Testing 假设检验
------
涉及到的几个概念：
- Null Hypothesis H0
- Test statistic T
- P-value
- Significance level
 - Threshold `u` controls false positive rate at level `α = P(T>u|H0)`

确定了`α`，做判断时就会产生__一类错误__和__二类错误__  
The probability that a hypothesis test will correctly reject a false null hypothesis is the `power` of the test.
Multiple Comparisons
----
因为我们是在处理`a family of tests`，选择合适的界值很有难度  
需要在`sensitivity(true positive rate)`和`specificity(true negative rate)`中进行权衡  
Measures of False Positives
----
几种量化假阳性可能性的方法：
- Family-Wise Error Rate (FWER)
 - Probability of any false positives
- False Discovery Rate (FDR)
 - Proportion of false positives among rejected tests

FWER Corredtion
----
the probability of making one or more Type I errors in a family of tests, under the null hypothesis.  
FWER controlling methods:
- Bonferroni correction
- Random Field Theory
- Permutation Tests

Family-wise null hypothesis:
- 所有的比较都没有意义
- 只要拒绝其中一个，就拒绝了Family-wise

Bonferroni Correction
----
- very conservative
 - it results in very strict significance levels
- It decreses the power of the test (probability of correctly rejecting a false null hypothesis) and greatly increases the chance of false negatives
- not optimal for correlated data

Spatial Correlation
----
Random Field Theory
----
allows one to incorporate the correlation into the calculation of the appropriate threshold.

Assumptions
----
- multivariate Gaussian or derived from multivariate Gaussian images
- be sufficiently smooth to approximate a continuous random field
- the amount of smoothness is assumed known
- several layers of approximations

Issues with FWER
----
- FWER provides a strong control over the number of false positives
- suffer from low power
- the most interesting effects are usually at the edge of detection

False Discovery Rate
----
Benjamini and Hochberg (1995)

- FWER controls the probability of any false positives
- FDR controls the proportion of false positives among all rejected tests

BH Procedure
----
1. select desired limit `q` on FDR (e.g.,0.05)
2. rank p-values, p_1 <= P_2 <= ... <- P_m  
3. let `r` be largest `i` such that  
    `p_i <= i/m *q`
4. reject all hypotheses corresponding to p_1,...,P_r

Any procedure that controls the FWER also controls the FDR.  
A procedure that controls the FDR only can be __less stringent__ and lead to a __gain in power__.
Since FDR works only on p-values, it can be applied to any valid statistical test.



    