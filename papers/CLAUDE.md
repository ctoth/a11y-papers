# Paper References

Quick reference for papers in this collection.

## How to Read Papers

Each paper folder contains:
- **notes.md** - Implementation-focused notes extracted from the paper (START HERE)
- **description.md** - Brief summary of the paper's contribution
- **paper.pdf** or similar - The original PDF
- **pngs/** - Page images for large PDFs (use when PDF is too large to read directly)
- **chunks/** - Text chunks for very large papers

**For implementation work**: Always read notes.md first - it contains the specific values, formulas, and parameters you need.

**For large PDFs**: Use the pngs/ folder. ImageMagick is installed for PDF-to-image conversion if needed.

---


## Mack_2021_AccessibilityResearchSurvey
This paper presents the first comprehensive literature survey of accessibility research at CHI and ASSETS from 1994 to 2019, qualitatively coding 506 papers and quantitatively analyzing 836 papers across 26 years. Key findings include that blind/low-vision users dominate the field (43.5% of papers), sample sizes are small (median 13 disabled participants), and emerging areas like neurodiversity, AR/VR, and game accessibility are growing but underrepresented. As the foundational map of the accessibility research landscape, this paper identifies which disability communities receive the most and least research attention and establishes baseline metrics for study methods, contribution types, and temporal trends essential for prioritizing this collection.

## Lazar_2007_ScreenReaderFrustration
Lazar et al. (2007) present an empirical diary study of 100 blind screen reader users who recorded 308 frustrating web experiences, producing a frequency-ranked taxonomy of accessibility failures with page layout (36 occurrences), screen reader–application conflicts (28), and unlabeled forms (23) as the top three causes. The study found that blind users lost an average of 30.4% of their computer session time to frustrating situations — less than sighted users in prior studies — because blind users tended to seek workarounds rather than rebooting, and the average frustration severity was 6.71 out of 9. For this collection, the paper provides the foundational empirical baseline for screen reader accessibility: a ranked, actionable list of web failures that blind users actually encounter, along with behavioral and emotional data that should inform screen reader design, web authoring guidance, and evaluation method research.

## Krishnavajjala_2024_MotorEase
MotorEase is an automated Android tool (ICSE 2024) that detects four categories of motor-impairment accessibility violations in mobile app UIs — inadequate touch target visual size, missing expanding-section closure mechanisms, inconsistent persistent element placement, and insufficient adjacent icon spacing — using a multimodal combination of computer vision (UIED edge detection, Faster-RCNN icon detection) and uiautomator XML metadata analysis. Evaluated on the MotorCheck benchmark of 555 annotated violations across 1,599 screens from 70 Android apps, MotorEase achieves ~90% average accuracy and ~86% F1, substantially outperforming Google Accessibility Scanner and the Groundhog baseline on their respective violation types. For this collection, it provides concrete, implementable detection thresholds (48px visual touch target, 8px icon gap, 95% MSE persistence similarity), a replicable benchmark construction methodology, and the only known automated approach covering these four previously unaddressed motor-accessibility violation categories.

## Wang_2021_ScientificPDFAccessibility
Wang et al. (2021) audit 11,397 scientific PDFs published 2010–2019 across 19 fields of study and find that only 2.4% satisfy all five standard PDF accessibility criteria, with 74.7% meeting none, establishing that inaccessibility is the near-universal default for scholarly literature. They introduce SciA11y, a machine-learning pipeline (built on S2ORC and DeepFigures) that converts scientific PDFs into accessible HTML with proper heading structure, bidirectional citation links, and a table of contents, processing 12 million papers with 87% of renders having no or only some readability problems, validated through a qualitative user study with six blind and low-vision researchers. For this collection, the paper provides the foundational empirical baseline for scientific PDF accessibility, five concrete design recommendations for accessible document reader systems, and key findings that LaTeX—the dominant tool in CS, physics, and mathematics—produces among the least accessible PDFs.

## Yuan_2011_GameAccessibilitySurvey
This 2011 survey by Yuan, Folmer, and Harris establishes the foundational framework for game accessibility research through a three-step game interaction model (receive stimuli, determine response, provide input) that maps each disability type to exactly the step it disrupts, explaining why fundamentally different solution strategies are needed for visual, hearing, cognitive, and motor impairments. Using 2002 US Census data, the paper estimates that 32.2 million Americans (~11% of the population) have their game-play affected by a disability, with 6.3 million completely excluded, and surveys dozens of accessible games across 8 genres to extract a two-level taxonomy of high- and low-level accessibility strategies. For this collection, it provides the conceptual backbone for all game accessibility work, the definitive strategy taxonomy (Table 7) linking disability-to-step-to-implementation, and population-scale evidence for the scope of game inaccessibility as a research and design problem.

## Gartland_2022_WebAccessibilityCognitive
This 2022 rapid evidence assessment by Gartland et al. synthesizes 45 peer-reviewed studies (2006-2021) on web accessibility for people with cognitive disabilities (PwCDs), finding that text-heavy web content and the exclusion of PwCDs from design processes are the dominant, persistent barriers despite decades of WCAG development. The review identifies three major contribution types across the corpus — barrier documentation, tool development and evaluation, and methodological best practices — and produces a four-quadrant framework (People, Technology, Space, Process) for conducting inclusive research with PwCDs as co-designers rather than test subjects. For this collection, this paper serves as the foundational evidence map for cognitive accessibility, anchoring claims about which WCAG criteria matter for PwCDs, which cognitive disability populations are under-researched, and what research methods produce ecologically valid findings.

