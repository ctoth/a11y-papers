# Accessible Interactive Maps for Visually Impaired Users

**Authors:** Julie Ducasse, Anke Brock, Christophe Jouffrais
**Year:** 2018
**Venue:** Book chapter in "Mobility in Visually Impaired People - Fundamentals and ICT Assistive Technologies" (Springer), Editors: E. Pissaloux, R. Velazquez
**DOI/URL:** https://arxiv.org/abs/2208.14685 / http://www.springer.com/in/book/9783319544441

## One-Sentence Summary
A comprehensive taxonomy and review of three decades of interactive map prototypes for visually impaired users, classifying them into Digital Interactive Maps (DIMs) and Hybrid Interactive Maps (HIMs) with subcategories by input/output modality, and comparing them on content, readability, interactivity, and spatial cognition support.

## Problem Addressed
No agreed-upon terminology or classification existed for the diverse field of accessible interactive maps. Prior surveys (Zeng & Weber 2011; Kaklanis et al. 2013) covered narrower design spaces. This chapter provides the first comprehensive classification spanning all interactive map types designed specifically for visually impaired users, from Parkes' 1988 NOMAD prototype through 2016 systems.

## Key Contributions
- A two-level classification of accessible interactive maps: Digital Interactive Maps (DIMs) vs. Hybrid Interactive Maps (HIMs), with subcategories by input device and physical display type
- Systematic review of ~60 interactive map prototypes with detailed descriptions of interaction techniques, feedback modalities, and evaluation results
- Comparative analysis across five dimensions: map content, map readability, haptic frame of reference, map interactivity, and spatial cognition support
- Identification of four future research directions: open data, authoring tools, shape-changing interfaces, and 3D printing with embedded interactivity

## Methodology
Exhaustive literature search across ACM Digital Library, SpringerLink, IEEE Explorer, and Google Scholar. Inclusion criteria: (1) designed specifically for visually impaired people, (2) published in journals or peer-reviewed conferences, (3) implemented (not just conceptual), (4) one publication per prototype unless major changes between versions.

## Classification Taxonomy

### Digital Interactive Maps (DIMs)
Maps displayed purely on flat digital surfaces (screen, projected surface). No physical elements.

**II.1.1 Regular 2D pointing devices:**
- **Keyboard:** iSonic (Zhao et al. 2008) - 3x3 grid mapped to numpad for choropleth maps. Keyboards mainly used as complement, not primary spatial input.
- **Joystick:** Picinali et al. (2014) - virtual environment navigation. Joysticks suffer from relative cursor displacement making position tracking difficult without vision.
- **Tangible pointing devices:** Mouse (NASA Earth+), pen/stylus (Milne et al. 2011; Daunys & Lauruska 2009; Brittell et al. 2013). Mouse problematic due to lift-and-move disorientation.

**II.1.2 Pointing devices with additional somatosensory feedback:**
- **Force feedback:** Force-feedback mice (Rice et al. 2005 - haptic grid overlay), gamepads (BATS - Parente & Bishop 2003), handle devices (Geomagic Touch X - 6 DoF; Novint Falcon - 3 DoF). HaptiRiaMaps (Kaklanis et al. 2011) used OSM data with haptic device.
- **Cutaneous feedback:** Pin-array mice (VTPlayer - 4x4 pin arrays under fingers), Tactos (Tixier et al. 2013 - braille cells + pointing device), latero-tactile displays (Levesque et al. 2012).

**II.1.3 Finger-based exploration:**
- **Touchscreens:** Jacobson (1998) - touchpad prototype. TimbreMap (Su et al. 2010) - sonification of floor plans on smartphone. TouchOverMap (Poppinga et al. 2011). Carroll et al. (2013) - weather map on tablet. Tikisi (Bahram 2013).
- **Tabletops:** Kane et al. (2011) - Edge Projection, Neighborhood Browsing, Touch-and-Speak techniques. Touch-and-Speak was fastest; Edge Projection second.
- **Camera-based:** KnowWhere (Krueger & Gilden 1997) - camera above illuminated table. AccessLens (Kane et al. 2013) - gesture/voice commands over paper documents. Bardot et al. (2014, 2016) - smartwatch-based motion tracking with mid-air gestures.

### Hybrid Interactive Maps (HIMs)
Maps with both digital and physical display components.

**II.2.1 Interactive Tactile Maps (ITMs):**
- **Interactive Raised-Line Maps:** Parkes (1988) NOMAD - first prototype. Weir et al. (2012) - weather maps. Senette et al. (2013) - street names via TTS. Brock et al. (2014, 2015) - gestural interaction, 24 blind participants showed interactivity shortened exploration time. Mappie (Brule et al. 2016) - multi-color overlay for blind + low vision + sighted collaboration. MapSense (Brule et al. 2016) - 14 additional tangibles with multisensory (olfactory) cues.
- **Commercial products:** ABAplans (AudioTactile association, Geneva) - raised-line overlay on mono-touch surface. IVEO (ViewPlus) - mono-touch sensitive surface with editor.
- **Camera-based ITMs:** Tactile Graphic Helper (Fusco & Morash 2015) - camera recognizes tactile layout and tracks fingers. Sullivan & Picinali (2014) - Leap Motion for pointing at tactile map elements. Gotzelmann & Pavkovic (2014) - automated 3D-printed maps with smartphone tracking.

**II.2.2 Tangible Maps:**
- Physical objects represent map elements (not just pointing devices). Schneider & Strothotte (2000) - building blocks for itinerary construction. Ducasse et al. (2016) - Tangible Reels (retractable strings for lines + stable objects for points), 8 VI users, 283/288 objects correctly placed, 24s average per object.

**II.2.3 Refreshable Tactile Maps:**
- Raised-pin displays using electromagnetic, piezoelectric, shape memory alloy, pneumatic, or heat pump actuation. BrailleDis 9000 (Zeng & Weber 2010) - 7200 pins in 60x120 matrix. ATMap (Limin Zeng & Weber 2012a) - pan, zoom, annotation sharing. Schmitz & Ertl (2012) - Hyperbraille display. Resolution drastically limited by pin count and device size.

## Comparative Analysis (Section III)

### Map Content
| Map Type | Content Capability | Limitations |
|----------|-------------------|-------------|
| DIMs (2D pointing) | Choropleth maps, few landmarks only | Mostly regions, very simple |
| DIMs (finger-based) | Simple maps, limited elements | Cannot distinguish close/crossing lines |
| DIMs (force-feedback) | Complex geographical areas possible | Haptic feedback enables more detail |
| HIMs (ITMs raised-line) | Complex maps with patterns for points/lines/areas | Static overlay constrains content |
| HIMs (Tangible) | Limited by physical icon size | Lines difficult, two prototypes only |
| HIMs (Refreshable) | Various patterns but limited resolution | Pin count constrains complexity |

### Map Readability
- **Number of points of contact:** Single-point-of-contact exploration is cognitively demanding (Loomis et al. 1991). Two-handed exploration significantly more efficient (Wijntjes et al. 2008a). Only GRAB (Iglesias et al. 2004) among DIMs provided two contact points. HIMs inherently support multi-point.
- **Haptic frame of reference:** Isometric devices (keyboard, joystick) provide no external haptic reference. Isotonic devices (mouse, handle) provide some reference but can be confusing. Direct touch on touch-enabled devices provides reliable reference (device outline = map boundary). HIMs provide the most stable haptic reference via physical display features.

### Map Interactivity
- All prototypes share basic element selection/naming.
- DIMs: Easily support panning/zooming but without tactile cues, creates cognitive challenges.
- ITMs: Cannot dynamically change overlay; must pre-print overlays for different views/scales.
- Tangible Maps: Objects can be moved/added/removed but rescaling requires full reconstruction ("scalability problem" - Shaer et al. 2009).
- Refreshable Maps: Most dynamic - can update instantly, support zoom/pan/annotation.
- Adapted exploration functions: distance computation, spatial/semantic filtering, overview ("gist"), search, locate-relocate-relate (Kane et al. 2011).

### Spatial Cognition
- Tactile maps preserve spatial relations within 1-2 hand-spans, demand smaller working memory than real environments (Thinus-Blanc & Gaunet 1997).
- DIMs with audio output: Users can build correct mental representations (Picinali et al. 2014; Simonnet et al. 2009). Adding vibration/tactile feedback makes sketch maps more accurate (Yatani et al. 2012).
- Interactive Tactile Maps: Significantly more efficient for spatial learning than non-interactive tactile maps (Brock et al. 2015). Jacobson (1996) showed interactive map users produced more accurate sketch maps than mobility instructor-led route learners.
- Refreshable Maps: Zeng & Weber (2014) found performance on raised-pin device matched raised-line maps but tablet-only failed for spatial tasks.
- Key finding: DIMs support spatial learning but mostly limited to simple topological features (relative positions). HIMs support more complex spatial knowledge acquisition.

## Figures of Interest
- **Fig 1 (page 4):** Production methods for tactile maps - (a) swell paper raised-line map, (b) magnetic board local map, (c) wooden small-scale model
- **Table (implicit, page 22-23):** Comparison of interactive map technologies across content, readability, interactivity dimensions

## Results Summary
- Interactive Raised-Line Maps (a type of HIM) are the most mature and widely deployed accessible interactive map technology, now used in specialized education centers
- No single technology type excels across all dimensions; each involves trade-offs between cost, portability, tactile fidelity, interactivity, and content complexity
- DIMs are cheap and portable but lack tactile cues critical for spatial understanding
- HIMs provide better spatial reference but are constrained by physical display properties
- Refreshable displays are theoretically ideal (dynamic content + tactile feedback + two-handed exploration) but remain too expensive and low-resolution for practical deployment

## Limitations
- Paper does not include formal user study data of its own; it is a review/classification paper
- Coverage ends around 2016; more recent developments (e.g., web-based accessible maps, AI-generated tactile graphics) are not covered
- The review excludes purely physical (non-interactive) maps and navigation/wayfinding systems
- Some prototype evaluations cited had very small sample sizes (1-5 blind users) limiting generalizability
- The classification focuses on technology type rather than task type or user population subgroups

## Testable Properties
- **Two-handed exploration superiority:** Maps that support bimanual exploration should produce more accurate spatial representations than single-point-of-contact maps
- **Haptic reference frame reliability:** Maps with physical boundaries/landmarks should produce better spatial accuracy than maps without haptic reference frames
- **Interactivity benefit:** Interactive maps should reduce exploration time and increase user satisfaction compared to non-interactive equivalents with identical content
- **Modality complementarity:** Adding tactile feedback to auditory-only maps should improve sketch map accuracy
- **Refreshable display resolution threshold:** Below some pin density, refreshable displays cannot render complex map content that raised-line maps can

## Relevance to Project
This paper is the definitive taxonomy for interactive map accessibility research. It directly connects to the visual impairment topic area and provides the classification framework referenced by subsequent work on map accessibility including Biggs et al.'s (2025) MEP Framework. The five-dimension comparison framework (content, readability, reference frame, interactivity, spatial cognition) provides evaluative criteria for any accessible map implementation.

## Open Questions
- [ ] What is the minimum resolution (pin density) for refreshable displays to match raised-line map content complexity?
- [ ] How do web-based accessible maps (Google Maps, OpenStreetMap with screen readers) compare to the research prototypes reviewed here?
- [ ] Can AI-generated descriptions substitute for interactive tactile exploration for spatial learning tasks?
- [ ] How does the Biggs et al. (2025) MEP Framework map onto the DIM/HIM classification in this paper?

## Related Work Worth Reading
- Parkes (1988) - NOMAD: the first accessible interactive map prototype
- Brock et al. (2015) - Interactivity Improves Usability of Geographic Maps for VI People (24-participant evaluation)
- Kane et al. (2011) - Access Overlays for large touch screens
- Zeng & Weber (2010, 2012) - BrailleDis/ATMap refreshable tactile map systems
- O'Modhrain et al. (2015) - Designing Media for Refreshable Touch Displays

## Collection Cross-References

### Already in Collection
- **Biggs_2025_MapEquivalentPurpose** - Directly extends this review's work on map accessibility; the MEP Framework evaluates text-based map representations that this paper's DIM category encompasses
- **Wobbrock_2011_AbilityBasedDesign** - The ability-based design principles apply to the adaptive interaction techniques reviewed here (e.g., Kane et al.'s tabletop techniques)
- **Lazar_2007_ScreenReaderFrustration** - Screen reader frustration with web maps is a motivating problem for the DIM category
- **Giudice_2020_CognitiveMappingWithoutVision** - Directly validates the DIM approach reviewed here: a vibro-audio touchscreen map achieves equivalent spatial learning to traditional tactile maps
- **Froehlich_2025_StreetReaderAI** - Advances this review's DIM category to the AI era with accessible virtual street exploration for blind users
- **Millar_1995_SpatialInformation** - Provides the cognitive science foundations for understanding spatial cognition without vision that underpins this review's spatial cognition analysis

### New Leads (Not Yet in Collection)
- Brock et al. (2015) - "Interactivity Improves Usability of Geographic Maps for Visually Impaired People" - The strongest empirical validation of interactive tactile maps with 24 blind participants
- Kane et al. (2011) - "Access Overlays: Improving Non-Visual Access to Large Touch Screens for Blind Users" - Key interaction technique design for accessible touch interfaces
- Zeng & Weber (2010) - "Audio-Haptic Browser for a Geographical Information System" - Foundational refreshable tactile map work
- O'Modhrain et al. (2015) - "Designing Media for Visually-Impaired Users of Refreshable Touch Displays" - Design guidelines for emerging refreshable display technology
- Klatzky et al. (2014) - "Touch-Screen Technology for the Dynamic Display of 2D Spatial Information Without Vision" - Cognitive science foundations for touch-based spatial access
