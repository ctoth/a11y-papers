# Accessibility Metatesting: Comparing Nine Testing Tools

**Authors:** Jonathan Robert Pool
**Year:** 2023
**Venue:** 20th International Web for All Conference (W4A '23), April 30–May 1, 2023, Austin, TX, USA
**DOI/URL:** https://doi.org/10.1145/3587281.3587282 | https://arxiv.org/abs/2304.07591

## One-Sentence Summary
Empirically tested nine automated accessibility tools on 121 web pages and found each tool uniquely discovers issue instances missed by all others, making no subset of tools sufficient — ensemble testing with all nine is substantially more informative than any single tool or subset.

## Problem Addressed
Organizations face an integration cost trade-off when using multiple automated accessibility tools. Prior research established that tools are complementary, but nobody had answered: is there a minimum sufficient subset? This paper asks whether a small tool set makes the others redundant, testing it empirically rather than relying on tool capability documentation.

## Key Contributions
- Empirical comparison of nine integration-friendly automated accessibility tools on a common 121-page corpus
- Pairwise increase tables showing that adding any second tool increases both issue instance counts (13–767%) and unique issue discovery (15–51 additional issues)
- Per-tool specialization inventory: each tool's distinctive issue categories and sole-source issues (issues found by only that tool)
- Issue taxonomy: 1,327 tool tests mapped to 245 distinct accessibility issues aligned to WCAG 2.1
- Practical integration cost enumeration (14 non-trivial engineering tasks for multi-tool ensembles)

## Methodology
- **Corpus:** Judgmental sample of 140 pages relevant to CVS Health (internal/external, own/vendor/competitor); narrowed to 121 publicly reachable, interaction-free pages
- **Tools:** Nine tools meeting criteria: currently maintained, free or nearly free, usable as REST API or NPM package
- **Analysis unit:** "Issue instance" — a specific occurrence of a classified defect on a specific page
- **Issue classification:** 1,327 tool tests mapped to 245 issues (defect types); warnings treated as separate from definitive failures
- **Duplication assumption:** If tool A reports m instances of issue C and tool B reports n > m, A's instances are assumed a subset of B's
- **No false-positive filtering:** Paper deliberately trusts tool claims without human validation; argues false positivity is a judgment, not a fact, and legal context (ADA litigation) makes treating automated reports as presumptively correct a risk-mitigation strategy

## Parameters / Tool Inventory

| Code | Full Name | Creator | Test Count |
|------|-----------|---------|------------|
| alfa | alfa | Siteimprove | 103 |
| axe | axe-core | Deque | 138 |
| continuum | Continuum Community Edition | Level Access | 267 |
| htmlcs | HTML CodeSniffer | Squiz | 98 |
| ibm | Equal Access | IBM | 163 |
| nuVal | Nu Html Checker | W3C | 147 |
| qualWeb | QualWeb | Universidade da Lisboa | 121 |
| tenon | Tenon | Tenon.io | 180 |
| wave | WAVE | WebAIM | 110 |
| **Total** | | | **1,327** |

## Issue Instance Counts (Table 2)

| Tool | Instance Count |
|------|---------------|
| qualWeb | 23,715 |
| axe | 12,364 |
| tenon | 8,328 |
| nuVal | 6,986 |
| htmlcs | 6,329 |
| ibm | 6,242 |
| wave | 6,095 |
| alfa | 5,605 |
| continuum | 3,089 |
| **Total** | **78,753** |

Note: QualWeb reports ~8x more instances than Continuum, but volume does not imply coverage superiority.

## Pairwise Increase in Issue Instance Count (Table 3)

Adding a second tool to a first increases instance count by 13% (Continuum added to QualWeb) to 767% (QualWeb added to Continuum). No tool subsumes any other. Every pair is bidirectionally complementary.

Key cells (1st tool → adding 2nd tool → % increase):
- WAVE + Continuum: +48%
- axe + QualWeb: +188%
- QualWeb is most prolific but adding it to any tool still yields meaningful gain

## Pairwise Increase in Issue Discovery (Table 4)

Adding any second tool discovers 15–51 additional distinct issue types. Minimum gain: +15 issues (adding Tenon to WAVE). Maximum gain: +51 issues (adding Nu Html Checker to QualWeb).

## Per-Tool Specializations (Section 5.3)

Each tool specializes in distinct issue categories:
- **alfa:** font and line sizing; skip-to-content links
- **axe-core:** color contrast; landmark placement
- **Continuum:** landmark purpose; placeholder versus label
- **HTML CodeSniffer:** heading levels; semantic use of elements
- **Equal Access (ibm):** landmark coverage; landmark purpose
- **Nu Html Checker:** control placement; attribute validity
- **QualWeb:** video alternatives; focus indication
- **Tenon:** horizontal scrolling; link purpose
- **WAVE:** label clarity; link purpose

## Sole-Source Issues (Table 5)

Issues found by **only one tool** — 112 total across all tools:

| Tool | Sole-Source Issue Count |
|------|------------------------|
| nuVal | 26 |
| htmlcs | 15 |
| ibm | 15 |
| axe | 12 |
| wave | 12 |
| continuum | 9 |
| alfa | 8 |
| tenon | 8 |
| qualWeb | 7 |
| **Total** | **112** |

Notable examples:
- Only WAVE found instances of pages entirely missing landmarks
- Only axe-core found instances of invisible form-control labels
- HTML CodeSniffer found 108 instances of bad iframe titles; no other tool found more than 27

## Failure Rate

Of 1,089 tool-page test attempts, 49 (4%) failed. Tool failures and negative results are practically equivalent — both mean that issue goes undetected by that tool.

## Integration Cost Enumeration (Section 6)

14 non-trivial engineering tasks for multi-tool ensembles:
1. Integrate tool invocation methods
2. Ensure test isolation
3. Integrate reporting formats
4. Integrate severity and certainty classifications
5. Integrate instance-location identification methods
6. Integrate pre-test browser action methods
7. Reconcile granularity differences in issue classifications
8. Determine which issues should be considered identical
9. Assign levels of trust to tools and their tests
10. Compensate for tool duplicativity when computing scores
11. Gather findings per issue from tool reports
12. Track tool revision history
13. Handle tool disagreements
14. Integrate with custom tests and standards

## Results Summary

- Every pairwise combination: each tool discovers instances the other misses
- No tool makes any other redundant
- All-nine-tool ensemble is substantially more informative than any subset
- Duplication also exists: up to 8 tools discovered the same issue type (e.g., links without accessible names), but even then coverage counts differed (WAVE: 240, Nu Html Checker: 2)
- Tool landscape is volatile: Tenon became unavailable for new subscribers after the study concluded

## Limitations

- Uses a judgmental sample (121 pages from CVS Health's domain of interest), not a random or representative web sample; results may not generalize
- Does not validate true/false positives — trusts tool claims as presumptively correct
- Duplication counting assumes subset relationship when instance counts differ (not verified per-instance)
- Tools evolve rapidly; Tenon exited the market before publication
- Does not measure recall against a ground truth accessibility audit

## Testable Properties

- **Complementarity invariant:** For any two tools A and B in the nine, A will find at least one instance that B misses, and B will find at least one instance that A misses (observed to hold for all 72 pairs)
- **Pairwise gain lower bound:** Adding any second tool to any first increases instance count by at least 13% (empirical lower bound from this sample)
- **Sole-source lower bound:** Every tool has at least 7 issues that only it discovers
- **Failure rate bound:** Tool failure rate is ~4% (49/1,089 attempts); any multi-tool system must handle partial tool failures gracefully
- **Volume ≠ coverage:** The highest-volume tool (qualWeb, 23,715 instances) does not subsume the lowest-volume tool (continuum, 3,089 instances)

## Relevance to Project

This is the foundational empirical paper for automated accessibility evaluation methods. It directly answers "which tool should I use?" with "all of them, and here's the data." For this collection's evaluation methods topic area, it provides:
- The definitive tool roster (nine integration-friendly tools) with their specializations
- Quantitative evidence that single-tool testing is substantially incomplete
- A practical integration cost framework for multi-tool ensemble implementation
- The issue taxonomy (1,327 tests → 245 issues → WCAG 2.1 mapping) as a reference classification

## Open Questions

- [ ] Would results generalize to a random web sample rather than CVS Health's specific domain?
- [ ] What is the actual false-positive rate for each tool? (Paper deliberately excludes this)
- [ ] How does ensemble coverage change over time as tools are updated?
- [ ] Is there a minimum-cost ensemble that approaches all-nine coverage?
- [ ] How do these nine tools compare against LLM-based accessibility checkers (cf. arxiv 2401.16450)?

## Related Work Worth Reading

- Abduganiev (2017) — Eight-tool comparison on 52 pages (Tajikistan/Austria); established complementarity finding
- Pădure and Pribeanu (2020) — Six-tool comparison on Romanian municipal sites; further complementarity evidence
- Kumar, Biswas, and Venkatesh (2021) — Ten-tool comparison on WHO/BBC sites; WCAG principle coverage analysis
- Silva et al. (2019) — Systematic literature mapping of automated tool vs. expert inspection vs. user testing problem types
- Burkard, Zimmermann, and Schwarzer (2021) — Commercial monitoring tool evaluation; fewest-issues tool still found unique violations

## Collection Cross-References

### Already in Collection
(none — no cited papers are currently in this collection)

### New Leads (Not Yet in Collection)
- Silva et al. (2019) — "Types of Problems Encountered by Automated Tool Accessibility Assessments, Expert Inspections and User Testing" — ACM ASSETS 2019 — directly compares automated tools, expert inspection, and user testing; essential complement to Pool's automated-only study
- Kumar, Venkatesh, and Biswas (2021) — "Comparing Ten WCAG Tools for Accessibility Evaluation of Websites" — Technology and Disability — largest tool count in the comparative literature; WCAG principle-level coverage analysis
- Burkard, Zimmermann, and Schwarzer (2021) — "Monitoring Systems for Checking Websites on Accessibility" — Frontiers in Computer Science — commercial tool evaluation, complementarity holds even for paid tools
- Abduganiev (2017) — "Towards Automated Web Accessibility Evaluation: A Comparative Study" — historical baseline for eight-tool comparison; establishes rapid tool turnover problem

### Supersedes or Recontextualizes
(none — no existing collection papers are directly superseded by this work)
