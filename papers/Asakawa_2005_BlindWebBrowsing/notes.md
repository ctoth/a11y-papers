# What's the Web Like If You Can't See It?

**Authors:** Chieko Asakawa
**Year:** 2005
**Venue:** Proceedings of the 2005 International Cross-Disciplinary Workshop on Web Accessibility (W4A), ACM. W4A at WWW2005, 10th May 2005, Chiba, Japan.
**DOI:** 10.1145/1061811.1061813

## One-Sentence Summary

A first-person account by the creator of IBM Home Page Reader documenting the history of nonvisual web browsing from 1994–2005, with longitudinal empirical data showing that compliance-driven improvements (alt text, skip-navigation links) are increasing but frequently broken or meaningless in practice.

## Problem Addressed

Web accessibility guidelines and regulations (WCAG, Section 508) are spreading awareness and producing measurable improvements, but many web developers comply with the letter of the rules without understanding the underlying user need — producing technically compliant pages that are nonetheless unusable by blind people. There was no practical mechanism for sighted developers to experience the blind browsing perspective.

## Key Contributions

1. **Longitudinal empirical dataset (1997–2005):** Tracked alt text coverage and skip-navigation link correctness across 11–12 major news/government sites, showing both progress and persistent failure modes.
2. **Taxonomy of broken skip-navigation links:** Four concrete code-level error patterns found in the wild on well-intentioned accessible sites.
3. **"Disability experience" argument:** Empirical and experiential case that tools enabling sighted developers to simulate blind browsing produce better accessibility outcomes than rule-checklist compliance alone.
4. **aDesigner tool description:** Visualization of voice-browser reaching-time as a design evaluation tool, including heuristic ALT text quality checking.
5. **Historical timeline of nonvisual web access:** Personal chronology from Lynx/1994 through HPR/1997 through IE DOM-based screen readers/2002, contextualized against web platform evolution.

## Methodology

- **Longitudinal site audit (Figure 1):** 11 sites tracked annually 1997–2005. Metrics: average number of images per entry page, average ratio of images missing ALT text.
- **Skip-navigation link audit (Figure 3, 4):** 12 major news sites (6 US, 6 Japan) sampled 2004 and 2005. Reaching-time to main content measured using aDesigner simulation. Figure 4 shows broken vs. correct skip-links at IBM, CNN, Mozilla.org, Whitehouse.gov, Section508.gov, Department of Justice.
- **First-person experiential narrative:** Author is herself blind; experiences with Lynx (1994), SR/2 (1996), and HPR (1997–) are primary sources for the qualitative claims.

## Key Empirical Findings

### Alt Text Coverage (Figure 1, 11 sites, 1997–2005)
| Year | Avg images/page | Images missing ALT | Missing ratio |
|------|----------------|-------------------|---------------|
| 2000 | ~34 | 13.2 | 38% |
| 2001 | ~48 | 9.1 | 19% |
| 2004 | ~80 | ~16 | ~20% |
| 2005 | ~87 | 3.1 | 7% |

- Sharp drop in 2001 attributed to Section 508 taking effect (June 2001): all 5 tested Federal Agency sites achieved 100% ALT coverage.
- 2005 improvement in private sites attributed to one news site going from 27% to 94% ALT coverage.

### Skip-Navigation Link Reaching Time (Figure 3, 12 news sites)
- 2004: Only 2 of 12 sites provided heading tags or skip-navigation links.
- 2005: 8 of 12 sites provided such tags.
- Visual bar chart shows dramatic reduction in reaching time to main content across most sites.

### Broken Skip-Navigation Links (Figure 4, 6 sites, 2004 crawl data)
| Site | Correct/no skip-link | Broken skip-link |
|------|---------------------|-----------------|
| IBM | 981 | 64 |
| CNN | 1071 | 70 |
| Mozilla.org | 380 | 0 |
| Whitehouse.gov | 61 | 1 |
| Section508.gov | 132 | 0 |
| Dept. of Justice | 1110 | 16 |

- IBM site: 6% of skip-navigation links broken (1,000 pages crawled).
- News site: 5% of skip-navigation links broken (1,140 pages crawled).

## Taxonomy of Broken Skip-Navigation Links

Four code-level patterns found in real accessible sites:

1. **Missing destination anchor**
   ```html
   <a href="#content"> skip to main content </a>
   <!-- No anchor named "content" exists in page -->
   ```

2. **Anchor name mismatch**
   ```html
   <a href="#content">skip to main content</a>
   <a name="maincontent">  <!-- "content" ≠ "maincontent" -->
   ```

3. **Wrong HREF (missing #)**
   ```html
   <a href="content"> skip-to-main content </a>
   <!-- Navigates to a different page, not intra-page -->
   ```

4. **Missing readable text**
   ```html
   <a href="#content" alt="skip to main content"></a>
   <!-- ALT on <a> tag doesn't work; no readable text inside tag -->
   ```

## Tool Descriptions

### IBM Home Page Reader (HPR)
- Original purpose: screen reader for blind users.
- Secondary use: disability simulation for sighted web developers.
- Architecture: parses HTML tags directly (not screen text), synchronized with Netscape Navigator / IE DOM API (HPR 3.04).
- Key functions for developers: synchronized speech + text view + graphics view highlighting; keyboard-only navigation via number pad; heading jump (H key); skip-navigation link testing.
- Reveals: URL fragments read aloud when no ALT text on image links; "spacer spacer spacer" repeating noise from decorative images; wrong reading order from layout tables.

### IBM aDesigner
- Purpose: disability simulator for sighted developers; not a screen reader.
- GUI-based, mouse-driven; lower learning curve than HPR.
- Key function: **reaching-time visualization** — background color gradation from light (fast to reach) to black (>90 seconds to reach) across page, calculated by simulating voice browser basic commands.
  - No skip/heading tags → page gradually blacks out.
  - Skip-navigation link present → lighter region at target position.
  - Heading tags present → sky-blue background at headings + lighter overall.
- Heuristic ALT text quality check: warns on "spacer", "image", "click here", recommends null string or space for non-significant images.
- Checks skip-navigation link integrity: broken link → no lighter section in reaching-time view.
- Reference: Takagi et al., ASSETS 2004 [8].

## Historical Timeline: Nonvisual Web Access (Table 1)

| Date | Event |
|------|-------|
| 1993 Mar | Lynx 2.0a released |
| 1993 Apr | Mosaic released |
| Early 1994 | Author's first web access: DOS screen reader + Lynx via telnet |
| Late 1994 | Japanese BBS (Asahi Net) web-to-text conversion service; WWW Consortium created |
| 1994 Dec | Netscape Navigator 1.0 |
| Early 1996 | PAL macro language for IBM SR/2 + Web Explorer (OS/2) |
| Mid-1996 | PAL for Netscape Navigator 2.0 on OS/2 |
| Early 1997 | First standalone "Web Reader" prototype |
| 1997 May | W3C WAI First Technical Meeting |
| 1997 Jul | HPR prototype complete; author buys cake online — first successful e-commerce task |
| 1997 Oct | HPR 1.0 released (Japanese only) |
| 1999 Jan | HPR 2.0 released (first English version) |
| 1999 May | Table navigation interface prototyped |
| 1999 Aug | HPR 2.5 released (7 languages) |
| 2001 Jun | Section 508 takes effect; measurable jump in alt text compliance |
| 2002 Aug | JAWS 4.5 with advanced web navigation |

## Key Design Insight: Compliance vs. Usability

Central argument: checklists catch presence/absence of accessibility features but cannot verify quality or correctness:
- Tools can detect `alt=""` is missing, but cannot reliably assess whether the alt text provided is meaningful.
- Tools cannot (as of 2005) detect whether a skip-navigation link exists without crawling for it.
- Tools cannot detect broken skip-navigation links automatically.
- aDesigner's heuristic ALT checker flags common bad patterns but is acknowledged as heuristic only.

**Key recommendation:** Web developers should experience the blind browsing perspective through tools like HPR or aDesigner, not merely run compliance checkers.

## Figures of Interest

- **Fig 1 (p.3):** Line chart — annual average image count and images-without-ALT for 11 sites, 1997–2005. Shows regulatory inflection points.
- **Fig 2 (p.4):** Side-by-side IBM.com in sighted browser vs. HPR text output — dramatic illustration of linearization.
- **Fig 3 (p.5):** Bar chart — reaching time to main content for 12 news sites, 2004 vs. 2005.
- **Fig 4 (p.6):** Stacked bar chart — correct vs. broken skip-links at 6 accessible sites.
- **Fig 5 (p.7):** aDesigner reaching-time visualization: (a) original, (b) inaccessible, (c) with skip-link, (d) with headings.

## Limitations

- Sample sizes are small: 11–12 sites for longitudinal data; 6 sites for skip-link audit.
- Sites selected are self-described accessible/prominent sites, not representative sample — actual population accessibility likely worse.
- aDesigner's ALT heuristic is explicitly approximate.
- Paper is a keynote address, not a controlled study; empirical data is descriptive.
- Table 1 relies entirely on author's personal experience, which is also a strength (lived expertise).

## Testable Properties

- **Broken skip-link rate:** Even accessibility-conscious sites had 5–6% broken skip-navigation links on crawl (IBM: 64/1045; CNN: 70/1141). Any implementation tracking skip-link correctness should expect non-zero failure rates even on maintained sites.
- **Regulation inflection:** ALT text missing ratio dropped from 38% (2000) to 19% (2001) coinciding with Section 508 effective date — testable hypothesis that regulatory deadlines produce step-change compliance improvements.
- **Null/empty ALT is correct for decorative images:** Per WCAG 1.0, decorative images should use `alt=""` or `alt=" "` so voice browsers skip them. A checker flagging all missing ALT is generating false positives for decorative images.
- **aDesigner reaching-time threshold:** >90 seconds = completely black in visualization. This is a usability threshold for page complexity evaluation.

## Relevance to Project

This paper is the foundational first-person account of screen reader / voice browser interaction with web content, written by the developer of one of the first web-aware screen readers. It provides:
- The primary historical record of nonvisual web access evolution (1994–2005).
- Empirical baseline data on alt text and skip-navigation compliance trends.
- A concrete, lived illustration of the gap between compliance and usability.
- Tool descriptions for HPR and aDesigner that anchor screen reader architecture discussions.
- The "disability experience" argument that predates and motivates later user study methodologies (connects to Lazar_2007_ScreenReaderFrustration).

## Open Questions

- [ ] Were the 11 sites tracked in Figure 1 identified? The paper does not name them (aside from implication that 5 are federal agencies).
- [ ] How does aDesigner's reaching-time calculation model voice browser commands — is the simulation model published?
- [ ] The broken skip-link rate in Figure 4 — does "correct skip-link/no skip-link" conflate two different states? Pages with no skip-link at all vs. correct skip-links are grouped, making the broken rate denominator unclear.
- [ ] Has aDesigner been empirically validated against actual HPR user behavior?

## Related Work Worth Reading

- Takagi, Asakawa, Fukuda, Maeda (ASSETS 2004) — aDesigner paper [8]: full technical description of reaching-time visualization.
- Asakawa & Itoh (ASSETS 1998) — HPR user interface paper [1]: original screen reader architecture.
- Asakawa & Takagi (ASSETS 2000) — Annotation-based transcoding [21]: web page restructuring for nonvisual access.
- Takagi et al. (ASSETS 2002) — Site-wide annotation [22]: systematic page reconstruction for accessibility.

## Collection Cross-References

### Already in Collection
- **Lazar_2007_ScreenReaderFrustration** — Asakawa's paper provides the historical/tooling context that precedes Lazar's empirical frustration diary study; together they form a before/after on the screen reader accessibility problem. Asakawa identifies the failure modes (broken skip-links, bad ALT text); Lazar quantifies how often they cause real-world frustration.
- **Pool_2023_AccessibilityMetatesting** — Asakawa's observation that tools cannot check skip-navigation link existence or quality (2005) is directly addressed 18 years later by Pool's evaluation of multi-tool ensembles. Asakawa identifies the tool gap; Pool maps which tools cover which issues.
- **Martins_2023_LargeScaleWebA11y** — Asakawa's longitudinal 11-site study is the direct precursor to Martins' 2.8M-page audit. Asakawa establishes that regulatory pressure drives compliance; Martins provides population-scale evidence of persistent failure.
- **Wobbrock_2011_AbilityBasedDesign** — Asakawa's "disability experience" argument (developers should experience blind browsing) is an early instance of the Accountability and Transparency principles in Wobbrock's ability-based design framework.

### New Leads (Not Yet in Collection)
- Takagi, Asakawa, Fukuda, Maeda (ASSETS 2004) — "Accessibility Designer: Visualizing Usability for the Blind" — the full technical paper behind aDesigner [8]. High priority: detailed methodology for reaching-time calculation.
- Asakawa & Itoh (ASSETS 1998) — "User Interface of a Home Page Reader" — architectural paper for HPR [1]. Medium priority: screen reader architecture.
- Asakawa & Takagi (ASSETS 2000) — "Annotation-based Transcoding for Nonvisual Web Access" [21]. Medium priority: web transcoding for accessibility.
- Laws & Asakawa (CSUN 1999) — "IBM Home Page Reader: The Voice of the World Wide Web" [13]. Low priority: product description, less technical.
