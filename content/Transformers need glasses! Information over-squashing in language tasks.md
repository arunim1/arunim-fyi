---
id: note_01jp37hatgep9vsxn5awafywb1
aliases:
  - "Transformers need glasses! Information over-squashing in language tasks"
  - "2406.04267"
public: true
tags:
  - "paper"
  - "ai"
---

[[2406.04267] Transformers need glasses! Information over-squashing in language tasks](https://arxiv.org/abs/2406.04267v2)

> We study how information propagates in decoder-only Transformers, which are the architectural backbone of most existing frontier large language models (LLMs). We rely on a theoretical signal propagation analysis -- specifically, we analyse the representations of the last token in the final layer of the Transformer, as this is the representation used for next-token prediction. Our analysis reveals a representational collapse phenomenon: we prove that certain distinct sequences of inputs to the Transformer can yield arbitrarily close representations in the final token. This effect is exacerbated by the low-precision floating-point formats frequently used in modern LLMs. As a result, the model is provably unable to respond to these sequences in different ways -- leading to errors in, e.g., tasks involving counting or copying. Further, we show that decoder-only Transformer language models can lose sensitivity to specific tokens in the input, which relates to the well-known phenomenon of over-squashing in graph neural networks. We provide empirical evidence supporting our claims on contemporary LLMs. Our theory also points to simple solutions towards ameliorating these issues.

I wanted to test out their "sums" experiment with a slight modification, where you give the model the tokens it needs to keep track of the sum as it goes.

Original setup has a prompt of the form:

> Please perform the following sum: 1 + 1 + 1 + 1 + 1. Please give the answer on the final line exactly as 'The final answer to your maths question is: xxxx', where 'xxxx' is your answer.

My test:

> Please perform the following sum: 1 + 1 (sum: 2) + 1 (sum: 3) + 1 (sum: blank) + 1 (sum: blank). Please give the answer on the final line exactly as 'The final answer to your maths question is: xxxx', where 'xxxx' is your answer.

Seems like it gets the same results! The models are indeed bad at counting in this format! Tried a few other formats which might be more intuitive, but it just seems to be robustly bad at this! The frontier models seem better, at least in the 100-200 range. If i had to guess though, they'd start to fail at some number that's just higher, rather than just being generally quite good (given that even in the 100-200 range, they end up off by a few here and there). Fascinating!