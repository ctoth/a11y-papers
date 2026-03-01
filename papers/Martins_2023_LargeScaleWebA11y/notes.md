# A large-scale web accessibility analysis considering technology adoption

**Authors:** Beatriz Martins, Carlos Duarte
**Year:** 2023 (published online 6 July 2023; journal volume 2024)
**Venue:** Universal Access in the Information Society, vol. 23, pp. 1857-1872
**DOI:** https://doi.org/10.1007/s10209-023-01010-0
**Open Access:** CC BY 4.0

## One-Sentence Summary
Automated WCAG 2.1 evaluation of 2,884,498 web pages (March–September 2021) shows 30 errors per page on average and reveals that the technology stack used to build a site is a statistically significant predictor of its accessibility level — with some technologies reliably associated with better or worse outcomes.

## Problem Addressed
We know web accessibility is broadly poor, but we lack large-scale evidence linking specific web technologies (CMSes, JS frameworks, libraries, advertising platforms) to measurable accessibility outcomes. This study fills that gap by combining automated accessibility evaluation with technology fingerprinting at near-3-million-page scale.

## Key Contributions
- Baseline: 2,884,498 pages, 166,311 websites, 86,644,426 total errors detected
- Technology fingerprinting using Wappalyzer + SimilarTech across 3,482 technologies in 166 categories
- Statistical comparison (Mann-Whitney U, Kruskal-Wallis, Dunn's test) of A3 accessibility metric scores across 32 technology categories, 6 categories at technology-specific level
- Identification of categories and specific technologies that predict better vs. worse accessibility
- Dataset available: https://doi.org/10.5281/zenodo.7494722

## Methodology

**Data source:** CommonCrawl (November/December 2020 snapshot), evaluated March–September 2021

**Accessibility evaluator:** QualWeb v0.6.1 — tests 72 ACT-Rules, covering 30 WCAG 2.1 success criteria (38% of total criteria). ACT-Rules only: reduces false positives at cost of false negatives.

**Accessibility metric:** A3 (aggregation function, range 0–1, higher = worse accessibility)

$$
A3 = 1 - \prod_{b}(1 - F_b)^{\frac{B_{pb}}{N_{pb}} + \frac{B_{pb}}{B_p}}
$$

Where:
- $B_{pb}$ = actual failure points of checkpoint $b$ on page $p$
- $N_{pb}$ = potential failure points of checkpoint $b$ on page $p$
- $F_b$ = severity of barrier $b$
- Average A3 for all pages = 0.6657

**Technology fingerprinting:** Wappalyzer (1,197 technologies detected) + SimilarTech (2,733 technologies). SimilarTech finds ~3x more technologies on average. Used together to maximize coverage. ~3,500 technologies total, merged into unified categories.

**Statistical tests:**
- Mann-Whitney U: 32 categories compared to non-category pages (significance: p < 0.0016 after Bonferroni correction for 32 tests)
- Kruskal-Wallis + Dunn's test with Bonferroni correction: intra-category technology comparison for 6 categories present in >1M pages

## Key Findings: Most Violated Rules

**Table 2 — ACT rules violated in >10% of pages:**

| ACT-rule | Description | Success Criteria | % of Pages |
|----------|-------------|-----------------|------------|
| 09o5cg | Text has enhanced contrast | 1.4.6 (Enhanced) | 79% |
| afw4f7 | Text has minimum contrast | 1.4.3 (Minimum) | 66% |
| c487ae | Link has non-empty accessible name | 4.1.2 / 2.4.4 / 2.4.9 | 52% |
| 3ea0c8 | id attribute value is unique | 4.1.1 (Parsing) | 31% |
| 23a2a8 | Image has non-empty accessible name | 1.1.1 (Non-text) | 30% |
| e086e5 | Form field has non-empty accessible name | 4.1.2 | 22% |
| b4f0c3 | meta viewport allows for zoom | 1.4.4 / 1.4.10 | 22% |
| cae760 | iframe has non-empty accessible name | 4.1.2 | 19% |
| b5c3f8 | HTML page has lang attribute | 3.1.1 | 18% |

**Key WCAG success criteria violated (% of pages):**
- 1.4.6 Contrast Enhanced: 79%
- 4.1.2 Name, role, value: 68%
- 1.4.3 Contrast Minimum: 66%
- 2.4.4 Link purpose (In Context): 52%
- 2.4.9 Link purpose (Link Only): 52%
- 1.1.1 Non-text content: 33%
- 4.1.1 Parsing: 31%
- 1.3.1 Info and relationships: 24% — **This corresponds mainly to improper use of ARIA roles and properties and missing relationships in table elements**
- 1.4.10 Reflow: 22%
- 1.4.4 Resize text: 22%
- 3.1.1 Language of page: 19%

**Critical ARIA finding:** WCAG 1.3.1 (Info and relationships) violations — identified in 24% of pages — are attributed specifically to improper use of ARIA roles and properties, making this the primary ARIA-related failure in the corpus.

## Key Findings: Technology and Accessibility

**Mann-Whitney U results (Table 4):** 29 of 32 technology categories show statistically significant differences (p < 0.001) in A3 scores between pages using vs. not using technologies in the category.

**Categories associated with IMPROVED accessibility (lower A3 = better):**
- Accessibility tools
- CMS
- JavaScript Frameworks
- JavaScript Graphics
- JavaScript Libraries
- LMS
- PaaS
- Page Builders
- Programming Languages
- Rich Text Editors
- Static Site Generators
- UI Frameworks
- Wikis
- Web Frameworks
- Multilingual
- Online Forms

**Categories associated with DECREASED accessibility (higher A3 = worse):**
- Advertising
- Comment Systems
- Editors
- LiveChat
- Maps
- Message Boards
- Security
- Social Logins
- Video Players
- Audio/Video Media
- Captcha
- Forum Software
- Online Video Platform

**Non-significant categories:** Mobile Frameworks (p=0.005), Photo Galleries (p=0.052), Website Builder (p=0.839)

## Key Findings: Specific Technologies (Table 5, Figure 9)

**JavaScript Libraries (widest A3 range: 0.441):**
- Best: Polyfill.js (μ=0.769), jQuery Migrate (μ=0.766)
- Worst: Isotope (μ=0.328) — significantly lower than all others
- Also notably low: Slick (μ=0.378), jQuery (μ=0.472), jQuery UI (μ=0.628)

**CMS:**
- Best: Jimdo (μ=0.855), Elementor (μ=0.789)
- Worst: Drupal (μ=0.586), Joomla (μ=0.566)
- WordPress (μ=0.624) — middle of the pack

**JavaScript Frameworks:**
- Best: Mustache JS (μ=0.809)
- Worst: MooTools (μ=0.583)
- React (μ=0.613) — notably poor

**Programming Languages:**
- Best: Python (μ=0.816), Java (μ=0.778)
- Worst: NodeJS (μ=0.547)

**UI Frameworks:**
- Bootstrap (μ=0.654) outperforms ZURB Foundation (μ=0.641)
- Both are below the overall mean (0.6657) — associated with better accessibility

**Advertising:**
- Best: Facebook Advertiser (μ=0.755), Google AdWords Advertiser (μ=0.752)
- Worst: DoubleClick (μ=0.652)

## Parameters

| Metric | Value | Notes |
|--------|-------|-------|
| Pages evaluated | 2,884,498 | From 166,311 websites |
| Total errors found | 86,644,426 | |
| Average errors per page | 30 | |
| Average errors per website | 521 | |
| Max errors on single page | 15,645 | |
| Pages with 0 errors | 15,963 (0.5%) | |
| Pages with ≥10 errors | ~63% (1,817,234) | |
| Average A3 score (all pages) | 0.6657 | Range 0–1, higher=worse |
| .gov pages avg errors | 16 per page | Best TLD |
| .edu pages avg errors | 18 per page | Second best |
| .br pages avg errors | 40 per page | Worst TLD |
| .news pages avg errors | 40 per page | Worst TLD |
| Study period | March–September 2021 | |
| ACT-Rules tested | 72 | QualWeb v0.6.1 |
| WCAG 2.1 success criteria covered | 30 (38%) | |
| Significance threshold | p < 0.0016 | Bonferroni for 32 tests |

## Implementation Details
- QualWeb uses ACT-Rules (community-validated test rules), not WCAG techniques — reduces false positives
- Wappalyzer available as QualWeb module — same web request handles both eval and tech identification
- SimilarTech run separately with its own Docker containers, synchronized via domain pool
- Results stored in PostgreSQL; QualWeb returns JSON; processed per-table for evaluation vs. technology data
- For intra-category analysis: only technologies present in >2% of category pages (>8% for Advertising due to 43 technologies)
- Statistical approach: Mann-Whitney for category-level; Kruskal-Wallis + Dunn's for specific technology comparison

## Figures of Interest
- **Fig. 1 (p. 4):** Log-scale distribution of % pages vs. max errors — 37% of pages have 0-10 errors
- **Fig. 2 (p. 5):** Error count by TLD — .gov (16) and .edu (18) best; .br and .news (40) worst
- **Fig. 9 (p. 9, Table 5 p. 9):** Technology distribution within each of 6 key categories — range of A3 scores from best to worst technology within each category

## Limitations
- Automated tool only (QualWeb): detects errors with high precision but misses human-judgment failures (e.g., meaningful vs. decorative images, comprehension)
- ACT-Rules cover only 38% of WCAG 2.1 success criteria — significant false negative rate for uncovered criteria
- Technology categorization from two tools may differ; merged categories may group differently-behaving technologies
- Study snapshot: March–September 2021 only; accessibility may have changed
- Does not evaluate ARIA-specific conformance directly — ARIA failures surface through WCAG SC violations (primarily 1.3.1 and 4.1.2)
- Does not analyze specific ARIA attributes or roles — only detects downstream effects (missing names, broken relationships)

## Testable Properties
- Average A3 across a large random web sample should be approximately 0.67 (from 2021 baseline)
- Pages with CMS technology should show better accessibility (lower A3) than pages without CMS
- Pages with advertising technology should show worse accessibility (higher A3) than pages without
- Government (.gov) and education (.edu) pages should show fewer errors than commercial (.com, .br, .news) pages
- Within JavaScript Libraries, Isotope-using pages should have significantly lower A3 than Polyfill-using pages
- Only about 0.5% of pages in a large web corpus should have zero detected accessibility errors
- 79% of pages violate WCAG 1.4.6 (enhanced contrast) and 66% violate 1.4.3 (minimum contrast) — contrast is the dominant failure

## Relevance to Project
This paper provides the largest-scale empirical baseline (2.9M pages) for WCAG 2.1 conformance rates and directly links technology stack choices to accessibility outcomes. For ARIA research specifically, the 24% WCAG 1.3.1 failure rate is identified as caused by "improper use of ARIA roles and properties" — this is the closest this paper gets to ARIA-specific analysis. The technology-level A3 data enables concrete guidance: developers using React (μ=0.613), jQuery (μ=0.472), or Isotope (μ=0.328) are on platforms statistically associated with accessibility failures; those using Python backends (μ=0.816) or Polyfill.js (μ=0.769) show better outcomes. The dataset (Zenodo) is publicly available for follow-up analysis.

## Open Questions
- [ ] Why does Isotope.js (a filtering/sorting library) show such dramatically low A3 (0.328)? Is this the library itself or the type of sites that use it?
- [ ] Why does NodeJS (μ=0.547) perform significantly worse than other server-side languages? Is this correlation with SPA architecture and dynamic content inaccessibility?
- [ ] How do these 2021 numbers compare to 2024? The WebAIM Million shows 30→56.8 errors per page from 2021→2024 — contradicts this study's 30 errors per page in 2021 (likely different tools and test scope)
- [ ] What specific ARIA attributes/roles are causing the 1.3.1 violations? This paper does not drill into which ARIA patterns are misused.
- [ ] The paper doesn't analyze landmark roles, aria-label, aria-labelledby separately — is a follow-up paper warranted?

## Related Work Worth Reading
- Ref [25]: WebAIM Million (2021) — large-scale baseline comparison used throughout; WebAIM reports 51.4 errors/page vs. this study's 30 (tool difference)
- Ref [15]: Duarte et al. (2016) — predecessor study evaluating 1669 pages + technology influence on accessibility
- Ref [36]: Martins & Duarte (2022) — "Large-scale study of web accessibility metrics" (same authors, prior work on metrics comparison)
- Ref [8]: Bühler et al. (2006) — A3 metric origin
- Ref [39]: Vigo et al. (2013) — Benchmarking web accessibility evaluation tools

---

## Collection Cross-References

### Already in Collection
- **Mack_2021_AccessibilityResearchSurvey** — provides the broader research landscape context; this paper fills the empirical large-scale evaluation gap identified in Mack's survey as underrepresented
- **Lazar_2007_ScreenReaderFrustration** — the user-facing complement: Lazar documents what screen reader users experience; this paper identifies the structural causes (missing names, improper ARIA, broken links) at scale

### New Leads (Not Yet in Collection)
- Duarte et al. (2016) "Development technologies impact web accessibility" W4A '16 — direct predecessor studying technology-accessibility link in 1,669 pages; foundational for this study
- WebAIM Million 2021 [ref 25] — largest-scale US-centric study; methodological comparison essential; freely available at webaim.org
- Martins & Duarte (2022) "Large-scale study of web accessibility metrics" UAIS — same authors comparing 11 accessibility metrics; directly relevant to evaluation methodology

### Supersedes or Recontextualizes
- None in current collection
