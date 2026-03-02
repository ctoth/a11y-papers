# Abstract

## Original Text (Verbatim)

Interactive streetscape mapping tools such as Google Street View (GSV) and Meta Mapillary enable users to virtually navigate and experience real-world environments via immersive 360° imagery but remain fundamentally inaccessible to blind users. We introduce StreetReaderAI, the first-ever accessible street view tool, which combines context-aware, multimodal AI, accessible navigation controls, and conversational speech. With StreetReaderAI, blind users can virtually examine destinations, engage in open-world exploration, or virtually tour any of the over 220 billion images and 100+ countries where GSV is deployed. We iteratively designed StreetReaderAI with a mixed-visual ability team and performed an evaluation with eleven blind users. Our findings demonstrate the value of an accessible street view in supporting POI investigations and remote route planning. We close by enumerating key guidelines for future work.

---

## Our Interpretation

This paper tackles the fundamental inaccessibility of street view platforms -- tools that billions of sighted users take for granted for route planning, destination investigation, and virtual exploration, but that are completely unusable by blind people. The key finding is that combining multimodal AI (for scene description and conversational Q&A) with reliable geographic data APIs (for places, roads, and addresses) and accessible keyboard/voice controls produces a system that blind users find highly useful and reasonably accurate, achieving 86.3% correctness on factual questions. For this project's research domain, the paper demonstrates that AI-mediated access to visual geographic content is now technically feasible and user-valued, while highlighting that AI hallucination, verbosity management, and spatial orientation communication remain critical unsolved design challenges.
