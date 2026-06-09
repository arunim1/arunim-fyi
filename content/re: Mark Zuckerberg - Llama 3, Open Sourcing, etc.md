---
id: note_01jp5sxzw0ehrsdv5q4sc7wx2z
tags:
  - "podcast"
  - "dwarkesh"
  - "ai"
updated: "June 17, 2024"
aliases:
  - "Zuckerberg-buying-GPUs"
  - "Zuckerberg buying GPUs"
public: true
---

TL;DR: Zuckerberg seemed pretty in-tune with the technical details of Meta's AI projects, and he clearly cares about making it accessibility for developers (side note: the financial case he made for open sourcing foundation models didn't strike me as sound)[^1]. However, in talking about Meta's investment in GPUs to make Instagram Reels competitive with TikTok, I found his comments about spending billions of dollars on infrastructure to keep users scrolling incredibly casual, even callous, and indicative of some important difference in perception.

## Meta's Investment in Reels

During the interview, Zuckerberg discussed Meta's decision to invest heavily in GPUs to make Reels more competitive with TikTok. He said:

> we were constrained on basically the infrastructure that we had to catch up to what TikTok was doing as quickly as we would have wanted to. So I basically looked at that and I was like, hey, we have to make sure that we're never in this situation again. So let's order enough GPUs to do what we need to do on reels and ranking content and feed. But let's also, let's double that, right?

It's crazy to think that in some ways, he aimed for TikTok and landed on AGI. What an incredible businessman, honestly. Initially, I thought it was [[luck]], but he was kind of [[going off of vibes]], and the vibe of "big models matter" that he got was absolutely correct.

## Adversarial Engagement-Optimized Algorithms

The algorithms powering Reels and TikTok and every other variant are designed to keep users scrolling and engaged. Maybe I, as a person who has been defeated numerous times by the algorithm (read: been convinced to stay on the app for hours or days on end), am projecting, but I genuinely feel like the training of these models is adversarial. The mush inside my skull (and billions just like it but slightly different) is going up against the best algorithm Meta's engineers could make, running on billions of dollars worth of Nvidia's finest GPUs.

Sure, the same general idea goes for the multi-billion dollar physical ad industry (or even Netflix optimizing watch time with A/B testing of button design), where the best marketing companies probably work out what colors will keep my eyes on their billboard long enough to get the message. However, I think that it's very different to compete against some project manager with a 20-person focus group and their own skull mush than to compete with a program made with a supercomputer. I'd take a daily chess match against 20+ humans over a million-dollar training run any day, especially if my wellbeing is on the line.

However, Zuckerberg characterizes this differently:

> Cause I mean, that's just such a big unlock for Instagram and Facebook to now being able to show people content that's interesting to them that they're from people that they're not even following.

This stark contrast in perception is concerning. What I see as yet another challenge in an adversarial battle for users' attention, Zuckerberg sees as a "big unlock". I readily acknowledge that I'm quite late to the game of "social media is bad for your brain", but I think that there's something different for me with the GPUs and (perhaps too anthropomorphized) neural networks I've got to compete against.

## Some Counterarguments

You might argue that Meta is just giving users what they want by showing them interesting content, and that it's up to each user to manage time spent on the app. But I think that ignores the fact that users a) may not be operating on complete information, and b) may have their desires changed. For example, take a friend who mistakenly believes that he won't find nicotine addictive, tries it, and gets hooked. He originally found it undesirable to get hooked, but the nicotine lights up pathways which alters his desires such that getting hooked is acceptable. Just because I find myself mindlessly scrolling through Reels for hours doesn't mean that's how I genuinely want to spend my time, and I'd argue it's dishonest to claim that I've “voted with my thumbs and that's that”.

[^1]: Side Note: Zuckerberg, if I recall correctly, defends the open-source argument by claiming that Meta could recoup a \$10B investment in a training run that was open-sourced by a 10% decrease in inference costs over \$100B original inference costs, powered by efficiency gains found by open-source developers. There's no way that the finances of this are correct. For one, it'd be a public good at that point, given that, as far as I know, the Llama architecture is not Meta-specific, let alone the hardware on which inference is run. Beyond that, say that the major efficiency gains are driven by ~75 developers. Meta can choose to instead spend \$1B on hiring 750 potential developers who can make the advancements instead, and have cut costs \$9B. The open-source decision for Meta is clearly image, PR, and values-driven, all of which can then translate into shareholder value, which makes the presentation of a financial case for it a bit odd to me