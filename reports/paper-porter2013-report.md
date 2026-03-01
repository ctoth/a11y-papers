# Paper Processing Report: Porter_2013_GameAccessibilityBarriers

## Status: Complete

## Paper
**Title:** An Empirical Study of Issues and Barriers to Mainstream Video Game Accessibility
**Authors:** John R. Porter, Julie A. Kientz
**Year:** 2013
**Venue:** ASSETS 2013 (ACM SIGACCESS)
**DOI:** 10.1145/2513383.2513444

## Retrieval
- **Source:** Direct public URL — UW faculty page (https://faculty.washington.edu/jkientz/papers/Porter-GameAccessibility-ASSETS2013.pdf)
- **Method:** curl direct download (no sci-hub needed)
- **File:** papers/Porter_2013_GameAccessibilityBarriers/paper.pdf
- **Size:** 406KB, 8 pages, PDF 1.5

## Reading
- **Path:** Step 2A (direct PDF read — 8 pages, well under 25-page threshold)
- **Success:** Yes — all 8 pages read cleanly

## Files Created
- `papers/Porter_2013_GameAccessibilityBarriers/notes.md` — full implementation notes (13KB)
- `papers/Porter_2013_GameAccessibilityBarriers/description.md` — three-sentence summary
- `papers/Porter_2013_GameAccessibilityBarriers/abstract.md` — verbatim abstract + interpretation
- `papers/Porter_2013_GameAccessibilityBarriers/citations.md` — all 28 references + 5 key follow-ups

## Index Updated
- `papers/CLAUDE.md` — Porter entry appended

## Cross-References
- **Already in collection (1):** Yuan_2011_GameAccessibilitySurvey — Porter is the empirical complement; backward annotation added to Yuan's notes.md
- **New leads (4):**
  - Bigham, Ladner, Borodin (2011) — human-powered access technology (ASSETS '11)
  - Trewin et al. (2009) — visual/motor accessibility in virtual worlds (TACCESS)
  - Miesenberger et al. (2008) — game accessibility and social participation
  - Bierre et al. (2004) — IGDA GA SIG foundational guidelines white paper

## Key Findings (for collection use)
1. **Dominant barrier:** Assistive technology incompatibility — games fail to work with the ATs disabled gamers depend on (screen readers, custom input programs, modified controllers). Not absent subtitles or colorblind modes, which have achieved reasonable cultural adoption.
2. **Multiplayer exclusion:** Motor-impaired gamers report being pushed out of multiplayer by inability to compete ("keep up"); also by social stigma from movement artifacts and communication differences.
3. **Social workaround:** Many disabled gamers recruit able-bodied help for inaccessible barriers — framed as a human-powered AT design space.
4. **Industry finding — low-hanging fruit first:** Simple accessibility features (colorblind palette, subtitles) get implemented; complex motor impairment solutions (high within-population variance) do not.
5. **Industry finding — middleware is the structural lever:** AT integration requires OS-level hooks that individual studios cannot build from scratch. Game engines (Unreal, Unity) are the right intervention target.
6. **Industry finding — top-down pressure required:** Accessibility only happens with executive/stakeholder priority or legislative mandate; developer awareness alone is insufficient.

## Usefulness to This Project
**Rating: High**

**What it provides:**
- Empirical gamer-side barrier data that complements Yuan_2011's theoretical taxonomy — together they form a complete picture of game accessibility
- The AT incompatibility finding directly extends the web-side AT/application conflict documented in Lazar_2007_ScreenReaderFrustration into the games domain
- The middleware structural argument is the most actionable finding: it explains *why* guidelines are not adopted (cost of per-game reimplementation) and points to *where* to intervene (engine-level)

**Actionable next steps:**
- Investigate current state of Unity/Unreal Engine accessibility APIs (this paper is from 2013 — significant engine-level accessibility work has occurred since)
- Retrieve Bigham et al. 2011 (human-powered AT) as a complement to the social assistance workaround theme
- Consider whether the multiplayer exclusion finding has been revisited empirically post-2020 (co-pilot modes, Xbox Adaptive Controller)

**Skip if:**
- The research focus is web-only and does not intersect games, game-like interfaces, or interactive media accessibility
