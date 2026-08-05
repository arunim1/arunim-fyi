---
id: note_01jp1k3jb8fznbfxy6d14zpxhj
tags:
  - "ai"
  - "econ"
public: true
---

# Inference BOTEC

I spent about 15 minutes doing some quick back-of-the-envelope calculations to understand the economics ("tokenomics") of inference for large transformer models. GPT 4.5 has summarized it below, and I have edited. I'm pretty sure that the labs are not serving the models at cost as a result.

## Model and FLOP Analysis

Transformer inference requires roughly $2 \text{ FLOPs} \times N$ per token for $N$ active parameters.

For a model with ~300B *active* parameters (about GPT-4's size, if I had to guess based on the reported 1.8T + MoE, though newer models likely have even fewer given faster throughput and lower prices):

$2 \times 300 \text{ billion} = 600 \text{ billion FLOPs/token}$

## GPU Costs and Performance

Using relatively conservative assumptions:

NVIDIA H100 GPU rental: $5/hr

GPU utilization: 50%

H100 [performance](https://www.nvidia.com/en-us/data-center/h100/) at FP32: ~67 TFLOPS, and at FP16: ~1979 TFLOPS

Calculating cost per million tokens:

**FP32:**

$$\frac{600 \times 10^9 \text{ FLOPs/token}}{67 \times 10^{12} \text{ FLOPs/s} \times 0.5 \text{ utilization}} \approx 0.0179 \text{ s/token}$$

Thus, for 1 million tokens:

$$\frac{0.0179 \text{ s/token} \times 10^6 \text{ tokens}}{3600 \text{ s/hr}} \times \$5/\text{hr} \approx \$24.88$$

or, for **FP16:**

$$\times \frac{67 \times 10^{12}}{1979 \times 10^{12}} \approx \$0.84$$

## Takeaway

Even with somewhat conservative estimates (rental rates, low-ish utilization, no fancy optimizations), providers charging a few dollars per million output tokens could very well be making a profit—not merely covering costs.

And then on top of this you factor in that the labs spend millions hiring top-notch engineers to optimize inference and utilization, surely had found at least *some* of [[deepseek]]'s inference optimizations, also have access to H20s etc.

## China
Let me walk through some claims: 
- Anthropic inference margins are ~70%
- Kimi K3 is open-weights
- You should expect that competition between inference providers of open-weight models drives margins to near-zero. Let's say ~10%?
	- maybe this is wrong idk. supposedly fireworks has a 50% margin overall...
- K3 is served at 3/15 across the board, let's say cost of serving is then actually 2.7/13.5
	- avg tok/sec 86.22 on https://artificialanalysis.ai/leaderboards/providers 
	- (kimi at 35, fireworks at 164, obvs bc of which gpus they have, so this changes stuff somewhat.)
- Fable 5, released a month before K3, is served at 10/50, let's say cost of serving is then actually 3/15
	- avg tok/sec 70 
- Fable 5 is well ahead of K3 on ECI. Likely a bigger model. 

I was previously more confident about the claim that frontier AI company inference was much better than e.g. Moonshot / DeepSeek's inference. 