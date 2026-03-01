# FigurA11y: AI Assistance for Writing Scientific Alt Text

**Authors:** Nikhil Singh, Lucy Lu Wang, Jonathan Bragg
**Year:** 2024
**Venue:** IUI 2024 (29th International Conference on Intelligent User Interfaces), March 18–21, Greenville, SC, USA
**DOI/URL:** https://dl.acm.org/doi/10.1145/3640543.3645212
**PDF:** https://llwang.net/assets/pdf/2024_singh_figura11y_iui.pdf
**Code:** https://github.com/allenai/figura11y

## One-Sentence Summary
FigurA11y is a human-AI collaborative system that uses GPT-4 conditioned on extracted figure metadata to generate draft alt text and interactive suggestions for scientific figures, validated in a within-subjects study (N=14) showing it enables efficient, descriptive alt text authoring without increased cognitive load.

## Problem Addressed
Alt text for scientific figures is nearly universally absent or inadequate (only 4.6% of HCI/Accessibility paper figures had valid alt text; essentially 0% in leading biomedical journals). Authors face three compound challenges: (1) figures are information-dense and visually complex, (2) accurate description requires deep domain knowledge that crowd-workers and automated systems lack, (3) fully automated approaches error-prone and constrained to specific figure types (plots, natural images) — leaving open-domain scientific figures (diagrams, multi-part composites) unserved.

## Key Contributions

1. **Formative study (N=6)** — technology probe with early prototype (text continuations + Q&A pairs); revealed needs for (DG1) more guidance during drafting and (DG2) increased control over where/how much text generation occurs.

2. **Automated LLM pipeline** — training-free, data-free, generalizes to arbitrary figure types. Extracts figure metadata (caption, mentioning paragraphs, OCR text via EasyOCR, data table for plots) and assembles a structured knowledge-base prompt for GPT-4. Incorporates DIAGRAM Center + SIGACCESS accessibility guidelines organized by figure type, including Lundgard & Satyanarayan's four-level semantic model (first three levels only — fourth requires too much exogenous context).

3. **Two system versions compared:**
   - **Draft+Revise (base):** Pre-generated full draft + extracted metadata + figure-type-specific guidelines
   - **Interactive Assistance (full):** Adds two features:
     - **Generate at Cursor** — on-demand GPT-4 text continuation/infilling at user's cursor position
     - **Potential User Questions** — auto-generated questions identifying ambiguous figure aspects + suggested answers, to prompt authors to address coverage gaps

4. **Within-subjects user study (N=14)** — authors described their own figures from their own papers, across diverse figure types and fields; most realistic and general AI-assisted alt text authoring study to date.

## Methodology

### Pipeline Architecture

```
Paper PDF upload
    → PDFFigures 2.0 [6] — figure extraction
    → GROBID [28] — mentioning paragraph extraction
    → EasyOCR — figure text extraction (OCR)
    → Layout-aware data table extraction (for plots)
    → Figure type classification (DocFigure [19])
    → Guideline selection (by figure type)
    → GPT-4 — draft generation / interactive suggestions
```

### Prompt Structure (Appendix B)
Three-part prompt:
1. **Instruction Prompt** — task-specific instruction (see variants below)
2. **Metadata Prompt** — assembled knowledge base:
   ```
   ---CAPTION <Caption Text>
   ---FIGURE MENTIONS FROM PAPER <Mentioning Paragraphs>
   ---OCR TEXT RECOGNIZED FROM FIGURE (MAY CONTAIN ERRORS) <OCR Text>
   ---DATA TABLE EXTRACTED FROM FIGURE (MAY CONTAIN ERRORS) <Data Table>
   ---Please refer to the following guidelines: <Selected Guidelines>
   ---
   ```
3. **Description Content** — existing partial description (for continuation/infilling)

### Instruction Prompt Variants

**Initial High-Level Summary (Generate at Cursor — start):**
> "Your goal is to assist in writing an alt text description of a figure that is as informative and accessible as possible, based on metadata provided to you. Some of this data is automatically extracted from the figure, and may contain errors. Infer as much detail as possible from the information given. Respond with only a brief and high-level overview (1-2 sentences), with no additional content. In your response, do not explicitly refer to the metadata (such as 'caption' or 'OCR text')."

**Text Continuation/Infilling (Generate at Cursor — mid-description):**
> "Respond with only a continuation of the given description itself (1-4 sentences), with no additional content. Add as much detail as possible. You may also be given a DESCRIPTION CONTEXT, which contains text after your response. In this case, provide text that bridges the gap between the description, and additional text the user has already written."

**Full Draft (pre-generation):**
> "Respond with a full description of the figure, with no additional content."

**Potential User Questions:**
> "What visual aspects of the figure are unclear from the given alt text description? Ask a series of questions to elicit all the necessary information about the figure to describe these elements. Based on the type of figure, focus on essential visual aspects that someone who cannot see the figure would need to know. Based on the guidelines and metadata you have access to, suggest an answer for each question. Do not repeat any existing questions."

### Prompt Engineering Choices (important for replication)
- Added "Respond with only x" to suppress chat-like responses
- Added instruction + logit biases to prevent explicit metadata references (e.g., "the OCR-extracted text contains...")
- Added "uncertainty prompt" to mitigate metadata extraction errors: acknowledge they may exist, encourage inferring despite errors
- Instruction repeated at end of instruction set to reinforce (reduces metadata reference occurrences further)
- Focus instruction on figure visual metadata, reducing text-derived suggestions that don't describe visual aspects

### Model Selection
Compared GPT-4 vs LLaVA on 5 development set figures:
- GPT-4 produced more descriptive alt text with fewer hallucinations
- LLaVA failed to generate output more often
- **GPT-4 Vision was not available at time of study** — noted as future direction
- Choice acknowledged as revisable with newer vision-language models

### Development Set Construction
- Base: SciCap challenge validation set (figures, captions, mentioning paragraphs)
- Problem: highly skewed distributions (Physics overrepresented, line plots dominant)
- Resampled to third most populous category for type (DocFigure classifier) and field (S2FOS classifier)
- Diversity selection: CLIP embeddings (figures) + SPECTER embeddings (text) + figure type one-hot → submodular facility location (apricot package) → 30 representative figures
- Confirmed low content overlap, visual distinctiveness, field coverage

### Guidelines Integration
- Collected from DIAGRAM Center (http://diagramcenter.org) and SIGACCESS
- Adapted: removed example figure references, removed presentational guidelines (brevity), kept content guidelines only
- Organized as nested list indexed by figure type
- General guidelines for all figures + plot-specific guidelines (Lundgard & Satyanarayan four-level model, levels 1–3)
- Level 4 removed: requires too much exogenous context; first three more consistently useful to end-users

## Parameters

| Name | Value | Notes |
|------|-------|-------|
| Study N (formative) | 6 | Paper authors, varying alt text experience (none to 5+ years) |
| Study N (main) | 14 | Paper authors, own figures, within-subjects |
| Development set size | 30 figures | Submodular diverse subset from SciCap validation |
| OCR tool | EasyOCR | Replaced Tesseract after formative study; more accurate |
| Base LLM | GPT-4 | Compared against LLaVA; GPT-4 won on descriptiveness + hallucination rate |
| Figure type classifier | DocFigure | Determines guideline selection |
| Field classifier | S2FOS | Used for development set resampling |
| Draft length | Full description | No explicit length constraint in full draft prompt |
| Text continuation length | 1-4 sentences | Per prompt instruction |
| High-level summary length | 1-2 sentences | Per prompt instruction |
| Summarization | One paragraph | Post-drafting condensation workflow |

## Implementation Details

### System Flow for Authors
1. Author uploads their paper PDF
2. System extracts all figures + metadata automatically
3. For each figure, author can:
   - Review pre-generated full draft (both versions)
   - Review extracted metadata (caption, mentions, OCR, data table) — positioned in main interface for cross-reference
   - Review figure-type-specific guidelines (both versions)
   - (Interactive Assistance only) Use Generate at Cursor: position cursor, request continuation/infilling
   - (Interactive Assistance only) Review Potential User Questions + suggested answers; paste answers into description
4. After drafting: summarization workflow condenses to one paragraph

### Feature: Generate at Cursor
- Detects cursor position in description text
- If at start: generates high-level summary (1-2 sentences)
- If mid-text: generates continuation (1-4 sentences)
- If text exists after cursor: generates infilling (bridges gap to existing following text)
- Grounded in metadata prompt constructed at request time

### Feature: Potential User Questions
- Generated from current partial description + metadata
- Questions identify ambiguous/uncovered visual aspects
- Each question paired with a suggested answer (drawn from metadata)
- Authors can review questions, paste answers, or ignore
- Motivated by: Morash et al.'s queried image description [33], VizWiz Q&A model [3]

### Feature: Prompt Ablation Settings (Interactive Assistance)
- UI menu allows authors to de-select specific metadata components
- Handles cases where OCR is highly erroneous or metadata is irrelevant

### Metadata Visibility Decision
- Formative study: metadata was in a menu (hidden by default)
- Observed: authors constantly referenced metadata for context while writing/evaluating
- Redesign: moved metadata into main interface for continuous cross-reference
- Key UX lesson: externalized knowledge context should be immediately visible

## Figures of Interest

- **Fig 1 (paper p.3):** System architecture diagram showing pipeline from PDF upload through metadata extraction to GPT-4 generation
- **Fig 2 (paper p.4):** Draft+Revise UI screenshot — figure display, metadata panel, guidelines panel, text editor
- **Fig 3 (paper p.5):** Interactive Assistance UI — adds Generate at Cursor buttons and Potential User Questions panel
- **Fig 4 (paper p.8):** Overall participant preference bar chart — Interactive Assistance preferred
- **Fig 5 (paper p.8):** NASA TLX partial raw scores — comparable cognitive load between versions
- **Fig 6 (paper p.9):** Usability/utility agreement ratings — both versions favorable; Interactive Assistance slightly stronger on efficiency
- **Fig 8 (paper p.11):** Event trace examples (P10, P12, P13) — shows diverse authoring strategies
- **Fig 10 (appendix):** Additional features: prompt ablation settings, guideline display (nested by figure type), summarization workflow

## Results Summary

### Quantitative (NASA TLX, N=14, within-subjects)
- Cognitive load (4-item raw NASA TLX, excluding physical demand and performance): **comparable between Draft+Revise and Interactive Assistance**
- No significant increase in workload from added interactive features

### Qualitative Findings
- Generated drafts enabled rapid initiation of descriptions (provided structure/starting point)
- Interactive Assistance prompted more iteration and deviation from generated drafts
- Greater deviation without increased cognitive load or manual effort on average
- Some participants (e.g., P12) were satisfied with pre-generated draft without editing (zero keystrokes in Draft+Revise condition)
- Paste event median higher in Interactive Assistance (5 vs. 2) — accounts for pasting from Potential User Questions answers
- Authors found Potential User Questions useful for testing "how it was coming across" even without directly pasting answers

### Usability Survey Highlights
- Both versions: general tool usability and acceptance comparable
- Interactive Assistance: more participants strongly agreed it improved efficiency and quality
- Both versions: majority would use if available, recommend to colleagues

### Alt Text Quality (descriptiveness)
- System assisted in producing descriptive alt text across diverse figures and domains
- Guidelines + metadata enabled coverage of elements authors wouldn't have considered independently

## Limitations

1. **GPT-4 Vision unavailable at study time** — pure language model approach may miss visual details not captured in OCR/caption metadata
2. **Automated metadata extraction errors** — OCR, data table extraction, figure type classification all error-prone; mitigated with uncertainty prompt and ablation UI
3. **No ground truth dataset** — impossible to train/fine-tune; zero-shot approach throughout
4. **N=14 study** — small sample; participants are paper authors (not BLV readers themselves); within-subjects design may introduce ordering effects despite counterbalancing
5. **No BLV reader validation** — quality assessed by authors + sighted evaluators, not by BLV readers who would actually use the alt text
6. **Figure type constraint** — despite claiming generality, guidelines are still organized by figure type; truly novel figure types may fall outside covered categories
7. **Domain-specific accuracy** — language model lacks visual grounding; generated text may confidently misrepresent complex domain-specific visual elements
8. **Rapid evolution of multimodal models** — GPT-4V and successors may quickly supersede this approach's core design choices

## Testable Properties

- Prompt ablation should always be available when metadata confidence is low (never a hidden setting)
- Generate at Cursor must detect cursor position before sending request (cannot generate without position context)
- Potential User Questions must not repeat questions already present in description
- Full draft generation must not explicitly reference metadata labels ("caption", "OCR text") — logit bias enforced
- Guidelines must be selected per figure type (not applied globally identically to all figures)
- Summarization workflow must produce output shorter than input description

## Relevance to Project

Directly relevant to this collection's focus on visual impairment and automated accessibility tooling. FigurA11y represents the state-of-the-art in human-AI collaborative alt text authoring for the hardest cases (complex open-domain scientific figures). It connects to Wang_2021_ScientificPDFAccessibility (which established that 97.6% of scientific PDFs are inaccessible and identified alt text as a key gap) by providing a concrete, validated solution for the author-side of that problem. The GPT-4 + structured metadata prompt approach is directly implementable for any system that needs to generate alt text for figures extracted from scientific literature.

## Open Questions

- [ ] How does performance degrade with GPT-4V (vision-enabled) input — does visual grounding reduce hallucinations on complex figures?
- [ ] Would BLV reader validation of output quality change conclusions about which features matter most?
- [ ] How do results generalize to non-English papers or figures with non-ASCII text?
- [ ] Does the Potential User Questions feature scale to figures with many ambiguous elements without becoming overwhelming?
- [ ] What is the minimum metadata subset needed for adequate draft quality? (Caption alone? Caption + OCR?)

## Related Work Worth Reading

- **Lundgard & Satyanarayan (2021)** — "Accessible visualization via natural language descriptions: A four-level model of semantic content" — the semantic level framework directly embedded in FigurA11y's guidelines [29]
- **Williams et al. (2022)** — "Toward supporting quality alt text in computing publications" — rubric for alt text descriptiveness; formative interviews revealing author challenges [46]
- **Mack et al. (2021)** — "Designing tools for high-quality alt text authoring" — templates vs. automated options comparison; found templates > auto-generated [30]
- **Chintalapati, Bragg & Wang (2022)** — "A dataset of alt texts from HCI publications" — established 4.6% valid alt text baseline in HCI/Accessibility venues [4]
- **VisText (Tang et al., 2023)** — "A Benchmark for Semantically Rich Chart Captioning" — metadata-only description for plots; finding that visual inputs didn't improve over metadata-only [44]
- **Morash et al. (2015)** — "Guiding novice web workers in making image descriptions using templates" — queried image description (QID) approach that inspired Potential User Questions feature [33]

## Collection Cross-References

### Already in Collection
- **Wang_2021_ScientificPDFAccessibility** — directly extended by FigurA11y: Wang established the scale of scientific PDF inaccessibility (97.6% fail all criteria) and that alt text is absent; FigurA11y addresses the author-side authoring gap Wang identified as a key recommendation.
- **Mack_2021_AccessibilityResearchSurvey** — survey context: FigurA11y represents the emerging AI+accessibility intersection that Mack's survey identified as an underexplored area.

### New Leads (Not Yet in Collection)
- **Lundgard & Satyanarayan (2021)** — "Accessible visualization via natural language descriptions: A four-level model" — IEEE TVCG — foundational semantic model for data visualization descriptions; directly embedded in FigurA11y; would strengthen the visual accessibility section of this collection
- **Williams et al. (2022)** — "Toward supporting quality alt text in computing publications" — W4A 2022 — rubric for alt text quality + author interviews; foundational empirical work on author challenges
- **Chintalapati, Bragg & Wang (2022)** — "A dataset of alt texts from HCI publications" — ASSETS 2022 — established empirical baseline (4.6% valid alt text in HCI papers); direct predecessor to FigurA11y
- **Mack et al. (2021, ASSETS)** — "Designing tools for high-quality alt text authoring" — templates vs. automated comparison; directly cited as motivating FigurA11y's design
