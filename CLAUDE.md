# Expedite GTM — Website Project Rules

## What this is

Expedite GTM's marketing website. Single-page site (`index.html`), deployed via GitHub Pages from the `main` branch root. Custom domain: `expeditegtm.com`.

## Design system

- **Light mode only.** `data-theme="light"` is hardcoded on `<html>`. No dark mode CSS exists. Don't add dark mode support.
- **Typeface:** Plus Jakarta Sans (Google Fonts), IBM Plex Mono for monospace/eyebrow labels.
- **Colour tokens** are defined as CSS custom properties in `:root`. Use them — don't hardcode hex values.
  - `--blue-600` / `--cyan-500` — primary accent pair, used in gradients
  - `--accent` / `--accent-deep` — semantic accent (maps to blue-600)
  - `--accent-tint` — light tinted background for tags
  - `--ink` / `--ink-soft` / `--ink-faint` — text hierarchy
  - `--bg` / `--bg-alt` — background surfaces
- **Gradient text** uses `background: linear-gradient(...); -webkit-background-clip: text; background-clip: text; -webkit-text-fill-color: transparent`. Used on `.hl-mark` headlines and `.feat-tier .amt` price display. Don't add gradient text to small elements.
- **Eyebrow tags** (`.eyebrow`): solid colours only, bold (700), no gradients. Blue on light sections, white on dark sections (`#cost`, CTA).
- **Transparent accent blends** use `color-mix(in srgb, var(--accent) N%, transparent)`.

## Copy voice

- Direct, specific, no fluff. Write as a practitioner talking to another practitioner (founders and marketing leaders at B2B SaaS companies).
- No em dashes in short copy (bullets, tags, single-sentence descriptions). Periods or commas instead.
- Outcome-oriented: bullets describe what the client walks away with, not abstract capabilities.
- Slogan density ceiling: max two punchy compressed lines in close proximity. Follow each with plain explanation.
- These three lines are approved and protected — don't rewrite them:
  1. "AI in the engine, senior judgement at the wheel."
  2. "Fewer channels, run harder."
  3. "Every quarter without a motion is a quarter your competitors have one."

## Pricing tiers

- Three tiers: GTM Advisory, ABM Programme, Fractional GTM Build.
- Uniform structure: each tier has "What you get" (4 items) + "How we work" (3 items).
- Keep this structure when editing pricing. If adding an item, remove another to stay at 4/3.

## People

- **Kartik Krishnan** — Founder. Sets strategy. 12 years enterprise GTM (fintech, regtech, AI SaaS).
- **Rahul** — Fractional Growth Marketer. Generalist. Not a founder.

## Deployment

Push to `main` to deploy. GitHub Pages serves from root. `CNAME` file must stay in root.
