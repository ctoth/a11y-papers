# Paper Processing Report: Kafle_2017_CaptionUsabilityDHH

**Date:** 2026-02-28
**Task:** Retrieve and process a foundational DHH/captioning accessibility paper to fill the collection's hearing-accessibility gap.

## Paper Processed

**Title:** Evaluating the Usability of Automatically Generated Captions for People who are Deaf or Hard of Hearing
**Authors:** Sushant Kafle, Matt Huenerfauth
**Year:** 2017
**Venue:** ACM SIGACCESS Conference on Computers and Accessibility (ASSETS '17)
**Source:** arXiv:1712.02033 (freely available)
**URL:** https://arxiv.org/abs/1712.02033

## Retrieval

- **Status:** Success
- **Source:** arxiv.org (direct PDF download)
- **Path:** `papers/Kafle_2017_CaptionUsabilityDHH/paper.pdf`
- **Size:** 1.97 MB, 8 pages, valid PDF document

## Reading and Annotation

- **Status:** Success (small paper, direct PDF read)
- **notes.md:** Created — full implementation notes including all equations in LaTeX, parameters table, algorithm details, results table, testable properties, cross-references
- **description.md:** Created — three-sentence paragraph
- **abstract.md:** Created — verbatim abstract + interpretation
- **citations.md:** Created — all 43 references extracted, 5 key citations for follow-up identified
- **papers/CLAUDE.md:** Updated with new entry

## Paper Summary

The paper introduces the ACE (Automated-Caption Evaluation) metric as a replacement for Word Error Rate (WER) when evaluating ASR caption quality for DHH users. The central finding: WER correlates with DHH subjective usability ratings at Spearman ρ=0.109 (essentially uncorrelated), while ACE correlates at ρ=0.743 (p<0.0001) across 2,700 responses from 30 participants.

ACE weights each ASR error by:
1. Word predictability (Shannon entropy from bidirectional n-gram model — high entropy = unpredictable = error is more harmful)
2. Semantic distance (word2vec cosine distance — larger deviation = more harmful)

Combined via: `I(e) = 0.65 * E(w) + 0.35 * D(w, e)` with final metric taking the max error impact score (not sum) normalized by log(N) - log(n).

## Gap Filled

This is the first hearing-accessibility paper in the collection. Per Mack_2021_AccessibilityResearchSurvey, DHH papers are only ~11% of accessibility research — this paper directly addresses that underrepresentation.

## Cross-References

- **Already in collection:** Mack_2021_AccessibilityResearchSurvey (motivates DHH gap)
- **New leads identified (4):**
  - Kushalnagar, Lasecki, Bigham (2014) — classroom captions evaluation (ACM TACCESS) — top priority next acquisition
  - Kafle & Huenerfauth (2016) — prior DHH comprehension dataset used to tune ACE's alpha
  - Kawas et al. (2016) — ASSETS 2016 — real-time captioning for DHH students
  - Lasecki & Bigham (2014) — crowd-sourced real-time captioning

## Usefulness Rating: High

**What it provides:**
- The only validated DHH-specific alternative to WER, with full formula and all tuned parameters (alpha=0.65, N_c=20, lambda=0.4, insertion/deletion constant=0.05)
- Concrete evidence that WER is the wrong metric for captioning accessibility research (ρ=0.109 vs ACE's ρ=0.743)
- A replicable evaluation framework (45-sentence stimuli, Wilcoxon + Spearman statistical tests) for any future DHH caption quality study
- Identifies the "keyword strategy" reading behavior in DHH users as the theoretical basis for weighting errors differently

**Actionable next steps:**
- Any future ASR captioning system evaluation in this collection should use ACE instead of WER
- The Kushalnagar et al. 2014 classroom captions paper is the natural next acquisition — it is the most-cited prior work and covers a different captioning context (classroom vs. workplace meeting)
- The alpha=0.65 parameter was tuned on 30 DHH participants aged 20-32; document this limitation when citing ACE for different populations
