# TEAM_COORDINATION.md Template

Only generate this if team size > 1. Replace all [BRACKETS].

```markdown
# Team Coordination — [PROJECT_NAME]

**Repo:** [repo_url]
**Deploy:** [deploy_url]

## Roles

IMPORTANT: The Agent Builder must own the entire pipeline + all tool calls.
Integration helpers build raw API wrappers to the Agent Builder's defined interface.
Agent Builder writes mocks FIRST so they're never blocked. See "Team split patterns" below.

| Person | Owns | P0 task | Kill criterion | Deadline |
|--------|------|---------|----------------|----------|
| [Name] | [specific files/features] | [one sentence] | [what "done" looks like] | [time] |

## Integration flow (who touches what)

- Shows how pieces connect. Prevents two people editing the same file.

```
[Person A]: [input] → [their module]
[Person B]: [their module] → feeds into [Person A's module]
[Person C]: [their module] reads from [shared resource]
```

## Per-person details

### @[Person] — [area] (P0)

**Ask:** [One question that determines if their part is on track]
**Kill criterion by [time]:** [What must be true, or fallback plan]
**Where to wire:** [Specific file paths they should be editing]
**Handoff to [other person]:** [What they deliver to whom]

- Repeat for each team member

## Demo commands (everyone)

```bash
[setup commands]
[run commands]
[test commands]
```

## Freeze checklist ([FREEZE_TIME])

- Everyone checks in at feature freeze. No surprises.

- [ ] [Person A]: [their deliverable] working?
- [ ] [Person B]: [their deliverable] working?
- [ ] Core loop runs end-to-end?
- [ ] Demo mode returns fixtures?
- [ ] Repo pushed, README updated?
```

## What's already done (don't redo)

- PolicyGuard's HANDOFF.md started with a status table so nobody wasted time
- redoing setup work. Critical when teammates arrive at different times.

| Layer | Status | Notes |
|-------|--------|-------|
| [Repo created] | DONE | [url] |
| [Deployed blank app] | DONE/TODO | [deploy url] |
| [API keys obtained] | DONE/TODO | In `.env.local` |
| [Sponsor tool tested] | DONE/TODO | `npm run test:[sponsor]` green |
| [Demo scenario decided] | DONE/TODO | [brand/input] |

## Concrete demo scenarios

- PolicyGuard pre-defined EXACTLY 3 actions with expected results.
- No improvisation on demo day. Everyone knows what "success" looks like.

| # | Input | Expected result | Sponsor visible |
|---|-------|----------------|-----------------|
| 1 | [specific input] | [specific output/verdict] | [which sponsor tool] |
| 2 | [specific input] | [specific output/verdict] | [which sponsor tool] |
| 3 | [specific input] | [specific output/verdict] | [which sponsor tool] |

## Acceptance criteria ("ready to demo" at [FREEZE_TIME])

- PolicyGuard had explicit acceptance criteria. If ANY is red, you're not done.

- [ ] Core loop runs end-to-end on live data (not just fixtures)
- [ ] Demo mode fixtures return deterministic results
- [ ] All [N] sponsor tools visible in the demo flow
- [ ] Demo scenario runs in under [DEMO_LENGTH]
- [ ] Backup recording exists
- [ ] README documents setup + sponsor tools
- [ ] Devpost draft written

## Team split patterns (from analyzed winners)

### Critical principle: Agent Builder owns the pipeline

The person building the agent/pipeline must own ALL tool calls and define
the integration interfaces. Integration helpers build raw API wrappers to
the Agent Builder's spec. This way:
- Agent Builder writes mocks/fixtures FIRST, is never blocked
- Integration helpers replace mocks with real API calls
- Agent Builder can test end-to-end at any time
- No cross-dependency friction

DO NOT split by "each person owns a different sponsor integration" —
the agent person can't test without knowing what integrations return.

### 4-person team
| Role | What they own | Key trait |
|------|-------------|-----------|
| **Agent Builder** | Pipeline/loop, ALL tool calls, API routes, demo fixtures, deploy | Defines integration interfaces. Writes mocks first. Tests end-to-end. Never blocked. |
| **Integration Helper A** | One raw API wrapper (e.g. `nimble.ts`) to Agent Builder's spec | Builds to the function signature Agent Builder defined. Moves to help Agent Builder when done. |
| **Integration Helper B** | Another raw API wrapper (e.g. `senso.ts`, `clickhouse.ts`) | Same — once wrapper works, helps Agent Builder or Glue Person. |
| **Glue Person** | UI, dashboard, README, devpost, demo recording, slides | Makes everything presentable. Often most commits. The "taste" person. |

**Interface contract:** Agent Builder defines the function signatures on day 1:
```typescript
// Agent Builder writes this interface. Helpers implement it.
searchBrand(brand: string): Promise<BrandMention[]>
publishCorrection(data: Correction): Promise<{url: string}>
```

### 3-person team
| Role | What they own |
|------|-------------|
| **Agent Builder** | Pipeline, ALL tool calls, API routes, demo fixtures |
| **Integration Helper** | All raw API wrappers to Agent Builder's spec |
| **Glue Person** | UI, dashboard, README, devpost, demo recording |

### 2-person team
| Role | What they own |
|------|-------------|
| **Agent + Backend** | Pipeline, tool calls, API routes, all integrations, demo fixtures |
| **UI + Demo** | Dashboard, components, README, devpost, slides, demo recording |

### Solo
Everything is yours. Prioritize: core loop → UI → polish → demo prep.
The CLAUDE.md IS your teammate — write it so well that Claude Code can execute phases independently.
