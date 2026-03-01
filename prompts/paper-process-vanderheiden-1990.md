**You are a WORKER agent launched via the Task tool. Execute this task directly. Do NOT dispatch subagents. Do NOT use the Task tool. Do NOT read foreman.md. Do NOT coordinate — DO the work yourself. If you attempt to use the Task tool, you have failed.**

# Task: Retrieve and Process Vanderheiden 1990 Foundational Paper

## Context
This is an accessibility research paper collection (C:/Users/Q/code/a11y-papers). We're building out the historical foundation — papers from the 80s, 90s, and 2000s that established accessibility as a field.

## Objective
Paper: Vanderheiden, Gregg C. (1990) — "Thirty-Something Million: Should They Be Exceptions?" published in Human Factors, Vol. 32, No. 4, pp. 383-396.

This is one of THE foundational papers in accessibility — Vanderheiden (founder of the Trace R&D Center at UW-Madison) argued that 36 million Americans with disabilities should not be treated as edge cases in technology design. This paper predates the ADA (1990) and WCAG by years.

Search with WebSearch for: Vanderheiden 1990 "Thirty-Something Million" "Should They Be Exceptions" Human Factors PDF

If you can't find it freely, try DOI: 10.1177/001872089003200404 via sci-hub using Chrome browser tools.

Use the Skill tool to invoke `research-papers:paper-process` with whatever URL/DOI you find.

## Output
When complete, the paper directory should contain: notes.md, description.md, abstract.md, citations.md
And papers/CLAUDE.md should be updated.

Write a brief status report to `./reports/paper-vanderheiden1990-report.md`

## CRITICAL
- Do NOT use the Task tool or dispatch subagents
- NEVER use git restore, checkout, reset, clean, or stash
- If Edit/Write fails, try path formats: `./relative`, `C:/forward/slashes`, `C:\back\slashes`
