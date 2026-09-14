---
name: pricing-tiers
description: Use this skill whenever editing, adding, or restructuring pricing tiers, plans, packages, or pricing pages on any website. Triggers when the user mentions pricing, plans, tiers, packages, rates, or asks to add/edit/restructure any pricing section — even indirectly (e.g. "add a bullet to the Pro plan", "make the pricing consistent", "the enterprise tier needs work"). Also use when reviewing a pricing page for consistency or when creating a new pricing section from scratch.
---

# Pricing Tiers

A skill for building and maintaining pricing sections that are structurally uniform, outcome-oriented, and scannable. Pricing is where most B2B sites lose clarity — tiers drift apart over time as items get added or reworded in isolation. This skill prevents that drift.

## Before making changes

### Intake questions

Ask only what's relevant. Skip questions the user's instruction already answers.

1. **What's the buyer deciding?** "Is the buyer choosing between your tiers, or comparing you against competitors?" This determines whether the tiers should emphasise differentiation between each other (internal comparison) or value against alternatives (external comparison). Skip if the tiers already exist and the user is just editing copy.

2. **What does each tier's buyer look like?** "Who picks the starter vs the top tier — is it team size, budget, maturity, or something else?" This shapes the description and bullet language. Skip if the user is only fixing formatting or structure.

3. **Any references?** "Is there a pricing page you like the structure of?" Ask once. If no, proceed with the existing structure or the patterns below.

### Audit the current state

Before editing anything, read all tiers and note:
- How many tiers exist
- What sections each tier has (description, bullet lists, CTAs, badges)
- How many items are in each list
- Whether the structure is uniform or has drifted

Flag any inconsistencies before starting work: "The Growth tier has 5 bullets but the other two have 3. Want me to trim it to match, or expand the others?"

## Structural rules

### Uniform skeleton

Every tier in a pricing group should have the same sections in the same order. A typical structure:

```
[Badge/label]        — "Most popular", "Enterprise", "Starter"
[Tier name]          — the plan name
[Price]              — amount + billing period
[Description]        — 1-2 sentences: who this is for and what it does
[Primary list]       — "What you get" / "Includes" — the deliverables
[Secondary list]     — "How we work" / "Support" — the engagement model (optional)
[CTA]                — one button per tier
```

If one tier has a secondary list, all tiers should. If one has a badge, give the others a badge too (even if it's a category label rather than a callout like "Most popular").

### Item count parity

All tiers should have the same number of items in each list section, or within one item of each other. This prevents visual imbalance where one tier's card is twice the height of another.

- **Max 4 items per list** in a marketing/landing context. More than 4 means the items are too granular (combine them) or the tier is doing too much.
- If a tier genuinely has fewer deliverables, consider whether the items are at the right altitude. "Email infrastructure" is one item at a high altitude. "Warm sending domains", "DKIM/DMARC configured", "Deliverability monitoring" are three items at a lower altitude describing the same thing. Match the altitude across tiers.

### Price formatting

- Be consistent: if one tier shows `£250 / hour`, don't show another as `From £6,000/mo`. Pick one format and apply it everywhere.
- Qualifiers ("Starts from", "From", "Custom") go in the same position across tiers.
- Currency symbols, thousand separators, and billing period labels should match.

## Copy rules

### Every bullet is an outcome or a deliverable

The buyer scans the bullet list to answer: "What do I walk away with?" Not "What does this company do in the abstract?"

**Weak (category/feature):**
- "Outbound infrastructure and segmentation"
- "Strategic advisory services"
- "Dedicated account management"

**Strong (outcome/deliverable):**
- "Sending domains, sequences and audience segments ready to run"
- "Your go-to-market plan reviewed and stress-tested"
- "A named account manager who joins your weekly standup"

The test: can the buyer picture the thing they receive? If not, rewrite.

### Same type of item in the same list

Don't mix outcomes with process descriptions in one list. If the items naturally split into "what you get" and "how the engagement works", use two labelled lists rather than jumbling them.

### Parallel grammar

Items in the same list should follow the same grammatical pattern:
- All start with a noun: "A named account list...", "Sending domains...", "One asset..."
- Or all start with a past participle: "Your team trained...", "Playbooks written...", "Infrastructure stood up..."
- Don't alternate randomly between patterns.

### Descriptions differentiate

The 1-2 sentence description below the price should answer "who is this for?" and "what's the headline outcome?" It should make the buyer self-select into the right tier. Avoid making all three descriptions sound like different wordings of the same thing.

## Verification

After making changes, run these checks:

1. **Structure parity**: do all tiers have the same sections in the same order?
2. **Item count**: are bullet counts within 1 of each other across tiers?
3. **Grammar**: do items in each list follow the same pattern?
4. **Outcome test**: would a buyer know what they receive from each bullet?
5. **Price format**: are amounts, currency, and billing periods consistent?
6. **Visual weight**: will the cards render at roughly the same height?

Flag anything that fails and fix it before committing.
