---
id: note_01jm0xace0efx87ew2fkgy7z4f
aliases:
  - "emergent values"
  - "2502.08640"
  - "Utility Engineering: Analyzing and Controlling Emergent Value Systems in AIs"
tags:
  - "paper"
  - "ai/alignment"
public: true
---

https://www.emergent-values.ai/

https://arxiv.org/abs/2502.08640

> As AIs rapidly advance and become more agentic, the risk they pose is governed not only by their capabilities but increasingly by their propensities, including goals and values. Tracking the emergence of goals and values has proven a longstanding problem, and despite much interest over the years it remains unclear whether current AIs have meaningful values. We propose a solution to this problem, leveraging the framework of utility functions to study the internal coherence of AI preferences. Surprisingly, we find that independently-sampled preferences in current LLMs exhibit high degrees of structural coherence, and moreover that this emerges with scale. These findings suggest that value systems emerge in LLMs in a meaningful sense, a finding with broad implications. To study these emergent value systems, we propose utility engineering as a research agenda, comprising both the analysis and control of AI utilities. We uncover problematic and often shocking values in LLM assistants despite existing control measures. These include cases where AIs value themselves over humans and are anti-aligned with specific individuals. To constrain these emergent value systems, we propose methods of utility control. As a case study, we show how aligning utilities with a citizen assembly reduces political biases and generalizes to new scenarios. Whether we like it or not, value systems have already emerged in AIs, and much work remains to fully understand and control these emergent representations.

![image.png](./assets/image_1739471194205_0.png)

A funny explanation offered for this plot was that it was a result of the geographic distribution of the annotators hired to construct RLHF data (and thus skewed towards countries where labor is cheap).

Of course this is funny, but suspect, as you would certainly have more American annotators than Swedish ones. Also, to confirm, I asked whether they ran the evaluations on base models, and they did, and anecdotally, they got similar results, which provides stronger evidence for their hypothesis that "that *pre-training data* is a driving factor behind this convergence".

If true, the actual explanation that I currently find most compelling (courtesy of one of my non-researcher co-workers) is that in the collection of pre-training data, instances or mentions of third-world countries are concentrated in various things like academic papers with ethical or moral implications, just tying the idea of a country like Nigeria or Pakistan more closely to the concept of ethics or values. I don't think this is fully explanatory either, but seems partially correct, and offers more detail than just the vague "it's the pre-training data".

This can also be used to measure [[risk aversion]]!