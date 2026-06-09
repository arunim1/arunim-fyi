---
id: note_01j8252begeg98k3wg11a8jg7q
public: true
aliases:
  - Fog-of-war
---

Fog-of-war chess is by far, my favorite game in the world. Fog-of-war is a variant of chess (available on [chess.com](https://www.chess.com/variants/fog-of-war)) where you are only able to see the squares your pieces are or where your pieces can move. That is, at the start of the game, you can see your half of the board (your pieces on the first two rows, and the next two rows, to which your pawns and knights can move), and nothing else.

![fow.png|424](assets/fow_1728409382048_0.png)

I first tried playing in early 2020 and became heavily invested (some have said addicted) over the course of quarantine.

There are so so so many great things about it, including that it's very much unsolved—there don't even exist superhuman bots for this game. I desperately want to ask the legends who [left](https://sifted.eu/articles/three-cofounders-leave-h-news) [hcompany](https://www.hcompany.ai/) if they want to solve fog of war with me instead of creating AGI. Why aren't there bots that can play fog-of-war chess well? Many reasons:

- You can, and likely should, truly randomize your actions rather than playing the same move in any given scenario—the action space is the "convex hull" over the usual actions available in the same board state in chess (nearly). You can imagine how this *greatly* increases the number of actual actions available at each step (goes from a medium-big number to technically infinity).
- It's an imperfect-information game—at most steps of the game, you do not know the true, full board state. You often have to internally model or just guess where your opponents pieces are or aren't. Also, because of this, it can become a bluffing game even at the non-elite levels, as opposed to traditional chess, in which at best, it's psychological at the elite levels, and only when you can see your opponent.
- You might be tempted to think: "poker is an imperfect information game where you can play mixed strategies, and poker is solved, so surely this is straightforward".[^1] NO. Even *actions* are often hidden in fog of war—especially in the opening, you can go for multiple turns without any proof that your opponent has taken a particular move.
- This might be minor, but there's some cases where you can *lose* information in fog-of-war, as opposed to other imperfect information games like Stratego, where you gain or retain information at each step.
- It is unfortunately the case that ~20k individuals play worldwide, meaning that it isn't exactly given the same investment as standard chess or go.

What else makes it so [[fun]]?

Even when you're down significant material, you can "hail mary" and occasionally catch your opponent off guard.

It has a reasonably quick learning curve starting from normal chess (or I'm misremembering because of just how many games I played)

Not all the traditional chess wisdom transfers! Hikaru himself has been beat on stream by random players. In fact, in at least one case, he even thought they had to be cheating when they weren't (necessarily), given that to a veteran fog-of-war-er like myself, the moves his opponent played were very reasonable.

I also think ELO : material handicap ratio would be very different in fog-of war. A player with an elo of +150 compared to me could very well beat me while down a queen (unfortunately I speak from experience here), whereas I doubt the same holds for normal chess.

[^1]: TODO Someone should fact check this, since it seems reasonable that the fact that poker actions are public means that mixed strategies are meaningless. But [Nate Silver said he agrees](https://open.substack.com/pub/natesilver/p/5545-is-a-really-close-race?r=6mm1j&selection=c8ac47c4-bcfc-45ab-af75-de0525d93984) so IDK. I'll get around to fact checking in a while.