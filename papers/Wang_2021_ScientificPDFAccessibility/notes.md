# Improving the Accessibility of Scientific Documents

**Authors:** Lucy Lu Wang, Isabel Cachola, Jonathan Bragg, Evie Yu-Yen Cheng, Chelsea Haupt, Matt Latzke, Bailey Kuehl, Madeleine van Zuylen, Linda Wagner, Daniel S. Weld
**Year:** 2021
**Venue:** arXiv preprint (cs.DL, cs.HC) — arXiv:2105.00076
**DOI/URL:** https://arxiv.org/abs/2105.00076

## One-Sentence Summary

Large-scale audit of 11,397 scientific PDFs finds only 2.4% fully accessible, then introduces SciA11y — a machine-learning pipeline that renders PDFs as accessible HTML — and validates it with six blind/low-vision researchers.

## Problem Addressed

Scientific literature is almost exclusively distributed as PDF. PDF conflates visual layout with content structure, making it inherently difficult for screen readers and other assistive technology to navigate. Authors rarely tag documents correctly; accessible PDFs require author action that most researchers do not take. This paper quantifies the scale of the problem and proposes a technological "band-aid" for the existing corpus.

## Key Contributions

1. **Meta-scientific audit**: 11,397 PDFs sampled from 2010–2019 across 19 fields of study; only 2.4% satisfy all five accessibility criteria (Adobe-5 Compliance).
2. **SciA11y system**: PDF-to-HTML pipeline using S2ORC (Grobid-based ML) + DeepFigures + Semantic Scholar API; processes 12M papers, 1.5M open-access renders available at scia11y.org.
3. **Qualitative user study**: Six BLV researchers, three-phase interview (current workflow, prototype interaction, Q&A); five design recommendations extracted.

## Methodology

### Part 1: Accessibility Audit

- **Sample**: Semantic Scholar corpus; papers published 2010–2019 stratified across 19 Microsoft Academic Graph fields of study; 1,058 unique publication venues; median 65 venues per field.
- **Checker**: Adobe Acrobat Pro DC Accessibility Checker, automated via AppleScript (~10s/PDF on MacOS); 1.6% of PDFs failed to generate a report (password-protected or corrupt).
- **Five criteria assessed** (following Lazar et al. [23]):
  - Alt-text: Figures have alternate text
  - Table headers: Tables have headers
  - Tagged PDF: Document tagged for correct reading order
  - Default language: Document has a specified reading language
  - Tab order: Document tagged with correct reading order for tab-key navigation
- **Aggregate metrics**:
  - *Total Compliance*: count of criteria met (0–5)
  - *Normalized Total Compliance*: Total Compliance / 5
  - *Adobe-5 Compliance*: binary — all 5 met (1) or not (0)

### Part 2: SciA11y Pipeline

- S2ORC [24] extracts: title, authors, abstract, section headers, body paragraphs, bibliography, inline citation links, figure/table handles (via Grobid v0.6.0 → JSON)
- DeepFigures [43] extracts: figure images, captions, table images, table captions
- Semantic Scholar API: supplemental metadata
- HTML construction: h1/h2 header tags, p paragraph tags, figure/figcaption tags; figures inserted immediately after first mention paragraph
- Novel navigational features: table of contents (sections + figures/tables), bidirectional inline citation ↔ reference links ("link to return to Section II"), placeholder text for unextracted equations/figures

### Part 3: HTML Quality Evaluation

- Open-coding on 24 papers to identify facets affecting readability
- Rubric: 11 extraction categories (title, authors, abstract, section headings, body text, figures, tables, equations, bibliography, inline citations, headers/footers/footnotes) — see Table 4
- 385 papers annotated across all fields; inter-annotator agreement computed (Cohen's Kappa categorical, ICC numerical)
- Readability scored: No major problems / Some problems / Lots of problems

### Part 4: User Study

- 6 BLV researchers (2 pilot, 4 main); over-18, screen-reader users who read >5 papers/year
- 75-minute sessions: Phase I (current workflow + challenges), Phase II (prototype interaction), Phase III (Q&A)
- Grounded theory: open coding → axial coding → themes
- Participants used: NVDA, JAWS, VoiceOver, Microsoft Narrator, braille displays, InftyReader, Mac Magnifying Glass

## Key Data: Accessibility Compliance Rates

| Criterion | CHI 2010 [23] | Ours-CHI 2010 | Ours-All (11,397) |
|-----------|---------------|---------------|-------------------|
| Alt-text | 3.6% | 4.0% | 7.5% |
| Table headers | 0.7% | 1.0% | 13.3% |
| Tagged PDF | 6.3% | 7.4% | 13.4% |
| Default language | 2.3% | 3.0% | 17.2% |
| Tab order | 0.3% | 1.0% | 9.3% |
| **Adobe-5 Compliance** | — | — | **2.4%** |

- 8,519 of 11,397 PDFs (74.7%) meet **zero** criteria
- Only 854 PDFs (7.5%) have alt-text for figures — the only criterion requiring explicit author action
- Alt-text compliance: lowest of all five, stable at 5–10% and not improving over the decade

## Key Data: Compliance by Field of Study (Adobe-5)

Highest: Philosophy (6.3%), Art (6.2%), Business (5.7%), Psychology (5.7%), History (5.3%)
Lowest: Geology (0.2%), Mathematics (0.3%), Biology (0.6%)

Correlation with Microsoft Word usage (r = 0.89, p < 0.001): fields that use Word more tend to produce more accessible PDFs.

## Key Data: Typesetting Software vs. Compliance

| Software | Count (%) | Compliance |
|----------|-----------|------------|
| Adobe InDesign | 1591 (14.0%) | Moderate-high |
| LaTeX | 1431 (12.6%) | Low |
| Arbortext APP | 1374 (12.1%) | Low |
| Microsoft Word | 1318 (11.6%) | Highest |
| Printer | 1021 (9.0%) | Very low |

ANOVA: F = 2587.1 (p < 0.001); Kruskal-Wallace H = 4422.0 (p < 0.001). Microsoft Word produces significantly more accessible PDFs than other software. LaTeX produces among the lowest compliance.

## Key Data: SciA11y HTML Render Quality (385 papers)

- 55% have **no major problems** impacting readability
- 32% have **some problems**
- 13% have **lots of problems**
- Combined: 87% have no or only some readability issues
- Most problematic extraction failures: missed/incorrect section headings (disrupts navigation trust); headers/footers mixed into body text

## Key Data: User Study Results

| Participant | Current Pipeline Difficulty | HTML Render Difficulty | Would use |
|-------------|----------------------------|------------------------|-----------|
| P1 (Pilot) | 4.0 | 4.0 (0.0) | Yes |
| P2 (Pilot, low vision) | 2.0 | 4.0 (−2.0) | Yes |
| P3 (Main) | 3.0 | 2.0 (+1.0) | Yes |
| P4 (Main) | 4.0 | 1.0 (+3.0) | Yes |
| P5 (Main) | 4.0 | 3.0 (+1.0) | Yes* |
| P6 (Main) | 4.0 | 3.5 (+0.5) | Yes |

Scale: 1 = very easy, 5 = very difficult. Median improvement: 0.75 points. All participants would use system. *P5's response contingent on heading extraction improvements.

## Design Recommendations (Section 6.3)

Five recommendations for accessible paper reading systems:

1. **Document structure should match the mental model of the user**: Hierarchical headings (h1–h6), correct reading order (title → authors → abstract → introduction → ... → references), remove interjections (headers, footers, footnotes) from body text flow.

2. **Objects should be tagged appropriately**: Headings as headings, figures as figures (not inline images), tables as tables, lists as ul/ol. Proper tagging enables screen reader shortcut navigation to specific object types.

3. **System should act as external memory for the user**: Bidirectional in-document links (inline citation → reference → back to citation location); bookmarking; table of contents with figures/tables. Visual layout provides external memory to sighted users; the system must replicate this for BLV users.

4. **Indicate known missing data and potential errors**: When extraction fails, insert explicit placeholder ("Figure 2. Not extracted; please refer to original document") rather than silently skipping. Builds user trust; users prefer knowing about failures.

5. **Reduce verbosity**: Remove unnecessary text around links; minimize keystrokes for navigation. Extra commas and whitespace that are invisible to sighted users add overhead for screen reader users.

## Implementation Details

### SciA11y Pipeline Components

- **S2ORC** (Lo et al., 2020): PDF → structured JSON using Grobid 0.6.0. Output: title, authors, abstract, section headers, body paragraphs, bibliography entries, inline citation → figure/table handle links.
- **DeepFigures** (Siegel et al., 2018): Computer vision model extracts figure/table images and their captions.
- **Custom Flask app**: Stitches S2ORC + DeepFigures + Semantic Scholar API output into HTML.
- **Figure placement algorithm**: Figure placed immediately after the paragraph containing the first mention of its handle (e.g., "In Fig. 1, we show..."). If handle not in text order, placed after paragraph 1 then paragraph 2 for later figures.

### Known Limitations of Pipeline

- **Mathematical equations**: Not extracted; display equations replaced with placeholder text "EQUATION (N): Not extracted; please refer to original document." Inline math partially extracted via S2ORC but quality is low.
- **Table content**: Tables extracted as images (not semantic content), table semantic structure not preserved.
- **Author affiliations**: Not surfaced in prototype.
- **Footnotes**: Often mixed into body text (most common extraction error impacting navigation).
- **Section heading errors**: Most impactful error — missed headings mean users cannot navigate between sections; incorrect headings erode trust.
- **Bias toward biomedical/CS domains**: S2ORC and DeepFigures trained primarily on those domains; humanities-adjacent fields (Art, Business, Economics, Environmental science) show lower extraction quality.

### Three Prototype Versions

- v0.1 (P1): basic HTML with title, authors, abstract, body, references, figures in separate section
- v0.2 (P2): added table of contents, placeholders for unextracted items, figures moved inline (at first mention)
- v0.3 (P3-P6): URLs in bibliography correctly extracted, minor fixes

## Figures of Interest

- **Fig. 1 (p. 3)**: Pipeline schematic — raw PDF → S2ORC extracts → DeepFigures extracts → HTML with navigational features. Shows HTML structure with h1, h2, p, figure tags.
- **Fig. 2 (p. 9)**: Distribution of Total Compliance score across 11,397 PDFs — majority (8519) at score 0, long tail toward score 5.
- **Fig. 3 (p. 9)**: Adobe-5 Compliance by field of study — bar chart showing Philosophy highest (6.3%), Geology lowest (0.2%).
- **Fig. 4 (p. 10)**: Accessibility compliance over time 2010–2019 — slow improvements in Tagged PDF, Tab order, Default language; Alt-text flat.
- **Fig. 5 (p. 12)**: Compliance histograms by typesetting software — Microsoft Word clearly superior.
- **Fig. 6 (p. 13)**: Scatter plot of Microsoft Word usage vs. normalized compliance by field (r = 0.89, p < 0.001).
- **Fig. 8 (p. 15)**: Example of extraction success and failure — successfully extracted figure with caption (left); placeholder image for unextracted figure (right); placeholder text for equation (bottom).
- **Fig. 9 (p. 21)**: Evaluation results across document component types — metadata, figures/tables, text elements, bibliography.
- **Fig. 10 (p. 22)**: Overall readability by field of study — Economics and Environmental science have worst parse quality.
- **Fig. 11 (p. 30)**: Five design recommendations diagram (visual summary).
- **Table 4 (p. 18)**: 11 extraction categories with common errors for each.
- **Table 9 (p. 28)**: Positive and negative features identified by user study participants.
- **Table 10 (p. 29)**: Participant difficulty scores (current vs. HTML render) and future usage intent.

## Results Summary

- 97.6% of scientific PDFs fail full accessibility compliance across all fields of study
- Alt-text (requiring author action) is the hardest criterion to meet and is not improving
- Typesetting software is more predictive of compliance than author intent — LaTeX produces inaccessible PDFs despite community guidelines
- SciA11y HTML renders are readable (no/some problems) for 87% of papers
- All 6 BLV study participants said they would use SciA11y in the future
- Most valued features: bidirectional citation links, hierarchical headings, table of contents
- Most critical failure: missed/incorrect section headings (destroys navigation)

## Limitations

1. **Small user study** (n=6): qualitative learnings only; not statistically generalizable
2. **Pipeline imperfect**: equations not extracted; tables semantic-free; high error rate in humanities
3. **Evaluation rubric**: inter-annotator agreement modest for readability score (ICC ~0.55)
4. **Checker accuracy**: Adobe Acrobat Pro checker used throughout; may not catch all accessibility issues
5. **No longitudinal study**: unknown whether BLV users would continue to use SciA11y after initial session
6. **No alt-text generation**: figures extracted as images but not described automatically

## Testable Properties

- Alt-text compliance should be between 5–10% for any large cross-domain PDF corpus sampled after 2010 (observed stable in this range)
- Adobe-5 Compliance (all 5 criteria) should be well below 10% for any random sample of scientific PDFs
- Microsoft Word typeset PDFs should have statistically higher compliance than LaTeX typeset PDFs (ANOVA p < 0.001 established)
- Fields with higher Microsoft Word adoption should show higher mean accessibility compliance (r = 0.89 established)
- An HTML render with no major extraction errors in headings/body text should produce a readability score of "No major problems"
- Bidirectional citation links require: every inline citation maps to a reference entry, and each reference entry provides back-links to the first mention in each citing section

## Relevance to Project

This is the primary empirical foundation for scientific PDF accessibility. It establishes:
- Baseline compliance rates for the field (2.4% full compliance, 7.5% alt-text)
- The five criteria by which PDF accessibility is standardly measured
- That LaTeX — the dominant typesetting tool in CS, physics, and math — produces among the least accessible PDFs
- The SciA11y HTML rendering approach as a practical mitigation strategy
- Five design recommendations that are directly applicable to any accessible document reader system

## Open Questions

- [ ] Can the SciA11y approach be extended to render accessible math (MathML)?
- [ ] Would crowd-sourced alt-text annotation (community pipeline) scale?
- [ ] How do compliance rates differ for papers published after 2021 (with ACM HTML dual-publication widespread)?
- [ ] Can ML classifiers predict extraction quality before surfacing a render to users?

## Related Work Worth Reading

- Lo et al. (2020) — S2ORC: The Semantic Scholar Open Research Corpus [24] — core extraction model used by SciA11y
- Siegel et al. (2018) — DeepFigures [43] — figure/table extraction via neural nets
- Lazar et al. (2017) — CHI/ASSETS accessibility compliance study [23] — prior work this paper replicates and extends
- Brady et al. (2015) — Creating accessible PDFs for conference proceedings [7] — prior CHI/ASSETS analysis
- Nganji (2015) — PDF accessibility in disability journals [33] — non-CS venue analysis
- Nielsen & Kaley (2020) — "PDF: Still Unfit for Human Consumption, 20 Years Later" [34] — argues PDF format is inherently inaccessible
- Rajkumar et al. (2020) — PDF Accessibility of Research Papers: What Tools Are Needed? [38] — HICSS companion

## Collection Cross-References

### Already in Collection
- **Mack_2021_AccessibilityResearchSurvey** — cited implicitly; provides landscape of accessibility research at CHI/ASSETS that Wang et al. sample from

### New Leads (Not Yet in Collection)
- Lazar et al. (2017) "Making the field of computing more inclusive" — Commun. ACM 60 — prior PDF accessibility compliance study, key comparator for Wang et al.'s numbers
- Brady et al. (2015) "Creating accessible PDFs for conference proceedings" — W4A — first CHI/ASSETS compliance analysis, foundational prior work
- Lo et al. (2020) "S2ORC: The Semantic Scholar Open Research Corpus" — ACL 2020 — the NLP pipeline underlying SciA11y
- Nganji (2015) "The Portable Document Format (PDF) accessibility practice of four journal publishers" — Library & Information Science Research — disability journals angle
- Siegel et al. (2018) "Extracting Scientific Figures with Distantly Supervised Neural Networks" — ACM/IEEE JCDL — DeepFigures paper
