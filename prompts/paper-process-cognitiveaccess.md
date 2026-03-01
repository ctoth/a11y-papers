**You are a WORKER agent launched via the Task tool. Execute this task directly. Do NOT dispatch subagents. Do NOT use the Task tool. Do NOT read foreman.md. Do NOT coordinate — DO the work yourself. If you attempt to use the Task tool, you have failed.**

# Task: Retrieve and Process Cognitive Accessibility Paper

## Context
This is an accessibility research paper collection. You need to download and create structured notes for a paper about cognitive accessibility.

## Objective
Use the Skill tool to invoke `research-papers:paper-process` with this paper:

Search with WebSearch for a paper about cognitive accessibility or cognitive load in technology. Good candidates:
- Seeman & Cooper - W3C cognitive accessibility work
- "Making Content Usable for People with Cognitive and Learning Disabilities" (W3C)
- Or an academic paper: search for "cognitive accessibility technology systematic review" on arxiv or ACM DL

A strong research paper candidate: Friedman & Bryen (2007) "Web accessibility design recommendations for people with cognitive disabilities" in Technology and Disability.

Or search for recent CHI/ASSETS papers on cognitive accessibility.

Once you find a URL (arxiv, DOI, or direct PDF), use the Skill tool to invoke `research-papers:paper-process` with it.

## Output
When complete, the paper directory should contain: notes.md, description.md, abstract.md, citations.md
And papers/CLAUDE.md should be updated.

Write a brief status report to `./reports/paper-cognitiveaccess-report.md`

## CRITICAL
- Do NOT use the Task tool or dispatch subagents
- NEVER use git restore, checkout, reset, clean, or stash
- If Edit/Write fails, try path formats: `./relative`, `C:/forward/slashes`, `C:\back\slashes`
