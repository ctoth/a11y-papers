# Ability-Based Design: Concept, Principles and Examples

**Authors:** Jacob O. Wobbrock, Shaun K. Kane, Krzysztof Z. Gajos, Susumu Harada, Jon Froehlich
**Year:** 2011
**Venue:** ACM Transactions on Accessible Computing (TACCESS), Vol. 3, No. 3, Article 9
**DOI/URL:** 10.1145/1952383.1952384 / https://kgajos.seas.harvard.edu/papers/wobbrock11abd.pdf

## One-Sentence Summary

Ability-based design is a principled accessible computing framework that shifts focus from compensating for disability to leveraging the full range of what users *can* do, offering seven concrete design principles organized into Stance, Interface, and System categories.

## Problem Addressed

Accessible computing has consistently centralized *disability* — asking "what disability does a person have?" — rather than *ability* — asking "what can a person do?" This disability-centric orientation leads to add-on assistive technology approaches that burden users with procurement, stigma, cost, and maintenance, and that require users to conform to inflexible systems. Ability-based design reframes the question so systems accommodate users, not the other way around.

## Key Contributions

- A named, principled design framework (ability-based design) that unifies and refocuses prior accessible computing approaches
- Seven ability-based design principles organized into three categories (Stance, Interface, System), each tagged Required / Recommended / Encouraged
- A taxonomy and review of 14 example projects spanning desktop text entry, mouse pointing, mobile devices, and web access — each mapped explicitly to which principles they uphold
- A research agenda identifying open challenges in ability measurement, context sensing, user modeling, and interface adaptation
- The conceptual shift from "design for all" (universal) to "universal application of design-for-one" — personalizing interfaces to individual abilities

## The Seven Principles (Table 1)

### STANCE (Required — must hold for any ability-based design)

**1. Ability**
Designers will focus on ability not *dis*-ability, striving to leverage all that users *can* do.

**2. Accountability**
Designers will respond to poor performance by changing systems, not users, leaving users as they are.

### INTERFACE (Recommended — enhance ability-based designs but not required by all)

**3. Adaptation**
Interfaces may be self-adaptive or user-adaptable to provide the best possible match to users' abilities.

**4. Transparency**
Interfaces may give users awareness of adaptations and the means to inspect, override, discard, revert, store, retrieve, preview, and test those adaptations.

### SYSTEM (Recommended / Encouraged)

**5. Performance**
Systems may regard users' performance, and may monitor, measure, model, or predict that performance. *(Recommended)*

**6. Context**
Systems may proactively sense context and anticipate its effects on users' abilities. *(Recommended)*

**7. Commodity**
Systems may comprise low-cost, inexpensive, readily available commodity hardware and software. *(Encouraged — acknowledges specialized hardware is sometimes warranted)*

**Minimum bar for ability-based design:** Must uphold principles 1 (Ability) and 2 (Accountability).

## Positioning Against Prior Approaches

| Approach | Focus | Key limitation vs. ABD |
|---|---|---|
| Assistive Technology | Add-on between user and system | Burden on user; "separate but equal"; stigma |
| Rehabilitation Engineering | Quantify/measure human performance | Too broad (not computer-specific); custom add-ons |
| Universal Design | One design that works for all (architecture origin) | "One size fits all" ring; scales poorly to individual differences |
| Universal Usability | Widest range of people | Inevitably "one size fits all"; covers gender/age/economics not just disability |
| Design for All (EU) | Barrier-free information society | Asks "what can *everyone* do?" — not what *you* can do |
| UI4All | Unified UI representations mapped to templates | Compatible with ABD when ability informs template mapping |
| Inclusive Design (UK) | Counter "design exclusion" | Relies on designer awareness, doesn't scale; ABD uses system sensing |
| Extra-Ordinary HCI | All users have abilities; context affects them | Provides conceptual framing but doesn't quantify or prescribe |

**Key distinction:** Ability-based design = "universal application of design-for-one" (Harper 2007 term). Universal design = one design for everyone. ABD = individualized design for each person's actual abilities.

## Key Insight: Adaptivity vs. Adaptability

- **Adaptivity** (system changes itself): Low adaptivity = immediate local changes (e.g., Angle Mouse gain); High adaptivity = lasting global model (e.g., SUPPLE)
- **Adaptability** (user changes system): Customizable settings; WebAnywhere is a strong example
- ABD does not *require* adaptation — but adaptation removes the need for assistive add-ons by making the burden of accommodation rest with the system

## Situationally-Induced Impairments and Disabilities (SIIDs)

Context temporarily reduces abilities in ways similar to health-related impairments. Examples:
- Gloves ("fat fingers"), walking/vibration, rain/cold, glare/darkness, distraction, confined spaces
- ABD applies to situational impairments too — not only permanent disability
- Designs that help disabled users often help temporarily situationally-impaired users (e.g., walking user interfaces help both motor-impaired users and walking users)

## Example Projects and Their Principles (Table 2)

### Desktop Text Entry
| Project | User Group | Principles Upheld |
|---|---|---|
| Dynamic Keyboard Model (Trewin & Pain 1997) | Motor-impaired typists | adaptation, transparency, performance, commodity |
| Invisible Keyguard (Trewin 2002) | Motor-impaired typists | adaptation, performance, commodity |
| Input Device Agent (Koester et al. 2005, 2007a) | Motor-impaired keyboard+mouse users | adaptation, performance, commodity |
| TrueKeys (Kane et al. 2008b) | Motor-impaired typists | transparency, performance, commodity |
| Trackball EdgeWrite (Wobbrock & Myers 2006–2007) | SCI users | adaptation, transparency, performance, commodity |

### Mouse Pointing
| Project | User Group | Principles Upheld |
|---|---|---|
| Steady Clicks (Trewin et al. 2006) | Motor-impaired | performance, commodity |
| Angle Mouse (Wobbrock et al. 2009) | Motor-impaired | adaptation, transparency, performance, commodity |
| SUPPLE (Gajos et al. 2007–2010) | Motor-impaired | adaptation, transparency, performance, commodity |
| Auto Mouse Pointing Assessment (Hurst et al. 2007, 2008a) | Motor-impaired detection | adaptation, performance, commodity |

### Mobile Devices
| Project | User Group | Principles Upheld |
|---|---|---|
| VoiceDraw (Harada et al. 2007) | Motor-impaired | adaptation, performance, commodity |
| Barrier Pointing (Froehlich et al. 2007) | Motor-impaired stylus | performance, commodity |
| Walking User Interfaces (Kane et al. 2008c) | Walking/situationally impaired | adaptation, context, commodity |
| Slide Rule (Kane et al. 2008a) | Blind users | performance, commodity |

### Web
| Project | User Group | Principles Upheld |
|---|---|---|
| WebAnywhere (Bigham et al. 2007–2010) | Blind users | adaptation, transparency, context, commodity |

## Notable Implementation Details

### SUPPLE (Section 5.8)
- Builds individual performance model from a short test battery: clicking, pointing, dragging, list selection tasks
- Because Fitts' law failed for motor-impaired users and unusual input devices, SUPPLE used custom automatic feature selection and regression models per user
- Optimization searched interface space for minimum movement time given the user model
- Results: motor-impaired users 28% faster, 73% more accurate, significantly more satisfied vs. manufacturer defaults
- Key ability-based insight: no knowledge of diagnosis/condition used — only performance measurements

### Angle Mouse (Section 5.7)
- Observes angular deviation of cursor path during pointing
- Low angular deviation (ballistic phase) → keep gain high
- High angular deviation (corrective phase) → drop gain to magnify target in motor-space
- Target-agnostic: requires no knowledge of target location from OS/application
- Result: >10% higher throughput, ~18% more accurate for motor-impaired users; no significant effect on non-impaired users

### TrueKeys (Section 5.4)
- 25,000-word lexicon + Levenshtein string distance + keyboard geometry model
- Corrects errors at word boundary (SPACEBAR trigger)
- N-best list provided for user override (transparency principle)
- Outperformed Microsoft Word 2004 spell checker and aspell/ispell

### Slide Rule (Section 5.13)
- "Reading finger" controls audio detail level: fast movement = first letter only; slow movement = full name
- "Second-finger-tap" (later incorporated as VoiceOver split-tap): pausing reading finger on target, tapping with second finger anywhere on screen triggers item — decouples location sensing from activation
- Key insight: leverages existing ability of blind users to navigate spatially with their fingers

### Invisible Keyguard (Section 5.2)
- Software-only keyguard eliminated need for physical template
- Three methods tested: heuristics, timing, language models
- Typing errors reduced by 80% with most successful time-based approach

## Figures of Interest

- **Fig 1 (page 2):** ISA wheelchair symbol vs. National Veterans Wheelchair Games logo — dis-ability vs. ability framing
- **Fig 2 (page 6):** Three-panel diagram: (a) matching user-system, (b) traditional AT add-on, (c) ability-based system that accommodates user
- **Table 1 (page 11):** Seven principles with category (Stance/Interface/System) and status (Required/Recommended/Encouraged)
- **Table 2 (page 14):** All 14 example projects with user group and principles upheld
- **Fig 4 (page 19):** Angle Mouse angular deviation visualization — low deviation (left) vs. high deviation (right)
- **Fig 5 (page 20):** SUPPLE's ability assessment battery tasks
- **Fig 6 (page 20):** SUPPLE-generated interfaces: MS Word default vs. Cerebral Palsy version vs. Muscular Dystrophy version
- **Fig 9 (page 24):** Walking user interface adaptation — standing layout (dense) vs. walking layout (large targets)

## Research Challenges Identified

1. **Ability measurement in the wild** — inferring user intent from unconstrained behavior (not test battery); requires task segmentation, target knowledge
2. **Context sensing** — environmental factors (noise, lighting, temperature, motion mode); mobile activity recognition
3. **User modeling under high variability** — conventional models don't hold for impaired users; need per-user models accommodating high variability
4. **Interface adaptation design** — how to incorporate errors, visual search time, aesthetic concerns beyond SUPPLE's movement-time optimization
5. **Previews for non-visual parameters** — showing users what adaptation changes will do before committing, especially for motor-oriented parameters
6. **Reconfigurable and remappable hardware** — software-defined input device capabilities

## Limitations

- The 14 example projects focus heavily (11/14) on motor impairments and pointing/typing; other disability types are noted as in-scope but not demonstrated
- Fitts' law inadequacy for motor-impaired users is noted but not resolved in SUPPLE — custom regression models are used as a workaround
- Adaptation requires accurate ability measurement, which remains an open research challenge — especially "in the wild" without a test battery
- Commodity principle (7) is "encouraged" not required, acknowledging that specialized hardware is still often necessary for severe disabilities

## Testable Properties

- **Minimum criteria:** An ability-based system MUST uphold principles 1 (Ability) and 2 (Accountability); any design lacking these two is not ability-based by definition
- **Angle Mouse:** High angular deviation during corrective phase must decrease gain; low angular deviation during ballistic phase must keep gain high
- **SUPPLE:** Generated interface must minimize predicted movement time for the specific user's regression model
- **Transparency requirement:** Any adaptation a system makes must be exposable, overridable, revocable, and storable by the user
- **Accountability:** If user performance is poor, the system (not the user) must be changed — never require the user to retrain, purchase special devices, or alter their behavior

## Relevance to Project

This is the foundational theoretical framework for accessible computing from an ability perspective — the paper that provides the conceptual vocabulary (ability, accountability, adaptation, transparency, performance, context, commodity) underlying all work on adaptive accessibility systems. The seven principles function as a design checklist applicable to screen readers, web accessibility tooling, AT evaluation, and adaptive UI research. Any paper in this collection involving adaptive interfaces, motor accessibility, or design philosophy should be cross-referenced against these principles.

## Open Questions

- [ ] How do the seven principles apply to cognitive accessibility (WCAG compliance, cognitive load reduction)?
- [ ] How does ability-based design relate to screen reader architecture — does the screen reader uphold accountability if it cannot adapt to the user's reading behavior?
- [ ] Is SUPPLE's approach extensible to visual/auditory ability measurement for vision/hearing impairment?
- [ ] How does the MotorEase automated detection approach (Krishnavajjala 2024) relate to the performance measurement principle?

## Related Work Worth Reading

- Gajos et al. (2010) — SUPPLE: Automatically generating personalized UIs (*Artificial Intelligence* 174) — deepest ability-based design example
- Hurst et al. (2008a) — Automatic pointing performance detection (IUI '08) — ability measurement in the wild
- Trewin & Pain (1997, 1999) — Dynamic keyboard model; keyboard/mouse errors due to motor disabilities
- Kane et al. (2008a) — Slide Rule (ASSETS '08) — blind users on touch screens
- Froehlich et al. (2007) — Barrier Pointing (ASSETS '07) — motor impairment on mobile
- Wobbrock et al. (2009) — Angle Mouse (CHI '09) — target-agnostic pointing facilitation
- Edwards, A.D.N. (ed., 1995) — *Extra-Ordinary Human-Computer Interaction* — conceptual forerunner
- Harper (2007) — "design for one" concept cited as vision for ABD end-state

## Collection Cross-References

### Already in Collection

- **Krishnavajjala_2024_MotorEase** — cited domain overlap: MotorEase automates detection of motor accessibility violations in mobile UIs; ABD's Principle 5 (Performance) and accountability principle are the theoretical foundation for why systems should detect and respond to user motor performance rather than requiring users to adapt. MotorEase operationalizes ABD's stance for static violation detection.
- **Mack_2021_AccessibilityResearchSurvey** — cited domain overlap: Mack's landscape survey documents the research distribution across disability types; ABD provides the theoretical vocabulary that explains *why* motor impairment research is concentrated in adaptive input (Principles 3, 5, 7).
- **Yuan_2011_GameAccessibilitySurvey** — cited domain overlap: Yuan's game accessibility framework maps disability types to interaction steps; ABD's ability vs. disability reframing applies directly to game accessibility design — games should ask what a player can do, not what disability they have.
- **Gartland_2022_WebAccessibilityCognitive** — cited domain overlap: ABD's principles apply to cognitive accessibility but the paper itself focuses on motor/visual; Gartland fills the cognitive dimension. ABD's Principle 2 (Accountability) aligns with Gartland's finding that PwCDs are excluded from design processes.

### New Leads (Not Yet in Collection)

- **Gajos, Weld, Wobbrock (2010)** — "Automatically generating personalized user interfaces with SUPPLE" (*Artificial Intelligence* 174, pp. 910-950) — The deepest implementation of ABD; full ability-based interface generation system with performance modeling. High priority for this collection.
- **Wobbrock, Fogarty, Liu, Kimuro, Harada (2009)** — "The Angle Mouse" (CHI '09, pp. 1401-1410) — Target-agnostic pointing facilitation via angular deviation; direct ABD implementation with quantitative results (>10% throughput gain for motor-impaired users).
- **Hurst, Hudson, Mankoff, Trewin (2008a)** — "Automatically detecting pointing performance" (IUI '08, pp. 11-19) — In-the-wild ability measurement without test battery; critical for Principle 5.
- **Kane, Bigham, Wobbrock (2008a)** — "Slide Rule: Making mobile touch screens accessible to blind people" (ASSETS '08, pp. 73-80) — Second-finger-tap technique (later VoiceOver split-tap); demonstrates ABD for visual impairment.
- **Froehlich, Wobbrock, Kane (2007)** — "Barrier Pointing" (ASSETS '07, pp. 19-26) — Physical bezel-based motor accessibility on mobile; demonstrates Principle 6 (Context).

### Supersedes or Recontextualizes

- This paper provides the theoretical framing that **Krishnavajjala_2024_MotorEase** implicitly operates within — MotorEase detects violations of what would be ABD Principle 2 (Accountability: the system should not require users to struggle with inadequate touch targets). The ABD framework makes explicit why MotorEase's detection targets matter theoretically.
