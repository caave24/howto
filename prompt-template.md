# Prompt template — build / dev requests

Use this shape any time you want Claude to build or modify something
(an app, script, tool, workflow). Skip sections that don't apply —
the point is coverage, not length.

## 1. One-line goal
What are you building, and what does "done" look like? Say it before
any implementation detail.

> e.g. "A local desktop tool that batch-converts image/video files
> sitting in a repo folder. Nothing touches GitHub itself."

## 2. Environment & constraints
- Language/runtime, OS target(s)
- Standing engineering rules (venv usage, non-regression editing, etc.)
  — state these once, then just say "use my usual rules" afterward
- Existing files to build on top of vs. a fresh project

## 3. Requirements — bulleted, not prose
Split into tiers so priority survives a long list:
- **Must have:** ...
- **Nice to have:** ...

## 4. Fields / data model (if relevant)
A small table beats a sentence — nothing to misparse:

| Field | Type | Example | Notes |
|---|---|---|---|
| repo | text | github.com/user/repo1 | label only |
| output folder | text | /output | appended to local path |

## 5. Explicit non-goals
The single highest-leverage section. Name anything a key term could
be mistaken for.

> e.g. "'Workflow' here means a saved local preset — NOT a
> `.github/workflows` CI file. This should never touch GitHub Actions."

## 6. Deliverable format
- Quick concept/mockup first, then full build? Or straight to full build?
- What files, what format, where should output land?

## 7. Definition of done
A short checklist Claude (and you) can verify against before calling
it finished.

---

## Do you need to define Claude's role?

Usually **no**, not for build tasks — a clear spec (sections 1–7 above)
does more work than a persona. Role framing earns its keep on
**judgment-shaped** tasks instead: "review this as a security engineer,"
"critique this like a skeptical editor," "advise as a financial
planner would." There, the role sets the evaluation lens. For "build
me X," the lens doesn't matter much — the spec does.

## Worked example: your prompt, retrofitted

**Goal:** Desktop Python tool to batch-convert/optimize images, gifs,
and videos in a local repo folder.

**Non-goal:** Not a `.github/workflows` CI file — purely local, no
GitHub Actions involved.

**Must have:** repo label field, local folder + browse, output
subfolder field, file-type filters, output type (images/gifs/videos),
keep-original / optimize / convert-to-gif / smaller-gif checkboxes,
saved named presets.

**Nice to have:** TinyPNG-style optimization if quality-safe.

**Deliverable:** quick graybox concept first, then full working app.

That's the same content you gave me — just organized so the one
ambiguous word ("workflow") can't hide inside a paragraph.
