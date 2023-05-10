---
layout: page
title: About
permalink: /about/
---

I'm a Research Scientist with the [NYU Alignment Research Group](https://wp.nyu.edu/arg/), where I'm currently working on various topics around large language model alignment. Previously, I was an early employee at [Cohere](https://www.cohere.ai), where I am still affiliated. [We're hiring!](https://jobs.lever.co/cohere/) I earned a Bachelor's from Duke University.

### Publications & Preprints

**Language Models Don't Always Say What They Think: Unfaithful Explanations in Chain-of-Thought Prompting**\
_**Miles Turpin**, Julian Michael, Ethan Perez, Samuel R. Bowman_\
arXiv, 2023
[[arXiv]](https://arxiv.org/abs/2305.04388)

**A machine learning toolkit for genetic engineering attribution to facilitate biosecurity**\
_Ethan C. Alley, **Miles Turpin**, Andrew Bo Liu, Taylor Kulp-McDowall, Jacob Swett, Rey Edison, Stephen E. Von Stetina, George M. Church & Kevin M. Esvelt_\
Nature Communications, 2020\
[[Paper]](https://www.nature.com/articles/s41467-020-19612-0) [[Twitter thread]](https://twitter.com/kesvelt/status/1336500662851526662) [[Code]](https://github.com/altLabs/attrib)

**Machine Learning Prediction of Surgical Intervention for Small Bowel Obstruction**\
_**Miles Turpin**, Joshua Watson, Matthew Engelhard, Ricardo Henao, David Thompson, Lawrence Carin, Allan Kirk_\
medRxiv, 2021\
[[Preprint]](https://www.medrxiv.org/content/10.1101/2021.04.13.21255428v1)

### Past Projects

* _Scalable Hierarchical Bayesian Neural Networks via Factorization._ During an internship at IBM Research in 2019, I worked with Dr. Soumya Ghosh on scaling hierarchical Bayesian modeling to Bayesian neural networks when dealing with very large numbers of groups. [Hierarchical bayesian modeling](https://en.wikipedia.org/wiki/Bayesian_hierarchical_modeling) 
<!-- (HBM) is a very elegant approach to integrating information about how datasets are structured. However, traditional HBMs have linear parameter growth w.r.t. to the number of groups, because they maintain a separate copy of model parameters for every group. If we have millions of groups and millions of parameters this is undesirable. In this project I explored using a low rank representation of the group-level parameters (i.e. neural net weight matrices) to cut parameter growth from a linear to constant factor rate. Essentially, instead of doing inference on model parameters, we do inference on latent variables, and map those latent variables model parameters. This can also be viewed as a [Bayesian Hypernetwork](https://arxiv.org/abs/1710.04759). -->

* _[Probabilistic Wave Function Collapse with Markov Random Fields](https://github.com/milesaturpin/probabilistic-wave-function-collapse)_. I used Markov Random Fields to create a generalized version of [Wave Function Collapse](https://github.com/mxgmn/WaveFunctionCollapse) algorithm for texture synthesis. This generalization enables the algorithm to handle continuous pixel values and model longer range dependencies. 
<!-- * _[Probabilistic Wave Function Collapse with Markov Random Fields](https://github.com/milesaturpin/probabilistic-wave-function-collapse)_. The [Wave Function Collapse](https://github.com/mxgmn/WaveFunctionCollapse) (WFC) algorithm from procedural generation synthesizes new images that try to match local relationships between blocks of pixels in a sample image. I realized that this algorithm is essentially an special instance of an undirected graphical model (aka Markov random field). The [Ising model](https://en.wikipedia.org/wiki/Ising_model) is the classic version of a simple MRF. WFC only works for categorical variables with few levels and only captures very local statistics. In this project I worked on a generalized version of the WFC algorithm enabling it to be used for continuous pixel values and modeling slightly longer range dependencies. The MCMC generated [some](https://github.com/milesaturpin/probabilistic-wave-function-collapse/blob/master/presentation/041320_050143.gif) [fun](https://github.com/milesaturpin/probabilistic-wave-function-collapse/blob/master/presentation/k2s1ts10000lb-1ub0.5_041420_124422.gif) [animations](https://github.com/milesaturpin/probabilistic-wave-function-collapse/blob/master/presentation/k18s9ts10000lb0.003ub0.1_041320_203604.gif). -->

### Get in touch

milesaturpin at gmail.com
