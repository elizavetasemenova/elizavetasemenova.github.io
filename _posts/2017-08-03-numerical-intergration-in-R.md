---
layout: post
title: Integrating not too bad singularities in R.
date: 2017-08-03
comments: true
---

Today somebody needed their one-dimentional integral to be evaluated numerically. Please meet this integral and the code used to compute it:
<script src="https://gist.github.com/elizavetasemenova/0b9dd4e1cd63bdd0169f29e99a7934ac.js"></script>

First, let us think of possible singularities (by trying to do this in my head I made a mistake, so at this point rather prompt
yourself with pen and paper). The danger may await in the points 0, 1 and Infinity. There are, however, no convergence issues. Still, 
understanding of the numerical effects which may occur due to these piculiarities is very useful.

By trying to perform numerical integration in R we notice that integration from the lower limit x=0 results in an error message, while 
integrating from x=1e-15 we get a reasonable answer. The issue, most probably, arises from the fact that R tries to evaluate the integrand at zero. An alternative explanation is that the algorithm uses such a partition of the x-axis that it hits x=1. Allowing ourselves to step away from the troublesome point x=0 by a very small number, say 1e-15, the problem is solved. 

To check, if the magnitude is correct, let us create a custom integration routine by implementing the most straightforward algorithm for the integration of a one-variable function: consider the equally spaced partitioning of the x-values in question and compute the Left-Hand- and Right-Hand- integral sums. By applying this procedure to the integrand in question we see good agreement. A potential pitfall within this approach is a too high number of subdivision points, which one may be tempted to specify to increase the precision, since by making the x-step too small one may eventually hit a value on the x-axis which is numerically not distiguishable from 1. And, hence, the function, evaluated at this point, will give the infinite value.

What remains to be done before we can report the answer, is the estimation of the portions of the integral which were discarded: the one 
from x=0 to 1e-15 and the other one from x=100 to Infinity. Those values are negligable since, in the first case, a function, tending to zero, is being integrated over a very small interval, and in the second case the function decays very fast due to the presence of the exponent.

An improvement can be achieved by selecting a non-equally spaced partitioning, which would take into account the growth speed of a function. In this case, to capture particular regions, one may chose more sparce and more dence partitioning in the regions of slow and fast growth, respectively.
