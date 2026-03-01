# An Empirical Study of Issues and Barriers to Mainstream Video Game Accessibility

**Authors:** John R. Porter, Julie A. Kientz
**Year:** 2013
**Venue:** ASSETS 2013 — Proceedings of the 15th International ACM SIGACCESS Conference on Computers and Accessibility
**DOI:** 10.1145/2513383.2513444
**URL:** https://faculty.washington.edu/jkientz/papers/Porter-GameAccessibility-ASSETS2013.pdf

## One-Sentence Summary
Dual empirical study (55-gamer survey + 6 industry interviews) that documents the actual barriers disabled gamers face in mainstream commercial games and the industry-side reasons those barriers persist.

## Problem Addressed
Prior game accessibility research relied on assumed impairment models (like Yuan 2011's Game Interaction Model) rather than empirical data from disabled gamers. Simultaneously, guidelines existed but were not being adopted — and no one had asked industry practitioners why. This paper fills both gaps.

## Key Contributions
- Empirical taxonomy of real-world accessibility barriers from 55 gamers with disabilities (open coding → thematic analysis)
- Industry-side barrier analysis from 6 semi-structured interviews with game developers/publishers
- Priming activity: coded top 10 grossing PC games of 2011 against IGDA GA SIG's "Top Ten" accessibility guidelines — partial/inconsistent compliance across all 10 games
- Identification of middleware as the most promising structural intervention for game accessibility
- Finding that assistive technology incompatibility (not missing features per se) is the dominant barrier class

## Study 1: Gamer Survey

### Method
- N=55 gamers with disabilities
- Recruited via Twitter, disability mailing lists, AbleGamers Foundation guest post
- Mix of closed-ended (platform, play style frequency) and open-ended (barriers, experiences) questions
- Open coding → affinity grouping for qualitative data
- Incentive: $50 Amazon gift card drawing

### Participant Demographics
| Attribute | Distribution |
|-----------|-------------|
| Total | 55 |
| Age | 10-29 (51%), 30-39 (20%), 40-49 (20%), 50-59 (5%), 60+ (2%) |
| Gender | Male (58%), Female (38%), Other (2%) |
| Motor impairment | 69% |
| Hearing impairment | 16% |
| Cognitive impairment | 15% |
| Visual impairment | 11% |

Note: impairment classes not mutually exclusive.

### Quantitative Findings
- PC/Mac/Linux is the most popular platform across all impairment classes
- Console is second most popular (hearing-impaired gamers favor it most)
- Handheld gaming (DS, Vita) has the lowest adoption among motor, visual, and cognitive impaired participants
- Multiplayer gaming (both online and in-person) is engaged in far less frequently than single-player independent gaming — across all impairment classes
- Collaborative single-player most common among motor and hearing impaired participants

### Qualitative Themes (from open coding)

**1. Incompatibility with assistive technologies**
- The dominant barrier category. Gamers report that their required ATs simply do not work with games.
- Screen readers cannot parse game UI (visual impairment)
- Custom input programs (AutoHotKey, on-screen keyboard) not recognized by game input systems (motor)
- Modified assistive controllers fail on consoles despite peripheral licensing (motor)
- Gamers express confusion and frustration that the same AT works in some games but not others
- Blame attributed to game developers for not testing with ATs

**2. Asking for help (social workaround)**
- When ATs fail, gamers frequently recruit able-bodied friends/family/PCAs to assist with specific barriers (QTEs, timed sequences, complex input)
- Reluctance accompanies this strategy — described as diminishing gameplay experience
- Some gamers refuse this workaround entirely, choosing instead to forgo the game
- Authors note this connects to "human-powered access technology" concept (Bigham et al. 2011)

**3. Motor impairment complicating multiplayer**
- Motor-impaired gamers report perceived inability to be competitive ("keep up," "level playing field")
- Many have abandoned multiplayer entirely or shifted to slower-paced game genres (casual, sim)
- Social pressure compounds technical barriers: fear of "acting atypical" leads to avoidance even when competitiveness is not actually impaired
- Cognitive-impaired gamers report communication difficulties causing negative reactions from other players

## Study 2: Industry Interviews

### Method
- N=6 industry participants (P1-P6), various roles
- 4 interview sessions (3 participants from same company interviewed as group)
- Semi-structured; initial questions + follow-up using Table 1 (priming activity results) as prompt
- Recruited via word-of-mouth and cold-contact in Seattle area
- Audio recorded, transcribed, open-coded, grouped into themes

### Industry Themes

**1. "Low-hanging fruit" comes first**
- Colorblind-friendly palettes and subtitles are addressed early because they are easiest and most obvious
- Complexity of the impaired population determines accessibility effort: hearing impairment has a near-one-to-one solution; motor impairment has enormous within-population variance, making it much harder
- Quote (P1): motor impairment — "one person's needs can be so different from the next, and the same solution won't work for both"

**2. Value of in-house expertise**
- Studios with disabled employees catch accessibility issues organically, early in development cycle
- P4: colorblindness coverage via colorblind staff — "We sort of cheat at [attention to colorblindness] because we have several colorblind people in the studio"
- P6: a test coordinator with hand impairment caused controls to be made remappable during pre-alpha
- Industry was historically dominated by young men without disability experience; demographic shift is gradually changing this

**3. Pressure to adhere to standards must come from above**
- Accessibility only gets prioritized if it comes from directors, executives, or stakeholders (P1)
- Legislation cited as the most effective potential driver — 21st Century Communications Act mentioned as already having impact (P2)
- Quote (P1): "Buildings have ramps because of legislature and mandates, not because every architect decided to follow best practices"

**4. Role of middleware (most actionable theme)**
- Middleware = game engines (Unreal Engine, Unity, Gamebryo, etc.) — foundational code shared across titles
- AT integration (e.g., screen reader parsability, text-to-speech) requires OS-level accessibility hooks that individual studios cannot feasibly build from scratch
- Quote (P6): tagging game UI with metadata for blind players "wouldn't really be that intensive... But the problem is, that information has to get sent out to the OS level in a way that is compliant with what the text-to-speech system is listening for, and that's something that wouldn't be feasible to develop from scratch. It would have to be supported by our engine."
- Quote (P2): "Having game developers reinvent the wheel every single time they do a game with accessibility is going to be a pain. If the Unreal engine itself supported some core accessibility functionality... you're much more likely to get people to [follow accessibility guidelines]"
- Proposed solution: PC accessibility specialists should engage directly with console manufacturers and middleware developers to inject standardized accessibility hooks

**5. Difficulty implementing AT on consoles**
- Consoles are "walled gardens" — proprietary peripheral ecosystems require manufacturer approval and chip inclusion
- No USB/Bluetooth open standard equivalent on consoles
- Approval processes through Microsoft and Sony are costly and restrictive
- PC's transition to the living room theorized as the likely resolution

## Priming Activity: Top 10 PC Games of 2011

Coded 10 top-grossing PC games against 11 IGDA GA SIG guidelines:

| Guideline | Compliance pattern |
|-----------|-------------------|
| Controller reconfiguration | Near-universal compliance |
| Colorblind-friendly | Near-universal compliance |
| Volume controls | High compliance |
| Sound alternatives | Mixed |
| High visibility | Mixed |
| Difficulty control | Inconsistent — several games fail entirely |
| Speed control | Inconsistent — several games fail entirely |
| Practice/tutorial | Mixed |
| Accessible menus | Mixed |
| Alternative controllers | Mixed |
| Feature list | Almost universally missing |

Key finding: even the "easy" guidelines (colorblind, controller reconfig) are not universally met; most guidelines show inconsistent adoption; listing accessibility features is almost never done.

## Limitations
- Survey N=55 is small and non-representative; motor-impaired gamers likely over-represented due to AbleGamers recruitment vector
- Only 6 industry participants; middleware developer perspective not obtained (recruitment failed)
- Impairment classification only at class level (not severity/type within class)
- PC-only priming activity (first author is a PC gamer)
- Study presented as "first step" — acknowledges need for more comprehensive follow-up

## Testable Properties
- PC platform adoption > console > handheld among disabled gamers (especially motor/visual/cognitive)
- Multiplayer engagement frequency < single-player independent engagement for all impairment classes
- AT incompatibility is the most-cited barrier category (not missing features like subtitles/colorblind modes)
- "Low-hanging fruit" accessibility features (colorblind, subtitles) have higher industry adoption than complex motor accessibility features

## Relevance to Project
Direct empirical complement to Yuan_2011_GameAccessibilitySurvey. Where Yuan provides a theoretical taxonomy of impairment-to-step-to-solution, Porter provides ground-truth data on what barriers actually manifest in practice. The middleware finding is particularly significant: it identifies the structural intervention point (game engines) rather than individual game design decisions. The AT incompatibility theme ties directly to screen reader research (Lazar_2007_ScreenReaderFrustration) — the same class of AT/application conflict that manifests on the web manifests in games. The social assistance workaround pattern is an underexplored design space connecting to human-powered accessibility.

## Open Questions
- [ ] What is the current (post-2013) state of middleware accessibility support? Unity, Unreal, and Godot have all made accessibility investments since this paper.
- [ ] Does the motor-impaired gaming population domination hold in later studies, or was it truly AbleGamers recruitment bias?
- [ ] Have the console "walled garden" constraints loosened with Xbox Adaptive Controller (2018) and similar?
- [ ] Is the social assistance workaround (human-powered access) now supported by any platform features (Share Play, co-pilot modes)?

## Related Work Worth Reading
- Yuan et al. 2010 — Game accessibility survey (already in collection as Yuan_2011_GameAccessibilitySurvey)
- Bigham, Ladner, Borodin 2011 — Human-powered access technology (ASSETS '11) — directly cited as framing for social assistance workaround
- Trewin et al. 2009 — PowerUp accessible virtual world study (TACCESS) — cited as best prior empirical work; Porter extends beyond it
- Bierre et al. 2004 — IGDA GA SIG white paper — the guideline source used in priming activity
- Miesenberger et al. 2008 — More Than Just a Game: Accessibility in Computer Games

## Collection Cross-References

### Already in Collection
- **Yuan_2011_GameAccessibilitySurvey** — Porter [27] cites Yuan as the prior theoretical framework; Porter is positioned as the empirical complement, providing gamer-reported data that Yuan's heuristic model lacked. Read together: Yuan gives the taxonomy of what barriers exist in principle; Porter gives the empirical record of which ones actually manifest.

### New Leads (Not Yet in Collection)
- Bigham, Ladner, Borodin (2011) — "The design of human-powered access technology" (ASSETS '11) — Porter frames social gaming assistance (relying on friends/PCAs) as a case for human-powered AT; this paper defines that concept
- Trewin, Laff, Hanson, Cavender (2009) — "Exploring Visual and Motor Accessibility in Navigating a Virtual World" (TACCESS) — best prior empirical work on game/virtual world accessibility; Porter explicitly extends this
- Miesenberger et al. (2008) — "More Than Just a Game: Accessibility in Computer Games" — framing paper for the social participation argument in game accessibility
- Bierre et al. (2004) — IGDA GA SIG white paper "Accessibility in Games: Motivations and Approaches" — the foundational industry guidelines document

### Supersedes or Recontextualizes
- **Yuan_2011_GameAccessibilitySurvey**: Porter does not supersede Yuan but recontextualizes it — Yuan's Game Interaction Model provides the theoretical mapping, but Porter shows the model had limited empirical basis. The papers are complementary and should be read as a pair.
