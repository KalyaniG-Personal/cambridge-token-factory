# Cambridge Underground Token Factory

**The AI data center of 2035, 50 m under Cambridge, MA.** Built for Track 1 of the SundAI × MIT AI Hackathon: design the most cost-effective energy-to-token conversion factory.

- **Live demo:** `index.html` (fleet planner and plant digital twin)
- **Bonus:** `demo/cool-chiplets.html` (Track 2 chiplet thermal optimizer)

Both are single self-contained HTML files. Open them in any browser; there's no build step and no server.

## The idea

1. **Cool with the ground.** Bedrock at 50 m stays near 12 °C all year. Liquid cooling (single-phase immersion in bio-based oil, or water direct-to-chip) dumps heat into a closed ground loop: no chillers, no cooling towers, no PFAS fluids.
2. **Sell the heat.** Heat pumps lift waste heat into Cambridge district heating, about 31 MW of heat per 100 MW of IT.
3. **Clean power, matched hourly.** Offshore wind, storage and firm clean power, plus an 800 V DC bus that cuts conversion losses from ~11% to ~3%.
4. **Efficient serving.** FP4 weights, speculative decoding, disaggregated prefill and decode racks, and a pooled context-memory tier.

## Results (from the demo)

| Metric | 2025-style baseline | This design |
| --- | --- | --- |
| Net energy per output token (plant twin mix) | 0.298 J | 0.069 J |
| PUE | ~1.28 | ~1.08 |
| Water per prompt | 0.49 mL | 0.009 mL |
| CO₂ per 100 MW plant per year (95% hourly clean power) | ~136 kt | ~19 kt |

**Against the challenge** ($30B over 5 years, 500 MW of Earth grid, up to 6 sites), at published 2025–26 usage per user:

- **Users:** all three cases served, 4.45B users (4B prompters, 50M agent developers, 400M knowledge workers)
- **Fleet:** about 193 MW of facility power and $6.8B over 5 years, on 2 sites of ~120 MW
- **Headroom:** per-user usage can grow 2.6× before the 500 MW cap binds

## What's in the twin

- **Fleet planner:** sizes decode GPUs (from the organizers' memory-bandwidth figures: 960 chat or 117 agent users per GPU), prefill GPUs, context memory, power, sites and 5-year cost. It also has an optional low-Earth-orbit overflow at $200/kg.
- **Plant twin:** an 8,760-hour simulation of Cambridge weather and bedrock covering free cooling, chillers, chip leakage versus coolant temperature, heat reuse, power conversion, clean-power matching, CO₂ and water. An optimizer searches about 1,000 designs.

## Data sources for usage per user

- **Prompters:** OpenAI/NBER reported 2.6B ChatGPT messages a day from 700M+ weekly users. https://www.computing.co.uk/news/2025/ai/openai-reveals-what-chatgpt-users-look-for
- **Response length:** https://arxiv.org/pdf/2506.08686
- **Agent developers:** Claude Code docs give about $13 per developer per active day. https://code.claude.com/docs/en/costs
- **Knowledge workers:** the St. Louis Fed found AI users spend ~43 min per workday with AI. https://www.stlouisfed.org/on-the-economy/2025/feb/impact-generative-ai-work-productivity
- **Token growth:** Google I/O 2026 reported 3.2 quadrillion tokens a month. https://blog.google/innovation-and-ai/sundar-pichai-io-2026/

## Environmental research used

- **Cooling life cycle:** Microsoft, Nature. https://news.microsoft.com/source/features/sustainability/microsoft-quantifies-environmental-impacts-of-datacenter-cooling-from-cradle-to-grave-in-new-nature-study/
- **AI water footprint:** Li et al. https://arxiv.org/html/2304.03271v5
- **24/7 clean energy:** Princeton ZERO Lab. https://www.canarymedia.com/articles/clean-energy/what-24-7-carbon-free-energy-can-achieve-over-the-long-term
- **PFAS and two-phase cooling:** https://www.hpcwire.com/2023/01/27/pfas-regulations-3m-exit-to-impact-two-phase-cooling-in-hpc/
- **Data center heat reuse (Meta Odense):** https://www.ramboll.com/projects/energy/meta-surplus-heat-to-district-heating

## Assumptions

2035 hardware prices and power, peak-to-average load, underground build cost ($13M/MW), electricity prices and orbital mass per kW are our estimates. Every one is editable in the demo. See the "Model and assumptions" sections in `index.html`.
