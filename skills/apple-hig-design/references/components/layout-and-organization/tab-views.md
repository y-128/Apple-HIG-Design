---
title: Tab views
url: https://developer.apple.com/design/human-interface-guidelines/tab-views
platforms: [macOS, watchOS]
last_updated: 2023-06-05
---

# Tab views

A tab view presents multiple mutually exclusive panes of content in the same area, which people can switch between using a tabbed control.

## Core guidance

### Best practices

**Use a tab view to present closely related areas of content.** The appearance of a tab view provides a strong visual indication of enclosure. People expect each tab to display content that is in some way similar or related to the content in the other tabs.

**Make sure the controls within a pane affect content only in the same pane.** Panes are mutually exclusive, so ensure they're fully self-contained.

**Provide a label for each tab that describes the contents of its pane.** A good label helps people predict the contents of a pane before clicking or tapping its tab. In general, use nouns or short noun phrases for tab labels. A verb or short verb phrase may make sense in some contexts. Use title-style capitalization for tab labels.

**Avoid using a pop-up button to switch between tabs.** A tabbed control is efficient because it requires a single click or tap to make a selection, whereas a pop-up button requires two. A tabbed control also presents all choices onscreen at the same time, whereas people must click a pop-up button to see its choices. Note that a pop-up button can be a reasonable alternative in cases where there are too many panes of content to reasonably display with tabs.

**Avoid providing more than six tabs in a tab view.** Having more than six tabs can be overwhelming and create layout issues. If you need to present six or more tabs, consider another way to implement the interface. For example, you could instead present each tab as a view option in a pop-up button menu.

For developer guidance, see `NSTabView`.

### Anatomy

The tabbed control appears on the top edge of the content area. You can choose to hide the control, which is appropriate for an app that switches between panes programmatically.

When you hide the tabbed control, the content area can be borderless, bezeled, or bordered with a line. A borderless view can be solid or transparent.

**In general, inset a tab view by leaving a margin of window-body area on all sides of a tab view.** This layout looks clean and leaves room for additional controls that aren't directly related to the contents of the tab view. You can extend a tab view to meet the window edges, but this layout is unusual.

## Platform considerations

Not supported in iOS, iPadOS, tvOS, or visionOS.

### iOS, iPadOS

For similar functionality, consider using a segmented control instead.

### watchOS

watchOS displays tab views using page controls. For developer guidance, see `TabView`.

## Native implementation

**Related**
- Tab bars
- Segmented controls

**Developer documentation**
- `TabView` — SwiftUI
- `NSTabView` — AppKit

**Key APIs**
- `NSTabView` — AppKit tab view control on macOS
- `TabView` — SwiftUI tab view, rendered as page controls on watchOS

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**A tabbed control that switches between mutually exclusive panes → the ARIA tabs pattern, not a set of buttons toggling divs.** Apple's tabbed control visually communicates that panes are mutually exclusive and belong to a single set. The direct web equivalent is the `tablist`/`tab`/`tabpanel` role structure with `aria-selected` and `aria-controls`, plus roving-tabindex arrow-key navigation between tabs. A row of plain buttons that each show and hide a `div` looks identical sighted but communicates none of this structure to assistive technology — the mutual-exclusivity relationship Apple's tab view encodes visually has to be encoded programmatically on the web, not left implicit.

**"Controls within a pane affect content only in the same pane" → real panel isolation, not just visual hiding.** Apple's self-containment rule maps to keeping each tabpanel's DOM subtree, form state, and element IDs independent of the others. An inactive panel should be removed from the tab order (via the `hidden` attribute, not just `display: none` applied inconsistently) so focus and keyboard navigation can't drift into a pane that isn't currently selected — the web analogue of a hidden pane's controls staying inert.

**Concise, predictable tab labels → the reasoning transfers, the capitalization convention doesn't have to.** Apple's case for noun-phrase labels is that people should predict a pane's contents before switching to it; that reasoning holds on the web without modification. Apple's title-style capitalization is a platform-wide typographic convention, though — a web tab label should follow whatever capitalization style the surrounding site already uses rather than importing Apple's rule wholesale.

**"Avoid a pop-up button when a tabbed control would work" → prefer a visible tablist over a `<select>` for a small, known set of choices.** Apple's argument is about interaction cost and visibility: a tabbed control needs one click and shows every option at once, while a pop-up needs two clicks and hides the options until opened. That argument is platform-agnostic and applies to the web exactly as stated — a `<select>` dropdown for five mutually exclusive views hides options a visible tablist wouldn't.

**"Avoid more than six tabs" → the number six is macOS-window-specific; the underlying constraint is available width, not a fixed count.** Six tabs is a reasonable ceiling for typical macOS window widths and label lengths, but a web tablist's real limit is whatever causes it to wrap to a second row or need horizontal scrolling — narrower containers hit that limit well before six, wider ones can sometimes exceed it. The escape hatch Apple recommends still transfers directly: once a tablist would overflow, fall back to a pop-up-style select or an overflow "more" menu rather than cramming in additional tabs.

**Inset margins, border styles, and hiding the tabbed control for programmatic pane switching → mostly macOS window-chrome detail with no strong web equivalent.** These are decisions about how a tab view sits inside a native window's body area, which doesn't have a meaningful parallel in a browser viewport. The one piece that does transfer is the general instinct behind it: give a tabpanel's content some padding rather than letting it touch the tablist or container edges, unless an edge-to-edge layout is a deliberate design choice.

**iOS/iPadOS's "use a segmented control instead" → on the web, tabs and a segmented-control look are typically the same accessibility pattern wearing different skins.** Apple treats `NSTabView` and a segmented control as genuinely different control classes with different APIs and different semantics (a segmented control is closer to a single-selection button group). On the web there's no equivalent hard platform split — a `tablist`/`tabpanel` structure styled to look like a segmented control is still, and should still behave as, a tabs pattern if it's switching between distinct panels of content; only use a radiogroup-style pattern instead if the choice doesn't actually swap panel content.

**watchOS's Digital Crown paging → hardware-specific, but the paging metaphor itself maps to swipeable tabs on narrow viewports.** The Digital Crown interaction has no web equivalent. The underlying idea — letting people page between sibling detail views without a persistent tabbed control taking up screen space — maps reasonably to a swipeable, dot-indicator carousel of tabpanels on a narrow layout, provided the swipe gesture has a keyboard- and screen-reader-accessible equivalent (visible next/previous controls or standard tab semantics) rather than being the only way to switch panes.

## Do / Don't

| Do | Don't |
|---|---|
| Use a tab view for closely related, self-contained areas of content | Group unrelated content into a single tab view |
| Keep each pane's controls affecting only that pane | Let a control in one pane change content in another pane |
| Give each tab a concise noun-phrase label in title-style capitalization | Use vague or verb-heavy tab labels |
| Prefer a tabbed control over a pop-up button when all choices should be visible at once | Force people to open a pop-up button to see options a tabbed control could show directly |
| Keep a tab view to six tabs or fewer | Cram a seventh-plus tab in without reconsidering the design |
| Inset a tab view with a margin of window-body area | Extend a tab view to the window edges without a specific reason |
| On iOS and iPadOS, use a segmented control for similar functionality | Attempt to use a tab view on iOS, iPadOS, tvOS, or visionOS |
| On watchOS, present multiple detail pages as tab view pages navigated with the Digital Crown | Assume watchOS tab views look or behave like the macOS tabbed control |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
