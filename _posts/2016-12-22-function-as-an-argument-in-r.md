---
layout: post
title: "Function as an argument in R and an mapply example."
date: 2016-12-22
comments: true
---

R allows functions to be arguments of other functions. To call an inside function as an argument of an outside function the following syntax can be used:

```r
outside_function <- function(non_func_arguments, FUN= inside_function){...}
```

The snippet below makes use of the mapply R-function. It becomes helpful when one wants to apply a function $f(x,y)$ to different sets of arguments $(x_1,y_1), (x_2,y_2).$ The arguments can be functions themselves. In this case after the name of the external function 'f' we will pass into mapply a vector with all values for the first argument $x=c(x_1,x_2,...),$ then for the second $y=c(y_1,y_2,..)$ and so on:

$mapply(f(x,y,z),
       c(x_1,x_2,...),
       c(y_1,y_2,...),
       c(z_1,z_2,..))$

Since R is known for being slow in running explicit loops, it gives us a perfect candidate for benchmarking: compare computation time of
exponentiation of all  integers from 1 to a given number n implemented via a loop, sapply or as a vectorozed function.

<script src="https://gist.github.com/elizavetasemenova/91e429c6d824ddcbf2d7ec18fa19e954.js"></script>
