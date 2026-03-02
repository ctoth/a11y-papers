# StreetReaderAI: Making Street View Accessible Using Context-Aware Multimodal AI

**Authors:** Jon E. Froehlich, Alexander Fiannaca, Nimer Jaber, Victor Tsaran, Shaun Kane
**Year:** 2025
**Venue:** UIST '25 (38th Annual ACM Symposium on User Interface Software and Technology), Busan, Republic of Korea
**DOI/URL:** https://doi.org/10.1145/3746059.3747756

## One-Sentence Summary
StreetReaderAI is the first accessible street view tool, combining Gemini Flash 2.0 multimodal AI with custom GSV navigation graphs, accessible keyboard controls, and conversational speech to enable blind users to virtually explore and investigate real-world locations via Google Street View imagery.

## Problem Addressed
Interactive streetscape mapping tools (Google Street View, Meta Mapillary) provide immersive 360-degree imagery for virtual exploration of real-world environments but remain fundamentally inaccessible to blind and low-vision (BLV) users due to reliance on visual panoramic imagery, mouse-driven panning, lack of image descriptions, and inaccessible navigation controls. No prior tool existed that enabled BLV users to independently navigate, investigate, and converse about street view content.

## Key Contributions
- First-ever accessible street view tool enabling blind users to virtually navigate 220+ billion GSV images across 100+ countries
- Three-subsystem AI architecture: AI Describer (concise scene description), AI Chat (conversational Q&A), AI Tour Guide (tourist-focused descriptions) -- all context-aware using geographic data, user profile, and current view
- Custom egocentric GSV navigation graph that extends Google's built-in two-direction links to support four-way (N/S/E/W) intersection navigation with road-matching logic
- Co-design methodology with mixed-visual-ability team and iterative design sessions with blind collaborators
- User study with 11 blind participants demonstrating value for POI investigation and remote route planning
- Identification of key design considerations: concision, orientation support, AI conversational interface, personalization, leveraging streetscape imagery, supporting "last 10 meters" navigation

## Methodology
- **Co-design phase:** Iterative design with two blind co-designers and feedback from professional designers/engineers with disabilities. Three sessions covering initial concept, low-fidelity prototyping, and refined prototype testing.
- **Evaluation:** Single-session in-person lab study, 1.5-2 hours per participant with 11 blind screen reader users (6 men, 5 women, ages 18-66). Four parts: (1) formative interview, (2) POI investigation with tutorial + 4 scenarios, (3) open-world navigation in two geographies, (4) debrief interview. Mixed methods: video recording, screen recording, client-side logger (commands, prompts, responses as timestamped JSON), thematic analysis, 7-point Likert scales.
- **POI tasks:** Coffee shop (tutorial), bus stop, playground, Mexican restaurant -- each with specific questions about physical features, safety, accessibility
- **Navigation tasks:** Walk from Airbnb to ice cream shop (Minneapolis), walk from bus stop to Japanese restaurant (Paris)

## Key Equations

N/A -- this is a systems/HCI paper without formal mathematical models.

## Parameters

| Name | Symbol | Units | Default | Range | Notes |
|------|--------|-------|---------|-------|-------|
| AI response time (AI Chat) | - | ms | Avg=968.6 | SD=678.8 | Via Gemini Live Multimodal API |
| AI response time (AI Describe) | - | ms | Avg=1,916 | SD=265.6 | Slower than Chat |
| Pano heading offset per turn | - | degrees | 45 | 45 or 90 | turnLeft45, turnLeft90, turnRight45, turnRight90 |
| Nearby places search radius | - | meters | 230 | - | 1 master search grid + 1 meter sub-searches per pano |
| Speech output rate | - | - | configurable | - | Natively voiced, togglable with/without screen readers |
| User view image upload | - | pixels | 640x640 | - | Extracted from current position and heading |
| AI accuracy (POI investigation) | - | % | 86.3 | - | 703/816 questions correctly answered |
| AI partially correct | - | % | 3.2 | - | 26/816 |
| AI incorrect | - | % | 3.9 | - | 32/816 |
| AI refused to answer | - | % | 6.6 | - | 54/816 |
| Usefulness rating (overall) | - | 1-7 Likert | Median=7 | Avg=6.4, SD=0.9 | All wanted to use as product |
| How well (POI) | - | 1-7 Likert | Median=6.0 | Mean=6.0, SD=0.7 | - |
| How valuable (POI) | - | 1-7 Likert | Median=7.0 | Mean=6.4, SD=0.6 | - |
| How accurate (POI) | - | 1-7 Likert | Median=6.0 | Mean=5.7, SD=0.9 | - |
| How well (Navigation) | - | 1-7 Likert | Median=6.0 | Mean=6.0, SD=0.9 | - |
| How valuable (Navigation) | - | 1-7 Likert | Median=6.5 | Mean=6.1, SD=1.1 | - |
| How accurate (Navigation) | - | 1-7 Likert | Median=5.5 | Mean=5.5, SD=1.2 | - |
| Total pano moves (study) | - | count | 356 | - | Across all 11 participants |
| Total heading changes (study) | - | count | 568 | - | Across all 11 participants |
| Total AI requests (study) | - | count | 1,053 | - | 136 AI Describe + 917 AI Chat |
| AI Chat per session | - | count | Median=10 | SD=7.5 | - |
| AI Describe per session | - | count | - | ~12.4x less than Chat | - |

## Implementation Details

### Technology Stack
- **Frontend:** TypeScript, Sass (SCSS), HTML using Lit (web components), RxJS (reactive state management), MobX (state observation/synchronization)
- **Backend:** Custom lightweight Python server (Flask), serving static app resources
- **AI Model:** Google Gemini Flash 2.0 (selected for benchmark performance, prototyping ease, multimodal support)
- **Speech:** Google Cloud Text-to-Speech API for output; Google Speech-to-Text API for voice recognition/transcription
- **AI Voice:** Vertex AI platform with Gemini 2.0 Flash model; status messages use male voice ("en-US-Wavenet-J"), chat uses female voice ("en-US-Wavenet-G")
- **API Caching:** IndexedDB (custom, location-based) for API call caching
- **Data APIs:** Google Maps Places API, Google Roads API, Google StreetView API
- **Accessibility:** ARIA live regions (aria-live) for screen reader output; natively voiced (toggleable)

### Navigation Graph Construction
For each GSV pano location:
1. Construct custom egocentric graph from GSV links (Google provides ~2 directions per pano)
2. Draw edges with endpoints in the four cardinal + four intercardinal directions
3. Where GSV only has two built-in links (bidirectional), the system extends to four-way intersection support by matching roads
4. Bridges where two roads cross but do not intersect are treated as same intersection (jump + "jumped" message)
5. Teleporting: search bar using Google Places API earsByText endpoint, teleport to closest pano with editorial summary

### Geographic Context Assembly (per view change/movement)
1. **Closest address** from reverse geocoding
2. **Current heading** (compass direction)
3. **Selected place** (if any)
4. **Neighborhood, city, state/province, country**
5. **Sorted list of nearby places** with business names, types, editorial summaries, `<lat,lng>` positions, distances, heading offsets, relative positions (left/behind user)
6. **User's view** -- 640x640 image uploaded from current position and heading

### Three AI Subsystems

**AI Describer** (Alt+D):
- Primary goal: concise scene awareness for orientation and navigation
- Persona: expert scene describer for BLV users
- Output style: short (1-2 sentences) or JSON format
- Interactivity: on-demand, supplementary (triggered on panning/movement or explicit hotkey)
- Full prompt: custom prompt requesting structured JSON response with alt-disability features, safety, and summary from the prompt persona

**AI Chat** (Alt+C for typing, Alt+Spacebar for speaking):
- Primary goal: navigational cues, interactive Q&A, system control
- Persona: helpful, responsive conversational agent for BLV users
- Output style: conversational text or speech
- Interactivity: real-time chat with on-demand conversation memory
- Supports semantic commands (e.g., "Turn me towards the cafe")
- Function declarations for navigation control: moveBackward, moveForward, moveToIntersection, turnLeft45, turnLeft90, turnRight45, turnRight90, turnAround (Table 3)

**AI Tour Guide** (Alt+T):
- Primary goal: engaging, informative virtual tour experience
- Persona: knowledgeable, engaging tour guide for BLV tourists
- Output style: descriptive narrative (4-5 sentences)
- Focus: historical facts, cultural significance, architectural styles, interesting anecdotes, nearby attractions, human activity descriptions

### Keyboard Controls (Table 1)

| Key | Action |
|-----|--------|
| Left/Right arrows | Rotate left or right 45 degrees |
| Up/Down arrows | Move forward/backward at current heading (if possible) |
| Alt+B | Go back to the last location (pano) |
| Alt+J | Jump to next intersection or 70 meters (230 feet), whichever is first at current heading |
| Alt+D | Describe current view with AI |
| Alt+C | Chat with AI agent (typing) |
| Alt+Spacebar | Talk with AI agent (speaking) |
| Alt+A | Repeat previous output again |
| Esc | Stop current speech output |
| Alt+W | Where am I? (current address and heading) |
| Alt+N | Get information about nearby places |
| Alt+I | Get information about current and next intersection |
| Alt+M | Get possible movements at current location |
| Alt+V/Y | Get visit history for current pano |
| Alt+P | Get date and photographer of current pano |

## Figures of Interest
- **Fig 1 (page 1):** System overview showing accessible streetscape mapping prototype with search, AI descriptions, and conversational AI chat
- **Fig 2 (page 2):** Context-aware multimodal AI Chat architecture: text prompt, user profile, MLLM live chat, panning/movement controls, custom GSV navigation network
- **Fig 3 (page 4):** Co-design process photos showing iterative design with blind collaborators
- **Fig 4 (page 5):** AI Describer output examples with custom prompt structure and contextual information
- **Fig 5 (page 6):** Custom egocentric GSV graph construction showing how 2-direction links are extended to 4-way navigation
- **Fig 6 (page 7):** AI Describer output examples across urban and residential scenes; AI Chat context-relevant follow-up suggestions
- **Fig 7 (page 8):** AI Chat examples from open-world navigation tasks demonstrating spatial orientation support
- **Fig 8 (page 9):** Virtual touring of Parthenon, Eiffel Tower, Grand Canyon via AI Tour Guide
- **Fig 9 (page 9):** Spatial orientation support in AI Chat -- user turns and gets updated directional descriptions
- **Table 4 (page 10):** POI Investigation tasks and questions for 5 scenarios (coffee shop, bus stop, playground, Mexican restaurant)
- **Table 5 (page 11):** Participant demographics, mobility aids, screen readers, mapping tools, AI familiarity
- **Fig 11 (page 12):** Open-world navigation task maps showing heading changes, steps, and distances
- **Table 6 (page 12):** AI Chat question type analysis (N=917) with 23 emergent categories
- **Table 7 (page 14):** Post-task scene questions with AI correctness percentages
- **Table 8 (page 14):** Post-hoc 7-point Likert scale ratings for POI investigation and navigation

## Results Summary

### AI Usage and Performance
- 1,053 total AI requests across study: 917 AI Chat, 136 AI Describe
- Participants used AI Chat 12.4x more than AI Describe on average
- AI Chat response time: Avg=968.6ms (SD=678.8), AI Describe: Avg=1,916ms (SD=265.6)
- Large majority of AI Chat questions voiced (94.4%) vs typed, due to Mac keyboard unfamiliarity and voice/speech affordances
- AI accuracy on 816 questions: 703 correct (86.3%), 32 incorrect (3.9%), 26 partially correct (3.2%), 54 refused (6.6%)

### Question Types (from 917 AI Chat interactions)
1. Spatial orientation (248; 27.0%) -- "How far is the bus stop from where I'm standing?"
2. Object existence (243; 26.5%) -- "Are there soccer fields?"
3. Description requests (169; 18.4%) -- "What's in front of me?"
4. Object/place location (137; 14.9%) -- "Where is the nearest intersection?"
5. Follow-up questions (132; 14.4%) -- "Tell me more about the mural"
6. Nearby places (85; 9.3%) -- "How to get to the door without bumping into any chairs?"
7. Safety/accessibility (51; 5.6%) -- "Is there an assistive pedestrian signal at this light?"

### POI Investigation
- All 11 participants completed POI investigations successfully
- AI correctness on post-task scene questions: bus stop 100%, playground 77-100%, Mexican restaurant 64-100%
- Participants relied primarily on AI Chat and AI Describe, plus Alt+N for nearby places

### Navigation
- 10/11 completed at least one navigation task; average 9.4 minutes per task
- Participants moved 356 panos, made 568 heading changes
- Main navigation strategy: listen to AI descriptions, ask orientation questions, use Alt+N for nearby places
- Ice cream shop task: ~4 heading changes, ~12 steps (107 meters / 350 ft)
- Japanese restaurant task: ~7 heading changes, ~5 steps (73 meters / 240 ft)

### Overarching Themes
- Usefulness rated highly (Median=7/7 overall; Avg=6.4; SD=0.9)
- Accuracy perceived as high (POI Med=6.0, Nav Med=5.5) despite occasional hallucinations
- Key tension: accuracy perceptions influenced by mixing reliable Google Maps data with sometimes-inaccurate AI descriptions
- Building spatial awareness: participants focused heavily on building mental models of spaces via orientation-related AI chats
- Conceptualizing street view controls: challenging to explain immersive 360-degree imagery to blind users; physical role-play (rotating bodies 45 degrees) helped understanding

## Limitations
- Single-session lab study (90 minutes, 11 participants) -- limited ecological validity
- Only evaluated with blind screen reader users, not low-vision users (though designed for both)
- Participants unfamiliar with the keyboard/OS used (Mac), affecting results
- Custom client-side logger lost data for some sessions (batching issue), resulting in <0.6% of logged events
- AI hallucinations remain a concern -- 3.9% incorrect, 6.6% refused to answer
- Navigation graph is constrained by Google's GSV link structure (typically 2 directions per pano)
- No integration with real-time data sources (transit schedules, crowd information)
- Does not yet support "last 10 meters" navigation (building-level granularity, entrance location)
- AI responses sometimes verbose; participants wanted more control over verbosity

## Testable Properties
- AI Describer responses must be concise (1-2 sentences or structured JSON)
- Navigation graph must provide four cardinal direction movements at intersections where roads exist in those directions
- Teleporting to a place must orient the user toward that destination
- Every view change must update geographic context (address, heading, nearby places)
- AI Chat must parse and execute semantic navigation commands (moveForward, turnLeft45, etc.)
- AI Chat accuracy on factual geographic questions (using Google Maps/Places data) should exceed accuracy on visual scene questions (using AI image analysis)
- Nearby places list must be sorted by distance from current position
- Keyboard shortcuts must not conflict with screen reader navigation commands (JAWS, NVDA, VoiceOver)
- All status messages must be surfaced to screen readers via ARIA live regions

## Relevance to Project
This paper is directly relevant to the visual impairment, assistive technology, and web standards topic areas of this collection. It demonstrates a state-of-the-art approach to making a fundamentally visual web application (street view) accessible to blind users through context-aware multimodal AI, advancing the Wobbrock_2011_AbilityBasedDesign framework's Ability and Adaptation principles. The co-design methodology with blind collaborators exemplifies the participatory approach advocated by Mankoff_2010_DisabilityStudiesCriticalInquiry. The system's reliance on geographic APIs (Google Maps, Roads, Places) for reliable context -- rather than AI vision alone -- addresses the accuracy concerns that pervade AI-generated descriptions, connecting to the alt text quality concerns raised by Singh_2024_FigurA11y. The navigation challenges documented here directly relate to the "equivalent purpose" questions raised by Biggs_2025_MapEquivalentPurpose regarding whether non-visual map representations can serve the same purpose as visual ones.

## Open Questions
- [ ] How does extended longitudinal use affect navigation strategies and spatial mental model development?
- [ ] What are the effects of AI hallucinations on trust and safety over time?
- [ ] How would StreetReaderAI perform with low-vision users who could benefit from combined visual and audio output?
- [ ] What is the optimal level of AI description verbosity for different task types?
- [ ] Can the navigation graph be extended with additional data sources (OpenStreetMap, city sidewalk data) for "last 10 meters" navigation?
- [ ] How does the system scale to areas with poor GSV coverage or outdated imagery?

## Related Work Worth Reading
- Asakawa (2005) -- historical blind web browsing context (already in collection as Asakawa_2005_BlindWebBrowsing)
- SoundScape by Microsoft (cited as [90]) -- 3D audio navigation for BLV users
- Cameleon by Saha et al. -- urban accessibility analysis from street view imagery
- Project Sidewalk by Saha et al. -- crowdsourced sidewalk accessibility auditing
- VizWiz and Be My AI -- visual question answering for blind users
- Google Lookout, Seeing AI, Image Describers -- mobile AI scene description tools

## Collection Cross-References

### Already in Collection
- **Wobbrock_2011_AbilityBasedDesign** -- Froehlich is a co-author of both papers; StreetReaderAI embodies the Ability and Adaptation principles
- **Mankoff_2010_DisabilityStudiesCriticalInquiry** -- the co-design methodology with blind users as co-designers reflects Mankoff's participatory design advocacy
- **Asakawa_2005_BlindWebBrowsing** -- historical context for blind web access; StreetReaderAI extends the vision of accessible web experiences beyond static pages to immersive street view
- **Biggs_2025_MapEquivalentPurpose** -- StreetReaderAI directly addresses the map equivalent purpose problem by providing non-visual access to geographic streetscape content; the MEP framework could be applied to evaluate StreetReaderAI's coverage
- **Mack_2021_AccessibilityResearchSurvey** -- StreetReaderAI is a BLV-focused system, contributing to the dominant research area identified in Mack's survey
- **Lazar_2007_ScreenReaderFrustration** -- StreetReaderAI's ARIA live regions and keyboard controls are designed to avoid the screen reader frustration patterns Lazar documented
- **Singh_2024_FigurA11y** -- both papers address AI-generated descriptions for visual content; FigurA11y for scientific figures, StreetReaderAI for streetscape imagery
- **Shneiderman_2000_UniversalUsability** -- StreetReaderAI addresses all three of Shneiderman's challenges (technology variety via web platform, user diversity via BLV-specific design, knowledge gap via tutorial and conversational AI)

### New Leads (Not Yet in Collection)
- Saha et al. (2019) "Project Sidewalk" -- crowdsourced sidewalk accessibility assessment from street view imagery
- Saha et al. (2021) "Urban Accessibility Analysis" -- using deep learning on street view to assess urban accessibility
- Gurari et al. (2018) "VizWiz Grand Challenge" -- visual question answering from blind users' photos
- Zhao et al. (2019) "AR Visualizations for Stair Navigation" -- accessible AR for low-vision users (UIST '19)
- Microsoft SoundScape -- 3D audio-based spatial navigation for blind users
- Bigham et al. (2010) "VizWiz" -- mobile system enabling blind users to ask visual questions

### Supersedes or Recontextualizes
- **Biggs_2025_MapEquivalentPurpose** -- StreetReaderAI provides a concrete implementation that goes far beyond the text-based map representations Biggs evaluated, offering conversational AI-mediated access to the full richness of streetscape imagery. StreetReaderAI could serve as a benchmark system for future MEP evaluations.
