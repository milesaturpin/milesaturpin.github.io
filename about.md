---
layout: page
title: About
permalink: /about/
---

I'm a Research Scientist on the [SEAL team](https://scale.com/blog/safety-evaluations-alignment-lab) at Scale AI, where I work on [faithfulness of model-generated reasoning](https://arxiv.org/abs/2305.04388) and scalable oversight. We're hiring in [scalable oversight](https://scale.com/careers/4529095005), [agent robustness](https://scale.com/careers/4529091005), and [frontier risk evaluations](https://scale.com/careers/4529094005)! Before Scale, I was a Research Scientist in the [NYU Alignment Research Group](https://wp.nyu.edu/arg/) under Prof. Sam Bowman. Before that, I was an early employee at [Cohere](https://www.cohere.ai). I earned a Bachelor's in Machine Learning and Mathematics from Duke University.

### Publications & Preprints

**Looking Inward: Language Models Can Learn About Themselves by Introspection**\
_Felix J Binder, James Chua, Tomek Korbak, Henry Sleight, John Hughes, Robert Long, Ethan Perez, **Miles Turpin**, Owain Evans_\
ICLR 2025\
[[arXiv]](https://arxiv.org/abs/2410.13787)

**Foundational Challenges in Assuring Alignment and Safety of Large Language Models**\
_Usman Anwar, Abulhair Saparov, Javier Rando, Daniel Paleka, **Miles Turpin**, Peter Hase, Ekdeep Singh Lubana, Erik Jenner, Stephen Casper, ...,  Yejin Choi, David Krueger_\
arXiv 2024\
[[arXiv]](https://arxiv.org/abs/2404.09932) [[Website]](https://llm-safety-challenges.github.io/) [[Summary twitter thread]](https://twitter.com/DavidSKrueger/status/1779900511627452467) [[Twitter Thread for Interpretability Section]](https://twitter.com/milesaturpin/status/1779906827624308976) 
- Co-authored section 3.4 (Tools for Interpreting or Explaining LLM Behavior Are Absent or Lack Faithfulness) with Peter Hase.

**Bias-Augmented Consistency Training Reduces Biased Reasoning in Chain-of-Thought**\
_James Chua, Edward Rees, Hunar Batra, Samuel R. Bowman, Julian Michael, Ethan Perez, **Miles Turpin**_\
arXiv 2024\
[[arXiv]](https://arxiv.org/abs/2403.05518) [[Twitter thread]](https://twitter.com/milesaturpin/status/1767327882978660513) [[Code]](https://github.com/raybears/cot-transparency)

**Language Models Don't Always Say What They Think: Unfaithful Explanations in Chain-of-Thought Prompting**\
_**Miles Turpin**, Julian Michael, Ethan Perez, Samuel R. Bowman_\
NeurIPS 2023\
[[OpenReview]](https://openreview.net/forum?id=bzs4uPLXvi) [[Twitter thread]](https://twitter.com/milesaturpin/status/1656010877269602304) [[Code]](https://github.com/milesaturpin/cot-unfaithfulness/)

**A machine learning toolkit for genetic engineering attribution to facilitate biosecurity**\
_Ethan C. Alley, **Miles Turpin**, Andrew Bo Liu, Taylor Kulp-McDowall, Jacob Swett, Rey Edison, Stephen E. Von Stetina, George M. Church & Kevin M. Esvelt_\
Nature Communications, 2020\
[[Paper]](https://www.nature.com/articles/s41467-020-19612-0) [[Twitter thread]](https://twitter.com/kesvelt/status/1336500662851526662) [[Code]](https://github.com/altLabs/attrib)

**Machine Learning Prediction of Surgical Intervention for Small Bowel Obstruction**\
_**Miles Turpin**, Joshua Watson, Matthew Engelhard, Ricardo Henao, David Thompson, Lawrence Carin, Allan Kirk_\
medRxiv, 2021\
[[Preprint]](https://www.medrxiv.org/content/10.1101/2021.04.13.21255428v1)

### Blog Posts

**Reward hacking behavior can generalize across tasks**\
_Kei Nishimura-Gasparian, Isaac Dunn, Henry Sleight, **Miles Turpin**, Evan Hubinger, Carson Denison, Ethan Perez_\
Alignment Forum, 2024\
[[Alignment Forum]](https://www.alignmentforum.org/posts/Ge55vxEmKXunFFwoe/reward-hacking-behavior-can-generalize-across-tasks)

### Past Projects

* _Scalable Hierarchical Bayesian Neural Networks via Factorization._ During an internship at IBM Research in 2019, I worked with Dr. Soumya Ghosh on scaling hierarchical Bayesian modeling to Bayesian neural networks when dealing with very large numbers of groups.
<!-- (HBM) is a very elegant approach to integrating information about how datasets are structured. However, traditional HBMs have linear parameter growth w.r.t. to the number of groups, because they maintain a separate copy of model parameters for every group. If we have millions of groups and millions of parameters this is undesirable. In this project I explored using a low rank representation of the group-level parameters (i.e. neural net weight matrices) to cut parameter growth from a linear to constant factor rate. Essentially, instead of doing inference on model parameters, we do inference on latent variables, and map those latent variables model parameters. This can also be viewed as a [Bayesian Hypernetwork](https://arxiv.org/abs/1710.04759). -->

* _[Probabilistic Wave Function Collapse with Markov Random Fields](https://github.com/milesaturpin/probabilistic-wave-function-collapse)_. I used Markov Random Fields to create a generalized version of [Wave Function Collapse](https://github.com/mxgmn/WaveFunctionCollapse) algorithm for texture synthesis. This generalization enables the algorithm to handle continuous pixel values and model longer range dependencies. 
<!-- * _[Probabilistic Wave Function Collapse with Markov Random Fields](https://github.com/milesaturpin/probabilistic-wave-function-collapse)_. The [Wave Function Collapse](https://github.com/mxgmn/WaveFunctionCollapse) (WFC) algorithm from procedural generation synthesizes new images that try to match local relationships between blocks of pixels in a sample image. I realized that this algorithm is essentially an special instance of an undirected graphical model (aka Markov random field). The [Ising model](https://en.wikipedia.org/wiki/Ising_model) is the classic version of a simple MRF. WFC only works for categorical variables with few levels and only captures very local statistics. In this project I worked on a generalized version of the WFC algorithm enabling it to be used for continuous pixel values and modeling slightly longer range dependencies. The MCMC generated [some](https://github.com/milesaturpin/probabilistic-wave-function-collapse/blob/master/presentation/041320_050143.gif) [fun](https://github.com/milesaturpin/probabilistic-wave-function-collapse/blob/master/presentation/k2s1ts10000lb-1ub0.5_041420_124422.gif) [animations](https://github.com/milesaturpin/probabilistic-wave-function-collapse/blob/master/presentation/k18s9ts10000lb0.003ub0.1_041320_203604.gif). -->

### Get in touch

milesaturpin at gmail.com
