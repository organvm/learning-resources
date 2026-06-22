# Discovery — organvm/learning-resources

**Date:** 2026-06-22
**Verdict:** VALUE FOUND → promote to ranked tier
**Build status at discovery:** green (14 tests passing, `pytest -q`)

## Value Thesis

Beneath an aspirational README that describes a creative-coding *content* repository,
the actual code is something more durable and more reusable: a clean, fully-tested,
**domain-agnostic learning-management engine** in ~470 lines of dependency-free Python.
`CurriculumBuilder` models modules/topics/objectives with Bloom-taxonomy levels and
resolves transitive prerequisite chains (a real DAG walk, not a stub); `LearningPath`
tracks ordered progression, completion, and scoring; `ExerciseBank` creates typed
questions and scores submissions against rubrics. Every primitive serializes to
JSON-ready dicts. Nothing in the code is specific to art — it is a generic substrate
for *any* structured curriculum, onboarding flow, or docs-as-course experience. That is
the latent value, and it is two-sided. (1) **Reusable estate capability:** the eight-organ
system has dozens of sibling repos and four example/showcase projects that each need
onboarding paths, tutorials, and assessable exercises; today there is no shared way to
author and track them. This engine is the natural standard — prerequisite resolution and
rubric scoring are exactly the non-trivial parts teams would otherwise rebuild badly.
(2) **Product/revenue path:** the README articulates a genuine, specific market gap —
Tier-3 *deployment* education for installation artists ("does not exist in any online
course") aimed at university new-media programs, museum workshops, and community events.
This engine is the publishing substrate for that sellable curriculum. The repo is
therefore **not archival**; it is an under-recognized platform primitive one
authoring-and-render step away from producing shippable, monetizable learning artifacts.

## What it actually is (verified)

- **`src/curriculum.py`** — `CurriculumBuilder`: modules → topics → Bloom-tagged
  `LearningObjective`s; transitive `get_prerequisite_chain()`; `export()` to dict.
- **`src/paths.py`** — `LearningPath`: ordered steps, completion timestamps, clamped
  scoring, `get_next_step()`, `progress_pct`, `get_average_score()`.
- **`src/exercises.py`** — `ExerciseBank`: 4 `QuestionType`s, point-weighted
  `score_answers()` rubric scoring.
- **Tests:** 14 passing; **Deps:** none (stdlib only); **Delivery target** (ecosystem.yaml):
  `web_app: not_started`.

## Gap blocking the value

The engine can `export()` to dicts but **cannot import/round-trip or render**. Curricula
can be built only imperatively in Python; they cannot be stored as data, reloaded, or
published. This is the single seam between "tidy library" and "publishing pipeline /
shippable product."

## Single best concrete first task

**Make curricula authorable-as-data and publishable.** Add `load_curriculum(dict)` as a
round-trip inverse of `CurriculumBuilder.export()` (with a test asserting
`export(load(d)) == d`) plus a `render_markdown(curriculum)` function, then commit the
README's **Tier-1 Foundations** pathway (8 modules) as the first data file
`curricula/tier-1-foundations.json`. This closes the export/import seam, proves the engine
on real content, and produces the first publishable artifact toward the dormant `web_app`
delivery target — converting latent value into a shippable learning path.
