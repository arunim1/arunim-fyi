---
id: note_01j9ccqhzrfker7zfhh9zxdjj4
aliases:
  - "Gradient-Based Language Model Red Teaming"
  - "2401.16656"
public: true
tags:
  - "paper"
  - "ai/adv"
---

[[2401.16656] Gradient-Based Language Model Red Teaming](https://arxiv.org/abs/2401.16656) introduces the GBRT algorithm, a way to construct language model inputs that cause a target language model to produce outputs deemed bad by some reward model.

- | **Similarities** | **Differences**|
  |-----------|----------|
  |test|test4|
  |test|test4|
  |test|test4|
  |test|test4|
- uhhh i had a similar idea around the time it was published but there's ~no way I would've done the engineering that could've made it work, ya know.
- I think this might be the truest form of endless jailbreaking. or some tokenizer shortcut
- i want to compare performance of this method vs tokenizer shortcut in javi rando's meta paper.
- kinda like [[gcg]] but a bit more principled and a bit worse performance (classic ML moment)
- One thing I quite like is that you can do this with any kind of classifier hooked up to the model, it's not totally reliant on some token-forcing thing.