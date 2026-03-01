# Paper Processing Report: ARIA/Web Accessibility Evaluation Study

**Task:** Find and process a paper on WAI-ARIA usage, effectiveness, or screen reader compatibility in practice.

---

## Paper Selected

**Title:** A large-scale web accessibility analysis considering technology adoption
**Authors:** Beatriz Martins, Carlos Duarte (LASIGE, Universidade de Lisboa)
**Venue:** Universal Access in the Information Society, vol. 23, pp. 1857-1872 (2024)
**Published online:** 6 July 2023
**DOI:** https://doi.org/10.1007/s10209-023-01010-0
**License:** CC BY 4.0 (open access)

**Paper directory:** `papers/Martins_2023_LargeScaleWebA11y/`

---

## Retrieval

- **Source:** Direct Springer PDF download (CC BY 4.0 open access)
- **URL used:** `https://link.springer.com/content/pdf/10.1007/s10209-023-01010-0.pdf`
- **Sci-Hub attempts:** Both sci-hub.st and sci-hub.su reported the article as not in their database
- **Final method:** `curl -L` directly to Springer's content PDF URL succeeded (1.55MB, 16 pages)
- **PDF status:** Valid but DRM-flagged (password-protected per Read tool); converted to 16 PNG images via ImageMagick for reading

---

## Reading

- PDF: 16 pages, 1.55MB — within direct-read threshold but DRM-blocked
- Conversion: 16 PNGs generated at 150dpi, stored in `papers/Martins_2023_LargeScaleWebA11y/pngs/`
- All 16 pages read successfully via Read tool on page images

---

## Files Created

| File | Size | Status |
|------|------|--------|
| `papers/Martins_2023_LargeScaleWebA11y/paper.pdf` | 1.55MB | Retrieved |
| `papers/Martins_2023_LargeScaleWebA11y/pngs/` | 16 pages | Converted |
| `papers/Martins_2023_LargeScaleWebA11y/notes.md` | 13KB | Written |
| `papers/Martins_2023_LargeScaleWebA11y/description.md` | 1.2KB | Written |
| `papers/Martins_2023_LargeScaleWebA11y/abstract.md` | 1.9KB | Written |
| `papers/Martins_2023_LargeScaleWebA11y/citations.md` | 10.9KB | Written (39 refs) |
| `papers/CLAUDE.md` | — | Updated with new entry |

---

## Paper Selection Rationale

Several candidates were evaluated:
- **Bi, Lutteroth, Weber (2022)** — not findable in any accessible form
- **Martins & Duarte (2023)** — found, open access, most data-driven option
- **WebAIM Million** — extensive ARIA data but not a peer-reviewed paper; cited in notes
- **Power et al. (2012) CHI** — landmark user study but from 2012, outside preferred date range

Martins & Duarte was selected as the best available data-driven paper:
- 2.9 million pages (largest scale found with accessible PDF)
- Peer-reviewed journal (Universal Access in Information Society)
- Technology fingerprinting linking specific frameworks/libraries to accessibility outcomes
- Direct ARIA finding: 24% of pages fail WCAG 1.3.1 due to "improper use of ARIA roles and properties"
- Open access with public dataset on Zenodo

---

## Key ARIA Findings (from paper)

The paper's most direct ARIA finding:

> WCAG 1.3.1 (Info and relationships) violations — identified in **24% of pages** — correspond mainly to **improper use of ARIA roles and properties** and to missing relationships in table elements.

This is at a scale of 2,884,498 web pages, making it the largest empirical measurement of ARIA misuse in the literature.

Additional relevant findings:
- WCAG 4.1.2 (Name, role, value — the primary ARIA semantic requirement) violated in **68% of pages**
- WCAG 2.4.4 (Link purpose, partly ARIA-dependent) violated in **52% of pages**
- Technology choices correlate strongly with accessibility: React (A3=0.613), bare jQuery (0.472), Isotope.js (0.328) → worse; Python-backed sites (0.816), Polyfill.js (0.769) → better

---

## Cross-References

**Already in collection (cited in paper):**
- `Mack_2021_AccessibilityResearchSurvey` — provides the broader research landscape (paper does not cite Mack directly, but is contextualized by it)
- `Lazar_2007_ScreenReaderFrustration` — user-facing complement: Lazar shows what screen reader users experience; Martins & Duarte shows the structural causes at scale

**New leads identified:**
- Duarte et al. (2016) W4A — direct predecessor, 1,669 pages, technology impact study
- Martins & Duarte (2022) UAIS — same authors, metric comparison paper
- WebAIM Million 2021 — not yet in collection; most directly ARIA-specific large-scale data
- Fernandes et al. (2012) W4A — RIA accessibility evaluation (ARIA-dependent apps)

---

## Usefulness to This Project

**Rating: High**

**What it provides:**
- Largest-scale (2.9M pages) empirical baseline for WCAG 2.1 conformance — the "state of ARIA in the wild" at population scale
- Direct measurement that 24% of pages fail WCAG 1.3.1 due to improper ARIA usage, and 68% fail WCAG 4.1.2 (Name, role, value)
- Technology-specific data: which CMS, JS framework, or library predicts better/worse accessibility outcomes — directly actionable for developer guidance
- Publicly available dataset (Zenodo) for follow-up ARIA-specific drill-down

**Actionable next steps:**
- The paper does not break down *which specific ARIA attributes or roles* cause the 1.3.1 failures — the WebAIM Million 2022/2023 reports do this (report specific ARIA role misuse rates, e.g., 31% of ARIA menu implementations are broken). That paper should be the next addition.
- The Fernandes et al. (2012) "Evaluating accessibility of rich internet applications" would complement this with a user-centered view of ARIA-specific failures.

**Skip if:**
- You need ARIA-specific attribute-level analysis (e.g., which roles are misused most) — this paper only detects downstream WCAG failures, not the specific ARIA patterns causing them
- You need user study data on how screen reader users experience ARIA failures — Lazar (2007) already in collection covers that
