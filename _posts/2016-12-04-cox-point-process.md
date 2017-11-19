---
layout: post
title: "Cox point process (Poisson process with random intensity) in R and Stan."
date: 2016-12-04
comments: true
---

Cox point process is another name for the Poisson process with random intensity. Let us consider an introductory example: 
for specified number of observations and regression coefficients generate a covariate and corresponding response,
compute the mean and estimate the parameters.

<script src="https://gist.github.com/elizavetasemenova/af7c2e8cd908f725076856e16be4d1f8.js"></script>

Well done, GLM! 

Now spice up the intensity of the Poisson process, $\lambda$ with a random normally dstributed value $r~N(\mu_r,\sigma_r)$ under the exponent sign and follow the same procedure as above.

<script src="https://gist.github.com/elizavetasemenova/c9ee7d911da7cc25faac21cef9bfb1da.js"></script>

Not surprisingly the mean and the estimates have changed. Could we have predicted their values prior to running the numerical experiment? Yes, and that is how. We are having in front of us a  **doubly stochastic process **. Let us compute the expectation of the intensity:

$$E[\lambda]=exp(\beta_0+\beta_1*x)*E[r]=exp(\beta_0+\beta_1*x)*exp(\mu_r+(\sigma_r)^2/2)$$

and so the inference routine, formulated incorrectly for the model without noise, interpretes the sum $\beta_0+\mu_r+(\sigma_r)^2/2$ as $\beta_0$.

To get fluent in probabilistics language <a href="http://mc-stan.org">STAN</a> and verify that Bayesian inference will give the same results as the frequentist, let us translate the above said into the corresponding STAN-model to run it for both non-noisy and noisy data.

Formulate the model
<script src="https://gist.github.com/elizavetasemenova/00116cd5788fbc910f071712f7ddeb9c.js"></script>

and call it via R-interface:
<script src="https://gist.github.com/elizavetasemenova/94a44f1363199577f8d9c5ea13744957.js"></script>

The outcome is as expected, which confirms that our model has been formulated correctly and we can build on it to fix the flaw.

Now ammend the STAN model with the random error term and its hyperparameters which we aim to infer along with the regression coefficients. Note that we are running into non-identifieability problem since $\beta_0$ and $\mu_r$ are participating in the term $\beta_0+\mu_r$ on euqal rights. However high we set the number of iterations for the Markov Chain Monte Carlo, the algorithm may keep wondering forever how to better split the sum. As a remedy, we accept, that the actual intercept is $\beta_0+\mu_r$ and the error has zero mean.

The new model
<script src="https://gist.github.com/elizavetasemenova/dde3db3455d426a72798bcc4f273fe2e.js"></script>

works with the R-call
<script src="https://gist.github.com/elizavetasemenova/941f8745185ae65adce9d6325a4c718b.js"></script>

and the estimates are as desired:
<script src="https://gist.github.com/elizavetasemenova/99889dc391cf8917ecbc0791a2a823d8.js"></script>

When log-intensity of the Cox process is a Gaussian Random Field, the process is called Log-Gaussian Cox Process (LGCP). The example above is a trivial version of it, when all error terms are independent (hence, the covariance matrix is diagonal). In more general cases any finite realization of the GP would have multivariate normal distribution with covariance of a more complex structure.
