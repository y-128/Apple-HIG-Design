---
title: Boxes
url: https://developer.apple.com/design/human-interface-guidelines/boxes
platforms: [iOS, iPadOS, macOS, visionOS]
last_updated: unknown
---

> **Source limitation:** Apple publishes no change log for this page, so its last revision date is unknown.

# Boxes

A box creates a visually distinct group of logically related information and components.

## Core guidance

By default, a box uses a visible border or background color to separate its contents from the rest of the interface. A box can also include a title.

### Best practices

**Prefer keeping a box relatively small in comparison with its containing view.** As a box's size gets close to the size of the containing window or screen, it becomes less effective at communicating the separation of grouped content, and it can crowd other content.

**Consider using padding and alignment to communicate additional grouping within a box.** A box's border is a distinct visual element — adding nested boxes to define subgroups can make your interface feel busy and constrained.

### Content

**Provide a succinct introductory title if it helps clarify the box's contents.** The appearance of a box helps people understand that its contents are related, but it might make sense to provide more detail about the relationship. Also, a title can help VoiceOver users predict the content they encounter within the box.

**If you need a title, write a brief phrase that describes the contents.** Use sentence-style capitalization. Avoid ending punctuation unless you use a box in a settings pane, where you append a colon to the title.

## Platform considerations

No additional considerations for visionOS. Not supported in tvOS or watchOS.

### iOS, iPadOS

By default, iOS and iPadOS use the secondary and tertiary background colors in boxes.

### macOS

By default, macOS displays a box's title above it.

## Native implementation

**Related**
- Layout

**Developer documentation**
- `GroupBox` — SwiftUI
- `NSBox` — AppKit

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mapping below applies the same principles to the web; it is inference, not Apple policy.

**A box's border or background → a visually bounded container.** Apple's reason for a box is to make grouped content read as a distinct unit without a person having to infer the grouping from layout alone. On the web this is a container with a border, a background-color shift from its surroundings, or both — the same visual logic as a `fieldset`, a card, or a bordered panel. What matters is that the boundary is perceptible, not which CSS property draws it.

**Keeping a box small relative to its container → don't let a bounded region swallow the viewport.** Apple's warning is that a box near the size of its window stops reading as a subgroup. The web equivalent is the same failure mode at the scale of a full-width or full-height panel: once a bordered container spans nearly the whole viewport, the border stops doing grouping work and just becomes visual noise. Reserve boxes for content that is genuinely a subset of a larger view.

**Avoiding nested boxes → avoid nested bordered containers.** Apple's advice to use padding and alignment instead of a second border applies directly on the web. Nested `border`s or nested card components compound visual weight fast; whitespace and alignment communicate a subgroup with less clutter than another rectangle.

**A title that helps VoiceOver users → an accessible name for the region.** Apple's point about titles aiding VoiceOver maps to using a heading element or an `aria-labelledby`/`aria-label` association on the container, so a screen reader announces what the group is before reading its contents — not just a visually adjacent heading with no programmatic link to the region.

## Do / Don't

| Do | Don't |
|---|---|
| Keep a box small relative to its containing view | Let a box approach the size of the window or screen |
| Use padding and alignment for subgroups | Nest boxes inside boxes to show subgroups |
| Give a box a succinct title when it clarifies content | Add a title that just repeats the obvious |
| Use sentence-style capitalization for a title | Add ending punctuation, except a colon in settings panes |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
