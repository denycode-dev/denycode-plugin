# Practical UI Design Guidelines

A logic-driven checklist for designing or reviewing an interface, synthesized from a UI design book's "Fundamentals," "Layout and spacing," and "Typography" chapters, plus four UX Planet articles on logic-driven UI tips, alignment, and button design (see Sources at the end). Everything below is organized by topic rather than by source, since most of these rules show up — and reinforce each other — across every source.

Use this as a checklist, not a narrative: when reviewing a screen, work down the list roughly in order. Early fixes (spacing/grouping, hierarchy) tend to make later ones (typography, alignment) obvious.

## Table of contents
1. Interaction cost
2. Spacing and grouping
3. Visual hierarchy
4. Color and contrast
5. Buttons
6. Typography
7. Alignment
8. Consistency and simplicity
9. Two worked examples
10. Sources

---

## 1. Interaction cost

Interaction cost is the total physical and mental effort someone spends to complete a task: looking, scrolling, reading, clicking, waiting, typing, thinking, remembering. It's measurable, which means it's fixable. Three of the most effective levers:

- **Keep related actions physically close.** A closer, larger target is faster to hit (Fitts's Law) — keep an action next to the element it acts on, and give interactive elements at least a 48×48pt target.
- **Reduce distractions.** Animated banners, pop-ups, and decorative visuals compete for attention with the task at hand.
- **Minimize choice.** More options, or more complex options, slow down decisions (Hick's Law). Surface a smaller set of recommended or popular choices instead of showing everything at once — e.g. replace a quantity dropdown (open → scroll → click) with a stepper (single click or type), and move the primary action physically next to it.

## 2. Spacing and grouping

Breaking information into smaller, related groups is one of the biggest levers for making an interface easy to scan and remember. There are four ways to signal that elements belong together, and they can be combined:

1. **Common region (containers).** Elements inside the same border, shadow, or background are read as a group. This is the *strongest* grouping cue — but also the easiest to overuse into visual clutter. Reach for it when other cues aren't enough, not as a default.
2. **Proximity (spacing).** Elements placed close together read as related; more space signals "not related." This alone is often enough to replace a container, producing a simpler, less boxy design.
3. **Similarity.** Elements that share size, shape, or color are grouped by the eye even without a container or extra spacing — e.g. nav links that all look alike are read as one group.
4. **Continuity.** Elements aligned in a continuous line (a list, a row of tabs) are read as related; breaking that alignment signals the end of a group or highlights one item.

**A spacing scale beats ad hoc pixel values.** Rather than nudging spacing one pixel at a time, define a small set of "t-shirt sized" spacing tokens on a common increment — an 8pt grid is the most common (8 / 16 / 24 / 32 / 48pt, growing non-linearly like a type scale), or 4pt increments for denser UI. Apply the smallest spacing to the most tightly related (innermost) elements and grow the spacing as you move to less related (outer) groups. A design that only ever uses the two smallest spacing values, regardless of how related elements actually are, will read as cluttered and squashed even if every individual element looks fine.

**Removing a container is often an improvement, not a compromise** — if elements are already grouped by proximity, similarity, and continuity, the container is redundant and just adds visual weight. This is especially true for lists/tables of repeated items (e.g. a playlist or article list): once rows share spacing, style, and alignment, the outer container can go.

**Watch for elements that look grouped but aren't** (or vice versa). Two visually similar things can accidentally read as related if they're close together — e.g. an author's byline sitting close to the article *below* it rather than the one it belongs to. When in doubt, add a container or asymmetric spacing to disambiguate.

## 3. Visual hierarchy

Not everything on a screen deserves the same visual weight. Order elements by actual importance using size, color, contrast, spacing, position, and depth so the most important thing is the most visually prominent thing.

**The Squint Test**: squint at the design (or blur it, or view it from across the room). You should still be able to tell what the primary action is and roughly what the screen is for. If several elements compete at similar visual weight, or the actual primary action doesn't stand out, the hierarchy isn't done yet.

A common failure mode: a large block of body text (like a long description) ends up more visually prominent than the primary button just because it's bigger and darker, even though the button is more important to the user's task. Fixing hierarchy often means simultaneously *increasing* the prominence of the primary action (higher contrast fill, bold weight) and *decreasing* the prominence of secondary content (lighter grey, smaller size) — see Typography below for the specific levers.

## 4. Color and contrast

- **UI elements (buttons, form fields, icons, borders that indicate shape) need at least 3:1 contrast** against their background so people with low vision can perceive them as interactive.
- **Text needs at least 4.5:1 contrast** at normal sizes (18px and under); large text (bold ≥18px, or regular ≥24px) can drop to 3:1.
- **Never rely on color alone** to convey selection, state, or meaning — some people are color blind and won't perceive the difference. Pair a color change with a second cue: an underline for a selected tab, a filled icon for a selected nav item, an underline for a link, a border or shape change for a selected state.
- **Use color purposefully, not decoratively.** Start with black/white/greyscale and add color only where it conveys meaning — most commonly, apply the brand color to interactive elements (links, buttons) so people learn "colored = clickable." Avoid putting the brand color on non-interactive elements (a heading, a star rating) purely for style, since it makes static content look clickable.
- **Avoid pure black text on white.** The maximum-possible contrast (21:1) between true black and white causes more eye strain than necessary; a dark grey is easier to read for extended text while still clearing the 4.5:1 minimum.
- Free tools worth using while designing: a WCAG contrast checker (e.g. WebAIM's) and a contrast-checking Figma plugin.

## 5. Buttons

**Use three button weights** — primary, secondary, tertiary — to communicate the relative importance of actions, and add larger/smaller sizes only if the interface's complexity calls for it.

**A safe, accessible default styling:**
- Primary: solid fill, high contrast against the background.
- Secondary: outline/border only, no fill, with a border that clears 3:1 contrast.
- Tertiary: styled as underlined text (this is fine even though it looks like a link — code it semantically as a button if it performs an action rather than navigating).

**Use exactly one primary button per screen.** If no single action is clearly the most important, downgrade every option to secondary/tertiary rather than using multiple primary buttons — multiple primaries compete for attention and blur the decision.

**Common button mistakes to check for** (each of these has shown up repeatedly in real products):
- A secondary button's fill or border contrast falls below 3:1 — it reads as decorative text, not a button.
- A light-grey secondary button that could be mistaken for a *disabled* button.
- Primary and secondary buttons styled almost identically, so the only way to tell them apart is hue — inaccessible to colorblind users and confusing for everyone else.
- A tertiary "button" that is plain colored text with no other affordance (no underline, no icon) — indistinguishable from a link or from non-interactive colored text for colorblind users.
- Buttons that function identically but look different (or vice versa) with no reason — e.g. a round primary button next to rectangular secondary/tertiary buttons.

**Sizing and spacing:** buttons (and other tap targets) should be at least 48×48pt — slightly larger than the WCAG-recommended 44×44pt minimum — and adjacent buttons should have at least 8pt (ideally 16pt) of separation so people don't mis-tap the wrong one. Widen buttons to fill available space rather than leaving them small when there's room.

**Links vs. buttons:** the old convention that links "go somewhere" and buttons "perform an action" is largely gone from how people actually perceive interfaces today — a call-to-action styled as a button (rather than plain underlined text) is usually more prominent and clearer, even if it technically navigates to another page. What matters for accessibility is that it's *coded* as a link or button correctly under the hood, regardless of how it's styled.

## 6. Typography

- **One sans-serif typeface** for UI text — sans-serif is the safest choice for legibility, neutrality, and simplicity across sizes. Prefer a typeface with a relatively tall x-height (taller lowercase letters), which improves legibility at small sizes.
- **Two font weights only: regular and bold** (semi-bold can substitute for bold if bold feels too heavy). More weights add visual noise and are harder to apply consistently. Use bold for headings/emphasis, regular for everything else; reserve very thin or very heavy weights (if used at all) for large display text, since they're hard to read small.
- **Avoid uppercase for anything but very short labels.** Readers recognize word *shapes*, and uppercase text is all the same rectangular shape, forcing letter-by-letter reading. Use sentence case (first word and proper nouns capitalized) instead.
- **Line length: 40–80 characters per line** including spaces, for comfortable reading — shorter forces the eyes to travel back too often, longer makes it hard to track where a line starts and ends. Don't stretch body text to the full width of a page just because the space is there.
- **Line height ≥1.5 (150%) for body text**, generally staying between 1.5–2. Tighter line height causes people to lose their place and reread lines.
- **Decrease letter spacing for large headings.** Most text typefaces are designed with wider spacing for legibility at small sizes; at large display sizes that spacing can look loose, so tightening it slightly improves the aesthetic (display typefaces usually don't need this adjustment).
- **Avoid pure black text** — see Color and contrast above.

## 7. Alignment

**Use as few alignments as possible within any one component or section — ideally just one.** Mixing left, center, and right alignment forces the eye to zig-zag and re-find the starting point of each line or element, adding cognitive load without any visual benefit.

- **Left-align body text and most UI content.** For languages read left-to-right, this matches natural reading flow and keeps a consistent starting edge.
- **Center alignment is fine for short text** (headings, a couple of lines) since it can be read in one glance, but avoid it for longer body text — the ragged, shifting left edge makes each new line harder to locate.
- When a section mixes alignments (e.g. centered tabs above a left-aligned list, or a testimonial with a centered name, right-aligned photo, and left-aligned quote), first ask whether the whole section could just be left-aligned. If one element must differ (e.g. a photo), keep the majority — especially all of the text — on a single alignment.

## 8. Consistency and simplicity

- **Similar-looking elements should behave similarly, and vice versa.** If two things share a visual style (color, fill, border), people will assume they work the same way. Icons or badges styled like a button (same fill/border/color) will be expected to be clickable even when they're not — strip the button-like styling from non-interactive elements to avoid false affordances.
- **Consistency compounds.** Small details — consistent corner radius across buttons/cards/images, a single icon stroke weight, matching spacing patterns — individually look minor but collectively make a design feel coherent versus assembled from mismatched parts.
- **Minimal ≠ simple.** A minimal interface has fewer visual elements, but that doesn't guarantee it's easy to understand — over-trimming can remove information people actually need (e.g. icon-only navigation with no text labels can be genuinely ambiguous, and hurts screen-reader users especially). Simplification should remove *noise*, not *substance*. If usability testing (or common sense) shows people can't tell what an icon means, add the label back.
- **Balance icon + text pairs.** When pairing an icon with a label (e.g. bottom navigation), make sure they carry similar visual weight — an icon that's bolder/larger/darker than its adjacent label will dominate and make the pairing feel unbalanced; darkening or resizing the text to match usually fixes it.
- **Remove unnecessary decoration.** Extra borders, background fills, or whitespace that don't serve a grouping or hierarchy purpose add cognitive load for no benefit — if removing a line or fill doesn't lose any information or grouping cue, remove it.

## 9. Two worked examples

Two end-to-end before/after walkthroughs informed this checklist:

- **A community blogging platform's profile page.** Applying the checklist above — an 8pt spacing scale, 3:1/4.5:1 contrast fixes on icons/buttons/tabs, collapsing to a single primary "follow" button, widening tap targets, un-hiding actions that were tucked into an overflow menu, tightening letter-spacing on the large name heading, adding an underline/fill to indicate selected tab/nav state, single left alignment, removing redundant containers around list items, trimming to two font weights, matching corner radii, and adding text labels to bottom-nav icons — took a cluttered, hard-to-scan profile page to a clean, accessible one without changing the underlying content or brand.
- **A short-term rental listing page.** The same kind of pass — grouping with spacing instead of tight clutter, fixing icon/button contrast, using the Squint Test to find and fix a weak visual hierarchy (a low-contrast primary button competing with a photo-count label), stripping decorative blue from non-interactive elements like a star rating, switching a detailed serif heading to a simple sans-serif with a taller x-height, moving from uppercase to sentence case, dropping to two font weights, using dark grey instead of pure black, left-aligning a centered paragraph, and increasing line-height from 1 to 1.5 — took a busy, hard-to-use listing page to a calmer, more usable one using the same checklist.

The pattern in both: fix spacing/grouping and visual hierarchy first (this alone resolves most of the "feels cluttered" complaints), then contrast and buttons (this resolves most accessibility risk), then typography and alignment (this resolves most of the remaining "feels unpolished" complaints).

## 10. Sources

This reference distills and reorganizes guidance from:
- A UI design book's "Fundamentals," "Layout and spacing," and "Typography" chapters (interaction cost, grouping methods, line length).
- Adham Dannaway, "14 logic-driven UI design tips to improve any interface," UX Planet.
- Adham Dannaway, "16 little UI design tips that make a big impact," UX Planet.
- Adham Dannaway, "UI design tip: Try to avoid using multiple alignments," UX Planet.
- Adham Dannaway, "I've been doing buttons wrong! Have you?," UX Planet.

For the original worked examples, illustrations, and full context, read the source articles directly — this file is a working checklist distilled from them, not a replacement for them.