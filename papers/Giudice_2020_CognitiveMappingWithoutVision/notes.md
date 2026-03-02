# Cognitive Mapping Without Vision: Comparing Wayfinding Performance After Learning From Digital Touchscreen-Based Multimodal Maps vs. Embossed Tactile Overlays

**Authors:** Nicholas A. Giudice, Benjamin A. Guenther, Nicholas A. Jensen, Kaitlyn N. Haase
**Year:** 2020
**Venue:** Frontiers in Human Neuroscience, 14:87
**DOI:** 10.3389/fnhum.2020.00087

## One-Sentence Summary

Demonstrates that a vibro-audio map (VAM) rendered on a commercial touchscreen tablet produces functionally equivalent cognitive maps and wayfinding performance to traditional embossed tactile map overlays for blind and visually impaired users, validating low-cost touchscreen-based digital interactive maps (DIMs) as a viable replacement for expensive tactile map production.

## Problem Addressed

Traditional tactile maps for BVI individuals are expensive to produce (requiring specialized equipment like tactile embossers costing up to $50,000), static (cannot be updated), cumbersome (large hardcopy format), and require expert authoring. Interactive digital maps exist but most prior research focused on perceptual factors (map reading) rather than cognitive factors (whether the learned spatial knowledge actually transfers to real-world wayfinding). No prior study had directly compared a touchscreen-based DIM with a traditional HTM overlay using an environmental transfer paradigm that tests real-world navigation.

## Key Contributions

- First study to use Bayesian equivalence testing (HDI + ROPE) to compare DIM vs. HIM wayfinding performance, rather than traditional NHST which can only reject differences rather than confirm equivalence
- Demonstrates that vibrotactile cues on a flat touchscreen are functionally sufficient for spatial learning -- embossed raised-line tactile stimuli are not required
- Validates an environmental transfer paradigm: participants learned maps then navigated corresponding real physical spaces from memory, directly testing cognitive map quality
- Provides evidence supporting the "amodal" spatial representation hypothesis -- spatial information learned via touch (regardless of tactile modality) is stored in a common format in the brain

## Methodology

### Experimental Design
- 2 (VAM-based DIM vs. HTM-based HIM) x 2 (two map layouts) within-subjects mixed factorial design
- N = 8 blind participants (4 female, 4 male; ages 18-55, SD = 13.9)
- All participants were daily iPhone users with at least 10h formal O&M training
- Each participant learned both building layouts using both map interfaces
- Counterbalanced (5 started with DIM, 3 with HIM -- not fully counterbalanced)
- Experiment duration: 75-120 min per participant

### Map Learning Phase
- Participants seated, blindfolded, tablet in front
- Up to 10 minutes to freely explore each experimental map
- Task: find 3 hidden target objects + home location, learn global spatial layout
- Learning criterion test: correctly identify and place all targets on blank map maintaining correct spatial topology
- If failed: additional 5 min learning, then retest (no participant needed this)

### Environmental Transfer Phase
- Participants led (blindfolded) to corresponding real building floor
- Positioned at "home" location, same orientation as during map learning
- Given target name, asked to navigate to it at normal speed via most efficient route
- No access to map during navigation
- Navigation order: object 1, object 2, object 3, then return to home
- Two experimenters accompanied: one supervised participant, one recorded route on floorplan
- If incorrect localization: informed, walked to correct location, then next trial
- Corrective procedure prevented error accumulation

### Dependent Variables
1. **Wayfinding accuracy**: binary (0/1) -- correct if stopped within 12 feet (3.7 m) of target
2. **Route efficiency**: binary (0/1) -- whether participant took shortest/most direct route vs. suboptimal
3. **Learning time**: seconds spent using each interface to learn the map

## Key Equations

### Bayesian Probit Regression Model

$$Y_{ijk} | p_{ijk} \sim \text{Bernoulli}(p_{ijk})$$

$$g(p_{ijk}) = \beta_0 + \alpha_i + a_j^{(R)} + b_k^{(R)}$$

Where:
- $Y_{ijk}$ = observed outcome (0 or 1) for interface $i$, target $j$, participant $k$
- $p_{ijk}$ = probability of success
- $g(\cdot)$ = probit link function
- $\beta_0$ = intercept
- $\alpha_i$ = fixed effect of interface ($\alpha_1 = 0$ for HIM baseline, $\alpha_2$ = DIM effect relative to HIM)
- $a_j^{(R)}$ = random effect for target
- $b_k^{(R)}$ = random effect for participant

### Prior Distributions
- $\beta_0 \sim \text{Cauchy}(0, 10)$
- $\alpha_1 = 0$ (constraint, HIM is baseline)
- $\alpha_2 \sim \text{Cauchy}(0, 2.5)$
- $a_j^{(R)} \sim N(0, \sigma_a^2)$
- $b_k^{(R)} \sim N(0, \sigma_b^2)$
- $\sigma_a^2 = \text{inv-}\Gamma(0.01, 0.01)$
- $\sigma_b^2 = \text{inv-}\Gamma(0.01, 0.01)$

### MCMC Parameters
- Burn-in: 5,000 iterations
- Post-burn-in: 30,000 iterations
- Thinning interval: 5
- Chains: 3
- Samples per chain: 6,000 (total = 18,000)
- Convergence: Gelman-Rubin diagnostic, all $\hat{R} < 1.01$
- ESS: 11,777.6 (wayfinding accuracy), 11,964.4 (route efficiency)

## Parameters

| Name | Symbol | Units | Default | Range | Notes |
|------|--------|-------|---------|-------|-------|
| Accuracy threshold | -- | feet | 12 | -- | 3.7 m radius; ~1 finger width on map |
| Vibration frequency (hallway) | -- | Hz | 250 | -- | Continuous steady vibration |
| Vibration pulse (object/junction) | -- | ms | 100 | -- | 50% duty cycle, pulsed |
| Speech rate | -- | wpm | ~150 | -- | User-selectable volume |
| Map line width | -- | in | 0.35 | -- | On tablet: 0.9 cm |
| Map square size | -- | in | 0.35 x 0.35 | -- | On tablet: 0.9 x 0.9 cm |
| Map learning time limit | -- | min | 10 | -- | Self-paced, max 10 min |
| ROPE boundary (accuracy) | -- | -- | -0.741 | -- | -25% probability from HIM mean |
| ROPE boundary (efficiency) | -- | -- | -0.716 | -- | -25% from HIM mean |
| ROPE boundary (learning time) | -- | s | +/-60 | -- | Equivalent if within 60s |
| HTM embosser DPI | -- | DPI | 20 | -- | View Plus Tiger Emspot |
| Tablet screen size | -- | inches | 7.6" x 4.8" | -- | 19.3 x 12.2 cm |
| Tablet model | -- | -- | Samsung Galaxy Tab GT-P2610 | -- | Android 3.2 Honeycomb |

## Implementation Details

### VAM (Vibro-Audio Map) -- Digital Interactive Map
- **Hardware**: Samsung Galaxy Tab (GT-P2610), 7.6" x 4.8" screen, Android 3.2 Honeycomb
- **Haptic border**: Cardboard frame around screen to provide edges + prevent accidental button presses
- **Map rendering**: Lines [0.35 in (0.9 cm)] for walkable hallways, squares [0.35" x 0.35" (0.9 x 0.9 cm)] for objects and junctions
- **Vibrotactile feedback**:
  - Hallway contact: continuous 250 Hz vibration
  - Object/junction contact: 100 ms pulsed vibration (50% duty cycle)
- **Audio feedback**: Text-to-speech at ~150 wpm
  - Touching any hallway segment: total corridor length in feet between junctions
  - Touching hallway junctions: junction type ("corner", "three-way", "dead-end")
  - Touching target objects: target name spoken via synthesized speech
  - Tap to repeat at any x-y position
- **Exploration**: Single dominant index finger on flat glass surface

### HTM (Hardcopy Tactile Map) -- Hybrid Interactive Map
- **Production**: View Plus Tiger Emspot embosser, 20 DPI resolution
- **Material**: Embossed tactile lines on thermoform paper
- **Overlay**: Mounted on the same Samsung Galaxy Tab used for DIM
- **Audio cues**: Identical to VAM condition (speech + audio labels)
- **Key difference**: Physical raised-line corridors instead of vibrotactile feedback
- **No additional cues**: Traditional tactile maps don't use vertex/intersection cues; none added here either. Alert tone at target locations was added as redundant cue (matching DIM).

### Environments
- Two partial floor plans from University of Maine buildings
- Practice map: Boardman Hall first floor
- Experimental maps: Little Hall third floor (two sections)
- Corridor lengths: 398 ft (121.3 m) and 411 ft (125.3 m)
- Topology: 3 two-way intersections, 2 three-way intersections, 2 dead ends, 1 loop
- All junctions 90 degrees
- Scale: map to physical space (not explicitly stated but implied by graphic scale on map)
- 3 unique target objects per map + 1 home location
- Target names from Snodgrass & Yuditsky (1996) norms: highly visualizable, readily memorable

### Learning Criterion Test
- Blank map (embossed square on cardstock matching tablet border)
- Participant places finger at approximate target locations
- Experimenter marks positions on paper
- Pass criteria: (1) correctly identify all targets by name; (2) maintain correct global spatial topology (relative positions)

## Figures of Interest

- **Fig 1 (page 8):** Building floorplans for both experimental conditions with highlighted map regions showing objects (numbered squares), home location (H), and optimal route arrows
- **Fig 2 (page 8):** Screenshots of practice and experimental maps as rendered on the tablet, showing the colored rectangle map elements with labeled objects
- **Fig 3 (page 9):** Photograph of the VAM-based DIM as used by participants -- tablet in cardboard frame
- **Fig 4 (page 9):** Photograph of the HTM tactile overlay mounted on the tablet
- **Fig 5 (page 12):** Bayesian model diagram with DAG showing model structure, priors, and hyperpriors
- **Fig 6 (page 13):** Posterior distributions for wayfinding accuracy -- fixed effect (DIM-HIM) and intercept (HIM)
- **Fig 7 (page 13):** Posterior distributions for route efficiency -- fixed effect and intercept
- **Fig 8 (page 14):** Posterior distribution for learning time difference (DIM-HIM)

## Results Summary

### Wayfinding Accuracy
| Interface | Mean Accuracy (SD) |
|-----------|--------------------|
| HIM/HTM   | 78% (+/-25)        |
| DIM/VAM   | 75% (+/-23)        |

- Bayesian predicted probability: HIM 82%, DIM 83% (nearly identical)
- HDI for interface effect ($\alpha_2$): [-0.747, 0.78], mean = 0.0252
- 97.8% of HDI above ROPE lower bound (-0.741)
- Only 2.2% of credible values fell below decision criterion
- **Conclusion**: Highly similar wayfinding accuracy; strong evidence for equivalence

### Route Efficiency
| Interface | Mean Efficiency (SD) |
|-----------|---------------------|
| HIM/HTM   | 79% (+/-19)         |
| DIM/VAM   | 67% (+/-32)         |

- Bayesian predicted probability: HIM 80%, DIM 65%
- HDI for interface effect: [-1.29, 0.315], mean = -0.468
- 73% of HDI above ROPE lower bound (-0.716)
- 27% below ROPE boundary
- **Conclusion**: Inconclusive; observed data suggests similar performance but cannot definitively confirm equivalence

### Learning Time
| Interface | Mean Learning Time (SD) |
|-----------|------------------------|
| HIM/HTM   | 194s (+/-111)          |
| DIM/VAM   | 364s (+/-180)          |

- Mean difference: 166s longer for DIM
- HDI: [-2.16, 336], mean = 166
- Only 8% of HDI within ROPE (+/-60s)
- 97.4% posterior probability that DIM takes longer
- **Conclusion**: DIM likely requires more learning time than HIM (not surprising given novelty of interface and that participants had prior tactile map experience but no VAM experience)

## Limitations

- **Small sample size**: N = 8 (though Bayesian analysis partially addresses this)
- **Not fully counterbalanced**: 5 started with DIM, 3 with HIM
- **Practice advantage for DIM**: Practice phase used DIM only (time constraints), potentially giving DIM a slight familiarity advantage
- **Indoor-only**: Tested in university building corridors; outdoor/complex environments not tested
- **No prior VAM experience**: All participants familiar with tactile maps but none had used VAM before; expertise effects unknown
- **Binary DVs**: Accuracy and efficiency measured as pass/fail rather than continuous (e.g., distance from target)
- **Experimenter provided intersection geometry**: Verbal cues about intersection type during navigation (to control for mobility challenge variation)
- **No correction for multiple comparisons**: Separate Bayesian models per DV

## Testable Properties

- **Wayfinding accuracy equivalence**: DIM accuracy should be within 25% of HIM accuracy (ROPE criterion used in the paper)
- **Learning time ordering**: DIM learning time >= HIM learning time for novel DIM users (consistent finding)
- **Vibrotactile discrimination**: Users must be able to distinguish continuous vibration (hallway) from pulsed vibration (object/junction) at 250 Hz / 100 ms pulse
- **Accuracy threshold**: 12 ft (3.7 m) radius defines "correct" target localization -- this corresponds to one finger width on the map
- **Criterion test requirement**: All participants should pass learning criterion (correct identification + topology) before transfer; 100% did in this study
- **Spatial topology preservation**: If cognitive map is accurate, relative positions of targets must be maintained even if absolute distances have error

## Relevance to Project

This paper is directly relevant to the collection's visual impairment and assistive technology areas. It provides empirical evidence that commercial touchscreen devices can replace expensive specialized tactile map hardware for spatial learning by BVI users, with equivalent wayfinding outcomes. The environmental transfer paradigm (map learning -> real-world navigation) is a gold standard for evaluating whether accessible map interfaces produce genuine spatial understanding rather than just perceptual access. The paper connects to Biggs_2025_MapEquivalentPurpose's framework for evaluating map equivalence -- the VAM demonstrated here would likely score well on MEP's survey knowledge and spatial relationship criteria, as participants successfully navigated real spaces from memory. The Bayesian equivalence testing methodology (HDI + ROPE) is a notable methodological contribution for accessibility research, where small sample sizes (as documented in Mack_2021) make traditional NHST underpowered.

## Open Questions

- [ ] How does VAM performance scale to larger, more complex environments (multi-floor, outdoor)?
- [ ] Does expertise with VAM reduce the learning time gap vs. HTM?
- [ ] Would continuous rather than binary accuracy measures (e.g., Euclidean distance to target) reveal finer-grained differences?
- [ ] How does the VAM compare to dynamic pin-array displays (e.g., BrailleDis 9000)?
- [ ] Can the VAM approach be extended to real-time navigation (not just pre-journey learning)?

## Related Work Worth Reading

- Brayda et al. (2018) -- Compared static tactile map vs. dynamic pin-array display for small-scale environmental transfer
- Ducasse et al. (2018) -- Categorization of accessible interactive maps (HIMs vs. DIMs)
- Adams et al. (2015) -- Multi-modal perception of spaces using accessible maps
- Simonnet et al. (2019) -- Comparing interaction techniques for blind map exploration on small touchscreen devices
- Palani and Giudice (2017) -- Large-format VAM panning and zooming operations

## Collection Cross-References

### Already in Collection
- **Biggs_2025_MapEquivalentPurpose** -- The MEP framework for evaluating map equivalence directly relates; this paper provides behavioral evidence that touchscreen-based maps achieve equivalent spatial understanding, which the MEP criteria attempt to formalize
- **Mack_2021_AccessibilityResearchSurvey** -- Documents the small sample size norm (median 13); this study's N=8 is below that but uses Bayesian methods to partially compensate
- **Vanderheiden_1990_ThirtySomethingMillion** -- The low-cost commercial hardware argument (Samsung tablet) directly instantiates Vanderheiden's zero-marginal-cost design philosophy
- **Wobbrock_2011_AbilityBasedDesign** -- The VAM leverages what blind users CAN do (touch, hear) on commodity hardware, exemplifying the Ability and Commodity principles

### New Leads (Not Yet in Collection)
- Ducasse et al. (2018) -- "Accessible interactive maps for visually impaired users" -- comprehensive categorization of HIM vs. DIM approaches
- Loomis et al. (2013) -- "Spatial Image" theory -- the amodal spatial representation framework that justifies why touch-learned spatial info transfers across modalities
- Espinosa et al. (1998) -- Comparing methods for introducing blind people to unfamiliar urban environments -- foundational transfer study methodology
- Golledge (1993) -- Geography and the disabled, foundational text on spatial cognition without vision

### Supersedes or Recontextualizes
- None directly; this paper extends the Giudice lab's own prior work (Giudice et al., 2012; Raja, 2011) to a full environmental transfer comparison
