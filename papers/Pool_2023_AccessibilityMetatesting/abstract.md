# Abstract

## Original Text (Verbatim)

Automated web accessibility testing tools have been found complementary. The implication: To catch as many issues as possible, use multiple tools. Doing this efficiently entails integration costs. Is there a small set of tools that, together, make additional tools redundant? I approach this problem by comparing nine comprehensive accessibility testing tools that are amenable to integration: alfa, axe-core, Continuum, Equal Access, HTML CodeSniffer, Nu Html Checker, QualWeb, Tenon, and WAVE. I tested 121 web pages of interest to CVS Health with these tools. Each tool only fractionally duplicated any other tool. Each discovered numerous issue instances missed by all the others. Thus, testing with all nine tools was substantially more informative than testing with any subset.

---

## Our Interpretation

The paper asks whether organizations can save integration effort by using a small "sufficient" subset of automated accessibility tools, and answers no: on a 121-page real-world corpus, every tool in a nine-tool ensemble uniquely discovers issue instances that none of the others catch. The key practical finding is that no tool makes any other redundant — not even the highest-volume tool (QualWeb, 23,715 instances) subsumes the lowest (Continuum, 3,089 instances) — establishing that ensemble testing is necessary for comprehensive automated coverage. For this project's evaluation methods topic, the abstract frames the central tension of automated accessibility testing: complementarity demands multiple tools, but multiple tools impose real engineering costs, making tool selection and integration a first-class research problem.
