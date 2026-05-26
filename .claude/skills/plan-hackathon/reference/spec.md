# SPEC.md Template for Hackathons

Generate this customized. Replace all [BRACKETS].

```markdown
# SPEC.md — [PROJECT_NAME]

**[HACKATHON_NAME] · [DATE] · build window [START]→[END] · [TEAM_SIZE] · [DEMO_LENGTH] demo**

## 1. The problem (one sentence)
// WHY: Forces you to articulate the gap. If it takes two sentences, sharpen it.
[One sentence describing what's broken/missing in the world]

## 2. The solution
// WHY: Numbered steps = clear scope. Each step maps to a demo moment.
[PROJECT_NAME] is an autonomous agent that [verb]. Point it at [input]. It:
1. **[Verb]s** — [what it does, which tool]
2. **[Verb]s** — [what it does, which tool]
3. **[Verb]s** — [what it does, which tool]
4. **Measures** — [metric tracked, which tool]
All steps run autonomously from a single trigger.

## 3. Sponsor mapping
// WHY: Makes sponsor integration explicit. Judges can see you thought about tool use.
| Role in product | Sponsor tool | What it does in [PROJECT_NAME] |
|-----------------|-------------|-------------------------------|
| [verb] | [sponsor] | [specific usage] |

> Minimum required: [N] sponsors. We target [M]. If [lowest-priority] runs long,
> cut it first — protect the [core sponsors] minimum.

## 4. Architecture
// WHY: ASCII diagram = shared mental model. Keep it to one screen.
```
[ASCII architecture diagram showing data flow between components]
```

## 5. MVP scope
// WHY: Explicit in/out scope prevents the "one more feature" trap.

### In scope
1. [specific deliverable]
2. [specific deliverable]
...

### Explicitly OUT of scope
- ❌ [tempting feature] — [why it's out, when it becomes relevant]
- ❌ Auth/login — nobody cares at a hackathon
- ❌ Mobile responsive — judges use a projector

## 5b. Locked API schema (define BEFORE code)

// WHY: PolicyGuard locked the verdict JSON schema in HANDOFF.md before writing any code.
// WHY: Everyone builds to this contract. No "let me change the shape" mid-hackathon.

The core output of your product. Lock this FIRST. All code builds to this shape.

```json
// Example: replace with your product's output format
{
  "field_1": "type — what it means",
  "field_2": "type — what it means",
  "nested": {
    "field_3": "type — agents consume this programmatically"
  }
}
```

Once locked: do not change during the hackathon. If you need to add a field, it's additive only.

## 6. The autonomy contract
// WHY: Many hackathons score autonomy. Define exactly what "autonomous" means.
Once [TRIGGER] is activated, zero human input until the result. The loop must:
- [autonomous decision 1]
- [autonomous decision 2]
- [autonomous decision 3]
In the demo: trigger once and **narrate while it runs itself**.

## 7. Data model (keep tiny)
// WHY: Complex schemas waste time. One table is often enough.
```sql
CREATE TABLE [table_name] (
  [field] [type],
  ...
) ENGINE = MergeTree ORDER BY ([key]);
```
Seed the "before" rows at setup; the live run inserts the "after" rows.

## 8. Demo scenario (pre-decide ONE)
// WHY: Undecided demo scenario = broken demo. Pick one, rehearse it.
- Brand/input: [specific value]
- Expected flow: [what happens step by step]
- Wow moment: [the single most impressive thing judges will see]

## 9. Risk register
// WHY: GhostWriter had 6 specific risks with mitigations. Anticipate failures BEFORE they happen.

| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|------------|
| Sponsor API slow/down/wrong docs | Med | High | Demo mode fixtures. Test API in setup phase, not during core build. |
| Live demo breaks on stage | Med | High | Backup recording at [FREEZE+15m]. Switch without apologizing. |
| Scope creep ("one more feature") | High | High | Scope gate in CLAUDE.md. "Will judge see it in 3 min? No? Don't." |
| Core loop doesn't converge in time | Low | Critical | Cut to minimum sponsors. Ugly but working > polished but broken. |
| LLM responses are non-deterministic | Med | Med | Demo mode returns fixtures. Seed "before" data. Live run = "after" only. |
| Team member blocked/behind | Med | Med | Kill criterion with deadline. Fallback to stub. Clear handoff point. |

## 10. Definition of done
- [ ] [checkbox 1]
- [ ] [checkbox 2]
...
```
