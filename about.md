---
layout: page
title: About
permalink: /about/
---

I'm a machine learning researcher at [Cohere](https://www.cohere.ai). My research interests include generative models, meta-learning, and AI alignment. I graduated from Duke in 2020 where I studied Machine Learning and Math. In my free time I like playing around with generative art, creating ambient lighting environments, and becoming one with nature.
 
### Publications & Preprints

**A machine learning toolkit for genetic engineering attribution to facilitate biosecurity**\
_Ethan C. Alley, **Miles Turpin**, Andrew Bo Liu, Taylor Kulp-McDowall, Jacob Swett, Rey Edison, Stephen E. Von Stetina, George M. Church & Kevin M. Esvelt_\
Nature Communications, December 2020\
[[Paper]](https://www.nature.com/articles/s41467-020-19612-0) [[Twitter thread]](https://twitter.com/kesvelt/status/1336500662851526662) [[Code]](https://github.com/altLabs/attrib)

**Machine Learning Prediction of Surgical Intervention for Small Bowel Obstruction**\
_**Miles Turpin**, Joshua Watson, Matthew Engelhard, Ricardo Henao, David Thompson, Lawrence Carin, Allan Kirk_\
medRxiv, April 2021\
[[Preprint]](https://www.medrxiv.org/content/10.1101/2021.04.13.21255428v1)

### Past Projects

* _Scalable Hierarchical Bayesian Neural Networks via Factorization._ During an internship at IBM Research in 2019, I worked with Dr. Soumya Ghosh on scaling hierarchical Bayesian modeling to Bayesian neural networks when dealing with very large numbers of groups. [Hierarchical bayesian modeling](https://en.wikipedia.org/wiki/Bayesian_hierarchical_modeling) (HBM) is a very elegant approach to integrating information about how datasets are structured. However, traditional HBMs have linear parameter growth w.r.t. to the number of groups, because they maintain a separate copy of model parameters for every group. If we have millions of groups and millions of parameters this is undesirable. In this project I explored using a low rank representation of the group-level parameters (i.e. neural net weight matrices) to cut parameter growth from a linear to constant factor rate. Essentially, instead of doing inference on model parameters, we do inference on latent variables, and map those latent variables model parameters. This can also be viewed as a [Bayesian Hypernetwork](https://arxiv.org/abs/1710.04759).

* _[Probabilistic Wave Function Collapse with Markov Random Fields](https://github.com/milesaturpin/probabilistic-wave-function-collapse)_ (Spring 2020). The [Wave Function Collapse](https://github.com/mxgmn/WaveFunctionCollapse) (WFC) algorithm from procedural generation synthesizes new images that try to match local relationships between blocks of pixels in a sample image. I realized that this algorithm is essentially an special instance of an undirected graphical model (aka Markov random field). The [Ising model](https://en.wikipedia.org/wiki/Ising_model) is the classic version of a simple MRF. WFC only works for categorical variables with few levels and only captures very local statistics. In this project I worked on a generalized version of the WFC algorithm enabling it to be used for continuous pixel values and modeling slightly longer range dependencies. The MCMC generated [some](https://github.com/milesaturpin/probabilistic-wave-function-collapse/blob/master/presentation/041320_050143.gif) [fun](https://github.com/milesaturpin/probabilistic-wave-function-collapse/blob/master/presentation/k2s1ts10000lb-1ub0.5_041420_124422.gif) [animations](https://github.com/milesaturpin/probabilistic-wave-function-collapse/blob/master/presentation/k18s9ts10000lb0.003ub0.1_041320_203604.gif).

### Contact me

[milesaturpin@gmail.com](mailto:milesaturpin@gmail.com)
