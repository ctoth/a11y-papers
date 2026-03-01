**You are a WORKER agent launched via the Task tool. Execute this task directly. Do NOT dispatch subagents. Do NOT use the Task tool. Do NOT read foreman.md. Do NOT coordinate — DO the work yourself. If you attempt to use the Task tool, you have failed.**

# Task: Retrieve and Process ARIA/Screen Reader Compatibility Paper

## Context
This is an accessibility research paper collection (C:/Users/Q/code/a11y-papers). We have a screen reader user frustration study (Lazar 2007) but nothing on WAI-ARIA effectiveness, screen reader compatibility, or how ARIA is actually used/misused in the wild.

## Objective
Find and process a paper on WAI-ARIA usage, effectiveness, or screen reader compatibility in practice.

Good candidates:
- Antonelli, Fortes, and Watanabe (2018) — "A Survey on Accessibility Awareness of Brazilian Web Developers"
- WebAIM Million analysis papers (automated scan of top 1M websites)
- Bi, Lutteroth, and Weber (2022) — studies of ARIA in practice
- Or any paper analyzing real-world ARIA adoption and its impact on screen reader users

Search with WebSearch for: WAI-ARIA screen reader compatibility usage study research paper arxiv OR acm 2020 2021 2022 2023

Pick the most data-driven paper you can find a PDF for, then use the Skill tool to invoke `research-papers:paper-process` with it.

## Output
When complete, the paper directory should contain: notes.md, description.md, abstract.md, citations.md
And papers/CLAUDE.md should be updated.

Write a brief status report to `./reports/paper-ariaeval-report.md`

## CRITICAL
- Do NOT use the Task tool or dispatch subagents
- NEVER use git restore, checkout, reset, clean, or stash
- If Edit/Write fails, try path formats: `./relative`, `C:/forward/slashes`, `C:\back\slashes`
