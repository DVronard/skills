---
"mattpocock-skills": minor
---

Add **`humanizer-ru`** to the **Productivity** bucket — a Russian-prose editor that strips the marks of AI generation, officialese and padding while keeping every fact of the original. It carries 38 slop patterns, a hard-ban list (negative parallelisms, em dashes, maths signs in prose, stacked chopped fragments), a deterministic linter, and a detect-only mode that audits a text and returns a verdict without touching a word of it.

Its defining move is that audit, fix and verify are three phases that never overlap. A model that starts rewriting while it reads repeats its own tells and misses half the patterns, so the first phase only builds a table of findings — quote, pattern number, treatment — and on a clean text it stops there and hands the text back unchanged, because re-editing prose that has nothing wrong with it only makes it worse. Verification is machine-checkable rather than a vibe: `scripts/lint.py` has to come back with zero errors, and where the harness has subagents a blind reader gets the final text and the pattern reference alone — no original, no findings table — because an editor recognises its own phrasing and grades it softly.

Productivity rather than engineering: it fires on sales scripts, comments and site copy as readily as on a README, and it refuses code, configs, legal and academic text outright, where the officialese is the genre rather than the defect. Model-invoked, because the trigger is "this reads like a bot" — something the agent can catch in the draft it is about to hand you, before you have to ask.

Wired as a promoted skill — plugin entry, an `agents/openai.yaml` interface for Codex, top-level and Productivity READMEs under **Model-invoked**, a docs page at `docs/productivity/humanizer-ru.md`, and a Standalone route in `ask-matt` that draws the border with `/wait-what` (the agent's last message, not a text of yours) and `/writing-for-agents` (documents agents read, not prose for people).

Vendored from [smixs/humanizer-ru](https://github.com/smixs/humanizer-ru) at v1.7 (commit `ff990df`), MIT, with the upstream `LICENSE` kept alongside `SKILL.md`.
