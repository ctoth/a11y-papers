**You are a WORKER agent launched via the Task tool. Execute this task directly. Do NOT dispatch subagents. Do NOT use the Task tool. Do NOT read foreman.md. Do NOT coordinate — DO the work yourself. If you attempt to use the Task tool, you have failed.**

# Task: Retrieve and Process Web Accessibility Automated Testing Paper

## Context
This is an accessibility research paper collection (C:/Users/Q/code/a11y-papers). We have no papers yet on automated web accessibility evaluation tools (axe, WAVE, Lighthouse, etc.) or their effectiveness.

## Objective
Find and process a paper on automated accessibility testing tools and their coverage/accuracy.

Good candidates:
- Vigo, Brown, and Conway (2013) — "Benchmarking Web Accessibility Evaluation Tools" (ACM Web4All)
- Alshayban, Ahmed, and Malek (2020) — "Accessibility Issues in Android Apps" (FSE)
- Frazão and Duarte (2020) — "Comparing Accessibility Evaluation Plug-ins"
- Or search for a recent large-scale study comparing automated a11y testing tools

Search with WebSearch for: "automated accessibility testing" evaluation tools comparison research paper 2020 2021 2022 2023 arxiv OR acm

Pick the most comprehensive or highly-cited paper available, then use the Skill tool to invoke `research-papers:paper-process` with it.

## Output
When complete, the paper directory should contain: notes.md, description.md, abstract.md, citations.md
And papers/CLAUDE.md should be updated.

Write a brief status report to `./reports/paper-automatedtesting-report.md`

## CRITICAL
- Do NOT use the Task tool or dispatch subagents
- NEVER use git restore, checkout, reset, clean, or stash
- If Edit/Write fails, try path formats: `./relative`, `C:/forward/slashes`, `C:\back\slashes`
