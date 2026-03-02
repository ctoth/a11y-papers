# Accessible Web Maps for Visually Impaired Users: Recommendations and Example Solutions

**Authors:** Sabine Hennig, Fritz Zobl, Wolfgang W. Wasserburger
**Year:** 2017
**Venue:** Cartographic Perspectives, No. 88, pp. 6-27
**DOI/URL:** 10.14714/cp88.1391

## One-Sentence Summary
Provides differentiated design recommendations for making web maps accessible to three distinct visual impairment user groups (color vision impaired, moderately visually impaired, and severely visually impaired/blind), grounded in empirical questionnaire data from two Austrian projects (AccessibleMap and senTour).

## Problem Addressed
Web maps are increasingly important for spatial orientation and daily life, yet existing web maps rarely meet the needs of visually impaired users. While paper maps have accessible analogues (tactile maps, Braille maps), digital web maps lack specific, actionable design guidance differentiated by type and degree of visual impairment. The paper identifies four barrier categories: inappropriate graphical design, lack of appropriate interaction modes, lack of verbal map content description, and excessive user interface complexity.

## Key Contributions
- Three-tier recommendation framework differentiating requirements for color vision impaired, moderately visually impaired, and severely visually impaired/blind users (Table 7)
- Detailed visual variable recommendations for map features (points, lines, areas, text) in Table 8
- Empirical questionnaire data from 158 visually impaired respondents (AccessibleMap) and 129 respondents (senTour) on preferences and needs
- Analysis of best-practice web map examples (Table 6) with specific implementable components
- Four-concept accessibility framework: accessibility, usability, utility, and compatibility (Table 9)
- Digital and spatial literacy skills taxonomy for visually impaired map users (Table 10)
- Advocacy for participatory design with visually impaired stakeholders throughout development (Table 11)

## Methodology
Mixed methods across two projects:
1. **AccessibleMap** (2011-2013): Urban environment (Vienna, 2nd and 20th districts). Literature review, questionnaire (55 open and closed questions, 158 valid responses from VI users), internet research, analysis of similar systems. Stakeholder: Austrian Association in Support of the Blind and Visually Impaired.
2. **senTour** (2014-2016): Natural site (Gesause National Park, Austria). Two questionnaires (first: 17 open questions to 197 protected area managers, 68 responses; second: 23 open/closed questions to target users, 129 responses). Stakeholder: Austrian National Council of Disabled Persons.
3. **Analysis of Similar Systems (AoSS)**: Evaluation of existing web map applications based on questionnaire and internet research findings, focusing on UI/map design, map content, functionalities, and WCAG 2.0 compliance.

## Key Equations
None (qualitative/design-focused paper).

## Parameters

| Name | Value/Range | Notes |
|------|-------------|-------|
| Font size (text on maps) | 12-18pt | Jeffrey and Fendley 2011; W3C 2008 |
| Color contrast ratio | Per WCAG 2.0 | Between text/background, symbol/background |
| Zoom steps | Pre-defined discrete levels | Tied to keyboard shortcuts |
| Basemap options | Standard, Black & White, per-color-blindness-type | Minimum set for color vision impaired users |
| Direction system | Hour system preferred (49%), letters (24%), number of roads (15%) | From blind user questionnaire (N=59) |
| Crossing description | Letters T/X/Y (30%), angular degree + street names (15%), number of roads (12%) | From blind user questionnaire (N=59) |
| Information amount | 50% prefer brief explanation, 20% detailed, 16% short note | From senTour questionnaire (N=129) |

## Implementation Details

### User Interface Design
- Implement only necessary control elements; remove unnecessary ones
- Group controls with similar focus; avoid too many grouped elements
- Locate same-type controls consistently across views
- Flat, horizontal layout with no dropdowns or nested elements
- Avoid/reduce scrolling; all elements visible without scrolling
- No overlapping of elements
- **Map-specific:** Place interaction tools (zoom, pan, basemap selectors, layer selectors) OUTSIDE the map component, not overlaid on it (Figure 4)

### Map Design (Visual Variables)
**Points:** Simple symbols and glyphs; widely/well-known icons; bright colors with optimized contrast between symbol and background per WCAG 2.0; different colors and icons for different feature categories; minimum acceptable symbol size tested with intended user group.

**Lines:** Not too thin; thickness depends on color use and background contrast; bright colors with optimized contrast; different colors for different line types; different line thickness and patterns (not just color) to represent types.

**Areas:** Dark outlines; bright colors with optimized contrast; patterns in combination with colors to distinguish area types.

**Text:** Black letters on white background (best practice); simple, popular sans-serif typefaces; no underlining or italicizing; only first character capitalized; 12-18pt font size; left-aligned; not overlapping with other features or labels.

### Interaction Modes
**For color vision impaired:** Visual interaction only.
**For moderately visually impaired:** Visual AND auditory interaction.
**For severely visually impaired/blind:** Auditory interaction (mandatory).

**Keyboard accessibility:** Pre-defined discrete zoom and pan steps tied to keyboard shortcuts. Map navigation must work without mouse. Focus indicators and defined navigation order required. Map control elements must be keyboard-operable.

**Assistive technology support:** Screen reader compatibility, voice output, screen magnification, Braille display support. Web maps must be compatible with existing AT.

### Verbal Description of Map Content
**Color vision impaired:** "Nice to have" (optional)
**Moderately visually impaired:** Depending on degree of impairment
**Severely visually impaired/blind:** Mandatory

**Content structure:**
1. Short description: General overview of map content (static, brief text element)
2. Detailed description: Feature-level information accessible via ALT tags, using HTML for screen reader access, ARIA, or separate text-based version
3. Auto-generated descriptions from spatial databases and GIS, updated dynamically when user pans/zooms/changes layers

**Verbal description content:**
- Order of information: Landmarks first, then paths/streets/trails (for cognitive map construction)
- Direction: Hour system (49% preference among blind users), cardinal points, or body-orientation
- Crossings: Described using letters (T-, V-, X-crossing) (30% preference)
- Distance: Both metric and walking time
- Amount: Brief explanations preferred (50%), with option for more detail

### Basemap Strategy
- Provide multiple basemaps: standard, black & white (high contrast), per-color-blindness-type (protanopia, deuteranopia, tritanopia)
- Users should be able to switch between basemaps
- Use ColorBrewer (colorbrewer2.org), Color Oracle (colororacle.org), or W3C Color Contrast Checker for color-safe design

## Figures of Interest
- **Fig 1 (page 9):** Workflow diagram showing the mixed-methods approach across both projects
- **Fig 2 (page 12):** Six charts showing AccessibleMap questionnaire results: device use, internet frequency, visual variable preferences, AT use, direction description preferences, crossing description preferences
- **Fig 3 (page 13):** senTour questionnaire results: information amount preferences and internet use for recreation planning
- **Fig 4 (page 15):** Sketch of accessible web map layout with interaction tools placed outside map component, basemap selectors for color blindness types, discrete zoom controls, and POI icons
- **Fig 5 (page 18):** Two approaches to verbal map description: short vs. detailed, with HTML/ARIA integration

## Results Summary
- 158 valid responses from AccessibleMap questionnaire (63% low vision, 37% severely VI/blind)
- Desktop PCs and laptops dominate device use; severely VI users heavily use screen readers (~80%)
- 77% of respondents want to adjust visual variables in maps themselves
- 49% of blind respondents prefer hour system for directions
- senTour: 73% use internet to get recreation/tourism information; 40% use it "often"
- Only a few specific recommendations exist for accessible web maps despite abundant general accessibility literature
- Best-practice examples (Google Maps, Vienna city map, Bern city map, German Railway, etc.) each implement only partial accessibility features

## Limitations
- Questionnaire respondents are from German-speaking countries (Austria, Germany, Switzerland); cultural specificity acknowledged
- Response rates and sample sizes are moderate (158 and 129)
- The paper provides recommendations but does not validate them through controlled user studies with implemented prototypes
- Best-practice analysis is descriptive, not empirical evaluation
- No automated or systematic WCAG conformance testing of examined web maps
- Rapidly changing technology landscape means specific tool recommendations may become outdated

## Testable Properties
- A web map claiming accessibility must support keyboard-only navigation for all core functions (pan, zoom, layer selection, feature selection)
- Map interaction tools must be located outside the map component (not overlaid)
- Color contrast between text and background, and between symbols and background, must meet WCAG 2.0 contrast ratios
- Font size for map text must be at least 12pt
- Multiple basemap options must be available (minimum: standard and black & white)
- Verbal descriptions must be provided for severely visually impaired/blind users (mandatory, not optional)
- All map control elements must have focus indicators and be in a defined tab order

## Relevance to Project
Directly relevant to the visual impairment and web standards topic areas. Provides the most detailed accessible web map design recommendations found in the collection, differentiated by impairment type. Connects to Biggs_2025_MapEquivalentPurpose (which evaluates text map representations for WCAG equivalence) and to broader web accessibility evaluation work. The four-concept framework (accessibility + usability + utility + compatibility) from Table 9 aligns with Newell_2000_UserSensitiveInclusiveDesign's argument that accessibility alone is insufficient. The participatory design emphasis connects to Mankoff_2010_DisabilityStudiesCriticalInquiry's methodological critique.

## Open Questions
- [ ] How do these recommendations translate to mobile/touch interfaces (paper focuses on desktop)?
- [ ] What is the minimum viable set of basemaps for color vision accessibility?
- [ ] How should auto-generated verbal descriptions handle complex map features (multi-story buildings, underground transit)?
- [ ] Has the AccessibleMap or senTour prototype been evaluated in controlled user studies since this publication?
- [ ] How do these recommendations interact with modern mapping frameworks (Mapbox GL JS, Leaflet, OpenLayers)?

## Related Work Worth Reading
- Höckner et al. (2012) - AccessibleMap: Web-Based City Maps for Blind and Visually Impaired (precursor project paper)
- Brock and Jouffrais (2015) - Interactive Audio-tactile Maps for Visually Impaired People (SIGACCESS)
- Call-Jimenz and Lujan-Mora (2016) - Web Accessibility Barriers in Geographic Maps
- Zeng and Weber (2010/2011/2012a/2012b) - Series on audio-haptic browser and tactile maps for VI
- Jenny and Kelso (2007) - Color Design for the Color Vision Impaired (Cartographic Perspectives)

## Collection Cross-References

### Already in Collection
- **Biggs_2025_MapEquivalentPurpose** - Evaluates text map representations for WCAG SC 1.1.1 equivalence; Hennig's verbal description recommendations are the design-side complement to Biggs's evaluation framework
- **Newell_2000_UserSensitiveInclusiveDesign** - Hennig's four-concept framework (accessibility, usability, utility, compatibility) independently arrives at the same conclusion that accessibility alone is insufficient
- **Mankoff_2010_DisabilityStudiesCriticalInquiry** - Hennig's emphasis on participatory design with VI stakeholders throughout development aligns with Mankoff's advocacy for disabled co-researchers
- **Lazar_2007_ScreenReaderFrustration** - Hennig's keyboard accessibility and screen reader compatibility recommendations directly address the frustration categories Lazar documented
- **Shneiderman_2000_UniversalUsability** - Hennig's work demonstrates the technology variety challenge (web maps must work across AT configurations) and user diversity challenge (three distinct VI user groups need different solutions)
- **Asakawa_2005_BlindWebBrowsing** - Hennig's mandatory verbal description for blind users and AT compatibility requirements connect to Asakawa's compliance-vs-usability gap

### New Leads (Not Yet in Collection)
- Call-Jimenz and Lujan-Mora (2016) - "Web Accessibility Barriers in Geographic Maps" - directly quantifies the barriers Hennig addresses
- Jenny and Kelso (2007) - "Color Design for the Color Vision Impaired" in Cartographic Perspectives - foundational for the color-specific map recommendations
- Brock and Jouffrais (2015) - Interactive Audio-tactile Maps for Visually Impaired People - SIGACCESS paper on alternative map modalities
- Zeng and Weber (2010) - Audio-Haptic Browser for GIS - multimodal map access for VI users
