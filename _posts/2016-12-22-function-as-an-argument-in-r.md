---
layout: post
title: "Function as an argument in R."
date: 2016-12-22
comments: true
---

The snippet below makes use of the mapply R-function. It becomes helpful when one wants to apply a function f(x,y) to different sets of arguments (x1,y1), (x2,y2). The arguments can be functions themselves. In this case after the name of the external function 'f' we will pass into mapply a vector with all values for the first argument of f x=c(x1,x2,...), then for the second y=c(y1,y2,..) and so on:

mapply(f(x,y,z),
       c(x1,x2,...),
       c(y1,y2,...),
       c(z1,z2,..))

Since R is known for being slow in running explicit loops, it gives us a perfect candidate for benchmarking: compare computation time of
exponentiation of all  integers from 1 to a given number n implemented via a loop, sapply or as a vectorozed function.

<script src="https://gist.github.com/elizavetasemenova/91e429c6d824ddcbf2d7ec18fa19e954.js"></script>
