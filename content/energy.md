---
id: note_01k0jjbtzrfsrbdj7ed8gndp11
public: true
tags:
  - "ai"
---

# Intro

Energy/power is important for datacenters, which are important for AI, which is important. I want to learn all about power generation and deployment. Here are a bunch of notes on power, largely from a conversation with [Owen](https://owenfrausto.github.io/).

# Power 101

Different sources and consumers of power have different characteristics, including their power factor and inertia.

## Real vs. Reactive Power (Power Factor)

Consumers of power have different power factors, defined as the ratio of real to total (real + reactive) power consumed.

Things like fridges have lower power factors, because they consume more reactive power (smth like inductors / capacitors and motors. Things like heaters have higher power factors.

Generation usually has a high power factor.

Changes in reactive power impact voltage stability.

### Aside: Physics

Real power $P = VI\cos(\phi)$ while reactive power $Q = VI\sin(\phi)$. Where $V$ is voltage, $I$ is current, and $\phi$ is the phase shift between the two.

So, for small phase shifts, which is what I expect, the level of reactive power is roughly linear with the phase shift. And it doesn’t seem to depend on the level of voltage or the level of current.

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXe_W2LVMDMEZw8yY9GhjYW1VoLvcQAirqcj9QYPaJ9Hyc7haA782gn0Jco8ma5VQe6RiOLoQbu7WRcuxJV_dJbS7WlBB7ELzxiEkeEfWgewUWSI5_Mw-ssBnnlb_VjqpgluKp06eg?key=xqgi-CVw8wnEvlh71gnfUg)

## Grid Inertia

To generate power, coal plants, for example, will rev up one of these absolute behemoths. This is the thing that creates the current when it rotates (with a coil).

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXdFB_nH1gfw7CLJf5oeLQLXbVeQUQM06wDAwUo7hJ6SmZpDUGIDpfsKh9D7ReVdjnXN3yGLVWyVXUJt9uXNHcnd37QP-1tsDAL5a4uqy_mDCc2HcrN9hob-e4bme_xccUpjwvOtDw?key=xqgi-CVw8wnEvlh71gnfUg)

So the concept of inertia is pretty intuitive, this giant cylinder literally has inertia—it’s difficult to change the rate at which it spins by very much.

People, on aggregate, usually have a very stable, difficult to change demand: high-inertia.

Coal and natural gas plants’ power generation is also high-inertia, the cylinder is not stopping.

Low-inertia generation are things like solar and wind. Nuclear is stable (high inertia).

The grid wants high inertia demand and high inertia supply, and to minimize the difference between supply and demand.

Changes in grid inertia affect frequency stability.

### Why minimize the difference between supply and demand?

If there’s a sudden drop in demand, there is momentarily more power generated than being used, and since the energy must go somewhere, those giant spinners literally end up spinning faster. Then you have to adjust how much mechanical input you’re putting into them, and hope that it stabilizes. And for that moment when they’re spinning faster, the frequency jumps from 60Hz to like 60.05 Hz!

High inertia sources can deal with this well, low inertia sources (usually) cannot. [TODO double-check]

## Analogy time

For the sake of the analogy, imagine this buff dude was doing the exercise all wrong, with the ropes in sync.

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXcoiigpkIL_f4iU3pKcv78Lbg7Nxdj2PiQDZp_zXgZfv1etVRyLwlPdgSeeBmbpXR3m1uks6uB-AM3bUxb7ojJzmaV-YrpNzMxqGuSvI7vPYzrMKVAdP9TgIhA3PMnWsLO81SiruQ?key=xqgi-CVw8wnEvlh71gnfUg)

TODO fill in the rest of the analogy.

## Inverter-based resources

Owen showed me this visual:

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXf_ZKOY35bX8pNpZerqQzxobGe2XU7W1YfHaD_rFb0EiIDwEtriA2gjf54d56y52D5j05fvSGIK6XhbcfVErUDPvS9r0OOCM325WHyEsW_7TKmZj5gQUt4GpP4k5MPRtXqkPi0sHw?key=xqgi-CVw8wnEvlh71gnfUg)

To which I asked “Why are batteries having to wait to get on the grid? Shouldn’t the grid be wanting more batteries which can help alleviate any differences in supply and demand?”

The answer is partially that batteries are inverter-based.

Inverter based resources include solar, wind, batteries, and anything that doesn’t immediately generate power at 60Hz or consistently spin at 3600 rpm.

These are bad at dispatching reactive power, and dispatch agnostic to grid frequency.

Also, adding storage would likely push the majority of the power generation stack to the right, and can push lower-inertia generation sources off the stack entirely.

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXcMBLppufBYY9NEY_L5AY98kJ-T5bBWJtPZVPrgEj4vz8vx5gak5kSaqcxcqrc2-3PeJHZWP-X9bVJbqkZ7DTO05c04YPc8K9fLdi4Ms8Xpjy2LVJdL-yUfplpi_mp65VlFJS7ewA?key=xqgi-CVw8wnEvlh71gnfUg)

# Economic Factors

## Congestion Pricing

Congestion pricing-esque dynamics make datacenters increase energy prices more than you might naively expect.

The price of power also includes the price of transporting energy to you, so if you are like 400 miles down the line, and a 1GW datacenter opens up 500 miles down the line, then the power plant has to ship that GW to you as well, and you end up paying for part of that burden. This is on top of simple supply vs demand incentives. And part of a more complex network, of course.

# Datacenters

## Characteristics

Datacenters are also low-inertia demand, see [this](https://semianalysis.com/2025/06/25/ai-training-load-fluctuations-at-gigawatt-scale-risk-of-power-grid-blackout/) from Semianalysis. Basically, both within a training run and in general, datacenters may quickly go from requesting nothing to hundreds of MW and vice versa.

Some folks, e.g. Southwest Power Pool (SPP) have started selling lower-tier power, which is essentially the first to get shut out when the grid needs to cut power to prevent a blackout.

## Incentives and Dynamics

There might be an incentive for the datacenters to *want* to be the kind of customers of power that the grid wants to sell to (i.e. stable demand). So, they might not just optimize for max FLOP or token or best training run, they might also optimize for stability of demand.

If the grid goes out dips a little bit, as a datacenter owner I might want to switch to backups until I'm sure we're good. But this is a huge imbalance for the grid which has just lost a ton of demand without also losing generation.

# US - China

Total power generation looks like this:

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXcOWOFOyzHtDZrIikGbg2yJj0u8armd8lQ9Cfp0emz4Is-voZ3KAL8VJ9x7y5Md8iTAhcZm7cRtthnjVa9-8FoRCR_CE5fKO5OmypIdMoONvBU_l95Cxb0qmMDa7ijCaSVvJLKtrw?key=xqgi-CVw8wnEvlh71gnfUg)

Two things to consider here:

Generation v. Generation Capacity: each one actually generates a bit under what it needs.

Generation Capacity v. Datacenter generation capacity: each one only allocates some portion of its generation to AI datacenters. So the relevant number to be watching out for is more like “total generation minus population and other non-datacenter consumption”. With any luck, Chinese electricity generation will keep going to the non-AI industrial centers and the Chinese population itself. (Realistically, it seems that the proportion towards industry in general will be higher in China, and become dominated by datacenters.)