# Idea Scoring Framework

## Scoring grid template

For each idea, fill this grid using the hackathon's ACTUAL judging criteria:

| Criterion | Weight | Score (1-5) | Reasoning | What would make it a 5 |
|-----------|--------|-------------|-----------|----------------------|
| [from rubric] | [%] | | | |

Weighted total = sum(score × weight). Compare across ideas.

## Challenge questions

Ask EVERY question. Don't skip uncomfortable ones.

### 1. "Can a judge understand this in 30 seconds?"
// WHY: Judges see 20+ demos. If yours needs explanation, you lose.
// WINNING PATTERN: "PolicyGuard is the compliance API for AI agents" — one sentence, immediately clear.
// RED FLAG: If you need to say "so basically what this does is..."

### 2. "What's the one-sentence pitch?"
// WHY: Forces clarity. If you can't say it in one sentence, scope is wrong.
// TEMPLATE: "[Product] is [what it is] that [key differentiator]."
// WINNING EXAMPLE: "GhostWriter closes the GEO loop — monitor, act, measure, prove, transact."

### 3. "Is this a wrapper or an autonomous agent?"
// WHY: Most hackathons score "autonomy" highly. Wrappers that just call an API don't count.
// TEST: After the user clicks ONE button, does it make decisions without human input?
// WINNING PATTERN: GhostWriter — one click runs the entire monitor→publish→measure loop.

### 4. "Which sponsor prizes does this NATURALLY target?"
// WHY: Forced integrations are obvious to judges. Natural fits win sponsor prizes.
// FRAMEWORK: For each sponsor, ask:
//   - Does the product genuinely need this tool? (not "we could add it")
//   - Can judges SEE the tool working during the 3-min demo?
//   - Does it meet the sponsor's SPECIFIC criteria? (read the prize description carefully)
// WINNING PATTERN: PolicyGuard naturally needed Nimble (fetch policies), Senso (publish to cited.md),
//   ClickHouse (log decisions). Each was visible in the demo.

### 5. "Can you demo the wow moment in under 60 seconds?"
// WHY: The demo is typically 3 min. The wow moment must hit in the first 60s.
// TEST: What's the single most impressive thing? Can you show it, not explain it?
// WINNING PATTERN: GhostWriter — click Deploy → agent runs → chart climbs. Visible in 30s.

### 6. "What happens when the API is down during demo?"
// WHY: Live demos break. Winners have DEMO_MODE=true that returns deterministic fixtures.
// REQUIREMENT: Build demo mode as a first-class feature, not an afterthought.
// WINNING PATTERN: PolicyGuard had POLICYGUARD_DEMO_MODE=true returning fixture verdicts.

### 7. "Is this achievable in the build window?"
// WHY: Overscoping is the #1 killer. Cut 40% of what you think you can build.
// TEST: Can the core loop (minimum viable demo) be done in 50% of build time?
// RULE: If the core loop isn't working at the halfway mark, cut features to protect it.

## Sponsor optimization framework

For each sponsor prize:

| Sponsor | Prize | Natural fit? | Visible in demo? | Meets specific criteria? | Target? |
|---------|-------|-------------|------------------|------------------------|---------|
| [name] | [amount] | Yes/Forced/No | Yes/No | Yes/Partial/No | Y/N |

Only target prizes where all three columns are "Yes".

## Winning idea patterns (from analyzed winners)

1. **Close a loop competitors leave open.**
   GhostWriter: "Every GEO tool monitors and recommends. We act and measure."
   PolicyGuard: "No compliance layer exists for AI agents acting on the web."

2. **Frame as infrastructure, not an app.**
   "The compliance API for the agentic web" > "A tool that checks policies"
   Infrastructure framing signals bigger vision to judges.

3. **Ride a trend that's getting worse.**
   AI agents acting without checking permissions (PolicyGuard).
   Brands being misrepresented by AI search (GhostWriter).
   Find a problem that's accelerating — cite data if possible.

4. **One trigger, full autonomy.**
   The user clicks ONE button. Everything else is autonomous. This is often 20% of the score.
