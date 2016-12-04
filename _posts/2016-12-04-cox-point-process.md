---
layout: post
title: "Cox point process (Poisson process with random intensity) in R and STAN."
date: 2016-12-04
comments: true
---

Cox point process is another name for the Poisson process with random intensity. Let us consider an introductory example: 
for a specified number of observations and regression coefficients generate a covariate and corresponding response,
compute the mean and estimate the parameters.

<script src="https://gist.github.com/elizavetasemenova/af7c2e8cd908f725076856e16be4d1f8.js"></script>

Well done, GLM! 

Now spice up the intensity of the Poisson process, $\lambda$ with a random normally dstributed value $r~N(\mu_r,\sigma_r)$ under the exponent sign and follow the same procedure as above.

<script src="https://gist.github.com/elizavetasemenova/c9ee7d911da7cc25faac21cef9bfb1da.js"></script>

Not surprisingly the mean and the estimates have changed. Could we have predicted their values prior to running the numerical experiment? Yes, and that is how. We are having in front of us a doubly stochastic process. Let us compute the expectation of the intensity:

$E[\lambda]=exp(\beta_0+\beta_1*x)*E[r]=exp(\beta_0+\beta_1*x)*exp(\mu_r+(\sigma_r)^2/2)$

and so the inference routine, formulated incorrectly for the model without noise, interpretes the sum $\beta_0+\mu_r+(\sigma_r)^2/2$ as $\beta_0$.

To get fluent in probabilistics language <a href="http://mc-stan.org">STAN</a> and verify that Bayesian inference will give the same results as the frequentist, let us translate the above said into the corresponding STAN-model to run it for both non-noisy and noisy data.

Formulate the model
<script src="https://gist.github.com/elizavetasemenova/00116cd5788fbc910f071712f7ddeb9c.js"></script>

and call it via R-interface:
<script src="https://gist.github.com/elizavetasemenova/94a44f1363199577f8d9c5ea13744957.js"></script>
