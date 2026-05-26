# Devpost Submission Template

Write this at FEATURE FREEZE time, not at submission. Treat it as a deliverable.

// WHY: PolicyGuard's devpost was the most thorough of all submissions.
// WHY: GhostWriter pre-wrote the pitch script which mapped directly to devpost sections.
// WHY: Judges read devpost AFTER demos. A great devpost reinforces a great demo.

```markdown
## Inspiration

// WHY: Ground the problem in reality. Data > opinion. Cite something.
// GOOD: "AI agents are taking real actions on the open web — $600M in x402
//   agent payments annualized. Yet no compliance layer exists."
// BAD: "We wanted to build something cool with AI."

[1-2 paragraphs. State the real-world problem with a data point or citation.
Reference a trend that's getting worse. Make it feel urgent.]

## What it does

// WHY: Walk through a CONCRETE example. Don't describe abstractly.
// WHY: PolicyGuard showed the exact 3-action flow with expected verdicts.
// GOOD: "A sales agent wants to scrape 100 LinkedIn profiles → BLOCKED.
//   Read public pricing → ALLOWED. Bulk-store emails → MODIFY_RECOMMENDED."
// BAD: "It evaluates agent actions against policies."

[Walk through ONE specific scenario step by step. Show the actual input and
output — quote the JSON schema or verdict if relevant. Make judges see
the product working in their mind.]

### Key output format
```json
[Paste your locked schema / output format here — judges love seeing
the actual API response, not a description of it]
```

## How we built it

// WHY: Show the sponsor tools explicitly. Judges scan for this.
// WHY: Architecture table > wall of text.

| Component | Tool | Role |
|-----------|------|------|
| [component] | **[Sponsor Tool]** | [what it does in the product] |
| [component] | **[Sponsor Tool]** | [what it does] |
| ... | ... | ... |

**Architecture:**
```
[Simple ASCII diagram or description of data flow]
```

**Stack:** [Framework], [Language], [LLM SDK], [Deploy target]

## Challenges we ran into

// WHY: Be specific and honest. Generic answers = you didn't actually build it.
// GOOD: "Nimble's SERP API returned raw HTML, not parsed results. We had to
//   discover the parsing.entities.OrganicResult path by testing."
// GOOD: "The LLM produced non-deterministic verdicts. We split into
//   LLM proposal + deterministic rule engine for the final decision."
// BAD: "Time management was hard."

[2-3 specific, technical challenges with what you did about them.]

## Accomplishments that we're proud of

// WHY: What's genuinely impressive? Not "we finished" — what's NOVEL?
// GOOD: "Six sponsor tools wired in one autonomous loop on live data."
// GOOD: "Real HTTP 402 paywall on Base Sepolia with per-query micropayments."

[2-3 concrete accomplishments. Quantify if possible.]

## What we learned

// WHY: One SHARP insight, not a list. This is the "memorable takeaway."
// GOOD: "Compliance for agents is a schema problem, not a model problem.
//   Structured verdicts outweigh natural-language reasoning."
// GOOD: "The agentic web needs a new substrate — agent-readable,
//   brand-verified, machine-monetizable."
// BAD: "We learned to work as a team."

[One insight that shows depth of thinking. Frame it as a thesis.]

## What's next for [PROJECT_NAME]

// WHY: Show the v2 vision. Judges want to see potential, not just a hack.
// WHY: Mention the business angle if there is one.

[2-3 bullet points:
- The v2 feature that would make this a real product
- The business model / go-to-market
- Technical improvements (multi-tenant, more providers, SDK)]

## Built with

// WHY: Tag EVERY sponsor tool. Judges filter by these tags for sponsor prizes.

[List all technologies. Include sponsor names explicitly.]
```

## Checklist before submitting

- [ ] Every section filled (no blanks)
- [ ] Concrete example in "What it does" (not abstract description)
- [ ] Sponsor tools named in "How we built it" table
- [ ] Challenges are specific and technical (not "time management")
- [ ] "What we learned" has ONE sharp insight
- [ ] All sponsor tools listed in "Built with" tags
- [ ] Demo video link included
- [ ] GitHub repo link included
