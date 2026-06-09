---
id: note_01jkp31fj8fb6vn1q937tfesnk
aliases:
  - "Trading Inference-Time Compute for Adversarial Robustness"
  - "2501.18841"
public: true
tags:
  - "paper"
  - "ai/adv"
---

[[2501.18841] Trading Inference-Time Compute for Adversarial Robustness](https://arxiv.org/abs/2501.18841v1)

> We conduct experiments on the impact of increasing inference-time compute in reasoning models (specifically OpenAI o1-preview and o1-mini) on their robustness to adversarial attacks. We find that across a variety of attacks, increased inference-time compute leads to improved robustness. In many cases (with important exceptions), the fraction of model samples where the attack succeeds tends to zero as the amount of test-time compute grows. We perform no adversarial training for the tasks we study, and we increase inference-time compute by simply allowing the models to spend more compute on reasoning, independently of the form of attack. Our results suggest that inference-time compute has the potential to improve adversarial robustness for Large Language Models. We also explore new attacks directed at reasoning models, as well as settings where inference-time compute does not improve reliability, and speculate on the reasons for these as well as ways to address them.

they say something like "we didn't train on these examples, this was just a safety external"

- it seems like OAI did in fact do safety training and red-teaming, so this should be viewed with that in mind.

they claim things like the jump is because of insufficient intelligence

- *seems like the alternative hypothesis is that it's because safety finetuning is mostly focused on like immediate rejections / refusal or something, which is more realistic*

see the related [[project]] idea here—super simple to do, actually.