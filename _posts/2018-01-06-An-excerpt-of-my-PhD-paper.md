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

The fitting of the model can be done either via this likelihood or, alternatively, via discretization of the study region $D$ into cells and the *grid approach*: despite the assumption of the continuity of the process, for computational purposes the study region is discretized and is being covered with a set of disjoint cells. In the framework of the grid approach all observed points are being framed by a discretized observation window. For each cell of this grid $c_i$ the observed number of cases falling within a grid cell $y_i$ are being collected and attributed to the cell:
\begin{equation}
y_{i} \mid \lambda(c_i) \sim \text{Pois}(\lambda(c_i)),
\end{equation}
\begin{equation}
\lambda(c_i) \approx \frac{\vert D \vert}{K} \lambda(g_i).
\end{equation}
where $K$ is the overall number of cells and $g_i$ denotes a cell centroid. I.e. the observed counts follow the Poisson distribution, conditioned on the random field. Further we show that the higher the number of cells, the closer is the discretized representation of the LGCP to its true continuous version. By independence of the counts within disjoint cells we compute

\begin{equation}
L_{\text{po}}^{\text{grid}} =  \prod\limits_{i=1}^{K}\exp(\lambda(c_i))(\lambda(c_i))^{y_i}/{y_i!} \propto \prod\limits_{i=1}^{K}  \exp(\lambda(c_i)) (\lambda(c_i))^{y_i}
\end{equation}

\begin{equation}
= \exp \left(-\sum\limits_{i=1}^{K}\lambda(c_i) \right) \prod (\lambda(c_i))^{y_i} =  \exp \left(-\lambda(D) \right) \prod (\lambda(c_i))^{y_i},
\end{equation}

the second product is taken over the cells with non-zero counts. As the volume of each cell becomes smaller $\vert c_i \vert \to 0$, the counts $y_i$ within cells become 0 or 1 and we obtain the same likelihood as $L_{\text{po}}.$ Thus, this fitting approach represents an alternative to the one through direct likelihood: instead of using only the points of the observed events and having to evaluate the integral over the observation region, we create artificial counts on a fine grid and use them to discover the intensity. 

## Negative Binomial count distribution
Now we challenge the traditional distribution assumption and derive log-likelihood for modeling of point patterns with Negative Binomial count distribution. For this we will use the following parametrization: 

\begin{equation}
\text{P}_\text{nb}^{\lambda, \phi} \left[ N(D)=n \right] = \binom{n + \phi -1}{n} \left(\{\lambda}{\lambda+\phi}\right)^n \left(\frac{\phi}{\lambda+\phi}\right)^{\phi},
\end{equation}

where $\lambda = \lambda(D)$ and $\phi>0$ is the over-dispersion parameter. Under this parametrization the mean and variance equal correspondingly $\text{E}[N(D)] = \lambda(D)$ and $\text{Var}[N(D)] = \lambda(D) + \frac{(\lambda(D))^2}{\phi}.$
Plugging this into the formula for $L(S),$ we obtain
\begin{equation}
L_{\text{nb}}(S) =\frac{(n+\phi+1)...(\phi+1) \phi^{\phi+1}}{(\lambda(D) + \phi)^{n+\phi}} \prod\limits_{i=1}^{n}\lambda(s_i).
\end{equation}
As in the case of the Poisson distribution, the likelihood requires the computation of the integral $\lambda(D).$ By analogy with the Poisson case we propose to apply the 
gridded approach to the Negative Binomial distribution and compare run times of the four fitting strategies.

## Discretization of the Gaussian Process
 When the context allows for covariates, the intensity takes the form
\begin{equation}
 \lambda(s) = \exp(\textbf{X}^T(s) \boldsymbol{\beta} + f(s)),
\end{equation}
where $f$ stands for the Gaussian Process. This case of the Cox process is important for practical use due to its ability to be linked to meaningful explanatory factors. Log-likelihood in the case of, for instance, the Poisson count distribution is composed as
\begin{equation}
\log L = - {\int_D \exp\{ \textbf{X}^T(s) \boldsymbol{\beta} + f(s)\} ds} + \sum\limits_{i=1}^{n} \{ \textbf{X}^T(s_i) \boldsymbol{\beta} + f(s_i)\}.
\end{equation}
Here integration is intractable because of the random term under the integral sign. Furthermore, the integral creates high computational burden as it is performed over the entire domain $D.$ An integration quadrature formula can be used, for instance,
\begin{equation}
\int_D \exp\{ \textbf{X}^T(s) \boldsymbol{\beta} + f(s)\} ds  \approx \frac{|D|}{K} \sum_{k=1}^{K} \exp\{ \textbf{X}^T(g_k) \boldsymbol{\beta} + f(g_k)\}.
\end{equation}
Treating this quadrature leads to the same computation issues, as when using the computational grid (Diggle (2013)) and fitting cell counts.

For practical applications one would like to keep the highest resolution, available for the spatial covariates while performing the inference. As a consequence, computational burden increases due to calculations on large matrices, required to describe the stochastic effect. Traditional mechanism to fit latent Gaussian models and find numerically posterior estimates of all the random terms comprising the latent field is the simulation-based and computationally intense Markov Chain Monte Carlo. Below we present a computational strategy allowing to reduce complexity and memory usage, applied to the fitting of LGCP and make it more feasible. 

Finite realizations of the stationary Gaussian process $f$ compose a vector distributed as $ \text{MVN}(m,\Sigma)$ with $\Sigma$ being a spatially-structured covariance matrix with elements 
\begin{equation}
\Sigma_{ij} =  \text{R}^{\theta}(d_{ij}).
\end{equation}
Here $\text{R}^{\theta}$ is an isomorphic spatial covariance function depending on the parameters $\theta$ and the distance between locations $d_{ij}.$ We opt for the Gaussian as the functional form of $\text{R}^{\theta}$ and this is crucial for our further considerations:

\begin{equation}
\text{R}_{ij} = \sigma^2\exp\Big(- 1/(2l^2)||x_i - x_j ||_2^2 \Big) =  \sigma^2\exp \Big( - 1/(2l^2) \sum_{d=1}^{D} (x_{i}^d-x_{j}^d)^2 \Big).
\end{equation}

The sum in the above formula is taken over all dimensions. Parameter $l$ denotes the length scale and can be chosen differently for different dimensions. For Bayesian inference of the vector-parameter $ \theta = ( \boldsymbol{\beta}, \sigma^2, l)$ and computation of the posterior distribution
$\pi (\theta | S ) \propto L(S| \theta ) \cdot \pi(\theta)$
the priors $\pi(\theta)$ need to be selected. 

Simulation-based inference requires realizations of the multivariate normal distribution $f \sim \text{MVN}(m,\Sigma),$ generated from the density $(2 \pi)^{-d/2} |\Sigma|^{-1/2} \exp( - \frac{1}{2} (x-m)^T \Sigma^{-1} (x-m))$ . The covariance matrix $\Sigma$ spans $N =n_y n_x$ and $N = n_y n_x n_t$ cells for spatial and spatiotemporal models, respectively. Hence, the size of the covariance matrix is $N^2$, and constitutes a computational bottleneck referring both to the run-time and required storage. To draw from the multivariate normal distribution $ \text{MVN}(0, \Sigma)$ and avoid matrix inversion, as well as the determinant calculation, an improvement can be achieved through the Cholesky factorization, i.e. a matrix $L,$ such that 
\begin{equation}
\Sigma= L L^T.
\end{equation}
In this case, if $z$ is an $N$-vector generated as $\text{MVN}(0, I_n),$ then 
\begin{equation}
Lz \sim \text{MVN}(0, \Sigma).
\end{equation}
This algorithm requires storage for the matrix $L$ of size $N \times N$. To mitigate this issue we exploit the *Kronecker (tensor) algebra*, as well as matrix-normal and array-normal distributions as described below.

## Kronecker algebra
If $A$ is an $m \times n$ matrix, and $B$ is an $p \times q$ matrix, then the *Kronecker-product* (or *tensor product*)  $A \otimes B$ is an $m p \times n q$ matrix with elements

\begin{equation}
A \otimes B = 
\end{equation}
\begin{equation}
\begin{bmatrix} a_{11}B & ..... & a_{1n}B \end{bmatrix}
\end{equation}
\begin{equation}
\begin{bmatrix}\\ ....... \\ \end{bmatrix}
\end{equation}
\begin{equation}
\begin{bmatrix} a_{m1}B & ... & a_{mn}B  \end{bmatrix}.
\end{equation}

All further explanations will be made for the 2d case and generalized after to 3d.

The covariance function, evaluated over a Cartesian grid, gives rise to a covariance matrix that
can be written as a Kronecker product of D smaller marginal covariance matrices. The side length of each such square matrix equals the number of cells along the given axis. This result follows from the definition of the Kronecker product and the chosen structure of the correlation matrix, i.e. 
\begin{equation}
\Sigma = V \otimes U.
\end{equation}
Instead of storing and inverting an $N \times N$ matrix, it suffices to store one $n_y \times n_y$ and one $n_x \times n_x$ matrices. Further gains can be made by avoiding $N \times N$ matrices in all intermediate computations and using the \textit{ matrix normal distribution} instead. An $n_y \times n_x$ matrix $f_{n_y,n_x}$ is said to follow the matrix-normal distribution
\begin{equation}
f_{n_y,n_x} \sim \text{MN}_{n_y,n_x}(\mu_{n_y,n_x}, U, V)
\end{equation}
with the $n_y \times n_x$ matrix-mean $\mu_{n_y,n_x}$, $n_y \times n_x$ between-rows covariance $U$ and $n_x \times n_x$ between-columns covariance $V$ if and only if 
\begin{equation}
vec(f_{n_y,n_x}) \sim \text{MVN}( vec(\mu_{n_y,n_x}), V \otimes U),
\end{equation}
where $vec(X)$ denotes vectorization of the matrix $X,$ i.e. a vector of length $n_y n_x$ obtained by stacking columns of the matrix $X$ one under another. Vectorization operator has an important property which connects it to the Kronecker product. Let $A$ be an $n_y \times n_y$, $X$ an $n_y \times n_x$ and $B$ a $n_x \times n_x$ matrices, respectively. Then it holds
\begin{equation}
(B \otimes A) vec(X) = vec(AXB^T).
\end{equation}

Let $L$ be the Cholesky factor of the matrix $\Sigma$, which allows the Kronecker decomposition $\Sigma= V \otimes U,$ and let  $L_V$ and $L_U$ be the square roots of $V$ and $U$, respectively. Then $V\otimes U = (L_V L_V^T) \otimes (L_U L_U^T) = (L_V \otimes L_U) (L_V \otimes L_U)^T$ due to the properties of the Kronecker product and it follows, that
\begin{equation}
L= L_V \otimes L_U.
\end{equation}

By $ vec^{-1}_{n_y, n_x}$ we denote the operation of mechanical unstacking of a vector into a matrix with $n_y$ rows and $n_x$ columns in the column-major order. An important implication of the two properties listed above is a method for sampling from the matrix-normal distribution: if 
\begin{equation}
z_{n_y, n_x} \sim \text{MN}_{n_y, n_x}(0, I, I)
\end{equation}
is an $n_y \times n_x$ matrix of independent draws from the standard normal distribution, then 
\begin{align}
L_U z_{n_y, n_x} L_V^T &= vec^{-1}_{n_y,n_x}((L_V \otimes L_U) vec(z_{n_y,n_x})) \\
&\sim  vec^{-1}_{n_y,n_x}(\text{MVN}(0, L L^T)) = \text{MN}_{n_y,n_x}(0, U, V).
\end{equation}
Generalizing this fact for 3d, we obtain
\begin{align}
 vec^{-1}_{n_y,n_x,n_t}((L_W \otimes L_V \otimes L_U) vec(z_{n_y,n_x, n_t})) \sim  \text{MN}_{n_y,n_x,n_t}(0, U, V, W).
\end{equation}


It follows, that instead of sampling from $\text{MVN}(0, \Sigma)$ via $f_N=Lz_N$ one can sample from the matrix-normal distribution $f_{n_y,n_x}= \text{MN}_{n_y,n_x}(0, U, V).$ This approach requires computation and storage of the Cholesky factors $U$ and $V$ of dimensions $n_y \times n_y$ and $n_x \times n_x,$ respectively, which is a noticeable parsimony compared to sampling through $L$: we need to store $n_y^2+n_x^2$ instead of $n_y^2n_x^2$ numbers and perform $O(n_y^3+n_x^3)$ operations instead of $O(n_y^3n_x^3)$. The last statement follows from the fact, that, in general, computation of the Cholesky factor of an $n \times n$ matrix requires $O(n^3)$ operations. Hence, the computational complexity and storage requirements grow linearly and not multiplicatively with each added dimension. 

Based on equality (25), there are two ways to perform the sampling from the array-normal distribution. First approach is to address the left hand side of the equality. It was taken by (Fernandes (1968)): originating from the field of stochastic automata, the algorithm computes left vector-matrix product, where the matrix is a Kronecker product of smaller matrices. The second approach is to execute  computations as expressed on the right hand side of (25). Such algorithm was presented in (Saatchi (2012)). Theoretical complexity of the two algorithms is identical, while real computation times may vary, depending on the software of implementation, due to the usage of such features as vectorization. 
We tested two identical programs,  formalized in the probabilistic programming language Stan (Carpenter et al. (2016)), which only differ in the part of sampling the values of the Gaussian Process and compare average run-times per chain.
