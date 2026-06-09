---
id: note_01kj65dap0e3svg1ca8nnq4cyp
public: true
tags:
  - "ai"
---

[Dwarkesh](https://xcancel.com/dwarkesh_sp/status/1989944140105486655) Nov. 2025:

> People will sometimes debate, "How much progress have we made so far between village idiot and AGI?" And I'm just thinking, what the fuck are you guys talking about? The models are currently so much dumber than the village idiot. Village idiots generate trillions of dollars in wages a year. These models generate $30B in revenue a year.

Dwarkesh is getting at something real — there's a huge discrepancy in the models' intuitive capabilities and the amount of revenue they're able to bring in. But another often-used frame is age / education level (e.g. in Situational Awareness), which seems a bit more quantifiable as well, so I wanted to quickly run the numbers on this as well.

Questions this may help answer:

- *Is there a consistent delay between models intuitively being as smart as a particular age and generating income comparable to humans of said age?*
- *If yes, what's the delay?*
- *What if we factor a delay from diffusion?*
- *Is it predictive?*

Future work may include a similar BOTEC but for IQ, e.g. based on https://www.trackingai.org/home

- Update: had Claude start looking into this, surprisingly promising.

== Claude-generated stuff ==

TODO clean up

# The numbers

Total US W-2 wages (TY 2020): **$7.93T** [verified — [IRS SOI W-2 tabulations](https://www.irs.gov/statistics/soi-tax-stats-individual-information-return-form-w2-statistics), TY2020 is most recent available as of Jan 2026]. World employee compensation: **~$58T** (world GDP ~$111T × [ILO global labor share ~52.4%](https://www.ilo.org/media/408221/download)) [verified direction, approximate].

AI lab revenue (annualized run-rate, early 2026): OpenAI **~$20B ARR** ([PYMNTS](https://www.pymnts.com/artificial-intelligence-2/2026/openais-annual-recurring-revenue-tripled-to-20-billion-in-2025/)), Anthropic **~$14B ARR** ([Sacra](https://sacra.com/c/anthropic/); [Epoch AI](https://epoch.ai/data/ai_companies_revenue_reports.csv)). Call it **~$34B** for the top two. **Important caveat**: these are ARR (annualized run-rate), not actual booked annual revenue, which is substantially lower due to rapid growth within the year. Actual 2025 booked revenue is probably more like ~$12B (OpenAI) + ~$4-5B (Anthropic) ≈ $16-17B. See [Ed Zitron on ARR abuse](https://www.wheresyoured.at/howmuchmoney/).

Now: [IRS W-2 data](https://www.irs.gov/statistics/soi-tax-stats-individual-information-return-form-w2-statistics) breaks wages down by age. The Under 26 bracket is the finest granularity the IRS provides — the sub-26 age splits below are **model-based estimates** (BLS employed counts × median weekly earnings, scaled to the IRS total), not hard IRS numbers. If you walk up from age 16 and accumulate total wages earned by everyone at or below each age, you cross the ~$34B mark around **age 18**.

| Age | Annual wage mass | Cumulative | Source |
|---|---|---|---|
| Under 26 (total) | $470B | $470B | IRS W-2 TY2020 [verified] |
| 16 | ~$9B | ~$9B | estimated (BLS weights) |
| 17 | ~$9B | ~$18B | estimated |
| 18 | ~$16B | ~$34B | estimated |
| 19 | ~$16B | ~$50B | estimated |
| 20-24 | ~$154B | ~$205B | estimated |
| 25 | ~$56B | ~$261B | estimated |
| 26-34 | $1.42T | $1.89T | IRS W-2 TY2020 [verified] |
| 35-44 | $1.95T | $3.84T | IRS W-2 TY2020 [verified] |
| 45-54 | $2.00T | $5.84T | IRS W-2 TY2020 [verified] |
| 55+ | $2.09T | $7.93T | IRS W-2 TY2020 [verified] |

So: using the ARR figure, **AI labs earn roughly what American 18-year-olds and younger earn in a year.** Using actual booked revenue (~$16-17B), the crossover is closer to **age 17**. Either way: LLMs just graduated high school.

# Is there a trend?

This is where it gets interesting. If you track AI lab revenue year-over-year and map it to the "equivalent age," you get a sense of how fast AI is economically maturing. Using **actual revenue** (not ARR) where possible:

| Year | OpenAI | Anthropic | Top 2 total | ~Econ. age | Sources |
|---|---|---|---|---|---|
| 2020 | ~$3.5M | — | ~$3.5M | newborn | [Getlatka](https://getlatka.com/companies/open-ai) |
| 2021 | ~$28M | — | ~$28M | infant | [Getlatka](https://getlatka.com/companies/open-ai) |
| 2022 | ~$200M | ~$10M | ~$210M | toddler | [Getlatka](https://getlatka.com/companies/open-ai); [Summit Ventures](https://www.summit-ventures.net/company/anthropic/) |
| 2023 | ~$1.6-2B | ~$100M | ~$1.7-2.1B | **~15-16** | [Epoch AI](https://epoch.ai/data-insights/openai-revenue); analyst estimates |
| 2024 | ~$3.7B | ~$0.5-1B | ~$4.2-4.7B | **~16** | [NYT/The Information](https://epoch.ai/data-insights/openai-revenue); [Anthropic Series F](https://www.anthropic.com/news/anthropic-raises-series-f-at-usd183b-post-money-valuation) |
| 2025 | ~$10-12B | ~$4-5B (est.) | ~$14-17B | **~17** | [SaaStr](https://www.saastr.com/openai-crosses-12-billion-arr-the-3-year-sprint-that-redefined-whats-possible-in-scaling-software/); [CNBC via Acquinox](https://acquinox.capital/blog/anthropic-investor-insights) |
| 2026 (ARR) | ~$20B | ~$14B | ~$34B | **~18** | [PYMNTS](https://www.pymnts.com/artificial-intelligence-2/2026/openais-annual-recurring-revenue-tripled-to-20-billion-in-2025/); [Sacra](https://sacra.com/c/anthropic/) |

Note: 2020-2022 figures are rough estimates from analyst databases [low confidence]. 2023-2025 are from credible reporting [medium-high confidence]. The 2026 row is ARR, not booked revenue [verified as ARR, but ARR ≠ revenue]. Anthropic actual 2025 revenue is especially hard to pin down — they grew from $87M ARR in Jan 2024 to $14B ARR in Feb 2026 ([Anthropic press releases](https://www.anthropic.com/news/anthropic-expands-global-leadership-in-enterprise-ai-naming-chris-ciauri-as-managing-director-of)), which means intra-year revenue lags the year-end ARR significantly.

Also note: this excludes Google (Gemini), Meta (Llama), xAI (Grok), etc. whose AI revenue isn't separately reported. The "real" total is higher but hard to quantify.

The economic age is ticking up fast. Something like 2-3 "economic years" per calendar year at current growth rates—though growth will slow at some point (or will it?). Per [Epoch AI](https://epoch.ai/data-insights/anthropic-openai-revenue), Anthropic has been growing at ~10×/year since hitting $1B, and OpenAI at ~3.4×/year.

- *At this growth rate, when does AI "turn 26" ($261B)? "Turn 35" (~$1.9T)?*

# Is this a useful frame?

**Arguments for:**

- It's concrete and intuitive. People understand what an 18-year-old earns. It sidesteps the whole [[agi terms]] mess.
- It captures something real about economic impact that benchmarks miss. As Dwarkesh points out, if models were so smart, they'd be earning more. Revenue is a revealed-preference measure of capability.
- It connects to [[The Roads Get Paved]]—the economic age will increase not just because models get smarter, but because companies restructure work to fit what models can do.

**Arguments against:**

- Revenue != value-add. AI is massively underpriced relative to the value it creates (just as a 16-year-old's wage underestimates the value of their labor). Labs are in growth mode, burning cash, pricing below cost. Revenue is a lower bound on economic value, not an accurate measure.
- The comparison is between *all* humans in an age bracket (millions of people) vs. *a few companies*. Revenue per "AI worker-equivalent" might tell a different story.
- W-2 wages miss self-employment income, and AI revenue is a different category of thing than wages. We're comparing gross revenue to compensation. The units don't actually match that cleanly.
- Most importantly: this frame doesn't help you make better predictions or decisions. Knowing AI "is 18" doesn't tell you when it'll be 25. The growth curve is the interesting thing, and you can just look at the growth curve directly.

Honestly, I think the Dwarkesh quote is compelling as a *vibe check*—a reminder that economically, AI is still tiny relative to human labor—but the "economic age" frame probably doesn't carry much analytical weight beyond that. The village idiot comparison works precisely because it's loose. Trying to make it precise might just reveal that it's more cute than useful.

That said, the one chart I'd love to see—AI revenue mapped to "economic age" over time, with projections—might be worth making just to see if the trendline is interesting. If AI is "aging" 2-3 economic years per calendar year and accelerating, that's a powerful visual even if the underlying comparison is imperfect. And the frame does get at something the [[AI progress]] discussion often misses: benchmarks go up, demos get better, but *the economy hasn't noticed yet*, not really. $34B is a rounding error on the $58T global wage bill.

See also: [[profit]] on counterfactual impact and whether AI lab revenue reflects genuine value creation vs. hype-driven investment.

--- 

# Sources & verification status

**Verified (hard numbers from primary sources):**

- IRS W-2 wage totals by age bracket (TY2020): [IRS SOI](https://www.irs.gov/statistics/soi-tax-stats-individual-information-return-form-w2-statistics)
- ILO global labor share (~52.4%): [ILO paper](https://www.ilo.org/media/408221/download)
- OpenAI ARR milestones ($12B ARR Jul 2025, $20B ARR end 2025): [SaaStr](https://www.saastr.com/openai-crosses-12-billion-arr-the-3-year-sprint-that-redefined-whats-possible-in-scaling-software/), [PYMNTS](https://www.pymnts.com/artificial-intelligence-2/2026/openais-annual-recurring-revenue-tripled-to-20-billion-in-2025/)
- Anthropic ARR trajectory ($87M Jan '24 → $14B Feb '26): [Anthropic press releases](https://www.anthropic.com/news/anthropic-expands-global-leadership-in-enterprise-ai-naming-chris-ciauri-as-managing-director-of), [Sacra](https://sacra.com/c/anthropic/)
- BLS weekly earnings by age: [BLS 2025 annual averages](https://www.bls.gov/news.release/wkyeng.nr0.htm) (note: Oct 2025 CPS missing due to govt shutdown)
- Epoch AI revenue comparison (OAI 3.4×/yr, Anthropic 10×/yr): [Epoch AI](https://epoch.ai/data-insights/anthropic-openai-revenue)

**Estimated (model-based or analyst figures, treat with caution):**

- Sub-26 age splits (the $9B/$16B per-year-of-age figures) — derived from BLS employed counts × median earnings, scaled to IRS total. Not from IRS directly.
- OpenAI revenue 2020-2022 (~$3.5M, ~$28M, ~$200M) — from [Getlatka](https://getlatka.com/companies/open-ai), an analyst database, not audited financials.
- Anthropic actual booked revenue for any year — only ARR milestones are publicly disclosed; actual annual revenue is inferred.
- The "economic age" mapping itself — depends on the estimated sub-26 splits.

**Key uncertainty:** the sub-26 age breakdown is the shakiest part of this analysis. The IRS only reports "Under 26" as one bucket ($470B total). The per-age splits that produce the "age 18 crossover" are estimates. The crossover could plausibly be anywhere from age 17 to 19 depending on methodology.

# Further reading

Epoch AI's best aggregated revenue dataset: [CSV](https://epoch.ai/data/ai_companies_revenue_reports.csv)

Broader gen-AI market size estimates range from $13-26B (2023) to $37-71B (2024-2025) depending on the research firm and what they include — [Grand View Research](https://www.grandviewresearch.com/industry-analysis/generative-ai-market-report), [MarketsandMarkets](https://www.marketsandmarkets.com/Market-Reports/generative-ai-market-142870584.html). These are much larger than "top labs only" because they include enterprise software, services, consulting, etc.

On ARR vs. real revenue: [Ed Zitron](https://www.wheresyoured.at/howmuchmoney/) on how ARR is "one of the most regularly-abused statistics in the startup world"