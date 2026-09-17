---
title: Path controls
url: https://developer.apple.com/design/human-interface-guidelines/path-controls
platforms: [macOS]
last_updated: unknown
---

> **Source limitation:** Apple publishes no change log for this page, so its last revision date is unknown.

# Path controls

A path control shows the file system path of a selected file or folder.

## Core guidance

For example, choosing View > Show Path Bar in the Finder displays a path bar at the bottom of the window. It shows the path of the selected item, or the path of the window's folder if nothing is selected.

### Styles

There are two styles of path control.

**Standard.** A linear list that includes the root disk, parent folders, and selected item. Each item appears with an icon and a name. If the list is too long to fit within the control, it hides names between the first and last items. If you make the control editable, people can drag an item onto the control to select the item and display its path in the control.

**Pop up.** A control similar to a pop-up button that shows the icon and name of the selected item. People can click the item to open a menu containing the root disk, parent folders, and selected item. If you make the control editable, the menu contains an additional Choose command that people can use to select an item and display it in the control. They can also drag an item onto the control to select it and display its path.

### Best practices

**Use a path control in the window body, not the window frame.** Path controls aren't intended for use in toolbars or status bars. Note that the path control in the Finder appears at the bottom of the window body, not in the status bar — Apple's own reference implementation is the counter-example to reach for if the temptation is to treat a path control as chrome.

## Platform considerations

Not supported in iOS, iPadOS, tvOS, visionOS, or watchOS. This is a macOS-only component with no cross-platform variant to compare against.

## Native implementation

**Related**
- File management

**Developer documentation**
- `NSPathControl` — AppKit

**Key APIs**
- `NSPathControl` — the sole API surface for this component; both the Standard and Pop up styles are configurations of the same class

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mapping below applies the same principles to the web; it is inference, not Apple policy.

**A path control is a breadcrumb trail, and the web already has a well-established pattern for it: `nav aria-label="Breadcrumb"` wrapping an ordered list of links, with the current (final) item marked `aria-current="page"` and not a link.** The reasoning behind Apple's control transfers directly: a path control exists so people can see *and* act on their position in a hierarchy — every ancestor is a real navigation target, not just a label. A web breadcrumb that renders ancestors as plain text rather than links throws away exactly the interaction Apple's Standard style is built around (clicking any parent folder jumps there).

**The Standard style's truncation behavior ("hides names between the first and last items" when the list is too long) → this is the same problem as an overflowing breadcrumb trail on a narrow viewport, and the standard web fix is structurally identical:** keep the first (root) and last (current) items always visible, collapse the middle into a single ellipsis item, and make that ellipsis item itself an activatable disclosure (a menu or dropdown) that reveals the hidden middle levels — which is effectively what Apple's Pop up style does unconditionally.

**The Pop up style's menu-as-control pattern → a `select`-like dropdown or a button that opens a listbox of ancestors,** useful specifically when horizontal space is tight enough that even a collapsed breadcrumb trail doesn't fit. The "Choose" command in an editable Pop up path control — letting someone pick an arbitrary new file or folder rather than only navigating existing ancestors — doesn't have a common web equivalent; that behavior belongs to a file picker, not a breadcrumb, so don't try to fold file-selection into a breadcrumb component on the web.

**"Use it in the window body, not the frame" → keep breadcrumbs in the content flow, not pinned into a toolbar or app-chrome region that visually reads as fixed navigation.** Apple's reasoning is about where people expect this information to live relative to what it describes; a breadcrumb that floats in a sticky top bar detached from the content it maps loses that same relationship on the web.

## Do / Don't

| Do | Don't |
|---|---|
| Place a path control in the window body | Put a path control in a toolbar or status bar |
| Show the root disk, parent folders, and selected item as one linear trail | Truncate without preserving the first and last items |
| Make every ancestor in the path clickable/navigable | Render path segments as inert, non-interactive text |
| Use the Pop up style when horizontal space is constrained | Force the full Standard trail into a space too narrow for it |
| Support drag-to-select onto an editable path control | Make an editable control accept only typed paths |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
