# Devpost Submission Template

Write this at FEATURE FREEZE time, not at submission. Treat it as a deliverable.

## Guidelines (read before generating — do NOT copy these into the output)

- **Inspiration:** Ground the problem in reality with data/citation. "362 AI incidents in 2025" > "We wanted to build something cool."
- **What it does:** Walk through ONE concrete example step by step. Show the actual output schema. Don't describe abstractly.
- **How we built it:** Use a sponsor mapping table. Judges scan for sponsor names here.
- **Challenges:** Be specific and technical. "Nimble SERP API returned raw HTML, had to discover parsing path" > "Time management was hard."
- **Accomplishments:** What's NOVEL, not just "we finished." Quantify when possible.
- **What we learned:** ONE sharp insight framed as a thesis. "Compliance for agents is a schema problem, not a model problem."
- **What's next:** v2 business vision, not just "add more features."
- **Built with:** Tag EVERY sponsor tool explicitly.

### Examples of good vs bad

| Section | Good | Bad |
|---------|------|-----|
| Inspiration | "AI agents are taking real actions — $600M in x402 payments. No compliance layer exists." | "We wanted to build something cool with AI." |
| Challenges | "The LLM produced non-deterministic verdicts. We split into LLM proposal + deterministic rule engine." | "Time management was hard." |
| What we learned | "The agentic web needs a new substrate — agent-readable, brand-verified, machine-monetizable." | "We learned to work as a team." |

---

## Template (generate this — clean, no comments)

```markdown
## Inspiration

[1-2 paragraphs. State the real-world problem with a data point or citation.
Reference a trend that's getting worse. Make it feel urgent.]

## What it does

[Walk through ONE specific scenario step by step. Show the actual input and
output. Make judges see the product working in their mind.]

### Key output format
```json
[Paste your locked schema / output format here]
```

## How we built it

| Component | Tool | Role |
|-----------|------|------|
| [component] | **[Sponsor Tool]** | [what it does in the product] |

**Architecture:**
```
[Simple ASCII diagram or description of data flow]
```

**Stack:** [Framework], [Language], [LLM SDK], [Deploy target]

## Challenges we ran into

[2-3 specific, technical challenges with what you did about them.]

## Accomplishments that we're proud of

[2-3 concrete accomplishments. Quantify if possible.]

## What we learned

[One insight that shows depth of thinking. Frame it as a thesis.]

## What's next for [PROJECT_NAME]

[2-3 bullet points: v2 feature, business model, technical improvements.]

## Built with

[List all technologies. Include sponsor names explicitly.]
```

## Checklist before submitting

- [ ] Every section filled (no blanks)
- [ ] Concrete example in "What it does" (not abstract description)
- [ ] Sponsor tools named in "How we built it" table
- [ ] Challenges are specific and technical
- [ ] "What we learned" has ONE sharp insight
- [ ] All sponsor tools listed in "Built with" tags
- [ ] Demo video link included
- [ ] GitHub repo link included
