# Visual Rules for Website Editing

These rules apply when writing or modifying CSS, adjusting layout, changing colours, or doing any visual/styling work on a website.

## Existing design system comes first

Before writing any new CSS:

1. **Scan for CSS custom properties** (variables). Most sites define a palette, spacing scale, and typography tokens in `:root`. Use these instead of hardcoding values.
2. **Check for recurring class patterns.** If there's a `.btn` with variants, a `.card` with established padding, or a `.section` with consistent spacing, follow the existing pattern.
3. **Look for a design tokens file** or a `CLAUDE.md` with colour/type specifications. If one exists, all visual changes derive from it.

When adding new styles, express them through existing tokens. Only add new tokens when the design genuinely needs a value that doesn't exist yet.

## Consistency across siblings

The most common visual bug on iteratively-edited sites is sibling inconsistency — similar elements that have drifted apart over multiple editing sessions.

**After every visual change, check:**
- Do all cards in a row have the same padding, border-radius, and shadow?
- Do all tags/badges/eyebrows use the same colour logic?
- Do all section headers follow the same pattern (eyebrow, heading, lede)?
- Do all buttons of the same type share the same size and style?
- Do all pricing tiers have the same visual weight and structure?

If you find inconsistency, flag it. "I'm fixing the hero tag colour. I also noticed the pricing section tags use a different treatment — want me to unify those too?"

## Colour decisions

- **Solid colours for small elements.** Tags, labels, badges, and inline text accents should use solid colours. Gradients on small elements read as decoration, not information.
- **Gradients for display elements.** Hero headlines, accent bars, and large decorative elements can use gradients when they serve a purpose (drawing the eye, creating depth).
- **Neutrals should look chosen.** Pure `#999` or `#ccc` grey reads as a default. A grey with a slight hue bias toward the page's accent colour reads as intentional. Pure white and near-black are fine grounds when they suit the design.
- **Transparent overlays via `color-mix`.** For tinted backgrounds, use `color-mix(in srgb, var(--accent) 10%, transparent)` rather than hardcoded rgba values. This keeps the tint tied to the accent colour.

## Typography

- **Font weight carries meaning.** 700+ for emphasis, labels, and headings. 400-500 for body text. Don't use bold for everything — it flattens the hierarchy.
- **Consistent type scale.** Check existing font-size values and stick to the established steps. If the site uses 14px body, 18px subheads, and 28px headings, don't introduce a 22px element without reason.
- **Uppercase labels need letter-spacing.** Any `text-transform: uppercase` text should have `letter-spacing: 0.05em` or more to stay readable.
- **Line length for readability.** Running text should be roughly 55-75 characters wide. Use `max-width` on text containers, not on the page itself.

## Layout

- **Flex and grid with `gap`, not margins.** Sibling spacing should come from the parent's `gap` property, not per-element margins that can collapse or double.
- **Wide content scrolls in its own container.** Tables, code blocks, and overflow-prone elements get `overflow-x: auto` on their own wrapper so the page body never scrolls horizontally.
- **Test narrow and wide.** After any layout change, check at ~400px (phone) and ~1200px+ (desktop). Watch for orphaned words, clipped text, and elements that overflow their container.
- **Height is set by content.** Don't use fixed heights on text containers. Let content determine height, and use `min-height` only when an element must meet a visual threshold (like a hero needing enough space for its background treatment).

## Specificity and cascade

- **Watch for selector conflicts.** A `.section` class fighting a `.cta` class over padding is a common bug in iteratively-edited CSS. After adding a new rule, check that it doesn't override or get overridden by an existing rule on the same element.
- **Same specificity, last wins.** If two rules at the same specificity target the same element, the one that appears later in the file wins. Be aware of rule order.
- **Avoid `!important` as a fix.** If a style isn't applying, find the conflicting rule and fix the specificity, don't force it with `!important`.
