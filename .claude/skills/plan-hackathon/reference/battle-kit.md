# BATTLE_KIT.md Template for Hackathons

Generate this customized. All times are formulas, not fixed values.

```markdown
# BATTLE_KIT.md — your day, on one page

Build window **[START] → [END]**. Submission **[SUBMISSION]**. [TEAM_SIZE]. [DEMO_LENGTH] demo.
Keep this open on your phone.

## Timeline

| Time | Phase | Task | Done = |
|------|-------|------|--------|
| [START - 1h] | Setup | Arrive, power, WiFi. Verify API keys. Deploy blank app. | Every key in `.env.local`, blank deploy works |
| [START] → [+30m] | **1 Scaffold** | Framework + deploy, integration stubs, `.env.example`. | Blank app live on deploy target |
| [+30m] → [HALFWAY] | **2 Core loop** | The autonomous loop end-to-end, ugly is fine. | One full run logs in console |
| [HALFWAY] → [+30m] | LUNCH | Eat. Solo = a bad call late sinks you; fuel up. | Brain still works |
| [HALFWAY+30m] → [FREEZE-1h] | **3 UI/Dashboard** | Render results, one-click trigger, progress indicator. | Click once → result renders |
| [FREEZE-1h] → [FREEZE] | **4 Polish** | Sponsor proof panels, loading states, seed data. Dark theme. | Demo looks intentional |
| [FREEZE] → [SUBMISSION] | **5 Demo prep** | **FEATURE FREEZE.** Seed clean run, rehearse 3x, record backup, push repo, README, submit. | Submitted with 10 min to spare |

**Formulas:**
- HALFWAY = START + (BUILD_WINDOW / 2)
- FREEZE = SUBMISSION - 2 hours
- SUBMIT_TARGET = SUBMISSION - 10 min

**Halfway checkpoint:** Is core loop running end-to-end? If NO → cut [lowest-priority sponsors], simplify to [minimum sponsor count] only.

## Pitch script ([DEMO_LENGTH])

// WHY: Pre-written > improvised. Time every section.

**[HOOK · ~15s]**
"[One provocative statement about the problem. Cite a stat if possible.]"

**[PROBLEM · ~20s]**
"[What's broken. Why existing solutions don't fix it. The gap.]"

**[SOLUTION · ~15s]**
"[PROJECT_NAME] is [what]. It [key differentiator]. Watch."

**[DEMO · ~60-90s — narrate while it runs]**
- *Click [trigger].* "One click. No more input from me."
- "[Narrate each step as it happens. Point to sponsor tools by name.]"
- "[Point out the metric/result that proves it worked.]"
- "[Show observability/proof panel if built.]"

**[SO WHAT · ~20s]**
"[Why this matters. Business angle. What's the v2.]"

**[CLOSER · ~10s]**
"[Tagline. Memorable one-liner.]"

## Demo survival rules

1. **Pre-load everything.** App open, warmed up, demo data pre-entered. Zero avoidable loading.
2. **Realistic data only.** Plausible brand/scenario, real-looking numbers. Never "Test Brand A."
3. **Backup recording.** Recorded at [FREEZE + 15m]. If live breaks: switch in 5s, no apology.
4. **Never apologize mid-demo.** Narrate past glitches: "and the analysis appears — there it is."
5. **Browser zoom ≥125%, dark mode.** Judges sit far back.
6. **Time it.** [DEMO_LENGTH] slot → rehearse to [DEMO_LENGTH - 30s]. Leave room for fumbles.

## Anticipated judge questions

| They ask | You answer |
|----------|-----------|
| "How autonomous is it?" | "[Describe what happens after ONE trigger without human input.]" |
| "Did you build all this today?" | "Yes — fresh repo. We pre-configured API keys to maximize build time." |
| "What's the business model?" | "[One sentence. v2 vision.]" |
| "What's the limitation?" | "[Honest answer. Frame as v2 opportunity.]" |
| "How does [sponsor tool] fit?" | "[Specific role in the product, not 'we also used it.']" |

## Pre-hackathon checklist (night before / morning of)

// WHY: GhostWriter pre-wrote CLAUDE.md, SPEC.md, BATTLE_KIT.md before the hackathon started.
// WHY: PolicyGuard pre-configured Senso org, ingested demo data, deployed placeholder site.

- [ ] CLAUDE.md, SPEC.md, BATTLE_KIT.md written and in repo
- [ ] All API keys obtained and verified working (`curl` test each)
- [ ] Repo created, blank app deployed to Vercel (prove the pipeline)
- [ ] `.env.example` with every key listed
- [ ] Demo scenario decided — brand/input values chosen, NOT "we'll figure it out"
- [ ] Team roles assigned with specific file ownership (if team)
- [ ] Sponsor docs read — know the API, ran their hello-world example
- [ ] Demo mode fixture data sketched out (what the deterministic response looks like)

## Commit strategy

// WHY: GhostWriter committed every phase. Judges can see the build progression.
// WHY: "Working code only on main" — never push broken code.

Commit after each phase with a clear message:
- `phase 1: scaffold + deploy + integration stubs`
- `phase 2: core agent loop end-to-end`
- `phase 3: dashboard UI + one-click trigger`
- `phase 4: polish + sponsor proof panels`
- `phase 5: README + demo prep`

## Demo harness command

// WHY: PolicyGuard had `npm run demo` that ran 3 scenarios deterministically.
// WHY: A reproducible demo command = guaranteed working presentation.

Add to `package.json`:
```json
"scripts": {
  "demo": "DEMO_MODE=true tsx scripts/demo.ts"
}
```
The demo script should trigger your agent loop with pre-configured inputs
and print/render the result. Same output every time.

## Devpost submission

Write devpost at [FREEZE] time. See `reference/devpost.md` for the full template.

## Submission checklist

- [ ] Public GitHub repo pushed, README lists sponsor tools used
- [ ] [DEMO_LENGTH] demo recording uploaded
- [ ] All Devpost fields filled (see `reference/devpost.md`)
- [ ] Sponsor tracks explicitly called out in submission
- [ ] Submitted by [SUBMIT_TARGET]
```
