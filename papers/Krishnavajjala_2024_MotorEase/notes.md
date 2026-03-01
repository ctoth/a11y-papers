# MotorEase: Automated Detection of Motor Impairment Accessibility Issues in Mobile App UIs

**Authors:** Arun Krishnavajjala, SM Hasan Mansur, Justin Jose, Kevin Moran
**Year:** 2024
**Venue:** ICSE 2024 (46th IEEE/ACM International Conference on Software Engineering)
**DOI/URL:** https://arxiv.org/abs/2403.13690 | https://dl.acm.org/doi/10.1145/3597503.3639167
**Code:** https://github.com/SageSELab/MotorEase

## One-Sentence Summary
MotorEase is an automated Android tool combining computer vision and XML metadata analysis to detect four categories of motor-impairment accessibility violations in mobile app UIs, achieving ~90% accuracy on a 1,599-screen benchmark.

## Problem Addressed
Motor-impaired users (who rely on switch scanning or constrained touch) face barriers in mobile apps that existing automated accessibility tools do not detect. Tools like Google Accessibility Scanner focus mainly on touch target size but miss expanding section closures, persistent element location drift, and adjacent icon crowding. No prior automated system addresses these four violation categories together.

## Key Contributions
- Four novel detectors for motor-impairment-specific accessibility violations not previously addressed by automated tools
- MotorCheck benchmark: 555 manually annotated violation examples across 1,599 screens from 70 Android apps
- Demonstrated ~90% average accuracy, outperforming Google Accessibility Scanner (0.8525 vs 0.6025 on touch targets) and Groundhog (0.9123 vs 0.7207 on expanding sections)
- Multimodal analysis combining visual screenshots with uiautomator XML metadata

## Motor Impairment Context
Motor-impaired users interact via two primary modalities:
- **Switch-based scanning** (Android Switch Access): averages ~3 words per minute vs. 40 wpm for touch users
- **Constrained touch input**: tremors, limited precision, reduced grip strength

The four detected violation categories directly impair both interaction modalities.

## Four Detector Components

### 1. Expanding Section Closure Detector
Detects pop-up menus and modal dialogs that lack a visible closure mechanism (e.g., no X button, no close label).

**Approach (dual pipeline, text-first):**
1. Extract text via OCR (Google OCR + EAST text detection) and uiautomator XML
2. Semantic match against 25 closure-related terms using GloVe word embeddings
3. If no text match: run Faster-RCNN icon detector trained on 7,291 synthetic images (Fontawesome + Flaticon icons)
4. Flag as violation if neither text nor icon closure found

**Threshold:** GloVe cosine similarity threshold (value not explicitly stated; tuned on benchmark)
**Training data:** 7,291 synthetic icon images across closure-related icon classes

**Performance:** Precision 0.9042, Recall 0.9205, Accuracy 0.9123, F1 0.9129

### 2. Visual Touch-Target Detector
Detects UI elements whose *visual* touch target is smaller than 48px (Google design guideline minimum), even when their programmatic bounding box meets the threshold.

**Key insight:** Programmatic bounding box padding can artificially inflate reported size. The visual boundary of the actual clickable graphic may be much smaller.

**Approach:**
1. Extract element bounding boxes from uiautomator XML (clickable elements only)
2. Apply UIED edge detection on the screenshot to find true visual element boundaries
3. Compare visual width and height against 48-pixel threshold
4. Flag if visual dimension < 48px

**Threshold:** 48 pixels (derived from Google Material Design accessibility guidelines)

**Performance:** Precision 1.0000, Recall 0.6648, Accuracy 0.8525, F1 0.7986
- Perfect precision (zero false positives) but misses ~33% of real violations (false negatives)
- Outperforms Google Accessibility Scanner (0.6025 accuracy)

### 3. Persisting Elements Detector
Detects when a persistent UI element (e.g., navigation bar, back button, menu) changes visual location between screens, forcing switch-scan users to re-scan from scratch.

**Approach:**
1. Use uiautomator XML to identify elements with the same resource ID across consecutive screens
2. Check location consistency: same bounding box position?
3. Check visual similarity: pixel-based MSE ≥ 95% threshold for same-element confirmation
4. Flag if element moves location

**Threshold:** 95% pixel-based mean squared error similarity for element identity confirmation

**Performance:** Precision 0.8214, Recall 0.9583, Accuracy 0.8776, F1 0.8846

### 4. Visual Icon Distance Detector
Detects adjacent clickable icons that are too close together (< 8px visual gap), creating mis-tap risk for users with motor tremors.

**Approach:**
1. Extract clickable element bounding boxes from uiautomator XML
2. Apply UIED edge detection to find true visual icon boundaries (strips padding)
3. Measure pixel distance between visually adjacent clickable icons
4. Flag pairs with distance < 8px

**Threshold:** 8 pixels between adjacent icon visual boundaries (derived from Kong et al. 2021 and Google accessibility standards)

**Performance:** Precision 0.7119, Recall 1.0000, Accuracy 0.9575, F1 0.8317
- Perfect recall (catches every real violation) but ~29% false positive rate

## Parameters

| Name | Symbol | Units | Value | Source | Notes |
|------|--------|-------|-------|--------|-------|
| Touch target minimum | - | pixels | 48 | Google Material Design | Visual boundary, not bounding box |
| Icon distance minimum | - | pixels | 8 | Kong et al. 2021 + Google | Visual gap between clickable icons |
| Element similarity threshold | - | % MSE | 95 | Paper | For persisting element identity |
| Closure vocabulary size | - | terms | 25 | Paper | GloVe semantic matching seed set |
| Synthetic training images | - | count | 7,291 | Paper | Faster-RCNN closure icon detector |

## Key Equations / Thresholds

**Visual touch target check:**
```
violation = (visual_width < 48px) OR (visual_height < 48px)
```

**Icon distance check:**
```
violation = (pixel_distance_between_visual_bounds < 8px)
for any pair of adjacent clickable elements
```

**Persistent element identity:**
```
same_element = (resource_id matches) AND (pixel_MSE >= 0.95)
violation = same_element AND (location changes between screens)
```

## Algorithms

**Expanding Section Detection Pipeline:**
1. Detect expanding sections (pop-ups, modals) via screen transition analysis
2. For each expanding section screen:
   a. Extract all text (OCR + XML)
   b. Embed text with GloVe; compute cosine similarity to 25 closure terms
   c. If max similarity < threshold → run Faster-RCNN on screen
   d. If no closure icon detected → flag as violation

**Touch Target Detection Pipeline:**
1. Parse uiautomator XML for all clickable elements
2. For each element: crop screenshot to bounding box
3. Run UIED edge detection on crop
4. Measure visual bounds of detected edges
5. Compare visual dimensions to 48px threshold

## MotorCheck Benchmark

| Category | Total Screens | Violations | Compliant |
|----------|--------------|------------|-----------|
| Expanding sections | 483 | 241 | 242 |
| Touch targets | 400 | 176 | 224 |
| Persistent elements | 49 apps | 24 violations | 25 compliant |
| Icon distance | 400 | 42 | 358 |
| **Total** | **1,599 screens** | **555 annotated examples** | - |

**Data source:** 70 Android apps from F-Droid and Google Play (≥1,000 downloads), tested via CrashScope automated exploration.

## Results Summary

| Detector | Precision | Recall | Accuracy | F1-Score |
|----------|-----------|--------|----------|----------|
| Expanding Sections | 0.9042 | 0.9205 | 0.9123 | 0.9129 |
| Touch Target | 1.0000 | 0.6648 | 0.8525 | 0.7986 |
| Persistent Elements | 0.8214 | 0.9583 | 0.8776 | 0.8846 |
| Icon Distance | 0.7119 | 1.0000 | 0.9575 | 0.8317 |
| **Average** | **0.8594** | **0.8859** | **0.8999** | **0.8570** |

**Comparative baselines:**
- Google Accessibility Scanner on touch targets: 0.6025 accuracy (MotorEase: 0.8525)
- Groundhog on expanding sections: 0.7207 accuracy (MotorEase: 0.9123)

## Implementation Details

**Runtime dependencies:**
- uiautomator XML from Android dynamic analysis (CrashScope, DroidBot, Sapienz, etc.)
- Screenshot images paired with XML
- UIED: UI element detection via edge detection
- GloVe embeddings for text-based closure detection
- Faster-RCNN (PyTorch/torchvision) for icon detection
- Google OCR + EAST for text extraction

**Data collection pipeline:**
1. Automated app exploration via CrashScope generates (screenshot, XML) pairs
2. MotorEase analyzers consume pairs
3. Results reported per-screen and per-app

**Key design choices:**
- Text-before-icon priority in closure detection (reduces false positives from incidental X glyphs)
- Visual bounds over programmatic bounds for touch targets and icon distance (captures real user experience)
- Resource ID matching for persisting element identity across screens

## Figures of Interest
- **Fig 1:** Four violation examples with screenshots showing each category
- **Fig 2:** MotorEase pipeline architecture diagram
- **Fig 3:** Expanding section closure detection pipeline (text + icon paths)
- **Fig 4:** Touch target visual vs. programmatic bounds comparison
- **Fig 5:** Results tables with baselines

## Limitations
- Depends on XML `clickable` attribute; elements without explicit clickable designation may be missed
- Potential false positives from functional X icons confused with close-button icons
- Not evaluated directly with motor-impaired users — benchmark is expert-annotated
- Limited to Android (uiautomator XML format); web or iOS not addressed
- Does not detect all motor-impairment barriers (e.g., gesture-only interactions, timing requirements)
- Touch target detector has high false-negative rate (recall 0.6648) — misses ~33% of real violations

## Testable Properties

- **Touch target threshold:** Any element flagged must have visual_width < 48px OR visual_height < 48px
- **Icon distance threshold:** Any pair flagged must have visual pixel gap < 8px between their edge-detected bounds
- **Precision floor:** Touch target detector must have zero false positives (precision = 1.0) by design
- **Recall ceiling on icon distance:** Icon distance detector catches all violations (recall = 1.0) by design
- **Persistence check requires multi-screen:** Persistent element violations require at least two screens with matching resource IDs
- **Closure detection ordering:** Icon detector only runs if text/GloVe match fails (text-first guarantee)

## Relevance to Project
Directly addresses motor impairment topic area. Provides concrete, implementable detection thresholds (48px touch target, 8px icon gap, 95% MSE similarity) and a novel multimodal approach (visual + XML) that could extend to web or iOS contexts. The MotorCheck benchmark methodology is a model for constructing accessible UI evaluation datasets.

## Open Questions
- [ ] What is the exact GloVe similarity threshold used for closure detection?
- [ ] How does performance generalize beyond the 70-app benchmark dataset?
- [ ] How do motor-impaired users actually perceive/experience these four violation types in practice?
- [ ] Can the visual touch target approach extend to web DOM + screenshot pairs?
- [ ] What is the minimum viable version of MotorEase runnable without CrashScope?

## Related Work Worth Reading
- Salehnamadi et al. (2022) — Groundhog: expanding section accessibility (direct baseline)
- Salehnamadi et al. (2021) — Latte: replay-based accessibility testing framework
- Kong et al. (2021) — Touch target sizing research (source of 8px icon distance threshold)
- Alshayban et al. (2020) — Accessibility issues in Android apps (landscape of what's been studied)
- Chiou et al. (2021/2023) — Keyboard accessibility failures (related automated detection)
- Moran et al. (2016) — CrashScope testing tool (data collection pipeline used here)

## Collection Cross-References

### Already in Collection
- None of the cited papers are currently in the collection.

### New Leads (Not Yet in Collection)
- Salehnamadi et al. (2022) "Groundhog" (ASE 2022) — direct baseline for expanding-section detection; worth adding for motor accessibility coverage
- Alshayban et al. (2020) — survey of Android app accessibility issues; foundational landscape paper
- Kong et al. (2021) — touch target size research; provides empirical basis for the 8px threshold used here
- Chiou et al. (2021/2023) (CHI) — keyboard accessibility failures; related automated detection work
- Mack et al. (2021) is already in collection but not cited by this paper
