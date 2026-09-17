---
title: Split views
url: https://developer.apple.com/design/human-interface-guidelines/split-views
platforms: [iOS, iPadOS, macOS, tvOS, visionOS, watchOS]
last_updated: 2025-06-09
---

# Split views

A split view manages the presentation of multiple adjacent panes of content, each of which can contain a variety of components, including tables, collections, images, and custom views.

## Core guidance

Typically, you use a split view to show multiple levels of your app's hierarchy at once and support navigation between them. In this scenario, selecting an item in the view's primary pane displays the item's contents in the secondary pane. Similarly, a split view can display a tertiary pane if items in the secondary pane contain additional content.

It's common to use a split view to display a sidebar for navigation, where the leading pane lists the top-level items or collections in an app, and the secondary and optional tertiary panes can present child collections and item details. Rarely, you might also use a split view to provide groups of functionality that supplement the primary view — for example, Keynote in macOS uses split view panes to present the slide navigator, the presenter notes, and the inspector pane in areas that surround the main slide canvas.

### Best practices

**To support navigation, persistently highlight the current selection in each pane that leads to the detail view.** The selected appearance clarifies the relationship between the content in various panes and helps people stay oriented.

**Consider letting people drag and drop content between panes.** Because a split view provides access to multiple levels of hierarchy, people can conveniently move content from one part of your app to another by dragging items to different panes. For guidance, see Drag and drop.

## Platform considerations

### iOS

**Prefer using a split view in a regular — not a compact — environment.** A split view needs horizontal space in which to display multiple panes. In a compact environment, such as iPhone in portrait orientation, it's difficult to display multiple panes without wrapping or truncating the content, making it less legible and harder to interact with.

### iPadOS

In iPadOS, a split view can include either two vertical panes, like Mail, or three vertical panes, like Keynote.

**Account for narrow, compact, and intermediate window widths.** Since iPad windows are fluidly resizable, it's important to consider the design of a split view layout at multiple widths. In particular, ensure that it's possible to navigate between the various panes in a logical way. For guidance, see Layout. For developer guidance, see `NavigationSplitView` and `UISplitViewController`.

### macOS

In macOS, you can arrange the panes of a split view vertically, horizontally, or both. A split view includes dividers between panes that can support dragging to resize them. For developer guidance, see `VSplitView` and `HSplitView`.

> *Image caption:* Example macOS split view pane arrangements: Vertical, Horizontal, and Multiple.

**Set reasonable defaults for minimum and maximum pane sizes.** If people can resize the panes in your app's split view, make sure to use sizes that keep the divider visible. If a pane gets too small, the divider can seem to disappear, becoming difficult to use.

**Consider letting people hide a pane when it makes sense.** If your app includes an editing area, for example, consider letting people hide other panes to reduce distractions or allow more room for editing — in Keynote, people can hide the navigator and presenter notes panes when they want to edit slide content.

**Provide multiple ways to reveal hidden panes.** For example, you might provide a toolbar button or a menu command — including a keyboard shortcut — that people can use to restore a hidden pane.

**Prefer the thin divider style.** The thin divider measures one point in width, giving you maximum space for content while remaining easy for people to use. Avoid using thicker divider styles unless you have a specific need. For example, if both sides of a divider present table rows that use strong linear elements that might make a thin divider hard to distinguish, it might work to use a thicker divider. For developer guidance, see `NSSplitView.DividerStyle`.

### tvOS

In tvOS, a split view can work well to help people filter content. When people choose a filter category in the primary pane, your app can display the results in the secondary pane.

**Choose a split view layout that keeps the panes looking balanced.** By default, a split view devotes a third of the screen width to the primary pane and two-thirds to the secondary pane, but you can also specify a half-and-half layout.

**Display a single title above a split view, helping people understand the content as a whole.** People already know how to use a split view to navigate and filter content; they don't need titles that describe what each pane contains.

**Choose the title's alignment based on the type of content the secondary pane contains.** Specifically, when the secondary pane contains a content collection, consider centering the title in the window. In contrast, if the secondary pane contains a single main view of important content, consider placing the title above the primary view to give the content more room.

### visionOS

**To display supplementary information, prefer a split view instead of a new window.** A split view gives people convenient access to more information without leaving the current context, whereas a new window may confuse people who are trying to navigate or reposition content. Opening more windows also requires you to carefully manage the relationship between views in your app or game. If you need to request a small amount of information or present a simple task that someone must complete before returning to their main task, use a sheet.

### watchOS

In watchOS, the split view displays either the list view or a detail view as a full-screen view.

**Automatically display the most relevant detail view.** When your app launches, show people the most pertinent information. For example, display information relevant to their location, the time, or their recent actions.

**If your app displays multiple detail pages, place the detail views in a vertical tab view.** People can then use the Digital Crown to scroll between the detail view's tabs. watchOS also displays a page indicator next to the Digital Crown, indicating the number of tabs and the currently selected tab.

## Native implementation

**Related**
- Sidebars
- Tab bars
- Layout

**Developer documentation**
- `NavigationSplitView` — SwiftUI
- `UISplitViewController` — UIKit
- `NSSplitViewController` — AppKit

**Key APIs**
- `NavigationSplitView` — SwiftUI split view with primary, secondary, and optional tertiary columns
- `UISplitViewController` — UIKit split view controller for iOS and iPadOS
- `NSSplitViewController` / `VSplitView` / `HSplitView` — AppKit split view arrangement on macOS
- `NSSplitView.DividerStyle` — thin, thick, and pane-splitter divider styles on macOS

**Videos:** Make your UIKit app more flexible

## Web translation *(derived — not from Apple)*

Apple's HIG contains no web guidance. The mappings below apply the same principles to the web; they are inference, not Apple policy.

**The sidebar/detail pattern → a two-pane responsive layout that collapses, not two separately routed pages.** Apple's core split-view idea — selecting an item in the primary pane updates the secondary pane in place, without losing the primary pane's context — is the same goal behind a well-built web master-detail layout: a CSS grid or flexbox two-column shell where clicking a list item swaps the detail pane's content (via client-side routing or a partial fetch) rather than triggering a full navigation that discards the sidebar's scroll position and selection state.

**Regular vs. compact environment → a container query on the shell, not a viewport breakpoint.** Apple's iOS rule — prefer a split view only in a regular environment, fall back to something else in compact — is a resizing rule about the split view's *own* available width, not the whole screen's. The web-native equivalent is a container query on the split-view shell itself, so an embedded split view collapses correctly even inside a narrower parent (a panel, a modal) regardless of the viewport's overall size. This is a stronger fit than a `min-width` media query, which only ever asks about the viewport.

**iPadOS's narrow/compact/intermediate widths → the same container-query logic, with more than two breakpoints.** iPad's guidance to design for multiple intermediate widths, not just a binary regular/compact split, argues against a single collapse threshold on the web too — a sidebar that's pinned-open, overlay, or fully hidden depending on available width (three states, not two) usually serves a resizable web layout better than one breakpoint.

**Draggable, minimum-size-respecting dividers → a resizer with a real hit target and persisted state.** Apple's macOS rule to keep the divider visible at minimum pane size is really an anti-footgun rule: don't let a resize action make the resize handle itself disappear. On the web this means giving the drag handle a hit target noticeably wider than its 1px visual line (mirroring Apple's "prefer the thin, one-point divider" — visually thin, not thin as a target), enforcing `min-width`/`max-width` on both panes during a drag, and persisting the chosen split (`localStorage` or user preference) the way a native app remembers a user-resized pane.

**Hiding a pane via multiple entry points → don't rely on the drag handle alone.** Apple explicitly requires more than one way to reveal a hidden pane (toolbar button, menu command, keyboard shortcut) precisely because a fully collapsed pane has nothing left to drag. The web equivalent is a visible toggle button that's independent of the resizer — a collapsed sidebar's only affordance shouldn't be "somehow find and drag the invisible edge."

**tvOS's single title above the whole split view → largely non-transferable.** This is a 10-foot-UI convention driven by focus-based navigation replacing per-pane chrome; it doesn't map cleanly onto pointer- or touch-driven web layouts, where each pane commonly needs its own heading for accessibility landmark purposes (`<h1>`/`<h2>` structure, `aria-label` per region) regardless of whether a page-level title also exists.

**visionOS's "prefer a split view over a new window for supplementary info" → prefer an inline panel or drawer over a new tab/window.** The underlying reasoning transfers well: opening a new browser tab or window for a small amount of supplementary information disorients people and forces you to manage state across two disconnected contexts, exactly as Apple describes for spatial windows. An inline expanding panel, drawer, or the detail pane itself is the web equivalent; reserve a genuinely new browsing context for tasks that are meant to be separate.

**watchOS's list-or-detail-never-both → this is just small-viewport responsive collapse.** Showing either the list or the detail as a full-screen view, never both, because the screen is too small for two panes, is the same reasoning that already drives the standard mobile-web pattern of replacing a list with a detail view on narrow screens rather than trying to render both. Apple's Digital Crown vertical-tab-view detail-paging is watch-hardware-specific and has no direct web equivalent, though the underlying idea — let people page between sibling detail views without returning to the list — maps to swipeable tabs or a paged detail carousel on a narrow web layout.

## Do / Don't

| Do | Don't |
|---|---|
| Persistently highlight the selection in each pane leading to the detail view | Leave the current selection ambiguous across panes |
| Use a split view only where there's horizontal space for multiple panes (iOS: regular environment) | Force a split view into a compact environment where content wraps or truncates |
| Design for narrow, compact, and intermediate iPad window widths | Design a split view for only one fixed window width |
| Keep the divider visible at minimum pane size | Let a pane shrink so far its divider becomes unusable |
| Provide a toolbar button, menu command, or shortcut to restore a hidden pane | Make the drag handle the only way to reveal a collapsed pane |
| Prefer the thin, one-point macOS divider unless strong linear content demands more | Use a thick divider by default without a specific need |
| Show a single title above a tvOS split view | Add a separate descriptive title to every tvOS pane |
| Use a split view instead of a new window for visionOS supplementary info | Open a new window for a small amount of supplementary content |
| Show list or detail as full-screen on watchOS, never both at once | Try to render both panes side by side on a watch-sized screen |

---

*Summarized from Apple's Human Interface Guidelines. Human Interface Guidelines © Apple Inc. All rights reserved. This project is not affiliated with or endorsed by Apple. The linked `url` above is authoritative; this page is a snapshot. See NOTICE.md at the skill root.*
