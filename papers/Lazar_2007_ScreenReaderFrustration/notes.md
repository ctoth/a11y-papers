# What Frustrates Screen Reader Users on the Web: A Study of 100 Blind Users

**Authors:** Jonathan Lazar, Aaron Allen, Jason Kleinman, Chris Malarkey
**Year:** 2007
**Venue:** International Journal of Human-Computer Interaction, 22(3), 247–269
**DOI:** 10.1080/10447310709336964

## One-Sentence Summary

An empirical study of 100 blind screen reader users who used time diaries to record 308 frustrating web experiences, quantifying cause frequencies, emotional responses, and time lost — providing a ranked, actionable list of accessibility failures for web developers and screen reader implementors.

## Problem Addressed

Prior frustration research focused on sighted student and workplace users. No previous studies had systematically documented and measured the frustrations that blind users face when browsing the Web using screen readers, or quantified how much time those frustrations consume.

## Key Contributions

- First large-scale empirical diary study of blind user frustration during Web use
- Ranked taxonomy of frustration causes by frequency (304 coded occurrences)
- Time-lost metric: blind users lost an average of **30.4%** of computer session time to frustrating situations (vs. 38.9% students, 42.7% workplace users in prior studies)
- Behavioral finding: blind users more likely to seek workarounds than reboot/restart — contrasting with sighted user behavior
- Emotional finding: blind users felt "helpless" (82 instances) and "determined to fix it" (81) more than angry at themselves (19)

## Methodology

**Data collection method:** Modified time diary (electronic RTF forms — not Web-based, to avoid circular dependency; not Word/forms due to screen reader crashes)

**Participant recruitment:** National Federation of the Blind Convention, Atlanta, July 2004; mail/email follow-up September 2004 – May 2005

**Sample:** 100 blind users (61 female, 39 male); avg age 43.37 years (SD=12.5); avg 8.06 years Web experience; avg 31.34 hr/week on computer

**Screen readers used:** JAWS (84 participants), Window-Eyes (12), other (4)

**OS:** Windows XP dominant (60), Windows 98 (22), Windows 2000 (15)

**Total frustrating experiences recorded:** 308 (avg 3.08 per person)

**Content analysis:** Five researchers coded qualitative diary entries; ambiguous entries coded "other"

**Time formula:**
$$
\text{Percent Time Lost} = \frac{MS + MR}{MT}
$$
Where: MS = minutes spent solving the problem, MR = minutes spent recovering lost work, MT = total minutes on computer. Outliers (>100%) excluded; n=90 for time analysis.

## Key Data: Causes of Frustration (Table 4, n=304 coded)

| Category | Sub-cause | Count |
|----------|-----------|-------|
| Layout | Page layout causing confusing SR feedback | **36** |
| Failures | Conflict between screen reader and application | **28** |
| Forms | Poorly designed/unlabeled form | **23** |
| Alt Text | No alt text for pictures | 18 |
| Links | Misleading links | 15 |
| Plug-ins | Inaccessible PDF | 15 |
| Failures | Screen reader crash | 15 |
| Links | Misleading links (tie with above) | 15 |
| Alt Text | Nondescriptive alt text | 10 |
| Plug-ins | Inaccessible Flash | 12 |
| Plug-ins | Slow web site download | 7 |
| Failures | 404-file not found | 6 |
| Navigation | Auto-refresh causes SR to continually restart | 5 |
| Alt Text | No alt text for reg-required pictures | 5 |
| Links | Link not working | 3 |
| Other | — | 49 |
| **Total** | | **304** |

**Top 5 causes (from abstract):**
1. Page layout causing confusing screen reader feedback (36 occurrences)
2. Conflict between screen reader and application (28)
3. Poorly designed/unlabeled forms (23)
4. No alt text for pictures (18)
5. Three-way tie: Misleading links / Inaccessible PDF / Screen reader crash (15 each)

## Key Data: User Responses to Frustration (Table 5)

| Response | n |
|----------|---|
| Unable to solve it | 110 |
| Knew how to solve (happened before) | 54 |
| Ignored or found alternative | 48 |
| Figured out fix without help | 39 |
| Asked someone for help | 32 |
| Tried again | 18 |
| Rebooted | 15 |
| Restarted the program | 7 |

Note: Blind users much less likely to reboot/restart (15+7=22) compared to visual users in prior studies, where restart/reboot was the most common response.

## Key Data: Frequency of Frustrating Experiences (Table 6)

| Frequency | n |
|-----------|---|
| First time it happened | 77 |
| Several times a week | 51 |
| More than once a day | 43 |
| Several times a month | 36 |
| Several times a year | 31 |
| Once a week | 29 |
| Once a month | 21 |
| One time a day | 10 |

## Key Data: Emotional Response (Table 7)

| Feeling | n |
|---------|---|
| Helpless | 82 |
| Determined to fix it | 81 |
| Other | 91 |
| Angry at the computer | 55 |
| Neutral | 36 |
| Angry at myself | 19 |

## Key Data: Frustration Level (Table 8, scale 1–9)

Average frustration level: **6.71** (SD=2.08) — very high. Scale: 1=not very frustrating, 9=very frustrating.

## Implementation Details

### For Web Developers (fixable with existing knowledge)
- **Forms:** Every form field must have a programmatic label — not "field3" but a descriptive name matching the field's purpose. Screen readers read labels in list mode.
- **Alt text:** Images must have meaningful alt text. Registration CAPTCHAs that require seeing text in an image must provide an audio alternative.
- **Links:** Link text must be meaningful out of context — blind users frequently navigate via links list, without surrounding text context. Avoid "click here," "this link," "take me there."
- **Skip navigation:** Provide a "skip to main content" link before navigation blocks so users don't rehear the nav every page load (Fig. 1 demonstrates).
- **Frames:** Name frames descriptively — "main content," "navigation," "search" not "left frame," "top frame."
- **Auto-refresh:** Avoid or provide user control. Auto-refresh resets screen reader position to top of page, forcing re-read.
- **Page layout:** Tables and frames used for visual layout cause screen readers to read content out of logical sequence. Use CSS for layout. Test by linearizing page (read left-to-right, top-to-bottom without visual grouping cues).
- **Pop-ups:** Pop-up boxes cause screen readers to reset to top of triggering page. Avoid where possible.
- **PDF:** Old PDFs (created before newer Acrobat) may be inaccessible. Re-create or tag PDFs with current Acrobat. Alternative HTML version is ideal.

### For Screen Reader Developers (technically complex)
- Reduce crash frequency — 15 crash events in this study
- Improve application conflict handling — 28 conflict events, the second-most common frustration
- Better testing with diverse applications before release

### Design/Testing Protocol
- Experience your own pages with a screen reader in linear reading mode (top-to-bottom, no visual layout cues)
- Card sorting and paper prototyping sufficient to fix labeling problems (Nielsen, 1994)
- Involve blind users early in design process

## Figures of Interest

- **Fig. 1 (page 261):** Screenshot demonstrating skip navigation — shows how a "skip navigation" link appears only to screen reader users, allowing them to bypass repeated navigation links

## Results Summary

- 30.4% of session time lost to frustrating experiences (calculated as (MS+MR)/MT, averaged per user, outliers excluded)
- Average 3.08 frustrating experiences per 100 participants during one session
- Most frustrations are usability problems (fixable by web developers), not technical failures
- Technical failures (SR crashes, SR-application conflicts) are more difficult and require screen reader developer action
- Blind users more resilient: they look for workarounds rather than restarting

## Limitations

- Participants are NFB convention attendees — likely more technically skilled, more advocacy-oriented than average blind Web users
- Data collection window: September 2004 – May 2005 (pre-AJAX era; technologies have changed significantly)
- Self-reported data; cannot determine how training type affected frustration (confounded)
- 10 users reported >100% time lost (excluded as outliers)
- Small word count for "other" category (49/304 = 16%) suggests good coverage but some residual ambiguity
- No specific task assigned — "browse the Web" — so site types vary

## Testable Properties

- A web page with all form fields labeled, all images with meaningful alt text, all links with descriptive text, no auto-refresh, and linearizable layout should produce zero frustrations in categories 1–4 from Table 4
- Screen reader crash rate should be inversely related to pre-release testing breadth with diverse web applications
- Time lost metric must satisfy: Percent Time Lost = (MS + MR) / MT, where each component is non-negative and MT > 0
- User frustration level (1–9 scale) correlates inversely with ability to solve the problem (unsolvable experiences = higher frustration)

## Relevance to Project

This is the foundational empirical study establishing what blind screen reader users actually find frustrating on the Web. It provides:
- A ranked, frequency-weighted list of accessibility failures that is the factual baseline for any screen reader research in this collection
- The 30.4% time-lost statistic — the most-cited quantitative finding in AT accessibility research
- A behavioral profile of blind user coping strategies that informs how to design for resilience
- Evidence that many accessibility failures are easy to fix (labeling, alt text, layout) and don't require advanced technical knowledge

## Open Questions

- [ ] How have these patterns changed post-AJAX, post-WAI-ARIA (2007 study predates ARIA)?
- [ ] Is the 30.4% time-lost figure still accurate for modern screen reader + browser combinations?
- [ ] Do NVDA/VoiceOver/TalkBack users show different frustration patterns than JAWS users (84% JAWS in this study)?
- [ ] Does the behavior pattern (seek workaround vs. reboot) hold for mobile screen reader use?

## Related Work Worth Reading

- Ceaparu et al. (2004) — Determining Causes and Severity of End-User Frustration (IJHCI, 17, 333–356) — the prior methodology this study adapts
- Lazar, Jones, & Shneiderman (2006) — Workplace user frustration study (Behaviour and Information Technology, 25, 239–251) — the comparative baseline
- Zajicek, Powell, & Reeves (1998) — BrookesTalk integrated screen reader/Web browser (ASSETS 1998) — cited as alternative screen reader approach
- Shneiderman (2000) — Universal usability framework (CACM, 43, 84–91)
- Hackett, Parmento, & Zeng (2004) — Web accessibility over time study (ACM ASSETS 2004)

## Collection Cross-References

### Already in Collection
- **Mack_2021_AccessibilityResearchSurvey** — This paper is a foundational study that the Mack survey's overview of blind/low-vision accessibility research encompasses; the Mack survey notes that blind/low-vision users dominate accessibility research (43.5% of papers), consistent with the prominence of the Lazar et al. study.

### New Leads (Not Yet in Collection)
- Ceaparu et al. (2004) — "Determining Causes and Severity of End-User Frustration" — IJHCI — foundational methodology paper this study directly extends
- Lazar, Jones, Hackley & Shneiderman (2006) — "Severity and impact of computer user frustration" — Interacting with Computers — parallel workplace frustration study
- Hackett, Parmento & Zeng (2004) — "Accessibility of Internet Websites through time" — ACM ASSETS 2004 — longitudinal accessibility measurement
- Zajicek, Powell & Reeves (1998) — BrookesTalk — "A Web navigation tool for the blind" — ASSETS 1998 — early integrated SR/browser work
- Trewin & Pain (1999) — "Keyboard and mouse errors due to motor disabilities" — IJHCS — AT input errors study

---

**See also:** Asakawa_2005_BlindWebBrowsing — Asakawa (2005) provides the historical context and tool-level analysis that precedes this work: the paper identifies broken skip-links and inappropriate ALT texts as specific failure modes (with longitudinal data and four code-level error patterns), and argues that sighted developers need to experience blind browsing to produce truly usable pages. The two papers together document the compliance-vs-usability gap from the tooling side (Asakawa) and the user experience side (Lazar et al.).
