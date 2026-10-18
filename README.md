# Cambridge Underground Token Factory

**The AI data center of 2035, 50 m under Cambridge, MA.** Built for Track 1 of the SundAI × MIT AI Hackathon: design the most cost-effective energy-to-token conversion factory.

- **Live demo:** `index.html` (fleet planner and plant digital twin)
- **Bonus:** `demo/cool-chiplets.html` (Track 2 chiplet thermal optimizer)
- **Pitch:** `pitch/` has the 10-slide deck (speaker notes, sources on every slide) and the Word playbook with script, Q&A and challenges

The demos are single self-contained HTML files. Open them in any browser; there's no build step and no server.

## The idea

1. **Cool with river and aquifer water.** Liquid cooling (single-phase immersion in bio-based oil, or water direct-to-chip) dumps heat into Charles River water and an aquifer cold well. The bedrock and aquifer store summer heat for winter. There are no cooling towers and no PFAS fluids. Rock alone absorbs heat too slowly at this scale (~10 MW per 1,000 boreholes), so water is the main sink.
2. **Sell the heat.** Heat pumps lift waste heat into Cambridge district heating, about 31 MW of heat per 100 MW of IT.
3. **Clean power, matched hourly.** Offshore wind, storage and firm clean power, plus an 800 V DC bus that cuts conversion losses from ~11% to ~3%.
4. **Efficient serving.** FP4 weights, speculative decoding, disaggregated prefill and decode racks, and a pooled context-memory tier.

## Results (from the demo)

| Metric | 2025-style baseline | This design |
| --- | --- | --- |
| Net energy per output token (plant twin mix) | 0.298 J | 0.069 J |
| PUE | ~1.28 | ~1.09, and 1.09 in July |
| Water per prompt | 0.49 mL | 0.009 mL |
| CO₂ per 100 MW plant per year (95% hourly clean power) | ~136 kt | ~20 kt |

**Against the challenge** ($30B over 5 years, 500 MW of Earth grid, up to 6 sites), at published 2025–26 usage per user:

- **Users:** all three cases served, 4.45B users (4B prompters, 50M agent developers, 400M knowledge workers)
- **Fleet:** about 194 MW of facility power at summer peak and $6.8B over 5 years, on 2 sites of ~120 MW
- **Headroom:** per-user usage can grow 2.6× before the 500 MW cap binds

Usage per user comes from OpenAI/NBER [9], Claude Code docs [10] and the St. Louis Fed [11].

**Where the gain comes from:** the serving stack (FP4, speculative decoding, batching) and the 800 V DC power chain give 3.5×, and any data center could adopt them. The site (liquid cooling to river and aquifer water, cooler chips, heat sales) cuts the remaining energy by a further 20%.

## What's in the twin

- **Fleet planner:** sizes decode GPUs (from the organizers' memory-bandwidth figures: 960 chat or 117 agent users per GPU), prefill GPUs, context memory, power, sites and 5-year cost. It also has an optional low-Earth-orbit overflow at $200/kg.
- **Plant twin:** an 8,760-hour simulation of Cambridge weather, river water and bedrock. It covers free cooling, chillers, chip leakage versus coolant temperature, heat reuse, power conversion, clean-power matching, CO₂ and water. Each heat sink has a hard capacity: boreholes at ~50 W per metre, a river intake capped by a discharge permit, and an aquifer cold well. Overflow goes to surface dry coolers. An optimizer searches about 1,700 designs.

## Research backing

Each claim and the evidence behind it. Numbers match the deck and the playbook.

| Claim | Evidence | Type |
| --- | --- | --- |
| Liquid cooling gives the most reusable heat | Air cooling returns ~15–30 °C water; liquid cooling ~50–60 °C [1] | Journal review |
| Heat pumps lift data center heat for district heating | ORNL: heat pumps up to 120 °C on Frontier supercomputer heat, ~85% less CO₂ than gas boilers [2] | Journal |
| Aquifer storage beats chillers in summer | COP 16.5 vs 2.4 at summer peak; cooling cost $15 → $5 per MWh [3] | Journal (modelling) |
| Cooling, heat recovery and aquifers combine | Control study combining all three [5] | Journal |
| Liquid cooling lowers life-cycle impact | Emissions −15–21%, energy −15–20%, water −31–52% vs air [4] | Journal (Nature) |
| Clean electricity dominates lifetime emissions | Operation ~70–90% of an AI chip's lifetime emissions [7] | Preprint |
| 24/7 clean power cuts emissions further, at a cost | 39–64% premium over annual matching in California [13] | Report |

## Real-world examples

| Example | What it shows | Ref |
| --- | --- | --- |
| Iron Mountain, Pennsylvania | Data halls ~22 stories underground in a limestone mine, cooled with an underground lake | [16] |
| Lefdal Mine, Norway | Data center inside a former mine, cooled with fjord water, on hydropower | [17] |
| Meta Odense, Denmark | ~45 MW of heat pumps; waste heat to 12,000+ homes | [15] |
| Stockholm Data Parks, Sweden | Data center heat for ~2,500 apartments | [1] |
| Microsoft and Fortum, Espoo, Finland | Planned ~40% of the area's district heat | [18] |

No study or plant yet combines all of these at 100 MW under a city. The evidence supports each link, and the twin shows how they fit.

## References

[1] Yuan X., Liang Y., Hu X., Xu Y., Chen Y., Kosonen R. (2023). Waste heat recoveries in data centers: A review. Renewable and Sustainable Energy Reviews, 188, 113777. *(journal)* https://acris.aalto.fi/ws/portalfiles/portal/124210750/1_s2.0_S1364032123006342_main.pdf

[2] Wang P., Gao Z., Kowalski S.P., et al. (2024). District heating utilizing waste heat of a data center: High-temperature heat pumps. Energy and Buildings, 315, 114327. doi:10.1016/j.enbuild.2024.114327 *(journal)* https://ornl.gov/publication/district-heating-utilizing-waste-heat-data-center-high-temperature-heat-pumps

[3] Oh H., Sickinger D., Acero-Allard D. (2025). Techno-economic analysis of reservoir (aquifer) thermal energy storage for data center cooling. Applied Energy. Summary by the National Laboratory of the Rockies (formerly NREL). *(journal)* https://www.nrel.gov/grid/news/program/2025/nlr-analysis-identifies-reservoir-thermal-energy-storage-as-a-solution-for-data-center-cooling-needs

[4] Microsoft researchers (2025). Using life cycle assessment to drive innovation for sustainable cool clouds. Nature. Summary by Microsoft. *(journal)* https://news.microsoft.com/source/features/sustainability/microsoft-quantifies-environmental-impacts-of-datacenter-cooling-from-cradle-to-grave-in-new-nature-study/

[5] Hong Kong Polytechnic University and Technical University of Denmark authors (2026). Physics-guided deep reinforcement learning for optimized data center cooling and waste heat recovery utilizing aquifer thermal energy storage. Applied Energy. doi:10.1016/j.apenergy.2025.126984 *(journal)* https://www.nature.com/nature-index/article/10.1016/j.apenergy.2025.126984

[6] Li P., Yang J., Islam M.A., Ren S. Making AI Less “Thirsty”: Uncovering and Addressing the Secret Water Footprint of AI Models. arXiv:2304.03271. *(preprint)* https://arxiv.org/html/2304.03271v5

[7] Google researchers (2025). Life-Cycle Emissions of AI Hardware: A Cradle-To-Grave Approach and Generational Trends. arXiv:2502.01671. *(preprint)* https://arxiv.org/html/2502.01671v1

[8] Brevity is the soul of sustainability: Characterizing LLM response lengths (2025). arXiv:2506.08686. *(preprint)* https://arxiv.org/pdf/2506.08686

[9] OpenAI with D. Deming (2025). How People Use ChatGPT. NBER working paper; reported by Computing, 17 Sep 2025. *(report)* https://www.computing.co.uk/news/2025/ai/openai-reveals-what-chatgpt-users-look-for

[10] Anthropic. Claude Code documentation: Manage costs effectively (accessed Oct 2026). *(report)* https://code.claude.com/docs/en/costs

[11] Federal Reserve Bank of St. Louis (27 Feb 2025). The Impact of Generative AI on Work Productivity. On the Economy blog. *(report)* https://www.stlouisfed.org/on-the-economy/2025/feb/impact-generative-ai-work-productivity

[12] Google (19 May 2026). I/O 2026 keynote recap: over 3.2 quadrillion tokens processed per month. *(report)* https://blog.google/innovation-and-ai/sundar-pichai-io-2026/

[13] Princeton ZERO Lab (J. Jenkins et al.). System-level impacts of 24/7 carbon-free electricity procurement; summarized by Canary Media, Nov 2021. *(report)* https://www.canarymedia.com/articles/clean-energy/what-24-7-carbon-free-energy-can-achieve-over-the-long-term

[14] Duke University Nicholas Institute (2025). Rethinking Load Growth: flexible large loads; reported by POWER magazine. *(report)* https://www.powermag.com/duke-researchers-grid-flexibility-key-to-accommodate-load-growth

[15] Ramboll. Meta: surplus heat to district heating, Odense, Denmark. *(industry)* https://www.ramboll.com/projects/energy/meta-surplus-heat-to-district-heating

[16] Mearian L. Green IT: 22 stories underground, Iron Mountain’s experimental Room 48. Network World. *(industry)* https://www.networkworld.com/article/769469/green-it-22-stories-underground-iron-mountain-s-experimental-room-48.html

[17] DatacenterDynamics. Secrets of Norway’s green labyrinth (Lefdal Mine Datacenter). *(industry)* https://www.datacenterdynamics.com/en/opinions/secrets-of-norways-green-labyrinth/

[18] Eurelectric. Microsoft data centers to provide 40% of Fortum’s electricity-based district heating in Espoo, Finland. *(industry)* https://www.eurelectric.org/stories/microsoft-data-centers-provide-40-of-fortums-electricity-based-district-heating-in-espoo-finland/

[19] HPCwire (27 Jan 2023). PFAS regulations, 3M exit to impact two-phase cooling in HPC. *(industry)* https://www.hpcwire.com/2023/01/27/pfas-regulations-3m-exit-to-impact-two-phase-cooling-in-hpc/

## Assumptions

2035 hardware prices and power, peak-to-average load, underground build cost ($13M/MW), electricity prices, river and aquifer capacities, borehole heat rates and orbital mass per kW are our estimates. Every one is editable in the demo. See the "Model and assumptions" sections in `index.html`.
