# Paper Processing Report: Ability-Based Design

**Date:** 2026-02-28
**Paper:** Wobbrock, Kane, Gajos, Harada, Froehlich (2011) — "Ability-Based Design: Concept, Principles and Examples"
**Venue:** ACM Transactions on Accessible Computing (TACCESS), Vol. 3, No. 3, Article 9
**DOI:** 10.1145/1952383.1952384

---

## Retrieval

**Status:** Success
**Source:** Harvard faculty website (direct PDF, free access)
**URL:** https://kgajos.seas.harvard.edu/papers/wobbrock11abd.pdf
**Directory:** `papers/Wobbrock_2011_AbilityBasedDesign/paper.pdf`
**Size:** 6.3 MB, 36 pages (PDF reported 10 pages in metadata, actual render was 36 page images)

---

## Reading

**Status:** Success
**Method:** Medium paper path (Step 2B) — PDF converted to 36 PNG images via ImageMagick, read sequentially
**All pages read:** Yes (pages 0–35)

---

## Files Created

| File | Status |
|---|---|
| `papers/Wobbrock_2011_AbilityBasedDesign/notes.md` | Created (17,600 bytes) |
| `papers/Wobbrock_2011_AbilityBasedDesign/description.md` | Created (1,096 bytes) |
| `papers/Wobbrock_2011_AbilityBasedDesign/abstract.md` | Created (1,976 bytes) |
| `papers/Wobbrock_2011_AbilityBasedDesign/citations.md` | Created (30,876 bytes) |
| `papers/Wobbrock_2011_AbilityBasedDesign/pngs/` | 36 page images |
| `papers/CLAUDE.md` | Updated with new entry |

---

## Cross-References

**Papers already in collection cited/overlapping with this paper:** 4

- `Krishnavajjala_2024_MotorEase` — ABD Principle 2 (Accountability) is the theoretical basis for MotorEase's violation detection targets; backward annotation added to MotorEase's notes.md
- `Mack_2021_AccessibilityResearchSurvey` — ABD provides vocabulary explaining motor accessibility research concentration
- `Yuan_2011_GameAccessibilitySurvey` — ABD's ability reframing applies directly to game accessibility design
- `Gartland_2022_WebAccessibilityCognitive` — ABD's Principle 2 aligns with Gartland's co-design critique

**New leads (not yet in collection):** 5 high-priority papers identified

1. Gajos, Weld, Wobbrock (2010) — SUPPLE: Full ABD implementation; *Artificial Intelligence* 174
2. Wobbrock et al. (2009) — The Angle Mouse; CHI '09
3. Hurst et al. (2008a) — Automatic pointing performance detection; IUI '08
4. Kane, Bigham, Wobbrock (2008a) — Slide Rule; ASSETS '08
5. Froehlich, Wobbrock, Kane (2007) — Barrier Pointing; ASSETS '07

**Backward annotations written:** 1 (MotorEase notes.md)

---

## Usefulness Assessment

**Rating:** High

**What it provides:**

- The canonical theoretical framework for accessible computing from an ability perspective — seven named, categorized design principles (Ability, Accountability, Adaptation, Transparency, Performance, Context, Commodity) that function as a design checklist applicable across any assistive or adaptive system
- The conceptual vocabulary shift from "what disability does a person have?" to "what can a person do?" — directly applicable as a critique and evaluation lens for any paper in this collection
- 14 concretely described example projects with explicit principle mappings — a reference taxonomy of ability-based implementations spanning keyboard, mouse, mobile, and web
- Key quantitative results from SUPPLE (28% speed, 73% accuracy gains for motor-impaired users) and Angle Mouse (>10% throughput, ~18% accuracy gain) that provide benchmarks for adaptive interface evaluation
- The situationally-induced impairments concept (SIIDs) — framing that connects disability accessibility work to universal design for all situational contexts

**Actionable next steps:**

- Use the seven principles as an evaluation checklist when reading/adding papers on adaptive interfaces (e.g., screen reader architecture papers: does the screen reader uphold Accountability by adapting to user behavior, or does it require the user to learn its conventions?)
- Cross-reference SUPPLE (Gajos et al. 2010) against this paper's description — SUPPLE is described in depth here and is the prime example of Principles 3, 4, 5, 7 in action; worth adding to the collection
- Apply ABD's Principle 5 (Performance measurement) as a theoretical frame when evaluating MotorEase's approach: MotorEase detects static violations, but ABD suggests the richer goal is dynamic performance monitoring and adaptation

**Skip if:**

- Unlikely to be skippable for this collection — this paper defines the foundational theory that underpins all motor accessibility, adaptive interface, and AT design research represented here
