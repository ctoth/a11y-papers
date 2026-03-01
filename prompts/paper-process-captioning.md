**You are a WORKER agent launched via the Task tool. Execute this task directly. Do NOT dispatch subagents. Do NOT use the Task tool. Do NOT read foreman.md. Do NOT coordinate — DO the work yourself. If you attempt to use the Task tool, you have failed.**

# Task: Retrieve and Process Captioning/DHH Accessibility Paper

## Context
This is an accessibility research paper collection (C:/Users/Q/code/a11y-papers). The collection currently has no papers on deaf/hard-of-hearing (DHH) accessibility or captioning. This is a known gap — Mack et al. 2021 found DHH papers are only 11.3% of the accessibility literature.

## Objective
Find and process a highly-cited paper on automatic captioning, sign language recognition, or DHH technology accessibility.

Good candidates:
- Kushalnagar, Lasecki, and Bigham (2014) — "Accessibility Evaluation of Classroom Captions" (ACM TACCESS)
- Or a recent ASR/captioning accuracy paper for DHH users
- Or Glasser et al. (2017) — "Deaf and hard of hearing experiences with large-scale automatic speech recognition" (ASSETS)

Search with WebSearch for: "deaf hard of hearing" captioning accessibility research paper arxiv OR acm

Pick the most foundational or highly-cited paper you can find a PDF for, then use the Skill tool to invoke `research-papers:paper-process` with it.

## Output
When complete, the paper directory should contain: notes.md, description.md, abstract.md, citations.md
And papers/CLAUDE.md should be updated.

Write a brief status report to `./reports/paper-captioning-report.md`

## CRITICAL
- Do NOT use the Task tool or dispatch subagents
- NEVER use git restore, checkout, reset, clean, or stash
- If Edit/Write fails, try path formats: `./relative`, `C:/forward/slashes`, `C:\back\slashes`
