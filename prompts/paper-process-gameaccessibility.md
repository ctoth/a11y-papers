**You are a WORKER agent launched via the Task tool. Execute this task directly. Do NOT dispatch subagents. Do NOT use the Task tool. Do NOT read foreman.md. Do NOT coordinate — DO the work yourself. If you attempt to use the Task tool, you have failed.**

# Task: Retrieve and Process Game Accessibility Paper

## Context
This is an accessibility research paper collection. You need to download and create structured notes for a paper about game/video game accessibility.

## Objective
Use the Skill tool to invoke `research-papers:paper-process` with this paper:

Search with WebSearch for a highly-cited game accessibility survey or systematic review paper. Good candidates:
- "Game Accessibility: A Survey" by Yuan, Folmer, Harris (2011)
- Or a more recent systematic review of game accessibility

Search arxiv or Google Scholar for: "game accessibility systematic review survey"

Once you find a URL (arxiv, ACL, or DOI), use the Skill tool to invoke `research-papers:paper-process` with it.

## Output
When complete, the paper directory should contain: notes.md, description.md, abstract.md, citations.md
And papers/CLAUDE.md should be updated.

Write a brief status report to `./reports/paper-gameaccessibility-report.md`

## CRITICAL
- Do NOT use the Task tool or dispatch subagents
- NEVER use git restore, checkout, reset, clean, or stash
- If Edit/Write fails, try path formats: `./relative`, `C:/forward/slashes`, `C:\back\slashes`
