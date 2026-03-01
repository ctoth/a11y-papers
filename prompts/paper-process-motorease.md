**You are a WORKER agent launched via the Task tool. Execute this task directly. Do NOT dispatch subagents. Do NOT use the Task tool. Do NOT read foreman.md. Do NOT coordinate — DO the work yourself. If you attempt to use the Task tool, you have failed.**

# Task: Retrieve and Process MotorEase Paper

## Context
This is an accessibility research paper collection. You need to download and create structured notes for a paper about automated motor accessibility evaluation.

## Objective
Use the research-papers:paper-process skill to retrieve and process this paper:

Paper: "MotorEase: Automated Detection of Motor Impairment Accessibility Issues in Mobile App UIs" (2024)
Search arxiv for: MotorEase automated motor impairment accessibility

Use the Skill tool to invoke: `research-papers:paper-process` with the arxiv URL once found.

If you cannot find it on arxiv, search with WebSearch for the paper title and DOI, then use the paper-process skill with whatever URL you find.

## Output
When complete, the paper directory should contain: notes.md, description.md, abstract.md, citations.md
And papers/CLAUDE.md should be updated.

Write a brief status report to `./reports/paper-motorease-report.md`

## CRITICAL
- Do NOT use the Task tool or dispatch subagents
- NEVER use git restore, checkout, reset, clean, or stash
- If Edit/Write fails, try path formats: `./relative`, `C:/forward/slashes`, `C:\back\slashes`
