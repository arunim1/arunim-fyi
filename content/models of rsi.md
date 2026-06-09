---
id: note_01kj65dap0f20v6s1rqhra2y48
public: true
tags:
  - "ai"
---
Status: rough draft

What even is RSI? Here's my attempt at [defining it](RSI). TLDR I think it means humans out of the loop of AI development 

Below are some models of how RSI comes about. 
## The naive one
This tweet from [Aidan McLaughlin, circa September 2024](https://xcancel.com/aidan_mclau/status/1838930959258775867), feels pretty representative of the vibe at the time.

>asi feels closer than agi if that makes sense

And the hype only intensified after we saw o3-preview.

My rough model at the time was "oh okay they're just going to RLVR all the way up to ASI somehow", (e.g. by learning from the problems GPT-N got right 10% of the time to make GPT-N+1 which gets these problems right 90% of the time) but it seems like that hasn't turned out to be the case. More and more compute has been applied to the RL part of training, the reasoning models have been used to train their successors, and while the returns have been large, they don't seem to be large enough to directly get us to completely automating AI R&D. Nor have they generalized in the strong ways that might have been expected. 

I think I'm getting a bit off track with this line of thought, though. The actual thing that I wanted to discuss or write about here is different models for takeoff or recursive self-improvement, and to actually examine how many of them, or which of them, are realistic given the evidence that we have accumulated so far. What I meant to convey with the RLVR point was that there was some feeling at the time in September 2024, that the path to ASI was indeed clear and it would simply be to scale up RL training. I think that is just not the case now for a variety of reasons. There are still a variety of approaches that could be plausible for recursive self-improvement, and I'd like to examine what they are because, in my view, the risks that we have to consider from AI development are quite path dependent on how exactly are we getting to ASI.
## The bottlenecks view
I also put substantial weight on "the bottlenecks view", by which I mean that AI developers will close loops / close the loop in AI development without initiating a discontinuous intelligence explosion. When people say that "AI systems haven't closed the loop" yet, I find it a bit off-putting. Like sure, they have. The outcome has just been capped. They've closed the loop on everything from datacenter to chip to kernel design ([AlphaEvolve](https://deepmind.google/discover/blog/alphaevolve-a-gemini-powered-coding-agent-for-designing-advanced-algorithms/)) and none of these have led to discontinuous AI development. 

Another way to look at this is that as soon as a given loop is closed, whereby an AI system can improve itself / the next generation, it often becomes worthwhile for AI developers to "let it rip", "go pedal to the metal" and the loop runs itself to whatever cap there is. This happens quickly, by virtue of the loop being automated, so most of the time is spent in normal rates of development, where AI is bottlenecked by whatever still remains. 

I think this hints at something like: for *actual* RSI, you would need AI-caused algorithmic improvements or other speedups which are themselves compounding. Speedups, like those that AlphaEvolve has found, are compounding in some ways, in that they apply to all future systems, but they don't themselves lead to. A "fully complete loop" with robots creating more robots and more compute would be compounding. But on reflection, this, too, would only be compounding up to the point where you run out of raw parts for said robot. 
## The bag of tricks 
Maybe things like the "bootstrapping" + RLVR method is just one of many ways in which AI will contribute to it's own development, and at some point, with enough such tricks stacking on top of one another, we get RSI. 
## Synthesis
I'm not certain what the takeaway from this line of thought should be. Overall, I'm more skeptical that RSI is the right framing at all, and instead think that the correct level of abstraction is "let's look at rates of all-things-considered-growth". 


## Things to read and review etc.
1. https://ai-2027.com/ 
2. https://www.planned-obsolescence.org/p/six-milestones-for-ai-automation
3. 