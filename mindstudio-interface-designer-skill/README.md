# MindStudio Interface Designer Skill

> **Original skill authored by [Sol](https://github.com/Sol1986) — [Sol1986/claude-skills](https://github.com/Sol1986/claude-skills/tree/main/mindstudio-interface-designer-skill).**
> This fork adds Interface Designer environment documentation, full bridge API examples (`useTemplateVariables`, `uploadFile`, `requestFile`), a Phase 13 Compile & Deploy section, and two new usage examples. All core skill logic, design philosophy, and authorship belong to Sol.

A master Claude Code skill for building production-grade React interfaces inside the [MindStudio Interface Designer](https://university.mindstudio.ai/docs/building-ai-agents/interface-designer).

Drop this skill into your Claude Code project via the MindStudio local tunnel and Claude will interview you before writing a single line of code, commit to a bold aesthetic direction, wire all inputs to your MindStudio workflow variables correctly, and deliver a component that compiles and hands off to the next block without breaking.

---

## What This Skill Does

- **Interviews first, builds second.** Claude asks focused discovery questions about purpose, audience, tone, brand, and variable names before any design or code work begins.
- **Maps inputs to MindStudio variables.** Every field gets a confirmed variable name. State keys match exactly. A comment block at the top of every component documents what the workflow receives.
- **Wires the bridge correctly.** Uses `submit()` and `useIsRunning()` from `./bridge` — the only correct way to advance a MindStudio workflow. Never uses `window.MindStudio.submit`.
- **Commits to a real aesthetic direction.** Chooses from 10 defined archetypes (Refined Minimal, Dark Technical, Glassmorphic, Luxury Editorial, etc.) and executes fully — no generic AI aesthetics.
- **Ships accessible, performant code.** WCAG AA contrast, keyboard navigation, `prefers-reduced-motion`, React performance patterns, and a 30-point pre-delivery checklist enforced on every build.

---

## Setup

### Requirements

- [MindStudio](https://www.mindstudio.ai) account with Interface Designer access
- Claude Code installed and running
- MindStudio local tunnel connected to Claude Code

### Installation

1. Clone or download this repository
2. Copy `SKILL.md` into your Claude Code skills directory (typically `.claude/skills/mindstudio-interface-designer-skill/SKILL.md`)
3. Open your MindStudio project and add a **User Input** block to your workflow
4. In the block's Optional Settings, switch **Interface** to **Custom (Beta)**
5. Click **Configure Interface** to open the Interface Designer
6. Use the **Chat Tab** to describe your interface in natural language, or the **Code Tab** to write directly
7. Click **Start** to spin up the dev environment and connect via the local tunnel to Claude Code
8. Iterate with vibe-coding or direct edits — check the **Live Preview** and **Logs Tab** as you go
9. When ready, click **Compile** to deploy the interface to your agent — this is the required final step

---

## How It Works

The skill follows a 12-phase process:

| Phase | What Happens |
|-------|-------------|
| 1. Discovery | Claude interviews you — one question at a time — about purpose, user, tone, brand, and variable names |
| 2. Aesthetic Direction | Claude commits to one of 10 archetypes and identifies the one unforgettable design moment |
| 3. Design System | Typography, color tokens, spacing, and z-index scale established before any code |
| 4. Component Architecture | MindStudio bridge wired correctly — `submit()`, `useIsRunning()`, variable state keys |
| 5. Visual Craft | Motion, backgrounds, depth, shadows, and glassmorphism patterns applied |
| 6. Interaction Design | Hover states, focus rings, loading states, form validation, touch targets |
| 7. Accessibility | ARIA labels, keyboard nav, contrast, `prefers-reduced-motion` |
| 8. React Performance | No waterfalls, no barrel imports, memoization, stable callbacks |
| 9. Light/Dark Mode | Both modes production-ready if theming is required |
| 10. Layout Patterns | Responsive layouts for forms, wizards, and dashboards |
| 11. Industry Guidance | SaaS, healthcare, fintech, beauty, creative — context-specific design direction |
| 12. Pre-Delivery Checklist | 30-point checklist covering visual, interaction, layout, accessibility, performance, and MindStudio compatibility |
| 13. Compile & Deploy | Review in Live Preview, check Logs Tab for errors, click Compile to build and deploy the interface |

---

## The Interface Designer Environment

The Interface Designer has three tabs and two key controls you need to know:

- **Chat Tab** — describe your UI in natural language; the AI generates it for you (vibe-coding)
- **Code Tab** — edit the generated React code directly, install npm packages, add custom logic
- **Logs Tab** — real-time debug feed; check here if anything goes wrong
- **Compile** — the final required step; deploys your interface to the agent (bottom dev controls)
- **Live Preview** — instant rendering of changes as you type or edit

> **Always click Compile** when you're done. An interface that hasn't been compiled isn't deployed.

---

## The MindStudio Bridge

The most critical piece. Every component this skill generates imports from `./bridge` — MindStudio's runtime connector between your React UI and the workflow engine.

```tsx
import { submit, useIsRunning } from './bridge'

export default function Interface() {
  const isRunning = useIsRunning()

  const handleSubmit = () => {
    submit({ topic, tone, keywords }) // advances to next workflow block
  }

  return (
    <button onClick={handleSubmit} disabled={isRunning}>
      {isRunning ? 'Processing...' : 'Submit'}
    </button>
  )
}
```

The skill enforces that `window.MindStudio.submit` and manual `setTimeout` loading patterns are never used — both fail silently in production.

---

## Aesthetic Archetypes

| Archetype | Best For |
|-----------|----------|
| Refined Minimal | SaaS, B2B, professional tools |
| Luxury Editorial | Portfolios, premium services |
| Dark Technical | Developer tools, AI products, fintech |
| Warm & Approachable | Consumer apps, health, education |
| Bold Brutalist | Fashion, art, provocative brands |
| Glassmorphic | Modern SaaS, dashboards |
| Bento Grid | Dashboards, feature showcases |
| Retro-Futuristic | AI tools, tech demos |
| Claymorphic | Consumer apps, games |
| Organic/Natural | Wellness, food, sustainability |

---

## Files

| File | Purpose |
|------|---------|
| `SKILL.md` | The skill itself — loaded by Claude Code |
| `README.md` | This file |
| `EXAMPLES.md` | Real prompt examples with expected variable output |
| `skill.json` | Skill metadata for registries and tooling |

---

## Attribution

This skill was originally created by **[Sol](https://github.com/Sol1986)** and published at [Sol1986/claude-skills](https://github.com/Sol1986/claude-skills/tree/main/mindstudio-interface-designer-skill) under the MIT License.

This fork extends the original with Interface Designer environment documentation and bridge API examples. All credit for the core skill design, 12-phase methodology, aesthetic archetypes, and MindStudio bridge integration goes to the original author.

If you find this skill useful, consider starring the [original repository](https://github.com/Sol1986/claude-skills).

## License

MIT
