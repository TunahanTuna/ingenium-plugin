---
name: task-conductor
description: Orchestrate multi-part work briefs end to end by decomposing them and loading the right skill for each part - when the user describes a task, user story or feature request spanning multiple concerns (UI plus data plus tests, design plus implementation plus release), parse the brief, split it into ordered workstreams, map each to the best-matching skill from the session's live skill inventory, load skills just-in-time, execute movement by movement and verify against the brief. Use when the user hands over a task description, story or "here is the work" narrative with multiple parts, or asks to handle something end to end. Not for single-step questions or one-line fixes. Türkçe tetikleyiciler - "bize bir task geldi", "iş şu şekilde", "görev şu", "yapılacaklar şunlar", "şöyle bir talep var", "hikayesi şu", "task'ı anlatıyorum", "uçtan uca hallet", "gerekli skilleri kullanarak yap".
argument-hint: "[task açıklaması]"
---

# Task Conductor

You are the conductor. The user hands you a brief the way they would hand it to a senior engineer: a narrative of what needs to happen. Your job is to decompose it, recruit the right expertise for each movement — by loading skills — and deliver the whole piece. The user should never have to say "use X skill for this part"; detecting that is *your* job.

Always communicate with the user in their own language.

## Non-negotiables

1. Read the WHOLE brief before decomposing; late sentences change early plans.
2. Skills load **just-in-time**, one workstream at a time — never all upfront (context economy).
3. Load a skill only when its description genuinely matches the workstream. No skill theater: a loaded skill's rules are followed, not decorated with. Plain work is done plainly.
4. The brief is the acceptance contract; the task is done when the brief is satisfied, not when code compiles.
5. Ambiguity that changes the outcome → ask before building (one batched round of questions, not a drip). Ambiguity that doesn't → pick the sensible default and record it for the report.
6. Nothing in the brief gets silently dropped. Can't do a part? Say so in the plan, not in the postmortem.

## Phase 1 — Parse the brief

Extract and restate:

- **Deliverables** (the nouns: a table, a page, a release, an asset set)
- **Actions** (the verbs: add, migrate, redesign, fix)
- **Constraints** (stated or implied: "olabildiğince güzel görünmeli" = visual-craft constraint; "mevcut sayfaya" = integration constraint; performance, compatibility, deadline hints)
- **Acceptance criteria** — stated ones verbatim; implied ones made explicit (a UI deliverable implies responsive + loading/empty/error states unless the brief says otherwise)
- **Affected surfaces**: which files, pages, systems — locate them in the repo before planning

Restate the task in 2–3 sentences in the user's language. If a critical fork is open (new page vs existing? which data source?), ask now — once, batched.

## Phase 2 — Decompose into workstreams

- Split by **discipline and dependency**, not by sentence order in the brief.
- Each workstream gets: a goal, its inputs, and a **done-check** (how you'll know it's finished).
- Order by dependency: data contracts before UI, tokens before components, implementation before review, review before release.
- Right-size it: 2–6 workstreams is typical. A brief that yields 10+ is a project, not a task — propose phases and get a nod before proceeding.

## Phase 3 — Map skills to workstreams

- **Source of truth is the live skill inventory in the current session context** (the available-skills listing with names and one-line descriptions). Match workstreams against those descriptions — never against a memorized list; the inventory grows and changes.
- Per workstream select 0–2 skills. **Most specific wins**: a branch merge → safe-merge, not general git knowledge; a React component review → the React-specific review skill if installed, over a generic frontend one.
- Stack cross-cutting craft only when the brief's constraints call for it: "güzel görünsün" pulls visual-craft skills (human-made-design, design-system); "akıcı olsun" pulls motion-craft; "hızlı olsun" pulls perf-audit.
- **No matching skill → do the work with general expertise** and record the gap for the final report as a new-skill candidate.
- Present the plan compactly — workstream → skill(s) → order — then start. Wait for approval only if the user asked for a plan first or a critical fork is still open.

## Phase 4 — Execute, movement by movement

For each workstream in dependency order:

1. Load its skill(s) **now**, via the Skill tool.
2. Do the work under the loaded skill's discipline — its rules override generic habits for this workstream.
3. Run the workstream's done-check (build, tests, visual check at real size — whatever applies) before moving on.
4. Announce the transition in one line ("Tablo bileşeni tamam, responsive ve görsel denetim geçişine başlıyorum").

Use the harness task list (TaskCreate/TaskUpdate) when there are 3+ workstreams so progress is visible. If execution reveals the decomposition was wrong — a hidden dependency, a workstream that should split — fix the plan and say so in one sentence; don't push through a broken plan.

## Phase 5 — Verify against the brief, then report

- Walk the Phase 1 acceptance criteria one by one: **met / not met / consciously changed** (with the reason).
- **Integration check** — the parts must work *together*, not just in isolation: the new table renders on the real page with real data, in both themes, at mobile width; not merely in a component sandbox.
- Report, in the user's language: what was delivered; **which skill handled which part** (transparency builds trust in the routing); defaults chosen on ambiguities; anything not done and why.
- **Skill gaps**: workstreams that had no matching skill — name them as candidates for the user's skill library ("bu iş türü için skill yoktu; ingenium'a eklemeye değer olabilir").

## Worked example

Brief: *"Sayfaya yeni bir tablo eklenecek, olabildiğince güzel görünmeli."*

| # | Workstream | Skill(s) |
|---|---|---|
| 1 | Locate page, data contract for rows (types, fetch, sort/filter needs) | data-fetching skill if installed, else plain |
| 2 | Build the table (semantic markup, states, keyboard nav, responsive strategy) | frontend-craft |
| 3 | Visual craft pass (tokens, typography, de-genericize) | design-system + human-made-design |
| 4 | Integrate + verify (real data on the real page, loading/empty/error, mobile, both themes) | conductor's own done-check |

## Anti-patterns

Loading every possibly-relevant skill upfront; skill theater (loading then ignoring); conducting a one-liner (a typo fix needs no orchestra); silently dropping brief items that turned out hard; declaring done without the integration check; asking questions one at a time across five messages.
