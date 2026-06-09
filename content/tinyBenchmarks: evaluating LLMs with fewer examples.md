---
id: note_01jmfv0nj8edps50jjfb02bq1c
aliases:
  - "tinyBenchmarks: evaluating LLMs with fewer examples"
  - "2402.14992"
public: true
tags:
  - "paper"
  - "ai/eval"
---

[[2402.14992] tinyBenchmarks: evaluating LLMs with fewer examples](https://arxiv.org/abs/2402.14992v2)

> The versatility of large language models (LLMs) led to the creation of diverse benchmarks that thoroughly test a variety of language models' abilities. These benchmarks consist of tens of thousands of examples making evaluation of LLMs very expensive. In this paper, we investigate strategies to reduce the number of evaluations needed to assess the performance of an LLM on several key benchmarks. For example, we show that to accurately estimate the performance of an LLM on MMLU, a popular multiple-choice QA benchmark consisting of 14K examples, it is sufficient to evaluate this LLM on 100 curated examples. We release evaluation tools and tiny versions of popular benchmarks: Open LLM Leaderboard, MMLU, HELM, and AlpacaEval 2.0. Our empirical analysis demonstrates that these tools and tiny benchmarks are sufficient to reliably and efficiently reproduce the original evaluation results.

Cool cool stuff.

TODO link with [[projects]] which reference this, take notes during meeting, and understand how it actually works.

[[2025-02-19 Wednesday]] Notes:

- In the paper, they try a few different methods.
- Input data simply looks like a large set of (model, example, performance) pairs
- One approach (the best they found) is:
	- to model the probability of a particular model getting a particular question correct
	- each model has a skill vector
	- each example is represented by an alpha (vector) and beta for bias (scalar)
- if the vectors align, then we expect the model to perform well on this one
- If a pair of examples have similar alpha and beta, then you should expect their performance to be similar, and can pretty much eval on one of them and assume performance translates.
- So, cluster according to alpha and beta and select points which are in different clusters.
- Then, with your subset of points, you can go back and fit a new theta for a new model keeping alpha and beta fixed.
- Then, use this new theta to estimate perf on each example you didn't see, and pretend that was the actual perf.
- 20-30 models could be enough to fit an IRT model, but you need to have this across capability levels.

next week

- try running a model on tinymmlu,
- try running train_irt and anchor_points, estimate_perf
- i'll try training on swe-bench and/or openllm leaderboard 2
- I'll aim to set up a pipeline for the whole thing.