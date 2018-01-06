---
layout: post
title: An excerpt of my PhD paper “Modeling Log-Gaussian Cox Processes on fine spatio-temporal scale"
date: 2018-01-06
comments: true
---

### Paper 1 - Model

## Log-Gaussian Cox Process
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

## Poisson count distribution
A customary assumption is that the number of points within a point pattern follows the Poisson distribution:
\begin{equation}
P_{po}^{\lambda} \left[ N(D)=n \right] = \frac{\exp(\lambda(D)) (\lambda(D))^n}{n!}
\end{equation}
and the data is distributed as a Poisson process, conditional on the intensity function $\lambda(s)$ : 
\begin{equation}
S \mid \lambda(s) \sim \text{PP}(\lambda(s)).
\end{equation}
The likelihood and log-likelihood for point patterns in this case depend on the entire intensity surface and are expressed as
\begin{equation}
L_{\text{po}}(s_1,\dots,s_n, s_i \in D; \lambda(s)) = \exp(-\lambda(D)) \prod\limits_{i=1}^{n}\lambda(s_i),
\end{equation}
\begin{equation}
\log L_{\text{po}}(s_1,\dots,s_n, s_i \in D; \lambda(s)) = -\lambda(D) + \sum\limits_{i=1}^{n}\log \lambda(s_i).
\end{equation}
As before, $\lambda(D)$ should be computed as an integral over the domain $D$.

The fitting of the model can be done either via this likelihood or, alternatively, via discretization of the study region $D$ into cells and the \textit{grid approach}: despite the assumption of the continuity of the process, for computational purposes the study region is discretized and is being covered with a set of disjoint cells. In the framework of the grid approach all observed points are being framed by a discretized observation window. For each cell of this grid $c_i$ the observed number of cases falling within a grid cell $y_i$ are being collected and attributed to the cell:
\begin{equation}
y_{i} \mid \lambda(c_i) \sim \text{Pois}(\lambda(c_i)),
\end{equation}
\begin{equation}
\lambda(c_i) \approx \frac{\vert D \vert}{K} \lambda(g_i).
\end{equation}
where $K$ is the overall number of cells and $g_i$ denotes a cell centroid. 
