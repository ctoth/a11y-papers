# Accessibility Research Papers Collection

This is an annotated research paper collection focused on **digital accessibility** — the design of technology that is usable by people with disabilities.

## Citation Discipline

Every claim about accessibility technology, standards, or research findings must reference a paper in this collection. If a paper isn't in the collection yet, retrieve and annotate it before citing it.

## Topic Areas

- **Screen readers** — JAWS, NVDA, VoiceOver, TalkBack architecture and interaction
- **Web standards** — WCAG, WAI-ARIA, HTML accessibility semantics
- **Assistive technology** — switches, eye tracking, brain-computer interfaces, alternative input
- **Visual impairment** — screen magnification, document accessibility, PDF remediation
- **Cognitive accessibility** — reading level, cognitive load, simplified interfaces
- **Motor impairment** — automated detection, adaptive input, keyboard-only navigation
- **Hearing accessibility** — captioning, sign language, audio description
- **Universal design** — inclusive design principles, design-for-all methodology
- **Evaluation methods** — automated testing, user studies with disabled participants, conformance testing

## Project Structure

```
papers/           # Paper library — each paper gets its own directory
papers/CLAUDE.md  # Paper index (auto-generated, read this first)
reports/          # Research output from /research skill
prompts/          # Prompt templates for large paper processing
scripts/          # Paper management scripts
```

## Paper Library

The paper library lives in `papers/`. Use `papers/CLAUDE.md` as the index — it lists every paper with a brief description.

Each paper directory contains:
- `notes.md` — Implementation-focused notes (START HERE)
- `description.md` — Three-sentence summary
- `abstract.md` — Verbatim abstract + interpretation
- `citations.md` — Full reference list + key follow-up citations
- `paper.pdf` — Original PDF (gitignored)

## Scripts

- `bash scripts/generate-paper-claude-md.sh` — Rebuild papers/CLAUDE.md from all description.md files
- `python scripts/cross-reference-papers.py` — Find and annotate cross-references between papers

## Skills (via research-papers plugin)

- `/research-papers:paper-process <url>` — Retrieve and annotate a paper in one step
- `/research-papers:paper-retriever <url>` — Just download the PDF
- `/research-papers:paper-reader <path>` — Just read and annotate an existing PDF
- `/research-papers:research <topic>` — Web research on a topic
