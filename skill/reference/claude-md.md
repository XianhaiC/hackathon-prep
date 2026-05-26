# CLAUDE.md Template for Hackathons

Generate this customized for the user's hackathon. Replace all [BRACKETS].

```markdown
# CLAUDE.md — [PROJECT_NAME] ([HACKATHON_NAME])

> Single source of truth. Read SPEC.md for full product spec. Read BATTLE_KIT.md for timeline + pitch.

## What we're building (one line)
// WHY: Forces clarity. If you can't say it in one line, scope is wrong.

**[PROJECT_NAME]** — [one sentence: what it is + what makes it different from everything else].

## Why this wins (the judging grid)
// WHY: Map EVERY criterion to your project. If any cell is weak, fix the idea not the grid.

| Criterion | Weight | How [PROJECT_NAME] scores |
|-----------|--------|--------------------------|
| [criterion_1] | [weight]% | [specific claim] |
| [criterion_2] | [weight]% | [specific claim] |
| ... | | |

## The stack (decided — do not re-litigate)
// WHY: Stack debates burn hours. Decide once, move on.

- **Frontend/host:** [framework] + [deploy target]
- **Agent/LLM:** [SDK + model]
- **[Sponsor 1]:** [what it does in your project]
- **[Sponsor 2]:** [what it does]
- ...

## Build order (phases — never skip, never reorder)
// WHY: Phased execution prevents scope creep. Each phase has a "done =" gate.

1. **Scaffold** (~[X]m): [Deploy target] blank deploy, env vars, integration stubs. Done = blank app live.
2. **Core loop** (~[X]m): The autonomous loop end-to-end, ugly. Done = one full run in console.
3. **Dashboard/UI** (~[X]m): Render results, progress, one-click trigger. Done = click once → result renders.
4. **Polish** (~[X]m): Sponsor proof panels, loading states, realistic data. Done = demo looks intentional.
5. **Demo prep** (~[X]m, LOCKED): Seed data, rehearse 3x, record backup, push repo, submit. Done = submitted.

## Hard rules (non-negotiable)
// WHY: These prevent the most common hackathon failures.

- **Scope gate:** Before adding ANY feature: will the judge see it in [DEMO_LENGTH]? Does the demo work without it? Can it be built in <20 min? If any NO → don't build it.
- **Autonomy is the demo.** The loop runs by itself once triggered. No "click next step."
- **[MIN_SPONSORS]+ sponsor tools visible in demo.** Code-only doesn't count.
- **Feature freeze at [FEATURE_FREEZE_TIME].** After this: polish + demo prep ONLY.
- **Seed don't scrape-live-for-everything.** Pre-seed "before" data. Live run produces "after."
- **Demo mode:** `DEMO_MODE=true` returns deterministic fixtures. Build this FIRST, not last.

## Conventions

- TypeScript everywhere. Small, single-purpose files.
- Each sponsor integration in its own module under `lib/integrations/` — so a broken one can be stubbed.
- One agent loop module (`lib/agent/loop.ts`) — orchestration isolated and testable.
- Commit every ~30 min. Working code only on main.

## Demo target (what must be true at submission)
// WHY: Work backwards from this. If it's not on this list, don't build it.

- [ ] One click runs the full autonomous loop to a rendered result
- [ ] Each sponsor tool is VISIBLE in the demo (not just in code)
- [ ] [specific_demo_moment_1]
- [ ] [specific_demo_moment_2]
- [ ] (Bonus) [stretch_feature]
- [ ] Public GitHub repo pushed
- [ ] [DEMO_LENGTH] demo recording uploaded
```
