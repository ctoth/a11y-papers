# Evaluating the Usability of Automatically Generated Captions for People who are Deaf or Hard of Hearing

**Authors:** Sushant Kafle, Matt Huenerfauth
**Year:** 2017
**Venue:** ACM SIGACCESS Conference on Computers and Accessibility (ASSETS '17)
**DOI/URL:** https://arxiv.org/abs/1712.02033

## One-Sentence Summary

Introduces the ACE (Automated-Caption Evaluation) metric — a replacement for Word Error Rate that predicts DHH users' subjective caption usability by weighting ASR errors based on word predictability (entropy) and semantic distance (word2vec), validated in a 30-participant DHH user study.

## Problem Addressed

Word Error Rate (WER), the dominant ASR evaluation metric, treats all word errors equally. It has no upper bound, penalizes each error identically regardless of whether the error disrupts comprehension, and has been found to correlate poorly with human task performance across multiple ASR applications. For DHH users in particular, some ASR errors are far more comprehension-damaging than others — especially errors on semantically important, low-predictability words — yet WER cannot distinguish them.

## Key Contributions

- The ACE metric: a new DHH-targeted evaluation metric that weighs each ASR error by (a) word predictability (entropy from n-gram language model) and (b) semantic distance (word2vec cosine distance)
- Empirical validation of ACE against WER with 30 DHH participants across 45 sentence pairs (2,700 total responses)
- Evidence that WER-ACE ratio identifies meaningfully different error profiles for identical WER scores
- A time-based word alignment algorithm for mapping ASR hypothesis output to reference text using word-level timestamps

## Methodology

**Training data for language model:** Switchboard, English CALLHOME, and TED-LIUM corpora — 1.9 million unique words from conversational speech dialogs.

**Stimuli generation:** Videos of staged one-on-one business meetings were processed through CMU Sphinx 4 to produce ASR hypotheses. 45 sentences were selected as stimuli pairs — each pair had identical WER (~0.25) but differing ACE scores. One text in each pair was "preferred by WER" (low WER-to-ACE ratio) and the other "preferred by ACE" (high WER-to-ACE ratio).

**Study design:** 30 DHH participants rated each text pair independently on a 10-point usability scale (frown to smiley face). All results collected in person at Rochester Institute of Technology.

**Participants:** Mean age 23.53, SD 4.92; 17 men / 13 women; 14 deaf, 8 Deaf, 8 hard-of-hearing; all regular captioning users.

## Key Equations

**Word Error Rate (baseline):**

$$
WER = \frac{S + D + I}{N}
$$

Where: S = substitutions, D = deletions, I = insertions, N = number of words spoken.

**ACE Error Impact Score (per error):**

$$
I(e_i) = \alpha \cdot E(w_i) + (1 - \alpha) \cdot D(w_i, e_i)
$$

Where:
- $E(w)$ = entropy (unpredictability) of reference word $w$ — higher = harder to predict = more impactful if wrong
- $D(w, e)$ = semantic distance between reference word $w$ and error word $e$ (word2vec)
- $\alpha$ = interpolation weight (tuned to **0.65** via grid search on prior DHH comprehension data)
- $I(e)$ = impact score for error $e$

**Word Entropy (word predictability sub-score):**

$$
E(w) = \sum_{i=0}^{N_c} -P(w_c(i)) \cdot \log(P(w_c(i)))
$$

Where: $N_c = 20$ top-ranked candidates from n-gram model, $P(w_c(i))$ = candidate probability. Higher entropy = more unpredictable word.

**Stupid Back-off scoring (left-context ranking):**

$$
S(w_i | w_{i-k+1}^{i-1}) = \begin{cases} \frac{\text{count}(w_{i-k+1}^i)}{\text{count}(w_{i-k+1}^{i-1})} & \text{if count}(w_{i-k+1}^i) > 0 \\ \lambda \cdot S(w_i | w_{i-k+2}^{i-1}) & \text{otherwise} \end{cases}
$$

Where $\lambda = 0.4$ (recommended value from Brants et al. 2007).

**Final ACE Metric:**

$$
ACE = \frac{\max_{e \in E} I(e)}{\log(N) - \log(n)}
$$

Where: $E$ = set of all errors (substitution, insertion, deletion), $N$ = length of reference text, $n$ = total number of errors. Takes the **maximum** error impact score (not sum or mean) — rationale: a single major error dominates sentence comprehensibility. Denominator gives logarithmic credit for surrounding context (more context = easier recovery) but subtracts for more errors.

## Parameters

| Name | Symbol | Value | Notes |
|------|--------|-------|-------|
| Interpolation weight | α | 0.65 | Tuned via grid search on prior DHH data; favors word predictability over semantic distance |
| Top candidate count | N_c | 20 | Number of n-gram candidates used for entropy calculation |
| Stupid Back-off lambda | λ | 0.4 | Standard value from Brants et al. 2007 |
| Insertion/deletion semantic constant | — | 0.05 | Scales word length to approximate semantic distance for ins/del errors; empirically set on separate dataset |
| n-gram order | n | 1–5 | Bidirectional (left and right context), combined and ranked |
| Target WER for stimuli | — | 0.25–0.30 | Chosen to reflect realistic commercial ASR in workplace noise without headset mic |

## Implementation Details

**Language model:** Train n-gram models (n=1 to 5) bidirectionally on conversational speech corpora (Switchboard, CALLHOME, TED-LIUM). Apply Stupid Back-off for smoothing.

**Word predictability:** For each word, take top 20 candidates from left+right context predictions, compute normalized probabilities, then compute Shannon entropy. Normalize entropy to (0,1) range. For insertion errors (two adjacent reference words responsible), average entropy of adjacent reference words.

**Semantic distance:** Use pre-trained Google word2vec embeddings to compute cosine distance between reference word and error word. For insertions/deletions, use: distance = 0.05 × word_length.

**Time-based alignment:** Standard edit-distance tools (like NIST sclite) cannot correctly align timestamp-bearing ASR output to reference text when multiple reference words map to one hypothesis word. Custom time-based alignment groups errors by word-level timestamps; produces confusion pairs rather than word-by-word alignment.

**Metric formulation choice:** The paper tried Version1_ACE = sum of impact scores / N (like WER). This was rejected because: (1) it ignores cascade effects, (2) the metric is always ≤ WER because N is not the true normalizing constant. The final ACE uses max impact score instead of sum, reflecting intuition that the worst error dominates sentence comprehension.

**Edge cases:**
- max(1, ACE(W)) can cap the metric at 1 if an upper bound is desired
- For multi-sentence texts, the max formulation does not extend cleanly (identified as future work)

## Figures of Interest

- **Table 1 (page 4):** Side-by-side demonstration of ACE vs WER on two ASR hypotheses with identical WER=0.25 but ACE=0.65 (worse) vs ACE=0.28 (better). Key example: "chains" vs "teams" — semantically distant, unpredictable word = high ACE penalty.
- **Figure 2 (page 5):** Visualization of word predictability entropy scores and semantic distance scores for an example sentence. Shows "requested" and "college" as high-entropy (unpredictable) words.
- **Figure 4 (page 7):** Time-based alignment diagram showing how error regions (including one-to-many and many-to-one mappings) are grouped by word timestamps.
- **Figure 6 (page 8):** Per-participant average usability ratings for ACE-preferred vs. non-preferred texts — ACE-preferred texts rated higher by most participants.
- **Figure 7(b) (page 8):** Scatter plot of ACE scores vs. subjective usability ratings — shows clear positive correlation (Spearman ρ = 0.743).

## Results Summary

| Hypothesis | Result | Test | Statistic |
|-----------|--------|------|-----------|
| H1: DHH prefer ACE-preferred texts | Supported | Wilcoxon signed-rank | W=643394, p<0.0001, median diff=2.5 |
| H2a: DHH ratings correlate with ACE | Supported | Spearman correlation | ρ=0.743, p<0.0001 |
| H2b: ACE correlates better than WER | Supported | Fisher r-to-z | z=5.771, p<0.0001; ACE ρ=0.743 vs WER ρ=0.109 |

WER correlated with DHH subjective judgment at only ρ = 0.109 — compared to ACE's ρ = 0.743. WER is essentially uncorrelated with what DHH users actually experience.

## Limitations

- ACE metric takes the max error impact, which does not extend cleanly to multi-sentence texts
- Semantic distance uses word2vec cosine similarity only — does not incorporate sentiment or other semantic features
- Alpha (0.65) was tuned on one prior dataset with 30 DHH participants (ages 20–32); may not generalize
- Only tested for one-on-one workplace meeting context; other captioning domains (classroom, TV) may require different calibration
- Study stimuli used WER range 0.25–0.30; metric behavior at very low or very high WER is untested

## Testable Properties

- ACE and WER should agree when all error impact scores equal 1.0 (WER becomes a special case of the Version1_ACE formulation)
- For a perfect hypothesis text (no errors), ACE = 0 (same as WER = 0)
- ACE score should be inversely correlated with DHH user subjective usability ratings (lower ACE = higher rated captions)
- Word entropy for function words ("is", "to", "the") should be lower than entropy for content words ("college", "requested")
- Semantic distance for minor morphological errors ("requested" → "request") should be lower than for unrelated substitutions ("college" → "launch")
- ACE is always positive; max(1, ACE) provides an upper-bounded variant
- Two texts with identical WER but different ACE should receive meaningfully different user ratings (this is the central empirical claim, confirmed at p<0.0001)

## Relevance to Project

This is the foundational paper for DHH captioning quality measurement. It directly addresses hearing accessibility — a gap identified in the Mack_2021_AccessibilityResearchSurvey, which found DHH papers are only ~11% of accessibility research. The ACE metric provides a concrete, implementable alternative to WER that is grounded in DHH-specific reading behavior (keyword strategy, literacy differences). Any research or system development involving ASR-based captioning for DHH users should use ACE or its successors rather than WER for evaluation.

## Open Questions

- [ ] How does ACE perform on multi-sentence passages — does a max-per-sentence approach aggregate correctly?
- [ ] How should alpha be re-tuned for different DHH populations (children, older adults, different primary languages)?
- [ ] Can sentiment-aware semantic distance improve ACE over word2vec cosine alone?
- [ ] Does the metric generalize to non-English captioning?
- [ ] What ACE threshold corresponds to "minimally acceptable" caption quality for DHH users?

## Related Work Worth Reading

- Kushalnagar, Lasecki, Bigham (2014) — "Accessibility evaluation of classroom captions" [ref 25] — the direct predecessor, covers classroom-specific captioning evaluation
- Kafle & Huenerfauth (2016) [ref 22] — "Effect of speech recognition errors in text understandability for people who are deaf or hard-of-hearing" — the prior dataset used to tune alpha in ACE
- Kawas et al., ASSETS 2016 [ref 23] — "Improving real-time captioning experiences for deaf and hard of hearing students" — real-time classroom captioning system context
- Lasecki & Bigham (2014) [ref 26] — "Real-time captioning with the crowd" — crowd-sourced captioning as alternative/complement to ASR
- Morris, Maier & Green (2004) [ref 32] — "From WER and RIL to MER and WIL" — MER and WIL as alternative WER replacements, context for why ACE improves over these

## Collection Cross-References

### Already in Collection
- **Mack_2021_AccessibilityResearchSurvey** — cited implicitly by context; the survey that identified DHH accessibility as underrepresented (11.3%) in the literature, motivating this paper's acquisition

### New Leads (Not Yet in Collection)
- Kushalnagar, Lasecki, Bigham (2014) — "Accessibility evaluation of classroom captions" — ACM TACCESS — highly relevant foundational DHH captioning paper, cited as [25]
- Kafle & Huenerfauth (2016) — "Effect of speech recognition errors in text understandability for DHH" — SLPAT/Interspeech — the dataset used to tune ACE's alpha parameter
- Kawas et al. (2016) — "Improving real-time captioning experiences for deaf and hard of hearing students" — ASSETS 2016 — real-time captioning system evaluation
- Lasecki & Bigham (2014) — "Real-time captioning with the crowd" — ACM interactions — crowd-sourced captioning architecture
