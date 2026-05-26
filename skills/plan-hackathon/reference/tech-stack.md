# Tech Stack Recommendations for Hackathons

## Recommended stack (proven by winners)

| Layer | Recommendation | Why | Alternative |
|-------|---------------|-----|------------|
| **Framework** | Next.js (App Router) | One repo, one deploy, API + UI | Remix, SvelteKit |
| **Deploy** | Vercel | Auto-deploy from GitHub, free, fast | Netlify, Railway |
| **Language** | TypeScript | Shared types, team handoff, most SDKs | — |
| **AI/LLM** | Vercel AI SDK (`ai` + `@ai-sdk/*`) | `generateObject()` + Zod = typed JSON, streaming, provider-agnostic | Raw OpenAI/Anthropic SDK |
| **Validation** | Zod | Request/response schemas, works with AI SDK | — |
| **UI** | Tailwind CSS v4 | Fast, no config file needed in v4 | — |
| **Charts** | recharts | Simple, React-native | Chart.js |
| **Package manager** | pnpm or yarn | Fast, lockfile | npm |

## Why Vercel AI SDK over raw SDKs

// This was the single biggest technical advantage winners had over us.

```typescript
// WITH Vercel AI SDK (PolicyGuard):
const { object } = await generateObject({
  model: anthropic("claude-sonnet-4-20250514"),
  schema: verdictSchema,  // Zod schema
  prompt: "..."
});
// Returns typed, validated JSON. Zero parsing. Provider-swappable.

// WITHOUT (what we did — raw Gemini SDK):
const result = await chat.sendMessage(currentParts)
const candidate = result.response.candidates?.[0]
const responseParts = candidate.content?.parts  // might be undefined!
// Manual parsing, manual tool dispatch, manual type casting, duplicate handling...
```

Benefits:
- `generateObject()` + Zod = guaranteed typed JSON, no parsing errors
- `streamText()` for SSE streaming with React helpers built-in
- Provider-agnostic — swap `anthropic()` for `openai()` or `google()` in one line
- Tool calling is declarative with Zod schemas
- No debugging duplicate responses, missing parts, bad JSON escapes

## UI patterns that win

### 1. Dark theme (the #1 quick win)
```css
body { background: #0a0a0a; color: #e8e8e8; }
```
// WHY: Hides alignment issues, looks premium, reads well on projectors.
// Both winning projects used dark themes. Our white theme looked "Claude-generated."

### 2. One accent color
Pick ONE: emerald `#10b981`, blue `#3b82f6`, or brand color. Use it everywhere.
// WHY: Consistency. Multiple colors = visual noise.

### 3. Uppercase labels
```html
<span class="text-[11px] uppercase tracking-[0.1em] text-[#666]">MONITOR</span>
```
// WHY: Instant visual hierarchy. Screams "intentional design."

### 4. Monospace for data
```html
<code class="font-mono text-sm">decision: blocked</code>
```
// WHY: Makes API output look professional, not dumped.

### 5. Component-per-panel
```
components/
  MonitoringPanel.tsx
  CompetitiveLeaderboard.tsx
  VerificationPanel.tsx
  TracePanel.tsx
```
// WHY: Each feature is its own file. Easy to build independently, easy to reorder.

### 6. Phase progress bar
```typescript
type Phase = 'idle' | 'monitoring' | 'detecting' | 'publishing' | 'measuring' | 'done';
```
// WHY: Drives the entire UI state. Users see progress. Judges understand the flow.

### 7. Pre-filled defaults
```typescript
const DEFAULT_BRAND = 'Resend';
const DEFAULT_QUERIES = ['best transactional email API', ...];
```
// WHY: Zero typing needed during demo. One click to go.

### 8. No emoji in production UI
// WHY: Emoji icons look AI-generated/amateur. Use SVG icons or plain text labels.

### 9. Big numbers for metrics
```html
<div class="text-4xl font-black">3/5 → 5/5</div>
```
// WHY: Legible from the back of the room. Judges see the impact instantly.

## Architecture patterns

### Each sponsor = one file
```
lib/integrations/
  nimble.ts       # Monitor
  senso.ts        # Publish
  clickhouse.ts   # Measure
  datadog.ts      # Observe
  x402.ts         # Transact
```
// WHY: If one breaks, stub it without touching anything else.

### Pipeline/loop as single orchestrator
```
lib/agent/loop.ts   # Calls integrations in sequence
```
// WHY: One file to debug. Clear execution order.

### Demo mode as first-class feature
```typescript
if (process.env.DEMO_MODE === 'true') {
  return DEMO_FIXTURES[scenario];
}
```
// WHY: Guaranteed working demo. No API keys needed. Build this FIRST.

### Seed "before" data
Pre-populate the database with "before" state. Live run only produces "after."
// WHY: Faster demo, deterministic comparison, less live API risk.

## Anti-patterns to avoid

- **Raw LLM SDK** (Gemini, Anthropic direct) — use Vercel AI SDK wrapper
- **White/light theme** — exposes every misalignment
- **Emoji as icons** — looks AI-generated
- **LangChain / CrewAI** — too much boilerplate for a hackathon
- **Separate backend + frontend** — two deploys = two failure points
- **Python + JS split** — splits the team, doubles the setup
- **Auth/login** — nobody needs it at a hackathon
- **Mobile responsive** — judges use a projector
- **`tailwind.config.ts`** — use Tailwind v4 (CSS-first, no config file)
