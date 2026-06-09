---
id: note_01jj5mae28fj4vpb20afa3gm2j
aliases:
  - "Safetywashing: Do AI Safety Benchmarks Actually Measure Safety Progress?"
  - "2407.21792"
  - safetywashing
public: true
tags:
  - paper
  - ai/eval
---

[[2407.21792] Safetywashing: Do AI Safety Benchmarks Actually Measure Safety Progress?](https://arxiv.org/abs/2407.21792v3)

> As artificial intelligence systems grow more powerful, there has been increasing interest in "AI safety" research to address emerging and future risks. However, the field of AI safety remains poorly defined and inconsistently measured, leading to confusion about how researchers can contribute. This lack of clarity is compounded by the unclear relationship between AI safety benchmarks and upstream general capabilities (e.g., general knowledge and reasoning). To address these issues, we conduct a comprehensive meta-analysis of AI safety benchmarks, empirically analyzing their correlation with general capabilities across dozens of models and providing a survey of existing directions in AI safety. Our findings reveal that many safety benchmarks highly correlate with both upstream model capabilities and training compute, potentially enabling "safetywashing"--where capability improvements are misrepresented as safety advancements. Based on these findings, we propose an empirical foundation for developing more meaningful safety metrics and define AI safety in a machine learning research context as a set of clearly delineated research goals that are empirically separable from generic capabilities advancements. In doing so, we aim to provide a more rigorous framework for AI safety research, advancing the science of safety evaluations and clarifying the path towards measurable progress.

Super interesting paper by my friend Richard Ren! I think it's a great way to more rigorously evaluate safety methods. *Good* safety methods shouldn't be overpowered by advancements which come with scale, at minimum they should complement. *Great* safety methods are those which tie performance on safety benchmarks to general capabilities improvements where they weren't previously tied.

For example: adversarial robustness (to jailbreaks like TAP and GCG, and human jailbreaks) was not previously generally tied to capabilities, but might be tied quite closely for [[reasoning models]] thanks to work like this: [[Trading Inference-Time Compute for Adversarial Robustness]]

- I actually think it's not quite as straightforward as this, as the trend you should expect to see over the course of years is still that base models scale, and the reasoning fine-tuning on top scales just a little bit more. For one, I'm skeptical models will ever reason for months on end, because at that point you could have trained an entirely new model! This style of argument is similar to [this](https://epoch.ai/blog/the-longest-training-run) argument from Epoch which proves that training runs won't last more than 14 months or something, because the hardware and techniques you'd use would have improved enough *during* that training run, that it would be better to wait.
- And so I think there's a [[project]] to be done here!