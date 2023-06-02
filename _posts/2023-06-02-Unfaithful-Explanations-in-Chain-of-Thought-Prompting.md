---
layout: post
title: Unfaithful Explanations in Chain-of-Thought Prompting
date: June 2, 2023
---

I recently released “[Language Models Don't Always Say What They Think: Unfaithful Explanations in Chain-of-Thought Prompting](https://arxiv.org/abs/2305.04388)” with collaborators Julian Michael, Ethan Perez, and Sam Bowman. For a summary of the paper, you can check out [this twitter thread](https://twitter.com/milesaturpin/status/1656010877269602304). In this post, I briefly elaborate on motivations/implications relevant to alignment and, most importantly, give some examples of future work that might address these problems (See Future Work).

**TLDR:**

- CoT doesn’t give us transparency because the process producing the explanation is still black-box. Our results demonstrate that in practice, it’s very easy to find instances of clearly unfaithful CoT explanations: models can confabulate plausible explanations for predictions made for different reasons than they state.
- To improve faithfulness, we either need (1) more context-independent reasoning, or (2) improvements to self-modeling and truthfulness. I’m more excited about (1), which would include methods like problem decomposition and explanation-consistency training.

I don’t think these results fully condemn CoT given that we haven’t tried very hard to explicitly encourage faithfulness. I’m uncertain about how promising CoT is as a starting point for explainability, but there seem to be enough tractable directions for future work that it merits investigation.

## Externalized Reasoning

This work fits into alignment through the Externalized Reasoning agenda, which Tamera Lanham did a good job of sketching out here: Externalized reasoning oversight: a research direction for language model alignment. The gist of this approach is to try to get models to do as much processing/reasoning through natural language as possible. As long as these reasoning traces accurately describe the process the model uses to give answers, then we might more easily detect undesirable behavior by simply monitoring the externalized reasoning. If mechanistic interpretability turns out to be very difficult, this could be one alternative that might help us sidestep those problems.
 

Framed in terms of the explainability literature, we want explanations that are not only plausible (convincing to a human) but also faithful (accurately describe the process models use to give some prediction) [1]. Getting CoT explanations to be faithful seems difficult. It might turn out that it’s just as hard as getting other alignment proposals to work, e.g., it might require us to solve scalable oversight. However, even if CoT can’t give us guarantees about avoiding bad behavior, it still could be valuable in the spirit of “It is easy to lie with statistics; it is easier to lie without them”—it may be possible to produce unfaithful (but detailed and internally consistent) externalized reasoning to justify taking bad actions that were actually chosen for other reasons, but it would be even easier for them to do bad things if they did not give any justifications at all.
 

We know that language models are sensitive to various undesirable factors, e.g., social biases, repeated patterns in contexts, and the inferred views of users they’re interacting with. One can leverage these features to bias models towards incorrect answers. With this paper we sought to investigate the following question: if you do CoT in the presence of these aforementioned biasing features, how does this affect performance when using CoT and how does this change the content of the CoT? For example, we reorder answer choices in a few-shot prompt such that the correct answer is always (A), then we observe if CoT explanations are more likely to rationalize an explanation for (A), even when that answer is incorrect.

## Findings

We found that:

- Models are heavily influenced by these biasing features even when using CoT. Using these biasing features to bias models towards incorrect answers makes accuracy drop significantly (as much as 36% averaged across 13 tasks).
- Not only are the final predictions affected, but the CoT explanations also rationalize giving answers in line with the biases. These unfaithful rationalizations can be very plausible despite arguing for incorrect answers, e.g., by taking advantage of ambiguities in the question.
- Zero-shot CoT can make models even more susceptible to bias than not doing CoT at all, despite their explanations not mentioning the source of the bias!

I encourage people to look at the samples in the paper to get a sense of the range of different ways the explanations can be unfaithful. 

# Future Work

I think when you use CoT (and explain-then-predict methods more generally), the reason for the final prediction factors into (A) the CoT explanation, and (B) the reason that the model produced the CoT explanation.^1 But, we can only see the first part. So, to get more faithful explanations, there are a few approaches:

1. Minimize the influence of (B), which I think amounts to getting more context-independent explanations. We want models to use a consistent explanation process across many instances—we don’t want the process by which models generate explanations to be affected by heuristics on particular examples. To the extent that this involves constraining models in some way, we need to make sure that these methods remain competitive.
2. Move reasons from (B) to (A), which amounts to improving self-modeling and truthfulness. 
    - Self-modeling does not necessarily require introspection, i.e., what a sophisticated system can report about its own internal processing (assuming no access to additional interpretability tools). We may be able to get models to identify features that seem to affect model outputs and so can try to correct for them, without being able to tell whether it’s actually affected by it through some introspective process. Without introspection, good self-modeling could be hard. And it’s very plausible to me that there are important limits to introspection, which makes me less excited about this direction.

I’m fairly uncertain if this is the right breakdown so definitely open to feedback. With this in mind, here are some possible directions:

- Decomposition-based methods help via (1). One alternative is to try to ditch CoT in favor of methods with better transparency guarantees. Problem decomposition is one such approach that tries to encourage faithfulness by construction [2, 3] Decomposition-based approaches can improve faithfulness because, by pre-committing to a particular structure for solving a problem, this could reduce the incidence of models steering the reasoning procedure in a certain direction to rationalize giving a desired end result. It also helps by limiting the amount of context provided to sub-models, which makes it easier to elicit context-independent reasoning by construction.

    - It still seems possible to get biased outcomes with these methods. Models could choose ways to decompose the problem that the model knows is biased towards a specific outcome. E.g., a model with a libertarian bent could choose an economic model that is biased toward giving libertarian answers.
    - I imagine that a central difficulty with decomposition-based methods will be getting them to be competitive with methods that don’t enforce any sort of structure. But, if we can show that they have significantly better faithfulness properties then perhaps paying the alignment tax is feasible.
- Explanation-consistency training could help via (1). Our current training schemes only evaluate the quality of single samples. This approach would involve incorporating penalties for inconsistency across samples. The hope would be that the equilibrium of this scheme would encourage models to use more context-independent reasoning, since that is hopefully the winning strategy that helps the model avoid contradicting itself in other contexts. I’d appreciate pointers for any work doing something similar! This sort of training may also improve (2) by improving self-modeling but this seems more speculative.

    - The details of getting consistency training to work may be tricky. It may be difficult to say whether two statements from a model contradict each other if we are unfamiliar with the domain that the statements are about. It might be difficult to efficiently find inputs that elicit contradictions, i.e., it might require a hypothesis about why the model is changing its answer.
- Prompting models could help via (1) or (2). Prompting models to be unbiased seems to be effective at reducing bias and unfaithfulness due to social stereotypes (according to our experiments and the experiments from The Capacity for Moral Self-Correction in Large Language Models). However, it is unclear to me if these methods can generalize to reduce sensitivity to biases that we are not aware of and so cannot explicitly prompt for. It’s also plausible that we could use prompting methods to try to get models to verbalize sensitivity to biases.
- Fine-tuning models to use specific explanation structures would help via (1). The explanation-generating process would be attributable to our fine-tuning, and thus more consistent across examples.
- Improvements to model honesty might help via (2) if models currently can do a decent amount of self-modeling but are not incentivized to verbalize it.
- Process-based oversight [2, 4] substantially changes the way that models do CoT, which may affect the faithfulness of the explanations. This isn’t exactly the goal of process-based oversight though so I’m unsure how much this would help, if at all.

## Why is CoT Unfaithful?

There are a number of reasons to expect CoT to not be faithful by default. Two reasons should be familiar to readers:

- RLHF may directly disincentivize faithful explanations, resulting in model responses that merely look good to human evaluators [5].
- To the extent that LLMs are trained on human-written explanations, these explanations are not only known to be incomplete, often omitting crucial parts of the causal chain for a particular event, but they can also often be unfaithful accounts of individuals' cognitive processes. Human explanations may be geared more towards convincing others or supporting their own beliefs, rather than accurately reflecting the true causes of decisions. 

However, there are a number of other reasons:

- Foremost is the fact that our training objectives simply do not explicitly incentivize models to accurately report the reasons for their behavior. This is not new, but we nonetheless find the degree of it somewhat surprising.
- Models are also trained on data from authors with incompatible attitudes and beliefs, so models may behave in contradictory ways in different contexts [6, 7].
- Furthermore, even if we do try to train CoT to verbalize factors influencing their explanations/predictions, I suspect that there are important limits to self-modeling/introspection, as mentioned before. I’d appreciate pointers to relevant work and ideas!
 

## Why is what we do in this paper interesting?

- Our evaluation setup, where we use biasing features that are unlikely to be mentioned in the explanations, allows us to evaluate explanation faithfulness just by comparing model predictions. This is much more efficient than the most general way to evaluate explanation faithfulness (based on the simulatability framework), which would involve manually reviewing explanations, determining their implications for model behavior on new inputs, and comparing the expectations against reality. The trade-off is that our setup gives a necessary, but not sufficient, test for faithfulness.
- Existing evaluations of CoT explanations have focused on demonstrating plausibility [1] failures in CoT explanations, e.g., missing steps in reasoning, logical coherence issues, final answers contradicting explanations, etc. I expect this sort of failure to go away with better models. I’m hoping our work will encourage people to look more at situations where explanations are plausible yet unfaithful.
- Existing CoT work mostly focuses on using CoT for reasoning tasks in very objective settings, like deductive logic or math. However, real-world deployment of LMs will likely include using them in domains that involve reasoning but also require handling ambiguity and subjectivity. It’s easy for inconsistent/unfaithful behavior to slip in unnoticed when this is the case.
- Using biasing features allows us to make a claim as to the real reason a model is giving a certain prediction. This helps us distinguish from less interesting sources of unfaithfulness/inconsistent model behavior. This would include inconsistent behavior due to sampling variance, or other unsystematic sensitivity to parts of the input (which may just be a robustness failure that goes away with better models).

## Acknowledgments

Thanks to my co-authors Julian Michael, Ethan Perez, and Sam Bowman for feedback on drafts of this post.

## Citations

[1] Towards Faithfully Interpretable NLP Systems: How Should We Define and Evaluate Faithfulness?

[2] Iterated Decomposition: Improving Science Q&A by Supervising Reasoning Processes

[3] Faithful Reasoning Using Large Language Models

[4] Let's Verify Step by Step

[5] Discovering Language Model Behaviors with Model-Written Evaluations

[6] Simulators  

[7] Language Models as Agent Models


 

^

A third factor is the model's prior over answer choices independent of the explanation since we know that models frequently make final predictions that contradict their CoT explanations. Leo Gao has some good work showing that final model predictions can be very insensitive to edits to the generated CoT explanation that models should respond to. Personally, I think this might improve by default with better models, insofar as better models are less likely to say contradictory things. The prior over answers also plays a large role in cases where the explanation doesn’t pick out a particular answer choice, leaving room for this factor to influence the final prediction.