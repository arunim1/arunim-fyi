---
id: note_01jssntctge0radsxefbw06jf6
aliases:
  - "Virology Capabilities Test (VCT): A Multimodal Virology Q&A Benchmark"
  - "2504.16137"
public: true
tags:
  - "paper"
  - "ai"
---

[[2504.16137] Virology Capabilities Test (VCT): A Multimodal Virology Q&A Benchmark](https://arxiv.org/abs/2504.16137v1)

> We present the Virology Capabilities Test (VCT), a large language model (LLM) benchmark that measures the capability to troubleshoot complex virology laboratory protocols. Constructed from the inputs of dozens of PhD-level expert virologists, VCT consists of $322$ multimodal questions covering fundamental, tacit, and visual knowledge that is essential for practical work in virology laboratories. VCT is difficult: expert virologists with access to the internet score an average of $22.1\%$ on questions specifically in their sub-areas of expertise. However, the most performant LLM, OpenAI's o3, reaches $43.8\%$ accuracy, outperforming $94\%$ of expert virologists even within their sub-areas of specialization. The ability to provide expert-level virology troubleshooting is inherently dual-use: it is useful for beneficial research, but it can also be misused. Therefore, the fact that publicly available models outperform virologists on VCT raises pressing governance considerations. We propose that the capability of LLMs to provide expert-level troubleshooting of dual-use virology work should be integrated into existing frameworks for handling dual-use technologies in the life sciences.

There's been some commentary about this paper on X, (aside: I enjoy the phrase *X commentariat* as first seen [here](https://www.ai-frontiers.org/articles/ai-risk-management-can-learn-a-lot-from-other-industries)), and one particularly persistent commenter has claimed that multiple choice question is an invalid format, presumably because it narrows the search space so much. I was going to suggest converting it to open-ended, but the paper authors already did this and ran it in "full text (FT)" mode:

| Model | MC | MR | FT simple (complex) |
|-------|-----|-----|---------------------|
| Claude 3.5 Sonnet (Jun '24) | 46.4 | 26.9 | 30.5 (33.2) |
| Claude 3.5 Sonnet (Oct '24) | 48.4 | 33.6 | 37.4 (37.2) |
| GPT-4o (Nov '24) | 39.0 | 18.8 | 25.5 (21.4) |
| Gemini 1.5 Pro | 40.7 | 25.4 | 31.9 (33.7) |
| Gemini 2.0 Flash (exp) | 37.9 | 19.5 | 30.9 (32.4) |

But the result of FT > MR is indeed weird! Does this mean that the MR is tripping up the models with e.g. plausible but incorrect answers? Or it's a overly permissive LLM judge. I imagine a human baseline for FT would be too expensive.
