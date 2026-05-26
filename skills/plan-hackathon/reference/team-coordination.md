# TEAM_COORDINATION.md Template

Only generate this if team size > 1. Replace all [BRACKETS].

```markdown
# Team Coordination — [PROJECT_NAME]

**Repo:** [repo_url]
**Deploy:** [deploy_url]

## Roles

// WHY: Each person owns SPECIFIC FILES, not concepts. "You do Nimble stuff" is too vague.
// WHY: Kill criteria with deadlines prevent "almost done" at submission time.

| Person | Owns | P0 task | Kill criterion | Deadline |
|--------|------|---------|----------------|----------|
| [Name] | [specific files/features] | [one sentence] | [what "done" looks like] | [time] |

## Integration flow (who touches what)

// WHY: Shows how pieces connect. Prevents two people editing the same file.

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

// Repeat for each team member

## Demo commands (everyone)

```bash
[setup commands]
[run commands]
[test commands]
```

## Freeze checklist ([FREEZE_TIME])

// WHY: Everyone checks in at feature freeze. No surprises.

- [ ] [Person A]: [their deliverable] working?
- [ ] [Person B]: [their deliverable] working?
- [ ] Core loop runs end-to-end?
- [ ] Demo mode returns fixtures?
- [ ] Repo pushed, README updated?
```

## Team split patterns (from analyzed winners)

### 4-person team (PolicyGuard pattern)
| Role | What they own | Key trait |
|------|-------------|-----------|
| **Core engineer** | API, pipeline, data model, deploy | Strongest builder. Owns the critical path. |
| **Integration 1** | Sponsor tool A integration | One file, clear handoff point. |
| **Integration 2** | Sponsor tool B + payments | One file, clear handoff point. |
| **Glue person** | README, UI, demo polish, devpost, site | Makes everything look cohesive for judges. Often most commits. |

### 2-person team
| Role | What they own |
|------|-------------|
| **Builder** | Agent loop, API, core logic, sponsor integrations |
| **Presenter** | UI, dashboard, demo prep, devpost, slides, README |

### Solo
Everything is yours. Prioritize: core loop → UI → polish → demo prep.
The CLAUDE.md IS your teammate — write it so well that Claude Code can execute phases independently.
