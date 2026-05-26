# SPEC.md Template for Hackathons

## Guidelines (read before generating — do NOT copy these into the output)

- **Problem:** One sentence. If it takes two, sharpen it.
- **Solution:** Numbered steps = clear scope. Each step maps to a demo moment.
- **Sponsor mapping:** Makes integration explicit. Judges scan for this. Note which sponsors to cut first if behind.
- **Architecture:** ASCII diagram = shared mental model. One screen max.
- **MVP scope:** Explicit in/out prevents "one more feature." OUT of scope list is as important as IN.
- **Locked schema:** PolicyGuard locked verdict JSON before writing code. Everyone builds to this contract. Don't change it during the hackathon.
- **Autonomy contract:** Many hackathons score autonomy at 20%. Define exactly what "autonomous" means.
- **Data model:** Keep tiny. One table is often enough. Seed "before" data, live run produces "after."
- **Demo scenario:** Undecided = broken demo. Pick ONE, rehearse it. Fake-but-realistic > real-but-flaky.
- **Risk register:** Anticipate failures. GhostWriter had 6 risks with mitigations ready.

---

## Template (generate this — clean, no comments)

```markdown
# SPEC.md — [PROJECT_NAME]

**[HACKATHON_NAME] · [DATE] · build window [START]→[END] · [TEAM_SIZE] · [DEMO_LENGTH] demo**

## 1. The problem (one sentence)

[One sentence describing what's broken/missing in the world]

## 2. The solution

[PROJECT_NAME] is an autonomous agent that [verb]. Point it at [input]. It:
1. **[Verb]s** — [what it does, which tool]
2. **[Verb]s** — [what it does, which tool]
3. **[Verb]s** — [what it does, which tool]
4. **Measures** — [metric tracked, which tool]

All steps run autonomously from a single trigger.

## 3. Sponsor mapping

| Role in product | Sponsor tool | What it does in [PROJECT_NAME] |
|-----------------|-------------|-------------------------------|
| [verb] | [sponsor] | [specific usage] |

> Minimum required: [N] sponsors. We target [M]. If [lowest-priority] runs long,
> cut it first — protect the [core sponsors] minimum.

## 4. Architecture

```
[ASCII architecture diagram showing data flow between components]
```

## 5. MVP scope

### In scope
1. [specific deliverable]
2. [specific deliverable]

### Explicitly OUT of scope
- ❌ [tempting feature] — [why it's out, when it becomes relevant]
- ❌ Auth/login — nobody cares at a hackathon
- ❌ Mobile responsive — judges use a projector

## 5b. Locked API schema (define BEFORE code)

The core output of your product. Lock this FIRST. All code builds to this shape.

```json
{
  "field_1": "type — what it means",
  "field_2": "type — what it means"
}
```

Once locked: do not change during the hackathon. Additive-only if needed.

## 6. The autonomy contract

Once [TRIGGER] is activated, zero human input until the result. The loop must:
- [autonomous decision 1]
- [autonomous decision 2]
- [autonomous decision 3]

In the demo: trigger once and **narrate while it runs itself**.

## 7. Data model (keep tiny)

```sql
CREATE TABLE [table_name] (
  [field] [type],
) ENGINE = MergeTree ORDER BY ([key]);
```

Seed the "before" rows at setup; the live run inserts the "after" rows.

## 8. Demo scenario (pre-decide ONE)

- Brand/input: [specific value]
- Expected flow: [what happens step by step]
- Wow moment: [the single most impressive thing judges will see]

## 9. Risk register

| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|------------|
| Sponsor API slow/down/wrong docs | Med | High | Demo mode fixtures. Test API in setup, not during build. |
| Live demo breaks on stage | Med | High | Backup recording. Switch without apologizing. |
| Scope creep ("one more feature") | High | High | Scope gate in CLAUDE.md. |
| Core loop doesn't converge in time | Low | Critical | Cut to minimum sponsors. Ugly but working > polished but broken. |
| LLM responses non-deterministic | Med | Med | Demo mode returns fixtures. Seed "before" data. |
| Team member blocked/behind | Med | Med | Kill criterion with deadline. Fallback to stub. |

## 10. Definition of done

- [ ] [checkbox 1]
- [ ] [checkbox 2]
```
