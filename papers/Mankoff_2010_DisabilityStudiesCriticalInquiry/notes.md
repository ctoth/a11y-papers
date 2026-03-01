# Disability Studies as a Source of Critical Inquiry for the Field of Assistive Technology

**Authors:** Jennifer Mankoff, Gillian R. Hayes, Devva Kasnitz
**Year:** 2010
**Venue:** ASSETS '10 — Proceedings of the 12th International ACM SIGACCESS Conference on Computers and Accessibility
**DOI:** 10.1145/1878803.1878807

## One-Sentence Summary

This paper argues that accessibility/AT researchers have been operating primarily within the medical model of disability and calls for substantive engagement with disability studies — its social/cultural models, critical methods, and nothing-about-us-without-us ethics — to find better problems, avoid paternalist errors, and do more impactful research.

## Problem Addressed

Disability studies and assistive technology share common goals but are nearly entirely disconnected in the literature. AT researchers default to a medical model that treats disability as an individual deficit to be fixed, missing the social, cultural, and political dimensions of disability that disability studies has theorized for decades. This gap leads AT researchers to solve the wrong problems, marginalize the people they aim to serve, and miss research directions that could be more impactful.

## Key Contributions

1. **Review of disability studies literature** relevant to AT — social/medical/postmodern models, language debates (person-first vs. identity-first), disability rights history, nothing-about-us-without-us principle.
2. **Two case studies** showing how disability studies transformed the authors' own AT research:
   - Autism + educational technology: how the medical model shapes special education and AT design in ways that reify disabled students' diminished status; how acknowledging autism culture expands the design space of augmentative communication tools.
   - Web/computer accessibility: how social models reframe who is "disabled by" a design, limitations of simulation-based evaluation, and the case for participatory design with disabled individuals.
3. **A curated reading list** of disability studies literature for AT researchers and students.
4. **Methodological recommendations** for more inclusive research practice: co-authorship with disabled individuals, participatory action research, service learning, deep longitudinal engagement.

## Disability Models Framework (Core Theoretical Content)

### Medical Model
- Focuses on individual physical/functional limitations
- Disability = deficit residing in the person
- Enables measurable, actionable solutions (screen readers, typing aids, AAC devices)
- Risk: frames disability as burden requiring "fixing"; can undercut autonomy; leads to "blame the victim" framing

### Social Model (UK/US variants)
- Disability = exclusion propagated by a society that marginalizes people with impairments
- Impairment is biological; disability is social
- Shifts focus from "cure" to "care," from clinicians to patients as leaders, from fixing individuals to changing environments
- Risk: if disability is only social, the reality of impairment pain/need for medical care is invalidated; can rest on assumption that "normality" is the goal

### Postmodern / Cultural Model
- Privileges each individual's unique lived experience
- Disability, illness, impairment, functional limitation, bodily anomaly are separate but complementary
- Resists the assumption that the goal is normality
- Many disability/impairment groups have reclaimed their identity labels positively (Deaf, Autistic, Little Person, Mad)

### Practical Synthesis (authors' position)
- AT researchers need all three: medical model for actionable functional challenges; social model to avoid "blame the victim"; cultural model to avoid defaulting to "normality" as the goal
- "The person designing a piece of software is, in some sense, defining who is disabled with respect to that software"

## Language / Labeling (Implementation Relevance)

- Person-first ("person with a disability") = U.S. standard; criticized for objectifying disability as a thing in the person
- Identity-first ("disabled person") = U.K. standard; foregrounds disability as a social process imposed on the person
- Many communities now reclaim identity descriptors: "Autistic person," "Deaf person," "Little person," "Mad person"
- No universal right answer; context of use, audience, and individual preference all matter
- Regardless of label: labeling itself can have negative consequences

## Case Study 1: Autism and Educational Technology

### Key insight from disability studies lens:
- Special education is structured around "mainstreaming" — teaching autistic students to perform neurotypical (NT) cultural norms
- This is explicit cultural transmission: teaching children "how to think, act, and feel" like non-autistic people
- AT tools for autism communication universally assume the goal is NT-style communication — an "ableist" premise
- Autism culture perspective: NTs may be over-communicative and demanding; autistic people may prefer direct, intellectually substantive communication

### Design space implication:
- AT for autism communication should involve BOTH interlocutors — not only tools to help autistic people approach NT norms, but also tools to help NT people approach autistic communication norms
- This moves beyond a medical "fix the person" model

### Structural critique:
- Early diagnosis surveillance programs (CDC "Learn the Signs, Act Early") create a "governmentality" — protective intent but normalizing, lacking understanding of disability culture/identity
- IEP outcome-based education creates documentation burden on classroom staff → led authors to build record-keeping technology (CareLog) → disability studies perspective then redirected focus from empowering teachers to empowering students

## Case Study 2: Web Accessibility and Simulation

### Key insight from disability studies lens:
- Poorly designed interfaces "disable" users with respect to that system — designers have responsibility not to marginalize atypical users
- Universal usability (Shneiderman 2000): not just access but success (access + usability) by all
- Inclusive design (Newell & Gregor 2000): extends user-centered design to include minority groups

### Evaluation methods compared (Mankoff et al. 2005, CHI):
1. Automated tools — find guideline violations, miss most important problems
2. Designers with minimal training (read W3C guidelines) — limited
3. Designers with screen reader access — consistently highest performers
4. Remote blind users testing at home — underperformed due to insufficient structure

### Simulation (EASE project — Mankoff et al. 2005, IBM Systems Journal):
- Extended VNC client to simulate motor and vision impairments in input/output streams
- Motor simulation: mouse behaves as if controlled by someone with motor impairment
- Vision simulation: modifies output to simulate blind spots or focus problems
- Validated: motor simulation produced predictable text entry speeds with word prediction
- Limitation: lacks the "soul" — real experience, workarounds, likes/dislikes, feelings of disabled users
- Risk: simulations often give uninitiated an overly negative view of disability

### Recommended alternatives to simulation:
1. **Deep longitudinal participatory engagement**: one or a few disabled individuals as equal partners throughout design process (problem definition through dissemination) — surfaces tacit false assumptions, provides insider knowledge
2. **Real data corpus**: captures authentic day-to-day experience, wide range of individuals, avoids simulation inaccuracy — still lacks interpretive faculties/soul

## Methodological Recommendations

### For research:
- Co-author and co-edit with disabled individuals
- Include disabled individuals as advisors
- True participatory research: disabled collaborators in problem definition, methods, data collection, analysis, publication, dissemination
- Participatory action research (PAR) as primary method
- Engage neurodiversity and disability rights communities directly (blogs, self-advocacy networks)

### For teaching:
- Required reading: *Encyclopedia of Disability* (Albrecht 2006), *Living in the State of Stuck* (Scherer 2000)
- Participatory methods reading: Balcazar et al. 1998, French 1994, Lloyd et al. 1996
- Attend Society for Disability Studies annual conference
- Topic-specific: for cognitive impairment → Mactavish et al. 2000; for hearing → "Sound and Fury" documentary
- Service learning: students as apprentices/assistants to community orgs, not as "problem solvers"
- Guest speakers who self-identify as disabled

## Parameters / Thresholds

No quantitative parameters (this is a theoretical/position paper, not an empirical measurement study).

## Figures of Interest

No figures. The paper is argument-driven with quoted text blocks and case study narratives.

## Limitations

- Case studies are from the authors' own work — not a systematic review; selection bias toward examples where disability studies was helpful
- The paper does not provide empirical evidence that disability-studies-informed AT research produces better outcomes; it argues by example
- Limited international scope: disability studies background focuses on U.S. and U.K. contexts
- No formal evaluation of the teaching recommendations

## Testable Properties

This is a position/theoretical paper; testable properties are methodological rather than computational:

- **Research with vs. about**: Any AT study claiming to be participatory should include disabled participants in ALL phases (problem definition, methods, data collection, analysis, publication, dissemination) — not just as test subjects
- **Model identification**: Any AT paper should be checkable for which disability model (medical/social/cultural) it implicitly assumes — papers working purely within the medical model should be flagged for potential blind spots
- **Language audit**: Terminology choices in AT papers (person-first vs. identity-first, "disabled people" vs. "people with disabilities") should be intentional and contextually appropriate, not default

## Relevance to Project

This paper is the foundational theoretical frame for the entire collection. It:
- Explains WHY accessibility research needs to engage with lived experience and not just technical metrics
- Provides the vocabulary (medical/social/postmodern models, ableism, nothing-about-us-without-us) that other papers in this collection implicitly or explicitly reference
- Is directly cited in Mack_2021 as a landmark paper calling for disability studies integration — it frames the critique that Mack et al. found evidence for (small samples, narrow disability focus, limited disabled participation)
- Connects to Wobbrock_2011_AbilityBasedDesign: ability-based design is a direct response to the disability-studies critique — it reframes design from "compensating for deficit" (medical model) to "leveraging what users can do"
- Connects to Gartland_2022_WebAccessibilityCognitive: the exclusion of people with cognitive disabilities from design processes is a concrete instance of what Mankoff et al. identify as the structural problem
- Connects to Wang_2021_ScientificPDFAccessibility and Singh_2024_FigurA11y: inaccessible scientific literature marginalizes disabled researchers — a social model problem as much as a technical one
- Connects to Lazar_2007_ScreenReaderFrustration: the diary study methodology is a practical attempt to include blind users' authentic lived experience rather than relying on simulation

## Open Questions

- [ ] Has the disability studies / AT integration actually increased since 2010? Mack_2021 would be the place to check — does their survey show growth in participatory methods or co-authorship with disabled individuals?
- [ ] Are there AT papers post-2010 that demonstrate measurable outcome improvements from disability-studies-informed methodology?
- [ ] How does the "autism culture" argument map onto current neurodiversity research and AAC design?
- [ ] The EASE simulation work is critiqued here — has simulation-based accessibility evaluation been superseded by better methods?

## Related Work Worth Reading

- Linton (1998). *Claiming Disability: Knowledge and Identity.* — foundational disability studies text [cited as ref 40]
- Scherer (2000). *Living in the State of Stuck.* — disability studies perspective on AT adoption [cited as ref 60]
- Meekosha & Shuttleworth (n.d.). "What's so 'critical' about critical disability studies?" — Australian Journal of Human Rights [cited as ref 49]
- Shneiderman (2000). "Universal usability." — Communications of the ACM [cited as ref 62]
- Mankoff, Fait & Tran (2005). "Is your web page accessible?" CHI'05 — the web accessibility evaluation methods comparison study [cited as ref 48]
- Mankoff, Fait & Juang (2005). "Evaluating accessibility through simulating the experiences of users with vision or motor impairments." IBM Systems Journal — the EASE simulation study [cited as ref 45]
- Balcazar et al. (1998). "Participatory action research and people with disabilities." — Canadian Journal of Rehabilitation [cited as ref 4]

## Collection Cross-References

### Already in Collection
- **Mack_2021_AccessibilityResearchSurvey** — directly cites Mankoff 2010 as a landmark paper; Mack's finding that 7.4% of ASSETS papers use participatory methods and that disabled participants are underrepresented is empirical confirmation of what Mankoff 2010 argues
- **Wobbrock_2011_AbilityBasedDesign** — ability-based design is a direct theoretical response to the medical-model critique in this paper; both papers appeared within a year of each other at the same community (ASSETS/TACCESS)
- **Gartland_2022_WebAccessibilityCognitive** — the "exclusion of PwCDs from design processes" finding is the exact structural problem Mankoff 2010 identifies; the four-quadrant framework includes "People" and "Process" as dimensions that address the nothing-about-us-without-us gap
- **Lazar_2007_ScreenReaderFrustration** — diary study of 100 blind users is methodologically aligned with Mankoff's call to capture authentic lived experience; the 30.4% time-loss finding is precisely the kind of "soul of the experience" data that simulation cannot produce
- **Wang_2021_ScientificPDFAccessibility** — inaccessibility of scientific literature to blind/low-vision researchers is a social model problem: the barrier is in the publication system, not in the readers
- **Singh_2024_FigurA11y** — participatory approach to alt text authoring (authors describing their own figures) resonates with the participatory design recommendations here

### New Leads (Not Yet in Collection)
- Shneiderman (2000). "Universal usability." *Communications of the ACM* 43(5), 84-91 — foundational for universal design / accessibility; already appears in Wobbrock_2011 collection but not separately annotated
- Mankoff, Fait & Tran (2005). "Is your web page accessible?: a comparative study of methods for assessing web page accessibility for the blind." *CHI'05*, pp. 41-50 — directly relevant to Pool_2023_AccessibilityMetatesting; provides earlier baseline for multi-method evaluation
- Balcazar et al. (1998). "Participatory action research and people with disabilities." — key methodological paper for any participatory study in this collection
- Linton (1998). *Claiming Disability: Knowledge and Identity.* — the foundational disability studies text cited throughout this paper; theoretical bedrock

### Supersedes or Recontextualizes
- **Wobbrock_2011_AbilityBasedDesign** — Mankoff 2010 provides the disability studies critique that ability-based design responds to; reading Mankoff first clarifies why ability-based design is a theoretical advance. Annotating Wobbrock notes file below.
