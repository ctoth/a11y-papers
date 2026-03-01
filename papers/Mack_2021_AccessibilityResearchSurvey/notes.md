# What Do We Mean by "Accessibility Research"? A Literature Survey of Accessibility Papers in CHI and ASSETS from 1994 to 2019

**Authors:** Kelly Mack, Emma McDonnell, Dhruv Jain, Lucy Lu Wang, Jon E. Froehlich, Leah Findlater
**Year:** 2021
**Venue:** CHI 2021 (Proceedings of the 2021 CHI Conference on Human Factors in Computing Systems)
**DOI/URL:** https://doi.org/10.1145/3411764.3445412 | arxiv: 2101.04271

## One-Sentence Summary
The first comprehensive literature survey of accessibility research at CHI and ASSETS (1994-2019), analyzing 836 papers to characterize who the field studies, what methods it uses, how it has evolved, and where gaps remain.

## Problem Addressed
Despite decades of growing accessibility research, no broad literature review existed to characterize the field's trends, gaps, and methodological norms — making it hard to identify underserved communities, overrepresented topics, or problematic research practices.

## Key Contributions
- A qualitative codebook (10 categories, 52 subcodes) applied to 506 papers from 2010-2019, capturing community of focus, study methods, participant groups, contribution types, and more
- A quantitative 26-year temporal analysis of 836 papers using keyword frequencies and paper counts
- Identification of disproportionate attention: 43.5% of papers focus on blind/low-vision (BLV) users, with precipitous drop to motor (14.2%), DHH (11.3%), cognitive (9.1%), and others
- An open-source dataset of 506 coded papers + metadata for 836 papers (github.com/makeabilitylab/accessibility-literature-survey)
- Reflections and recommendations for future accessibility research

## Methodology
Two-phase approach:
1. **Qualitative coding** (2010-2019, N=506): Three coders iteratively developed a codebook with 10 categories. IRR via Krippendorff's alpha averaged 0.76 (SD=0.09) across subcodes. Papers identified via keyword search in ACM DL (accessibility, disability, disabled, impairment, impaired, assistive technology).
2. **Quantitative keyword analysis** (1994-2019, N=836): Programmatic analysis of paper counts, author keywords (N=511 unique appearing 2+ times), and temporal trends across 5-year bins.

Dataset creation: All ASSETS papers included by default. CHI papers filtered by accessibility-related keywords in title, abstract, or author keywords. False positive check via independent dual coding. False negative check on random sample of 100 non-candidate CHI papers (only 1 arguably missed).

## Key Equations
N/A — this is a survey paper, not a methods paper.

## Parameters

| Name | Value | Notes |
|------|-------|-------|
| Total papers analyzed | 836 | 260 CHI + 576 ASSETS, 1994-2019 |
| Qualitatively coded papers | 506 | 215 CHI + 291 ASSETS, 2010-2019 |
| Codebook categories | 10 | With 52 total subcodes |
| Mean IRR (Krippendorff's alpha) | 0.76 (SD=0.09) | Excluding "other" subcodes; range 0.63-0.91 |
| Median disabled participants per paper | 13 | IQR=13.0, M=62.0, SD=478.8 |
| Median total participants per paper | 18 | IQR=29.0, M=830.1, SD=16,140.3 |
| Papers with user studies | 477/506 | 94.3% |
| Papers with multiple study methods | 269/506 | 56.4% (of user-study papers) |

## Implementation Details
N/A — survey paper. Key data structures are the codebook (Table 1) and the open dataset.

## Figures of Interest
- **Fig 1 (page 15):** Growth of accessibility papers over time — papers/year at CHI+ASSETS grew from 22 (1994) to 95 (2019). CHI accessibility papers reached 7.8% of all CHI papers by 2019.
- **Table 1 (page 8):** Complete codebook with 10 categories, subcodes, and IRR values.
- **Table 2 (page 9):** Frequency table for community of focus, issues addressed, and contribution type.
- **Table 3 (page 11):** Study method, study location, and participant group frequencies.
- **Table 5 (page 16):** Top 12 keyword groups for communities, technologies, and methods over 26 years with sparkline trends.

## Results Summary

### Communities of Focus (2010-2019)
| Community | Papers | % |
|-----------|--------|---|
| BLV (blind/low-vision) | 220 | 43.5% |
| Motor/Physical | 72 | 14.2% |
| DHH (deaf/hard-of-hearing) | 57 | 11.3% |
| Cognitive impairment | 46 | 9.1% |
| Older adults | 45 | 8.9% |
| Autism | 31 | 6.1% |
| IDD | 14 | 2.8% |
| General disability | 46 | 9.1% |

### Issues Addressed
- Digital access (36.8%) — most common overall
- Understanding users (27.5%)
- Physical access (20.8%)
- Independence (18.4%)
- Communication (16.0%) — dominant for DHH (64.9% of DHH papers)
- Behavior change (7.7%) — common for autism

### Study Methods (of 477 user-study papers)
- Interviews: 42.1%
- Usability testing: 41.7%
- Controlled experiments: 34.6%
- Surveys: 25.6%
- Workshop/design sessions: 18.4%

### Contribution Types
- Empirical: 60.3%
- Artifact: 55.5%
- Theoretical: 8.7%
- Methodological: 3.2%
- Dataset: 1.4%
- Survey: 0.6%

### Temporal Trends (26-year)
- BLV dominance is longstanding and consistent
- Motor/physical and DHH present since early years
- Autism/neurodiversity emerging from 2000-2004
- "Web" is all-time top technology keyword but declining
- "Mobile" grew substantially then plateaued in last 5 years
- New technology areas: games, wearables, AR/MR/VR, 3D printing, social computing

## Limitations
- Scoped to CHI and ASSETS only — norms may differ at TOCHI, TACCESS, W4A, and other venues
- Codebook reflects authors' positionality (team of white and Asian scholars, two identifying as disabled)
- Community boundaries are overlapping and ill-defined (e.g., stroke survivors may have cognitive + motor + physical issues)
- Keyword-based paper identification may miss relevant CHI papers that don't use accessibility terms in metadata
- Disability is culturally constructed — the categories concretized by the codebook are somewhat problematic

## Testable Properties
- BLV papers should represent >40% of accessibility papers in any 5-year window at CHI+ASSETS (historically stable)
- Papers with user studies should exceed 90% of total (94.3% in 2010-2019)
- Median disabled participant sample size should be in range [9, 28] depending on community
- Accessibility papers as % of CHI should be increasing over time (reached 7.8% by 2019)

## Relevance to Project
This is the foundational map of the accessibility research landscape. It identifies which disability communities receive the most and least attention, what methods are standard, and where gaps exist. Essential for understanding what our collection should prioritize and where original research is most needed.

## Open Questions
- [ ] Has the BLV dominance shifted post-2019 with growing interest in cognitive accessibility and neurodiversity?
- [ ] What does the picture look like when expanded beyond CHI/ASSETS to include W4A, TACCESS, TOCHI?
- [ ] The open dataset at github.com/makeabilitylab/accessibility-literature-survey — is it still maintained?
- [ ] How do industry accessibility practices compare to the academic trends identified here?

## Related Work Worth Reading
- Bhowmick & Hazarika [20] — high-level analysis of 3,010 visual accessibility papers
- Brulé et al. [28] — quantitative evaluation practices for visual impairment tech (178 papers)
- Spiel et al. [140] — critical discourse analysis of 185 autism technology papers
- Vines et al. [151] — 644 papers on aging across 16 HCI venues
- Mankoff et al. [99] — landmark paper calling for disability studies integration in accessibility research
- Trewin et al. [147] — usage of subjective scales in accessibility research

---

**See also:** Gartland_2022_WebAccessibilityCognitive — Cites Mack et al. [25] to contextualize the underrepresentation of PwCDs in CHI/ASSETS research; Gartland et al. use the finding that cognitive disabilities are among the least-studied populations to justify a dedicated systematic review on web accessibility for this group.
