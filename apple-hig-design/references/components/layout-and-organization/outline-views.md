---
title: Outline views
url: https://developer.apple.com/design/human-interface-guidelines/outline-views
platforms: [macOS]
last_updated: unknown
---

# Outline views

> **Source limitation:** Apple publishes no change log for this page, so its last revision date is unknown.

An outline view presents hierarchical data in a scrolling list of cells that are organized into columns and rows.

## Core guidance

An outline view includes at least one column that contains primary hierarchical data, such as a set of parent containers and their children. You can add columns, as needed, to display attributes that supplement the primary data; for example, sizes and modification dates. Parent containers have disclosure triangles that expand to reveal their children.

Finder windows offer an outline view for navigating the file system.

### Best practices

Outline views work well to display text-based content and often appear in the leading side of a split view, with related content on the opposite side.

**Use a table instead of an outline view to present data that's not hierarchical.** For guidance, see Lists and tables.

**Expose data hierarchy in the first column only.** Other columns can display attributes that apply to the hierarchical data in the primary column.

**Use descriptive column headings to provide context.** Use nouns or short noun phrases with title-style capitalization and no punctuation; in particular, avoid adding a trailing colon. Always provide column headings in a multi-column outline view. If you don't include a column heading in a single-column outline view, use a label or other means to make sure there's enough context.

**Consider letting people click column headings to sort an outline view.** In a sortable outline view, people can click a column heading to perform an ascending or descending sort based on that column. You can implement additional sorting based on secondary columns behind the scenes, if necessary. If people click the primary column heading, sorting occurs at each hierarchy level. For example, in the Finder, all top-level folders are sorted, then the items within each folder are sorted. If people click the heading of a column that's already sorted, the folders and their contents are sorted again in the opposite direction.

**Let people resize columns.** Data displayed in an outline view often varies in width. It's important to let people adjust column width as needed to reveal data that's wider than the column.

**Make it easy for people to expand or collapse nested containers.** For example, clicking a disclosure triangle for a folder in a Finder window expands only that folder. However, Option-clicking the disclosure triangle expands all of its subfolders.

**Retain people's expansion choices.** If people expand various levels of an outline view to reach a specific item, store the state so you can display it again the next time. This way, people won't need to navigate back to the same place again.

**Consider using alternating row colors in multi-column outline views.** Alternating colors can make it easier for people to track row values across columns, especially in wide outline views.

**Let people edit data if it makes sense in your app.** In an editable outline view cell, people expect to be able to single-click a cell to edit its contents. Note that a cell can respond differently to a double click. For example, an outline view listing files might let people single-click a file's name to edit it, but double-click a file's name to open the file. You can also let people reorder, add, and remove rows if it would be useful.

**Consider using a centered ellipsis to truncate cell text instead of clipping it.** An ellipsis in the middle preserves the beginning and end of the cell text, which can make the content more distinct and recognizable than clipped text.

**Consider offering a search field to help people find values quickly in a lengthy outline view.** Windows with an outline view as the primary feature often include a search field in the toolbar. For guidance, see Search fields.

## Platform considerations

Outline views are a macOS-specific component. Not supported in iOS, iPadOS, tvOS, visionOS, or watchOS.

## Native implementation

**Related**
- Column views
- Lists and tables
- Split views

**Developer documentation**
- `OutlineGroup` — SwiftUI
- `NSOutlineView` — AppKit

**Videos:** Stacks, Grids, and Outlines in SwiftUI

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy. Of the components in this collection, an outline view maps unusually well to an existing web pattern: the tree view.

**Hierarchical disclosure → `role="tree"` / `role="treeitem"`, or nested `<details>` for the simple case.** Apple's disclosure-triangle-per-parent-container structure is exactly what ARIA's tree pattern (`role="tree"`, `role="treeitem"`, `aria-expanded`) exists to describe, and it's the right choice when you need multi-column data, keyboard arrow-key navigation between nodes, and programmatic selection. For a simpler, single-column outline with no need for custom keyboard handling, nested `<details>`/`<summary>` elements get expand/collapse and keyboard support for free from the browser, at the cost of the multi-column layout and fine-grained control Apple's version has.

**"Expose hierarchy in the first column only" → keep the tree semantics on one column, decorate the rest.** This transfers directly: only the primary column's cells should carry `role="treeitem"` / `aria-level` / `aria-expanded`; supplementary columns (size, date) are presented as plain descriptive text tied to the same row, not as separate tree nodes.

**Option-click-to-expand-all → a documented keyboard/modifier shortcut, not a hidden one.** Apple's power-user shortcut for expanding every subfolder at once has a reasonable web equivalent (e.g., Alt/Option-click on a disclosure control, or a "Expand all" action exposed in a toolbar), but unlike on macOS, there's no cross-browser convention people already know — so on the web this needs a visible, discoverable affordance, not a purely modifier-key-only secret.

**Retaining expansion state → persist it, and restore it before first paint if you can.** Apple's instruction to store which nodes are expanded maps to `localStorage`, a URL query parameter, or server-side state, depending on whether the tree should survive a page reload, be shareable via link, or sync across devices. The important part carries over unchanged: don't make someone re-expand the same five folders every time they return.

**Single-click-to-edit vs. double-click-to-open → the web has no shared convention here; be explicit.** This is where the mapping breaks down. macOS users have decades of learned expectation that single-click-to-edit and double-click-to-open coexist predictably in an outline view; no equivalent shared convention exists on the web, and overloading click count is a known accessibility and discoverability problem (double-click doesn't work well with touch or screen-reader interaction). Prefer separate, visible affordances — an explicit edit action (icon, keyboard shortcut, or dedicated edit mode) rather than relying on click-count alone.

**Centered-ellipsis truncation → same caveat as in lists and tables.** As with table cells, `text-overflow: ellipsis` only truncates at the end; reproducing Apple's centered truncation requires custom measurement logic, and the full value should remain available via `title` or an accessible name regardless of which truncation strategy you pick.

## Do / Don't

| Do | Don't |
|---|---|
| Use an outline view (tree view) only for genuinely hierarchical data | Use a hierarchical tree structure for flat, non-hierarchical data |
| Keep hierarchy markup and disclosure state in the primary column only | Scatter tree semantics across supplementary attribute columns |
| Use short, punctuation-free noun-phrase column headings | Add a trailing colon to a column heading |
| Let people resize and, where useful, sort columns | Lock column widths when content routinely overflows them |
| Persist which nodes are expanded across sessions | Force people to re-expand the same nodes every visit |
| Offer a visible, discoverable way to expand all nested levels at once | Hide "expand all" behind an undiscoverable modifier-only shortcut |
| Use separate, visible affordances for editing vs. opening an item | Rely on single-click vs. double-click alone to distinguish edit from open |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
