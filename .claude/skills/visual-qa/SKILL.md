---
name: visual-qa
description: Use this skill after making any CSS, styling, or layout changes to a website. Run it as a post-edit check to catch visual inconsistencies, sibling drift, cascade conflicts, and responsive issues before committing. Also use when the user asks to audit, review, or clean up the visual consistency of a page — or when you notice styling issues during other work. Triggers on phrases like "check the styling", "make it consistent", "audit the CSS", "something looks off", or after any visual/CSS edit you just made.
---

# Visual QA

A post-edit checklist for catching visual bugs that slip through when websites are edited iteratively over multiple sessions. Each session's edits make sense in isolation, but over time sibling elements drift apart, cascade conflicts accumulate, and formatting decisions lose consistency.

Run this checklist after any CSS or layout change, or when asked to audit visual consistency.

## When to run

- **After every CSS/styling edit.** Even a one-line colour change can create inconsistency with sibling elements.
- **When the user says something looks off.** Run the full checklist rather than guessing what's wrong.
- **Before committing visual changes.** Catch problems before they ship.
- **On request.** When asked to audit, review, or clean up styling.

## The checklist

Work through each category. Only flag actual problems — don't report passing checks.

### 1. Sibling consistency

Find all groups of repeated elements on the page:
- Cards in a row (pricing tiers, feature cards, team members)
- Tags, badges, labels, eyebrow text
- Section headers (eyebrow + heading + lede patterns)
- Buttons of the same type/variant
- List items within the same list
- Navigation items

For each group, verify:
- **Same padding and margin** — measure by reading the CSS, not by eyeballing
- **Same font size, weight, and colour logic** — all tags should use the same treatment, not three different ones
- **Same border, radius, and shadow** — if one card has `border-radius: 12px` and another has `8px`, that's a bug
- **Same number of child elements** where structure implies parity (e.g. pricing tier bullet counts)
- **Same colour treatment** — if tags are blue on light backgrounds, they should all be the same blue, not three shades

### 2. Colour consistency

Scan the CSS for colour values and check:
- **Hardcoded values that should be tokens.** If the page defines `--accent: #1F54DD` but a rule uses `color: #1F54DD` directly, it should reference the variable.
- **Near-duplicate colours.** `#1F54DD` and `#1E53DC` are probably meant to be the same colour. Flag them.
- **Gradients on small elements.** Tags, labels, badges, and inline text should use solid colours. Gradients belong on display-size elements (heroes, accent bars).
- **Contrast.** Light text on light backgrounds, or dark text on dark backgrounds. Pay special attention to text on tinted/coloured backgrounds.

### 3. Typography consistency

- **Font weight discipline.** Are headings consistently bold? Are body paragraphs consistently regular? Is there a heading somewhere using `font-weight: 400` while its siblings use `700`?
- **Uppercase without letter-spacing.** Any `text-transform: uppercase` should have `letter-spacing` of at least `0.05em`. Without it, uppercase text looks cramped.
- **Type scale coherence.** List the font sizes in use and check they follow a consistent scale. A page using 14, 16, 18, 24, 32 has a clear scale. A page using 14, 15, 17, 19, 23 has drifted.
- **Line height.** Body text should be 1.5-1.7. Headings should be 1.1-1.3. Values outside these ranges are worth flagging.

### 4. Spacing and layout

- **Gap vs margin consistency.** Sibling spacing should come from the parent's `gap`, not per-element margins. Mixed approaches in the same layout are a bug.
- **Section spacing rhythm.** Check that vertical spacing between major sections is consistent. If most sections have `padding: 80px 0` but one has `60px`, that's drift.
- **Orphaned words.** Short last lines (1-2 words) at narrow widths, especially in headlines. Fix with `text-wrap: balance` on headings or by adjusting `max-width`.
- **Overflow.** Check for elements that might overflow their container at narrow widths: long words, fixed-width elements, images without `max-width: 100%`.

### 5. Cascade conflicts

- **Specificity fights.** Two rules targeting the same element with different values for the same property. The more specific one wins, but the less specific one was probably intended to apply somewhere. Flag ambiguous cases.
- **Order-dependent rules.** Two rules at the same specificity where the later one silently overrides the earlier. This often happens with section-specific overrides (`.pricing .btn` vs `.hero .btn`).
- **`!important` usage.** Any `!important` is a sign of a specificity problem. Flag it and suggest the proper fix.
- **Inline styles.** Styles applied directly on HTML elements (`style="..."`) that override class-based styling. These are hard to maintain and easy to forget.

### 6. Responsive checks

- **Mobile width (~400px).** Would any element overflow, clip, or become unreadable?
- **Text containers.** Is there a `max-width` on running text to keep line length under ~75 characters on wide screens?
- **Flexible images.** Do all images have `max-width: 100%`?
- **Horizontal scroll.** Does any element cause the page body to scroll horizontally? Wide elements should be in `overflow-x: auto` containers.

## Reporting

After running the checklist, report findings grouped by severity:

1. **Breaks** — things that are visually broken (text unreadable, elements overlapping, layout collapsing on mobile)
2. **Inconsistencies** — sibling drift, mixed colour treatments, mismatched spacing
3. **Cleanup** — minor issues that don't break anything but reduce polish (hardcoded colours, unnecessary `!important`, imprecise type scale)

For each finding: name the element, quote the relevant CSS, and state the fix. Don't just describe the problem — propose the solution.

If there are no findings, say so. Don't pad the report with passing checks.
