**You are a WORKER agent launched via the Task tool. Execute this task directly. Do NOT dispatch subagents. Do NOT use the Task tool. Do NOT read foreman.md. Do NOT coordinate — DO the work yourself. If you attempt to use the Task tool, you have failed.**

# Task: Retrieve and Process Game Accessibility Guidelines Paper

## Context
This is an accessibility research paper collection (C:/Users/Q/code/a11y-papers). We have Yuan_2011 (survey/taxonomy) and are building out the game accessibility cluster. We need a paper focused specifically on practical accessibility guidelines for game developers.

## Objective
Find and process the most impactful paper about game accessibility guidelines — the equivalent of WCAG but for games.

Good candidates (in order of preference):
1. Aguado-Delgado, Santiago; Gutiérrez-Martínez, José-María; Hilera, José R.; de-Marcos, Luis; Otón, Salvador (2020) — "Accessibility in video games: a systematic review" — recent comprehensive guidelines review
2. Gonçalves et al. (2023 or 2024) — any recent game accessibility guidelines paper
3. Cairns, Power, Barlet, Haynes (2019 or 2020) — "Future Design of Accessibility in Games"
4. Any paper specifically analyzing the Xbox Accessibility Guidelines, the Game Accessibility Guidelines (gameaccessibilityguidelines.com), or similar industry standards from an academic perspective

Search with WebSearch for: "game accessibility guidelines" systematic review 2020 2021 2022 2023 research paper arxiv OR acm OR springer

Pick whichever is most comprehensive and available. Use the Skill tool to invoke `research-papers:paper-process` with whatever URL/DOI you find.

## Output
When complete, the paper directory should contain: notes.md, description.md, abstract.md, citations.md
And papers/CLAUDE.md should be updated.

Write a brief status report to `./reports/paper-gameaguidelines-report.md`

## CRITICAL
- Do NOT use the Task tool or dispatch subagents
- NEVER use git restore, checkout, reset, clean, or stash
- If Edit/Write fails, try path formats: `./relative`, `C:/forward/slashes`, `C:\back\slashes`
