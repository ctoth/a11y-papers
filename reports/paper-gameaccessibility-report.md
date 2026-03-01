# Paper Process Report: Game Accessibility Survey

**Date:** 2026-02-28
**Paper:** "Game accessibility: a survey"
**Authors:** Bei Yuan, Eelke Folmer, Frederick C. Harris Jr.
**Published:** Universal Access in the Information Society, Vol. 10, pp. 81–100, 2011 (online June 2010)
**DOI:** https://doi.org/10.1007/s10209-010-0189-5

---

## Retrieval

**Status:** SUCCESS

**Source:** sci-hub.su (DOI `10.1007/s10209-010-0189-5`)

**Notes:**
- sci-hub.st did not have this paper (2010 Springer article appears absent from .st database)
- sci-hub.su resolved the DOI correctly and provided the PDF
- PDF downloaded as `yuan2010.pdf` (627KB), valid PDF document
- PDF was Springer-protected (Read tool reported "password-protected"); used ImageMagick to render all 20 pages to PNG for reading
- All 20 pages rendered and read successfully

**Directory:** `papers/Yuan_2011_GameAccessibilitySurvey/`

---

## Reading

**Status:** SUCCESS

All 20 pages read from PNG renders. Content fully extracted including:
- Abstract (p. 1)
- Game interaction model with sequence diagram and finite state machine (pp. 83–85)
- Disability statistics table from 2002 US Census (p. 86)
- All four impairment sections with selected game catalogues and strategy tables (pp. 87–94)
- Discussion and research issues (pp. 95–97)
- Conclusions (pp. 97–98)
- Full reference list, 106 entries (pp. 98–100)

---

## Files Created

| File | Size | Status |
|------|------|--------|
| `papers/Yuan_2011_GameAccessibilitySurvey/notes.md` | 15KB | Created |
| `papers/Yuan_2011_GameAccessibilitySurvey/description.md` | 1KB | Created |
| `papers/Yuan_2011_GameAccessibilitySurvey/abstract.md` | 2KB | Created |
| `papers/Yuan_2011_GameAccessibilitySurvey/citations.md` | 19KB | Created |
| `papers/Yuan_2011_GameAccessibilitySurvey/pngs/` | 20 PNGs | Created (rendering artifact, kept) |
| `papers/CLAUDE.md` | — | Updated with new entry |

---

## Cross-References

**Already in collection:**
- `Mack_2021_AccessibilityResearchSurvey` — identifies game accessibility as an emerging underrepresented area; Yuan et al. is the foundational paper behind that observation

**New leads identified (not yet in collection):**
- Grammenos et al. (2005) — UA Chess, universally accessible board game design
- Simpson & Koester (1999) — Adaptive one-switch row-column scanning (motor AT fundamentals)
- Yuan & Folmer (2008) — Blind Hero (haptic guitar hero, specific accessible game)
- Folmer et al. (2009) — Textsl, command-based virtual world interface for visually impaired
- Smith & Graham (2006) — Eye movements for video game control

---

## Usefulness Assessment

**Rating:** High

**What it provides:**
- The canonical three-step game interaction model (receive stimuli → determine response → provide input) that maps each disability type to exactly one step — this is the conceptual skeleton all subsequent game accessibility work builds on
- Table 7 (accessibility strategies summary): the most comprehensive taxonomy of game accessibility strategies in the literature, organized by impairment type and interaction step, with two levels (high-level and low-level implementations)
- Population statistics: 32.2 million Americans affected (~11%), with 6.3 million completely excluded — the go-to citation for scale arguments in game accessibility
- Concrete catalogue of accessible games per genre and impairment type, with specific strategies used in each
- Research gap identification: strategy/sports/RPG genres severely underrepresented; cognitive accessibility barely researched; no standardized metrics for game accessibility

**Actionable next steps:**
- Use Table 7 as a checklist when evaluating any game for accessibility compliance
- Follow up on the IGDA SIG White Paper [41] and Norwegian Medialt guidelines [89] to understand the prior art this paper supersedes
- Identify whether post-2011 accessible games (e.g., The Last of Us Part II, Xbox Adaptive Controller games) can be mapped to this framework to validate or extend it
- The cognitive accessibility section (only 5 games found) is the largest research gap and most promising area for new collection papers

**Skip if:**
- The research focus is purely on web/software accessibility with no game-specific interest
- The question is about post-2018 game accessibility (Xbox Adaptive Controller era); this paper will need to be supplemented with newer work
