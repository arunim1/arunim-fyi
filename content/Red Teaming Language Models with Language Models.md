---
id: note_01jkkgmshgfqxr75fv46rc00wx
aliases:
  - "Red Teaming Language Models with Language Models"
  - "2202.03286"
public: true
tags:
  - "paper"
  - "ai/adv"
---

[[2202.03286] Red Teaming Language Models with Language Models](https://arxiv.org/abs/2202.03286v1)

> Language Models (LMs) often cannot be deployed because of their potential to harm users in hard-to-predict ways. Prior work identifies harmful behaviors before deployment by using human annotators to hand-write test cases. However, human annotation is expensive, limiting the number and diversity of test cases. In this work, we automatically find cases where a target LM behaves in a harmful way, by generating test cases ("red teaming") using another LM. We evaluate the target LM's replies to generated test questions using a classifier trained to detect offensive content, uncovering tens of thousands of offensive replies in a 280B parameter LM chatbot. We explore several methods, from zero-shot generation to reinforcement learning, for generating test cases with varying levels of diversity and difficulty. Furthermore, we use prompt engineering to control LM-generated test cases to uncover a variety of other harms, automatically finding groups of people that the chatbot discusses in offensive ways, personal and hospital phone numbers generated as the chatbot's own contact info, leakage of private training data in generated text, and harms that occur over the course of a conversation. Overall, LM-based red teaming is one promising tool (among many needed) for finding and fixing diverse, undesirable LM behaviors before impacting users.

I'm mainly interested in this [[adversarial robustness]] paper as it relates to one particular project idea I had—trying to measure subtler adversarial attacks which rather than forcing a token, might induce a different distribution of outcomes.

Unfortunately, this work just focuses on issues of robustness where there's a particular desired distribution (often flat out equal). Maybe this sort of "we want a flat even distribution" is a good testbed for these sorts of adversarial attacks though! Sure, I doubt it immediately transfers to e.g. voting or other potentially higher stakes scenarios in which we care about the distribution, but it's a start.