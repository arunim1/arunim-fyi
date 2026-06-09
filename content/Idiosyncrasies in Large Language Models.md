---
id: note_01jpp0wrvref8rfgcx740sdjed
aliases:
  - "Idiosyncrasies in Large Language Models"
  - "2502.12150"
public: true
tags:
  - "paper"
  - "ai"
---

[[2502.12150] Idiosyncrasies in Large Language Models](https://arxiv.org/abs/2502.12150v1) 

> In this work, we unveil and study idiosyncrasies in Large Language Models (LLMs) -- unique patterns in their outputs that can be used to distinguish the models. To do so, we consider a simple classification task: given a particular text output, the objective is to predict the source LLM that generates the text. We evaluate this synthetic task across various groups of LLMs and find that simply fine-tuning existing text embedding models on LLM-generated texts yields excellent classification accuracy. Notably, we achieve 97.1% accuracy on held-out validation data in the five-way classification problem involving ChatGPT, Claude, Grok, Gemini, and DeepSeek. Our further investigation reveals that these idiosyncrasies are rooted in word-level distributions. These patterns persist even when the texts are rewritten, translated, or summarized by an external LLM, suggesting that they are also encoded in the semantic content. Additionally, we leverage LLM as judges to generate detailed, open-ended descriptions of each model's idiosyncrasies. Finally, we discuss the broader implications of our findings, particularly for training on synthetic data and inferring model similarity. Code is available at https://github.com/locuslab/llm-idiosyncrasies.

Very fun paper. Two notes. 

on Table 1 (a): notice that the lowest binary classification accuracies, the only ones below 98%, are for ChatGPT with Grok and DeepSeek. 

*I can't believe OpenAI would cheat like that! Copying xAI and DeepSeek's work? OpenAI is clearly training on Grok and DeepSeek outputs, what a shame.*

on Figure 7: one of these is not like the others... Why is Gemini starting it's responses with python, elara, and rain? Okay, maybe '```python' is reasonable, but [Elara](https://en.wikipedia.org/wiki/Elara_(mythology))?? I have to imagine that it's because of low sample size.