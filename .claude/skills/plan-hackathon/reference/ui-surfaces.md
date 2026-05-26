# UI Surfaces & Visual Design Guide

## Guidelines (read before generating — do NOT copy these into the output)

### The core rule: if it's not visible, don't build it

Every feature must connect to something a judge sees on screen during the 3-min demo.
Backend logic that doesn't surface visually should be dropped or stubbed. The demo IS
the product at a hackathon.

### What winning UIs had in common

Both PolicyGuard and GhostWriter used a **single-page dashboard** with:
1. A trigger section (input form + one button)
2. A progress indicator (phase bar or status line)
3. Multiple result panels that appear after the agent runs
4. Each sponsor tool had its own visible panel

GhostWriter had 12 distinct panels. PolicyGuard had streaming verdict cards.
Neither had multiple pages or navigation — everything was one scrollable view.

### Design system (from winners)

- **Dark theme:** `bg-zinc-950 text-zinc-50` (GhostWriter) or dark with green accents (PolicyGuard)
- **One accent color:** emerald `#10b981` (GhostWriter), green for ALLOWED / red for BLOCKED (PolicyGuard)
- **Typography:** monospace for data/labels (`font-mono`), sans-serif for prose, uppercase tracking for section labels
- **Borders:** `border-zinc-800` (subtle, dark), rounded corners `rounded-xl`
- **Cards:** `bg-zinc-900/40 backdrop-blur-sm border border-zinc-800 rounded-xl p-5`
- **Subtle background:** grid pattern or gradient glow behind hero section
- **Status indicators:** pulsing dot for "live", colored badges for verdicts
- **No emoji** — text labels, SVG icons, or colored dots only
- **Browser zoom 125%+** for demo — design for legibility at distance

### Panel architecture

Each panel follows a consistent structure:
```
Section number + label (uppercase, colored)
Title (large, bold)
Description (1 line, muted)
Content (the actual data/visualization)
```

### Surfaces to plan

For each hackathon project, define these surfaces BEFORE building:

1. **Trigger panel** — input form + one big button. Pre-filled defaults.
2. **Progress indicator** — phase bar showing where the agent is.
3. **One panel per sponsor** — each sponsor tool gets a visible card proving it was used.
4. **Hero metric** — the single most impressive number/comparison (big, bold, center).
5. **Agent trace** — expandable view of what the agent did (for technical judges).
6. **Optional: before/after** — visual comparison showing the agent's impact.

---

## Surface planning template (generate this for the user)

When generating battle docs, include a UI surface map like this:

```markdown
## UI Surface Map

All features must connect to a visible surface. If it doesn't appear here, don't build it.

### Page layout (single page, scrollable)

1. **Header**
   - Project name + status badge (live/demo)
   - One-line description with sponsor names highlighted

2. **Trigger Section**
   - Input: [what the user enters — pre-filled for demo]
   - Button: "[Action verb] Agent" (one click starts everything)
   - Status: phase progress bar → [PHASE1] → [PHASE2] → [PHASE3] → done

3. **Hero Metric**
   - The wow number: "[Before] → [After]" in large bold text
   - Must be visible from back of room

4. **[Sponsor A] Panel** — proves sponsor tool was used
   - Shows: [what data from this sponsor]
   - Visual: [table/chart/card]

5. **[Sponsor B] Panel** — proves sponsor tool was used
   - Shows: [what data from this sponsor]
   - Visual: [table/chart/card]

6. **[Sponsor C] Panel** — proves sponsor tool was used
   - Shows: [what data from this sponsor]
   - Visual: [table/chart/card]

7. **Agent Trace Panel** — proves it's a real agent, not a script
   - Expandable steps with timing
   - Links to observability dashboard if available

8. **[Additional panels as needed]**
```

### Feature-to-surface mapping

Every backend feature must map to a surface:

| Feature | Visible surface | If no surface → |
|---------|----------------|-----------------|
| [feature] | [which panel shows it] | Drop it |

If a feature has no entry in the "Visible surface" column, it should NOT be built.

## Component patterns (from GhostWriter — copy these)

### Phase progress bar
```typescript
type Phase = 'idle' | 'step1' | 'step2' | 'step3' | 'done' | 'error';

const PHASE_ORDER: Phase[] = ['step1', 'step2', 'step3'];

// Render as horizontal bar with filled segments
```

### Section wrapper (consistent for all panels)
```tsx
<section className="border border-zinc-800 rounded-xl p-5 bg-zinc-900/40 space-y-3">
  <div className="flex items-baseline gap-3">
    <span className="text-xs font-mono font-semibold text-emerald-400 uppercase tracking-wider">
      01 · SECTION LABEL
    </span>
  </div>
  <h3 className="text-xl font-semibold text-zinc-100">Section Title</h3>
  <p className="text-sm text-zinc-400">One-line description.</p>
  {/* Content */}
</section>
```

### Hero metric (before → after)
```tsx
<div className="flex items-center gap-6">
  <div>
    <span className="text-xs uppercase text-zinc-500">Before</span>
    <span className="text-5xl font-bold text-zinc-400">3/5</span>
  </div>
  <span className="text-2xl text-zinc-600">→</span>
  <div>
    <span className="text-xs uppercase text-emerald-400">After</span>
    <span className="text-5xl font-bold text-emerald-400">5/5</span>
  </div>
</div>
```

### Sponsor proof panel
```tsx
<section className="border border-zinc-800 rounded-xl p-5 bg-zinc-900/40">
  <div className="flex items-center gap-2 mb-3">
    <img src="/sponsor-logo.png" className="h-5" />
    <span className="text-xs font-mono text-zinc-500 uppercase">Sponsor Name</span>
  </div>
  {/* Sponsor-specific data visualization */}
</section>
```

### Pre-filled input form
```tsx
const DEFAULT_BRAND = 'Resend';
const DEFAULT_QUERIES = ['best transactional email API', ...];
// Zero typing needed during demo. One click to go.
```
