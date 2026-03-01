**You are a WORKER agent launched via the Task tool. Execute this task directly. Do NOT dispatch subagents. Do NOT use the Task tool. Do NOT read foreman.md. Do NOT coordinate — DO the work yourself. If you attempt to use the Task tool, you have failed.**

# Task: Retrieve and Process LLM/AI for Accessibility Paper

## Context
This is an accessibility research paper collection (C:/Users/Q/code/a11y-papers). We have no papers on the emerging area of using large language models or AI to improve accessibility (alt text generation, automatic remediation, accessibility testing with AI, etc.).

## Objective
Find and process a recent paper on using LLMs or AI for accessibility improvements.

Good candidates:
- Trewin et al. (2020) — "AI Fairness for People with Disabilities" (cited in our Mack collection)
- Zhong et al. (2023) — papers on LLM-generated alt text
- Huh et al. (2023/2024) — "GenAssist" or similar AI-assisted accessibility tools
- Zhang et al. (2024) — any recent CHI/ASSETS paper on AI + accessibility
- Papers on GPT-4V / multimodal LLMs for image description / alt text

Search with WebSearch for: "large language model" OR "LLM" accessibility alt text remediation 2023 2024 arxiv OR acm

Pick the most impactful recent paper available, then use the Skill tool to invoke `research-papers:paper-process` with it.

## Output
When complete, the paper directory should contain: notes.md, description.md, abstract.md, citations.md
And papers/CLAUDE.md should be updated.

Write a brief status report to `./reports/paper-llmaccessibility-report.md`

## CRITICAL
- Do NOT use the Task tool or dispatch subagents
- NEVER use git restore, checkout, reset, clean, or stash
- If Edit/Write fails, try path formats: `./relative`, `C:/forward/slashes`, `C:\back\slashes`
