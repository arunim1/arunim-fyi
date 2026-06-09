---
id: note_01j9wvdzs8esgvp0z6j2mzqafh
aliases:
  - "Membership Inference Attacks Cannot Prove that a Model Was Trained On Your Data"
  - "2409.19798"
public: true
tags:
  - "paper"
  - "ai"
---

In response to [this blog post](https://blog.ml.cmu.edu/2024/09/13/rethinking-llm-memorization/) I once said:

- > If a certain phrase exists within the LLM training data (e.g., is not itself generated text) *and* it can be reproduced with fewer input tokens than output tokens, then the phrase must be stored somehow within the weights of the LLM.
- not really sure this is true—can def think of cases where it feels like it need not be the case. If a simple sequence only explicitly shows up in the training data once, but the general form is present many times such that the full sequence can be inferred, it seems more likely that the phrase is not what is stored, but the general form. (e.g. multi-digit addition)

This seems related to this paper. TODO: read and write about this paper: https://arxiv.org/pdf/2409.19798
