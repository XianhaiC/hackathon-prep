# hackathon-prep

A battle-tested system for winning hackathons, built from analyzing winners at the Agentic Engineering Hack (May 2026).

## What's inside

### `/skill` — Claude Code skill

A `/plan-hackathon` skill for [Claude Code](https://claude.ai/code) that walks you through hackathon planning:

1. **Discovery** — Understands the hackathon rules, judging criteria, sponsor prizes
2. **Idea scoring** — Generates ideas and scores them against the rubric, challenges weak points
3. **Battle documents** — Generates CLAUDE.md, SPEC.md, BATTLE_KIT.md, TEAM_COORDINATION.md
4. **Tech stack** — Recommends a proven stack (Vercel AI SDK, Next.js, Tailwind v4 dark theme)
5. **File generation** — Writes all docs to your project after review

### Install the skill

```bash
cp -r skills/plan-hackathon ~/.claude/skills/plan-hackathon
```

Then in any Claude Code session:
```
/plan-hackathon
```

## Key principles

These come from analyzing two winning projects (PolicyGuard — 4-person team, GhostWriter — solo):

- **Scope kills.** Every feature must pass: "Will the judge see it in 3 min?"
- **Demo mode is mandatory.** `DEMO_MODE=true` returns fixtures. No API = no broken demo.
- **Lock the schema before code.** API contracts, data models — decide FIRST, build to them.
- **Feature freeze = submission - 2 hours.** After that: polish + demo prep only.
- **The devpost is a deliverable.** Write it at feature freeze, not at submission.
- **Dark theme + one accent color.** Looks 10x more polished than white theme with emoji.
- **Each sponsor = one file.** `lib/integrations/nimble.ts` — if it breaks, stub it.
- **Record a backup demo.** If live breaks, switch in 5 seconds without apologizing.

## Recommended stack

| Layer | Choice | Why |
|-------|--------|-----|
| Framework | Next.js (App Router) | One repo, one deploy |
| Deploy | Vercel | Auto-deploy, free |
| AI/LLM | Vercel AI SDK (`ai` + `@ai-sdk/*`) | `generateObject()` + Zod = typed JSON |
| UI | Tailwind CSS v4, dark theme | Fast, hides imperfections |
| Charts | recharts | Simple, React-native |
| Validation | Zod | Works with AI SDK |

## Documents generated

| Document | Purpose |
|----------|---------|
| `CLAUDE.md` | Source of truth for Claude Code — what to build, rules, scope gates |
| `SPEC.md` | Full product spec with sponsor mapping, architecture, risk register |
| `BATTLE_KIT.md` | Day-of timeline, pitch script, demo survival rules, checklists |
| `TEAM_COORDINATION.md` | Owner table, kill criteria, integration flow (teams only) |
| `DEMO_SCRIPT.md` | Timed script with what to say and expect on screen |

## Coming soon

- [ ] Starter template (Next.js + Vercel AI SDK + Tailwind v4 dark theme)
- [ ] Demo mode scaffolding
- [ ] Sponsor integration stubs
- [ ] `npm run demo` harness
