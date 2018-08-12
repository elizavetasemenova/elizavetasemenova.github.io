---
layout: post
title: Once and forever - Negative Binomial parametrizations
date: 2018-04-03
comments: true
---
Just because I get confused/forget every.single.time.

Once and forever I would like to commemorate the relation between two parametrizations of the Negative Binomial distribution: the one, using size=n and prob = p (and used in R as the default version), against the one where explicitly known are the mean $\mu$ and and the overdispersion parameter $k$:
\begin{equation}
NB(y \mid k, \mu) = \binom{y + k -1}{y} (\mu+k)^y \left(\frac{k}{\mu+k}\right)^{k},
\end{equation}

The relationship is as follows:
\begin{equation}
n = \frac{\mu p}{1-p}, \quad \mu + \frac{\mu^2}{k} = \frac{n(1-p)}{p^2}.
\end{equation}

