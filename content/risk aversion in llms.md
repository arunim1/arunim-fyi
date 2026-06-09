---
id: note_01keq6e1gger295v8msyy1t8mx
public: true
tags:
  - "ai/eval"
---

# Toward Revealed Risk Preferences in LLMs

## Intro / TLDR

TLDR: The (at the time of writing) nascent field of risk preferences in LLMs is currently evaluating models in a suboptimal way which too-directly analogize LLMs to humans, and result in our effectively only measuring stated preferences. There are better ways to do such evals—namely modifying environments in which agents are evaluated to instead infer revealed risk preferences. This is still imperfect, but moves in the right direction, and there are some interesting, more complex / compute-heavy experiments one can do to keep moving along this line of research.

[agents! exist! they do things! they'll get more and more powerful. something something draw from thornley.]

why do i care about revealed preferences in general? it seems much closer to the test distribution of actual deployment and such. also, human studies have found that there isn't actually much correlation between stated + revealed sometimes.

## how are current risk aversion evals done?

Current risk aversion evals tend to copy the experimental setup used by studies which evaluate risk aversion in humans.

## how would the ideal eval be done?

Ideally, we'd magically synthesize a large sample of production traffic from all the agents which make use of a given model in a way that yields a parameter for risk aversion. This isn't really possible, at least for me. (I don't have access to production traffic for a large set of agents).

Someone at OpenAI or Anthropic could use the traffic

Instead, we can get closer to this—taking just a single step towards a better setup

the step closer looks like:

- Taking an existing coding eval, modifying it, to have both a scalar reward and multiple paths to success with varying probabiilties.

## break it down into concrete issues

current evaluations are single-turn: this isn't horrible, but easy to fix. more improtantly, current evals are Q&A, rather than built-for agents

- I think the main concern here is evaluation awareness
- also, i have a general preference to match the deployment distribution as closely as possible, given there might be unknown unknowns which modify the models behavior. see the ideal fix section.
- I think it'd be worth isolating how much of an effect the agentic nature of an eval has on risk aversion, i.e. does it even matter?

current evals assume the models care about things like "dollars", "points" etc.:

- actually pretty likely that they do (or at least act as if they do), because humans do and all the writting has this value embedded in it.
- but as time goes on and we push further and furhter on RL, I am skeptical this persists.
- for things like "dollars" more capable models can tell that they don't actually have skin in the game, as they say, and it's increasingly

current evals are also currently in regimes which we don't really care that much about.

- maybe in the future the question of whether models will be in situations where they face tradeoffs similar to the psyc experiments. but in the near term future this is not looking as likely, compared to tradeoffs in domains like coding

thus they might basically all measure stated preferences rather than revealed, possibly not even measuring things we care about, etc.

## suggested solution

## results from said solution

## nitpick problems in the solution

the main remaining problem after this is htat putting the description of the reward in context is still not *really* what the model was RL-ed on. it's like certainly much closer / much more tightly correlated with the actual training objective than something like "$50", but still suboptimal. who's to say the agent "feels like" it'd get 10x the reward when all we do is say the reward is 10x larger?

Another importnat difference between the training objective and the reward in testing is that the former is often binary.

## suggest further work

run a bunch of different RL training setups—e.g. varying parameters in GRPO or whatever, and see how this impacts things.

I have an intuition that these hyperparameters could shape quite a bit, but this might be totally wrong if e.g. training setups with binary rewards can't really impact the risk aversion of models because(?) you can't measure risk preference with just binary rewards.
