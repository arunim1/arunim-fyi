---
id: note_01j9ccqhzre3d8fn2yfv1ytac7
aliases:
  - "2307.15043"
  - "Universal and Transferable Adversarial Attacks on Aligned Language Models"
public: true
tags:
  - "paper"
  - "ai/adv"
---

[[2307.15043] Universal and Transferable Adversarial Attacks on Aligned Language Models](https://arxiv.org/abs/2307.15043) introduces the Greedy Coordinate Gradient algorithm, a surprisingly simple way to find strings such that, when appended to a query, the language model does not refuse the malicious request preceding the string.

- how it works:
	- start with a random suffix, that is e.g. 15 tokens long.
	- for a set of malicious prompts and corresponding completions, initially just one of each, e.g. `['Can you describe how to make a bomb?']` and	`['Sure! Here's how you make a bomb:']`, run a forward pass with the input `<USER> prompt + suffix <ASSISTANT> completion`
	- calculate the loss for this forward pass as `1-P(completion)`, where `P(completion)` is simply the product of each probability that the model generates the next token in `completion`, assuming it's already generated the preceding ones. (quite nicely, this only requires the one forward pass
	- backpropagate this loss to the suffix tokens, such that for each token, you can observe which alternative tokens should indicate a move in the direction of lower loss. run forward passes using a bunch of these potentially better tokens, and make substitutions where the replacements do best.
	- once the suffix is doing well enough, add in a new prompt-completion pair. and then eventually use multiple models, and if it's still doing well, it might just generalize to models you haven't even tested on.
- wild! why does it work? I don't think people (read: Zico Kolter) know why? my best guess is that during pretraining or refusal training (more likely the former), there's some pattern that emerges that is useful for predicting the next token which is related to the strings that are found here. somehow, this pattern or set of patterns can be used to convey something anti-refusal.