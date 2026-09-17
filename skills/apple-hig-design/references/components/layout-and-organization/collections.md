---
title: Collections
url: https://developer.apple.com/design/human-interface-guidelines/collections
platforms: [iOS, iPadOS, macOS, tvOS, visionOS]
last_updated: unknown
---

> **Source limitation:** Apple publishes no change log for this page, so its last revision date is unknown.

# Collections

A collection manages an ordered set of content and presents it in a customizable and highly visual layout.

## Core guidance

Generally speaking, collections are ideal for showing image-based content.

### Best practices

**Use the standard row or grid layout whenever possible.** Collections display content by default in a horizontal row or a grid, which are simple, effective appearances that people expect. Avoid creating a custom layout that might confuse people or draw undue attention to itself.

**Consider using a table instead of a collection for text.** It's generally simpler and more efficient to view and digest textual information when it's displayed in a scrollable list.

**Make it easy to choose an item.** If it's too difficult to get to an item in your collection, people will get frustrated and lose interest before reaching the content they want. Use adequate padding around images to keep focus or hover effects easy to see and prevent content from overlapping.

**Add custom interactions when necessary.** By default, people can tap to select, touch and hold to edit, and swipe to scroll. If your app requires it, you can add more gestures for performing custom actions.

**Consider using animations to provide feedback when people insert, delete, or reorder items.** Collections support standard animations for these actions, and you can also use custom animations.

## Platform considerations

No additional considerations for macOS, tvOS, or visionOS. Not supported in watchOS.

### iOS, iPadOS

**Use caution when making dynamic layout changes.** The layout of a collection can change dynamically. Be sure any changes make sense and are easy to track. If possible, try to avoid changing the layout while people are viewing and interacting with it, unless it's in response to an explicit action.

## Native implementation

**Related**
- Lists and tables
- Image views
- Layout

**Developer documentation**
- `UICollectionView` — UIKit
- `NSCollectionView` — AppKit

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**Standard row or grid layout → CSS Grid or Flexbox with a conventional visual rhythm.** Apple's reasoning is that people already carry an expectation of how image collections behave, so a custom scroll or reflow pattern spends attention on itself instead of on the content. On the web this argues against novel masonry or scroll-jacking layouts for what is fundamentally a photo grid — a plain grid with consistent gutters meets the expectation with the least friction.

**Prefer a table for text → prefer a list, not a card grid, for text-dominant content.** The underlying reasoning is about reading efficiency: a vertical, linearly scrollable arrangement is easier to scan than a two-dimensional grid when the content is mostly words. The web analogue is the same choice between a `table`/list layout and a grid of cards — grids cost more scanning effort for text and pay off mainly for images.

**Adequate padding around images → don't let hover/focus states collide.** Apple's concern is that focus or hover effects need enough surrounding space to render without visually merging into a neighboring item. On the web this is spacing generous enough that a `:hover` or `:focus-visible` outline, scale transform, or elevation shadow on one grid item doesn't overlap the adjacent item's box.

**Custom interactions on top of defaults → keyboard and pointer parity.** Apple's defaults (tap to select, hold to edit, swipe to scroll) are gestures; the web has no universal touch-and-hold convention, so a genuine equivalent needs a visible affordance (a context menu button, an edit toggle) reachable by keyboard, not just a `contextmenu` handler that assumes a pointing device.

**Animate insert/delete/reorder → animate list mutations so identity survives the change.** The reasoning behind Apple's default animations is that people track items by position, and an item that appears to teleport or vanish breaks that mental model. The web equivalent is animating layout changes (the FLIP technique, the View Transitions API, or a library's list-transition primitive) rather than letting the DOM reflow instantly.

**Caution with dynamic layout changes → don't reflow content under an active pointer or reading position.** Apple's iOS/iPadOS warning about changing layout mid-interaction maps directly to the web anti-pattern of content shifting under a person's cursor or scroll position — the same failure the web separately measures as cumulative layout shift.

## Do / Don't

| Do | Don't |
|---|---|
| Use the standard row or grid layout | Invent a custom layout that draws attention to itself |
| Use a table for text-heavy content | Force text content into an image-style collection |
| Give images adequate padding for focus/hover effects | Let items crowd or overlap each other |
| Add custom gestures only when the app needs them | Layer on interactions with no clear purpose |
| Animate inserts, deletes, and reorders | Let items appear or vanish with no transition |
| Change layout cautiously and predictably on iOS/iPadOS | Reflow the layout while someone is actively interacting with it |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
