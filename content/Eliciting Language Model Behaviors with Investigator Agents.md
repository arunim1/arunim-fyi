---
id: note_01jkkgmshgf779hved6wb8wz7j
aliases:
  - "Eliciting Language Model Behaviors with Investigator Agents"
  - "2502.01236"
public: true
tags:
  - "paper"
  - "ai/adv"
---

[[2502.01236] Eliciting Language Model Behaviors with Investigator Agents](https://arxiv.org/abs/2502.01236v1)

> Language models exhibit complex, diverse behaviors when prompted with free-form text, making it difficult to characterize the space of possible outputs. We study the problem of behavior elicitation, where the goal is to search for prompts that induce specific target behaviors (e.g., hallucinations or harmful responses) from a target language model. To navigate the exponentially large space of possible prompts, we train investigator models to map randomly-chosen target behaviors to a diverse distribution of outputs that elicit them, similar to amortized Bayesian inference. We do this through supervised fine-tuning, reinforcement learning via DPO, and a novel Frank-Wolfe training objective to iteratively discover diverse prompting strategies. Our investigator models surface a variety of effective and human-interpretable prompts leading to jailbreaks, hallucinations, and open-ended aberrant behaviors, obtaining a 100% attack success rate on a subset of AdvBench (Harmful Behaviors) and an 85% hallucination rate.

The concept here is pretty creative, I quite like it! Have LLMs predict the prompts which lead to bad outputs, then just use those prompts!

Works as a much cheaper LM inverter than [adversarial robustness](/tags/ai/adv) methods like fine-tuning or [[gbrt]].

Again, seems like the only issue here is that I'm not sure how this readily translates out of the token-forcing regime. Maybe it just does, and you can replace the input of a specific prompt by filling the latent with vaguely X-biased representations as opposed to not-X, and get a distribution of outputs which vaguely favor X.