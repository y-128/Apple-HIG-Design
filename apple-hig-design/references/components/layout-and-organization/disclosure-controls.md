---
title: Disclosure controls
url: https://developer.apple.com/design/human-interface-guidelines/disclosure-controls
platforms: [iOS, iPadOS, macOS, visionOS]
last_updated: unknown
---

> **Source limitation:** Apple publishes no change log for this page, so its last revision date is unknown.

# Disclosure controls

Disclosure controls reveal and hide information and functionality related to specific controls or views.

## Core guidance

### Best practices

**Use a disclosure control to hide details until they're relevant.** Place controls that people are most likely to use at the top of the disclosure hierarchy so they're always visible, with more advanced functionality hidden by default. This organization helps people quickly find the most essential information without overwhelming them with too many detailed options.

### Disclosure triangles

A disclosure triangle shows and hides information and functionality associated with a view or a list of items. For example, Keynote uses a disclosure triangle to show advanced options when exporting a presentation, and the Finder uses disclosure triangles to progressively reveal hierarchy when navigating a folder structure in list view.

> *Image caption:* A disclosure triangle shown in its collapsed and expanded states.

A disclosure triangle points inward from the leading edge when its content is hidden and down when its content is visible. Clicking or tapping the disclosure triangle switches between these two states, and the view expands or collapses accordingly to accommodate the content.

**Provide a descriptive label when using a disclosure triangle.** Make sure your labels indicate what is disclosed or hidden, like "Advanced Options."

> **Developer note (Apple):** For developer guidance, see `NSButton.BezelStyle.disclosure`.

### Disclosure buttons

A disclosure button shows and hides functionality associated with a specific control. For example, the macOS Save sheet shows a disclosure button next to the Save As text field. When people click or tap this button, the Save dialog expands to give advanced navigation options for selecting an output location for their document.

A disclosure button points down when its content is hidden and up when its content is visible. Clicking or tapping the disclosure button switches between these two states, and the view expands or collapses accordingly to accommodate the content.

> *Image caption:* A disclosure button shown in its collapsed and expanded states.

**Place a disclosure button near the content that it shows and hides.** Establish a clear relationship between the control and the expanded choices that appear when a person clicks or taps a button.

**Use no more than one disclosure button in a single view.** Multiple disclosure buttons add complexity and can be confusing.

> **Developer note (Apple):** For developer guidance, see `NSButton.BezelStyle.pushDisclosure`.

## Platform considerations

No additional considerations for macOS. Not supported in tvOS or watchOS.

### iOS, iPadOS, visionOS

Disclosure controls are available in iOS, iPadOS, and visionOS with the SwiftUI `DisclosureGroup` view.

## Native implementation

**Related**
- Outline views
- Lists and tables
- Buttons

**Developer documentation**
- `DisclosureGroup` — SwiftUI
- `NSButton.BezelStyle.disclosure` — AppKit
- `NSButton.BezelStyle.pushDisclosure` — AppKit

**Videos:** Stacks, Grids, and Outlines in SwiftUI

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**Hiding details until relevant, most-used controls at the top → progressive disclosure via `<details>`/`<summary>` or an accessible expand/collapse widget.** Apple's underlying reasoning is that surfacing every option at once overwhelms people, so the interface should default to showing what's essential and let people opt into complexity. The native HTML `<details>` element gives this behavior for free, including keyboard and screen-reader support; a custom-built expand/collapse component needs to reproduce that same accessible toggle semantics (`aria-expanded`, keyboard activation) by hand.

**Disclosure triangle → the native disclosure marker, or a rotated chevron/icon tied to `aria-expanded`.** The reasoning behind the triangle's two orientations (inward when collapsed, down when expanded) is to give a persistent, glanceable state indicator independent of the label text. On the web, `<details>` ships a default marker that does exactly this, and it can be restyled; if you build a custom toggle, the icon's rotation must be driven by the same state that controls visibility, not by a separate flag that can fall out of sync.

**A descriptive label naming what's disclosed → the trigger's accessible name must say what it reveals.** Apple's "Advanced Options" example is a label rule, not a triangle rule — the triangle only carries state, the label carries meaning. This transfers directly: a web toggle's visible text (and its accessible name, if an icon-only trigger is used) must name the hidden content, not read as a generic "More" or "Details" with no context.

**Disclosure button placement near its content → visual and DOM proximity, not just visual proximity.** Apple's point is that the relationship between trigger and revealed content must be obvious. On the web this means the trigger and the region it controls should also be linked programmatically with `aria-controls` (or by DOM adjacency), so the relationship survives for assistive technology, not only for sighted users who can see the layout.

**At most one disclosure button per view → don't stack multiple independent expand controls without a clear hierarchy.** Apple's reasoning is that multiple disclosure buttons compound complexity. This is a stricter rule than "avoid clutter" for the specific *disclosure button* pattern (a button that unexpectedly reconfigures a dialog/sheet); ordinary `<details>` accordions with several independent sections are common and fine on the web, but each toggle should have an unambiguous, singular target — don't let one control's expansion state depend on another's.

## Do / Don't

| Do | Don't |
|---|---|
| Hide advanced functionality behind a disclosure control by default | Surface every option at once and overwhelm people |
| Put the most-used controls at the top of the hierarchy | Bury commonly needed controls behind a disclosure |
| Label a disclosure triangle with what it reveals, like "Advanced Options" | Leave a disclosure triangle with no descriptive label |
| Place a disclosure button near the content it controls | Separate a disclosure button from the content it affects |
| Use at most one disclosure button per view | Stack multiple disclosure buttons in the same view |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
