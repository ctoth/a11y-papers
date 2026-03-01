# Paper Processing Report: Wang_2021_ScientificPDFAccessibility

**Date:** 2026-02-28
**Paper:** Improving the Accessibility of Scientific Documents (arXiv:2105.00076)
**Authors:** Lucy Lu Wang, Isabel Cachola, Jonathan Bragg, et al. (10 authors, Allen Institute for AI)
**Year:** 2021

---

## Retrieval

- **Source:** arxiv (https://arxiv.org/pdf/2105.00076.pdf)
- **Status:** Success
- **File:** `papers/Wang_2021_ScientificPDFAccessibility/paper.pdf`
- **Size:** 2.7 MB
- **Pages:** 44 (PDF header reported 6 pages incorrectly; actual page count confirmed by ImageMagick conversion)

**Note on PDF read:** The arxiv PDF reports as "password-protected" to the Read tool (a known false-positive for arxiv PDFs, documented in the retriever skill). Paper was converted to 44 PNG images via ImageMagick and read sequentially. Pages 0–35 contain the main paper (abstract through references); pages 36–43 are appendices.

---

## Reading

- **Status:** Success
- **Method:** Image conversion (44 PNG pages at 150 DPI); pages read sequentially using Read tool
- **Pages read:** 0–35 (full paper), spot-checks on 36+ (appendices)

---

## Files Created

| File | Size | Status |
|------|------|--------|
| `papers/Wang_2021_ScientificPDFAccessibility/paper.pdf` | 2.7 MB | Retrieved |
| `papers/Wang_2021_ScientificPDFAccessibility/pngs/` | 44 PNGs | Created |
| `papers/Wang_2021_ScientificPDFAccessibility/notes.md` | 16 KB | Created |
| `papers/Wang_2021_ScientificPDFAccessibility/description.md` | 1 KB | Created |
| `papers/Wang_2021_ScientificPDFAccessibility/abstract.md` | 2.3 KB | Created |
| `papers/Wang_2021_ScientificPDFAccessibility/citations.md` | 11 KB | Created |
| `papers/CLAUDE.md` | Updated | Wang_2021 entry appended |

---

## Cross-References

**Papers already in collection:**
- `Mack_2021_AccessibilityResearchSurvey` — cited implicitly; same CHI/ASSETS accessibility landscape that Wang et al. sample from

**New leads not yet in collection (5 key citations):**
- Lazar et al. (2017) "Making the field of computing more inclusive" — Commun. ACM — prior PDF compliance study, key comparator for the 2.4% figure
- Lo et al. (2020) "S2ORC: The Semantic Scholar Open Research Corpus" — ACL 2020 — foundational ML pipeline underlying SciA11y
- Brady et al. (2015) "Creating accessible PDFs for conference proceedings" — W4A — first CHI/ASSETS compliance analysis
- Siegel et al. (2018) "Extracting Scientific Figures with Distantly Supervised Neural Networks" — JCDL — DeepFigures paper
- Ahmetovic et al. (2018) "Axessibility" — SIGACCESS — LaTeX package for accessible math equations (addresses SciA11y's equation limitation)

**Backward annotations:** None (no existing paper is directly superseded or recontextualized by Wang et al.)

---

## Usefulness to This Project

**Rating:** High

**What it provides:**
- The definitive empirical baseline for scientific PDF inaccessibility: 2.4% full compliance, 74.7% zero compliance across 11,397 PDFs from 2010–2019
- Five concrete, implementation-actionable design recommendations for accessible document reader systems (structure, tagging, external memory, error indication, verbosity reduction)
- Compliance breakdown by typesetting software: Microsoft Word > Adobe InDesign > Arbortext APP > LaTeX — directly relevant for researchers who want to produce accessible outputs
- Compliance breakdown by field of study — establishes that STEM fields (mathematics, biology, geology) are worst performers
- Validated ML-to-HTML pipeline (SciA11y) with extraction error taxonomy (Table 4: 11 categories with common errors) — reusable framework for evaluating any PDF extraction system
- User study data on what BLV researchers actually need (bidirectional citation links, proper headings, table of contents, error transparency)

**Actionable next steps:**
- Use the five accessibility criteria (alt-text, table headers, tagged PDF, default language, tab order) as the standard checklist for any PDF accessibility evaluation in this collection
- Investigate follow-up paper arXiv:2410.03022 (Wang et al. 2024, "Uncovering the New Accessibility Crisis in Scholarly PDFs") which extends this to 20,000 PDFs with updated findings
- Retrieve Lazar et al. (2017) [23] to complete the baseline compliance study lineage
- Consider retrieving Lo et al. (2020) S2ORC paper for technical detail on the extraction pipeline

**Skip if:**
- Research focus is exclusively on web or mobile accessibility (this paper is specific to scientific PDF documents)
- Looking for WCAG or WAI-ARIA standards work (only tangentially referenced here)
