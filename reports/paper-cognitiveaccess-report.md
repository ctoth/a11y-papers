# Paper Processing Report: Cognitive Accessibility

**Task:** Retrieve and process a cognitive accessibility paper
**Date:** 2026-02-28
**Status:** Complete

---

## Paper Selected

**Title:** The State of Web Accessibility for People with Cognitive Disabilities: A Rapid Evidence Assessment
**Authors:** Sara Gartland, Paul Flynn, Maria Ana Carneiro, Greg Holloway, Jose de Sousa Fialho, Joe Cullen, Emma Hamilton, Amy Harris, Clare Cullen
**Year:** 2022
**Journal:** Behavioral Sciences (MDPI), Vol. 12, No. 2, Article 26
**DOI:** 10.3390/bs12020026

**Selection rationale:** Systematic review (45 papers, 2006-2021) providing the broadest available empirical coverage of cognitive accessibility in the web domain. Open-access MDPI publication. Directly addresses a gap in the collection (no cognitive accessibility papers previously present). Covers WCAG implications, disability-specific barriers, tools, and research methodology — maximally useful as a foundational reference.

---

## Retrieval

**Source:** MDPI (open access) — direct PDF via `mdpi-res.com` CDN with browser User-Agent
**URL used:** `https://mdpi-res.com/d_attachment/behavsci/behavsci-12-00026/article_deploy/behavsci-12-00026.pdf`
**Size:** 1,144,012 bytes (1.1 MB)
**File:** `papers/Gartland_2022_WebAccessibilityCognitive/paper.pdf`
**Verified:** PDF document, version 1.7, 44 pages (after image conversion)

**Attempts before success:**
1. `https://www.mdpi.com/2076-328X/12/2/26/pdf` — returned HTML (redirect loop)
2. `https://doi.org/10.3390/bs12020026` with Accept: application/pdf — returned HTML
3. `https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8869505/pdf/` — returned HTML (login required)
4. Sci-Hub — paper absent from database
5. MDPI CDN URL with browser User-Agent — SUCCESS

---

## Reading

**Method:** PDF conversion to PNG images via ImageMagick (44 pages generated), read sequentially
**Reason PDF not read directly:** False "password-protected" error from Read tool (known issue with some PDFs)
**All pages read:** Yes (pages 000-043 including all appendices and reference list)

**Output files created:**
- `papers/Gartland_2022_WebAccessibilityCognitive/notes.md` — 14,150 bytes
- `papers/Gartland_2022_WebAccessibilityCognitive/description.md` — 952 bytes
- `papers/Gartland_2022_WebAccessibilityCognitive/abstract.md` — 2,168 bytes
- `papers/Gartland_2022_WebAccessibilityCognitive/citations.md` — 17,902 bytes (all 74 references)
- `papers/Gartland_2022_WebAccessibilityCognitive/pngs/` — 44 page images retained

---

## Index Update

`papers/CLAUDE.md` updated with new entry for `Gartland_2022_WebAccessibilityCognitive`.

---

## Cross-References

**Already in collection:**
- `Mack_2021_AccessibilityResearchSurvey` — cited as [25] by Gartland et al. to establish that PwCDs are underrepresented in CHI/ASSETS accessibility research. Backward annotation added to Mack notes.md.

**New leads (not yet in collection):**
- Borg, Lantz, Gulliksen (2015) — direct predecessor systematic review on electronic communication accessibility for PwCDs; Univers. Access Inf. Soc.
- Karreman, van der Geest, Buursink (2007) — empirical evidence for easy-to-read design principles for intellectual disabilities
- Lazar et al. (2018) — co-design methodology example with Down syndrome participants; best practices illustration
- Ophoff, Johnson, Renaud (2021) — CAPTCHA/authentication barriers for people with dyslexia; W4A 2021
- Gillespie-Lynch et al. (2014) — autism + internet use from participant perspective

---

## Usefulness Assessment

**Rating:** High

**What it provides:**
- Foundational evidence map for the cognitive accessibility topic area — the first systematic review in this collection covering this population
- WCAG 2.0/2.1/2.2 criteria specifically flagged by W3C COGA Task Force as supporting PwCDs (extracted as a complete annotated list in notes.md)
- Disability-by-barrier matrix: which cognitive disability types face which specific barriers, with empirical citations
- Four-quadrant best-practices framework (People/Technology/Space/Process) for conducting research with PwCDs as co-designers
- Identification of the most and least studied cognitive disability populations in the field

**Actionable next steps:**
- Retrieve Borg et al. (2015) as the predecessor review to understand the evolution of findings over time
- Retrieve WAI-COGA Task Force documents (not a paper, but the primary normative reference underlying this review)
- When adding any paper on dyslexia, autism, intellectual disability, or dementia + web/tech, cross-reference to this review's barrier taxonomy

**Skip if:**
- Looking only for assistive technology that does not involve web content (e.g., hardware input devices, screen reader internals)
- Working exclusively on WCAG automated testing without regard for the user populations the guidelines are meant to serve
