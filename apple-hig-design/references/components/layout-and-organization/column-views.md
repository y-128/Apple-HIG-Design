---
title: Column views
url: https://developer.apple.com/design/human-interface-guidelines/column-views
platforms: [macOS]
last_updated: unknown
---

> **Source limitation:** Apple publishes no change log for this page, so its last revision date is unknown.

# Column views

A column view — also called a browser — lets people view and navigate a data hierarchy using a series of vertical columns.

## Core guidance

Each column represents one level of the hierarchy and contains horizontal rows of data items. Within a column, any parent item that contains nested child items is marked with a triangle icon. When people select a parent, the next column displays its children. People can continue navigating in this way until they reach an item with no children, and can also navigate back up the hierarchy to explore other branches of data.

> **Note (Apple):** If you need to manage the presentation of hierarchical content in your iPadOS or visionOS app, consider using a split view.

### Best practices

**Consider using a column view when you have a deep data hierarchy in which people tend to navigate back and forth frequently between levels, and you don't need the sorting capabilities that a list or table provides.** For example, Finder offers a column view (in addition to icon, list, and gallery views) for navigating directory structures.

**Show the root level of your data hierarchy in the first column.** People know they can quickly scroll back to the first column to begin navigating the hierarchy from the top again.

**Consider showing information about the selected item when there are no nested items to display.** The Finder, for example, shows a preview of the selected item and information like the creation date, modification date, file type, and size.

**Let people resize columns.** This is especially important if the names of some data items are too long to fit within the default column width.

## Platform considerations

Not supported in iOS, iPadOS, tvOS, visionOS, or watchOS. Column views are a macOS-only pattern.

## Native implementation

**Related**
- Lists and tables
- Outline views
- Split views

**Developer documentation**
- `NSBrowser` — AppKit

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**Multi-column hierarchy navigation → the miller-column pattern.** Apple's own reasoning for the column view is narrow: it fits a *deep* hierarchy where people move back and forth between levels a lot, and don't need sorting. On the web, the direct analogue is a set of horizontally scrolling panel columns (the pattern popularized as "Miller columns"), each column populated by the previous column's selection. It is a genuine, non-stretched match because the interaction Apple describes — select a parent, reveal its children in the next column, keep prior columns visible for backtracking — translates without loss to a row of `overflow-x` scrollable panels driven by selection state.

**Root level always in the first, fixed column → keep the entry point pinned.** The reasoning is that people rely on being able to jump back to the start without hunting for it. On the web this means the leftmost column should not scroll out of view or get replaced — either pin it, or make navigating back to it a single, obvious action, not a multi-step undo of the browsing path.

**Showing item details in an empty terminal column → a persistent detail/preview pane.** When there is nothing further to drill into, Apple's Finder shows metadata instead of an empty column. The web equivalent is a detail pane that appears once selection reaches a leaf node, rather than leaving a column visually blank — an empty column reads as a bug, not as "you've reached the end."

**Resizable columns → resizable panels, with the same practical justification.** Apple's stated reason is that item names vary in length and a fixed width truncates some of them. This reasoning transfers directly: a web implementation needs draggable column dividers (or a min/max width with truncation plus a tooltip as a fallback) for the same reason, not as a nice-to-have.

**Where the mapping breaks down.** Column views are Apple's answer to a specific interaction cost — frequent back-and-forth across levels of a *known-deep* hierarchy — and the HIG itself steers iPadOS and visionOS toward a split view instead. On narrow viewports the miller-column pattern degrades badly (each column needs real width to show item names), so the honest web translation is: use it for wide desktop-class layouts navigating genuinely hierarchical data, and fall back to a breadcrumb-driven single list or a split view/master-detail pattern everywhere else — which is exactly what Apple does across its own platforms.

## Do / Don't

| Do | Don't |
|---|---|
| Use a column view for deep hierarchies with frequent back-and-forth navigation | Use it when a list or table's sorting is what people actually need |
| Show the root level in the first column | Bury the top of the hierarchy several columns deep |
| Show details for a selected item with no children | Leave a trailing column empty with no information |
| Let people resize columns | Force a fixed width that truncates long item names |
| Reach for a split view on iPadOS or visionOS | Try to reproduce a column view on a platform that doesn't support it |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
