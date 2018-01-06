---
layout: post
title: An excerpt of my PhD paper “Modeling Log-Gaussian Cox Processes on fine spatio-temporal scale"
date: 2018-01-06
comments: true
---

## Paper 1 - Model

### Log-Gaussian Cox Process
We consider a random realization of a point process $S=\{s_1, \dots ,s_n\}$ - a *point pattern* in a study region $D$. The aim of point patterns analysis is to discover the underlying process based on the generated events $S$. Both the number of events $n$ and their locations $S$ are random. Point processes are characterized by their first- and second- order properties. First-order properties, such as *intensity function*, measure the distribution of events in a study region. Second-order properties measure the tendency of events to appear clustered, independently, or regularly-spaced. The *intensity function* $\lambda(s)$ represents the non-normalized location probability density and sums up to the expectation of the total number of points within the study region $D$: 
\begin{equation}
\text{E}[N(D)] = \lambda(D) = \int_D \lambda(s)ds,
\end{equation}
where $N(.)$ is a counting measure. To construct a probabilistic model for a point pattern $S$ one needs to specify distributions for the total number of points $N(D)$ and the locations of the points:
\begin{equation}
L(S) = \text{P} \left[ N(D)=n \right] n! f(s_1,...,s_n \mid n),
\end{equation}
where the factorial n! comes from the exchangeability of the events within $S$ and $f(s_1,...,s_n \mid n)$ stands for the location density, given $N(D)=n$. Due to the independence of disjoint sets one obtains
\begin{equation}
f(s_1,...,s_n \mid n) = \prod\limits_{i=1}^{n}f(s_i) = \prod\limits_{i=1}^{n} \frac{\lambda(s_i)}{\lambda(D)} = \frac{1}{(\lambda(D))^n}\prod\limits_{i=1}^{n}\lambda(s_i),
\end{equation}
i.e. the likelihood of a point pattern can be rewritten as
\begin{equation}
L(S) = \text{P}\left[ N(D)=n \right] n! \frac{1}{(\lambda(D))^n}\prod\limits_{i=1}^{n}\lambda(s_i).
\end{equation}
Log-Gaussian Cox Process is a doubly-stochastic process with Gaussian log-intensity. Further we consider two possible choices for the probability distribution of the number of points: Poisson and Negative Binomial.

