# Full-Body Motion-Based Game Interaction for Older Adults

**Authors:** Kathrin M. Gerling, Ian J. Livingston, Lennart E. Nacke, Regan L. Mandryk
**Year:** 2012
**Venue:** Proceedings of CHI 2012, ACM, pp. 1873–1882
**DOI:** 10.1145/2207676.2208324

## One-Sentence Summary
Two user studies with 15 and 12 institutionalized older adults (most in wheelchairs, many post-stroke) establish a gesture set and seven concrete design guidelines for full-body motion-controlled games (Kinect-style) that accommodate age-related motor and cognitive impairments.

## Problem Addressed
Commercially available full-body motion games are designed around younger, able-bodied players and actively put institutionalized older adults at risk of injury or exclude them entirely. No validated gesture set or design guidelines existed for this population before this paper. Applying traditional HCI guidelines fails because games require challenge-versus-ease balancing that general usability guidelines do not address.

## Key Contributions
1. A validated 8-gesture set (4 static, 4 dynamic) derived from physical therapy exercises, suitable for institutionalized older adults including wheelchair users and stroke survivors with unilateral paralysis.
2. A working Kinect game prototype ("flower garden" theme) with automated per-player calibration covering range of motion (ROM), strength, and agility.
3. Seven empirically grounded design guidelines for full-body gesture interaction targeted at institutionalized older adults (Table 5, page 7).
4. Empirical evidence that playing the game produced a statistically significant improvement in positive affect (PANAS, p<0.01), with no increase in negative affect.

## Methodology
**Study 1 (gesture evaluation):**
- N=15 institutionalized older adults, mean age 73.72 (SD=9.90, range 60–90)
- 13/15 in wheelchairs; 6/15 post-stroke with unilateral paralysis
- Custom gesture analysis tool (C#, Microsoft Kinect SDK + Game Studio 4.0)
- Participants performed gesture set twice; tool logged completion rate and tracking quality
- Questionnaire on 5-point Likert scale for fun, difficulty, exhaustion, fear of falling
- 95% CI reported on completion rates

**Study 2 (in-game gesture use):**
- N=12 institutionalized older adults, mean age 76.7 (SD=10.6, range 60–91)
- 11/12 in wheelchairs; 6/12 post-stroke
- Same game tool with calibration routine + guided tutorial + 5 min free play
- Pre/post PANAS questionnaire for positive and negative affect
- Paired-samples t-test for mood change analysis

## Gesture Set (Table 1)

| Gesture | Static | Dynamic |
|---------|--------|---------|
| 1 | Hands together | Clap hands |
| 2 | Raise one arm | Wave arm |
| 3 | Arms to the side | Pretend to fly |
| 4 | One-leg stand | Walk in place |

Design rationale:
- Derived from physical therapy exercises + everyday movements
- Limited to 4 core movements (reduces sensorimotor learning load)
- Most executable while seated (accommodates wheelchair users)
- Gestures implementable using relative Kinect joint positions (not absolute)

## Calibration System (Study 2 Game)

Three measured parameters:
1. **ROM (range of motion):** Player collects flowers across screen; extent of reach recorded → sets gesture precision threshold (low ROM → reduce required precision)
2. **Strength:** Player holds flowers at fixed screen positions → sets effect duration (low strength → effects stay active longer to prevent overexertion)
3. **Agility:** Completion time of calibration task → sets gesture time window (low agility → wider time window for gesture recognition)

Calibration also determines: seated vs. standing interaction mode; one-handed vs. two-handed play.

## Key Results

**Study 1 gesture completion rates:**
- Overall completion: 54.17%
- 16.67% of correctly-performed gestures not recognized (Kinect tracking failure, especially with wheelchair users)
- Static hand-based gestures: highest completion rates
- Dynamic gestures: lower completion rates (repeated movement more demanding than holding a pose)
- Gesture 4 (walking in place): extremely low for wheelchair users (most could not move feet independently)

**Study 1 questionnaire (5-point Likert, N=15):**

| Item | Mean | SD |
|------|------|----|
| Fun | 3.40 | 1.72 |
| Tiresome | 1.87 | 1.41 |
| Easy | 4.40 | 1.30 |
| Difficult | 2.20 | 1.57 |

- 67% not afraid of losing balance; 87% not afraid of falling
- 93% found instructions sufficient; 87% found feedback sufficient

**Study 2 gesture completion rates (in-game, N=12):**
- Raise arm: 100%
- Arms to side: 100%
- Catch bird (hand reach): 92%
- Foot-based gestures: 1/12 participants only

**Study 2 PANAS mood results:**
- Positive affect: pre-game M=3.34 (SD=0.64) → post-game M=3.88 (SD=0.79), t(11)=-2.92, p<0.01
- Negative affect: pre M=1.72 (SD=0.78) → post M=1.68 (SD=0.86), t(11)=0.28, p=0.79 (no change)

**Study 2 game questionnaire (5-point Likert):**

| Item | Mean | SD |
|------|------|----|
| Fun | 3.79 | 0.99 |
| Tiresome | 2.13 | 1.57 |
| Easy | 3.71 | 1.48 |
| Difficult | 1.83 | 1.11 |

## Design Guidelines (Table 5, full text)

**Guideline 1: Age-Inclusive Design**
Create inclusive games by embracing age-related physical and cognitive impairments. Systems should include gestures that adapt to individual impairments (e.g., one arm OR both arms). Cognitive changes require simpler game structures.

**Guideline 2: ROM-Adaptability**
Calibrate interaction to individual range of motion. Use bigger tolerance in gesture recognition rather than requiring high precision. Prevents injury from overextension.

**Guideline 3: Exertion Management**
Alternate physically intense and less challenging periods. Shorten challenging periods for frailer players. Integrate break reminders or automatic shutdown based on fitness level.

**Guideline 4: Dynamic Game Difficulty**
Adjust difficulty between players AND account for daily within-player variability. Do not assume monotonically increasing challenge across sessions — returning players need per-session re-adaptation, not just cumulative progression.

**Guideline 5: Easy Gesture Recall**
Use natural mappings; map in-game actions to real-world activities. Avoid extra GUI elements. Do not require players to recall gestures unprompted — use in-game affordances to cue gestures (e.g., item appears at top of screen → suggests raising arm).

**Guideline 6: Continuous Player Support**
Extended tutorials + repetition throughout gameplay. Visual and audible prompting if no interaction detected. Do not assume players know when actions are required.

**Guideline 7: Simple Setup Routines**
Cannot assume technical knowledge from older adults or nursing staff. Easy start/stop; simple menu navigation or no menu at all.

## Implementation Details

- Tool implemented in C# using Microsoft Kinect SDK + Microsoft Game Studio 4.0
- Gestures tracked using **relative joint positions** (handles wheelchair geometry)
- System needs: determine seated/standing at game start; detect one-handed vs. two-handed capability
- Kinect SDK at time of study only supported standing skeleton — workaround: use lateral tracking space not blocked by chair; remove bulky chair parts (arm rests, lap trays) to improve skeleton tracking
- Free play (no guided prompting) was not successful for this population — nearly all participants needed experimenter assistance during free play

## Figures of Interest
- **Fig 1 (page 4):** Bar chart of gesture completion rates for static vs. dynamic gestures at 95% CI — shows static consistently higher; dynamic Gesture 4 (walking) near zero for wheelchair users
- **Fig 2 (page 5):** Screenshot of tutorial phase — stick figure on left side of screen demonstrating gesture; garden scene right
- **Table 5 (pages 7–8):** Full text of all seven design guidelines

## Limitations
- Small samples: N=15 (Study 1), N=12 (Study 2) — all from single nursing home facility
- All Study 2 participants were assigned static gestures only (due to ability levels) — no within-study comparison of static vs. dynamic in game context
- Kinect SDK (2012) did not natively support seated/wheelchair skeleton tracking — required manual calibration workarounds
- Free play failure suggests tutorial design remains unsolved — future work needed
- No longitudinal data — effects of repeated play unknown
- Mood improvement measured immediately post-session only; durability of effect not assessed
- No control group for mood improvement

## Testable Properties
- Static gestures must have higher completion rates than their dynamic counterparts for this population (observed: true for all 4 gesture pairs)
- ROM-calibrated systems should achieve higher completion rates than uncalibrated systems (Study 2 completion rates notably higher than Study 1 for arm gestures)
- Positive affect (PANAS) must increase post-play (t-test significant at p<0.01)
- Negative affect (PANAS) must not change significantly post-play (confirmed, p=0.79)
- Gesture recognition tolerance must increase (not decrease) as ROM value decreases
- Effect duration must increase (not decrease) as strength value decreases
- Time window for gesture completion must increase (not decrease) as agility value decreases

## Relevance to Project
This paper directly extends Yuan_2011_GameAccessibilitySurvey's motor impairment category into a concrete empirical study with older adults and wheelchair users. It provides:
- Specific gesture thresholds (ROM, strength, agility) for Kinect-style motion input
- Empirically validated calibration architecture
- Seven named, actionable design guidelines directly applicable to any motion-based accessible game system
- PANAS mood data supporting the claim that accessible motion games improve emotional well-being

It also engages directly with Wobbrock_2011_AbilityBasedDesign's ability-based design framework — the per-player calibration system is a direct instantiation of the Adaptation principle, and the argument for "prioritizing ability before mechanics" echoes ability-based design's core stance.

## Open Questions
- [ ] Do the guidelines generalize to populations with cognitive impairments (dementia)?
- [ ] What tutorial design produces successful independent free play?
- [ ] Do weekly gameplay sessions produce lasting improvement in mood or physical fitness?
- [ ] How does the approach scale to modern depth-sensor hardware (Azure Kinect, LiDAR)?
- [ ] What is the minimum gesture set that avoids boredom while remaining accessible?

## Collection Cross-References

### Already in Collection
- **Yuan_2011_GameAccessibilitySurvey** — cited implicitly; Gerling's study is a concrete empirical instantiation of Yuan's motor impairment category in the three-step game interaction model. Gerling's calibration architecture directly addresses the "provide input" step that Yuan identifies as the key failure point for motor-impaired players.

### New Leads (Not Yet in Collection)
- Rice et al. (2011) — "Evaluating Gesture-Based Games With Older Adults on a Large-Screen Display" [Sandbox '11] — direct predecessor study; explicitly called out as the gap Gerling fills
- Norton, Wingrave, and LaViola (2010) — "Exploring Strategies and Guidelines for Developing Full Body Video Game Interfaces" [FDG 2010] — the population-general guideline set that Gerling specializes for older adults
- Flores et al. (2008) — "Improving patient motivation in game development for motor deficit rehabilitation" [ACE 2008] — closest prior work on ROM-adaptive game design for impaired players
- Watson, Clark, and Tellegen (1988) — PANAS scale validation — measurement foundation for any emotional well-being study using PANAS

### Supersedes or Recontextualizes
None — Gerling 2012 extends Yuan_2011 by drilling into one specific population and input modality, it does not correct or supersede it.

---

## Related Work Worth Reading
- Rice et al. (2011) — gesture-based mini games with 36 older adults on large-screen display [ref 23]
- Norton, Wingrave, and LaViola (2010) — gesture strategies for full-body video game interfaces [ref 21]
- Flores et al. (2008) — game design for motor deficit rehabilitation [ref 10]
- Ijsselsteijn et al. (2007) — digital game design for elderly users [ref 15]
- Watson, Clark, and Tellegen (1988) — PANAS scales validation [ref 28]
