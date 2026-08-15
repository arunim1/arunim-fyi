---
tags:
  - ai
public: true
---
Rough notes on [Attestable](https://attestable.com).

## What is Attestable

They have created a prover, and the prover creates a proof alongside inference that is occurring on a transformer. Given the weights of the model, the policy of the prover, the policy of the inference, the input, and a random seed, it proves that this output is indeed corresponding to the model and the input. And in particular, it does so in a way such that the verifier of this proof does not need to see any of the weights. The verifier just sees the input, the proof, the random seed, the policy, and the output, and can confirm that this output corresponds to this input and model.

## Their framing

The way that they frame it, at least for AI safety, is as a model-weight security thing — you can block all network egress except things that have been cryptographically verified to have come from the model. On some level this makes a bunch of sense. On another level it doesn't make total sense: in the interview with one of the VCs that funded the startup, they say you need to be hardened against state-level adversaries.

Separately, they brought up two other threat models that are interesting to think about, and are much stronger in my opinion. One is that the code you're running is compromised — PyTorch is compromised. The second is that the attacker has root access to the hardware, or the data center, or the GPUs in the data center.

## Model weight security
### Red-teaming

What would I do if I was the attacker in these scenarios? I would just read off the weights, transcribe them to text, tell the model to repeat back to me these weights, sign it, exfiltrate it, convert it back to numbers. No problem. Or you can get more inventive with the vocabulary — if you're encoding things in hexadecimal, this shrinks the number of tokens you need, maybe with a slightly higher error rate. It's on the order of less than a percent of a day's worth of data center output, and adversaries are more than capable of waiting that long.

### Counterpoint/Blue-teaming

The counterpoint is to verify that inputs and outputs correspond to particular inputs that have been received. On the egress layer, the verifier would have to store a set of approved inputs and append to that as prompts come in, and check against it. I haven't thought too hard about it, but in hindsight I think that just works. It solves that, and invalidates my suggested workaround.

## Claims

The other thing was that there are claims on Twitter, at least from Yonadav Shavit, that this gets you a lot of the way to verifying whether it is or not. And what do I think? At some level, I think this ends up pointing me to confusion about the actual thing the prover is able to do. What information does the verifier have?

## What can the verifier see?

Who's the verifier in the case we care most about? China, I think. Does China have access to everything? My initial guess is that they have access to everything. They have to share artifacts, which isn't that bad. It's fine. A follow-up question is how detailed that has to be — how much of the architecture, how much of the infrastructure.

The biggest question from my take is: what is the relationship between inputs to the verifier and things the opposing party in a bilateral agreement is able to see? My current understanding is that they are the same. In that case it seems very relevant and important.

The verifier does not have the weights. But what is the policy? I think the policy is basically everything from the architecture to the kernels and any other optimizations in the code. Is that shared with the verifier? My assumption is yes. I remember seeing something about being able to hold out any one of the inputs — so you don't have to hide only the model weights, you can hide the policy — but my intuition is that this comes at the cost of showing the model weights, which is obviously not something people are going to be amenable to.

But yeah, if you do share architecture, it seems quite promising. And then you need to prove the number of operations you did — and it seems like to do that you need the architecture and the kernels, everything that goes into inference apart from the weights.

So you can actually get good verification out of it, which I'm happy about. But it's good verification at the cost of high transparency, and there are obvious concerns about distillation.

## Inference-only verification

Inference-only data center verification is intimately tied to the verifier being able to see the policy, and then based on the policy and the input and the output, compute how many FLOPs were performed.

So what verification regime do you get if all my assumptions are true? If you share all the input data, all the output data, and the architecture, then you can get verification that data centers are inference-only. It doesn't seem particularly likely — but I'm glad there is another option now available.

I'm not commenting much on model-weight security. I don't think that's the biggest issue. I think that has been more on track to getting solved than inference-only data center verification, so the fact that it's been more robustly solved makes it less of a candidate, in my opinion. Though of course it has good upsides too.

![[Pasted image 20260814135854.png|346]]

## Harden before you verify

Actually, I think the way in which they solved model-weight security is probably quite good.

For a while there was a general concern in the spheres of people interested in MAIM — Mutual Assured AI Malfunction — about ending up in a regime where you have hardened before you verify, which makes the verification very difficult. The MAIM concern is actually distinct from the harden-before-you-verify thing. Harden-before-you-verify is the more general concern: if you want both verification and hardening, you need to do verification first and hardening second. Otherwise you end up in a regime where it's very easy to get one but not the other — in particular it's very easy to get hardened systems without having them verified, because once they're hardened it's harder to send somebody in and change the infrastructure, whereas the other way around is much more feasible.

The kind of hardening you get from this is just network egress. This, plus network egress, plus prompt-input caching or adding to a list on the verifier securely, seems sufficient. You should still do physical security, but you don't need some of the more stringent measures people were thinking of for SL5. I should think more about this.

Of the SL5 solutions, this seems like one that is not detrimental to the prospect of verification in the near future. Indeed, it enables a particular kind of verification if implemented as an SL5 standard.

## Mutual assured AI malfunction

You may still want the dynamic of countries being able to sabotage each other's training runs, or even inference. Default proposals for SL5 seemed to be full-stack, in the sense that they would prevent those kinds of attacks as well. Proponents of mutual assured AI malfunction say these attacks are good to keep open, because they slow down development and enable more time for things like verification to get solved.

This kind of model-weight security doesn't really prevent attackers from getting in, screwing with stuff, changing settings so the GPUs degrade, or whatever the sabotage is — which is nice, because it leaves the option open.

## Overall

Overall I'm pretty bullish. I can think of schemes in which you use this to get both model-weight security and maybe enforceable-treaty verification. There's a lot more that would have to go into an international treaty: you can tell how many FLOPs of inference a data center is doing, but you also need to go down the stack to make sure there isn't secret chip production or secret GPU stores. In general this is why verification is a harder problem. But overall, pretty excited about this.