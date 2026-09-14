---
name: website-builder
description: Use this skill whenever editing, building, or modifying a website — HTML pages, CSS, copy, layout, pricing sections, landing pages, or UI components. Triggers on any website task including copy rewrites, visual/CSS changes, adding or restructuring sections, pricing tiers, CTAs, or page-wide consistency passes. Use it when the user mentions their website, landing page, homepage, or any section of a site they want changed — even if they don't say "website" explicitly (e.g. "rewrite the hero", "fix the pricing", "make the nav sticky").
---

# Website Builder

A skill for editing and building websites with intentional copy, consistent visual design, and uniform structure. It works by detecting what kind of edit you're making, asking targeted questions before starting, applying general best-practice rules, and reading any project-specific rules from CLAUDE.md.

## Detect the task type

Before doing anything, classify the task. Most edits fall into one of three categories, and some span multiple:

- **Copy**: rewriting text, headlines, descriptions, bullet points, CTAs, section ledes
- **Visual**: CSS changes, colours, spacing, typography, layout, responsive behaviour
- **Structural**: adding/removing sections, reorganising content, making elements uniform across the page

The intake questions, rules, and verification steps depend on which type applies.

## Intake questions

Ask these before starting work. Only ask the ones relevant to the task type — a CSS colour fix doesn't need audience questions, and a copy rewrite doesn't need a design reference. Keep it to 2-3 questions max per task, never more. If the answer is obvious from context (the user already said who the audience is, or you can see the design system in the CSS), skip the question.

### For copy tasks

1. **Audience + goal**: "Who reads this section, and what should they do after reading it?" Skip if the user's instruction already implies both (e.g. "rewrite pricing bullets so founders see outcomes" answers both).

2. **Reference or tone**: "Do you have an example of copy you like for this, or a tone to match?" Ask once. If no, make a confident call based on the rest of the page and move on.

### For visual tasks

1. **Design reference**: "Do you have a site or screenshot for the look you want?" Ask once. If no, look at the existing design tokens in the CSS (colours, fonts, spacing, border-radius) and make a call that's consistent with what's already there.

2. **Consistency scope**: "Are there similar elements elsewhere on the page that should match this?" Check yourself first — scan the HTML for repeated patterns (cards, tags, section headers, buttons). If you find inconsistency, flag it: "I noticed the eyebrow tags use three different colour treatments. Want me to unify them while I'm here?"

### For structural tasks

1. **Uniformity rules**: "Should all items in this group follow the same pattern?" (same number of bullets, same section types, same visual weight). Again, check yourself first — if you can see the pattern is already partially established, propose completing it rather than asking.

## General rules

These apply to every website edit regardless of project. Project-specific rules from CLAUDE.md take precedence when they conflict.

### Copy rules

Read `references/copy-rules.md` when working on any text content. The short version:

- **Outcomes over features.** Every bullet point and description should tell the reader what they walk away with, not what the product/service abstractly "is." "Outbound infrastructure" is a category. "Sending domains, sequences and segments ready to run" is a deliverable.
- **One idea per sentence.** Don't compress two insights into one balanced construction ("X doesn't Y. It Z."). State the point directly.
- **Active voice.** "We build your pipeline" not "Your pipeline is built by our team."
- **Concrete and specific.** Names, numbers, timeframes, and mechanisms beat abstractions. "60 to 90 days" beats "quickly."
- **No em dashes in short copy.** In bullets, CTAs, and single-sentence descriptions, use a period or comma instead. In longer paragraphs (3+ sentences), one em dash is acceptable if it genuinely helps the rhythm.
- **Uniform density.** If a section has multiple punchy one-liners in a row (balanced slogans, pithy contrasts, compressed wisdom), flag it. Two strong lines in close proximity is fine. Three or more creates a wall that reads as performed rather than genuine. Break them up with plain explanation.

### Visual rules

Read `references/visual-rules.md` when working on CSS or layout. The short version:

- **Check for an existing design system first.** Before writing any CSS, scan the file for custom properties (CSS variables), recurring class patterns, and established spacing/colour/typography tokens. New styles should use existing tokens, not introduce parallel values.
- **Consistency across siblings.** Cards in a row, list items, pricing tiers, tags — same treatment. If you're editing one, check that all siblings match. Same padding, same font size, same colour logic, same number of items where the structure implies uniformity.
- **Solid colours over gradients for small elements.** Tags, labels, badges, and eyebrow text should use solid colours. Gradients belong on large display elements (hero headlines, accent bars) where they have room to breathe.
- **Font weight carries meaning.** Bold (700+) for emphasis and labels. Regular (400) for body text. Don't mix arbitrarily within the same element type.
- **Test at both extremes.** Check that changes work on mobile (~400px) and wide desktop. If the element has text, make sure it doesn't orphan single words on narrow screens.

### Structural rules

- **Uniform structure across groups.** If there are three pricing tiers, they should have the same sections (description, bullet list, CTA), the same number of bullet items (or within one), and the same visual weight. Don't let one tier look sparse while another overflows.
- **Max 4 items per bullet list** in marketing/landing page context. If you have more, either the items are too granular (combine related ones) or the section is doing too much (split it).
- **Every section earns its place.** Before adding a new section, check if an existing one already covers the same ground. Before adding a bullet point, check if it duplicates a point already made elsewhere on the page.

## Project-specific rules

Before starting work, check for a `CLAUDE.md` (or `.claude/CLAUDE.md`) in the project root. If one exists, read it — it contains project-specific rules about brand voice, design tokens, formatting conventions, and editorial decisions that override the general rules above. Things like:

- Approved colour palette and when to use each colour
- Typography choices and type scale
- Specific words or phrases to avoid (or always use)
- Formatting conventions (how eyebrows should look, how pricing is displayed)
- Editorial decisions already made (light mode only, no dark theme, etc.)

If no CLAUDE.md exists and the project has enough established patterns to warrant one, suggest creating it after the current task.

## Workflow

1. **Classify** the task type (copy / visual / structural, or a combination)
2. **Ask** the relevant intake questions (2-3 max, skip what's obvious)
3. **Read** project CLAUDE.md if it exists
4. **Scan** the page for existing patterns, design tokens, and sibling elements
5. **Plan** the changes — state what you'll do in 1-2 sentences
6. **Execute** the changes
7. **Verify** consistency: after making changes, check that sibling elements still match and no new inconsistencies were introduced
8. **Commit and push** when the user confirms

## What this skill does NOT do

- It doesn't design from scratch. For new site builds or major redesigns, the `frontend-design` and `artifact-design` skills are better suited.
- It doesn't generate marketing strategy. It helps execute copy and design, not decide what to say.
- It doesn't replace project-specific skills. If a project has a dedicated deployment skill or CMS integration, defer to those.
