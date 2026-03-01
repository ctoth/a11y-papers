# Thirty Something (Million): Should They Be Exceptions?

**Authors:** Gregg C. Vanderheiden
**Year:** 1990
**Venue:** Human Factors, Vol. 32, No. 4, pp. 383–396
**DOI/URL:** https://pubmed.ncbi.nlm.nih.gov/2150062/ (PMID: 2150062); HTML full text: https://park.org/Guests/Trace/pavilion/30_some.htm
**Institution:** Trace Research and Development Center, Waisman Center and Department of Industrial Engineering, University of Wisconsin-Madison

## One-Sentence Summary
The foundational argument (pre-ADA, 1990) that 30+ million Americans with disabilities represent 12–20% of the population and must be incorporated into mainstream human factors design rather than treated as edge cases handled by special-purpose products.

## Problem Addressed
The human factors field in 1990 was designing for "the 95th percentile" on individual dimensions (height, vision, hearing) while implicitly assuming this covered nearly everyone. Vanderheiden shows this is mathematically false — designing to the 95th percentile on each of N independent dimensions leaves far fewer than 95% of real users able to use a product. Simultaneously, the field was treating disability/aging as a niche specialty rather than a mainstream concern, despite the population size.

## Key Contributions
- **The 95th Percentile Illusion**: Formal argument that meeting the 95th percentile on each of N ability dimensions does not mean 95% of the population can use the product. With 5 independent dimensions each excluding 10%, a product excludes ~40% of users. (Cited Kroemer 1987 noting that 95th percentile datasets often excluded people with disabilities entirely.)
- **Population sizing**: ~30 million Americans (12–20% of population) have disabilities or functional limitations; 45% of those who survive to age 65 have functional limitations; 72.5% of those who survive to age 75+. Disability is not rare — it is the expected late-life experience.
- **Impairment vs. functional limitation distinction**: Impairment = individual's capability deficit; functional limitation = interaction between impairment and design. Better design reduces functional limitation even without changing impairment.
- **TABs framing**: Disabled community calls non-disabled people "Temporarily Able-Bodied" — reframes disability as a universal life-course phenomenon, not a permanent minority characteristic.
- **Economic case for mainstream inclusion**: Accessible design is usually zero-marginal-cost (Apple Sticky Keys = 4KB; Mouse Keys = 4KB; CloseView = 20KB, all shipped standard). Special-market products are economically infeasible at the sub-5% market sizes involved.
- **Curb-cut effect (named implicitly)**: For every wheelchair user at a curb cut, 10–100 bicycles, skateboards, shopping carts, and carriages also use it. Accessible design benefits everyone.
- **Cost-reduction through accessible design**: Elevator advance-signal reprogramming (software-only) solved wheelchair boarding without adding elevators, and also sped normal boarding — reducing elevator fleet cost.
- **Disability transfer payment burden**: US disability expenditures rose from $50B (1975) to $170B (1986) linearly; projected >$200B in 1990. Economic loss from disability (excluding transfers) estimated at $177B in 1980 (~$290B in 1990 dollars). ~2 million unemployed disabled workers = $30B lost productivity annually.

## Methodology
Policy/advocacy paper with demographic analysis. No original empirical data — synthesizes NHIS (National Health Interview Survey) 1979, 1983–85 data; Kraus & Stoddard 1989 chartbook; Berkowitz & Greene 1989 disability expenditures; and concrete product case studies (Apple accessibility features, elevator design, curb cuts, Palentype system).

## Key Equations / Quantitative Arguments

The 95th Percentile Illusion (informal):

If 10% of population is excluded on each of 5 independent ability dimensions, and exclusions are independent across persons, then usable population ≈ 0.9^5 ≈ 59% — i.e., the product is usable by only ~59% despite "meeting the 90th percentile" on each dimension individually.

(Vanderheiden uses a simpler illustration: 10 people, 10% excluded on each of 5 dimensions = different people each time = only 5 can use it.)

## Parameters / Data Points

| Statistic | Value | Source |
|-----------|-------|--------|
| US population with disabilities or functional limitations | >30 million, 12–20% of population | Kraus & Stoddard 1989 |
| Functional limitation prevalence at age 65+ | 45% | US statistics cited |
| Functional limitation prevalence at age 75+ | 72.5% | US statistics cited |
| US population over 55 (projected 2050) | 35% | OTA 1985 |
| Multiple impairments among speech-impaired | 75% | NHIS 1983–85 via LaPlante 1988 |
| Multiple impairments among blind | 73% | NHIS 1983–85 via LaPlante 1988 |
| Multiple impairments among completely paralyzed | 71.4% | NHIS 1983–85 via LaPlante 1988 |
| Multiple impairments among deaf (both ears) | 55.4% | NHIS 1983–85 via LaPlante 1988 |
| Disability expenditures 1975 | $50 billion | Berkowitz & Greene 1989 |
| Disability expenditures 1986 | $170 billion | Berkowitz & Greene 1989 |
| Disability expenditures projected 1990 | >$200 billion | Extrapolated |
| Economic losses (ex transfers) 1980 | >$177B ($290B in 1990 $) | Chirikos 1989 |
| Unemployed disabled who want to work | ~2 million (1/3 of those who can work) | Kraus & Stoddard 1989 |
| Lost productivity from disabled unemployment | ~$30B/year | Vanderheiden calculation |
| Apple Sticky Keys disk space | 4 KB | Apple case study |
| Apple Mouse Keys disk space | 4 KB | Apple case study |
| Apple CloseView disk space | 20 KB | Apple case study |
| Bicycle/cart ratio at curb cuts vs. wheelchair users | 10:1 to 100:1 | Cited (no specific source given) |

## Implementation Details / Design Principles

**From this paper (prescriptive):**
1. Design for ability distributions, not ability thresholds. Ability is continuous, not bimodal.
2. Do not assume "95th percentile on each dimension" covers the population. Independence of dimensions means compound exclusion is multiplicative.
3. Distinguish impairment (person-side) from functional limitation (design-side). Only functional limitation is addressable by design.
4. Prioritize zero-cost accessibility features in software/firmware. Cost objection is usually unfounded.
5. When special-market products are needed, acknowledge they cannot be economically sustained below ~5% market size — this is an argument FOR mainstream inclusion.
6. Evaluate accessible design for co-benefits to non-disabled users (curb-cut effect). These benefits strengthen the business case.

**Concrete examples given:**
- Apple Sticky Keys: sequential key-press instead of simultaneous; activated by 5 taps on shift; deactivates on simultaneous press; transparent to normal users.
- Apple Mouse Keys: numeric keypad controls cursor; one-pixel nudge capability usable by sighted users for precision.
- Apple CloseView: 16x screen magnification; no external hardware needed.
- Elevator advance signal: software-only reprogramming; signals correct elevator before arrival; benefits all users by allowing pre-positioning.

## Figures of Interest
- **Table 1**: Prevalence of selected impairments in US all ages vs. over 65. Shows data sums to 121% (all ages) and 236% (65+) — demonstrating overlap in disability statistics and why simple addition is invalid.
- **Figure 1** (referenced, not reproduced in HTML): Non-duplicative breakdown of NHIS 1979 impairment data.
- **Figure 2** (referenced): Disability profile for younger people — learning disabilities dominate over "classic" disabilities (deafness, blindness).
- **Figure 3** (referenced): Disability profile for older people — visual and hearing impairments dominate.
- **Figure 4** (referenced): Functional limitation rates by age, including the 45% at 65 and 72.5% at 75+ statistics.
- **Figure 5** (referenced): Forecast of US population over 55 through 2050.
- **Figure 6** (referenced): US disability expenditure trend 1975–1990.

## Limitations
- No original empirical data; all statistics synthesized from secondary sources (1979–1989).
- The 95th percentile illusion illustration uses an oversimplified 10-person example with independence assumption; real-world disability correlates are complex (acknowledged briefly).
- "Costs" section is brief and largely defers the hard questions (curriculum expansion, knowledge base development) without quantifying them.
- Paper predates Web/digital interfaces — examples focus on hardware products and operating systems.

## Testable Properties
- **Monotonic**: As the number of independent ability dimensions in a product's design increases, the percentage of the population that can use the product decreases (compound exclusion).
- **Bound**: If each ability dimension excludes p% of the population independently, and there are N such dimensions, usable population upper bound ≈ (1-p)^N.
- **Empirical bound**: At age 75+, functional limitation prevalence ≥ 72.5% (from cited US data).
- **Economic invariant**: Zero-marginal-cost accessibility (software feature added to existing OS) should have ROI dominated by market expansion, not development cost.

## Relevance to Project
This is the historical origin paper for the "universal design beats special-case design" argument that underpins nearly every paper in this collection. The TABs framing, the 95th percentile critique, the economic feasibility argument, and the curb-cut effect are all foundational concepts that later papers (Wobbrock_2011_AbilityBasedDesign, Mack_2021_AccessibilityResearchSurvey, Gartland_2022_WebAccessibilityCognitive) assume without restating. It establishes the population-scale framing (12–20% of US population) that motivates the entire field.

## Open Questions
- [ ] The figures (1–6) referenced in the HTML are not rendered — demographic breakdowns by disability type may be worth locating from original journal.
- [ ] The paper was written just as the ADA was being passed (1990) — a follow-up question: which of Vanderheiden's predictions about mainstream product accessibility came true?
- [ ] The 95th percentile illusion calculation assumes independence across ability dimensions; a follow-up paper examining correlated disabilities (e.g., aging causing correlated visual + hearing + motor declines) would affect the math.

## Collection Cross-References

### Already in Collection
- **Wobbrock_2011_AbilityBasedDesign** — directly extends this paper's framework; ability-based design formalizes Vanderheiden's "design for ability distributions, not thresholds" into 7 explicit principles. Vanderheiden 1990 is the implicit precursor.
- **Mack_2021_AccessibilityResearchSurvey** — maps 26 years of CHI/ASSETS papers; the underrepresentation Vanderheiden diagnosed in 1990 ("only a small percentage of Human Factors Journal papers deal with disability") is the baseline Mack et al. measure change against.
- **Yuan_2011_GameAccessibilitySurvey** — uses 2002 Census data (~32.2 million Americans affected by game-inaccessibility) which is the same population-scale framing as Vanderheiden 1990; provides the game-specific update to the 30-million argument.
- **Gartland_2022_WebAccessibilityCognitive** — the field's current inability to include PwCDs in design is the exact problem Vanderheiden identifies (lack of awareness, lack of skills in the designer community) applied to Web/cognitive domain.

### New Leads (Not Yet in Collection)
- **Newell & Cairns (1987)** — "Human interface studies and the handicapped" — cited multiple times for the curb-cut/co-benefit argument; foundational for the "design for disability benefits everyone" framing.
- **Kroemer (1987)** — "Engineering anthropometry" in Salvendy Handbook of Human Factors — the source for the claim that 95th percentile datasets exclude people with disabilities; important methodological critique.
- **Kraus & Stoddard (1989)** — "Chartbook on disability in the United States" — the primary statistical source for the 30-million figure and unemployment statistics.
- **LaPlante (1988)** — "Data on disability from the NHIS 1983–85" — source for the multiple-impairment co-occurrence statistics.
- **Chirikos (1989)** — "Aggregate economic losses from disability in the United States" — source for the $177B economic loss figure.

### Supersedes or Recontextualizes
- **Wobbrock_2011_AbilityBasedDesign** — Vanderheiden 1990 is a direct predecessor to ability-based design. Wobbrock formalizes what Vanderheiden argues informally. Backward annotation warranted.
