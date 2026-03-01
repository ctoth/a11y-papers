# Game Accessibility: A Survey

**Authors:** Bei Yuan, Eelke Folmer, Frederick C. Harris Jr.
**Year:** 2011 (published online June 2010)
**Venue:** Universal Access in the Information Society, Vol. 10, pp. 81–100
**DOI/URL:** https://doi.org/10.1007/s10209-010-0189-5

## One-Sentence Summary
Foundational survey mapping how each disability type (visual, hearing, motor, cognitive) maps to a specific step in a three-step game interaction model, then catalogues accessible games by genre and extracts high-level and low-level accessibility strategies for game developers.

## Problem Addressed
No systematic framework existed to explain *why* a disability prevents game play and *what kind* of accessibility solution is needed. Existing guidelines (IGDA SIG 2004, Norwegian Medialt 2006) listed rules without explaining the underlying accessibility problem each rule solves, making them hard to apply to new game genres.

## Key Contributions
- **Game interaction model**: three-step cycle (Receive Stimuli → Determine Response → Provide Input) that maps each disability type to exactly one step where it causes a barrier
- **Accessibility statistics**: estimates from 2002 US Census that 32.2 million people (~11% of US population) have game-play affected by a disability; 6.3 million (~2%) completely excluded, 25.9 million (~9%) reduced experience
- **Accessible game catalogue**: surveyed accessible games across 8 genres for 4 impairment types, documenting which strategies each uses
- **Strategy taxonomy**: two-level hierarchy — high-level strategies (enhance, replace, reduce stimuli/input/response) and low-level strategies (concrete implementations)

## Game Interaction Model

The three-step model, applied per-game-cycle:

1. **Receive Stimuli** — game outputs visual (primary in most genres), auditory, or haptic feedback
   - *Primary stimuli*: required to play (visual in FPS, visual+audio in dance/rhythm)
   - *Secondary stimuli*: supplemental (audio in FPS; losing it reduces experience but doesn't block play)
2. **Determine Response** — player cognitively selects an in-game action from available options
3. **Provide Input** — player physically actuates a device (keyboard, mouse, controller, steering wheel)
   - *Discrete input*: on/off switch (keyboard keys, controller buttons)
   - *Analog input*: continuous (mouse, thumbstick) — requires more precise motor skill

**Key insight**: Failure at step N prevents successful performance of steps N+1 and N+2. Therefore:
- Visual impairment → blocks step 1 (primary stimuli) → blocks all subsequent steps
- Hearing impairment → blocks only secondary stimuli → reduced experience, not exclusion (except dance/rhythm)
- Cognitive impairment → blocks step 2
- Motor impairment → blocks step 3

## Disability Classification (per WHO ICIDH)

| Type | Subtype | Barrier step | Barrier severity |
|------|---------|-------------|-----------------|
| Visual | Severe (blindness) | Step 1 (primary stimuli) | Critical — excluded |
| Visual | Mild (colorblindness, low vision) | Step 1 (secondary) | Non-critical — reduced |
| Hearing | Severe (deafness) | Step 1 (secondary stimuli) | Non-critical (most genres) |
| Hearing | — in dance/rhythm | Step 1 (primary) | Critical |
| Cognitive | Learning disability, autism, mental retardation, dementia | Step 2 | Non-critical to critical |
| Motor | Severe (quadriplegia) | Step 3 | Critical — excluded |
| Motor | Mild (arthritis) | Step 3 | Non-critical — reduced |

## Accessibility Statistics (US, 2002 Census)

| Disability | Severity | US count (thousands) |
|-----------|---------|------------------|
| Motor: difficulty grasping | Severe (critical) | 918 |
| Motor: difficulty grasping | Not severe (non-critical) | 3,745 |
| Visual: difficulty seeing words/letters | Severe (critical) | 1,965 |
| Visual | Not severe (non-critical) | 6,369 |
| Hearing: difficulty hearing conversation | Severe (non-critical) | 1,118 |
| Hearing/cognitive: difficulty with speech | Severe (non-critical) | 727 |
| Cognitive: learning disability | Non-critical | 4,489 |
| Cognitive: mental retardation | Critical | 1,447 |
| Cognitive: Alzheimer/dementia | Critical | 1,937 |
| **ALL — critical barrier** | | **6,267** |
| **ALL — non-critical barrier** | | **25,946** |
| **ALL — any barrier** | | **32,213** |

Total: ~32.2 million (~11% of US population); 2% completely excluded, 9% reduced experience.

## Strategy Taxonomy (Table 7)

### High-Level → Low-Level Strategies

**Step 1: Receive Stimuli (Visual/Hearing impairment)**

| High-level | Direction | Low-level implementations |
|-----------|-----------|--------------------------|
| Enhance stimuli | Visual | High contrast color schemes; Increase font size; Color blind color schemes; Zoom options |
| Replace stimuli | Audio → Visual | Text (subtitles, closed captioning); Non-text (visual cues, sound radar, signing) |
| Replace stimuli | Visual → Audio | Speech (screen reader, self voicing); Audio cues; Sonification (earcons, sonar, auditory icons) |
| Replace stimuli | Visual → Haptic | Haptic cues |

**Step 2: Determine Response (Cognitive impairment)**

| High-level | Low-level implementations |
|-----------|--------------------------|
| Reduce stimuli | Limit number of game objects; Simplify storyline |
| Reduce time constraints | Increase response time; Slow down game |
| Reduce input | Remove input; Automate input |

**Step 3: Provide Input (Motor impairment)**

| High-level | Low-level implementations |
|-----------|--------------------------|
| Reduce input | Scanning; Remove input; Automate input |
| Replace input | Voice/brain control |

## Alternative Input Devices (for motor impairment)

- **Switches**: body-part-agnostic (sip-and-puff, pull, push, squeeze); one-switch = minimum discrete input
- **Eye trackers** [58]: track gaze for cursor control
- **Brain wave controllers** [59]: BCI for game control
- **Head trackers** [58]: Natural Point Trackir 4
- **One-handed controllers** [51]: quad controller with sip-and-puff
- **Voice joystick** [38, 40]: vocal joystick for cursor
- **Scanning**: iterates chains of options; MS Windows XP on-screen keyboard supports it; multi-step scanners [86] aggregate options; two-step row-column scanning for 2D grids
  - Types: Binary one-switch (fastest if few options); Context-agnostic (CA, same throughout); Context-sensitive (CS, adapts to game state)

## Motor-Accessible Game Strategies (Table 3)

| Game | Modification | Binary one-switch | Reduction | Automation | Scanning |
|------|------------|-----------------|----------|-----------|---------|
| Strange Attractors | No | No | — | — | — |
| Sudoku Access | Yes | Yes | No | No | CA |
| Jet Boarder | Yes | No | Yes | Yes | No |
| Mini Golf | Yes | Yes | No | No | CA |
| Frogger | Yes | Yes | Yes | No | CA |
| Branston | Yes | No | No | Yes | CS |
| Gordon's Trigger Finger | Yes | Yes | Yes | Yes | No |

Key insight: time-sensitive games (Frogger, racing) are hardest for one-switch because scanning slows input rate.

## Blind-Accessible Game Strategies (Table 4)

| Game | Genre | Feedback | Input |
|------|-------|---------|-------|
| Mach 1 Car Racing | Racing | Audio cues | Keyboard |
| Shades of Doom | FPS | Audio cues, speech | Keyboard |
| AudioQuake | FPS | Sonification, speech | Keyboard |
| Terraformers | FPS | Sonification, speech | Keyboard |
| The Last Crusade | RPG | Speech | Keyboard |
| AudioBattleShip | RTS | Audio cues | Tablet |
| GMA Tank Commander | Arcade | Audio cues | Keyboard |
| Speed Sonic Across the Span | Platform | Audio cues | Controller |
| Metris | Puzzle | Sonification | Keyboard |
| AudiOdyssey | Music | Audio cues | Wiimote |
| Blind Hero | Music | Haptic | Guitar controller |
| Finger Dance | Music | Audio cues | Keyboard |

**Strategies for visual replacement**:
- Speech (screen reader / self-voicing)
- Audio cues (real-world sounds)
- Sonification: Auditory Icons, Ear Cons, Sonar (spatial info)
- Enhance: high-contrast color, scalable fonts, color-blind schemes, zoom, unit color customization

## Hearing-Accessible Game Strategies (Table 5)

| Game | Genre | Text | Non-text |
|------|-------|------|---------|
| XIII | FPS | — | Transcribing |
| The Sims | Simulation | — | Visual cues |
| Doom 3 | FPS | CC | Sound radar |
| Torque CC | Any 3D | CC | Sound radar |
| Zork:GI | Adventure | CC | — |
| Halflife 2 | FPS | CC | — |
| Sin episodes | FPS | CC | — |
| Smile | Virtual world | CC | — |
| CopyCat | Adventure | CC | — |

Strategies: Replace Audio with Text (subtitles, closed captioning); Replace Audio with Non-text (visual cues, sound radar, signing).

## Cognitive-Accessible Game Strategies (Table 6)

| Game | Reduce input | Reduce stimuli | Reduce time |
|------|------------|--------------|------------|
| Ilbo (FPS-like) | Yes | Yes | Yes |
| Coucou Caché | Yes | Yes | Yes |
| FLOW | Yes | Yes | Yes |
| SIDES | Yes | Yes | Yes |

All four games: no time sensitivity, limited visual stimuli, limited/intuitive controls.

## Universally Accessible Games

- **UA Chess** [34] and **Universal Tic-Tac-Toe** [65]: board games supporting vision- and motor-impaired via scanning, voice input, and synthetic speech
- **Access Invaders** [35]: one-switch control, scalable objects, audio cues + speech for visual access

## Figures of Interest

- **Fig. 1 (p. 84)**: Interaction sequence diagram (player ↔ game, stimulus/response loop)
- **Fig. 2 (p. 85)**: Interaction finite state machine
- **Fig. 3 (p. 87)**: Switch controller and mouth controller photos
- **Fig. 4 (p. 89)**: One-switch game screenshots (Jet Boarder, Sudoku Access)
- **Fig. 5 (p. 92)**: Hearing-accessible game screenshots (XIII, Torque CC)
- **Fig. 6 (p. 93)**: Cognitive-accessible game screenshots (Coucou Caché, SIDES)
- **Fig. 7 (p. 94)**: Universal design games (UA Chess, UA Tic Tac Toe)
- **Table 7 (p. 95)**: Complete accessibility strategies summary — key reference table

## Tradeoffs Between Approaches

1. **Modify existing game (top-down)**: cheaper, but gameplay often must be compromised (e.g., one-switch Frogger removes L/R movement)
2. **Design from scratch (bottom-up)**: no gameplay compromise, but more expensive; examples: Strange Attractors, AudiOdyssey

**Scanning tradeoff**: slows input rate — only suitable for non-time-sensitive games. For time-sensitive games, input must be reduced or automated.

**Modality conversion tradeoff**: visual → audio loses resolution (visual stimuli far richer than audio channel capacity); audio → visual loses immersion.

**Multiplayer fairness**: one-switch FPS with automation (Gordon's Trigger Finger) gives motor-impaired player significantly different capability vs. non-disabled players — fairness concern [12].

## Results Summary

- Most accessible games are modifications of existing games
- FPS genre has the most accessible games across all impairment types (open-source engines enable this)
- Strategy/sports/RPG genres are severely underrepresented for motor- and visual-impaired players
- Only 5 games found for cognitive impairment
- Hearing impairment: largest supply of accessible games, but mostly via CC which is non-standard

## Limitations

- Accessible game census incomplete — "technology Web sites, online and paper-based journals" only; no formal search protocol
- Cognitive impairment strategies extracted from very few games (2 genres); low confidence in completeness
- No data on implementation cost of each accessibility strategy
- US census only (2002); cannot combine with international statistics due to methodology differences
- Low-level strategies are context-sensitive (e.g., closed captioning not applicable to chess games without dialog)
- Survey predates modern game accessibility standards and hardware (e.g., Xbox Adaptive Controller 2018)

## Testable Properties

- **Model coverage**: every impairment type must map to exactly one of the three interaction steps (no impairment spans all three simultaneously)
- **Strategy necessity**: a game accessible to severely visually impaired players must implement at least one "Replace stimuli: Visual → Audio" or "Visual → Haptic" strategy
- **Scanning incompatibility with time-sensitive games**: games with real-time combat or racing mechanics cannot be made accessible with scanning alone without also automating inputs
- **Cognitive strategy overlap**: all three cognitive strategies (reduce stimuli, reduce time, reduce input) must be present together for severe cognitive impairment access (all four surveyed games use all three)
- **Statistics bound**: fraction of population with game-critical barriers must be ≤ fraction with all disabilities (2% ≤ 11%)

## Relevance to Project

This paper provides the foundational taxonomy for game accessibility research. Its three-step interaction model is the conceptual framework cited in virtually all subsequent game accessibility work. The strategy taxonomy (Table 7) directly maps disability types to implementation approaches. The paper is particularly relevant for any work on alternative input methods, audio game design, and cognitive accessibility evaluation. It also establishes baseline statistics on the scale of the excluded gaming population.

## Open Questions
- [ ] Which strategies have been implemented in mainstream AAA games since 2011? (The paper predates Xbox Adaptive Controller, PS5 accessibility features, etc.)
- [ ] Can the interaction model be extended for VR/AR gaming where spatial presence adds a fourth modality?
- [ ] How does the cognitive strategy taxonomy map to specific WCAG success criteria for cognitive accessibility?
- [ ] Is the 2002 census estimate still the best available, or have more recent studies updated these numbers?

## Related Work Worth Reading
- IGDA SIG Game Accessibility White Paper [41] — the 19 guidelines this paper critiques
- Norwegian Medialt 34 guidelines [89] — the other set of existing guidelines
- Folmer (2006) [25] — usability patterns in games, referenced for context-sensitivity concern
- Grammenos et al. (2008) [33] — "Game over: learning by dying" game design
- van Tol (2006) [96] — gaming with auditory disability

## Collection Cross-References

### Already in Collection
- **Mack_2021_AccessibilityResearchSurvey** — cites game accessibility as an emerging underrepresented area; Yuan et al. is likely a foundational reference for that observation. This paper provides the underlying research they identify as growing.

### New Leads (Not Yet in Collection)
- Grammenos et al. (2005) [34] — UA Chess, universally accessible board game design — relevant for universal design principles
- Folmer et al. (2007) [27] — Textsl: command-based virtual world interface for visually impaired — AT + virtual worlds intersection
- Smith et al. (2006) [81] — eye movements for video game control — alternative input
- Simpson et al. (1999) [80] — adaptive one-switch row-column scanning — motor AT fundamentals
- Yuan & Folmer (2008) [106] — Blind Hero (haptic guitar hero) — specific accessible game design

---

**See also:** Porter_2013_GameAccessibilityBarriers — Empirical complement to this paper. Porter & Kientz (ASSETS 2013) conducted surveys of 55 disabled gamers and interviews with 6 game developers, providing ground-truth data on which barriers from Yuan's theoretical framework actually manifest in practice. Key finding: AT incompatibility is the dominant real-world barrier; middleware is the primary structural intervention point.

**See also:** Gerling_2012_FullBodyMotionGame — Empirical instantiation of Yuan's motor impairment category for institutionalized older adults using Kinect full-body motion control. Two user studies (N=15, N=12) with wheelchair users and stroke survivors validate a gesture set and produce seven design guidelines for the "provide input" step specifically. Provides per-player calibration architecture (ROM, strength, agility) and PANAS mood improvement data (p<0.01).

**See also:** Westin_2004_GameAccessibilityTerraformers — The earliest concrete case study of 3D game accessibility (2000–2003 development, 2004 publication) that predates and helped motivate this survey. Westin initiated the IGDA Game Accessibility SIG that Yuan et al. cite as a community resource, and Terraformers is one of the earliest games bridging visual/audio hybrid gameplay for blind and sighted players simultaneously.

**See also:** Grammenos_2009_UniversallyAccessibleGames — The primary implementation-level paper underlying Yuan's conceptual framework. Grammenos et al. define UA-Games (universally accessible games), demonstrate four working implementations (UA-Chess, Access Invaders, Game Over\!, Terrestrial Invaders), and introduce the Parallel Game Universes concept for cross-disability multiplayer. Table I of Grammenos maps directly onto Yuan's two-level strategy taxonomy, providing the concrete adaptation parameters (13 categories: Speed, Quantity, Size, Layout, Firepower, Visual complexity, Contrast, Sound, Interaction rules, Analogue vs. digital control, Hints, Stamina) that Yuan surveys at a high level.

---

**See also:** AguadoDelgado_2020_VideoGamesA11ySystematicReview — extends Yuan (2011) as a PRISMA-compliant systematic mapping study of 45 game accessibility papers (2004–2014); builds on this paper's three-phase interaction model and disability taxonomy; provides the quantitative evidence base and a 45-study retrieval appendix complementing this paper's conceptual framework.
