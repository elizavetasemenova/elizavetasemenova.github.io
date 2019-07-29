---
layout: post
title: Ordered Logistic regression and Probabilistic Programming with examples in Stan, PyMC3 and Turing.
date: 2019-07-28
comments: true
---
In this post, we discuss probabilistic programming languages on the example of ordered logistic regression.

### Probabilistic programming languages (PPLs)
Bayesian machine learning (read 'Bayesian statistics', 'probabilistic modelling' or even 'Bayesian Deep Learning' if 
you prefer) is a fast-developing field fueled by modelling frameworks such as probabilistic programming languages 
(PPLs). A PPL allows to formalize a Bayesian model and perform inference with the help of powerful algorithms. The 
list of currently existing PPLs is overwhelmingly long and only keeps growing: Stan, PyMC3, PyMC4, Nimble, Pyro, Edward,
TensorFlow Probability, Gen, Turing, Stheno, SOSS, Omega, Infer.NET to name a few. The choice of a modelling tool can be 
driven by the programming language that one is used to, domain-specific culture, active community or PPL's functionality. 
It is relatively straightforward to formulate a simple model, such as linear regression, in the majority of the PPLs 
(see a compilation of examples here). Advantages or disadvantages of a certain framework become clearer only on the examples 
of more involved models, e.g. models with discrete parameters, parameters of variable size, etc. Model formulation and 
inference for such cases prove to be harder or even impossible in some PPLs.

### PPLs and GPPLs
For the examples below I have selected three pairs of PPLs and general-purpose programming languages (GPPLs) providing 
interfaces to the former: R and Stan, Python and PyMC3, Julia and Turing. For each GPPL-PPL pair, I will show how to 
specify a model, sample from posterior, extract parameter estimates and obtain predictions. At the end of the post, I will 
discuss the modelling experiences across the three setups.

### Why Julia?
Python and R dominate the worlds of machine learning and statistics. They are easy to learn, but both lack speed. Julia is a
young (released in 2012) GPPL which was created to overcome this issue. It retains the simplicity and readability of R and 
Python but provides additionally computational speed analogous to C. The new language is not meant to substitute the two 
established ones, but rather to augment them since a lot of R and Python functionality is available in Julia.
Julia has quickly become popular in the scientific community leading to its fast development. As a consequence of the 
permanent ongoing improvement new versions of some commands and libraries might become incompatible with older versions. 
But as time goes, things will most likely settle and commands will become stable. 

In the context of probabilistic modelling, Julia is a fertile ground for several native PPLs. This is why it was chosen 
as one of the three examples in this post.

### Ordered logistic regression
Ordered logistic regression aka the proportional odds model is a standard choice for modelling ordinal outcomes. Such data
is frequently collected via surveys in the form of likert scales. For instance, a service provider might ask how likely it
is that one would recommend them to a friend with the answer options being "unlikely", "somewhat likely", "very likely". 
Results of such surveys are discrete and ordered data. Further examples of ordinal outcomes include disease progression 
states or toxicity of drugs. 

The code chunks below show the main steps of ordinal data modelling in the three languages. All of them consist of the same
essential steps:
* read data,
* model specification,
* sampling,
* obtain parameter estimates,
* make predictions.

### R and Stan example

### Python and PyMC3 examples

### Julia and Turing example

### What have we learned?
* Both Stan and PyMC3 are well-stablished tools and provide a wide range of distributions, as well as detailed documentation. 
In Turing for the given case (ordinal regression), the probability distribution had to be implemented by hand.

* Parameter estimates are very similar, implying that our implementation in Turing is reliable.

* Making predictions in Stan is straightforward and can be done directly in the 'generated quantities' block. As a result, the model needs to be run only once - both for inferring the parameters and to obtain predictions. In PyMC3 a separate command for posterior predictive checks needs to be executed to obtain predictions. Turing does not have such functionality at the moment and predictions need to be computed from posterior parameter estimates by hand using the generative model.

* This post does not cover model comparison, but this is another important criteria to look at while deciding for a PPL: in Stan, for instance, log-likelihood can be stored using the 'generated quantities' block, allowing to compute information criteria such WAIC.

### More examples to come
This post covered ordinal logistic regression in Stan, PyMC3 and Turing. For more implementations of common models across 
PPLs see this GitHub repository.

### Acknowledgements
This post is a byproduct of my work at AstraZeneca with Stanley Lazic who introduced me to Julia, Turing and real-life problems solvable with the help of ordered logistic regression. Many thanks also go to Martin Trapp who provided a lot of help with understanding Turing.
