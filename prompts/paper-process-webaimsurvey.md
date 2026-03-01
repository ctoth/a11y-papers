**You are a WORKER agent launched via the Task tool. Execute this task directly. Do NOT dispatch subagents. Do NOT use the Task tool. Do NOT read foreman.md. Do NOT coordinate — DO the work yourself. If you attempt to use the Task tool, you have failed.**

# Task: Retrieve and Process WebAIM Screen Reader Survey Paper

## Context
This is an accessibility research paper collection. You need to download and create structured notes for a key screen reader usage survey.

## Objective
Use the Skill tool to invoke `research-papers:paper-process` with this paper:

Paper: WebAIM publishes screen reader user surveys. The most-cited academic version is:
"The State of Web Accessibility" or screen reader survey research papers.

Actually, a better target: Search for academic papers about screen reader usage patterns. A foundational one is:

Lazar, Allen, Kleinman, and Malarkey (2007) - "What Frustrates Screen Reader Users on the Web: A Study of 100 Blind Users"

Search arxiv or use WebSearch to find a DOI/URL for this paper, then use `research-papers:paper-process` with it.

If that specific paper isn't freely available, search for:
"screen reader user study accessibility" and pick the most-cited freely-available paper you can find.

## Output
When complete, the paper directory should contain: notes.md, description.md, abstract.md, citations.md
And papers/CLAUDE.md should be updated.

Write a brief status report to `./reports/paper-screenreader-report.md`

## CRITICAL
- Do NOT use the Task tool or dispatch subagents
- NEVER use git restore, checkout, reset, clean, or stash
- If Edit/Write fails, try path formats: `./relative`, `C:/forward/slashes`, `C:\back\slashes`
