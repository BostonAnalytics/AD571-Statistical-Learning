---
name: course-note-editor
description: Edit AD571 or other course lecture notes, Quarto books, teaching chapters, labs, or educational prose so they read as polished student-facing material. Use when revising course notes, converting notebooks/slides into lectures, removing process chatter, preventing source-mining notes from leaking into chapters, or checking that instructional content is concise, neutral, and publication-ready.
---

# Course Note Editor

## Rule

Treat lecture chapters as student-facing course material. Do not expose
agent thoughts, migration history, source-mining notes, TODO chatter, or
private editorial reasoning in chapter prose.

## Editing Workflow

1. Separate audiences before editing:
   - Put concepts, explanations, examples, equations, and exercises in
     lecture chapters.
   - Put provenance, local paths, migration notes, build plans, and
     conversion instructions in maintainer docs.
2. Rewrite source references into teaching content:
   - Bad: "The retired M3 draft covered Monte Carlo simulation."
   - Good: "Monte Carlo simulation propagates uncertainty through a
     decision model."
3. Remove process language from chapters:
   - "retired draft"
   - "merged"
   - "next pass"
   - "placeholder"
   - "book version"
   - "source notes"
   - "build status"
   - "student-facing text"
   - "this should become"
4. Keep future-work notes out of lectures unless they are framed as
   learning objectives or exercises.
5. Before finishing, search changed course files for process language
   and clean any hits that are not intentionally in maintainer docs.

## Acceptable Locations

Use `docs/source-map.qmd`, `docs/conversion-guide.qmd`, comments, or a
private issue list for provenance and conversion details. Do not place
those details in `lectures/*.qmd` unless the text is genuinely useful to
students.

## Final Check

Run a text scan equivalent to:

```powershell
rg -n "retired|draft|merged|next pass|placeholder|source notes|build status|book version|student-facing|maintainer|local path" lectures docs index.qmd
```

Only `docs/` should normally contain these terms.
