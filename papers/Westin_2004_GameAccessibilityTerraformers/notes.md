# Game Accessibility Case Study: Terraformers – a Real-Time 3D Graphic Game

**Authors:** T Westin
**Year:** 2004
**Venue:** Proceedings of the 5th International Conference on Disability, Virtual Reality and Associated Technologies (ICDVRAT), Oxford, UK
**DOI/URL:** https://www.icdvrat.com/2004/P/S03_N3_Westin_2004.pdf

## One-Sentence Summary
Documents the first 3D real-time game designed from the ground up to be playable by blind, low-vision, and sighted players simultaneously, cataloguing the specific audio/spatial techniques that made this dual-access possible.

## Problem Addressed
The game industry in 2004 had a complete split: mainstream 3D games required full sight; blind-accessible games used audio only. No 3D game had bridged these two audiences. Westin's three-year Terraformers project attempted to close this gap by making a real-time 3D action game fully playable without vision while retaining the 3D graphical world for sighted players.

## Key Contributions
- Demonstrated that a commercial real-time 3D game can be simultaneously accessible to blind, low-vision, and fully sighted players
- Catalogued a complete set of non-visual spatial navigation techniques (Sound Compass, Sonar, GPS, Direct Orientation) mapped onto keyboard controls
- Showed that voiced hierarchical menu systems (Backpack, GPS) can serve as a complete non-visual inventory interface
- Provided a post-mortem user survey from blind players evaluating the interface
- Initiated the IGDA Game Accessibility Special Interest Group (GA-SIG) as a direct outcome of this work

## Methodology
Three-year iterative development (November 2000 – December 2003) with ad hoc user testing with blind programmers and students at a Stockholm school for the blind. Post-mortem email survey submitted to the first 35 customers; 4 usable replies received. The game itself is treated as the primary artifact embodying the research findings.

## Accessibility Feature Catalogue

### Non-Visual Spatial Navigation
| Feature | Mechanism | Output |
|---------|-----------|--------|
| Sound Compass | 3D positional sound (north) | Rough 8-direction spoken feedback via numpad key |
| Sonar | 3D sound | Distance-to-object in faced direction; key press announces object type |
| GPS | Voiced menu system | Exact coordinates of objects and avatar; nearby object overview |
| Direct Orientation | Numpad | Avatar faces one of 8 compass directions directly |

### Visual Accessibility
| Feature | Mechanism |
|---------|-----------|
| High Contrast Mode | Parts of 3D scene rendered black/white toon-style, enhancing contrast for low-vision |
| No 3D Graphics Mode | 3D rendering disabled entirely for blind players without GPU hardware |
| CPU-only rendering | Bypasses malfunctioning GPU drivers (common blind user scenario) |

### Other Interfaces
- **Powersuit + voiced PDA**: In-game fiction wrapper that delivers all accessibility feedback
- **Backpack**: Hierarchical voiced menu with dynamic sound effects attached to voices
- **Game objects**: All objects have voiced feedback and 3D positional sound icons
- **Environments**: Ambient sounds + footstep sounds on different ground materials + voiced sensory descriptions

## Parameters / Design Values

| Name | Value | Notes |
|------|-------|-------|
| Compass directions | 8 | N, NE, E, SE, S, SW, W, NW |
| Post-mortem survey sample | 35 sent, 4 usable replies | All respondents were blind |
| Development duration | ~3 years | Nov 2000 – Dec 2003 |
| Minimum tested hardware | Pentium II 350MHz, GeForce II, SoundBlaster Live | Game runs "OK but not optimal" |

## User Survey Results (n=4, all blind)

All four respondents rated overall usability as easy or very easy. All accessibility navigation features (Sonar, Compass, GPS, Backpack) were rated easy to use by all respondents. The tutorial was considered sufficient for learning the interface. Difficulty opinions were mixed (one respondent found it too easy; one found enemies very challenging). Completion times ranged from under 2 hours to approximately 8 hours.

Key negative feedback:
- Enemies too easy / slow (one respondent)
- Character movement felt too slow / unresponsive (possibly performance-related)
- Game crashes (attributed to unstable GPU/sound drivers — a known issue for 3D games, noted as a special problem for blind users who rarely update GPU drivers)

## Implementation Details
- The spatial audio approach uses **3D positional sound** (true spatial audio, not stereo panning) for compass, sonar, and sound icons — allows blind players to localize objects in 3D space
- The **Powersuit** narrative frame is a design pattern: embedding accessibility features within diegetic game fiction reduces stigma and cognitive friction
- All menu systems use the **same voiced menu architecture** — backpack, GPS, communications, and start menu all share one interaction model, reducing learning overhead
- Sound effects can be dynamically attached to voiced menu items at runtime
- High Contrast mode and No-3D mode are independent toggles — not mutually exclusive

## Figures of Interest
- **Figure 1 (page 2):** Side-by-side screenshots of normal contrast vs. high contrast toon-style 3D rendering — clearest visual documentation of the high-contrast mode feature
- **Table 1 (page 3):** Full post-mortem survey matrix — 4 blind respondents, 11 questions, verbatim responses

## Results Summary
The post-mortem survey (n=4, all blind) found the game's accessibility interface to be easy to use across all measured features. The game was commercially released and reached paying customers. The IGDA GA-SIG white paper was initiated as a direct follow-on. The paper is primarily a design documentation/case study, not a controlled experiment.

## Limitations
- Survey has only 4 usable responses — no statistical conclusions possible
- Development evaluation was ad hoc; not documented in writing
- Many survey follow-up questions remain unresolved (respondents were not contacted for clarification)
- Game crashes on some systems due to unstable drivers — special problem for blind users who don't update GPU drivers
- Difficulty balance was inconsistent across players
- Paper is author's own project — no independent evaluation

## Testable Properties
- If voiced menus share a single interaction architecture across all subsystems, then learning one menu subsystem should transfer to all others (cognitive load claim)
- Disabling 3D rendering should not disable audio accessibility features (independent subsystems)
- 8-direction discrete orientation via numpad is a design invariant — not continuous rotation
- High contrast mode and No-3D mode must be independently toggleable (not mutually exclusive)

## Relevance to Project
This is one of the earliest documented case studies of game accessibility for blind players using spatial audio. It predates most game accessibility literature and directly catalyzed the IGDA GA-SIG and the broader game accessibility research community. The accessibility feature taxonomy (Sonar, Compass, GPS, voiced menus) provides a reference vocabulary and concrete implementation patterns for non-visual game interface design. The post-mortem survey methodology is notable: using paying customers rather than lab subjects.

## Open Questions
- [ ] How does this compare to the IGDA GA-SIG white paper Westin helped write in 2004–2005?
- [ ] Are the spatial audio techniques (3D positional sound for compass/sonar) discussed in terms of specific audio APIs or middleware?
- [ ] Does the Bierre et al. 2005 "Game Not Over" paper cite Terraformers directly?
- [ ] What happened to the Terraformers game and Pin Interactive after 2004?

## Related Work Worth Reading
- Gaver 1994 — "Using and Creating Auditory Icons" — foundational reference for the sound icon design used in game objects
- Mynatt 1997 — "Transforming graphical interfaces into auditory interfaces for blind users" — directly relevant to the spatial-audio-as-substitute-for-graphics approach
- Winberg & Hellström 2000 — "Investigating Auditory Direct Manipulation: Sonifying the Towers of Hanoi" — auditory manipulation research cited as related work
- Bierre et al. 2005 — "Game Not Over: Accessibility Issues in Video Games" — the IGDA GA-SIG paper that grew from this work (not yet in collection)

## Collection Cross-References

### Already in Collection
None of the three direct references are in the collection yet.

Adjacent papers already in collection:
- **Yuan_2011_GameAccessibilitySurvey** — the 2011 survey that reviews game accessibility advances from 2005–2010, which explicitly builds on this 2004 work and the IGDA GA-SIG white paper Westin initiated
- **Porter_2013_GameAccessibilityBarriers** — empirical follow-on to the game accessibility problem space Westin helped define

### New Leads (Not Yet in Collection)
- Gaver (1994) — "Using and Creating Auditory Icons" in *Auditory Display* — foundational for audio icon design in accessibility; relevant to hearing accessibility
- Mynatt (1997) — "Transforming graphical interfaces into auditory interfaces for blind users" — *Human-Computer Interaction, 12*, 7-45 — directly relevant to screen reader and audio interface research
- Winberg & Hellström (2000) — "Investigating Auditory Direct Manipulation: Sonifying the Towers of Hanoi" — CHI 2000 — auditory interface research
- Bierre et al. (2005) — "Game Not Over: Accessibility Issues in Video Games" — HCII 2005 — the paper this task originally targeted; grew directly from Westin's IGDA work
