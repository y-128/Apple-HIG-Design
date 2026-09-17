---
title: Lists and tables
url: https://developer.apple.com/design/human-interface-guidelines/lists-and-tables
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: 2023-06-21
---

# Lists and tables

Lists and tables present data in one or more columns of rows.

## Core guidance

A table or list can represent data that's organized in groups or hierarchies, and it can support user interactions like selecting, adding, deleting, and reordering. Apps and games on all platforms can use tables to present content and options; many apps use lists to express an overall information hierarchy and help people navigate it. For example, iOS Settings uses a hierarchy of lists to help people choose options, and several apps — such as Mail in iPadOS and macOS — use a table within a split view.

Sometimes people need to work with complex data in a multicolumn table or a spreadsheet. Apps that offer productivity tasks often use a table to represent various characteristics or attributes of the data in separate, sortable columns.

### Best practices

**Prefer displaying text in a list or table.** A table can include any type of content, but the row-based format is especially well suited to making text easy to scan and read. If you have items that vary widely in size — or you need to display a large number of images — consider using a collection instead.

**Let people edit a table when it makes sense.** People appreciate being able to reorder a list, even if they can't add or remove items. In iOS and iPadOS, people must enter an edit mode before they can select table items.

**Provide appropriate feedback when people select a list item.** The feedback can vary depending on whether selecting the item reveals a new view or toggles the item's state. In general, a table that helps people navigate through a hierarchy persistently highlights the selected row to clarify the path people are taking. In contrast, a table that lists options often highlights a row only briefly before adding an image — such as a checkmark — indicating that the item is selected.

### Content

**Keep item text succinct so row content is comfortable to read.** Short, succinct text can help minimize truncation and wrapping, making text easier to read and scan. If each item consists of a large amount of text, consider alternatives that help you avoid displaying over-large table rows. For example, you could list item titles only, letting people choose an item to reveal its content in a detail view.

**Consider ways to preserve readability of text that might otherwise get clipped or truncated.** When a table is narrow — for example, if people can vary its width — you want content to remain recognizable and easy to read. Sometimes, an ellipsis in the middle of text can make an item easier to distinguish because it preserves both the beginning and the end of the content.

**Use descriptive column headings in a multicolumn table.** Use nouns or short noun phrases with title-style capitalization, and don't add ending punctuation. If you don't include a column heading in a single-column table view, use a label or a header to help people understand the context.

### Style

**Choose a table or list style that coordinates with your data and platform.** Some styles use visual details to help communicate grouping and hierarchy or to provide specific experiences. In iOS and iPadOS, for example, the grouped style uses headers, footers, and additional space to separate groups of data; the elliptical style available in watchOS makes items appear as if they're rolling off a rounded surface as people scroll; and macOS defines a bordered style that uses alternating row backgrounds to help make large tables easier to use. For developer guidance, see `ListStyle`.

**Choose a row style that fits the information you need to display.** For example, you might need to display a small image in the leading end of a row, followed by a brief explanatory label. Some platforms provide built-in row styles you can use to arrange content in list rows, such as the `UIListContentConfiguration` API you can use to lay out content in a list's rows, headers, and footers in iOS, iPadOS, and tvOS.

## Platform considerations

### iOS, iPadOS, visionOS

**Use an info button only to reveal more information about a row's content.** An info button — called a detail disclosure button when it appears in a list row — doesn't support navigation through a hierarchical table or list. If you need to let people drill into a list or table row's subviews, use a disclosure indicator accessory control. For developer guidance, see `UITableViewCell.AccessoryType.disclosureIndicator`.

> *Image caption:* An info button shows details about a list item; it doesn't support navigation.
> *Image caption:* A disclosure indicator reveals the next level in a hierarchy; it doesn't show details about the item.

**Avoid adding an index to a table that displays controls — like disclosure indicators — in the trailing ends of its rows.** An index typically consists of the letters in an alphabet, displayed vertically at the trailing side of a list. People can jump to a specific section in the list by choosing the index letter that maps to it. Because both the index and elements like disclosure indicators appear on the trailing side of a list, it can be difficult for people to use one element without activating the other.

### macOS

**When it provides value, let people click a column heading to sort a table view based on that column.** If people click the heading of a column that's already sorted, re-sort the data in the opposite direction.

**Let people resize columns.** Data displayed in a table view often varies in width. People appreciate resizing columns to help them concentrate on different areas or reveal clipped data.

**Consider using alternating row colors in a multicolumn table.** Alternating colors can help people track row values across columns, especially in a wide table.

**Use an outline view instead of a table view to present hierarchical data.** An outline view looks like a table view, but includes disclosure triangles for exposing nested levels of data. For example, an outline view might display folders and the items they contain.

### tvOS

**Confirm that images near a table still look good as each row highlights and slightly increases in size when it becomes focused.** A focused row's corners can also become rounded, which may affect the appearance of images on either side of it. Account for this effect as you prepare images, and don't add your own masks to round the corners.

### watchOS

**When possible, limit the number of rows.** Short lists are easier for people to scan, but sometimes people expect a long list of items. For example, if people subscribe to a large number of podcasts, they might think something's wrong if they can't view all their items. You can help make a long list more manageable by listing the most relevant items and providing a way for people to view more.

**Constrain the length of detail views if you want to support vertical page-based navigation.** People use vertical page-based navigation to swipe vertically among the detail items of different list rows. Navigating in this way saves time because people don't need to return to the list to tap a new detail item, but it works only when detail views are short. If your detail views scroll, people won't be able to use vertical page-based navigation to swipe among them.

## Native implementation

**Related**
- Collections
- Outline views
- Layout

**Developer documentation**
- List — SwiftUI
- Tables — SwiftUI
- `UITableView` — UIKit
- `NSTableView` — AppKit

**Key APIs**
- `ListStyle` — choose a list style (grouped, elliptical, bordered, and others) that coordinates with platform and data
- `UIListContentConfiguration` — lay out content in a list's rows, headers, and footers on iOS, iPadOS, and tvOS
- `UITableViewCell.AccessoryType.disclosureIndicator` — the accessory control for drilling into a row's subviews, distinct from an info button
- `NSTableView` — table view on macOS

**Videos:** Stacks, Grids, and Outlines in SwiftUI

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**Row-based text scanning → a semantic `<table>` or list, not a grid of divs.** Apple's preference for row-based text over image-heavy collections maps directly onto the web's own accessibility tree: a `<table>` with `<th>` headers, or an ordered/unordered list with one focusable row per `<li>`, gives screen readers and keyboard navigation a structure to walk that a bare grid of `<div>`s does not. Where Apple says "consider a collection instead" for widely varying item sizes or heavy image content, the web analogue is a card grid rather than forcing irregular content into table rows.

**Persistent selection highlighting → `aria-selected` and `aria-current`, not just a background color.** Apple's rule that hierarchical navigation persistently highlights the selected row exists so people stay oriented as they drill down. On the web, a CSS background change alone communicates nothing to assistive technology; pair it with `aria-selected="true"` on the row or `aria-current="page"` when the row represents the active location in a navigation hierarchy.

**Middle-truncated text → CSS can't do it natively; decide deliberately.** Apple's centered-ellipsis technique (preserving both the start and end of a string) has no direct CSS equivalent — `text-overflow: ellipsis` only truncates at the end. Reproducing the HIG behavior on the web requires either a small script that measures and truncates the string in JavaScript, or accepting end-truncation as the pragmatic web default. Either way, keep the full value in a `title` attribute or an accessible name so the truncation never hides information entirely.

**Column headings and sortable columns → `<th scope="col">` plus `aria-sort`.** macOS's click-to-sort, click-again-to-reverse pattern is exactly what `aria-sort="ascending" | "descending"` exists to announce. Apple's rule against ending punctuation and its preference for short noun-phrase headings both transfer unchanged — they're really about scanability, which is platform-independent.

**Resizable columns → a resize handle with a real hit target, not a 1px border.** Apple's macOS guidance to let people resize columns assumes a precise pointer. On the web, a resizable column needs a wider invisible drag handle than its visible divider, because touch and imprecise-pointer input make a hairline border effectively unusable. Persist the chosen widths (e.g., to `localStorage`) the way a native app persists user-adjusted column widths.

**Focus-driven row growth (tvOS) → `:focus-visible` scaling, tested against layout shift.** tvOS grows and rounds a focused row; a web equivalent using `transform: scale()` on `:focus-visible` avoids the layout-shift problems that scaling `width`/`height` would cause, and, like Apple's warning about image masks, needs to be designed so any thumbnail inside the row already anticipates the rounded/scaled state rather than fighting it via `overflow: hidden` tricks alone.

**Watch-scale row limits → don't stretch this rule to phone or desktop.** Apple's "limit the number of rows" guidance is explicitly a small-screen, glanceable-content rule for watchOS. On a desktop or even phone-sized web layout there's no equivalent physical constraint — the better web practice is virtualization or pagination for genuinely long lists, not an arbitrary row cap borrowed from a much smaller screen.

## Do / Don't

| Do | Don't |
|---|---|
| Use a row-based list or table for scannable text content | Force widely varying item sizes or heavy imagery into table rows |
| Let people reorder a list even without add/remove | Require an edit mode for actions people expect to do directly |
| Persistently highlight the selected row when it leads to a detail view | Leave selection state ambiguous during hierarchical navigation |
| Keep row text succinct; push large content into a detail view | Let a single row balloon with a large amount of text |
| Use short, noun-phrase column headings with title-style capitalization | Add ending punctuation to column headings |
| Use a disclosure indicator to drill into a row's subviews | Use an info button to support navigation |
| Let people resize and sort columns on macOS | Add an index next to trailing-edge accessory controls like disclosure indicators |
| Use an outline view instead of a table view for hierarchical data on macOS | Add your own corner masks to images near a tvOS focused row |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
