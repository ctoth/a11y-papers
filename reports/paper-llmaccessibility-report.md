# LLM/AI Accessibility Paper — Process Report

**Date:** 2026-02-28
**Task:** Find and process a recent paper on using LLMs or AI to improve accessibility.

---

## Paper Selected

**FigurA11y: AI Assistance for Writing Scientific Alt Text**
- Authors: Nikhil Singh, Lucy Lu Wang, Jonathan Bragg
- Year: 2024
- Venue: IUI 2024 (29th International Conference on Intelligent User Interfaces)
- DOI: https://dl.acm.org/doi/10.1145/3640543.3645212
- PDF source: https://llwang.net/assets/pdf/2024_singh_figura11y_iui.pdf (author's personal website)
- Paper directory: `papers/Singh_2024_FigurA11y/`

### Why This Paper

FigurA11y was selected over other candidates (GenAssist, Trewin et al. AI Fairness) because:
1. It connects directly to an existing paper in the collection (Wang_2021_ScientificPDFAccessibility), creating an immediately useful cross-reference
2. It is the most concrete, implementable recent paper — includes full prompt templates in an appendix
3. It addresses the hardest alt text case (open-domain scientific figures) rather than constrained domains
4. Published in a peer-reviewed ACM venue (IUI 2024) with a full user study (N=14), not just a system description
5. The PDF was freely accessible from the author's website without requiring sci-hub

---

## Retrieval

- **Method:** Direct curl download from author's personal website (llwang.net)
- **Status:** Success
- **File size:** 6.5 MB (6,649,380 bytes)
- **Pages:** 21 (confirmed with pdfinfo)
- **PDF validity:** Confirmed (PDF document version 1.5)
- **Text extraction:** pdftotext successful — full paper text available despite Read tool reporting password-protection (known false positive with some PDF compression schemes)

---

## Reading and Annotation

- **Path taken:** Small paper (21 pages, <20MB) — direct text extraction via pdftotext
- **Status:** Success — all four annotation files created

### Files Created

| File | Size | Status |
|------|------|--------|
| `papers/Singh_2024_FigurA11y/paper.pdf` | 6.5 MB | Retrieved |
| `papers/Singh_2024_FigurA11y/notes.md` | 18.5 KB | Created |
| `papers/Singh_2024_FigurA11y/description.md` | 1.2 KB | Created |
| `papers/Singh_2024_FigurA11y/abstract.md` | 2.8 KB | Created |
| `papers/Singh_2024_FigurA11y/citations.md` | 14.0 KB | Created |

---

## papers/CLAUDE.md Updated

The Singh_2024_FigurA11y entry has been appended to `papers/CLAUDE.md`.

---

## Cross-References

### Already in Collection
- **Wang_2021_ScientificPDFAccessibility** — FigurA11y directly addresses the author-side alt text tooling gap identified in Wang et al.'s recommendations. Backward annotation added to Wang_2021 notes.md.
- **Mack_2021_AccessibilityResearchSurvey** — Survey context: FigurA11y represents the emerging AI+accessibility intersection Mack identified as underexplored.

### New Leads Identified (not yet in collection)
- **Lundgard & Satyanarayan (2021)** — "Accessible visualization via natural language descriptions: A four-level model" — IEEE TVCG — foundational semantic framework embedded in FigurA11y; high priority addition
- **Chintalapati, Bragg & Wang (2022)** — "A dataset of alt texts from HCI publications" — ASSETS 2022 — established 4.6% valid alt text baseline
- **Williams et al. (2022)** — "Toward supporting quality alt text in computing publications" — W4A 2022 — author interview study + descriptiveness rubric
- **Mack et al. (2021, ASSETS)** — "Designing tools for high-quality alt text authoring" — direct design predecessor to FigurA11y
- **Wu et al. (2017)** — "Automatic alt-text" (Facebook) — CSCW 2017 — large-scale industrial alt text precedent

### Backward Annotations Written
- `papers/Wang_2021_ScientificPDFAccessibility/notes.md` — appended See Also note pointing to Singh_2024_FigurA11y

---

## Usefulness Rating: HIGH

### What It Provides

- **Complete prompt templates** (Appendix B) — four instruction prompt variants for different generation tasks (high-level summary, continuation/infilling, full draft, potential user questions), ready to adapt
- **Metadata extraction pipeline** — validated combination of PDFFigures 2.0 + GROBID + EasyOCR + data table extraction; shows what contextual signals improve LLM alt text quality
- **LLM selection evidence** — GPT-4 vs LLaVA comparison on scientific figures; GPT-4 wins on descriptiveness and hallucination rate
- **Prompt engineering lessons** — logit biases to prevent metadata label leakage; uncertainty prompts for noisy OCR; instruction repetition for reliability
- **User study design** — within-subjects (N=14), authors use their own figures, NASA TLX cognitive load measurement; replicable methodology for evaluating AI-assisted accessibility tools
- **Validated UX pattern** — metadata visible in main interface (not hidden in menu) is important for author cross-reference during drafting

### Actionable Next Steps

- If building any alt text tooling: use the Appendix B prompt templates as starting point
- The metadata prompt structure (caption + mentions + OCR + data table + guidelines) is the key design pattern — replicate this for other figure description contexts
- Lundgard & Satyanarayan (2021) four-level model should be added next — it's the semantic framework that determines what goes into a complete scientific figure description

### Skip If

- Research question is about BLV reader experience (not author tooling) — this paper studies authors, not BLV users
- Focus is on natural images or social media images (not scientific/academic figures)
- Fully automated (no human in loop) approach is required — FigurA11y explicitly requires author involvement
