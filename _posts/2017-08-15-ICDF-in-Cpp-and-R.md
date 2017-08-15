---
ayout: post
title: The Inverse Cumulative Distribution Function (ICDF) sampling method implemented in C++ and R.
date: 2017-08-15
comments: true
---

Attempting to re-write in C++ the Gillespie algorithm, which I earlier implemented in R, I stumbled upon the fact that sampling from 
various probability distributions is not as straightforward in C++ as it is in R. Luckily, all I needed was the exponential distribution,
where the Inverse Cumulative Distribution Function offers an elegant workaround.

<img src="../images/Dilbert.png">
<font size="-1">Source: http://dilbert.com/strip/2001-10-25</font>

In general, this method allows to sample from a distribution that is not readily available. To be more precise, given a probability 
density function $f(x)$ (for continuous variables) or probability mass function $p(x)$ (for discrete variables) or, alternatively, 
cumulative distribution function $F(x)$ we would like to generate $x$ such that $P(X<= x) =F(x).$ <em>The Inverse Cumulative Distribution 
Function (ICDF) method</em>, also called <em>the inverse transform method</em>, allows to generate random variables following a 
distribution with a known explicit form of the ICDF. The simulation is enabled by the generalised inverse function (the quantile function) 
$F^{-}(u)=min\{x: F(x) >= u\}, u \in [0,1]$ with the properties $ F^{-1}(F(x))<=x$ and  $ F(F^{-1}(u))<=u.$ For continuous
random variables this will be a regular inverse CDF. The properties of the ICDF suggest the inverse transform method:

<p>
Given a CDF $F,$ if  $u$ is distributed uniformly on $(0,1)$, then $x=F^{-1}(u)$ is distributed as $F,$ that is  $P(X<= x) =F(x).$
</p>

This method makes simulation of variables following such continuous distributions as Exponential, Cauchy, Logistic, truncated Normal 
and Pareto distributions straightforward. Knowledge of the relationships between distributions provides ways of deriving simulations of, 
for instance, Chi Squared, Gamma and Beta from the Exponential. In the same way Student’s distribution can be derived from Cauchy. 

In the codes presented below I implemented the ICDF method to sample from the Exponential distribution with parameter $\lambda$. The plots
aim to compare the simulation resulting from the C++ and R implementations based on ICDF, as well the the built-in R functionality.

Similar to <a href="https://elizavetasemenova.github.io/blog/2017/08/08/C++-easily-compiled-in-command-line">the previous post</a> we can 
use the workflow to compile and execute the C++ code with

<b>sh compileICDF.sh</b>

Which other obstacles are awaiting the enterprise of translating the Gillespie algorithm into C++? Stay tuned and I will keep you posted!
