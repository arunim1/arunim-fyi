---
id: note_01jwksqfw0frrvrsfmrvqj7qkr
aliases:
  - remrofsnart
public: true
tags:
  - "ai"
---

TL;DR: I trained a previous-token-predictor, because it is funny! Maybe it can also serve as a jumping-off point for some adversarial robustness helper, kind of like [[Eliciting Language Model Behaviors with Investigator Agents]].

Play with the model [here](https://huggingface.co/spaces/arunim1/remrofsnart)!

GPT says: What happens when you flip the script—literally. Instead of predicting the next token, what if we tried predicting the previous one? Intuitively, pre-trained models trained with the objective of predicting the next token are learning the correlation between input tokens and what follows, and so might be a few steps of fine-tuning away from predicting *previous* tokens instead. On the other hand, language often follows a somewhat logical structure, and working backwards is often harder—for example, language is probably designed (evolved?) such that there are always many more questions per-answer than there are answers-per-question.

### Goals:

[done] Recall how to train a transformer

[done] Flip things around so we learn previous tokens instead of next tokens.

~~Profit~~

Implement a bunch of the architectural improvements that I don't fully understand yet, and use this as an excuse to understand them.

Compare how much easier / more difficult forward vs. backward is in various languages.

### Notes

I did the first two, and found that, for small-ish datasets, e.g. shakespeare, the previous token-predictor does quite well (loss < 3.1), while for larger datasets, e.g. open web text, the previous token predictor both requires more substantial training (shocker), and still only achieves a loss of ~3.3.

See [wandb](https://api.wandb.ai/links/arunim_a/8lcegnba) logs.

### Future extensions

I'm very curious to see how this works for various languages—i.e. what's the difference in loss for finetuning on a Chinese equivalent of Openwebtext when predicting next tokens vs predicting previous tokens? There are very likely