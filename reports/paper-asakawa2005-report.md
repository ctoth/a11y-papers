# Paper Processing Report: Asakawa 2005

## Status: Complete

**Paper:** "What's the Web Like If You Can't See It?"
**Author:** Chieko Asakawa
**Venue:** W4A 2005 (International Cross-Disciplinary Workshop on Web Accessibility), ACM
**DOI:** 10.1145/1061811.1061813

---

## Retrieval

- **Source:** sci-hub.st
- **URL:** `https://sci-hub.st/storage/2024/4359/95c99358f1f4d5cb064fb49a1b848f22/asakawa2005.pdf`
- **File:** `papers/Asakawa_2005_BlindWebBrowsing/paper.pdf`
- **Size:** 252 KB, 8 pages
- **PDF valid:** Yes (PDF document, version 1.3, 8 pages confirmed by `file` command)

---

## Reading and Annotation

All four annotation files created successfully:

| File | Status |
|------|--------|
| `notes.md` | Created — full implementation notes with empirical data tables, skip-link taxonomy, tool descriptions, cross-references |
| `description.md` | Created — three-sentence summary |
| `abstract.md` | Created — verbatim abstract + interpretation |
| `citations.md` | Created — all 25 references + 5 key follow-up citations |

**papers/CLAUDE.md:** Updated with description entry for `Asakawa_2005_BlindWebBrowsing`.

**Backward annotation:** Appended see-also note to `Lazar_2007_ScreenReaderFrustration/notes.md` documenting the precursor relationship.

---

## Cross-References

### Already in Collection (4 papers)
- **Lazar_2007_ScreenReaderFrustration** — Asakawa identifies the failure modes (broken skip-links, bad ALT text); Lazar quantifies how often they cause real-world frustration. Backward annotation added.
- **Pool_2023_AccessibilityMetatesting** — Asakawa's 2005 observation that tools cannot check skip-navigation quality is the tool gap Pool's 2023 ensemble study addresses 18 years later.
- **Martins_2023_LargeScaleWebA11y** — Asakawa's 11-site longitudinal audit is the direct small-scale precursor to Martins' 2.8M-page study.
- **Wobbrock_2011_AbilityBasedDesign** — Asakawa's "disability experience" argument is an early instance of Wobbrock's Accountability and Transparency principles.

### New Leads (Not Yet in Collection)
- **Takagi et al. (ASSETS 2004)** — "Accessibility Designer: Visualizing Usability for the Blind" — full aDesigner technical paper. High priority.
- **Asakawa & Itoh (ASSETS 1998)** — "User Interface of a Home Page Reader" — HPR architecture paper. High priority.
- **Asakawa & Takagi (ASSETS 2000)** — "Annotation-based Transcoding for Nonvisual Web Access." Medium priority.
- **Takagi et al. (ASSETS 2002)** — "Site-wide Annotation: Reconstructing Existing Pages to be Accessible." Medium priority.
- **Asakawa & Itoh (CHI 1999)** — "User Interface of Non-visual Table Navigation Method." Medium priority.

---

## Usefulness Assessment

**Rating: High**

**What it provides:**
- The foundational historical document on voice browser / screen reader web interaction, written by the creator of IBM Home Page Reader who is herself blind — authoritative first-person and empirical.
- Longitudinal empirical data (1997–2005, 11 sites) on alt text coverage trends, with regulatory inflection point documented: Section 508 effective June 2001 coincides with immediate improvement in federal agency ALT compliance.
- A four-pattern taxonomy of broken skip-navigation link code failures found in well-intentioned, accessibility-focused sites — directly implementable as a test suite for any skip-link checker.
- Description of aDesigner reaching-time visualization as a design evaluation approach — a specific, concrete tool design that is still relevant for modern accessibility evaluation tooling.

**Actionable next steps:**
- Add the Takagi et al. ASSETS 2004 aDesigner paper to the collection — it is the detailed technical reference for the tool described here.
- Add Asakawa & Itoh ASSETS 1998 for screen reader architecture detail.
- The four broken skip-link patterns (Section 4.2) are directly usable as test cases for Pool_2023-style automated tool evaluation.

**Skip if:**
- The research focus is exclusively on cognitive or motor accessibility rather than screen reader / visual impairment topics.
