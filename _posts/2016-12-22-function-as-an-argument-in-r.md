---
layout: post
title: "Function as an argument in R."
date: 2016-12-22
comments: true
---

Since I am currently looking at various simulation algorithms, it comes very often to measuring computation time. Here is a snippet making 
use of the mapply R-function. It is helpful when we want to apply a function f(x,y) to different sets of arguments (x1,y1), (x2,y2)... 
The arguments can be functions themselves. In this case after the name of the external function 'f' we will pass into mapply a vector 
with all values for the first argument of f x=c(x1,x2,...) and then for y=c(y1,y2,..):

mapply(f(x,y),
       c(x1,x2,...),
       c(y1,y2,...)

Since R is known to be slow in running explicit loops, it gives us a perfect candidate for benchmarking: compare computation time of
exponentiation of all  integers from 1 to a given number n implemented via a loop, sapply or vectorozed function.

<script src="https://gist.github.com/elizavetasemenova/91e429c6d824ddcbf2d7ec18fa19e954.js"></script>
