---
id: note_01jshspfz8e2ka1v9g9647w5ar
tags:
  - "ai"
public: true
---

todo organize these!

[[reinforcement learning]]

## Training

- ZeRO stage 1:
	- data parallel
	- all params on all gpus
	- local loss, local gradients
	- construct the global gradient on every by averaging the local gradients
	- update optimization variables (e.g. moment and variance) corresponding to the right set of 1/n parameters
- ZeRO stage 2:
	- same as above except that the gradients are also split, so you calculate a portion of the
- Stage 3:
	- same as above except that the params are split, so you have to copy them over to each GPU to run fwd pass, and each
- Mixed precision?
	- we want to do computations in FP16, because FLOPs are expensive.
	- memory is also expensive too, but less than computations, and so we're more willing to give
	- loss scaling helps mitigate some of the issues we would face from FP16 computations, by artificially scaling up the loss and before backward pass, but you can get more from loss scaling if the copy of the weighs you're updating are
