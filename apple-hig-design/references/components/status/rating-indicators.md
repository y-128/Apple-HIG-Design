---
title: Rating indicators
url: https://developer.apple.com/design/human-interface-guidelines/rating-indicators
platforms: [macOS]
last_updated: 2022-09-23
---

# Rating indicators

A rating indicator uses a series of horizontally arranged graphical symbols — by default, stars — to communicate a ranking level.

## Core guidance

A rating indicator doesn't display partial symbols; it rounds the value to display complete symbols only. Within a rating indicator, symbols are always the same distance apart and don't expand or shrink to fit the component's width.

### Best practices

**Make it easy to change rankings.** When presenting a list of ranked items, let people adjust the rank of individual items inline without navigating to a separate editing screen.

**If you replace the star with a custom symbol, make sure that its purpose is clear.** The star is a very recognizable ranking symbol, and people may not associate other symbols with a rating scale.

## Platform considerations

No additional considerations for macOS, the only platform rating indicators support. Not supported in iOS, iPadOS, tvOS, visionOS, or watchOS.

## Native implementation

**Related**
- Ratings and reviews

**Developer documentation**
- `NSLevelIndicator.Style.rating` — AppKit

**Key APIs**
- `NSLevelIndicator.Style.rating` — configures an `NSLevelIndicator` to render as a rating indicator

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**Unlike most components in this skill, the web audience for star ratings is bigger than Apple's own.** Apple scopes this component to macOS only — it's genuinely rare in Apple's own apps. On the web, star ratings are one of the most common UI patterns in existence (e-commerce, review sites, app stores), so the principles below carry more real-world weight on the web side of the mapping than they do in Apple's own ecosystem.

**"Rounds to complete symbols only, never partial" → this is where the mapping explicitly breaks down.** Apple's rating indicator is a display-only, whole-symbol-only component: it rounds a value like 3.6 to either 3 or 4 full stars and never renders a partial star. Web rating UI has gone the opposite direction almost universally — half-star and fractional-star fills (via a background gradient or a clipped overlay star) are the de facto standard because web ratings are usually aggregate scores (an average of many individual 1–5 ratings) where the extra precision genuinely matters to shoppers and readers. Don't treat Apple's whole-symbols-only rule as a web best practice; it's a deliberate simplification suited to a narrow macOS context, not a general rating-display principle.

**"Symbols are always the same distance apart, never expand or shrink to fit" → the CSS translation is exact.** This is a warning against `justify-content: space-between` or `space-around` on a rating widget's container — those stretch the gaps as the component resizes, which is precisely the behavior Apple prohibits. Use a fixed `gap` value between symbols instead, so the rating always reads as a consistent unit regardless of container width.

**"Make it easy to change rankings inline" → this is a rating *input*, and it needs the accessibility semantics of one, not of a static display.** An editable rating widget on the web should behave like a radio group: arrow-key navigation between the discrete values, a single tab stop for the whole control, and the current value exposed via `aria-valuenow` if built as a `slider`-role widget, or via checked-state semantics if built as visually-restyled radio inputs. A row of clickable `<span>` stars with no keyboard support or accessible name is the most common failure mode for this exact component on the web — Apple's inline-editing guidance implies keyboard and assistive-technology parity with the rest of the ranked-list UI, which a mouse-only star row doesn't provide.

**"If you replace the star with a custom symbol, make sure its purpose is clear" → applies unchanged, and matters more given how overloaded a bare icon symbol is on the web.** Hearts, thumbs, and circles are all in wide use for entirely different actions (favoriting, liking, availability status) elsewhere on the same page or site. If a custom rating symbol could plausibly be mistaken for one of those other affordances, pair it with a visible or `aria-label` text cue rather than relying on the symbol alone.

**Structured-data note: rating markup on the web carries SEO weight Apple's platform doesn't have to consider.** A macOS rating indicator is purely a UI element. A web rating widget, especially one showing an aggregate score, is frequently also marked up with schema.org `AggregateRating` for search-result rich snippets — a consideration with no HIG parallel, since it's about search engines rather than people using the interface.

## Do / Don't

| Do | Don't |
|---|---|
| Round to whole symbols only; never render a partial symbol | Display fractional or partially-filled symbols |
| Keep symbol spacing fixed regardless of the component's width | Stretch or compress symbol spacing to fill available width |
| Let people adjust an individual item's rank inline | Force navigation to a separate screen just to change a ranking |
| Use the star, since it's an instantly recognizable ranking symbol | Substitute a custom symbol without clarifying what it represents |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
