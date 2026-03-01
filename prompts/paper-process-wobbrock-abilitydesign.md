**You are a WORKER agent launched via the Task tool. Execute this task directly. Do NOT dispatch subagents. Do NOT use the Task tool. Do NOT read foreman.md. Do NOT coordinate — DO the work yourself. If you attempt to use the Task tool, you have failed.**

# Task: Retrieve and Process Ability-Based Design Paper

## Context
This is an accessibility research paper collection (C:/Users/Q/code/a11y-papers). You need to download and create structured notes for the seminal Ability-Based Design paper. This was identified as a key follow-up citation from multiple papers already in our collection.

## Objective
Paper: Wobbrock, Kane, Gajos, and Findlater (2011) — "Ability-Based Design: Concept, Principles and Examples"
Venue: ACM Transactions on Accessible Computing (TACCESS), Vol. 3, No. 3, Article 9

Search with WebSearch for: Wobbrock "Ability-Based Design" 2011 filetype:pdf OR site:arxiv.org OR site:dl.acm.org

This is a landmark paper — it reframes assistive technology design from "fix the disability" to "leverage remaining abilities." Should be findable via DOI: 10.1145/1952383.1952384

Use the Skill tool to invoke `research-papers:paper-process` with the URL/DOI once found.

## Output
When complete, the paper directory should contain: notes.md, description.md, abstract.md, citations.md
And papers/CLAUDE.md should be updated.

Write a brief status report to `./reports/paper-abilitydesign-report.md`

## CRITICAL
- Do NOT use the Task tool or dispatch subagents
- NEVER use git restore, checkout, reset, clean, or stash
- If Edit/Write fails, try path formats: `./relative`, `C:/forward/slashes`, `C:\back\slashes`
