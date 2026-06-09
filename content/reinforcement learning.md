---
id: note_01jxqv9gwrffet1pfegx2hatk3
tags:
  - "ai/rl"
public: true
---

## Basics

### DQN

### PPO

$L = \min(r_t(\theta)A_t, \text{clip}(r_t(\theta))A_t)$

where the probability ratio $r_t(\theta) = \pi_\theta(a_t | s_t)/\pi_{\theta_{old}}(a_t | s_t)$, i.e. the ratio of the probability that we take the given action under new policy to the probability we take the action under the old policy. Or, in even simpler terms, how different our policies are.

## LLMs

### RLHF

### GPRO
