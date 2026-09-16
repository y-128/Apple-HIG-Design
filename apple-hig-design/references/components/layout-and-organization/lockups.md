---
title: Lockups
url: https://developer.apple.com/design/human-interface-guidelines/lockups
platforms: [tvOS]
last_updated: unknown
---

# Lockups

> **Source limitation:** Apple publishes no change log for this page, so its last revision date is unknown.

Lockups combine multiple separate views into a single, interactive unit.

## Core guidance

Each lockup consists of a content view, a header, and a footer. Headers appear above the main content for a lockup, and footers appear below the main content. All three views expand and contract together as the lockup gets focus.

According to the needs of your app, you can combine four types of lockup: cards, caption buttons, monograms, and posters.

### Best practices

**Allow adequate space between lockups.** A focused lockup expands in size, so leave enough room between lockups to avoid overlapping or displacing other lockups. For guidance, see Layout.

**Use consistent lockup sizes within a row or group.** A group of buttons or a row of content images is more visually appealing when the widths and heights of all elements match.

For developer guidance, see `TVLockupView` and `TVLockupHeaderFooterView`.

### Cards

A card combines a header, footer, and content view to present ratings and reviews for media items.

For developer guidance, see `TVCardView`.

### Caption buttons

A caption button can include a title and a subtitle beneath the button. A caption button can contain either an image or text.

**Make sure that when people focus on them, caption buttons tilt with the motion that they swipe.** When aligned vertically, caption buttons tilt up and down. When aligned horizontally, caption buttons tilt left and right. When displayed in a grid, caption buttons tilt both vertically and horizontally.

For developer guidance, see `TVCaptionButtonView`.

### Monograms

Monograms identify people, usually the cast and crew for a media item. Each monogram consists of a circular picture of the person and their name. If an image isn't available, the person's initials appear in place of an image.

**Prefer images over initials.** An image of a person creates a more intimate connection than text.

For developer guidance, see `TVMonogramContentView`.

### Posters

Posters consist of an image and an optional title and subtitle, which are hidden until the poster comes into focus. Posters can be any size, but the size needs to be appropriate for their content. For related guidance, see Image views.

For developer guidance, see `TVPosterView`.

## Platform considerations

Lockups are a tvOS-specific component. Not supported in iOS, iPadOS, macOS, visionOS, or watchOS.

## Native implementation

**Related**
- Designing for tvOS
- Layout

**Developer documentation**
- `TVLockupView` — TVUIKit
- `TVLockupHeaderFooterView` — TVUIKit

**Key APIs**
- `TVCardView` — the card lockup type
- `TVCaptionButtonView` — the caption button lockup type
- `TVMonogramContentView` — the monogram lockup type
- `TVPosterView` — the poster lockup type

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance, and lockups are a poor fit for it in the first place: they exist to solve a problem the web mostly doesn't have. A lockup's defining behavior — a header, content view, and footer that expand and contract together as a single unit gains remote-control focus — is built for the 10-foot, D-pad-driven interaction model of tvOS. The web's dominant input is a mouse or touch pointer with hover and click, not a directional-focus engine moving between discrete, pre-registered focusable regions across a whole screen. There's no meaningful web analogue for the tilt-with-swipe-motion behavior of caption buttons or the coordinated expand/contract of a focused lockup's three sub-views; treat this as platform-specific.

That said, two narrower ideas do transfer, because they aren't really about the focus engine:

**Consistent sizing within a row or group → still a real web rule.** Apple's instruction to match widths and heights across a row of lockups is just good grid hygiene, and it applies identically to a web card grid or carousel — mismatched card dimensions in a row look sloppy and cause layout jitter regardless of input model.

**Monograms → the avatar-with-initials-fallback pattern.** "Prefer images over initials, but fall back to initials when no image is available" is one of the most common patterns in web UI (Slack, GitHub, and most avatar components work exactly this way), and Apple's reasoning — a photo creates a more intimate connection than text — is the same reasoning that motivates it on the web. The circular-picture-plus-name composition, and the graceful degradation to initials, is worth keeping even though the surrounding lockup mechanics are not.

## Do / Don't

| Do | Don't |
|---|---|
| Leave enough space between lockups for the focused one to expand | Let a focused lockup overlap or displace its neighbors |
| Keep lockup widths and heights consistent within a row or group | Mix mismatched lockup sizes in the same row |
| Tilt caption buttons in the direction of the swipe motion | Leave caption buttons static when people focus and swipe them |
| Prefer a real photo for a monogram | Show initials when a usable image is available |
| Size a poster appropriately for its content | Reveal a poster's title and subtitle before it has focus |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
