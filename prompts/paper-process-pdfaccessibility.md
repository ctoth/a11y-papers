**You are a WORKER agent launched via the Task tool. Execute this task directly. Do NOT dispatch subagents. Do NOT use the Task tool. Do NOT read foreman.md. Do NOT coordinate — DO the work yourself. If you attempt to use the Task tool, you have failed.**

# Task: Retrieve and Process PDF Accessibility Paper

## Context
This is an accessibility research paper collection. You need to download and create structured notes for a paper about PDF document accessibility.

## Objective
Use the Skill tool to invoke `research-papers:paper-process` with this paper:

Paper: Wang et al. - large-scale study of PDF accessibility (analyzed thousands of PDFs)
The specific paper is likely: "Improving the Accessibility of Scientific Documents" or a similar title analyzing PDF accessibility at scale.

Search with WebSearch for: "PDF accessibility research paper" site:arxiv.org OR site:dl.acm.org
Look for papers by Lucy Lu Wang or similar authors who did large-scale PDF accessibility analysis.

A strong candidate: "Do HTML and ARIA Improve the Accessibility of PDF Documents?" or "SciA11y" papers.

Once you find a URL, use the Skill tool to invoke `research-papers:paper-process` with it.

## Output
When complete, the paper directory should contain: notes.md, description.md, abstract.md, citations.md
And papers/CLAUDE.md should be updated.

Write a brief status report to `./reports/paper-pdfaccessibility-report.md`

## CRITICAL
- Do NOT use the Task tool or dispatch subagents
- NEVER use git restore, checkout, reset, clean, or stash
- If Edit/Write fails, try path formats: `./relative`, `C:/forward/slashes`, `C:\back\slashes`
