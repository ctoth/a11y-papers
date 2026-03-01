# Accessibility in video games: a systematic review

**Authors:** Juan Aguado-Delgado, José-María Gutiérrez-Martínez, José R. Hilera, Luis de-Marcos, Salvador Otón
**Year:** 2018 (published online August 10, 2018; journal volume 2020)
**Venue:** Universal Access in the Information Society, Vol. 19, pp. 169–193
**DOI/URL:** https://doi.org/10.1007/s10209-018-0628-2

## One-Sentence Summary

A systematic mapping study that reviews 45 papers on video game accessibility (2004–2014), characterizing the landscape by disability type, research approach, and solution category, and concluding that no existing initiative can guarantee universally accessible video games.

## Problem Addressed

Video games are a major cultural and economic product, but their developers routinely fail to consider players with disabilities. The paper's primary aim is to map the state of the literature — what research exists, which disability types are covered, what solutions have been proposed — and to identify research gaps that a future integral software engineering methodology should address.

## Key Contributions

- PRISMA-compliant systematic mapping study (SMS) of 45 primary studies on video game accessibility (screened from 2805 initial results)
- Disability taxonomy for the video games context: Visual, Auditory, Motor, Cognitive (with subcategories; Fig. 2)
- Three-phase interaction model (receive stimuli → determine response → provide input) mapping disability types to where they block game interaction
- Quantitative breakdown of the 45 studies by: type of research (Validation/Evaluation/Solution Proposal/Philosophical/Opinion/Experience), type of disability addressed, research questions answered, and publication year
- Six research questions (RQ1–RQ6) with evidence-based answers derived from the corpus
- Identification of gaps: RQ3 (methodology for universal accessibility) has zero studies answering it; auditory and cognitive disability research is underrepresented vs. motor and visual
- Appendix: Table 11 — full metadata for all 45 studies with DOI links, enabling direct follow-up retrieval

## Methodology

Systematic Mapping Study (SMS) — a broad-coverage variant of systematic literature review (SLR) focused on quantitative characterization rather than deep synthesis. Process followed EBSE guidelines [Kitchenham et al.] and PRISMA reporting standards.

Search sources (20 databases): Google Scholar, BUAH, ACM Digital Library, IEEE Xplore, SpringerLink, ScienceDirect, Web of Science, INSPEC, Scopus, ArXiv, and others.

Search expression: `(accessibility OR accessible) AND ("video game" OR "mobile game")` in both English and Spanish.

Execution: end of 2014 to end of 2015; searches covered publications 2004–2014. 2805 results → 320 after manual search extension → 45 studies included after full-text review.

## Research Questions and Answers

| RQ | Question | Answer |
|----|----------|--------|
| RQ1 | Are video games truly accessible today? | No — 29/45 studies address this; universal accessibility is not achieved |
| RQ2 | Have enough solutions been proposed to increase accessibility? | Yes, many proposed, but not enough adopted — 38/45 studies address this |
| RQ3 | Does a development methodology from adapted solutions have notable impact? | **No answer** — zero studies address this |
| RQ4 | Do developers appreciate prior accessibility proposals? | No — developers do not apply them (9/45 studies) |
| RQ5 | Is universal accessibility a realistic/achievable aim? | Difficult — generally not realistic given cost and ignorance (8/45 studies) |
| RQ6 | Do video games provide benefits beyond entertainment? | Yes — learning and rehabilitation (29/45 studies) |

## Key Findings

1. **No universally accessible video game exists.** Approaches involving particular custom interfaces may segregate disabled players. Frameworks depending on specific technologies limit developer options. Guidelines are widely ignored.

2. **Motor impairment is the most-studied disability type** (30 studies), followed by visual (27), then cognitive and auditory (both 20). Auditory and cognitive are underrepresented relative to their prevalence.

3. **Solution proposals dominate the literature** (17 studies), followed closely by evaluation research (18 studies). Only 5 validation studies exist — most proposed solutions are never independently validated.

4. **Research activity increased significantly** from an average of 1.57 works/year (2004–2010) to 8.5 works/year (2011–2014), indicating a maturing field.

5. **RQ3 has zero answers.** No existing study provides a software development methodology that systematically integrates accessibility throughout the video game development lifecycle.

6. **Conference papers dominate** (48.9% of selected works) over journals (44.5%), with Web (2.2%) and Reports (4.5%) being residual.

## Disability Taxonomy (Fig. 2)

```
Types of disability
├── Sensory disability
│   ├── Visual disability
│   │   ├── Blindness
│   │   ├── Low vision
│   │   ├── Color blindness
│   │   └── ...
│   └── Auditory disability
│       ├── Deafness
│       ├── Hearing loss
│       └── ...
├── Motor disability
│   ├── Paralysis
│   ├── Neurological disorders
│   ├── Repetitive stress injury
│   └── ...
└── Cognitive disability
    ├── Memory loss
    ├── Attention Deficit Disorder
    ├── Dyslexia
    └── ...
```

## Three-Phase Game Interaction Model

Derived from Yuan et al. (2011), this model locates where each disability type creates a barrier:

1. **Receive stimuli** (visual, auditory, or tactile) → blocked by sensory disabilities
2. **Determine response** → blocked by cognitive disabilities
3. **Provide input** through the relevant interface → blocked by motor disabilities

This model is cited as foundational for explaining why different disability types require fundamentally different solution strategies.

## Solution Categories Surveyed (from state-of-the-art review, Section 2.3)

### Hardware approaches
- **eyeCan**: gaze-gesture capture for game input [ref 32]
- **EPOC brain-computer interface (BCI)**: electroencephalograph + electromyograph + gyroscope; allows limited motor-skills players to control games [ref 41]
- **Kinect**: natural user interface (NUI) for body-gesture game access [ref 19, 46]

### Software approaches
- **Frameworks**: AGA framework [ref 35], FAAST [ref 46], GADF [ref 47], Exertion Framework [ref 39], KINECTWheels [ref 15, 17], RTSS [ref 38]
- **Guidelines**: Multiple publications provide accessibility guideline sets for game development [refs 4–6, 11, 13, 16, 23, 52]
- **High-level design methods**: Adaptation of Unified User Interface Design [ref 22]; assessment frameworks [refs 2, 20]
- **Accessible games**: Blind hero [ref 51], VI Bowling [ref 37], Terraformers [ref 49], TapBeats [ref 25]

## Key Study Identifiers (Most Valuable per Table 10)

Studies S10, S19, and S22 answer 5 research questions each (most comprehensive):
- **S10**: Game Accessibility: Enabling Everyone to Play (Garber 2013, Computer magazine)
- **S19**: S22: Porter & Kientz (2013) empirical study of issues/barriers in mainstream games; Gerling et al. motion-based games

Studies S01, S21, S32, and S35 answer 4 RQs and are also highly valuable.

## Parameters / Quantitative Results

| Metric | Value |
|--------|-------|
| Initial search results | 2805 (962 ES + 1843 EN) |
| After deduplication | 2472 |
| After full-text screening | 320 |
| Excluded after full-text review | 275 |
| Final included studies | 45 |
| Motor disability coverage | 30 studies |
| Visual disability coverage | 27 studies |
| Auditory disability coverage | 20 studies |
| Cognitive disability coverage | 20 studies |
| RQ1 coverage | 29 studies |
| RQ2 coverage | 38 studies |
| RQ6 coverage | 29 studies |
| Databases searched | 20 |
| Year range | 2004–2014 |
| Search execution period | end-2014 to end-2015 |

## Figures of Interest

- **Fig. 1 (page 1)**: PRISMA flow diagram — 2805 → 2472 → 320 → 45
- **Fig. 2 (page 2)**: Disability taxonomy tree (Sensory/Motor/Cognitive with subtypes)
- **Fig. 3 (page 5)**: Four-step review protocol flowchart
- **Fig. 4 (page 10)**: Full search process diagram
- **Fig. 5 (page 10)**: Collection/selection funnel
- **Fig. 6 (page 12)**: Bar chart — distribution by research type (Solution Proposal 17, Evaluation Research 18, Validation Research 5)
- **Fig. 7 (page 13)**: Distribution by research questions answered (RQ2: 38, RQ1 and RQ6: 29)
- **Fig. 8 (page 13)**: Distribution by disability type (Motor 30, Visual 27, Auditory/Cognitive 20)
- **Fig. 9 (page 14)**: Timeline of publications 2004–2014 by type
- **Fig. 10 (page 16)**: Bubble plot — research type facet vs research questions facet (systematic map visualization)
- **Table 11 (pages 17–22)**: Full appendix — all 45 studies with metadata and DOIs

## Limitations

1. **Multidisciplinary scope**: Studies crossing Computer Science and Medicine made data extraction inconsistent due to different reporting standards.
2. **Systematic Mapping Study breadth vs. depth**: The SMS approach provides broad coverage but less depth per study than a conventional SLR.
3. **Language restriction**: Only Spanish and English publications were included; non-English literature excluded.
4. **Temporal cutoff**: Covers only 2004–2014; the field has grown substantially since.
5. **No answer for RQ3**: No software engineering methodology for universally accessible game development was found; the authors propose future work on this.
6. **Cross-disciplinary noise**: Some excluded works used gaming terminology (violence, politics) rather than referring to video game software products.

## Testable Properties

- Any accessibility solution claiming "universal accessibility" for video games should be challenged: this review found zero such validated systems as of 2014.
- A game evaluation rubric covering all four disability categories (Visual, Auditory, Motor, Cognitive) is necessary for completeness — studies covering only motor impairment omit 20 studies' worth of other disability considerations.
- The three-phase interaction model predicts that accessibility barriers for sensory, cognitive, and motor disabilities are distinct and non-overlapping — a solution addressing motor input (Phase 3) does not address sensory output (Phase 1).
- Publication count per year should be monotonically increasing post-2010; any dataset showing decline would indicate field contraction.

## Relevance to Project

This paper is the 2018 systematic literature map of the same research territory covered by Yuan_2011_GameAccessibilitySurvey. Where Yuan (2011) provides a conceptual framework and strategy taxonomy, this paper provides a quantitative evidence base: which disability types are researched, which research questions have been answered, and what the field has not yet addressed. Together they form the dual foundation for game accessibility work in this collection — Yuan provides the "what" taxonomy, Aguado-Delgado provides the "what has been studied" landscape.

The paper also catalogs 45 primary studies (Table 11, Appendix) with DOIs, making it a direct retrieval guide for expanding this collection's game accessibility coverage.

## Open Questions

- [ ] How has the landscape changed since 2014? (Hassan 2024 review covers 2016–2020; should be retrieved)
- [ ] Which of the 45 studies in the appendix are highest-priority for collection inclusion?
- [ ] Does a software engineering methodology for universally accessible game development exist in the post-2014 literature (answer to RQ3)?
- [ ] What is the current state of the Game Accessibility Guidelines (gameaccessibilityguidelines.com), cited as ref [5] and one of the few practical guideline documents identified?

## Related Work Worth Reading

- **Yuan, Folmer, Harris (2011)**: "Game accessibility: a survey" — already in collection as Yuan_2011_GameAccessibilitySurvey. This paper's three-phase interaction model and disability strategy taxonomy are foundational to Aguado-Delgado's framework.
- **Barlet and Spohn (2012)**: "A practical guide to game accessibility" (The Ablegamers Foundation) [ref 4] — the practitioner's guideline document, cited repeatedly
- **Porter (2014)** [S01]: "Understanding and Addressing Real-world Accessibility Issues in Mainstream Video Games" (ACM SIGACCESS) — most comprehensive single study (4 RQs answered)
- **Gerling et al. (2012)** [S03, S26]: Motion-based game interaction for older adults (SIGCHI + CHI) — highest citation cluster in the corpus
- **Porter and Kientz (2013)** [S32]: "An Empirical Study of Issues and Barriers to Mainstream Video Game Accessibility" — empirical barrier study, answers 4 RQs

## Collection Cross-References

### Already in Collection
- **Yuan_2011_GameAccessibilitySurvey** — cited as reference [52] throughout; this paper's three-phase interaction model and disability taxonomy directly extend Yuan's work. Aguado-Delgado explicitly builds on Yuan's framework.

### New Leads (Not Yet in Collection)
- Barlet, M.C., Spohn, S.D. (2012) — "A practical guide to game accessibility" — The Ablegamers Foundation — key practitioner guideline document, cited as foundation for accessibility guideline research
- Porter, J.R., Kientz, J.A. (2013) — "An Empirical Study of Issues and Barriers to Mainstream Video Game Accessibility" — SIGACCESS 2013 — empirical barrier study covering 4 of 6 RQs [S32]
- Gerling, K.M. et al. (2012) — multiple papers on motion-based/full-body game interaction for older adults with motor impairments [S03, S26] — highly cited cluster
- Grammenos, D., Savidis, A., Stephanidis, C. (2007) — "Unified design of universally accessible games" — Int Conf Univers Access Hum Comput Interact — foundational unified design paper [S22]

### Supersedes or Recontextualizes
- **Yuan_2011_GameAccessibilitySurvey** — Aguado-Delgado (2018) extends and updates Yuan (2011). Yuan's survey is pre-systematic and covers up to 2009–2010 with narrative taxonomy; Aguado-Delgado provides a formal PRISMA-compliant map of 45 studies from 2004–2014. The two papers are complementary rather than one superseding the other.
