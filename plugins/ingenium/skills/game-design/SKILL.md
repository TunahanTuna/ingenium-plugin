---
name: game-design
description: Game design before game code - shape a vague idea into a buildable, fun game. Core loop definition, one-page game design document, ruthless MVP scoping (is it fun with rectangles?), difficulty and progression curves, reward schedules and economy sanity, level design principles and playtest methodology. Use when starting a new game, when a game idea is fuzzy, when a prototype is not fun yet, or when balancing difficulty, progression or rewards. Türkçe tetikleyiciler - "oyun fikrim var", "oyun tasarlayalım", "oyun dokümanı hazırla", "core loop tasarla", "oyun sıkıcı olmuş", "zorluk dengesini ayarla", "level tasarımı", "oyun ekonomisi kur", "oyunum eğlenceli değil".
---

# Game Design

You design the smallest fun thing, then grow it. Fun is *found* through iteration, never specified up front — so your job is to get the idea to a testable core loop fast, and to protect the project from its own scope.

Always communicate with the user in their own language.

## Phase 1 — Interrogate the idea

Extract (or propose, if the user can't answer — offer 2–3 sharp options, not open questions):

- **Fantasy**: what does the player *get to be or do*? ("be a sneaky goose", "build an empire from nothing")
- **Core verbs**: the 1–3 actions the player repeats (jump, build, deceive, combine). More than 3 core verbs in an MVP is a red flag.
- **The 30-second loop**: do X → get Y → want Z → repeat. If this sentence can't be written, the idea isn't a game yet — it's a theme.
- **Fail state and stakes**: what does losing mean, and how fast is retry?
- **Session shape**: 2-minute runs or 2-hour sits? This drives everything downstream.
- **References**: two games to steal from, one trap to avoid ("like Celeste's movement, without the story scope").

## Phase 2 — One-page GDD (one page, enforced)

A 30-page document about an unbuilt game is fiction. Produce exactly this:

```markdown
# <Title>
**Concept**: <one sentence - fantasy + core verb + twist>
**Core loop**: <X → Y → Z → repeat>
**Mechanics — MVP**: <3-5 bullets max>
**Mechanics — later**: <parking lot; nothing here blocks MVP>
**Progression**: <what changes as the player gets better/further>
**Look & sound**: <one line, e.g. "1-bit pixel, moody ambient">
**This game is NOT**: <2-3 scope guardrails>
**Fun test**: <the question a playtest must answer>
```

## Phase 3 — MVP scoping (ruthless)

- One mechanic, one level, one challenge type, placeholder art.
- **The rectangle test**: the core loop must be fun with colored rectangles. Art hides boring mechanics only temporarily.
- Content multiplies later, mechanics don't: 1 great verb × 20 levels beats 5 verbs × 4 levels.
- Cut anything the fun test doesn't need — menus, settings, save systems all wait.

## Phase 4 — Difficulty and progression

- Teach in the pattern: **introduce safely → practice → test → combine**. Each new element gets a no-punishment introduction before it appears in combinations.
- Difficulty grows through **combinations and context**, not stat inflation (enemy with more HP is not harder, it is longer).
- Calibrate failure cost: instant retry (Celeste, Super Meat Boy) buys you permission for high difficulty; expensive retry demands gentler curves.
- Design valleys after peaks — a breather level after a hard one is pacing, not padding.
- Skill floor vs ceiling: easy to do, hard to master (a dash anyone can use, experts cancel-chain).
- Assist options (game speed, damage taken) are design for reach, not cheating — decide them on purpose.

## Phase 5 — Rewards and economy

- Layered schedule: constant small (score ticks, sounds), periodic medium (level clear, unlock), rare large (new ability, boss down).
- Favor **intrinsic** rewards (mastery, discovery, expression) reinforced by extrinsic ones — pure number-go-up burns out.
- Economy sanity table: list every source and every sink of each currency/resource; a resource with sources and no sinks inflates into meaninglessness.
- New ability > new number: unlocks that change *how you play* beat +5% damage.
- No dark patterns in a premium game: no artificial timers, no fake scarcity, no FOMO mechanics.

## Phase 6 — Level design principles

- The first level IS the tutorial — teach with level shape, not text boxes (the first pit teaches jumping better than a prompt).
- Guide with light, color, motion and geometry lines; players follow contrast.
- Reward curiosity: visible-but-not-obvious secrets make exploration a habit.
- Each level has a *thesis* — one idea it introduces, twists or masters.

## Phase 7 — Playtest loop

- Watch someone play in silence; where they stop smiling, get lost or quit is the data. If remote, ask structured questions: "where did you get stuck or bored?" — never "did you like it?" (everyone lies).
- Change ONE thing per iteration, informed by the fun-test question from the GDD.
- Kill features that don't serve the core loop, even the clever ones. Especially the clever ones.

## Handoff

Design settled → implementation via **pixel-game-dev** (web/pixel art) or **godot-dev** (Godot/native path). Bring the one-page GDD along; it becomes the scope contract.
