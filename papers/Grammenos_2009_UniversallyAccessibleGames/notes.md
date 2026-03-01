# Designing Universally Accessible Games

**Authors:** Dimitris Grammenos, Anthony Savidis, Constantine Stephanidis
**Year:** 2009
**Venue:** ACM Computers in Entertainment, Vol. 7, No. 1, Article 8
**DOI:** 10.1145/1486508.1486516

## One-Sentence Summary

This paper introduces the UA-Games (universally accessible games) concept and demonstrates it through four concrete case studies — UA-Chess, Access Invaders, Game Over!, and Terrestrial Invaders — providing a unified design methodology and the concept of Parallel Game Universes for concurrent cross-disability multiplayer play.

## Problem Addressed

Computer games are demanding in motor, sensory, and cognitive skills; existing approaches either retrofit accessibility via third-party assistive technology (low quality, no upward compatibility) or build separate disability-specific games (expensive, socially segregating). Neither approach allows people with diverse abilities to play together simultaneously in a shared social experience. The paper addresses the gap: no games existed that could be concurrently played by sighted, blind, and motor-impaired people with no special adjustments or modifications.

## Key Contributions

1. **UA-Games concept**: Defines "universally accessible games" as games proactively designed to optimally fit and adapt to individual gamer characteristics, concurrently playable by people with diverse abilities without particular adjustments.
2. **Unified design method for UA-Games**: A 5-step iterative process adapted from unified user interface design (Savidis and Stephanidis 2004): (1) Abstract task-based game design, (2) Polymorphic specialization with design alternatives, (3) Appropriateness analysis, (4) Compatibility analysis among alternatives, (5) Prototyping and usability/accessibility evaluation.
3. **Four case studies**: UA-Chess (web chess), Access Invaders (Space Invaders remake), Game Over! (intentionally inaccessible educational tool), Terrestrial Invaders (accessible Space Invaders).
4. **Parallel Game Universes (PGU) concept**: A framework for multiplayer UA-Games where each player plays in their own optimally adapted "game universe" connected via transition functions.

## Methodology

The unified design method (Figure 1, page 8:7) is a top-down, iterative, participatory process:
- Begins with abstract task definition (context-independent game logic)
- Performs polymorphic specialization: generate multiple concrete interaction designs for each disability user group
- Analyses appropriateness of each design alternative for each target user group
- Analyses compatibility among alternatives (can they coexist in a single game?)
- Prototypes and evaluates with representative end-users with diverse characteristics
- Iterates — can return to any previous step

Evaluation used the IBM Usability Satisfaction Questionnaires (Lewis 1995), adapted for the game context. Scores below 3 (on an unspecified scale) are considered "very good."

## Key Algorithms / Design Patterns

### Hierarchical Scanning (Motor-Impaired Access)
- A colored "focus frame" moves through interaction objects using any binary switch or keyboard key
- Two object types:
  - **Container objects**: group related items; scanning "locks in" to contents when selected; has Select state (green rectangle) and Exit state (red rectangle with X)
  - **Simple objects**: no sub-items; selection triggers the corresponding action
- **Automatic scanning**: single switch moves focus at constant time intervals automatically
- **Manual scanning**: user explicitly advances focus (even zero switches needed in auto mode)
- The X symbol distinguishes exit state for color-blind users

### Nonvisual Navigation (Blind Access)
- Modified hierarchical scanning with no "lock-in": when the last item in a container is reached, focus moves to the next item at the same level (like Tab key behavior in Windows apps)
- Output: aural (speech + audio) — integrated screen reader that reads game events, focused objects, and game state
- Added-value orally-accessible info: selected piece, board contents, opponent piece positions (via menu/shortcuts)
- Voice input: feedback only on reversible commands (reversible → read aloud; irreversible critical actions → explicit confirmation required)

### Profile-Driven Adaptation
- Two profile types:
  - **Fixed profiles**: alterable during session but not saved; ensures baseline accessibility regardless of session changes (e.g., blind profile cannot have speech disabled by another player)
  - **User-defined profiles**: permanently stored preferences
- Profile bootstrap paradox: the profile-selection dialogue itself must already be accessible — solution is to embed maximum redundant accessibility features in that dialogue

### Parallel Game Universes (PGU)
- Each player plays in their own "game universe" (adapted version of the game)
- A **transition function** (fT) translates events from one universe to another in a format suitable for each universe's representation
- "Shared" elements: if a game element is destroyed in one universe, it is destroyed in all its instances in other universes
- Implementation requirements for incompatible universes: dedicated audio hardware (extra sound cards, earphones), potentially multiple displays or computers
- Two modes for competitive play fairness:
  1. **Collaborative gaming**: control shared among multiple players (like WWII biplanes); hardware example: Team Xtreme (N64 box, 1–5 switches)
  2. **AI-supported gaming**: AI compensates for individual player weaknesses (e.g., aiming assist for motor-impaired players)

## Parameters / Thresholds Observed

| Feature | Value | Notes |
|---------|-------|-------|
| UA-Chess zoom | Up to 2400% | Single chess piece fills entire screen |
| UA-Chess resize on 17" monitor | Chess pieces up to 2×2 cm | Screen magnification via vector graphics |
| UA-Chess scanning speed | Constant time intervals (automatic mode) | Configurable |
| Access Invaders controls | Keyboard, mouse, joystick, gamepad, binary switches | All supported in parallel |
| Access Invaders spaceship commands | 3: move left, move right, fire | Minimum control set |
| Game Over! levels | 21 | Each violates one accessibility guideline |
| Game Over! lives per level | 3 | Must lose 3 lives to advance |
| Game Over! score penalty | -100 points per life lost | |
| UA-Chess usability evaluation | 6 participants, ages 19–25 | 1 able-bodied, 2 blind, 3 motor-impaired (1, 2, 3 switches) |
| Access Invaders usability | 9 participants, ages 19–30 | 3 able-bodied, 3 blind, 3 motor-impaired |
| IBM USQ threshold | <3 = "very good" | All metrics for blind and motor-impaired were below 3 |
| Game Over! feedback | 49 feedback forms, 239 registrations | Web-based evaluation |
| Game Over! recommendation rate | 71% "definitely" + 14% "probably" would recommend | Developers recommending to peers |
| Game Over! educational usefulness | 47% "very much" + 37% "much" | For teaching game accessibility |

## Implementation Details

### UA-Chess (ActionScript 2.0, Flash)
- Runs in any Web browser with Flash Player plugin
- User categories supported: sighted, low vision, blind, hand-motor impaired, mild memory/cognitive impairment
- Two-player mode: local (same computer — UI switches between player profiles automatically) or remote (over Internet)
- Input modalities: mouse, keyboard, any binary switch, speech recognition (SALT technology for voice-enabled Web apps)
- Self-voicing: built-in screen reader (not reliant on external AT)
- UI components: (a) Menu bar, (b) Board (8×8, A–H columns, 1–8 rows), (c) Active player indicator, (d) Moves history list with plain-language descriptions, (e) Command feedback line
- Board orientations: 8 alternatives (white at bottom/left/top/right, plus mirror variants; Fig. 6)
- Visual cues for cognitive users: last move, valid moves highlighted, selected move, selected piece, check indicator (Fig. 5)
- Pawn promotion: click-on-board dialogue
- Commandline input supported: type "F3F5" to move piece from F3 to F5

### Access Invaders (multiplatform)
- Profile-driven: 13 adaptation categories across Game Content and Game Rules (Table I, p. 8:15):
  - Game Content: Speed, Quantity, Size, Layout, Firepower, Visual complexity, Contrast, Sound
  - Game Rules: Interaction among game elements, Analogue vs. digital control, Hints, Stamina
- Internally: single application with runtime polymorphism (Savidis and Stephanidis 2004)
- Externally: appears as collection of distinct accessible game versions
- Blind player-specific: 3D sonification required; fewer aliens; instant-target bullets; no shields; discrete movement + auditory feedback when in firing position
- Cognitive impairment: avoid blinking/flashing graphics (seizure risk at certain rates); visualize moving object paths; simplify overall game

### Terrestrial Invaders
- Descendent of Access Invaders, byproduct of Game Over! development
- Full accessibility feature list (p. 8:20):
  - Adjustable overall game speed
  - Adjustable enemies' speed (can be stopped completely)
  - Adjustable size of all game graphics
  - Adjustable size of player bombs
  - Separately adjustable FX, music, and speech volume
  - Optional specification of max concurrent enemy bullets
  - 2D sound for locating objects on 2D plane
  - Spatially located captions (text and/or graphics) for visualizing all game sounds
  - Reading aloud + automatic scanning of game menus
  - Two high-contrast modes (bright graphics on dark; dark on bright)
  - Two novel audio description types: summary and detailed (verbalize relative positions of attacking spaceships, warn of incoming fire)
  - Simple shapes option (rectangles, ellipses) for severe visual impairment
  - Cheats: extra life, destroy random enemy, activate shield
  - Controls can be redefined via XML level description files
  - Supports: multiple keyboard keys/switches, single key (one-switch), mouse, typed keywords ("left"/"right"), microphone blow (with auto-gain)
  - Multiple concurrent players and multiple enemy groups

## Figures of Interest

- **Fig. 1 (page 8:7)**: The unified design process flowchart — 5 steps with throwaway prototypes, expert/user assessment, and iterative feedback loops
- **Fig. 2 (page 8:9)**: UA-Chess visual interface — shows 5 labeled components (menu bar, board, active player, moves list, command feedback)
- **Fig. 4 (page 8:11)**: Scanning focus frame states — (a) select state (green rectangle), (b) exit state (red rectangle with X)
- **Fig. 5 (page 8:13)**: Available visual cues — last move, valid moves, selected move, selected piece, check
- **Fig. 6 (page 8:13)**: 8 alternative board orientations
- **Table I (page 8:15)**: Access Invaders adaptation categories — 8 game content + 5 game rules categories
- **Fig. 8 (page 8:17)**: Access Invaders profile screenshots — basic, single-switch, X-Large, nonvisual
- **Fig. 10 (page 8:21)**: Terrestrial Invaders adaptation screenshots — audio captions, magnification, high contrast, simplified graphics
- **Fig. 11 (page 8:22)**: Parallel game universes diagram — two single-player games X and Y merging into multiplayer game X∩Y
- **Fig. 12 (page 8:24)**: Competitive PGU example — blind player (2D Pong-like) vs. sighted player (3D tennis simulation) connected by transition function fT

## Results Summary

- UA-Chess: All IBM USQ metrics below 3 (very good) for blind and motor-impaired users; participants enthusiastic about playing computer games; unknown-opponent reveal during evaluation increased engagement
- Access Invaders: IBM USQ overall "very good"; social value of UA concept created positive attitude, forgiving users; blind players complained about speech/sound quality and lack of auditory help; difficulty calibration a problem (too hard or too easy)
- Game Over!: 71% would definitely recommend to other game developers; 84% found it useful/very useful as educational tool; 38%+ of those knowing <50% of guidelines said they learned "very much" or "much"
- Formal HCI accessibility evaluation tools assessed as "less than adequate or insufficient" for game contexts

## Limitations

- Concurrent multiplayer with incompatible output universes requires extra hardware (sound cards, earphones, multiple computers)
- The "transition function" between incompatible PGUs is not fully formalized or automated
- No formal accessibility evaluation methodology exists for games; current HCI tools are inadequate
- Some games intrinsically cannot be universally accessible (e.g., "find the song title from a melody" for deaf users; complex strategy games for severely cognitively disabled)
- Gameplay coherence may be reduced when adapting for extreme accessibility needs — authors argue this is acceptable given the social inclusion benefit
- Sample sizes in usability evaluations are small (6–9 participants)
- Voice recognition usability poor for non-native speakers

## Testable Properties

- A UA-Game profile-selection dialogue must itself be accessible: any accessibility feature required in the game must be present in the profile dialogue
- Fixed profiles must override session-level changes: a blind user's speech output cannot be disabled by a co-player's session actions
- In hierarchical scanning, every interaction object must be reachable with a single binary switch; focus must cycle through all objects
- In the PGU model, destroying a shared game element in universe A must destroy it in all other universes; this is an invariant of the shared-element relationship
- Automatic scanning speed must be independently configurable from game speed (they are separate parameters)
- Voice input must provide explicit confirmation for irreversible critical actions and implicit (aural) feedback for reversible ones

## Relevance to Project

This paper is the primary implementation reference for game accessibility, directly cited by Yuan_2011_GameAccessibilitySurvey as a foundational case study. It provides: (1) a concrete, step-by-step design methodology for building cross-disability games; (2) detailed implementation specifications for hierarchical scanning, nonvisual navigation, and profile-driven adaptation that can be implemented in any game engine; (3) the Parallel Game Universes framework for multiplayer accessibility; (4) Table I (Access Invaders adaptation categories) as a practical checklist for game adaptation parameters across disability types. For this collection, it is the most implementation-specific game accessibility paper, filling the gap between Yuan 2011's conceptual framework and actual game construction.

## Open Questions

- [ ] How does the transition function fT work mathematically for incompatible universes? The paper describes the concept but does not formalize it
- [ ] How many switches constitute the practical minimum for each disability level — the paper gives examples (1–3) but no principled taxonomy
- [ ] How does the runtime polymorphism architecture (Savidis and Stephanidis 2004) actually structure the code — this is referenced but not detailed here
- [ ] What constitutes an "acceptable" level of gameplay coherence degradation under universal access constraints?

## Related Work Worth Reading

- Savidis and Stephanidis (2004) — "Unified user interface design: Designing universally accessible interactions" — the foundational design methodology underlying all UA-Games work
- Grammenos et al. (2007) — "Unified design of universally accessible games" — elaborates each step of the design process described here
- Ntoa et al. (2004) — "FastScanner: An accessibility tool for motor impaired users" — the switching/scanning technology underlying motor access
- McCrindle and Symons (2000) — "Audio Space Invaders" — early audio-game predecessor

## Collection Cross-References

### Already in Collection
- **Yuan_2011_GameAccessibilitySurvey** — cites Grammenos et al. 2009 extensively; this paper provides the concrete implementation details that Yuan 2011 surveys at a high level

### New Leads (Not Yet in Collection)
- Savidis and Stephanidis (2004) — "Unified user interface design" — the formal methodology foundation; highly relevant for universal design topic area
- Grammenos et al. (2007) — UAHCI conference paper — the detailed design process elaboration
- Bierre et al. (2005) — "Game not over: Accessibility issues in video games" — cited as overview of game accessibility problems, potentially useful survey
- Ntoa et al. (2004) — "FastScanner" — motor accessibility tool directly used in UA-Chess
- IGDA GA-SIG (2004) — White paper on game accessibility — industry guidelines document; Game Over! levels are based on this

### Supersedes or Recontextualizes
This paper provides the primary source for the UA-Chess and Access Invaders case studies that Yuan_2011_GameAccessibilitySurvey cites. Yuan's survey relies on this paper's findings; reading them together shows that Yuan 2011's "high-level strategy" taxonomy maps directly onto Grammenos's Table I adaptation categories.
